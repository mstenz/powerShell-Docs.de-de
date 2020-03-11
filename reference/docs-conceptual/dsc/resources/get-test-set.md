---
ms.date: 12/12/2018
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: Get-Test-Set
ms.openlocfilehash: bf409f71c07c434fbc7389789e16575868d21b42
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278415"
---
# <a name="get-test-set"></a>Get-Test-Set

>Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

![Get, Test und Set](media/get-test-set/get-test-set.png)

PowerShell Desired State Configuration ist um einen **Get**-, **Test**- und **Set**-Prozess herum konstruiert. Die DSC-[Ressourcen](resources.md) enthalten Methoden, um jeden dieser Vorgänge abzuschließen. In einer [Konfiguration](../configurations/configurations.md) definieren Sie Ressourcenblöcke, um Schlüssel auszufüllen, die Parameter für **Get**-, **Test**- und **Set**-Methoden einer Ressource werden.

Dies ist die Syntax für einen **Service**-Ressourcenblock. Die **Service**-Ressource konfiguriert Windows-Dienste.

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

Die Parameterblöcke der **Get**-, **Test**- und **Set**-Methoden der **Service**-Ressource akzeptieren diese Werte.

```powershell
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [System.String]
        $Name,

        [System.String]
        [ValidateSet("Automatic", "Manual", "Disabled")]
        $StartupType,

        [System.String]
        [ValidateSet("LocalSystem", "LocalService", "NetworkService")]
        $BuiltInAccount,

        [System.Management.Automation.PSCredential]
        [ValidateNotNull()]
        $Credential,

        [System.String]
        [ValidateSet("Running", "Stopped")]
        $State="Running",

        [System.String]
        [ValidateNotNullOrEmpty()]
        $DisplayName,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Description,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Path,

        [System.String[]]
        [ValidateNotNullOrEmpty()]
        $Dependencies,

        [System.String]
        [ValidateSet("Present", "Absent")]
        $Ensure="Present"
    )
```

> [!NOTE]
> Die zum Definieren der Ressource verwendete Sprache und Methode bestimmt, wie die **Get**-, **Test**- und **Set**-Methoden definiert werden.

Da die **Service**-Ressource nur einen einzigen Schlüssel (`Name`) benötigt, könnte eine **Service**-Blockressource so einfach sein wie folgt:

```powershell
Configuration TestConfig
{
    Import-DSCResource -Name Service
    Node localhost
    {
        Service "MyService"
        {
            Name = "Spooler"
        }
    }
}
```

Beim Kompilieren der obigen Konfiguration werden die Werte, die Sie für einen Schlüssel angeben, in der generierten MOF-Datei gespeichert. Weitere Informationen finden Sie unter [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).

```
instance of MSFT_ServiceResource as $MSFT_ServiceResource1ref
{
SourceInfo = "::5::1::Service";
 ModuleName = "PsDesiredStateConfiguration";
 ResourceID = "[Service]MyService";
 Name = "Spooler";

ModuleVersion = "1.0";

 ConfigurationName = "Test";

};
```

Bei Anwendung liest der [lokale Konfigurations-Manager](../managing-nodes/metaConfig.md) (Local Configuration Manager, LCM) den Wert „Spooler“ aus der MOF-Datei und übergibt ihn dem `-Name`-Parameter der **Get**-, **Test**- und **Set**-Methode für die Instanz „MyService“ der **Service**-Ressource.

## <a name="get"></a>Herunterladen

Die **Get**-Methode einer Ressource ruft den Status der Ressource ab, wenn sie auf dem Zielknoten konfiguriert wird. Dieser Status wird als [Hashtabelle](/powershell/module/microsoft.powershell.core/about/about_hash_tables) zurückgegeben. Die Schlüssel der **Hashtabelle** sind die konfigurierbaren Werte oder Parameter, die die Ressource akzeptiert.

Die **Get**-Methode wird direkt dem [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration)-Cmdlet zugeordnet. Beim Aufruf von `Get-DSCConfiguration` führt der LCM die **Get**-Methoden der einzelnen Ressourcen in der gerade angewendeten Konfiguration aus. Der LCM nutzt die in der MOF-Datei gespeicherten Schlüsselwerte als Parameter für die jeweilige entsprechende Ressourceninstanz.

Dies ist eine Beispielausgabe einer **Service**-Ressource, die den „Spooler“-Dienst konfiguriert.

