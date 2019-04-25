---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Debuggen von DSC-Ressourcen
ms.openlocfilehash: c088e13a25ba31ceebaf52b2d24b5d32b96ae2fc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076802"
---
# <a name="debugging-dsc-resources"></a><span data-ttu-id="a3914-103">Debuggen von DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="a3914-103">Debugging DSC resources</span></span>

> <span data-ttu-id="a3914-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a3914-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="a3914-105">In PowerShell 5.0 wurde ein neues Feature in der Konfiguration für den gewünschten Zustand (Desired State Configuration, DSC) eingeführt, mit dem Sie eine DSC-Ressource beim Anwenden einer Konfiguration debuggen können.</span><span class="sxs-lookup"><span data-stu-id="a3914-105">In PowerShell 5.0, a new feature was introduced in Desired State Configuration (DSC) that allows you to debug a DSC resource as a configuration is being applied.</span></span>

## <a name="enabling-dsc-debugging"></a><span data-ttu-id="a3914-106">Aktivieren des DSC-Debuggens</span><span class="sxs-lookup"><span data-stu-id="a3914-106">Enabling DSC debugging</span></span>
<span data-ttu-id="a3914-107">Bevor Sie eine Ressource debuggen können, müssen Sie das Cmdlet [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) aufrufen, um das Debuggen zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="a3914-107">Before you can debug a resource, you have to enable debugging by calling the [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) cmdlet.</span></span>
<span data-ttu-id="a3914-108">Dieses Cmdlet verfügt über den Pflichtparameter **BreakAll**.</span><span class="sxs-lookup"><span data-stu-id="a3914-108">This cmdlet takes a mandatory parameter, **BreakAll**.</span></span>

