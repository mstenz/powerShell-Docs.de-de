# Melden des Konfigurationsstatus an zentralem Ort

Detaillierte Informationen zum Status der DSC-Konfiguration können an einen Server gesendet werden, auf dem der DSC-Dienst ausgeführt wird. Dieselben Informationen, die vom Cmdlet „Get-DscConfigurationStatus“ zurückgegeben werden, werden an den DSC-Dienst gesendet. Durch Definieren des Berichtsservers in einer Metakonfiguration wird dieser Status an den Server gesendet, wenn ein Fehler auftritt oder die Konfiguration erfolgreich abgeschlossen wird. Diese Informationen werden gesendet, wenn ein Knoten im Pull- oder Pushmodus konfiguriert ist. Statusinformationen werden in der DSC-Dienstdatenbank gespeichert.

## Beispiel einer Metakonfiguration für den Berichtsstatus
```PowerShell
[DscLocalConfigurationManager()]
Configuration ReportingClientMetaConfig
{
    Settings
        {
            RefreshFrequencyMins = 30
            RefreshMode = "PUSH"
            ConfigurationModeFrequencyMins = 15
            AllowModuleOverwrite = $true
        }

        ReportServerWeb ReportManager
        {
            ServerUrL = "http://localhost:8080/PSDSCPullServer/PSDSCPullserver.svc"
            AllowUnsecureConnection  = $true
        }           
}
```
Mit dem DSC-Dienst wird ein neuer OData-Endpunkt erstellt, der diese Statusinformationen verfügbar macht. Durch Übergeben einer Konfigurations- oder Agent-ID {$guid} an den Endpunkt kann der gesamte Status für einen Knoten gesammelt und analysiert werden.

## Beispiel einer Webanforderung zum Erfassen des Konfigurationsstatus 
```PowerShell
$statusReports = Invoke-WebRequest -Uri "[http://localhost:8080/PSDSCPullserver/PSDSCPullserver.svc/Node(ConfigurationId='$guid')/StatusReport](http://localhost:8080/PSDSCPullserver/psdscpullserver.svc/Node(ConfigurationId='$guid')/StatusReport)s" -UseBasicParsing -UseDefaultCredentials -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" -Headers @{Accept = "application/json"; ProtocolVersion = “1.1”}
```<!--HONumber=Mar16_HO2-->