```output
ConfigurationName    : Test
DependsOn            :
ModuleName           : PsDesiredStateConfiguration
ModuleVersion        : 1.1
PsDscRunAsCredential :
ResourceId           : [Service]Spooler
SourceInfo           :
BuiltInAccount       : LocalSystem
Credential           :
Dependencies         : {RPCSS, http}
Description          : This service spools print jobs and handles interaction with the printer.  If you turn off
                       this service, you won't be able to print or see your printers.
DisplayName          : Print Spooler
Ensure               :
Name                 : Spooler
Path                 : C:\WINDOWS\System32\spoolsv.exe
StartupType          : Automatic
State                : Running
Status               :
PSComputerName       :
CimClassName         : MSFT_ServiceResource
```

Die Ausgabe zeigt die aktuellen, mit der **Service**-Ressource konfigurierbaren Werteigenschaften.

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

## <a name="test"></a>Test

Die **Test**-Methode einer Ressource bestimmt, ob der Zielknoten derzeit mit dem *gewünschten Status* der Ressource konform ist. Die **Test**-Methode gibt `$True` oder `$False` nur zurück, um anzuzeigen, ob der Knoten konform ist.
Beim Aufruf von [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) ruft der LCM die **Test**-Methoden der einzelnen Ressourcen in der gerade angewendeten Konfiguration auf. Der LCM nutzt die in der MOF-Datei gespeicherten Schlüsselwerte als Parameter für die jeweilige entsprechende Ressourceninstanz.

Wenn das Ergebnis von **Test** einer beliebigen einzelnen Ressource `$False` ist, gibt `Test-DSCConfiguration``$False` zurück, um anzugeben, dass der Knoten nicht konform ist. Wenn die **Test**-Methoden aller Ressourcen `$True` zurückgeben, gibt `Test-DSCConfiguration``$True` zurück, um anzugeben, dass der Knoten konform ist.

```powershell
Test-DSCConfiguration
```

```output
True
```

Ab PowerShell 5.0 wurde der `-Detailed`-Parameter hinzugefügt. Die Angabe von `-Detailed` bewirkt, dass `Test-DSCConfiguration` ein Objekt zurückgibt, das Sammlungen von Ergebnissen für konforme und nicht konforme Ressourcen enthält.

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

Weitere Informationen finden Sie unter [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

## <a name="set"></a>Set

Die **Set**-Methode einer Ressource versucht, die Konformität des Knotens mit dem *gewünschten Status* der Ressource zu erzwingen. Die **Set**-Methode soll **idempotent** sein, was bedeutet, dass **Set** mehrmals ausgeführt werden und immer ohne Fehler das gleiche Ergebnis erzielen könnte.  Beim Aufruf von [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration) durchläuft der LCM die einzelnen Ressourcen in der gerade angewendeten Konfiguration. Der LCM ruft Schlüsselwerte für die aktuelle Ressourceninstanz aus der MOF-Datei ab und verwendet sie als Parameter für die **Test**-Methode. Wenn die **Test**-Methode `$True` zurückgibt, ist der Knoten mit der aktuellen Ressource konform, und die **Set**-Methode wird übersprungen. Wenn der **Test**`$False` zurückgibt, ist der Knoten nicht konform.  Der LCM übergibt die Schlüsselwerte der Ressourceninstanz als Parameter an die **Set**-Methode der Ressource und stellt dabei die Konformität des Knotens wieder her.

Durch Angabe der Parameter `-Verbose` und `-Wait` können Sie den Fortschritt des `Start-DSCConfiguration`-Cmdlets verfolgen. In diesem Beispiel ist der Knoten bereits konform. Die `Verbose`-Ausgabe gibt an, dass die **Set**-Methode übersprungen wurde.

```
PS> Start-DSCConfiguration -Verbose -Wait -UseExisting

VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
ApplyConfiguration,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer SERVER01 with user sid
S-1-5-21-124525095-708259637-1543119021-1282804.
VERBOSE: [SERVER01]:                            [] Starting consistency engine.
VERBOSE: [SERVER01]:                            [] Checking consistency for current configuration.
VERBOSE: [SERVER01]:                            [DSCEngine] Importing the module
C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\DscResources\MSFT_ServiceResource\MSFT
_ServiceResource.psm1 in force mode.
VERBOSE: [SERVER01]: LCM:  [ Start  Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ Start  Test     ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [[Service]Spooler] Importing the module MSFT_ServiceResource in
force mode.
VERBOSE: [SERVER01]: LCM:  [ End    Test     ]  [[Service]Spooler]  in 0.2540 seconds.
VERBOSE: [SERVER01]: LCM:  [ Skip   Set      ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ End    Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [] Consistency check completed.
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Time taken for configuration job to complete is 1.379 seconds
```

## <a name="see-also"></a>Weitere Informationen

- [Azure Automation DSC – Übersicht](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Einrichten eines SMB-Pullservers](../pull-server/pullServerSMB.md)
- [Konfigurieren eines Pullclients](../pull-server/pullClientConfigID.md)
