---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Überwachung und Berichterstellung zu JEA
ms.openlocfilehash: 2388c735840d8d3683aa8bc9869b9fb0371e5902
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851219"
---
# <a name="auditing-and-reporting-on-jea"></a>Überwachung und Berichterstellung zu JEA

> Gilt für: Windows PowerShell 5.0

Nachdem Sie JEA bereitgestellt haben, sollten Sie die JEA-Konfiguration regelmäßig überwachen.
Auf diese Weise können Sie leichter beurteilen, ob die Benutzer, die auf den JEA-Endpunkt zugreifen, dazu autorisiert sind und ob die ihnen zugewiesenen Rollen noch geeignet sind.

Dieses Thema beschreibt die verschiedenen Methoden zur Überwachung eines JEA-Endpunkts.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Ermitteln von registrierten JEA-Sitzungen auf einem Computer

Verwenden Sie das [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration)-Cmdlet, um zu überprüfen, welche JEA-Sitzungen auf einem Computer registriert sind.

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

Die jeweils gültigen Rechte für den Endpunkt werden in der Eigenschaft „Berechtigung“ aufgeführt.
Diese Benutzer sind berechtigt, eine Verbindung mit dem JEA-Endpunkt herzustellen. Auf welche Rollen (und im weiteren Sinne Befehle) sie jedoch Zugriff haben, richtet sich nach dem Feld „RoleDefinitions“ in der [Sitzungskonfigurationsdatei](session-configurations.md), die beim Registrieren des Endpunkts verwendet wurde.

Sie können die Rollenzuordnungen in einem registrierten JEA-Endpunkt bewerten, indem Sie die Daten in der Eigenschaft „RoleDefinitions“ erweitern.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Ermitteln verfügbarer Rollenfunktionen auf dem Computer

Rollenfunktionsdateien werden nur dann von JEA verwendet, wenn sie in einem Ordner „RoleCapabilities“ in einem gültigen PowerShell-Modul gespeichert sind.
Sie erhalten alle verfügbaren Rollenfunktionen, indem Sie die Liste verfügbarer Module durchsuchen.

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
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> Die Reihenfolge der Ergebnisse dieser Funktion entspricht nicht zwangsläufig der Reihenfolge, in der die Rollenfunktionen ausgewählt werden, wenn mehrere Rollenfunktionen den gleichen Namen haben.

## <a name="check-effective-rights-for-a-specific-user"></a>Überprüfen gültiger Berechtigungen für einen bestimmten Benutzer

Nachdem Sie einen JEA-Endpunkt eingerichtet haben, sollten Sie überprüfen, welche Befehle in einer JEA-Sitzung für einen bestimmten Benutzer verfügbar sind.
Sie können [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) zum Auflisten aller Befehle verwenden, die für Benutzer gelten, die eine JEA-Sitzung mit ihren aktuellen Gruppenmitgliedschaften starten.
Die Ausgabe von `Get-PSSessionCapability` ist identisch mit dem angegebenen Benutzerkonto, das `Get-Command -CommandType All` in einer JEA-Sitzung ausführt.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Wenn Ihre Benutzer keine ständigen Mitglieder von Gruppen sind, die ihnen zusätzliche JEA-Rechte erteilen, spiegelt dieses Cmdlet möglicherweise nicht die zusätzlichen Berechtigungen wider.
Dies ist i.d.R. der Fall, wenn Just-in-Time-Privileged Access Management-Systeme verwendet werden, um Benutzern vorübergehend die Aufnahme in eine Sicherheitsgruppe zu ermöglichen.
Überprüfen Sie daher stets sorgfältig die Zuordnung von Benutzern zu Rollen und den Inhalt der einzelnen Rollen, um sicherzustellen, dass Benutzer nur Zugriff auf jene Befehle habe, die sie zur Erfüllung ihrer Aufgaben unbedingt benötigen.

## <a name="powershell-event-logs"></a>PowerShell-Ereignisprotokolle

Wenn Sie die Modul- und/oder Skriptblockprotokollierung im System aktivieren, enthalten die Windows-Ereignisprotokolle Ereignisse für jeden Befehl, den Benutzer in ihren JEA-Sitzungen ausgeführt haben.
Um diese Ereignisse zu finden, öffnen Sie die Windows-Ereignisanzeige, navigieren Sie zum Ereignisprotokoll **Microsoft-Windows-PowerShell/Operational** Ereignisprotokoll, und suchen Sie nach Ereignissen mit der Ereignis-ID **4104**.

