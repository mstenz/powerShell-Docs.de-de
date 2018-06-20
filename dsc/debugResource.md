---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Debuggen von DSC-Ressourcen
ms.openlocfilehash: 30d49768fc2301b5306d0001e157d60e2e991883
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219105"
---
# <a name="debugging-dsc-resources"></a><span data-ttu-id="6a9d9-103">Debuggen von DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="6a9d9-103">Debugging DSC resources</span></span>

> <span data-ttu-id="6a9d9-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6a9d9-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="6a9d9-105">In PowerShell 5.0 wurde ein neues Feature in DSC (Konfiguration für den gewünschten Zustand) eingeführt, mit dem Sie eine DSC-Ressource beim Anwenden einer Konfiguration debuggen können.</span><span class="sxs-lookup"><span data-stu-id="6a9d9-105">In PowerShell 5.0, a new feature was introduced in Desired State Configuraiton (DSC) that allows you to debug a DSC resource as a configuration is being applied.</span></span>

## <a name="enabling-dsc-debugging"></a><span data-ttu-id="6a9d9-106">Aktivieren des DSC-Debuggens</span><span class="sxs-lookup"><span data-stu-id="6a9d9-106">Enabling DSC debugging</span></span>
<span data-ttu-id="6a9d9-107">Bevor Sie eine Ressource debuggen können, müssen Sie das Cmdlet [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx) aufrufen, um das Debuggen zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="6a9d9-107">Before you can debug a resource, you have to enable debugging by calling the [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx) cmdlet.</span></span>
<span data-ttu-id="6a9d9-108">Dieses Cmdlet verfügt über den Pflichtparameter **BreakAll**.</span><span class="sxs-lookup"><span data-stu-id="6a9d9-108">This cmdlet takes a mandatory parameter, **BreakAll**.</span></span>

<span data-ttu-id="6a9d9-109">Um zu überprüfen, ob das Debuggen aktiviert wurde, werfen Sie einen Blick auf das Ergebnis eines Aufrufs von [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx).</span><span class="sxs-lookup"><span data-stu-id="6a9d9-109">You can verify that debugging has been enabled by looking at the result of a call to [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx).</span></span>

<span data-ttu-id="6a9d9-110">Die folgende PowerShell-Ausgabe zeigt das Ergebnis der Aktivierung des Debuggens an:</span><span class="sxs-lookup"><span data-stu-id="6a9d9-110">The following PowerShell output shows the result of enabling debugging:</span></span>


```powershell
PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
NONE

PS C:\DebugTest> Enable-DscDebug -BreakAll

PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
ForceModuleImport
ResourceScriptBreakAll

PS C:\DebugTest>
```


## <a name="starting-a-configuration-with-debug-enabled"></a><span data-ttu-id="6a9d9-111">Starten einer Konfiguration mit aktiviertem Debuggen</span><span class="sxs-lookup"><span data-stu-id="6a9d9-111">Starting a configuration with debug enabled</span></span>
<span data-ttu-id="6a9d9-112">Um eine DSC-Ressource zu debuggen, starten Sie eine Konfiguration, die diese Ressource aufruft.</span><span class="sxs-lookup"><span data-stu-id="6a9d9-112">To debug a DSC resource, you start a configuration that calls that resource.</span></span>
<span data-ttu-id="6a9d9-113">In diesem Beispiel betrachten wir eine einfache Konfiguration, die die Ressource [WindowsFeature](windowsfeatureResource.md) aufruft, um sicherzustellen, dass das Feature „WindowsPowerShellWebAccess“ installiert wurde:</span><span class="sxs-lookup"><span data-stu-id="6a9d9-113">For this example, we'll look at a simple configuration that calls the [WindowsFeature](windowsfeatureResource.md) resource to ensure that the "WindowsPowerShellWebAccess" feature is installed:</span></span>

```powershell
Configuration PSWebAccess
    {
    Import-DscResource -ModuleName 'PsDesiredStateConfiguration'
    Node localhost
        {
        WindowsFeature PSWA
            {
            Name = 'WindowsPowerShellWebAccess'
            Ensure = 'Present'
            }
        }
    }
PSWebAccess
```
<span data-ttu-id="6a9d9-114">Rufen Sie nach dem Kompilieren der Konfiguration [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) auf, um die Konfiguration zu starten.</span><span class="sxs-lookup"><span data-stu-id="6a9d9-114">After compiling the configuration, start it by calling [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx).</span></span>
<span data-ttu-id="6a9d9-115">Die Konfiguration wird beendet, wenn der lokale Konfigurations-Manager die erste Ressource in der Konfiguration aufruft.</span><span class="sxs-lookup"><span data-stu-id="6a9d9-115">The configuration will stop when the Local Configuration Manager (LCM) calls into the first resource in the configuration.</span></span>
<span data-ttu-id="6a9d9-116">Bei Verwendung der Parameter `-Verbose` und `-Wait` werden in der Ausgabe die Zeilen angezeigt, die Sie eingeben müssen, um das Debuggen zu starten.</span><span class="sxs-lookup"><span data-stu-id="6a9d9-116">If you use the `-Verbose` and `-Wait` parameters, the output displays the lines you need to enter to start debugging.</span></span>

