---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Prüfliste für die Ressourcenerstellung
ms.openlocfilehash: 76d9fecca8618fcc178975465f45cda0d0e04064
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189957"
---
# <a name="resource-authoring-checklist"></a><span data-ttu-id="5f063-103">Prüfliste für die Ressourcenerstellung</span><span class="sxs-lookup"><span data-stu-id="5f063-103">Resource authoring checklist</span></span>
<span data-ttu-id="5f063-104">Diese Prüfliste ist eine Liste der bewährten Methoden beim Erstellen einer neuen DSC-Ressource.</span><span class="sxs-lookup"><span data-stu-id="5f063-104">This checklist is a list of best practices when authoring a new DSC Resource.</span></span>
## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a><span data-ttu-id="5f063-105">Das Ressourcenmodul enthält für jede Ressource Dateien des Typs „.psd1“ und „schema.mof“.</span><span class="sxs-lookup"><span data-stu-id="5f063-105">Resource module contains .psd1 file and schema.mof for every resource</span></span>
<span data-ttu-id="5f063-106">Stellen Sie sicher, dass Ihre Ressource eine ordnungsgemäße Struktur hat und alle erforderlichen Dateien enthält.</span><span class="sxs-lookup"><span data-stu-id="5f063-106">Check that your resource has correct structure and contains all required files.</span></span> <span data-ttu-id="5f063-107">Ein Ressourcenmodul muss eine PSD1-Datei enthalten, und für jede nicht zusammengesetzte Ressource muss die Datei „schema.mof“ vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="5f063-107">Every resource module should contain a .psd1 file and every non-composite resource should have schema.mof file.</span></span> <span data-ttu-id="5f063-108">Ressourcen ohne Schema werden nach Ausführen von **Get-DscResource** nicht aufgeführt. Zudem können Benutzer nicht mit IntelliSense arbeiten, wenn Code für diese Module in der ISE geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="5f063-108">Resources that do not contain schema will not be listed by **Get-DscResource** and users will not be able to use the intellisense when writing code against those modules in ISE.</span></span>
<span data-ttu-id="5f063-109">Die Verzeichnisstruktur für die Ressource „xRemoteFile“, die Teil des [Ressourcenmoduls „xPSDesiredStateConfiguration“](https://github.com/PowerShell/xPSDesiredStateConfiguration) ist, sieht folgendermaßen aus:</span><span class="sxs-lookup"><span data-stu-id="5f063-109">The directory structure for xRemoteFile resource, which is part of the [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), looks as follows:</span></span>


```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a><span data-ttu-id="5f063-110">Die Ressource und das Schema sind richtig##</span><span class="sxs-lookup"><span data-stu-id="5f063-110">Resource and schema are correct##</span></span>
<span data-ttu-id="5f063-111">Überprüfen Sie die Ressourcenschemadatei („\*.schema.mof“).</span><span class="sxs-lookup"><span data-stu-id="5f063-111">Verify the resource schema (\*.schema.mof) file.</span></span> <span data-ttu-id="5f063-112">Sie können den [DSC-Ressourcen-Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) verwenden, um Ihr Schema zu entwickeln und zu testen.</span><span class="sxs-lookup"><span data-stu-id="5f063-112">You can use the [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) to help develop and test your schema.</span></span>
<span data-ttu-id="5f063-113">Stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="5f063-113">Make sure that:</span></span>
- <span data-ttu-id="5f063-114">Eigenschaftentypen sind ordnungsgemäß (z. B. STRING wird nicht für Eigenschaften für numerische Werte verwendet, wofür UInt32 oder andere numerische Typen gewählt werden müssen).</span><span class="sxs-lookup"><span data-stu-id="5f063-114">Property types are correct (e.g. don’t use String for properties which accept numeric values, you should use UInt32 or other numeric types instead)</span></span>
- <span data-ttu-id="5f063-115">Eigenschaftsattribute sind ordnungsgemäß angegeben als: ([key], [required], [write], [read]).</span><span class="sxs-lookup"><span data-stu-id="5f063-115">Property attributes are specified correctly as: ([key], [required], [write], [read])</span></span>
- <span data-ttu-id="5f063-116">Mindestens ein Parameter im Schema muss als [key] markiert sein.</span><span class="sxs-lookup"><span data-stu-id="5f063-116">At least one parameter in the schema has to be marked as [key]</span></span>
- <span data-ttu-id="5f063-117">Die [read]-Eigenschaft darf nicht zusammen mit den folgenden Eigenschaften angegeben werden: [required], [key], [write]</span><span class="sxs-lookup"><span data-stu-id="5f063-117">[read] property does not coexist together with any of: [required], [key], [write]</span></span>
- <span data-ttu-id="5f063-118">Wenn mehrere Qualifizierer außer [read] angegeben sind, hat [key] Vorrang.</span><span class="sxs-lookup"><span data-stu-id="5f063-118">If multiple qualifiers are specified except [read], then [key] takes precedence</span></span>
- <span data-ttu-id="5f063-119">Wenn [write] und [required] angegeben sind, hat [required] Vorrang.</span><span class="sxs-lookup"><span data-stu-id="5f063-119">If [write] and [required] are specified, then [required] takes precedence</span></span>
- <span data-ttu-id="5f063-120">„ValueMap“ wird gegebenenfalls angegeben.</span><span class="sxs-lookup"><span data-stu-id="5f063-120">ValueMap is specified where appropriate</span></span>

<span data-ttu-id="5f063-121">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="5f063-121">Example:</span></span>
```
[Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
```

- <span data-ttu-id="5f063-122">Der Anzeigename ist angegeben und entspricht den DSC-Benennungskonventionen.</span><span class="sxs-lookup"><span data-stu-id="5f063-122">Friendly name is specified and confirms to DSC naming conventions</span></span>

<span data-ttu-id="5f063-123">Beispiel: ```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```</span><span class="sxs-lookup"><span data-stu-id="5f063-123">Example: ```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```</span></span>

- <span data-ttu-id="5f063-124">Jedes Feld hat eine aussagekräftige Beschreibung.</span><span class="sxs-lookup"><span data-stu-id="5f063-124">Every field has meaningful description.</span></span> <span data-ttu-id="5f063-125">Das PowerShell-GitHub-Repository enthält gute Beispiele, z.B. [die Datei „.schema.mof“ für „xRemoteFile“](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span><span class="sxs-lookup"><span data-stu-id="5f063-125">The PowerShell GitHub repository has good examples, such as [the .schema.mof for xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span></span>

<span data-ttu-id="5f063-126">Sie sollten darüber hinaus die Cmdlets **Test-xDscResource** und **Test-xDscSchema** im [DSC-Ressourcen-Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) verwenden, um die Ressource und das Schema automatisch zu überprüfen:</span><span class="sxs-lookup"><span data-stu-id="5f063-126">Additionally, you should use **Test-xDscResource** and **Test-xDscSchema** cmdlets from [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) to automatically verify the resource and schema:</span></span>
```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```
<span data-ttu-id="5f063-127">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="5f063-127">For example:</span></span>
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a><span data-ttu-id="5f063-128">Ressource wird ohne Fehler geladen.</span><span class="sxs-lookup"><span data-stu-id="5f063-128">Resource loads without errors</span></span> ##
<span data-ttu-id="5f063-129">Überprüfen Sie, ob das Ressourcenmodul erfolgreich geladen werden kann.</span><span class="sxs-lookup"><span data-stu-id="5f063-129">Check whether the resource module can be successfully loaded.</span></span>
<span data-ttu-id="5f063-130">Dies kann manuell erfolgen, indem `Import-Module <resource_module> -force ` ausgeführt und bestätigt wird, dass keine Fehler aufgetreten sind. Sie können auch einen automatisierten Test schreiben.</span><span class="sxs-lookup"><span data-stu-id="5f063-130">This can be achieved manually, by running `Import-Module <resource_module> -force ` and confirming that no errors occurred, or by writing test automation.</span></span> <span data-ttu-id="5f063-131">Im letzteren Fall können Sie diese Struktur bei Ihrem Testfall befolgen:</span><span class="sxs-lookup"><span data-stu-id="5f063-131">In case of the latter, you can follow this structure in your test case:</span></span>
```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```
## <a name="resource-is-idempotent-in-the-positive-case"></a><span data-ttu-id="5f063-132">Die Ressource ist im positiven Sinn idempotent</span><span class="sxs-lookup"><span data-stu-id="5f063-132">Resource is idempotent in the positive case</span></span>
<span data-ttu-id="5f063-133">Eines der grundlegenden Merkmale von DSC-Ressourcen ist die Idempotenz.</span><span class="sxs-lookup"><span data-stu-id="5f063-133">One of the fundamental characteristics of DSC resources is be idempotence.</span></span> <span data-ttu-id="5f063-134">Dies bedeutet, dass beim Anwenden einer DSC-Konfiguration, die diese Ressource mehrmals enthält, immer das gleiche Ergebnis erreicht wird.</span><span class="sxs-lookup"><span data-stu-id="5f063-134">It means that applying a DSC configuration containing that resource multiple times will always achieve the same result.</span></span> <span data-ttu-id="5f063-135">Angenommen, wir erstellen eine Konfiguration mit der folgenden „File“-Ressource:</span><span class="sxs-lookup"><span data-stu-id="5f063-135">For example, if we create a configuration which contains the following File resource:</span></span>
```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```
<span data-ttu-id="5f063-136">Nach dem ersten Anwenden sollte die Datei „Test.txt“ im Ordner „C:\test“ enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="5f063-136">After applying it for the first time, file test.txt should appear in C:\test folder.</span></span> <span data-ttu-id="5f063-137">Bei nachfolgenden Ausführungen derselben Konfiguration sollte sich der Zustand des Computers nicht ändern (d.h. keine Kopien der Datei „Test.txt“ sollten erstellt werden).</span><span class="sxs-lookup"><span data-stu-id="5f063-137">However, subsequent runs of the same configuration should not change the state of the machine (e.g. no copies of the test.txt file should be created).</span></span>
<span data-ttu-id="5f063-138">Um sicherzustellen, dass eine Ressource idempotent ist, können Sie beim direkten Testen der Ressource **Set-TargetResource** wiederholt aufrufen. Bei End-to-End-Tests können Sie **Start-DscConfiguration** mehrmals aufrufen.</span><span class="sxs-lookup"><span data-stu-id="5f063-138">To ensure a resource is idempotent you can repeatedly call **Set-TargetResource** when testing the resource directly, or call **Start-DscConfiguration** multiple times when doing end to end testing.</span></span> <span data-ttu-id="5f063-139">Das Ergebnis sollte nach jeder Ausführung identisch sein.</span><span class="sxs-lookup"><span data-stu-id="5f063-139">The result should be the same after every run.</span></span>


## <a name="test-user-modification-scenario"></a><span data-ttu-id="5f063-140">Testen des Benutzeränderungsszenarios</span><span class="sxs-lookup"><span data-stu-id="5f063-140">Test user modification scenario</span></span> ##
<span data-ttu-id="5f063-141">Sie können sicherstellen, dass **Set-TargetResource** und **Test-TargetResource** ordnungsgemäß funktionieren, indem Sie den Zustand des Computers ändern und DSC anschließend erneut ausführen.</span><span class="sxs-lookup"><span data-stu-id="5f063-141">By changing the state of the machine and then rerunning DSC, you can verify that **Set-TargetResource** and **Test-TargetResource** function properly.</span></span> <span data-ttu-id="5f063-142">Führen Sie dazu die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="5f063-142">Here are steps you should take:</span></span>
1.  <span data-ttu-id="5f063-143">Beginnen Sie mit einer Ressource, die nicht im gewünschten Zustand ist.</span><span class="sxs-lookup"><span data-stu-id="5f063-143">Start with the resource not in the desired state.</span></span>
2.  <span data-ttu-id="5f063-144">Wenden Sie eine Konfiguration auf die Ressource an.</span><span class="sxs-lookup"><span data-stu-id="5f063-144">Run configuration with your resource</span></span>
3.  <span data-ttu-id="5f063-145">Überprüfen Sie, ob **Test-DscConfiguration** „True“ zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="5f063-145">Verify **Test-DscConfiguration** returns True</span></span>
4.  <span data-ttu-id="5f063-146">Ändern Sie das konfigurierte Element dahingehend, dass es dem gewünschten Zustand nicht mehr entspricht.</span><span class="sxs-lookup"><span data-stu-id="5f063-146">Modify the configured item to be out of the desired state</span></span>
5.  <span data-ttu-id="5f063-147">Überprüfen Sie, ob **Test-DscConfiguration** „False“ zurückgibt. Hier ein konkreteres Beispiel der Ressource „Registry“:</span><span class="sxs-lookup"><span data-stu-id="5f063-147">Verify **Test-DscConfiguration** returns false Here’s a more concrete example using Registry resource:</span></span>
1.  <span data-ttu-id="5f063-148">Beginnen Sie mit einem Registrierungsschlüssel, der nicht im gewünschten Zustand ist.</span><span class="sxs-lookup"><span data-stu-id="5f063-148">Start with registry key not in the desired state</span></span>
2.  <span data-ttu-id="5f063-149">Führen Sie **Start-DscConfiguration** mit einer Konfiguration aus, um sie in den gewünschten Zustand zu versetzen, der eine Überprüfung besteht.</span><span class="sxs-lookup"><span data-stu-id="5f063-149">Run **Start-DscConfiguration** with a configuration to put it in the desired state and verify it passes.</span></span>
3.  <span data-ttu-id="5f063-150">Führen Sie **Test-DscConfiguration** aus, und prüfen Sie, ob „True“ zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="5f063-150">Run **Test-DscConfiguration** and verify it returns true</span></span>
4.  <span data-ttu-id="5f063-151">Ändern Sie den Wert des Schlüssels so, dass er sich nicht im gewünschten Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="5f063-151">Modify the value of the key so that it is not in the desired state</span></span>
5.  <span data-ttu-id="5f063-152">Führen Sie **Test-DscConfiguration** aus, und prüfen Sie, ob „False“ zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="5f063-152">Run **Test-DscConfiguration** and verify it returns false</span></span>
6.  <span data-ttu-id="5f063-153">Überprüfen von „Get-TargetResource“-Funktionalität mit „Get-DscConfiguration“</span><span class="sxs-lookup"><span data-stu-id="5f063-153">Get-TargetResource functionality was verified using Get-DscConfiguration</span></span>

<span data-ttu-id="5f063-154">„Get-TargetResource“ sollte Details zum aktuellen Zustand der Ressource zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="5f063-154">Get-TargetResource should return details of the current state of the resource.</span></span> <span data-ttu-id="5f063-155">Testen Sie die Konfiguration durch Aufrufen von „Get-DscConfiguration“ nachdem Sie sie angewendet haben, und stellen Sie sicher, dass die Ausgabe den aktuellen Zustand des Computers ordnungsgemäß widerspiegelt.</span><span class="sxs-lookup"><span data-stu-id="5f063-155">Make sure to test it by calling Get-DscConfiguration after you apply the configuration and verifying that output correctly reflects the current state of the machine.</span></span> <span data-ttu-id="5f063-156">Es müssen unbedingt getrennte Tests erfolgen, da Probleme in diesem Bereich nicht auftauchen, wenn „Start-DscConfiguration“ aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="5f063-156">It's important to test it separately, since any issues in this area won't appear when calling Start-DscConfiguration.</span></span>

## <a name="call-getsettest-targetresource-functions-directly"></a><span data-ttu-id="5f063-157">Direktes Aufrufen der **Get/Set/Test-TargetResource**-Funktionen</span><span class="sxs-lookup"><span data-stu-id="5f063-157">Call **Get/Set/Test-TargetResource** functions directly</span></span> ##

<span data-ttu-id="5f063-158">Stellen Sie sicher, dass Sie die **Get/Set/Test-TargetResource**-Funktionen testen, die in Ihrer Ressource implementiert sind, indem Sie sie direkt aufrufen und sicherstellen, dass sie erwartungsgemäß funktionieren.</span><span class="sxs-lookup"><span data-stu-id="5f063-158">Make sure you test the **Get/Set/Test-TargetResource** functions implemented in your resource by calling them directly and verifying that they work as expected.</span></span>

## <a name="verify-end-to-end-using-start-dscconfiguration"></a><span data-ttu-id="5f063-159">End-to-End-Überprüfen der Ressource mithilfe von **Start-DscConfiguration**</span><span class="sxs-lookup"><span data-stu-id="5f063-159">Verify End to End using **Start-DscConfiguration**</span></span> ##

<span data-ttu-id="5f063-160">Das Testen von **Get/Set/Test-TargetResource**-Funktionen, indem sie direkt aufgerufen werden, ist wichtig, doch auf diese Weise werden nicht alle Probleme ermittelt.</span><span class="sxs-lookup"><span data-stu-id="5f063-160">Testing **Get/Set/Test-TargetResource** functions by calling them directly is important, but not all issues will be discovered this way.</span></span> <span data-ttu-id="5f063-161">Konzentrieren Sie einen wesentlichen Teil Ihrer Tests auf das Verwenden von **Start-DscConfiguration** oder des Pullservers.</span><span class="sxs-lookup"><span data-stu-id="5f063-161">You should focus significant part of your testing on using **Start-DscConfiguration** or the pull server.</span></span> <span data-ttu-id="5f063-162">Benutzer verwenden die Ressource genau so, weshalb Sie die Bedeutung dieser Art von Tests nicht unterschätzen sollten.</span><span class="sxs-lookup"><span data-stu-id="5f063-162">In fact, this is how users will use the resource, so don’t underestimate the significance of this type of tests.</span></span>
<span data-ttu-id="5f063-163">Mögliche Problemtypen:</span><span class="sxs-lookup"><span data-stu-id="5f063-163">Possible types of issues:</span></span>
- <span data-ttu-id="5f063-164">Das Verhalten von Anmeldeinformationen oder der Sitzung ist möglicherweise anders, da der DSC-Agent als Dienst ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5f063-164">Credential/Session may behave differently because the DSC agent runs as a service.</span></span>  <span data-ttu-id="5f063-165">Führen Sie in diesem Bereich auf jeden Fall End-to-End-Tests von Features durch.</span><span class="sxs-lookup"><span data-stu-id="5f063-165">Be sure to test any features here end to end.</span></span>
- <span data-ttu-id="5f063-166">Von **Start-DscConfiguration** ausgegebene Fehler sind ggf. anders als die, die angezeigt werden, wenn die Funktion **Set-TargetResource** direkt aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="5f063-166">Errors output by **Start-DscConfiguration** may be different than those displayed when calling the **Set-TargetResource** function directly.</span></span>

## <a name="test-compatability-on-all-dsc-supported-platforms"></a><span data-ttu-id="5f063-167">Testen der Kompatibilität auf allen DSC-unterstützten Plattformen</span><span class="sxs-lookup"><span data-stu-id="5f063-167">Test compatability on all DSC supported platforms</span></span> ##
<span data-ttu-id="5f063-168">Die Ressource sollte auf allen von DSC unterstützten Plattformen funktionieren (Windows Server 2008 R2 und höher).</span><span class="sxs-lookup"><span data-stu-id="5f063-168">Resource should work on all DSC supported platforms (Windows Server 2008 R2 and newer).</span></span> <span data-ttu-id="5f063-169">Installieren Sie für Ihr Betriebssystem das neueste WMF (Windows Management Framework), um die neueste DSC-Version zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5f063-169">Install the latest WMF (Windows Management Framework) on your OS to get the latest version of DSC.</span></span> <span data-ttu-id="5f063-170">Wenn Ihre Ressource einige dieser Plattformen entwurfsbedingt nicht unterstützt, sollte eine bestimmte Fehlermeldung zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="5f063-170">If your resource does not work on some of these platforms by design, a specific error message should be returned.</span></span> <span data-ttu-id="5f063-171">Stellen Sie außerdem sicher, dass die Ressource überprüft, ob die Cmdlets, die Sie aufrufen, auf einem bestimmten Computer vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="5f063-171">Also, make sure your resource checks whether cmdlets you are calling are present on particular machine.</span></span> <span data-ttu-id="5f063-172">Windows Server 2012 wurde eine große Anzahl neuer Cmdlets hinzugefügt, die unter Windows Server 2008 R2, sogar mit installiertem WMF, nicht verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="5f063-172">Windows Server 2012 added a large number of new cmdlets that are not available on Windows Server 2008R2, even with WMF installed.</span></span>

## <a name="verify-on-windows-client-if-applicable"></a><span data-ttu-id="5f063-173">Überprüfen auf Windows-Client (falls zutreffend)</span><span class="sxs-lookup"><span data-stu-id="5f063-173">Verify on Windows Client (if applicable)</span></span> ##
<span data-ttu-id="5f063-174">Sehr häufig wird bei Tests die Ressource nur auf den Serverversionen von Windows zu überprüft.</span><span class="sxs-lookup"><span data-stu-id="5f063-174">One very common test gap is verifying the resource only on server versions of Windows.</span></span> <span data-ttu-id="5f063-175">Viele Ressourcen sind aber auch für Client-SKUs konzipiert. Vergessen Sie daher nicht, wenn dies für Sie gilt, sie auf diesen Plattformen ebenfalls zu testen.</span><span class="sxs-lookup"><span data-stu-id="5f063-175">Many resources are also designed to work on Client SKUs, so if that’s true in your case, don’t forget to test it on those platforms as well.</span></span>
## <a name="get-dscresource-lists-the-resource"></a><span data-ttu-id="5f063-176">Auflisten der Ressourcen mit „Get-DSCResource“</span><span class="sxs-lookup"><span data-stu-id="5f063-176">Get-DSCResource lists the resource</span></span> ##
<span data-ttu-id="5f063-177">Nach der Bereitstellung des Moduls sollte ein Aufruf von „Get-DscResource“ u.a. Ihre Ressource im Ergebnis auflisten.</span><span class="sxs-lookup"><span data-stu-id="5f063-177">After deploying the module, calling Get-DscResource should list your resource among others as a result.</span></span> <span data-ttu-id="5f063-178">Wenn Sie die Ressource nicht finden können, stellen Sie sicher, dass die Datei „schema.mof“ für die Ressource vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="5f063-178">If you can’t find your resource in the list, make sure that schema.mof file for that resource exists.</span></span>
## <a name="resource-module-contains-examples"></a><span data-ttu-id="5f063-179">Ressourcenmodul enthält Beispiele</span><span class="sxs-lookup"><span data-stu-id="5f063-179">Resource module contains examples</span></span> ##
<span data-ttu-id="5f063-180">Erstellen Sie anschauliche Beispiele, die anderen helfen, die Verwendung zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="5f063-180">Creating quality examples which will help others understand how to use it.</span></span> <span data-ttu-id="5f063-181">Dies ist entscheidend, insbesondere seitdem viele Benutzer Beispielcode als Dokumentation behandeln.</span><span class="sxs-lookup"><span data-stu-id="5f063-181">This is crucial, especially since many users treat sample code as documentation.</span></span>
- <span data-ttu-id="5f063-182">Zunächst sollten Sie die Beispiele bestimmen, die Sie dem Modul hinzufügen möchten. Zumindest sollten die wichtigsten Anwendungsfälle für Ihre Ressource abgedeckt werden:</span><span class="sxs-lookup"><span data-stu-id="5f063-182">First, you should determine the examples that will be included with the module – at minimum, you should cover most important use cases for your resource:</span></span>
- <span data-ttu-id="5f063-183">Wenn Ihr Modul mehrere Ressourcen enthält, die für ein End-to-End-Szenario zusammenarbeiten müssen, bietet sich idealerweise das grundlegende End-to-End-Beispiel als Erstes an.</span><span class="sxs-lookup"><span data-stu-id="5f063-183">If your module contains several resources that need to work together for an end-to-end scenario, the basic end-to-end example would ideally be first.</span></span>
- <span data-ttu-id="5f063-184">Die anfänglichen Beispiele sollten sehr einfach sein und die ersten Schritte mit Ihren Ressourcen in kurzen, übersichtlichen Abschnitten erläutern (z. B. das Erstellen einer neuen virtuellen Festplatte [VHD]).</span><span class="sxs-lookup"><span data-stu-id="5f063-184">The initial examples should be very simple -- how to get started with your resources in small manageable chunks (e.g. creating a new VHD)</span></span>
- <span data-ttu-id="5f063-185">Nachfolgende Beispiele sollten auf diesen Beispielen aufbauen (z. b. Erstellen einer VM anhand einer VHD, Entfernen einer VM, Ändern einer VM) und erweiterte Funktionen veranschaulichen (z. B. das Erstellen einer VM mit dynamischem Arbeitsspeicher).</span><span class="sxs-lookup"><span data-stu-id="5f063-185">Subsequent examples should build on those examples (e.g. creating a VM from a VHD, removing VM, modifying VM), and show advanced functionality (e.g. creating a VM with dynamic memory)</span></span>
- <span data-ttu-id="5f063-186">Beispielkonfigurationen sollten parametrisiert sein (alle Werte sollten als Parameter an die Konfiguration übergeben werden, und es darf keine hartcodierten Werte geben):</span><span class="sxs-lookup"><span data-stu-id="5f063-186">Example configurations should be parameterized (all values should be passed to the configuration as parameters and there should be no hardcoded values):</span></span>
```powershell
configuration Sample_xRemoteFile_DownloadFile
{
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
}
```
- <span data-ttu-id="5f063-187">Es empfiehlt sich, am Ende des Beispielskripts ein (auskommentiertes) Beispiel hinzuzufügen, wie die Konfiguration mit den tatsächlichen Werte aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="5f063-187">It’s a good practice to include (commented out) example of how to call the configuration with the actual values at the end of the example script.</span></span>
<span data-ttu-id="5f063-188">Aus der obigen Konfiguration geht beispielsweise nicht unbedingt hervor, dass die beste Möglichkeit zum Angeben von „UserAgent“ wie folgt aussieht:</span><span class="sxs-lookup"><span data-stu-id="5f063-188">For example, in the configuration above it isn't neccessarily obvious that the best way to specify UserAgent is:</span></span>

<span data-ttu-id="5f063-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In diesem Fall kann ein Kommentar die beabsichtigte Ausführung der Konfiguration verdeutlichen:</span><span class="sxs-lookup"><span data-stu-id="5f063-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In which case a comment can clarify the intended execution of the configuration:</span></span>
```
<#
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>
```
- <span data-ttu-id="5f063-190">Schreiben Sie für jedes Beispiel eine kurze Beschreibung mit einer Erläuterung der Funktionsweise und Bedeutung der Parameter.</span><span class="sxs-lookup"><span data-stu-id="5f063-190">For each example, write a short description which explains what it does, and the meaning of the parameters.</span></span>
- <span data-ttu-id="5f063-191">Vergewissern Sie sich, dass die Beispiele die meisten wichtigen Szenarien für Ihre Ressource abdecken. Wenn nichts fehlt, überprüfen Sie, dass sie alle ausgeführt werden und den Computer in den gewünschten Zustand versetzen.</span><span class="sxs-lookup"><span data-stu-id="5f063-191">Make sure examples cover most the important scenarios for your resource and if there’s nothing missing, verify that they all execute and put machine in the desired state.</span></span>

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a><span data-ttu-id="5f063-192">Leicht verständliche Fehlermeldungen helfen Benutzern bei der Problembehebung</span><span class="sxs-lookup"><span data-stu-id="5f063-192">Error messages are easy to understand and help users solve problems</span></span> ##
<span data-ttu-id="5f063-193">Gute Fehlermeldungen zeichnen sich wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="5f063-193">Good error messages should be:</span></span>
- <span data-ttu-id="5f063-194">Ihr Vorhandensein: Das größte Problem bei Fehlermeldungen besteht darin, dass sie häufig nicht vorhanden sind. Achten Sie deshalb darauf, dass sie vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="5f063-194">There: The biggest problem with error messages is that they often don’t exist, so make sure they are there.</span></span>
- <span data-ttu-id="5f063-195">Einfach zu verstehende, von Menschen lesbare, nicht kryptische Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="5f063-195">Easy to understand: Human readable, no obscure error codes</span></span>
- <span data-ttu-id="5f063-196">Genaue Beschreibung, was das Problem ist.</span><span class="sxs-lookup"><span data-stu-id="5f063-196">Precise: Describe what’s exactly the problem</span></span>
- <span data-ttu-id="5f063-197">Konstruktive Ratschläge zum Beheben des Problems.</span><span class="sxs-lookup"><span data-stu-id="5f063-197">Constructive: Advice how to fix the issue</span></span>
- <span data-ttu-id="5f063-198">Höfliche Informationen, die dem Benutzer nicht die Schuld geben oder ihm ein schlechtes Gefühl vermitteln. Stellen Sie sicher, dass Sie Fehler in End-to-End-Szenarien (mit **Start-DscConfiguration**) überprüfen, da sie sich von denjenigen unterscheiden können, die bei direkter Ausführung von Ressourcenfunktionen zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="5f063-198">Polite: Don’t blame user or make them feel bad Make sure you verify errors in End to End scenarios (using **Start-DscConfiguration**), because they may differ from those returned when running resource functions directly.</span></span>

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a><span data-ttu-id="5f063-199">Protokollmeldungen sind leicht verständlich und informativ (z. B. „–verbose“, „–debug“ und ETW-Protokolle)</span><span class="sxs-lookup"><span data-stu-id="5f063-199">Log messages are easy to understand and informative (including –verbose, –debug and ETW logs)</span></span> ##
<span data-ttu-id="5f063-200">Stellen Sie sicher, dass Protokolle, die von der Ressource ausgegeben werden, leicht verständlich und für den Benutzer von Nutzen sind.</span><span class="sxs-lookup"><span data-stu-id="5f063-200">Ensure that logs outputted by the resource are easy to understand and provide value to the user.</span></span> <span data-ttu-id="5f063-201">Ressourcen sollten alle Informationen ausgeben, die für den Benutzer hilfreich sind, doch mehr Protokolle sind nicht unbedingt besser.</span><span class="sxs-lookup"><span data-stu-id="5f063-201">Resources should output all information which might be helpful to the user, but more logs is not always better.</span></span> <span data-ttu-id="5f063-202">Sie sollten das Ausgeben redundanter Daten ohne Mehrwert unbedingt vermeiden. Lassen Sie Benutzer nicht Hunderte von Protokolleinträgen durchlaufen, damit sie finden, was sie suchen.</span><span class="sxs-lookup"><span data-stu-id="5f063-202">You should avoid redundancy and outputting data which does not provide additional value – don’t make someone go through hundreds of log entries in order to find what they're looking for.</span></span> <span data-ttu-id="5f063-203">Keine Protokolle sind freilich keine akzeptable Lösung dieses Problems.</span><span class="sxs-lookup"><span data-stu-id="5f063-203">Of course, no logs is not an acceptable solution for this problem either.</span></span>

<span data-ttu-id="5f063-204">Beim Testen sollten Sie auch ausführliche und Debugprotokolle (durch Ausführen von **Start-DscConfiguration** mit den Schaltern „–verbose“ und „–debug“) sowie ETW-Protokolle analysieren.</span><span class="sxs-lookup"><span data-stu-id="5f063-204">When testing, you should also analyze verbose and debug logs (by running **Start-DscConfiguration** with –verbose and –debug switches appropriately), as well as ETW logs.</span></span> <span data-ttu-id="5f063-205">Um ETW-Protokolle für DSC anzuzeigen, wechseln Sie zur Ereignisanzeige, und öffnen Sie den folgenden Ordner: Anwendungen und Dienste -> Microsoft -> Windows -> Konfiguration für den gewünschten Zustand.</span><span class="sxs-lookup"><span data-stu-id="5f063-205">To see DSC ETW logs, go to Event Viewer and open the following folder: Applications and Services- Microsoft - Windows - Desired State Configuration.</span></span>  <span data-ttu-id="5f063-206">In der Standardeinstellung gibt es den Kanal „Betriebsbereit“. Aktivieren Sie vor dem Ausführen der Konfiguration jedoch auch die Kanäle „Analyse“ und „Debuggen“.</span><span class="sxs-lookup"><span data-stu-id="5f063-206">By default there will be Operational channel, but make sure you enable Analytic and Debug channels before running the configuration.</span></span>
<span data-ttu-id="5f063-207">Zum Aktivieren der Kanäle „Analyse/Debuggen“ können Sie das folgende Skript ausführen:</span><span class="sxs-lookup"><span data-stu-id="5f063-207">To enable Analytic/Debug channels, you can execute script below:</span></span>
```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```
## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a><span data-ttu-id="5f063-208">Ressourcenimplementierung ohne hartcodierte Pfade</span><span class="sxs-lookup"><span data-stu-id="5f063-208">Resource implementation does not contain hardcoded paths</span></span> ##
<span data-ttu-id="5f063-209">Vergewissern Sie sich, dass es in der Ressourcenimplementierung keine hartcodierten Pfade gibt, insbesondere wenn diese eine Sprache voraussetzen (z. B. en-us), oder wenn es Systemvariablen gibt, die verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="5f063-209">Ensure there are no hardcoded paths in the resource implementation, particularly if they assume language (en-us), or when there are system variables that can be used.</span></span>
<span data-ttu-id="5f063-210">Wenn Ihre Ressource auf bestimmte Pfade zugreifen muss, verwenden Sie Umgebungsvariablen anstelle eines hartcodierten Pfads, da sich dieser je nach Computer unterscheiden kann.</span><span class="sxs-lookup"><span data-stu-id="5f063-210">If your resource need to access specific paths, use environment variables instead of hardcoding the path, as it may differ on other machines.</span></span>

<span data-ttu-id="5f063-211">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="5f063-211">Example:</span></span>

<span data-ttu-id="5f063-212">Anstelle von:</span><span class="sxs-lookup"><span data-stu-id="5f063-212">Instead of:</span></span>
```
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
 ```
<span data-ttu-id="5f063-213">Können Sie Folgendes schreiben:</span><span class="sxs-lookup"><span data-stu-id="5f063-213">You can write:</span></span>
```
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```
## <a name="resource-implementation-does-not-contain-user-information"></a><span data-ttu-id="5f063-214">Ressourcenimplementierung ohne Benutzerinformationen</span><span class="sxs-lookup"><span data-stu-id="5f063-214">Resource implementation does not contain user information</span></span> ##
<span data-ttu-id="5f063-215">Stellen Sie sicher, dass im Code keine E-Mail-Adressen, Kontoinformationen oder Namen von Personen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="5f063-215">Make sure there are no email names, account information, or names of people in the code.</span></span>
## <a name="resource-was-tested-with-validinvalid-credentials"></a><span data-ttu-id="5f063-216">Ressourcentests mit gültigen/ungültigen Anmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="5f063-216">Resource was tested with valid/invalid credentials</span></span> ##
<span data-ttu-id="5f063-217">Wenn Ihre Ressource Anmeldeinformationen als Parameter verwendet:</span><span class="sxs-lookup"><span data-stu-id="5f063-217">If your resource takes a credential as parameter:</span></span>
- <span data-ttu-id="5f063-218">Überprüfen Sie, ob die Ressource funktioniert, wenn das lokale System (oder das Computerkonto für Remoteressourcen) keinen Zugriff hat.</span><span class="sxs-lookup"><span data-stu-id="5f063-218">Verify the resource works when Local System (or the computer account for remote resources) does not have access.</span></span>
- <span data-ttu-id="5f063-219">Überprüfen Sie, ob die Ressource mit für „Get“, „Set“ und „Test“ angegebenen Anmeldeinformationen funktioniert.</span><span class="sxs-lookup"><span data-stu-id="5f063-219">Verify the resource works with a credential specified for Get, Set and Test</span></span>
- <span data-ttu-id="5f063-220">Wenn die Ressource auf Freigaben zugreift, testen Sie alle Varianten, die Sie unterstützen müssen, wie z.B.:</span><span class="sxs-lookup"><span data-stu-id="5f063-220">If your resource accesses shares, test all the variants you need to support, such as:</span></span>
  - <span data-ttu-id="5f063-221">Windows-Standardfreigaben.</span><span class="sxs-lookup"><span data-stu-id="5f063-221">Standard windows shares.</span></span>
  - <span data-ttu-id="5f063-222">DFS-Freigaben</span><span class="sxs-lookup"><span data-stu-id="5f063-222">DFS shares.</span></span>
  - <span data-ttu-id="5f063-223">SAMBA-Freigaben (wenn Sie Linux unterstützen möchten)</span><span class="sxs-lookup"><span data-stu-id="5f063-223">SAMBA shares (if you want to support Linux.)</span></span>

## <a name="resource-does-not-require-interactive-input"></a><span data-ttu-id="5f063-224">Die Ressource benötigt keine interaktive Eingabe</span><span class="sxs-lookup"><span data-stu-id="5f063-224">Resource does not require interactive input</span></span> ##
<span data-ttu-id="5f063-225">**Get/Set/Test-TargetResource**-Funktionen sollen automatisch ausgeführt werden und in keiner Phase der Ausführung auf Benutzereingaben warten (platzieren Sie deshalb **Get-Credential** nicht innerhalb dieser Funktionen).</span><span class="sxs-lookup"><span data-stu-id="5f063-225">**Get/Set/Test-TargetResource** functions should be executed automatically and must not wait for user’s input at any stage of execution (e.g. you should not use **Get-Credential** inside these functions).</span></span> <span data-ttu-id="5f063-226">Wenn Sie Benutzereingaben bereitstellen müssen, sollten Sie sie in der Kompilierungsphase als Parameter an die Konfiguration übergeben.</span><span class="sxs-lookup"><span data-stu-id="5f063-226">If you need to provide user’s input, you should pass it to the configuration as parameter during the compilation phase.</span></span>
## <a name="resource-functionality-was-thoroughly-tested"></a><span data-ttu-id="5f063-227">Gründliches Testen der Ressourcenfunktionalität</span><span class="sxs-lookup"><span data-stu-id="5f063-227">Resource functionality was thoroughly tested</span></span> ##
<span data-ttu-id="5f063-228">Diese Prüfliste enthält Elemente, die unbedingt getestet werden sollten und/oder oft übersehen werden.</span><span class="sxs-lookup"><span data-stu-id="5f063-228">This checklist contains items which are important to be tested and/or are often missed.</span></span> <span data-ttu-id="5f063-229">Es gibt eine Vielzahl von Tests, hauptsächlich Funktionstests, die spezifisch für die Ressource sind, die Sie testen, und hier nicht erwähnt werden.</span><span class="sxs-lookup"><span data-stu-id="5f063-229">There will be bunch of tests, mainly functional ones which will be specific to the resource you are testing and are not mentioned here.</span></span> <span data-ttu-id="5f063-230">Vergessen Sie nicht die negativen Testfälle.</span><span class="sxs-lookup"><span data-stu-id="5f063-230">Don’t forget about negative test cases.</span></span>
## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a><span data-ttu-id="5f063-231">Bewährte Methode: Ressourcenmodul enthält den Ordner „Tests“ mit dem Skript „ResourceDesignerTests.ps1“</span><span class="sxs-lookup"><span data-stu-id="5f063-231">Best practice: Resource module contains Tests folder with ResourceDesignerTests.ps1 script</span></span> ##
<span data-ttu-id="5f063-232">Es empfiehlt sich, im Ressourcenmodul den Ordner „Tests“ anzulegen, die Datei „ResourceDesignerTests.ps1“ zu erstellen und über **Test-xDscResource** und **Test-xDscSchema** Tests für alle Ressourcen in einem bestimmten Modul hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="5f063-232">It’s a good practice to create folder “Tests” inside resource module, create ResourceDesignerTests.ps1 file and add tests using **Test-xDscResource** and **Test-xDscSchema** for all resources in given module.</span></span>
<span data-ttu-id="5f063-233">Auf diese Weise können Sie schnell die Schemas aller Ressourcen aus den angegebenen Modulen überprüfen und vor der Veröffentlichung eine Integritätsprüfung vornehmen.</span><span class="sxs-lookup"><span data-stu-id="5f063-233">This way you can quickly validate schemas of all resources from the given modules and do a sanity check before publishing.</span></span>
<span data-ttu-id="5f063-234">Für „xRemoteFile“ kann „ResourceTests.ps1“ einfach so aussehen:</span><span class="sxs-lookup"><span data-stu-id="5f063-234">For xRemoteFile, ResourceTests.ps1 could look as simple as:</span></span>
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```
##<a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a><span data-ttu-id="5f063-235">Bewährte Methode: Ressourcenordner enthält Ressourcen-Designer-Skript zum Generieren des Schemas##</span><span class="sxs-lookup"><span data-stu-id="5f063-235">Best practice: Resource folder contains resource designer script for generating schema##</span></span>
<span data-ttu-id="5f063-236">Jede Ressource sollte ein Ressourcen-Designer-Skript enthalten, mit dem ein MOF-Schema der Ressource generiert wird.</span><span class="sxs-lookup"><span data-stu-id="5f063-236">Each resource should contain a resource designer script which generates a mof schema of the resource.</span></span> <span data-ttu-id="5f063-237">Diese Datei sollte in <ResourceName>\ResourceDesignerScripts abgelegt und „Generate<ResourceName>Schema.ps1“ genannt werden. Bei der Ressource „xRemoteFile“ würde diese Datei „GenerateXRemoteFileSchema.ps1“ heißen und Folgendes beinhalten:</span><span class="sxs-lookup"><span data-stu-id="5f063-237">This file should be placed in <ResourceName>\ResourceDesignerScripts and be named Generate<ResourceName>Schema.ps1 For xRemoteFile resource this file would be called GenerateXRemoteFileSchema.ps1 and contain:</span></span>
```powershell
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.'
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile
```
## <a name="best-practice-resource-supports--whatif"></a><span data-ttu-id="5f063-238">Bewährte Methode: Die Ressource unterstützt „-whatif“</span><span class="sxs-lookup"><span data-stu-id="5f063-238">Best practice: Resource supports -whatif</span></span> ##
<span data-ttu-id="5f063-239">Wenn mit der Ressource „gefährliche“ Vorgänge ausgeführt werden, empfiehlt es sich, „-whatif“-Funktionalität zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="5f063-239">If your resource is performing “dangerous” operations, it’s a good practice to implement -whatif functionality.</span></span> <span data-ttu-id="5f063-240">Nachdem dies erfolgt ist, stellen Sie sicher, dass die „whatif“-Ausgabe Vorgänge ordnungsgemäß beschreibt, die eintreten würden, wenn der Befehl ohne den Schalter „whatif“ ausgeführt würde.</span><span class="sxs-lookup"><span data-stu-id="5f063-240">After it’s done, make sure that whatif output correctly describes operations which would happen if command was executed without whatif switch.</span></span>
<span data-ttu-id="5f063-241">Vergewissern Sie sich auch, dass wenn der Schalter „-whatif“ vorhanden ist, keine Vorgänge ausgeführt werden (d. h. keine Änderungen am Zustand des Knotens erfolgen).</span><span class="sxs-lookup"><span data-stu-id="5f063-241">Also, verify that operations does not execute (no changes to the node’s state are made) when –whatif switch is present.</span></span>
<span data-ttu-id="5f063-242">Angenommen, wir testen die Ressource „File“.</span><span class="sxs-lookup"><span data-stu-id="5f063-242">For example, let’s assume we are testing File resource.</span></span> <span data-ttu-id="5f063-243">Nachstehend finden Sie einfache Konfiguration, die die Datei „test.txt“ mit dem Inhalt „test“ erstellt:</span><span class="sxs-lookup"><span data-stu-id="5f063-243">Below is simple configuration which creates file “test.txt” with contents “test”:</span></span>
```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```
<span data-ttu-id="5f063-244">Wenn wir die Konfiguration kompilieren und dann mit dem Schalter „-whatif“ ausführen, gibt die Ausgabe genau an, was bei Ausführung der Konfiguration passieren würde.</span><span class="sxs-lookup"><span data-stu-id="5f063-244">If we compile and then execute the configuration with the –whatif switch, the output is telling us exactly what would happen when we run the configuration.</span></span> <span data-ttu-id="5f063-245">Die Konfiguration selbst wurde jedoch nicht ausgeführt (die Datei „test.txt“ wurde nicht erstellt).</span><span class="sxs-lookup"><span data-stu-id="5f063-245">The configuration itself however was not executed (test.txt file was not created).</span></span>
```powershell
Start-DscConfiguration -path .\config -ComputerName localhost -wait -verbose -whatif
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="5f063-246">Diese Liste ist nicht vollständig. Sie deckt jedoch viele wichtige Aspekte ab, die beim Entwerfen, Entwickeln und Testen von DSC-Ressourcen auftreten können.</span><span class="sxs-lookup"><span data-stu-id="5f063-246">This list is not exhaustive, but it covers many important issues which can be encountered while designing, developing and testing DSC resources.</span></span>