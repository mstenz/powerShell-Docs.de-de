---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,security
title: Registrieren von JEA-Konfigurationen
ms.openlocfilehash: 0684a1c7acffbccbedab9dba4689611a24c8ae25
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="registering-jea-configurations" class="xliff"></a>
# Registrieren von JEA-Konfigurationen

> Gilt für: Windows PowerShell 5.0

Sobald Sie Ihre [Rollenfunktionen](role-capabilities.md) und die [Sitzungskonfigurationsdatei](session-configurations.md) erstellt haben, ist JEA einsatzbereit. Der letzte Schritt besteht darin, den JEA-Endpunkt zu registrieren.
Bei diesem Vorgang werden die Informationen der Sitzungskonfiguration auf das System angewendet, und der Endpunkt kann von Benutzern und Automatisierungsmodulen verwendet werden.

<a id="single-machine-configuration" class="xliff"></a>
## Einzelcomputerkonfiguration

Sie können JEA für kleine Umgebungen bereitstellen, indem Sie die Konfigurationsdatei mithilfe des [Register-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration)-Cmdlets registrieren.

Vergewissern Sie sich vor Beginn, dass die folgenden Voraussetzungen erfüllt sind:
- Eine oder mehrere Rollen wurden erstellt und im Ordner „RoleCapabilities“ eines gültigen PowerShell-Moduls abgelegt.
- Eine Sitzungskonfigurationsdatei wurde erstellt und getestet.
- Der Benutzer, der die JEA-Konfiguration registriert, verfügt über Administratorrechte auf den Systemen.

Sie müssen auch einen Namen für den JEA-Endpunkt auswählen.
Der Name des JEA-Endpunkts wird benötigt, wenn Benutzer mithilfe von JEA eine Verbindung mit dem System herstellen möchten.
Sie können das [Get-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration)-Cmdlet zum Überprüfen der Namen der vorhandenen Endpunkte auf dem System verwenden.
Endpunkte, deren Name mit „microsoft“ beginnt, gehören normalerweise zum Funktionsumfang von Windows.
Der Endpunkt „microsoft.powershell“ ist der Standardendpunkt, der verwendet wird, wenn eine Verbindung mit einem PowerShell-Remoteendpunkt hergestellt wird.

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

Wenn Sie einen entsprechenden Namen für den JEA-Endpunkt festgelegt haben, führen Sie den folgenden Befehl zum Registrieren des Endpunkts aus:

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> Durch den oben angegebenen Befehl wird der WinRM-Dienst auf dem System neu gestartet.
> Dadurch werden alle PowerShell-Remoting-Sitzungen sowie alle laufenden DSC-Konfigurationen beendet.
> Schalten Sie nach Möglichkeit vor dem Ausführen des Befehls alle Produktionscomputern offline, um Unterbrechung des Geschäftsbetriebs zu vermeiden.

Wenn die Registrierung erfolgreich war, können Sie mit dem [Verwenden von JEA](using-jea.md) beginnen.
Sie können die Sitzungskonfigurationsdatei jederzeit löschen. Sie wird nach der Registrierung nicht verwendet.

<a id="multi-machine-configuration-with-dsc" class="xliff"></a>
## Konfigurieren mehrerer Computer mit DSC (Desired State Configuration)

