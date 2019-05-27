---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Bekannte Probleme und Einschränkungen bei DSC (Desired State Configuration)
ms.openlocfilehash: 6faf24795d14a93f265943029d9f6f1388f32263
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855475"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="90230-103">Bekannte Probleme und Einschränkungen bei DSC (Desired State Configuration)</span><span class="sxs-lookup"><span data-stu-id="90230-103">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="90230-104">Breaking Change: Zertifikate zum Verschlüsseln und Entschlüsseln von Kennwörtern in DSC-Konfigurationen funktionieren nach der Installation von WMF 5.0 RTM ggf. nicht</span><span class="sxs-lookup"><span data-stu-id="90230-104">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="90230-105">In den Versionen WMF 4.0 und WMF 5.0 Preview lässt DSC in der Konfiguration keine Kennwörter mit mehr als 121 Zeichen zu.</span><span class="sxs-lookup"><span data-stu-id="90230-105">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="90230-106">DSC erzwang das Verwenden kurzer Kennwörter, auch wenn längere und sichere Kennwörter gewünscht waren.</span><span class="sxs-lookup"><span data-stu-id="90230-106">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="90230-107">Dank dieser wichtigen Änderungen können Kennwörter in der DSC-Konfiguration nun eine beliebige Länge haben.</span><span class="sxs-lookup"><span data-stu-id="90230-107">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="90230-108">**Lösung:** Erstellen Sie das Zertifikat mit der Schlüsselverwendung für die Daten- oder Schlüsselchiffrierung und der erweiterten Schlüsselverwendung für die Dokumentverschlüsselung (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="90230-108">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="90230-109">Weitere Informationen finden Sie unter [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span><span class="sxs-lookup"><span data-stu-id="90230-109">For more information, see [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span></span>

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="90230-110">DSC-Cmdlets funktionieren nach Installation von WMF 5.0 RTM ggf. nicht mehr</span><span class="sxs-lookup"><span data-stu-id="90230-110">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="90230-111">`Start-DscConfiguration` und andere DSC-Cmdlets funktionieren ggf. nach der Installation von WMF 5.0 RTM nicht mehr, und der folgende Fehler wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="90230-111">`Start-DscConfiguration` and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>

```Output
LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
+ CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : MI RESULT 6
+ PSComputerName : localhost
```

<span data-ttu-id="90230-112">**Lösung:** Löschen Sie „DSCEngineCache.mof“, indem Sie den folgenden Befehl mit erhöhten Rechten in einer PowerShell-Sitzung ausführen (Als Administrator ausführen):</span><span class="sxs-lookup"><span data-stu-id="90230-112">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="90230-113">DSC-Cmdlets funktionieren ggf. nicht, wenn die WMF 5.0 RTM-Version zusätzlich zur WMF 5.0 Production Preview-Version installiert wird</span><span class="sxs-lookup"><span data-stu-id="90230-113">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>

<span data-ttu-id="90230-114">**Lösung:** Führen Sie den folgenden Befehl mit erhöhten Rechten in einer PowerShell-Sitzung aus (Als Administrator ausführen):</span><span class="sxs-lookup"><span data-stu-id="90230-114">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>

