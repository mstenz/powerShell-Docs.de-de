# Details zum Konfigurationsstatus

Das Cmdlet `Get-DscConfigurationStatus` ruft von einem Zielknoten Informationen zum Konfigurationsstatus ab. Ein umfangreiches Objekt wird zurückgegeben, das ausführliche Informationen dazu enthält, ob die Ausführung der Konfiguration erfolgreich war oder nicht. Sie können das Objekt eingehender untersuchen, um Details zur Ausführung der Konfiguration zu ermitteln, wie z. B.:

* Alle fehlerhaften Ressourcen
* Alle Ressourcen, die ein Neustart erfordern
* Metakonfigurationseinstellungen zum Zeitpunkt der Konfigurationsausführung
* usw.

Die folgende Parametergruppe gibt die Statusinformationen zur letzten Konfigurationsausführung zurück:

```powershell
Get-DscConfigurationStatus  [-CimSession <CimSession[]>] 
                            [-ThrottleLimit <int>] 
                            [-AsJob] 
                            [<CommonParameters>]
```
Die folgende Parametergruppe gibt die Statusinformationen zu allen vorherigen Konfigurationsausführungen zurück:

```powershell
Get-DscConfigurationStatus  -All 
                            [-CimSession <CimSession[]>] 
                            [-ThrottleLimit <int>] 
                            [-AsJob] 
                            [<CommonParameters>]
```

## Beispiel

```powershell
PS C:\> $Status = Get-DscConfigurationStatus 

PS C:\> $Status

Status      StartDate               Type            Mode    RebootRequested     NumberOfResources
------      ---------               ----            ----    ---------------     -----------------
Failure     11/24/2015  3:44:56     Consistency     Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName       :   MyService
DependsOn               :   
ModuleName              :   PSDesiredStateConfiguration
ModuleVersion           :   1.1
PsDscRunAsCredential    :   
ResourceID              :   [File]ServiceDll
SourceInfo              :   c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds       :   0.19
Error                   :   SourcePath must be accessible for current configuration. The related file/directory is:
                            \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState              :   
InDesiredState          :   False
InitialState            :   
InstanceName            :   ServiceDll
RebootRequested         :   False
ReosurceName            :   File
StartDate               :   11/24/2015  3:44:56
PSComputerName          :
```<!--HONumber=Mar16_HO2-->
