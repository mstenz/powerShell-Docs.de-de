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
# <a name="get-test-set"></a><span data-ttu-id="636c4-103">Get-Test-Set</span><span class="sxs-lookup"><span data-stu-id="636c4-103">Get-Test-Set</span></span>

><span data-ttu-id="636c4-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="636c4-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

![Get, Test und Set](/media/get-test-set.png)

<span data-ttu-id="636c4-106">PowerShell Desired State Configuration wird erstellt, um eine **erhalten**, **Test**, und **festgelegt** Prozess.</span><span class="sxs-lookup"><span data-stu-id="636c4-106">PowerShell Desired State Configuration is constructed around a **Get**, **Test**, and **Set** process.</span></span> <span data-ttu-id="636c4-107">DSC [Ressourcen](resources.md) jede enthält Methoden, um jeden dieser Vorgänge abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="636c4-107">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span> <span data-ttu-id="636c4-108">In einem [Konfiguration](../configurations/configurations.md), definieren Sie ressourcenblöcke Schlüssel eingeben, die Parameter für einer Ressource werden **erhalten**, **Test**, und **festgelegt** -Methoden.</span><span class="sxs-lookup"><span data-stu-id="636c4-108">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get**, **Test**, and **Set** methods.</span></span>

<span data-ttu-id="636c4-109">Dies ist die Syntax für eine **Service** Ressourcenblock.</span><span class="sxs-lookup"><span data-stu-id="636c4-109">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="636c4-110">Die **Service** Windows-Dienste konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="636c4-110">The **Service** resource configures Windows services.</span></span>

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

<span data-ttu-id="636c4-111">Die **erhalten**, **Test**, und **festgelegt** Methoden der **Service** Ressource müssen Parameterblöcke, die diese Werte zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="636c4-111">The **Get**, **Test**, and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

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
> <span data-ttu-id="636c4-112">Bestimmt die Sprache und die Methode verwendet, um die Ressource definiert werden wie die **erhalten**, **Test**, und **festgelegt** Methoden definiert werden.</span><span class="sxs-lookup"><span data-stu-id="636c4-112">The language and method used to define the resource determines how the **Get**, **Test**, and **Set** methods will be defined.</span></span>

<span data-ttu-id="636c4-113">Da die **Service** Ressource verfügt nur über einen erforderlichen Schlüssel (`Name`), ein **Service** Block-Ressource ist möglicherweise so einfach wie folgt:</span><span class="sxs-lookup"><span data-stu-id="636c4-113">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

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

<span data-ttu-id="636c4-114">Beim Kompilieren der Konfigurations oben werden die Werte, die Sie für einen Schlüssel angeben, in der Datei "MOF" gespeichert, die generiert wird.</span><span class="sxs-lookup"><span data-stu-id="636c4-114">When you compile the Configuration above, the values you specify for a key are stored in the ".mof" file that is generated.</span></span> <span data-ttu-id="636c4-115">Weitere Informationen finden Sie unter [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="636c4-115">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

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

<span data-ttu-id="636c4-116">Bei Anwendung der [lokalen Konfigurations-Managers](../managing-nodes/metaConfig.md) liest den Wert "Spooler" aus der Datei "MOF", und übergeben Sie sie an der `-Name` Parameter der **erhalten**, **Test**, und **festgelegt** Methoden für die Instanz "MyService" von der **Service** Ressource.</span><span class="sxs-lookup"><span data-stu-id="636c4-116">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) will read the value "Spooler" from the ".mof" file, and pass it to the `-Name` parameter of the **Get**, **Test**, and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="636c4-117">Abrufen</span><span class="sxs-lookup"><span data-stu-id="636c4-117">Get</span></span>