```powershell
mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="90230-115">Der LCM kann bei Verwenden von „Get-DscConfiguration“ im Debugmodus instabil werden</span><span class="sxs-lookup"><span data-stu-id="90230-115">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>

<span data-ttu-id="90230-116">Wenn der LCM im Debugmodus ist, kann das Drücken von STRG+C zum Bearbeiten von `Get-DscConfiguration` bewirken, dass der LCM so instabil wird, dass die Mehrheit der DSC-Cmdlets nicht funktioniert.</span><span class="sxs-lookup"><span data-stu-id="90230-116">If LCM is in DebugMode, pressing CTRL+C to stop the processing of `Get-DscConfiguration` can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="90230-117">**Lösung:** Drücken Sie während des Debuggens des Cmdlets `Get-DscConfiguration` nicht STRG+C.</span><span class="sxs-lookup"><span data-stu-id="90230-117">**Resolution:** Don’t press CTRL+C while debugging `Get-DscConfiguration` cmdlet.</span></span>

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a><span data-ttu-id="90230-118">Das Cmdlet „Stop-DscConfiguration“ reagiert im Debugmodus möglicherweise nicht.</span><span class="sxs-lookup"><span data-stu-id="90230-118">Stop-DscConfiguration may not respond in DebugMode</span></span>

<span data-ttu-id="90230-119">Wenn der lokale Konfigurations-Manager im Debugmodus ist, reagiert `Stop-DscConfiguration` möglicherweise nicht beim Versuch, einen Vorgang zu beenden, der mit `Get-DscConfiguration` gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="90230-119">If LCM is in DebugMode, `Stop-DscConfiguration` may not respond while trying to stop an operation started by `Get-DscConfiguration`</span></span>

<span data-ttu-id="90230-120">**Lösung:** Beenden Sie das Debuggen des mit `Get-DscConfiguration` gestarteten Vorgangs gemäß der Anweisungen unter [Debuggen von DSC-Ressourcen](/powershell/dsc/troubleshooting/debugResource).</span><span class="sxs-lookup"><span data-stu-id="90230-120">**Resolution:** Finish the debugging of the operation started by `Get-DscConfiguration` as outlined in [Debugging DSC resources](/powershell/dsc/troubleshooting/debugResource).</span></span>

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="90230-121">Im Debugmodus werden keine ausführlichen Fehlermeldungen angezeigt</span><span class="sxs-lookup"><span data-stu-id="90230-121">No Verbose Error Messages are shown in DebugMode</span></span>

<span data-ttu-id="90230-122">Wenn der LCM im **DebugMode** (Debugmodus) ist, werden von DSC-Ressourcen keine ausführlichen Fehlermeldungen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="90230-122">If LCM is in **DebugMode**, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="90230-123">**Lösung:** Deaktivieren Sie den **Debugmodus**, um ausführliche Meldungen der Ressource anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="90230-123">**Resolution:** Disable **DebugMode** to see verbose messages from the resource</span></span>

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="90230-124">„Invoke-DscResource“-Vorgänge können vom Cmdlet „Get-DscConfigurationStatus“ nicht abgerufen werden</span><span class="sxs-lookup"><span data-stu-id="90230-124">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="90230-125">Nach Verwenden des Cmdlets `Invoke-DscResource` zum direkten Aufrufen von Methoden einer Ressource können die Datensätze eines solchen Vorgangs später nicht mit `Get-DscConfigurationStatus` abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="90230-125">After using `Invoke-DscResource` cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through `Get-DscConfigurationStatus`.</span></span>

<span data-ttu-id="90230-126">**Lösung:** Keine.</span><span class="sxs-lookup"><span data-stu-id="90230-126">**Resolution:** None.</span></span>

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="90230-127">„Get-DscConfigurationStatus“ gibt Pullzyklusvorgänge mit dem Typ **Consistency** zurück</span><span class="sxs-lookup"><span data-stu-id="90230-127">Get-DscConfigurationStatus returns pull cycle operations as type **Consistency**</span></span>

<span data-ttu-id="90230-128">Wenn ein Knoten auf den PULL-Aktualisierungsmodus festgelegt ist, meldet das Cmdlet `Get-DscConfigurationStatus` den Vorgangstyp als **Consistency** anstatt als *Initial*.</span><span class="sxs-lookup"><span data-stu-id="90230-128">When a node is set to PULL refresh mode, for each pull operation performed, `Get-DscConfigurationStatus` cmdlet reports the operation type as **Consistency** instead of *Initial*</span></span>

<span data-ttu-id="90230-129">**Lösung:** Keine.</span><span class="sxs-lookup"><span data-stu-id="90230-129">**Resolution:** None.</span></span>

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="90230-130">Das Cmdlet „Invoke-DscResource“ gibt Meldungen nicht in der Reihenfolge ihrer Erstellung zurück</span><span class="sxs-lookup"><span data-stu-id="90230-130">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>

<span data-ttu-id="90230-131">Das Cmdlet `Invoke-DscResource` gibt ausführliche, Warn- und Fehlermeldungen nicht in der Reihenfolge zurück, in der sie vom LCM oder der DSC-Ressource erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="90230-131">The `Invoke-DscResource` cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="90230-132">**Lösung:** Keine.</span><span class="sxs-lookup"><span data-stu-id="90230-132">**Resolution:** None.</span></span>

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="90230-133">Bei Verwendung mit „Invoke-DscResource“ ist das Debuggen von DSC-Ressourcen nicht einfach</span><span class="sxs-lookup"><span data-stu-id="90230-133">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>

<span data-ttu-id="90230-134">Wenn der LCM im Debugmodus ausgeführt wird, bietet das Cmdlet `Invoke-DscResource` keine Informationen zum Runspace, mit dem zum Debuggen eine Verbindung hergestellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="90230-134">When LCM is running in debug mode, `Invoke-DscResource` cmdlet does not give information about runspace to connect to for debugging.</span></span> <span data-ttu-id="90230-135">Weitere Informationen finden Sie unter [Debuggen von DSC-Ressourcen](/powershell/dsc/troubleshooting/debugResource).</span><span class="sxs-lookup"><span data-stu-id="90230-135">For more information, see [Debugging DSC resources](/powershell/dsc/troubleshooting/debugResource).</span></span>

<span data-ttu-id="90230-136">**Lösung:** Ermitteln und Anfügen an den Runspace mithilfe der Cmdlets `Get-PSHostProcessInfo`, `Enter-PSHostProcess`, `Get-Runspace` und `Debug-Runspace` zum Debuggen der DSC-Ressource.</span><span class="sxs-lookup"><span data-stu-id="90230-136">**Resolution:** Discover and attach to the runspace using cmdlets `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` and `Debug-Runspace` to debug the DSC resource.</span></span>

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName    ProcessId AppDomainName
-----------    --------- -------------
powershell          3932 DefaultAppDomain
powershell_ise      2304 DefaultAppDomain
WmiPrvSE            3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name       ComputerName Type  State  Availability
-- ----       ------------ ----  -----  ------------
 2 Runspace2  localhost    Local Opened InBreakpoint
 5 RemoteHost localhost    Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="90230-137">Verschiedene Teilkonfigurationsdokumente für denselben Knoten dürfen keine identischen Ressourcennamen aufweisen</span><span class="sxs-lookup"><span data-stu-id="90230-137">Various Partial Configuration documents for same node cannot have identical resource names</span></span>

<span data-ttu-id="90230-138">Wenn mehrere Teilkonfigurationen, die auf einem einzelnen Knoten bereitgestellt sind, identische Ressourcennamen aufweisen, kann ein Laufzeitfehler auftreten.</span><span class="sxs-lookup"><span data-stu-id="90230-138">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="90230-139">**Lösung:** Verwenden Sie auch für die gleichen Ressourcen in verschiedenen Teilkonfigurationen verschiedene Namen.</span><span class="sxs-lookup"><span data-stu-id="90230-139">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="90230-140">„Start-DscConfiguration –UseExisting“ funktioniert nicht mit „-Credential“</span><span class="sxs-lookup"><span data-stu-id="90230-140">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>

<span data-ttu-id="90230-141">Bei Verwendung von `Start-DscConfiguration` mit dem **UseExisting** wird der Parameter **Credential** ignoriert.</span><span class="sxs-lookup"><span data-stu-id="90230-141">When using `Start-DscConfiguration` with **UseExisting** parameter, the **Credential** parameter is ignored.</span></span> <span data-ttu-id="90230-142">DSC verwendet die Standardprozessidentität, um den Vorgang fortzusetzen.</span><span class="sxs-lookup"><span data-stu-id="90230-142">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="90230-143">Dies bewirkt einen Fehler, wenn für das Fortsetzen auf einem Remoteknoten andere Anmeldeinformationen benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="90230-143">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="90230-144">**Lösung:** Verwenden Sie eine CIM-Sitzung für DSC-Remotevorgänge:</span><span class="sxs-lookup"><span data-stu-id="90230-144">**Resolution:** Use CIM session for remote DSC operations:</span></span>

```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="90230-145">IPv6-Adressen als Knotennamen in DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="90230-145">IPv6 Addresses as Node Names in DSC configurations</span></span>

