---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Get-Test-Set
ms.openlocfilehash: e46710954679bf20f4536c6efbcbd4dafd9e629e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401445"
---
# <a name="get-test-set"></a>Get-Test-Set

>Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

![Get, Test und Set](/media/get-test-set.png)

PowerShell Desired State Configuration wird erstellt, um eine **erhalten**, **Test**, und **festgelegt** Prozess. DSC [Ressourcen](resources.md) jede enthält Methoden, um jeden dieser Vorgänge abzuschließen. In einem [Konfiguration](../configurations/configurations.md), definieren Sie ressourcenblöcke Schlüssel eingeben, die Parameter für einer Ressource werden **erhalten**, **Test**, und **festgelegt** -Methoden.

Dies ist die Syntax für eine **Service** Ressourcenblock. Die **Service** Windows-Dienste konfiguriert.

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

Die **erhalten**, **Test**, und **festgelegt** Methoden der **Service** Ressource müssen Parameterblöcke, die diese Werte zu akzeptieren.

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
> Bestimmt die Sprache und die Methode verwendet, um die Ressource definiert werden wie die **erhalten**, **Test**, und **festgelegt** Methoden definiert werden.

Da die **Service** Ressource verfügt nur über einen erforderlichen Schlüssel (`Name`), ein **Service** Block-Ressource ist möglicherweise so einfach wie folgt:

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

Beim Kompilieren der Konfigurations oben werden die Werte, die Sie für einen Schlüssel angeben, in der Datei "MOF" gespeichert, die generiert wird. Weitere Informationen finden Sie unter [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).

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

Bei Anwendung der [lokalen Konfigurations-Managers](../managing-nodes/metaConfig.md) liest den Wert "Spooler" aus der Datei "MOF", und übergeben Sie sie an der `-Name` Parameter der **erhalten**, **Test**, und **festgelegt** Methoden für die Instanz "MyService" von der **Service** Ressource.

## <a name="get"></a>Abrufen

Die **erhalten** Methode einer Ressource, ruft den Zustand der Ressource aus, weil er auf der Ziel-Knoten konfiguriert ist. Dieser Zustand wird zurückgegeben, als eine [Hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables). Der Schlüssel, der die **Hashtable** werden die konfigurierbaren Werte oder Parameter, die Ressource akzeptiert.

Die **erhalten** Methode ordnet direkt zu den ["Get-dscconfiguration"](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) Cmdlet. Beim Aufruf `Get-DSCConfiguration`, der LCM ausgeführt wird die **erhalten** Methode der einzelnen Ressourcen in der gerade angewendeten Konfiguration. Der LCM nutzt die Schlüsselwerte, die in der Datei "MOF" als Parameter für jede Ressourceninstanz der entsprechenden gespeichert.

Dies ist eine Beispielausgabe einer **Service** Ressource, die der Dienst "Spooler" konfiguriert.

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
                       this service, you won’t be able to print or see your printers.
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

Die Ausgabe zeigt die aktuellen Werteigenschaften kann vom konfiguriert die **Service** Ressource.

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

Die **Test** Methode einer Ressource bestimmt, ob es sich bei Zielknoten derzeit mit der Ressource konform ist *gewünschter advisorzustand*. Die **Test** Methodenrückgabe `$True` oder `$False` nur an, ob der Knoten konform ist.
Beim Aufruf [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), der LCM Aufrufe der **Test** Methode der einzelnen Ressourcen in der gerade angewendeten Konfiguration. Der LCM nutzt die Schlüsselwerte, die in der Datei "MOF" als Parameter für jede Ressourceninstanz der entsprechenden gespeichert.

Wenn das Ergebnis jeder einzelnen Ressource **Test** ist `$False`, `Test-DSCConfiguration` gibt `$False` gibt an, dass der Knoten nicht kompatibel ist. Wenn alle Ressource **Test** Methoden zurückgeben `$True`, `Test-DSCConfiguration` gibt `$True` um anzugeben, dass der Knoten konform ist.

```powershell
Test-DSCConfiguration
```

```output
True
```

In PowerShell 5.0 ab der `-Detailed` -Parameter hinzugefügt wurde. Angeben von `-Detailed` bewirkt, dass `Test-DSCConfiguration` um ein Objekt mit Auflistungen von Ergebnissen für kompatible und nicht konforme Ressourcen zurückzugeben.

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

Weitere Informationen finden Sie unter [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)

## <a name="set"></a>Festlegen

Die **festgelegt** Methode einer Ressource versucht, die erzwingen, dass den Knoten, die mit der Ressource Konformität *gewünschter advisorzustand*. Die **festgelegt** Methode soll **Idempotent**, was bedeutet, dass **festgelegt** möglicherweise mehrmals ausführen, und erhalten immer das gleiche Ergebnis ohne Fehler.  Beim Ausführen von [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), die der LCM durchläuft jede Ressource in der gerade angewendeten Konfiguration. Der LCM Schlüsselwerte für die aktuelle Ressourceninstanz aus der Datei "MOF" abgerufen und verwendet sie als Parameter für die **Test** Methode. Wenn die **Test** Methodenrückgabe `$True`, der Knoten mit der aktuellen Ressource konform ist und die **festgelegt** Methode wird übersprungen. Wenn die **Test** gibt `$False`, der Knoten ist nicht kompatibel.  Der LCM übergibt die Ressource die Schlüsselwerte der Instanz als Parameter an der Ressource **festgelegt** -Methode, den Knoten der Kompatibilität wiederherstellen.

Durch Angabe der `-Verbose` und `-Wait` Parameter, Sie können den Fortschritt ansehen der `Start-DSCConfiguration` Cmdlet. In diesem Beispiel ist der Knoten bereits kompatibel. Die `Verbose` Ausgabe gibt an, dass die **festgelegt** Methode wurde übersprungen.

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

## <a name="see-also"></a>Siehe auch

- [Azure Automation DSC – Übersicht](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [Einrichten eines SMB-Pullservers](../pull-server/pullServerSMB.md)
- [Konfigurieren eines Pullclients](../pull-server/pullClientConfigID.md)
