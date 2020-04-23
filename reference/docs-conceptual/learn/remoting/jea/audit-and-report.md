---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Überwachung und Berichterstellung zu JEA
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "70017791"
---
# <a name="auditing-and-reporting-on-jea"></a>Überwachung und Berichterstellung zu JEA

Nachdem Sie JEA bereitgestellt haben, muss die JEA-Konfiguration regelmäßig überwacht werden. Dadurch können Sie leichter beurteilen, ob die Benutzer, die auf den JEA-Endpunkt zugreifen, dazu berechtigt sind und ob die ihnen zugewiesenen Rollen noch geeignet sind.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Ermitteln von registrierten JEA-Sitzungen auf einem Computer

Verwenden Sie das [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration)-Cmdlet, um zu überprüfen, welche JEA-Sitzungen auf einem Computer registriert sind.

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }
```

```Output
Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed,
                CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

Die jeweils gültigen Rechte für den Endpunkt werden in der Eigenschaft **Berechtigung** aufgeführt. Diese Benutzer sind berechtigt, mit dem JEA-Endpunkt eine Verbindung herzustellen. Auf welche Rollen und Befehle sie jedoch Zugriff haben, richtet sich nach der Eigenschaft **RoleDefinitions** in der [Sitzungskonfigurationsdatei](session-configurations.md), die beim Registrieren des Endpunkts verwendet wurde. Erweitern Sie die Eigenschaft **RoleDefinitions**, um die Rollenzuordnungen in einem registrierten JEA-Endpunkt zu bewerten.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Ermitteln verfügbarer Rollenfunktionen auf dem Computer

