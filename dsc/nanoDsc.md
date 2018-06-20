---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Verwenden von DSC auf Nano Server
ms.openlocfilehash: 9e26c525b48e8656a3479db9c0a760eaeb8cf58a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190246"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="55b97-103">Verwenden von DSC auf Nano Server</span><span class="sxs-lookup"><span data-stu-id="55b97-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="55b97-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="55b97-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="55b97-105">**DSC unter Nano Server** ist ein optionales Paket im Ordner `NanoServer\Packages` des Windows Server 2016-Mediums.</span><span class="sxs-lookup"><span data-stu-id="55b97-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="55b97-106">Das Paket kann installiert werden, wenn Sie eine VHD (virtuelle Festplatte) für einen Nano Server erstellen, indem Sie **Microsoft-NanoServer-DSC-Package** als Wert des Parameters **Packages** der Funktion **New-NanoServerImage** angeben.</span><span class="sxs-lookup"><span data-stu-id="55b97-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="55b97-107">Wenn Sie beispielsweise eine virtuelle Festplatte für einen virtuellen Computer erstellen, würde der Befehl wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="55b97-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="55b97-108">Informationen zum Installieren und Verwenden von Nano Server sowie zum Verwalten von Nano Server mit PowerShell-Remoting finden Sie unter [Erste Schritte mit Nano Server](https://technet.microsoft.com/library/mt126167.aspx).</span><span class="sxs-lookup"><span data-stu-id="55b97-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](https://technet.microsoft.com/library/mt126167.aspx).</span></span>


## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="55b97-109">Unter Nano Server verfügbare DSC-Funktionen</span><span class="sxs-lookup"><span data-stu-id="55b97-109">DSC features available on Nano Server</span></span>

 <span data-ttu-id="55b97-110">Da Nano Server im Vergleich mit einer Vollversion von Windows Server nur einen eingeschränkten Satz von APIs unterstützt, besitzt DSC zurzeit unter Nano Server nicht denselben, vollständigen Funktionsumfang wie DSC, das auf vollständigen SKUs ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="55b97-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="55b97-111">DSC unter Nano Server befindet sich in der aktiven Entwicklung, und der Funktionsumfang ist noch nicht vollständig.</span><span class="sxs-lookup"><span data-stu-id="55b97-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

 <span data-ttu-id="55b97-112">Die folgenden DSC-Funktionen sind zurzeit unter Nano Server verfügbar:</span><span class="sxs-lookup"><span data-stu-id="55b97-112">The following DSC features are currently available on Nano Server:</span></span>


* <span data-ttu-id="55b97-113">Sowohl Push- als auch Pull-Modus</span><span class="sxs-lookup"><span data-stu-id="55b97-113">Both push and pull modes</span></span>

* <span data-ttu-id="55b97-114">Alle DSC-Cmdlets, die eine Vollversion von Windows Server beinhaltet, einschließlich der folgenden:</span><span class="sxs-lookup"><span data-stu-id="55b97-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
  * [<span data-ttu-id="55b97-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="55b97-115">Get-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/library/dn407378.aspx)
  * [<span data-ttu-id="55b97-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="55b97-116">Set-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/library/dn521621.aspx)
  * [<span data-ttu-id="55b97-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="55b97-117">Enable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [<span data-ttu-id="55b97-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="55b97-118">Disable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517872.aspx)
  * [<span data-ttu-id="55b97-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="55b97-119">Start-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [<span data-ttu-id="55b97-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="55b97-120">Stop-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [<span data-ttu-id="55b97-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="55b97-121">Get-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [<span data-ttu-id="55b97-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="55b97-122">Test-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407382.aspx)
  * [<span data-ttu-id="55b97-123">Publish-DscConfiguraiton</span><span class="sxs-lookup"><span data-stu-id="55b97-123">Publish-DscConfiguraiton</span></span>](https://technet.microsoft.com/en-us/library/mt517875.aspx)
  * [<span data-ttu-id="55b97-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="55b97-124">Update-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [<span data-ttu-id="55b97-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="55b97-125">Restore-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [<span data-ttu-id="55b97-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="55b97-126">Remove-DscConfigurationDocument</span></span>](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [<span data-ttu-id="55b97-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="55b97-127">Get-DscConfigurationStatus</span></span>](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [<span data-ttu-id="55b97-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="55b97-128">Invoke-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [<span data-ttu-id="55b97-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="55b97-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [<span data-ttu-id="55b97-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="55b97-130">Get-DscResource</span></span>](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [<span data-ttu-id="55b97-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="55b97-131">New-DscChecksum</span></span>](https://technet.microsoft.com/en-us/library/dn521622.aspx)

* <span data-ttu-id="55b97-132">Kompilieren von Konfigurationen (siehe [DSC-Konfigurationen](configurations.md))</span><span class="sxs-lookup"><span data-stu-id="55b97-132">Compiling configurations (see [DSC configurations](configurations.md))</span></span>

  <span data-ttu-id="55b97-133">**Problem:** Die Kennwortverschlüsselung (siehe [Schützen der MOF-Datei](securemof.md)) während der Konfigurationskompilierung funktioniert nicht.</span><span class="sxs-lookup"><span data-stu-id="55b97-133">**Issue:** Password encryption (see [Securing the MOF File](securemof.md)) during configuration compilation doesn't work.</span></span>

* <span data-ttu-id="55b97-134">Kompilieren von Metakonfigurationen (siehe [Konfigurieren des lokalen Konfigurations-Managers](metaConfig.md)</span><span class="sxs-lookup"><span data-stu-id="55b97-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](metaConfig.md))</span></span>

* <span data-ttu-id="55b97-135">Ausführen einer Ressource unter dem Benutzerkontext (siehe [Ausführen von DSC mit Benutzeranmeldeinformationen („Ausführen als“, RunAs)](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="55b97-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](runAsUser.md))</span></span>

* <span data-ttu-id="55b97-136">Klassenbasierte Ressourcen (siehe [Schreiben einer benutzerdefinierten DSC-Ressource mit PowerShell-Klassen](authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="55b97-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](authoringResourceClass.md))</span></span>

* <span data-ttu-id="55b97-137">Debuggen von DSC-Ressourcen (siehe [Debuggen von DSC-Ressourcen](debugresource.md))</span><span class="sxs-lookup"><span data-stu-id="55b97-137">Debugging of DSC resources (see [Debugging DSC resources](debugresource.md))</span></span>

  <span data-ttu-id="55b97-138">**Problem:** Funktioniert nicht, wenn eine Ressource PsDscRunAsCredential verwendet (siehe [Ausführen von DSC mit Benutzeranmeldeinformationen](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="55b97-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](runAsUser.md))</span></span>

* [<span data-ttu-id="55b97-139">Angeben knotenübergreifender Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="55b97-139">Specifying cross-node dependencies</span></span>](crossNodeDependencies.md)

* [<span data-ttu-id="55b97-140">Ressourcenversionsverwaltung</span><span class="sxs-lookup"><span data-stu-id="55b97-140">Resource versioning</span></span>](sxsResource.md)

* <span data-ttu-id="55b97-141">Pullclient (Konfigurationen und Ressourcen) (siehe [Einrichten eines Pullclients mithilfe von Konfigurationsnamen](pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="55b97-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](pullClientConfigNames.md))</span></span>

* [<span data-ttu-id="55b97-142">Teilkonfigurationen (Pull und Push)</span><span class="sxs-lookup"><span data-stu-id="55b97-142">Partial configurations (pull & push)</span></span>](partialConfigs.md)

* [<span data-ttu-id="55b97-143">Berichterstattung an Pullserver</span><span class="sxs-lookup"><span data-stu-id="55b97-143">Reporting to pull server</span></span>](reportServer.md)

* <span data-ttu-id="55b97-144">MOF-Verschlüsselung</span><span class="sxs-lookup"><span data-stu-id="55b97-144">MOF encryption</span></span>

* <span data-ttu-id="55b97-145">Protokollierung</span><span class="sxs-lookup"><span data-stu-id="55b97-145">Event logging</span></span>

* <span data-ttu-id="55b97-146">Azure Automation-DSC-Berichte</span><span class="sxs-lookup"><span data-stu-id="55b97-146">Azure Automation DSC reporting</span></span>

* <span data-ttu-id="55b97-147">Ressourcen, die voll funktionsfähig sind</span><span class="sxs-lookup"><span data-stu-id="55b97-147">Resources that are fully functional</span></span>
  * [<span data-ttu-id="55b97-148">Archive</span><span class="sxs-lookup"><span data-stu-id="55b97-148">Archive</span></span>](archiveResource.md)
  * [<span data-ttu-id="55b97-149">Environment</span><span class="sxs-lookup"><span data-stu-id="55b97-149">Environment</span></span>](environmentResource.md)
  * [<span data-ttu-id="55b97-150">File</span><span class="sxs-lookup"><span data-stu-id="55b97-150">File</span></span>](fileResource.md)
  * [<span data-ttu-id="55b97-151">Log</span><span class="sxs-lookup"><span data-stu-id="55b97-151">Log</span></span>](logResource.md)
  * <span data-ttu-id="55b97-152">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="55b97-152">ProcessSet</span></span>
  * [<span data-ttu-id="55b97-153">Registry</span><span class="sxs-lookup"><span data-stu-id="55b97-153">Registry</span></span>](registryResource.md)
  * [<span data-ttu-id="55b97-154">Script</span><span class="sxs-lookup"><span data-stu-id="55b97-154">Script</span></span>](scriptResource.md)
  * <span data-ttu-id="55b97-155">WindowsPackageCab</span><span class="sxs-lookup"><span data-stu-id="55b97-155">WindowsPackageCab</span></span>
  * [<span data-ttu-id="55b97-156">WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="55b97-156">WindowsProcess</span></span>](windowsProcessResource.md)
  * <span data-ttu-id="55b97-157">WaitForAll (siehe [Angeben knotenübergreifender Abhängigkeiten](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="55b97-157">WaitForAll (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="55b97-158">WaitForAny (siehe [Angeben knotenübergreifender Abhängigkeiten](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="55b97-158">WaitForAny (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="55b97-159">WaitForSome (siehe [Angeben knotenübergreifender Abhängigkeiten](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="55b97-159">WaitForSome (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>

* <span data-ttu-id="55b97-160">Ressourcen, die teilweise funktionsfähig sind</span><span class="sxs-lookup"><span data-stu-id="55b97-160">Resources that are partially functional</span></span>
  * [<span data-ttu-id="55b97-161">Gruppe</span><span class="sxs-lookup"><span data-stu-id="55b97-161">Group</span></span>](groupResource.md)
  * <span data-ttu-id="55b97-162">GroupSet</span><span class="sxs-lookup"><span data-stu-id="55b97-162">GroupSet</span></span>

  <span data-ttu-id="55b97-163">**Problem:** Bei den oben genannten Ressourcen tritt ein Fehler auf, wenn eine bestimmte Instanz zweimal aufgerufen wird (bzw. wenn die gleiche Konfiguration zweimal ausgeführt wird)</span><span class="sxs-lookup"><span data-stu-id="55b97-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

  * [<span data-ttu-id="55b97-164">Service</span><span class="sxs-lookup"><span data-stu-id="55b97-164">Service</span></span>](serviceResource.md)
  * <span data-ttu-id="55b97-165">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="55b97-165">ServiceSet</span></span>

  <span data-ttu-id="55b97-166">**Problem:** Funktioniert nur beim Starten/Beenden (Status) des Diensts.</span><span class="sxs-lookup"><span data-stu-id="55b97-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="55b97-167">Schlägt fehl, wenn versucht wird, andere Attribute des Diensts zu ändern, z. B. Starttyp, Anmeldeinformationen, Beschreibung usw.</span><span class="sxs-lookup"><span data-stu-id="55b97-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="55b97-168">Ein Fehler mit etwa folgendem Wortlaut wird ausgelöst:</span><span class="sxs-lookup"><span data-stu-id="55b97-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="55b97-169">*Typ [management.managementobject] wurde nicht gefunden: Stellen Sie sicher, dass die Assembly, die diesen Typ enthält, geladen wird.*</span><span class="sxs-lookup"><span data-stu-id="55b97-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

* <span data-ttu-id="55b97-170">Ressourcen, die nicht funktionsfähig sind</span><span class="sxs-lookup"><span data-stu-id="55b97-170">Resources that are not functional</span></span>
  * [<span data-ttu-id="55b97-171">User</span><span class="sxs-lookup"><span data-stu-id="55b97-171">User</span></span>](userResource.md)


## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="55b97-172">Unter Nano Server nicht verfügbare DSC-Funktionen</span><span class="sxs-lookup"><span data-stu-id="55b97-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="55b97-173">Die folgenden DSC-Funktionen sind zurzeit unter Nano Server nicht verfügbar:</span><span class="sxs-lookup"><span data-stu-id="55b97-173">The following DSC features are not currently available on Nano Server:</span></span>

* <span data-ttu-id="55b97-174">Entschlüsseln von MOF-Dokumenten mit verschlüsselten Kennwörtern</span><span class="sxs-lookup"><span data-stu-id="55b97-174">Decrypting MOF document with encrypted password(s)</span></span>
* <span data-ttu-id="55b97-175">Pullserver: Sie können zurzeit keinen Pullserver unter Nano Server einrichten.</span><span class="sxs-lookup"><span data-stu-id="55b97-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
* <span data-ttu-id="55b97-176">Alle Funktionen, die nicht in der Liste der Funktionen aufgeführt sind, funktionieren.</span><span class="sxs-lookup"><span data-stu-id="55b97-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="55b97-177">Verwenden benutzerdefinierter DSC-Ressourcen unter Nano Server</span><span class="sxs-lookup"><span data-stu-id="55b97-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="55b97-178">Aufgrund eingeschränkter Sätze von Windows-APIs und CLR-Bibliotheken, die unter Nano Server verfügbar sind, funktionieren DSC-Ressourcen, die in der vollständigen CLR-Version von Windows funktionieren, nicht notwendigerweise auch unter Nano Server.</span><span class="sxs-lookup"><span data-stu-id="55b97-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="55b97-179">Führen Sie zuerst End-to-End-Tests durch, bevor Sie benutzerdefinierte DSC-Ressourcen in einer Produktionsumgebung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="55b97-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="55b97-180">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="55b97-180">See Also</span></span>
- [<span data-ttu-id="55b97-181">Erste Schritte mit Nano Server</span><span class="sxs-lookup"><span data-stu-id="55b97-181">Getting Started with Nano Server</span></span>](https://technet.microsoft.com/library/mt126167.aspx)