<span data-ttu-id="90230-146">IPv6-Adressen als Knotennamen in DSC-Konfigurationsskripts werden in dieser Version nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="90230-146">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="90230-147">**Lösung:** Keine.</span><span class="sxs-lookup"><span data-stu-id="90230-147">**Resolution:** None.</span></span>

## <a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="90230-148">Debuggen von `Class-Based` DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="90230-148">Debugging of `Class-Based` DSC Resources</span></span>

<span data-ttu-id="90230-149">Das Debuggen klassenbasierter DSC-Ressourcen wird in dieser Version nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="90230-149">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="90230-150">**Lösung:** Keine.</span><span class="sxs-lookup"><span data-stu-id="90230-150">**Resolution:** None.</span></span>

## <a name="variables-and-functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="90230-151">Variablen und Funktionen, die im Bereich „$script“ in klassenbasierten DSC-Ressourcen definiert werden, bleiben bei mehreren Aufrufen einer DSC-Ressource nicht erhalten.</span><span class="sxs-lookup"><span data-stu-id="90230-151">Variables and functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span>

<span data-ttu-id="90230-152">Mehrere aufeinander folgende Aufrufe von `Start-DSCConfiguration` misslingen, wenn die Konfiguration klassenbasierte Ressourcen mit im Bereich `$script` definierten Variablen oder Funktionen verwendet.</span><span class="sxs-lookup"><span data-stu-id="90230-152">Multiple consecutive calls to `Start-DSCConfiguration` fails if the configuration is using any class-based resource which has variables or functions defined in `$script` scope.</span></span>

