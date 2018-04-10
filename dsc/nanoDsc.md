---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Verwenden von DSC auf Nano Server
ms.openlocfilehash: 9ebc1f046893c360538009b5ecbcfb6456f92bbb
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="45eba-103">Verwenden von DSC auf Nano Server</span><span class="sxs-lookup"><span data-stu-id="45eba-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="45eba-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="45eba-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="45eba-105">**DSC unter Nano Server** ist ein optionales Paket im Ordner `NanoServer\Packages` des Windows Server 2016-Mediums.</span><span class="sxs-lookup"><span data-stu-id="45eba-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="45eba-106">Das Paket kann installiert werden, wenn Sie eine VHD (virtuelle Festplatte) für einen Nano Server erstellen, indem Sie **Microsoft-NanoServer-DSC-Package** als Wert des Parameters **Packages** der Funktion **New-NanoServerImage** angeben.</span><span class="sxs-lookup"><span data-stu-id="45eba-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="45eba-107">Wenn Sie beispielsweise eine virtuelle Festplatte für einen virtuellen Computer erstellen, würde der Befehl wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="45eba-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="45eba-108">Informationen zum Installieren und Verwenden von Nano Server sowie zum Verwalten von Nano Server mit PowerShell-Remoting finden Sie unter [Erste Schritte mit Nano Server](https://technet.microsoft.com/library/mt126167.aspx).</span><span class="sxs-lookup"><span data-stu-id="45eba-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](https://technet.microsoft.com/library/mt126167.aspx).</span></span>


## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="45eba-109">Unter Nano Server verfügbare DSC-Funktionen</span><span class="sxs-lookup"><span data-stu-id="45eba-109">DSC features available on Nano Server</span></span>

 <span data-ttu-id="45eba-110">Da Nano Server im Vergleich mit einer Vollversion von Windows Server nur einen eingeschränkten Satz von APIs unterstützt, besitzt DSC zurzeit unter Nano Server nicht denselben, vollständigen Funktionsumfang wie DSC, das auf vollständigen SKUs ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="45eba-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="45eba-111">DSC unter Nano Server befindet sich in der aktiven Entwicklung, und der Funktionsumfang ist noch nicht vollständig.</span><span class="sxs-lookup"><span data-stu-id="45eba-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

 <span data-ttu-id="45eba-112">Die folgenden DSC-Funktionen sind zurzeit unter Nano Server verfügbar:</span><span class="sxs-lookup"><span data-stu-id="45eba-112">The following DSC features are currently available on Nano Server:</span></span>


* <span data-ttu-id="45eba-113">Sowohl Push- als auch Pull-Modus</span><span class="sxs-lookup"><span data-stu-id="45eba-113">Both push and pull modes</span></span>

* <span data-ttu-id="45eba-114">Alle DSC-Cmdlets, die eine Vollversion von Windows Server beinhaltet, einschließlich der folgenden:</span><span class="sxs-lookup"><span data-stu-id="45eba-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
  * [<span data-ttu-id="45eba-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="45eba-115">Get-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/library/dn407378.aspx)
  * [<span data-ttu-id="45eba-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="45eba-116">Set-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/library/dn521621.aspx)
  * [<span data-ttu-id="45eba-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="45eba-117">Enable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [<span data-ttu-id="45eba-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="45eba-118">Disable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517872.aspx)
  * [<span data-ttu-id="45eba-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="45eba-119">Start-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [<span data-ttu-id="45eba-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="45eba-120">Stop-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [<span data-ttu-id="45eba-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="45eba-121">Get-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [<span data-ttu-id="45eba-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="45eba-122">Test-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407382.aspx)
  * [<span data-ttu-id="45eba-123">Publish-DscConfiguraiton</span><span class="sxs-lookup"><span data-stu-id="45eba-123">Publish-DscConfiguraiton</span></span>](https://technet.microsoft.com/en-us/library/mt517875.aspx)
  * [<span data-ttu-id="45eba-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="45eba-124">Update-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [<span data-ttu-id="45eba-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="45eba-125">Restore-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [<span data-ttu-id="45eba-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="45eba-126">Remove-DscConfigurationDocument</span></span>](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [<span data-ttu-id="45eba-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="45eba-127">Get-DscConfigurationStatus</span></span>](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [<span data-ttu-id="45eba-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="45eba-128">Invoke-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [<span data-ttu-id="45eba-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="45eba-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [<span data-ttu-id="45eba-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="45eba-130">Get-DscResource</span></span>](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [<span data-ttu-id="45eba-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="45eba-131">New-DscChecksum</span></span>](https://technet.microsoft.com/en-us/library/dn521622.aspx)

* <span data-ttu-id="45eba-132">Kompilieren von Konfigurationen (siehe [DSC-Konfigurationen](configurations.md))</span><span class="sxs-lookup"><span data-stu-id="45eba-132">Compiling configurations (see [DSC configurations](configurations.md))</span></span>

  <span data-ttu-id="45eba-133">**Problem:** Die Kennwortverschlüsselung (siehe [Schützen der MOF-Datei](securemof.md)) während der Konfigurationskompilierung funktioniert nicht.</span><span class="sxs-lookup"><span data-stu-id="45eba-133">**Issue:** Password encryption (see [Securing the MOF File](securemof.md)) during configuration compilation doesn't work.</span></span>

* <span data-ttu-id="45eba-134">Kompilieren von Metakonfigurationen (siehe [Konfigurieren des lokalen Konfigurations-Managers](metaConfig.md)</span><span class="sxs-lookup"><span data-stu-id="45eba-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](metaConfig.md))</span></span>

* <span data-ttu-id="45eba-135">Ausführen einer Ressource unter dem Benutzerkontext (siehe [Ausführen von DSC mit Benutzeranmeldeinformationen („Ausführen als“, RunAs)](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="45eba-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](runAsUser.md))</span></span>

* <span data-ttu-id="45eba-136">Klassenbasierte Ressourcen (siehe [Schreiben einer benutzerdefinierten DSC-Ressource mit PowerShell-Klassen](authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="45eba-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](authoringResourceClass.md))</span></span>

* <span data-ttu-id="45eba-137">Debuggen von DSC-Ressourcen (siehe [Debuggen von DSC-Ressourcen](debugresource.md))</span><span class="sxs-lookup"><span data-stu-id="45eba-137">Debugging of DSC resources (see [Debugging DSC resources](debugresource.md))</span></span>

  <span data-ttu-id="45eba-138">**Problem:** Funktioniert nicht, wenn eine Ressource PsDscRunAsCredential verwendet (siehe [Ausführen von DSC mit Benutzeranmeldeinformationen](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="45eba-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](runAsUser.md))</span></span>

* [<span data-ttu-id="45eba-139">Angeben knotenübergreifender Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="45eba-139">Specifying cross-node dependencies</span></span>](crossNodeDependencies.md)

* [<span data-ttu-id="45eba-140">Ressourcenversionsverwaltung</span><span class="sxs-lookup"><span data-stu-id="45eba-140">Resource versioning</span></span>](sxsResource.md)

* <span data-ttu-id="45eba-141">Pullclient (Konfigurationen und Ressourcen) (siehe [Einrichten eines Pullclients mithilfe von Konfigurationsnamen](pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="45eba-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](pullClientConfigNames.md))</span></span>

* [<span data-ttu-id="45eba-142">Teilkonfigurationen (Pull und Push)</span><span class="sxs-lookup"><span data-stu-id="45eba-142">Partial configurations (pull & push)</span></span>](partialConfigs.md)

* [<span data-ttu-id="45eba-143">Berichterstattung an Pullserver</span><span class="sxs-lookup"><span data-stu-id="45eba-143">Reporting to pull server</span></span>](reportServer.md)

* <span data-ttu-id="45eba-144">MOF-Verschlüsselung</span><span class="sxs-lookup"><span data-stu-id="45eba-144">MOF encryption</span></span>

* <span data-ttu-id="45eba-145">Protokollierung</span><span class="sxs-lookup"><span data-stu-id="45eba-145">Event logging</span></span>

* <span data-ttu-id="45eba-146">Azure Automation-DSC-Berichte</span><span class="sxs-lookup"><span data-stu-id="45eba-146">Azure Automation DSC reporting</span></span>

* <span data-ttu-id="45eba-147">Ressourcen, die voll funktionsfähig sind</span><span class="sxs-lookup"><span data-stu-id="45eba-147">Resources that are fully functional</span></span>
  * [<span data-ttu-id="45eba-148">Archive</span><span class="sxs-lookup"><span data-stu-id="45eba-148">Archive</span></span>](archiveResource.md)
  * [<span data-ttu-id="45eba-149">Environment</span><span class="sxs-lookup"><span data-stu-id="45eba-149">Environment</span></span>](environmentResource.md)
  * [<span data-ttu-id="45eba-150">File</span><span class="sxs-lookup"><span data-stu-id="45eba-150">File</span></span>](fileResource.md)
  * [<span data-ttu-id="45eba-151">Log</span><span class="sxs-lookup"><span data-stu-id="45eba-151">Log</span></span>](logResource.md)
  * <span data-ttu-id="45eba-152">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="45eba-152">ProcessSet</span></span>
  * [<span data-ttu-id="45eba-153">Registry</span><span class="sxs-lookup"><span data-stu-id="45eba-153">Registry</span></span>](registryResource.md)
  * [<span data-ttu-id="45eba-154">Script</span><span class="sxs-lookup"><span data-stu-id="45eba-154">Script</span></span>](scriptResource.md)
  * <span data-ttu-id="45eba-155">WindowsPackageCab</span><span class="sxs-lookup"><span data-stu-id="45eba-155">WindowsPackageCab</span></span>
  * [<span data-ttu-id="45eba-156">WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="45eba-156">WindowsProcess</span></span>](windowsProcessResource.md)
  * <span data-ttu-id="45eba-157">WaitForAll (siehe [Angeben knotenübergreifender Abhängigkeiten](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="45eba-157">WaitForAll (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="45eba-158">WaitForAny (siehe [Angeben knotenübergreifender Abhängigkeiten](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="45eba-158">WaitForAny (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="45eba-159">WaitForSome (siehe [Angeben knotenübergreifender Abhängigkeiten](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="45eba-159">WaitForSome (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>

* <span data-ttu-id="45eba-160">Ressourcen, die teilweise funktionsfähig sind</span><span class="sxs-lookup"><span data-stu-id="45eba-160">Resources that are partially functional</span></span>
  * [<span data-ttu-id="45eba-161">Gruppe</span><span class="sxs-lookup"><span data-stu-id="45eba-161">Group</span></span>](groupResource.md)
  * <span data-ttu-id="45eba-162">GroupSet</span><span class="sxs-lookup"><span data-stu-id="45eba-162">GroupSet</span></span>

  <span data-ttu-id="45eba-163">**Problem:** Bei den oben genannten Ressourcen tritt ein Fehler auf, wenn eine bestimmte Instanz zweimal aufgerufen wird (bzw. wenn die gleiche Konfiguration zweimal ausgeführt wird)</span><span class="sxs-lookup"><span data-stu-id="45eba-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

  * [<span data-ttu-id="45eba-164">Service</span><span class="sxs-lookup"><span data-stu-id="45eba-164">Service</span></span>](serviceResource.md)
  * <span data-ttu-id="45eba-165">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="45eba-165">ServiceSet</span></span>

  <span data-ttu-id="45eba-166">**Problem:** Funktioniert nur beim Starten/Beenden (Status) des Diensts.</span><span class="sxs-lookup"><span data-stu-id="45eba-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="45eba-167">Schlägt fehl, wenn versucht wird, andere Attribute des Diensts zu ändern, z. B. Starttyp, Anmeldeinformationen, Beschreibung usw.</span><span class="sxs-lookup"><span data-stu-id="45eba-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="45eba-168">Ein Fehler mit etwa folgendem Wortlaut wird ausgelöst:</span><span class="sxs-lookup"><span data-stu-id="45eba-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="45eba-169">*Typ [management.managementobject] wurde nicht gefunden: Stellen Sie sicher, dass die Assembly, die diesen Typ enthält, geladen wird.*</span><span class="sxs-lookup"><span data-stu-id="45eba-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

* <span data-ttu-id="45eba-170">Ressourcen, die nicht funktionsfähig sind</span><span class="sxs-lookup"><span data-stu-id="45eba-170">Resources that are not functional</span></span>
  * [<span data-ttu-id="45eba-171">User</span><span class="sxs-lookup"><span data-stu-id="45eba-171">User</span></span>](userResource.md)


## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="45eba-172">Unter Nano Server nicht verfügbare DSC-Funktionen</span><span class="sxs-lookup"><span data-stu-id="45eba-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="45eba-173">Die folgenden DSC-Funktionen sind zurzeit unter Nano Server nicht verfügbar:</span><span class="sxs-lookup"><span data-stu-id="45eba-173">The following DSC features are not currently available on Nano Server:</span></span>

* <span data-ttu-id="45eba-174">Entschlüsseln von MOF-Dokumenten mit verschlüsselten Kennwörtern</span><span class="sxs-lookup"><span data-stu-id="45eba-174">Decrypting MOF document with encrypted password(s)</span></span>
* <span data-ttu-id="45eba-175">Pullserver: Sie können zurzeit keinen Pullserver unter Nano Server einrichten.</span><span class="sxs-lookup"><span data-stu-id="45eba-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
* <span data-ttu-id="45eba-176">Alle Funktionen, die nicht in der Liste der Funktionen aufgeführt sind, funktionieren.</span><span class="sxs-lookup"><span data-stu-id="45eba-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="45eba-177">Verwenden benutzerdefinierter DSC-Ressourcen unter Nano Server</span><span class="sxs-lookup"><span data-stu-id="45eba-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="45eba-178">Aufgrund eingeschränkter Sätze von Windows-APIs und CLR-Bibliotheken, die unter Nano Server verfügbar sind, funktionieren DSC-Ressourcen, die in der vollständigen CLR-Version von Windows funktionieren, nicht notwendigerweise auch unter Nano Server.</span><span class="sxs-lookup"><span data-stu-id="45eba-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="45eba-179">Führen Sie zuerst End-to-End-Tests durch, bevor Sie benutzerdefinierte DSC-Ressourcen in einer Produktionsumgebung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="45eba-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="45eba-180">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="45eba-180">See Also</span></span>
- [<span data-ttu-id="45eba-181">Erste Schritte mit Nano Server</span><span class="sxs-lookup"><span data-stu-id="45eba-181">Getting Started with Nano Server</span></span>](https://technet.microsoft.com/library/mt126167.aspx)