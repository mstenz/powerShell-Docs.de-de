---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Verwenden von DSC auf Nano Server
ms.openlocfilehash: fd81fe56d16100f45d9ee2dfd8fdc303c2a6c17a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401436"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="1d650-103">Verwenden von DSC auf Nano Server</span><span class="sxs-lookup"><span data-stu-id="1d650-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="1d650-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1d650-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="1d650-105">**DSC unter Nano Server** ist ein optionales Paket im Ordner `NanoServer\Packages` des Windows Server 2016-Mediums.</span><span class="sxs-lookup"><span data-stu-id="1d650-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="1d650-106">Das Paket kann installiert werden, wenn Sie eine VHD (virtuelle Festplatte) für einen Nano Server erstellen, indem Sie **Microsoft-NanoServer-DSC-Package** als Wert des Parameters **Packages** der Funktion **New-NanoServerImage** angeben.</span><span class="sxs-lookup"><span data-stu-id="1d650-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="1d650-107">Wenn Sie beispielsweise eine virtuelle Festplatte für einen virtuellen Computer erstellen, würde der Befehl wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="1d650-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="1d650-108">Informationen zum Installieren und Verwenden von Nano Server sowie zum Verwalten von Nano Server mit PowerShell-Remoting finden Sie unter [Erste Schritte mit Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span><span class="sxs-lookup"><span data-stu-id="1d650-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span></span>

## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="1d650-109">Unter Nano Server verfügbare DSC-Funktionen</span><span class="sxs-lookup"><span data-stu-id="1d650-109">DSC features available on Nano Server</span></span>

<span data-ttu-id="1d650-110">Da Nano Server im Vergleich mit einer Vollversion von Windows Server nur einen eingeschränkten Satz von APIs unterstützt, besitzt DSC zurzeit unter Nano Server nicht denselben, vollständigen Funktionsumfang wie DSC, das auf vollständigen SKUs ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="1d650-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="1d650-111">DSC unter Nano Server befindet sich in der aktiven Entwicklung, und der Funktionsumfang ist noch nicht vollständig.</span><span class="sxs-lookup"><span data-stu-id="1d650-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

<span data-ttu-id="1d650-112">Die folgenden DSC-Funktionen sind zurzeit unter Nano Server verfügbar:</span><span class="sxs-lookup"><span data-stu-id="1d650-112">The following DSC features are currently available on Nano Server:</span></span>

<span data-ttu-id="1d650-113">Sowohl Push- als auch Pull-Modus</span><span class="sxs-lookup"><span data-stu-id="1d650-113">Both push and pull modes</span></span>

- <span data-ttu-id="1d650-114">Alle DSC-Cmdlets, die eine Vollversion von Windows Server beinhaltet, einschließlich der folgenden:</span><span class="sxs-lookup"><span data-stu-id="1d650-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
- [<span data-ttu-id="1d650-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="1d650-115">Get-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [<span data-ttu-id="1d650-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="1d650-116">Set-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [<span data-ttu-id="1d650-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="1d650-117">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [<span data-ttu-id="1d650-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="1d650-118">Disable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [<span data-ttu-id="1d650-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1d650-119">Start-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [<span data-ttu-id="1d650-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1d650-120">Stop-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [<span data-ttu-id="1d650-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1d650-121">Get-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [<span data-ttu-id="1d650-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1d650-122">Test-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [<span data-ttu-id="1d650-123">Publish-DscConfiguraiton</span><span class="sxs-lookup"><span data-stu-id="1d650-123">Publish-DscConfiguraiton</span></span>](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [<span data-ttu-id="1d650-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1d650-124">Update-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [<span data-ttu-id="1d650-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1d650-125">Restore-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [<span data-ttu-id="1d650-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="1d650-126">Remove-DscConfigurationDocument</span></span>](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [<span data-ttu-id="1d650-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="1d650-127">Get-DscConfigurationStatus</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [<span data-ttu-id="1d650-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="1d650-128">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [<span data-ttu-id="1d650-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="1d650-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [<span data-ttu-id="1d650-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="1d650-130">Get-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [<span data-ttu-id="1d650-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="1d650-131">New-DscChecksum</span></span>](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- <span data-ttu-id="1d650-132">Kompilieren von Konfigurationen (siehe [DSC-Konfigurationen](../configurations/configurations.md))</span><span class="sxs-lookup"><span data-stu-id="1d650-132">Compiling configurations (see [DSC configurations](../configurations/configurations.md))</span></span>

  <span data-ttu-id="1d650-133">**Issue #1629 (Problem #1629)** Verschlüsselung von Kennwörtern (finden Sie unter [Schützen der MOF-Datei](../pull-server/secureMOF.md)) während der Konfiguration, zu konfigurationskompilierung funktioniert nicht.</span><span class="sxs-lookup"><span data-stu-id="1d650-133">**Issue:** Password encryption (see [Securing the MOF File](../pull-server/secureMOF.md)) during configuration compilation doesn't work.</span></span>

- <span data-ttu-id="1d650-134">Kompilieren von Metakonfigurationen (siehe [Konfigurieren des lokalen Konfigurations-Managers](../managing-nodes/metaConfig.md)</span><span class="sxs-lookup"><span data-stu-id="1d650-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md))</span></span>

- <span data-ttu-id="1d650-135">Ausführen einer Ressource unter dem Benutzerkontext (siehe [Ausführen von DSC mit Benutzeranmeldeinformationen („Ausführen als“, RunAs)](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="1d650-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](../configurations/runAsUser.md))</span></span>

- <span data-ttu-id="1d650-136">Klassenbasierte Ressourcen (siehe [Schreiben einer benutzerdefinierten DSC-Ressource mit PowerShell-Klassen](../resources/authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="1d650-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](../resources/authoringResourceClass.md))</span></span>

- <span data-ttu-id="1d650-137">Debuggen von DSC-Ressourcen (siehe [Debuggen von DSC-Ressourcen](../troubleshooting/debugResource.md))</span><span class="sxs-lookup"><span data-stu-id="1d650-137">Debugging of DSC resources (see [Debugging DSC resources](../troubleshooting/debugResource.md))</span></span>

  <span data-ttu-id="1d650-138">**Issue #1629 (Problem #1629)** Funktioniert nicht, wenn eine Ressource PsDscRunAsCredential verwendet (siehe [Ausführen von DSC mit Benutzeranmeldeinformationen](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="1d650-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](../configurations/runAsUser.md))</span></span>

- [<span data-ttu-id="1d650-139">Angeben knotenübergreifender Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="1d650-139">Specifying cross-node dependencies</span></span>](../configurations/crossNodeDependencies.md)

- [<span data-ttu-id="1d650-140">Ressourcenversionsverwaltung</span><span class="sxs-lookup"><span data-stu-id="1d650-140">Resource versioning</span></span>](../configurations/sxsResource.md)

- <span data-ttu-id="1d650-141">Pullclient (Konfigurationen und Ressourcen) (siehe [Einrichten eines Pullclients mithilfe von Konfigurationsnamen](../pull-server/pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="1d650-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](../pull-server/pullClientConfigNames.md))</span></span>

- [<span data-ttu-id="1d650-142">Teilkonfigurationen (Pull und Push)</span><span class="sxs-lookup"><span data-stu-id="1d650-142">Partial configurations (pull & push)</span></span>](../pull-server/partialConfigs.md)

- [<span data-ttu-id="1d650-143">Berichterstattung an Pullserver</span><span class="sxs-lookup"><span data-stu-id="1d650-143">Reporting to pull server</span></span>](../pull-server/reportServer.md)

- <span data-ttu-id="1d650-144">MOF-Verschlüsselung</span><span class="sxs-lookup"><span data-stu-id="1d650-144">MOF encryption</span></span>

- <span data-ttu-id="1d650-145">Protokollierung</span><span class="sxs-lookup"><span data-stu-id="1d650-145">Event logging</span></span>

- <span data-ttu-id="1d650-146">Azure Automation-DSC-Berichte</span><span class="sxs-lookup"><span data-stu-id="1d650-146">Azure Automation DSC reporting</span></span>

- <span data-ttu-id="1d650-147">Ressourcen, die voll funktionsfähig sind</span><span class="sxs-lookup"><span data-stu-id="1d650-147">Resources that are fully functional</span></span>

- <span data-ttu-id="1d650-148">**Archive**</span><span class="sxs-lookup"><span data-stu-id="1d650-148">**Archive**</span></span>
- <span data-ttu-id="1d650-149">**Environment**</span><span class="sxs-lookup"><span data-stu-id="1d650-149">**Environment**</span></span>
- <span data-ttu-id="1d650-150">**File**</span><span class="sxs-lookup"><span data-stu-id="1d650-150">**File**</span></span>
- <span data-ttu-id="1d650-151">**Log**</span><span class="sxs-lookup"><span data-stu-id="1d650-151">**Log**</span></span>
- <span data-ttu-id="1d650-152">**ProcessSet**</span><span class="sxs-lookup"><span data-stu-id="1d650-152">**ProcessSet**</span></span>
- <span data-ttu-id="1d650-153">**Registry**</span><span class="sxs-lookup"><span data-stu-id="1d650-153">**Registry**</span></span>
- <span data-ttu-id="1d650-154">**Script**</span><span class="sxs-lookup"><span data-stu-id="1d650-154">**Script**</span></span>
- <span data-ttu-id="1d650-155">**WindowsPackageCab**</span><span class="sxs-lookup"><span data-stu-id="1d650-155">**WindowsPackageCab**</span></span>
- <span data-ttu-id="1d650-156">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="1d650-156">**WindowsProcess**</span></span>
- <span data-ttu-id="1d650-157">**WaitForAll** (siehe [Angeben knotenübergreifender Abhängigkeiten](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="1d650-157">**WaitForAll** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="1d650-158">**WaitForAny** (siehe [Angeben knotenübergreifender Abhängigkeiten](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="1d650-158">**WaitForAny** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="1d650-159">**WaitForSome** (siehe [Angeben knotenübergreifender Abhängigkeiten](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="1d650-159">**WaitForSome** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>

- <span data-ttu-id="1d650-160">Ressourcen, die teilweise funktionsfähig sind</span><span class="sxs-lookup"><span data-stu-id="1d650-160">Resources that are partially functional</span></span>
- <span data-ttu-id="1d650-161">**Gruppe**</span><span class="sxs-lookup"><span data-stu-id="1d650-161">**Group**</span></span>
- <span data-ttu-id="1d650-162">**GroupSet**</span><span class="sxs-lookup"><span data-stu-id="1d650-162">**GroupSet**</span></span>

  <span data-ttu-id="1d650-163">**Issue #1629 (Problem #1629)** Oben genannten Ressourcen fehl, wenn bestimmte Instanz zweimal aufgerufen wird (die gleiche Konfiguration zweimal ausgeführt)</span><span class="sxs-lookup"><span data-stu-id="1d650-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

- <span data-ttu-id="1d650-164">**Service**</span><span class="sxs-lookup"><span data-stu-id="1d650-164">**Service**</span></span>
- <span data-ttu-id="1d650-165">**ServiceSet**</span><span class="sxs-lookup"><span data-stu-id="1d650-165">**ServiceSet**</span></span>

  <span data-ttu-id="1d650-166">**Issue #1629 (Problem #1629)** Funktioniert nur bei starten/beenden (Status) des Diensts.</span><span class="sxs-lookup"><span data-stu-id="1d650-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="1d650-167">Schlägt fehl, wenn versucht wird, andere Attribute des Diensts zu ändern, z. B. Starttyp, Anmeldeinformationen, Beschreibung usw.</span><span class="sxs-lookup"><span data-stu-id="1d650-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="1d650-168">Ein Fehler mit etwa folgendem Wortlaut wird ausgelöst:</span><span class="sxs-lookup"><span data-stu-id="1d650-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="1d650-169">*Typ [management.managementobject] wurde nicht gefunden: Stellen Sie sicher, dass die Assembly, die diesen Typ enthält, geladen wird.*</span><span class="sxs-lookup"><span data-stu-id="1d650-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

- <span data-ttu-id="1d650-170">Ressourcen, die nicht funktionsfähig sind</span><span class="sxs-lookup"><span data-stu-id="1d650-170">Resources that are not functional</span></span>
- <span data-ttu-id="1d650-171">**User**</span><span class="sxs-lookup"><span data-stu-id="1d650-171">**User**</span></span>

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="1d650-172">Unter Nano Server nicht verfügbare DSC-Funktionen</span><span class="sxs-lookup"><span data-stu-id="1d650-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="1d650-173">Die folgenden DSC-Funktionen sind zurzeit unter Nano Server nicht verfügbar:</span><span class="sxs-lookup"><span data-stu-id="1d650-173">The following DSC features are not currently available on Nano Server:</span></span>

- <span data-ttu-id="1d650-174">Entschlüsseln von MOF-Dokumenten mit verschlüsselten Kennwörtern</span><span class="sxs-lookup"><span data-stu-id="1d650-174">Decrypting MOF document with encrypted password(s)</span></span>
- <span data-ttu-id="1d650-175">Pullserver: Sie können zurzeit keinen Pullserver unter Nano Server einrichten.</span><span class="sxs-lookup"><span data-stu-id="1d650-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
- <span data-ttu-id="1d650-176">Alle Funktionen, die nicht in der Liste der Funktionen aufgeführt sind, funktionieren.</span><span class="sxs-lookup"><span data-stu-id="1d650-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="1d650-177">Verwenden benutzerdefinierter DSC-Ressourcen unter Nano Server</span><span class="sxs-lookup"><span data-stu-id="1d650-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="1d650-178">Aufgrund eingeschränkter Sätze von Windows-APIs und CLR-Bibliotheken, die unter Nano Server verfügbar sind, funktionieren DSC-Ressourcen, die in der vollständigen CLR-Version von Windows funktionieren, nicht notwendigerweise auch unter Nano Server.</span><span class="sxs-lookup"><span data-stu-id="1d650-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="1d650-179">Führen Sie zuerst End-to-End-Tests durch, bevor Sie benutzerdefinierte DSC-Ressourcen in einer Produktionsumgebung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="1d650-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d650-180">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1d650-180">See Also</span></span>

- [<span data-ttu-id="1d650-181">Erste Schritte mit Nano Server</span><span class="sxs-lookup"><span data-stu-id="1d650-181">Getting Started with Nano Server</span></span>](/windows-server/get-started/getting-started-with-nano-server)