```powershell
Start-DscConfiguration .\PSWebAccess -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfiguration
Manager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Set      ]
WARNING: [TEST-SRV]:                            [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode.  Resource script processing will
be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [TEST-SRV]:                            [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateCo
nfiguration\DscResources\MSFT_RoleResource\MSFT_RoleResource.psm1 in force mode.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Resource ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]: LCM:  [ Start  Test     ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]:                            [[WindowsFeature]PSWA] Importing the module MSFT_RoleResource in force mode.
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach.
Use the following commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```
<span data-ttu-id="6a9d9-117">An diesem Punkt hat der lokale Konfigurations-Manager die Ressource aufgerufen und den ersten Haltepunkt erreicht.</span><span class="sxs-lookup"><span data-stu-id="6a9d9-117">At this point, the LCM has called the resource, and come to the first break point.</span></span>
<span data-ttu-id="6a9d9-118">Die letzten drei Zeilen in der Ausgabe zeigen, wie das Ressourcenskript an den Prozess angefügt und das Debuggen gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="6a9d9-118">The last three lines in the output show you how to attach to the process and start debugging the resource script.</span></span>

## <a name="debugging-the-resource-script"></a><span data-ttu-id="6a9d9-119">Debuggen des Ressourcenskripts</span><span class="sxs-lookup"><span data-stu-id="6a9d9-119">Debugging the resource script</span></span>

<span data-ttu-id="6a9d9-120">Starten Sie eine neue Instanz von PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="6a9d9-120">Start a new instance of the PowerShell ISE.</span></span>
<span data-ttu-id="6a9d9-121">Geben Sie im Konsolenbereich die letzten drei Zeilen der `Start-DscConfiguration`-Ausgabe als Befehle ein, wobei Sie `<credentials>` durch gültige Benutzeranmeldeinformationen ersetzen.</span><span class="sxs-lookup"><span data-stu-id="6a9d9-121">In the console pane, enter the last three lines of output from the `Start-DscConfiguration` output as commands, replacing `<credentials>` with valid user credentials.</span></span>
<span data-ttu-id="6a9d9-122">Jetzt sollte eine Eingabeaufforderung angezeigt werden, die in etwa so aussieht:</span><span class="sxs-lookup"><span data-stu-id="6a9d9-122">You should now see a prompt that looks similar to:</span></span>

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

<span data-ttu-id="6a9d9-123">Das Ressourcenskript wird im Skriptfenster geöffnet, und der Debugger wird in der ersten Zeile der Funktion **Test-TargetResource** angehalten (der **Test()**-Methode einer klassenbasierten Ressource).</span><span class="sxs-lookup"><span data-stu-id="6a9d9-123">The resource script will open in the script pane, and the debugger is stopped at the first line of the **Test-TargetResource** function (the **Test()** method of a class-based resource).</span></span>
<span data-ttu-id="6a9d9-124">Jetzt können Sie die Debugbefehle in der ISE verwenden, um das Ressourcenskript schrittweise zu durchlaufen, sich die Variablenwerte anzuschauen, die Aufrufliste anzuzeigen, usw.</span><span class="sxs-lookup"><span data-stu-id="6a9d9-124">Now you can use the debug commands in the ISE to step through the resource script, look at variable values, view the call stack, and so on.</span></span>
<span data-ttu-id="6a9d9-125">Weitere Informationen zum Debuggen in PowerShell ISE finden Sie unter [So wird's gemacht: Debuggen von Skripts in Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819480.aspx).</span><span class="sxs-lookup"><span data-stu-id="6a9d9-125">For information about debugging in the PowerShell ISE, see [How to Debug Scripts in Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819480.aspx).</span></span>
<span data-ttu-id="6a9d9-126">Denken Sie daran, dass jede Zeile im Ressourcenskript (oder in der Klasse) als Haltepunkt festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="6a9d9-126">Remember that every line in the resource script (or class) is set as a break point.</span></span>

## <a name="disabling-dsc-debugging"></a><span data-ttu-id="6a9d9-127">Deaktivieren des DSC-Debuggens</span><span class="sxs-lookup"><span data-stu-id="6a9d9-127">Disabling DSC debugging</span></span>

<span data-ttu-id="6a9d9-128">Nach Aufrufen von [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx), führen alle Aufrufe von [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) dazu, dass die Konfiguration unterbrochen und der Debugger gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="6a9d9-128">After calling [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx), all calls to [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) will result in the configuration breaking into the debugger.</span></span> <span data-ttu-id="6a9d9-129">Damit Konfigurationen wie gewohnt ausgeführt werden können, müssen Sie das Debuggen durch Aufrufen des Cmdlets [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx) deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="6a9d9-129">To allow configurations to run normally, you must disable debugging by calling the [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx) cmdlet.</span></span>

><span data-ttu-id="6a9d9-130">**Hinweis:** Ein Neustart ändert den Debugzustand des LCM nicht.</span><span class="sxs-lookup"><span data-stu-id="6a9d9-130">**Note:** Rebooting does not change the debug state of the LCM.</span></span> <span data-ttu-id="6a9d9-131">Wenn das Debuggen aktiviert ist, wird nach einem Neustart weiterhin das Starten einer Konfiguration unterbrochen und der Debugger gestartet.</span><span class="sxs-lookup"><span data-stu-id="6a9d9-131">If debugging is enabled, starting a configuration will still break into the debugger after a reboot.</span></span>


## <a name="see-also"></a><span data-ttu-id="6a9d9-132">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6a9d9-132">See Also</span></span>
- [<span data-ttu-id="6a9d9-133">Schreiben einer benutzerdefinierten DSC-Ressource mit MOF</span><span class="sxs-lookup"><span data-stu-id="6a9d9-133">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="6a9d9-134">Schreiben einer benutzerdefinierten DSC-Ressource mit PowerShell-Klassen</span><span class="sxs-lookup"><span data-stu-id="6a9d9-134">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)