<span data-ttu-id="a3914-109">Um zu überprüfen, ob das Debuggen aktiviert wurde, werfen Sie einen Blick auf das Ergebnis eines Aufrufs von [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="a3914-109">You can verify that debugging has been enabled by looking at the result of a call to [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span></span>

<span data-ttu-id="a3914-110">Die folgende PowerShell-Ausgabe zeigt das Ergebnis der Aktivierung des Debuggens an:</span><span class="sxs-lookup"><span data-stu-id="a3914-110">The following PowerShell output shows the result of enabling debugging:</span></span>


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


## <a name="starting-a-configuration-with-debug-enabled"></a><span data-ttu-id="a3914-111">Starten einer Konfiguration mit aktiviertem Debuggen</span><span class="sxs-lookup"><span data-stu-id="a3914-111">Starting a configuration with debug enabled</span></span>
<span data-ttu-id="a3914-112">Um eine DSC-Ressource zu debuggen, starten Sie eine Konfiguration, die diese Ressource aufruft.</span><span class="sxs-lookup"><span data-stu-id="a3914-112">To debug a DSC resource, you start a configuration that calls that resource.</span></span>
<span data-ttu-id="a3914-113">In diesem Beispiel betrachten wir eine einfache Konfiguration, die die Ressource **WindowsFeature** aufruft, um sicherzustellen, dass das Feature „WindowsPowerShellWebAccess“ installiert wurde:</span><span class="sxs-lookup"><span data-stu-id="a3914-113">For this example, we'll look at a simple configuration that calls the **WindowsFeature** resource to ensure that the "WindowsPowerShellWebAccess" feature is installed:</span></span>

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
<span data-ttu-id="a3914-114">Rufen Sie nach dem Kompilieren der Konfiguration [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) auf, um die Konfiguration zu starten.</span><span class="sxs-lookup"><span data-stu-id="a3914-114">After compiling the configuration, start it by calling [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span></span>
<span data-ttu-id="a3914-115">Die Konfiguration wird beendet, wenn der lokale Konfigurations-Manager die erste Ressource in der Konfiguration aufruft.</span><span class="sxs-lookup"><span data-stu-id="a3914-115">The configuration will stop when the Local Configuration Manager (LCM) calls into the first resource in the configuration.</span></span>
<span data-ttu-id="a3914-116">Bei Verwendung der Parameter `-Verbose` und `-Wait` werden in der Ausgabe die Zeilen angezeigt, die Sie eingeben müssen, um das Debuggen zu starten.</span><span class="sxs-lookup"><span data-stu-id="a3914-116">If you use the `-Verbose` and `-Wait` parameters, the output displays the lines you need to enter to start debugging.</span></span>

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
<span data-ttu-id="a3914-117">An diesem Punkt hat der lokale Konfigurations-Manager die Ressource aufgerufen und den ersten Haltepunkt erreicht.</span><span class="sxs-lookup"><span data-stu-id="a3914-117">At this point, the LCM has called the resource, and come to the first break point.</span></span>
<span data-ttu-id="a3914-118">Die letzten drei Zeilen in der Ausgabe zeigen, wie das Ressourcenskript an den Prozess angefügt und das Debuggen gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="a3914-118">The last three lines in the output show you how to attach to the process and start debugging the resource script.</span></span>

## <a name="debugging-the-resource-script"></a><span data-ttu-id="a3914-119">Debuggen des Ressourcenskripts</span><span class="sxs-lookup"><span data-stu-id="a3914-119">Debugging the resource script</span></span>

<span data-ttu-id="a3914-120">Starten Sie eine neue Instanz von PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a3914-120">Start a new instance of the PowerShell ISE.</span></span>
<span data-ttu-id="a3914-121">Geben Sie im Konsolenbereich die letzten drei Zeilen der `Start-DscConfiguration`-Ausgabe als Befehle ein, wobei Sie `<credentials>` durch gültige Benutzeranmeldeinformationen ersetzen.</span><span class="sxs-lookup"><span data-stu-id="a3914-121">In the console pane, enter the last three lines of output from the `Start-DscConfiguration` output as commands, replacing `<credentials>` with valid user credentials.</span></span>
<span data-ttu-id="a3914-122">Jetzt sollte eine Eingabeaufforderung angezeigt werden, die in etwa so aussieht:</span><span class="sxs-lookup"><span data-stu-id="a3914-122">You should now see a prompt that looks similar to:</span></span>

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

<span data-ttu-id="a3914-123">Das Ressourcenskript wird im Skriptfenster geöffnet, und der Debugger wird in der ersten Zeile der Funktion **Test-TargetResource** angehalten (der **Test()**-Methode einer klassenbasierten Ressource).</span><span class="sxs-lookup"><span data-stu-id="a3914-123">The resource script will open in the script pane, and the debugger is stopped at the first line of the **Test-TargetResource** function (the **Test()** method of a class-based resource).</span></span>
<span data-ttu-id="a3914-124">Jetzt können Sie die Debugbefehle in der ISE verwenden, um das Ressourcenskript schrittweise zu durchlaufen, sich die Variablenwerte anzuschauen, die Aufrufliste anzuzeigen, usw.</span><span class="sxs-lookup"><span data-stu-id="a3914-124">Now you can use the debug commands in the ISE to step through the resource script, look at variable values, view the call stack, and so on.</span></span> <span data-ttu-id="a3914-125">Denken Sie daran, dass jede Zeile im Ressourcenskript (oder in der Klasse) als Haltepunkt festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="a3914-125">Remember that every line in the resource script (or class) is set as a break point.</span></span>

## <a name="disabling-dsc-debugging"></a><span data-ttu-id="a3914-126">Deaktivieren des DSC-Debuggens</span><span class="sxs-lookup"><span data-stu-id="a3914-126">Disabling DSC debugging</span></span>

<span data-ttu-id="a3914-127">Nach Aufrufen von [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), führen alle Aufrufe von [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) dazu, dass die Konfiguration unterbrochen und der Debugger gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="a3914-127">After calling [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), all calls to [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) will result in the configuration breaking into the debugger.</span></span> <span data-ttu-id="a3914-128">Damit Konfigurationen wie gewohnt ausgeführt werden können, müssen Sie das Debuggen durch Aufrufen des Cmdlets [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="a3914-128">To allow configurations to run normally, you must disable debugging by calling the [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) cmdlet.</span></span>

><span data-ttu-id="a3914-129">**Hinweis:** Ein Neustart ändert den Debugzustand des LCM nicht.</span><span class="sxs-lookup"><span data-stu-id="a3914-129">**Note:** Rebooting does not change the debug state of the LCM.</span></span> <span data-ttu-id="a3914-130">Wenn das Debuggen aktiviert ist, wird nach einem Neustart weiterhin das Starten einer Konfiguration unterbrochen und der Debugger gestartet.</span><span class="sxs-lookup"><span data-stu-id="a3914-130">If debugging is enabled, starting a configuration will still break into the debugger after a reboot.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3914-131">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a3914-131">See Also</span></span>

- [<span data-ttu-id="a3914-132">Schreiben einer benutzerdefinierten DSC-Ressource mit MOF</span><span class="sxs-lookup"><span data-stu-id="a3914-132">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="a3914-133">Schreiben einer benutzerdefinierten DSC-Ressource mit PowerShell-Klassen</span><span class="sxs-lookup"><span data-stu-id="a3914-133">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