<span data-ttu-id="90230-153">**Lösung:** Definieren Sie alle Variablen und Funktionen in der DSC-Ressourcenklasse selbst.</span><span class="sxs-lookup"><span data-stu-id="90230-153">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="90230-154">Keine Variablen/Funktionen aus dem Bereich `$script`.</span><span class="sxs-lookup"><span data-stu-id="90230-154">No `$script` scope variables/functions.</span></span>

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="90230-155">Debuggen von DSC-Ressourcen, wenn eine Ressource „PSDscRunAsCredential“ verwendet</span><span class="sxs-lookup"><span data-stu-id="90230-155">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>

<span data-ttu-id="90230-156">Das Debuggen von DSC-Ressourcen, wenn eine Ressource **PSDscRunAsCredential** in der Konfiguration verwendet, wird in dieser Version nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="90230-156">DSC Resource debugging when a resource is using the **PSDscRunAsCredential** property in the configuration is not supported in this release.</span></span>

<span data-ttu-id="90230-157">**Lösung:** Keine.</span><span class="sxs-lookup"><span data-stu-id="90230-157">**Resolution:** None.</span></span>

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="90230-158">„PsDscRunAsCredential“ wird für zusammengesetzte DSC-Ressourcen nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="90230-158">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>

<span data-ttu-id="90230-159">**Lösung:** Verwenden Sie, falls verfügbar, die Eigenschaft „Credential“.</span><span class="sxs-lookup"><span data-stu-id="90230-159">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="90230-160">Beispiel für „ServiceSet“ und „WindowsFeatureSet“</span><span class="sxs-lookup"><span data-stu-id="90230-160">Example ServiceSet and WindowsFeatureSet</span></span>

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="90230-161">„-Syntax“ von „Get-DscResource“ spiegelt „PsDscRunAsCredential“ nicht ordnungsgemäß wider</span><span class="sxs-lookup"><span data-stu-id="90230-161">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly</span></span>

