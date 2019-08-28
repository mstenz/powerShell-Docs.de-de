---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Registrieren von JEA-Konfigurationen
ms.openlocfilehash: c85eddea2196e4db4bbeea54bde11074f3d1c927
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017711"
---
# <a name="registering-jea-configurations"></a>Registrieren von JEA-Konfigurationen

Nachdem Sie Ihre [Rollenfunktionen](role-capabilities.md) und die [Sitzungskonfigurationsdatei](session-configurations.md) erstellt haben, müssen Sie nur noch den JEA-Endpunkt registrieren. Das Registrieren des JEA-Endpunkts beim System stellt den Endpunkt für Benutzer und Automatisierungs-Engines zur Verfügung.

## <a name="single-machine-configuration"></a>Einzelcomputerkonfiguration

Sie können JEA für kleine Umgebungen bereitstellen, indem Sie die Konfigurationsdatei mithilfe des [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration)-Cmdlets registrieren.

Vergewissern Sie sich vor Beginn, dass die folgenden Voraussetzungen erfüllt sind:

- Eine oder mehrere Rollen wurden erstellt und im Ordner **RoleCapabilities** eines PowerShell-Moduls abgelegt.
- Eine Sitzungskonfigurationsdatei wurde erstellt und getestet.
- Der Benutzer, der die JEA-Konfiguration registriert, verfügt über Administratorrechte auf dem System.
- Sie haben einen Namen für Ihren JEA-Endpunkt ausgewählt.

Der Name des JEA-Endpunkts wird benötigt, wenn Benutzer mit JEA eine Verbindung mit dem System herstellen. Das [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration)-Cmdlet listet die Namen der Endpunkte auf einem System auf. Endpunkte, deren Name mit `microsoft` beginnen, gehören normalerweise zum Funktionsumfang von Windows. Der Endpunkt `microsoft.powershell` ist der Standardendpunkt, der verwendet wird, wenn eine Verbindung mit einem PowerShell-Remoteendpunkt hergestellt wird.

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

Führen Sie den folgenden Befehl aus, um den Endpunkt zu registrieren:

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> Der oben angegebene Befehl startet den WinRM-Dienst im System neu. Dadurch werden alle PowerShell-Remotingsitzungen und alle laufenden DSC-Konfigurationen beendet. Schalten Sie nach Möglichkeit vor dem Ausführen des Befehls alle Produktionscomputer offline, um Unterbrechung des Geschäftsbetriebs zu vermeiden.

Nach der Registrierung können Sie [JEA verwenden](using-jea.md). Sie können die Sitzungskonfigurationsdatei jederzeit löschen. Die Konfigurationsdatei wird nach der Registrierung des Endpunkts nicht verwendet.

## <a name="multi-machine-configuration-with-dsc"></a>Konfigurieren mehrerer Computer mit DSC (Desired State Configuration)

Wenn Sie JEA auf mehreren Computern bereitstellen, bietet sich als einfachstes Bereitstellungsmodell die Verwendung der JEA-[DSC-](/powershell/dsc/overview)-Ressource (Desired State Configuration) an, um JEA schnell und konsistent auf jedem Computer bereitzustellen.

Um JEA mit DSC bereitzustellen, müssen die folgenden Voraussetzungen erfüllt sein:

- Eine oder mehrere Rollenfunktionen wurden erstellt und einem PowerShell-Modul hinzugefügt.
- Das PowerShell-Modul, das die Rollen enthält, ist auf einer (schreibgeschützten) Freigabe gespeichert, auf die von jedem Computer aus zugegriffen werden kann.
- Die Einstellungen für die Sitzungskonfiguration wurden festgelegt. Sie müssen keine Sitzungskonfigurationsdatei erstellen, um die JEA-DSC-Ressource zu verwenden.
- Sie verfügen über Anmeldeinformationen, die Verwaltungsaktionen auf allen Computern ermöglichen, oder Sie haben Zugriff auf einen DSC-Pullserver, um die Computer zu verwalten.
- Sie haben die [JEA-DSC-Ressourcen](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource) heruntergeladen.

Erstellen Sie auf einem Zielcomputer (oder gegebenenfalls einem Pullserver) eine DSC-Konfiguration für Ihren JEA-Endpunkt. In dieser Konfiguration definiert die **JustEnoughAdministration**-DSC-Ressource die Sitzungskonfigurationsdatei, und die **Dateiressource** kopiert die Rollenfunktionen aus der Dateifreigabe.

Die folgenden Eigenschaften können mithilfe der DSC-Ressource konfiguriert werden:

- Rollendefinitionen
- Virtuelle Kontogruppen
- Gruppenverwalteter Dienstkontoname
- Aufzeichnungsverzeichnis
- Benutzerlaufwerk
- Regeln für bedingten Zugriff
- Skripts zum Starten der JEA-Sitzung

Die Syntax für jede dieser Eigenschaften in einer DSC-Konfiguration stimmt mit Konfigurationsdatei der PowerShell-Sitzung überein.

Es folgt ein Beispiel einer DSC-Konfiguration für ein allgemeines Serverwartungsmodul. Dabei wird von einem gültigen PowerShell-Modul mit Rollenfunktionen ausgegangen, das sich auf der Dateifreigabe `\\myfileshare\JEA` befindet.

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

Diese Konfiguration wird danach auf einem System angewendet. Dazu müssen Sie den [lokalen Konfigurations-Manager aufrufen ](/powershell/dsc/managing-nodes/metaConfig) oder die [Pullserverkonfiguration](/powershell/dsc/pull-server/pullServer) aktualisieren.

Mithilfe der DSC-Ressource können Sie außerdem den **Microsoft.PowerShell**-Standardendpunkt ersetzen. Wenn dieser ersetzt wird, registriert die Ressource automatisch einen Sicherungsendpunkt namens **Microsoft.PowerShell.Restricted**. Der Sicherungsendpunkt verfügt über die Standard-WinRM-ACL, die Remotemanagementbenutzern und Mitgliedern der lokalen Administratorengruppe erlaubt, auf diesen zuzugreifen.

## <a name="unregistering-jea-configurations"></a>Aufheben der Registrierung von JEA-Konfigurationen

Verwenden Sie das [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration)-Cmdlet, um einen JEA-Endpunkt von einem System zu entfernen. Das Aufheben der Registrierung eines JEA-Endpunkts verhindert, dass neue Benutzer neue JEA-Sitzungen auf dem System erstellen. Sie können auch eine JEA-Konfiguration aktualisieren, indem Sie eine aktualisierte Sitzungskonfigurationsdatei erneut registrieren und den gleichen Endpunktnamen verwenden.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Wenn Sie die Registrierung eines JEA-Endpunkts aufheben, wird der WinRM-Dienst neu gestartet. Dadurch werden die meisten aktuell ausgeführten Remoteverwaltungsvorgänge unterbrochen, z.B. andere PowerShell-Sitzungen, WMI-Aufrufe und einige Verwaltungstools. Heben Sie daher die Registrierung von PowerShell-Endpunkte nur während geplanter Wartungsfenster auf.

## <a name="next-steps"></a>Nächste Schritte

[Verwenden von JEA](using-jea.md)