<span data-ttu-id="636c4-118">Die **erhalten** Methode einer Ressource, ruft den Zustand der Ressource aus, weil er auf der Ziel-Knoten konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="636c4-118">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="636c4-119">Dieser Zustand wird zurückgegeben, als eine [Hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="636c4-119">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span> <span data-ttu-id="636c4-120">Der Schlüssel, der die **Hashtable** werden die konfigurierbaren Werte oder Parameter, die Ressource akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="636c4-120">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="636c4-121">Die **erhalten** Methode ordnet direkt zu den ["Get-dscconfiguration"](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="636c4-121">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="636c4-122">Beim Aufruf `Get-DSCConfiguration`, der LCM ausgeführt wird die **erhalten** Methode der einzelnen Ressourcen in der gerade angewendeten Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="636c4-122">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="636c4-123">Der LCM nutzt die Schlüsselwerte, die in der Datei "MOF" als Parameter für jede Ressourceninstanz der entsprechenden gespeichert.</span><span class="sxs-lookup"><span data-stu-id="636c4-123">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="636c4-124">Dies ist eine Beispielausgabe einer **Service** Ressource, die der Dienst "Spooler" konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="636c4-124">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

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

<span data-ttu-id="636c4-125">Die Ausgabe zeigt die aktuellen Werteigenschaften kann vom konfiguriert die **Service** Ressource.</span><span class="sxs-lookup"><span data-stu-id="636c4-125">The output shows the current value properties configurable by the **Service** resource.</span></span>

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

## <a name="test"></a><span data-ttu-id="636c4-126">Test</span><span class="sxs-lookup"><span data-stu-id="636c4-126">Test</span></span>

<span data-ttu-id="636c4-127">Die **Test** Methode einer Ressource bestimmt, ob es sich bei Zielknoten derzeit mit der Ressource konform ist *gewünschter advisorzustand*.</span><span class="sxs-lookup"><span data-stu-id="636c4-127">The **Test** method of a resource determines if the target node is currently compliant with the resource's *desired state*.</span></span> <span data-ttu-id="636c4-128">Die **Test** Methodenrückgabe `$True` oder `$False` nur an, ob der Knoten konform ist.</span><span class="sxs-lookup"><span data-stu-id="636c4-128">The **Test** method returns `$True` or `$False` only to indicate whether the Node is compliant.</span></span>
<span data-ttu-id="636c4-129">Beim Aufruf [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), der LCM Aufrufe der **Test** Methode der einzelnen Ressourcen in der gerade angewendeten Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="636c4-129">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="636c4-130">Der LCM nutzt die Schlüsselwerte, die in der Datei "MOF" als Parameter für jede Ressourceninstanz der entsprechenden gespeichert.</span><span class="sxs-lookup"><span data-stu-id="636c4-130">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="636c4-131">Wenn das Ergebnis jeder einzelnen Ressource **Test** ist `$False`, `Test-DSCConfiguration` gibt `$False` gibt an, dass der Knoten nicht kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="636c4-131">If the result of any individual resource's **Test** is `$False`, `Test-DSCConfiguration` returns `$False` indicating that the Node is not compliant.</span></span> <span data-ttu-id="636c4-132">Wenn alle Ressource **Test** Methoden zurückgeben `$True`, `Test-DSCConfiguration` gibt `$True` um anzugeben, dass der Knoten konform ist.</span><span class="sxs-lookup"><span data-stu-id="636c4-132">If all resource's **Test** methods return `$True`, `Test-DSCConfiguration` returns `$True` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="636c4-133">In PowerShell 5.0 ab der `-Detailed` -Parameter hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="636c4-133">Beginning in PowerShell 5.0, the `-Detailed` parameter was added.</span></span> <span data-ttu-id="636c4-134">Angeben von `-Detailed` bewirkt, dass `Test-DSCConfiguration` um ein Objekt mit Auflistungen von Ergebnissen für kompatible und nicht konforme Ressourcen zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="636c4-134">Specifying `-Detailed` causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="636c4-135">Weitere Informationen finden Sie unter [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span><span class="sxs-lookup"><span data-stu-id="636c4-135">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span></span>

## <a name="set"></a><span data-ttu-id="636c4-136">Festlegen</span><span class="sxs-lookup"><span data-stu-id="636c4-136">Set</span></span>

<span data-ttu-id="636c4-137">Die **festgelegt** Methode einer Ressource versucht, die erzwingen, dass den Knoten, die mit der Ressource Konformität *gewünschter advisorzustand*.</span><span class="sxs-lookup"><span data-stu-id="636c4-137">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="636c4-138">Die **festgelegt** Methode soll **Idempotent**, was bedeutet, dass **festgelegt** möglicherweise mehrmals ausführen, und erhalten immer das gleiche Ergebnis ohne Fehler.</span><span class="sxs-lookup"><span data-stu-id="636c4-138">The **Set** method is meant to be **idempotent**, which means that **Set** could be run multiple times and always get the same result without errors.</span></span>  <span data-ttu-id="636c4-139">Beim Ausführen von [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), die der LCM durchläuft jede Ressource in der gerade angewendeten Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="636c4-139">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="636c4-140">Der LCM Schlüsselwerte für die aktuelle Ressourceninstanz aus der Datei "MOF" abgerufen und verwendet sie als Parameter für die **Test** Methode.</span><span class="sxs-lookup"><span data-stu-id="636c4-140">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="636c4-141">Wenn die **Test** Methodenrückgabe `$True`, der Knoten mit der aktuellen Ressource konform ist und die **festgelegt** Methode wird übersprungen.</span><span class="sxs-lookup"><span data-stu-id="636c4-141">If the **Test** method returns `$True`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="636c4-142">Wenn die **Test** gibt `$False`, der Knoten ist nicht kompatibel.</span><span class="sxs-lookup"><span data-stu-id="636c4-142">If the **Test** returns `$False`, the Node is non-compliant.</span></span>  <span data-ttu-id="636c4-143">Der LCM übergibt die Ressource die Schlüsselwerte der Instanz als Parameter an der Ressource **festgelegt** -Methode, den Knoten der Kompatibilität wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="636c4-143">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="636c4-144">Durch Angabe der `-Verbose` und `-Wait` Parameter, Sie können den Fortschritt ansehen der `Start-DSCConfiguration` Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="636c4-144">By specifying the `-Verbose` and `-Wait` parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="636c4-145">In diesem Beispiel ist der Knoten bereits kompatibel.</span><span class="sxs-lookup"><span data-stu-id="636c4-145">In this example, the Node is already compliant.</span></span> <span data-ttu-id="636c4-146">Die `Verbose` Ausgabe gibt an, dass die **festgelegt** Methode wurde übersprungen.</span><span class="sxs-lookup"><span data-stu-id="636c4-146">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="636c4-147">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="636c4-147">See also</span></span>

- [<span data-ttu-id="636c4-148">Azure Automation DSC – Übersicht</span><span class="sxs-lookup"><span data-stu-id="636c4-148">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="636c4-149">Einrichten eines SMB-Pullservers</span><span class="sxs-lookup"><span data-stu-id="636c4-149">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="636c4-150">Konfigurieren eines Pullclients</span><span class="sxs-lookup"><span data-stu-id="636c4-150">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