Wenn Sie JEA auf mehreren Computern bereitstellen, bietet sich als einfachstes Bereitstellungsmodell die Verwendung der JEA-[DSC-](https://msdn.microsoft.com/en-us/powershell/dsc/overview)-Ressource an, um JEA schnell und konsistent auf jedem Computer bereitzustellen.

Wenn Sie JEA mit DSC bereitstellen möchten, müssen Sie sicherstellen, dass die folgenden erforderlichen Anforderungen erfüllt sind:
- Eine oder mehrere Rollenfunktionen wurden erstellt und einem gültigen PowerShell-Modul hinzugefügt.
- Das PowerShell-Modul, das die Rollen enthält, ist auf einer (schreibgeschützten) Freigabe gespeichert, auf die von jedem Computer aus zugegriffen werden kann.
- Die Einstellungen für die Sitzungskonfiguration wurden festgelegt. Sie müssen keine Sitzungskonfigurationsdatei erstellen, um die JEA-DSC-Ressource zu verwenden.
- Sie verfügen über Anmeldeinformationen, mit denen Sie administrative Aktionen auf allen Computern ausführen können, oder Sie haben Zugriff auf einen DSC-Pullserver, um die Computer zu verwalten.
- Sie haben die [JEA-DSC-Ressourcen](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource) heruntergeladen.

Erstellen Sie auf einem Zielcomputer (oder gegebenenfalls einem Pullserver) eine DSC-Konfiguration für Ihren JEA-Endpunkt.
In dieser Konfiguration verwenden Sie die JustEnoughAdministration-DSC-Ressource, um die Sitzungskonfigurationsdatei einzurichten, und die Dateiressource, um die Rollenfunktionen von der Dateifreigabe zu kopieren.

Die folgenden Eigenschaften können mithilfe der DSC-Ressource konfiguriert werden:
- Rollendefinitionen
- Virtuelle Kontogruppen
- Gruppenverwalteter Dienstkontoname
- Aufzeichnungsverzeichnis
- Benutzerlaufwerk
- Regeln für bedingten Zugriff
- Skripts zum Starten der JEA-Sitzung

Die Syntax für jede dieser Eigenschaften in einer DSC-Konfiguration stimmt mit Konfigurationsdatei der PowerShell-Sitzung überein.

Es folgt ein Beispiel einer DSC-Konfiguration für ein allgemeines Serverwartungsmodul.

Dabei wird von einem gültigen PowerShell-Modul mit Rollenfunktionen in einem Unterordner „RoleCapabilities“ ausgegangen, das sich auf der Dateifreigabe „\\\\Myfileshare\\JEA“ befindet.


```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

Diese Konfiguration kann direkt auf einem System angewendet werden. Dazu müssen Sie den [lokalen Konfigurations-Managers aufrufen ](https://msdn.microsoft.com/en-us/powershell/dsc/metaconfig) oder die [Pullserverkonfiguration](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver) aktualisieren.

Mithilfe der DSC-Ressource können Sie außerdem den standardmäßigen Microsoft.PowerShell-Remoting-Endpunkt ersetzen.
In diesem Fall registriert die Ressource automatisch einen nicht eingeschränkten Sicherungsendpunkt mit dem Namen „Microsoft.PowerShell.Restricted“, der über die Standard-WinRM-ACL verfügt. (Remotemanagementbenutzer und Mitglieder lokaler Administratorengruppen erhalten auf diese Weise Zugriff.)

<a id="unregistering-jea-configurations" class="xliff"></a>
## Aufheben der Registrierung von JEA-Konfigurationen

Verwenden Sie das [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration)-Cmdlet, um einen JEA-Endpunkt von einem System zu entfernen.
Durch das Aufheben der Registrierung eines JEA-Endpunkts wird verhindert, dass neue Benutzer neue JEA-Sitzungen auf dem System erstellen.
Sie können auch eine JEA-Konfiguration aktualisieren, indem Sie eine aktualisierte Sitzungskonfigurationsdatei erneut registrieren und den gleichen Endpunktnamen verwenden.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Wenn Sie die Registrierung eines JEA-Endpunkts aufheben, wird der WinRM-Dienst neu gestartet.
> Dadurch werden die meisten aktuell ausgeführten Remoteverwaltungsvorgänge unterbrochen, darunter andere PowerShell-Sitzungen, WMI-Aufrufe und einige Verwaltungstools.
> Heben Sie daher die Registrierung von PowerShell-Endpunkte nur während geplanter Wartungsfenster auf.

<a id="next-steps" class="xliff"></a>
## Nächste Schritte

- [Verwenden von JEA](using-jea.md)