Jeder Eintrag im Ereignisprotokoll enthält Informationen über die Sitzung, in der der Befehl ausgeführt wurde.
Bei JEA-Sitzungen handelt es sich dabei um wichtige Informationen zum **ConnectedUser**, also dem tatsächlichen Benutzer, der die JEA-Sitzung erstellt hat, als auch zum Parameter **RunAsUser**, der das JEA-Konto angibt, das zum Ausführen des Befehls verwendet wurde.
Anwendungsereignisprotokolle zeigen Änderungen durch RunAsUser. Die Aufzeichnungs- bzw Modul-/Skriptprotokollierung sollte daher unbedingt aktiviert sein, um einen bestimmten Befehlsaufruf zu einem Benutzer zurückverfolgen zu können.

## <a name="application-event-logs"></a>Anwendungsereignisprotokolle

Wenn Sie einen Befehl in einer JEA-Sitzung ausführen, die mit einer externen Anwendung oder einem externen Dienst interagiert, können diese Anwendungen Ereignisse in ihren eigenen Ereignisprotokollen protokollieren.
Im Gegensatz zu PowerShell-Protokollen und Aufzeichnungen erfassen andere Protokollierungsmechanismen nicht den Benutzer, der eine Verbindung zur JEA-Sitzung aufbaut. Stattdessen wird nur das Konto des virtuellen, ausführenden Benutzers bzw. des gruppenverwalteten Dienstkontos protokolliert.
Um zu bestimmen, wer den Befehl ausgeführt hat, überprüfen Sie eine [Sitzungsaufzeichnung](#session-transcripts), oder korrelieren Sie PowerShell-Ereignisprotokolle mit dem Zeitpunkt und den Benutzern, die im Anwendungsereignisprotokoll angezeigt werden.

Das WinRM-Protokoll kann ebenfalls hilfreich sein, wenn Sie ausführende Benutzer in einem Anwendungsereignisprotokoll mit dem Benutzer korrelieren möchten, der eine Verbindung herstellt.
Die Ereignis-ID **193** im Protokoll **Microsoft-Windows-Windows Remote Management/Operational** erfasst bei jeder Erstellung einer JEA-Sitzung die Sicherheits-ID (SID) und den Kontonamen sowohl des Benutzers, der eine Verbindung herstellt, als auch des ausführenden Benutzers.

## <a name="session-transcripts"></a>Sitzungsaufzeichnungen

Wenn Sie JEA für die Erstellung einer Aufzeichnung bei jeder Benutzersitzung konfiguriert haben, wird eine Textkopie für die Aktionen aller Benutzer im angegebenen Ordner gespeichert.

Sie finden sämtliche Aufzeichnungsverzeichnisse, indem Sie den folgenden Befehl als Administrator auf dem mit JEA konfigurierten Computer ausführen:

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
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

Der Hauptteil der Aufzeichnung enthält Informationen zu jedem Befehl, den der Benutzer aufgerufen hat.
Die genaue Syntax des durch den Benutzer ausgeführten Befehls ist in JEA-Sitzungen nicht verfügbar. Dies ist auf die Art und Weise zurückzuführen, in der Befehle für PowerShell-Remoting verarbeitet werden. Der tatsächlich ausgeführt Befehl kann jedoch weiterhin ermittelt werden.
Im Folgenden finden Sie ein Beispiel für einen Aufzeichnungsausschnitt eines Benutzers, der in einer JEA-Sitzung `Get-Service Dns` ausgeführt hat:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Für jeden Befehl, den der Benutzer ausführt, wird eine Zeile „CommandInvocation“ geschrieben. Sie beschreibt das Cmdlet bzw. die Funktion, das bzw. die der Benutzer aufgerufen hat.
Auf jede Zeile „CommandInvocation“ folgt „ParameterBindings“ mit Information über jeden Parameter und Wert, der für den Befehl angegeben wurde.
Im voranstehenden Beispiel sehen Sie, dass für den Parameter „Name“ der Wert „Dns“ für das Cmdlet „Get-Service“ angegeben wurde.

Die Ausgabe jedes Befehls löst außerdem eine „CommandInvocation“ aus, in der Regel nach „Out-Default“.
Das vom Befehl zurückgegebene PowerShell-Objekt fungiert als InputObject für„InputObject“ von „Out-Default“.
Die Details des Objekts einige Zeilen darunter bilden täuschend ähnlich das nach, was der Benutzer gesehen hätte.

## <a name="see-also"></a>Siehe auch

- [*PowerShell ♥ the Blue Team (PowerShell ♥ das Blue Team)* – Blogbeitrag zum Thema Sicherheit](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)