JEA ruft die im Ordner `.psrc`RoleCapabilities**gespeicherten**-Dateien innerhalb eines PowerShell-Moduls ab. Mit der folgenden Funktion können Sie alle auf einem Computer verfügbaren Rollenfunktionen ermitteln:

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{
        Name = 'Path'; Expression = { $_.FullName }
    } | Sort-Object Name
}
```

> [!NOTE]
> Die Reihenfolge der Ergebnisse dieser Funktion entspricht nicht zwangsläufig der Reihenfolge, in der die Rollenfunktionen ausgewählt werden, wenn mehrere Rollenfunktionen den gleichen Namen haben.

## <a name="check-effective-rights-for-a-specific-user"></a>Überprüfen gültiger Berechtigungen für einen bestimmten Benutzer

Mit dem Cmdlet [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) werden alle für den JEA-Endpunkt verfügbaren Befehle basierend auf den Mitgliedschaften einer Benutzergruppe aufgelistet.
Die Ausgabe von `Get-PSSessionCapability` ist identisch mit dem angegebenen Benutzerkonto, das `Get-Command -CommandType All` in einer JEA-Sitzung ausführt.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Wenn Ihre Benutzer keine ständigen Mitglieder von Gruppen sind, die ihnen zusätzliche JEA-Rechte erteilen, entspricht dieses Cmdlet möglicherweise nicht den zusätzlichen Berechtigungen. Dies ist der Fall, wenn Just-in-Time-Systeme für Privileged Access Management verwendet werden, um Benutzern vorübergehend die Aufnahme in eine Sicherheitsgruppe zu ermöglichen. Gehen Sie bei der Bewertung der Zuordnung von Benutzern zu Rollen und Funktionen sorgfältig vor, um den einzelnen Benutzern nur die für eine erfolgreiche Verrichtung ihrer Arbeit erforderliche Zugriffsebene zu gewähren.

## <a name="powershell-event-logs"></a>PowerShell-Ereignisprotokolle

Wenn Sie die Protokollierung von Modul- oder Skriptblöcken für das System aktivieren, enthalten die Windows-Ereignisprotokolle Ereignisse für jeden Befehl, den ein Benutzer in einer JEA-Sitzung ausführt. Öffnen Sie für die Suche nach diesen Ereignissen das Ereignisprotokoll **Microsoft-Windows-PowerShell/Operational**, und suchen Sie nach Ereignissen mit der Ereignis-ID **4104**.

Jeder Eintrag im Ereignisprotokoll enthält Informationen über die Sitzung, in der der Befehl ausgeführt wurde. Bei JEA-Sitzungen enthält das Ereignis Informationen zu **ConnectedUser** und **RunAsUser**. **ConnectedUser** ist der Benutzer, der die JEA-Sitzung tatsächlich erstellt hat. **RunAsUser** ist das Konto, mit dem JEA den Befehl ausgeführt hat.

Die Anwendungsereignisprotokolle enthalten Änderungen, die von **RunAsUser** vorgenommen wurden. Die Modul- und Skriptprotokollierung muss also aktiviert sein, um einen bestimmten Befehlsaufruf zu **ConnectedUser** zurückzuverfolgen.

## <a name="application-event-logs"></a>Anwendungsereignisprotokolle

In einer JEA-Sitzung ausgeführte Befehle, die mit externen Anwendungen oder Diensten interagieren, protokollieren möglicherweise Ereignisse in ihren eigenen Ereignisprotokollen. Im Gegensatz zu PowerShell-Protokollen und -Aufzeichnungen erfassen andere Protokollierungsmechanismen nicht den verbundenen Benutzer der JEA-Sitzung. Stattdessen protokollieren diese Anwendungen nur den virtuellen ausführenden Benutzer.
Überprüfen Sie zur Bestimmung, wer den Befehl ausgeführt hat, eine [Sitzungsaufzeichnung](#session-transcripts), oder korrelieren Sie PowerShell-Ereignisprotokolle mit dem Zeitpunkt und Benutzer, die im Anwendungsereignisprotokoll angezeigt werden.

Mit dem WinRM-Protokoll können Sie in einem Anwendungsereignisprotokoll ebenfalls ausführende Benutzer mit dem Benutzer korrelieren, der eine Verbindung herstellt. Mit der Ereignis-ID **193** im Protokoll **Microsoft-Windows-Windows Remote Management/Operational** werden bei jeder neuen JEA-Sitzung die Sicherheits-ID (SID) und der Kontoname sowohl des Benutzers, der eine Verbindung herstellt, als auch des ausführenden Benutzers erfasst.

## <a name="session-transcripts"></a>Sitzungsaufzeichnungen

Wenn Sie JEA für die Erstellung einer Aufzeichnung bei jeder Benutzersitzung konfiguriert haben, wird eine Textkopie für die Aktionen aller Benutzer im angegebenen Ordner gespeichert.

Mit dem folgenden Befehl können Sie (als Administrator) nach allen Aufzeichnungsverzeichnissen suchen.

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

Jede Aufzeichnung beginnt mit Informationen über den Zeitpunkt, zu dem die Sitzung gestartet wurde, welche Benutzer eine Verbindung mit der Sitzung hergestellt haben und welche JEA-Identität ihnen zugewiesen wurde.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

Der Hauptteil der Aufzeichnung enthält Informationen zu jedem vom Benutzer aufgerufenen Befehl. Die genaue Syntax des verwendeten Befehls ist für JEA-Sitzungen aufgrund der Transformationsart von Befehlen für PowerShell-Remoting nicht verfügbar. Der tatsächlich ausgeführte Befehl kann jedoch weiterhin ermittelt werden. Im Folgenden finden Sie ein Beispiel für einen Aufzeichnungsausschnitt eines Benutzers, der in einer JEA-Sitzung `Get-Service Dns` ausgeführt hat:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Für jeden von einem Benutzer ausgeführten Befehl wird eine **CommandInvocation**-Zeile geschrieben. Mit **ParameterBindings** werden alle Parameter und Werte erfasst, die für den Befehl angegeben wurden. Im vorherigen Beispiel wird für das Cmdlet **der Parameter**Name**mit dem Wert**Dns`Get-Service` angegeben.

Die Ausgabe jedes Befehls löst außerdem **CommandInvocation** aus, in der Regel zu `Out-Default`. **InputObject** von `Out-Default` stellt das vom Befehl zurückgegebene PowerShell-Objekt dar. Die Details des Objekts einige Zeilen darunter bilden täuschend ähnlich das nach, was der Benutzer gesehen hätte.

## <a name="see-also"></a>Weitere Informationen

[*PowerShell ♥ the Blue Team (PowerShell ♥ das Blue Team)* – Blogbeitrag zum Thema Sicherheit](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