<span data-ttu-id="90230-162">Der Parameter **Syntax** spiegelt **PsDscRunAsCredential** nicht ordnungsgemäß wider, wenn ihn eine Ressource als erforderlich kennzeichnet oder nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="90230-162">The **Syntax** parameter does not reflect **PsDscRunAsCredential** correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="90230-163">**Lösung:** Keine.</span><span class="sxs-lookup"><span data-stu-id="90230-163">**Resolution:** None.</span></span> <span data-ttu-id="90230-164">Die Erstellungskonfiguration in ISE spiegelt jedoch ordnungsgemäße Metadaten zur **PsDscRunAsCredential**-Eigenschaft wider, wenn IntelliSense verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="90230-164">However, authoring configuration in ISE reflects correct metadata about **PsDscRunAsCredential** property when using IntelliSense.</span></span>

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="90230-165">„WindowsOptionalFeature“ ist unter Windows 7 nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="90230-165">WindowsOptionalFeature is not available in Windows 7</span></span>

<span data-ttu-id="90230-166">Die DSC-Ressource **WindowsOptionalFeature** ist unter Windows 7 nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="90230-166">The **WindowsOptionalFeature** DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="90230-167">Diese Ressource erfordert das DISM-Modul und DISM-Cmdlets, die ab Windows 8 und in neueren Versionen des Windows-Betriebssystems verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="90230-167">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="90230-168">Bei klassenbasierten DSC-Ressourcen funktioniert „Import-DscResource-ModuleVersion“ möglicherweise nicht wie erwartet</span><span class="sxs-lookup"><span data-stu-id="90230-168">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>

<span data-ttu-id="90230-169">Falls der Kompilierungsknoten mehrere Versionen eines klassenbasierten DSC-Ressourcenmoduls aufweist, wählt `Import-DscResource -ModuleVersion` nicht die angegebene Version aus und folgender Kompilierungsfehler wird zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="90230-169">If the compilation node has multiple versions of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```Output
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s):
 "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="90230-170">**Lösung:** Importieren Sie die erforderliche Version, indem Sie das **ModuleSpecification**-Objekt auf den **ModuleName**-Parameter definieren, mit dem Schlüssel **RequiredVersion** festgelegt wie folgt :</span><span class="sxs-lookup"><span data-stu-id="90230-170">**Resolution:** Import the required version by defining the **ModuleSpecification** object to the **ModuleName** parameter with **RequiredVersion** key specified as follows:</span></span>

```powershell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="90230-171">Bei einigen DSC-Ressourcen, wie z. B. der Registrierungsressource, kann das Starten der Verarbeitung der Anforderung lange dauern.</span><span class="sxs-lookup"><span data-stu-id="90230-171">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>

<span data-ttu-id="90230-172">**Lösung 1:** Erstellen Sie eine geplante Aufgabe zum regelmäßigen Bereinigen des folgenden Ordners.</span><span class="sxs-lookup"><span data-stu-id="90230-172">**Resolution 1:** Create a schedule task that cleans up the following folder periodically.</span></span>

```powershell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

<span data-ttu-id="90230-173">**Lösung 2:** Ändern Sie die DSC-Konfiguration so, dass der Ordner *CommandAnalysis* am Ende der Konfiguration bereinigt wird.</span><span class="sxs-lookup"><span data-stu-id="90230-173">**Resolution 2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>

```powershell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn = "[Registry]SetRegisteredOwner"
        getscript = "@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
