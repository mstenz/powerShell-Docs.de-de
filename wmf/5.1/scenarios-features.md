---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Neue Szenarios und Features in WMF 5.1
ms.openlocfilehash: 430781c5c9a59fc544db4f94098313ae1e9cf610
ms.sourcegitcommit: a6ee6e64d369ecf82c730411bed9750278fdb5c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2017
---
# <a name="new-scenarios-and-features-in-wmf-51"></a><span data-ttu-id="717f8-103">Neue Szenarios und Features in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="717f8-103">New Scenarios and Features in WMF 5.1</span></span> #

> <span data-ttu-id="717f8-104">Hinweis: Diese Dokumentation ist vorläufig und kann geändert werden.</span><span class="sxs-lookup"><span data-stu-id="717f8-104">Note: This information is preliminary and subject to change.</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="717f8-105">PowerShell-Editionen</span><span class="sxs-lookup"><span data-stu-id="717f8-105">PowerShell Editions</span></span> ##
<span data-ttu-id="717f8-106">Ab Version 5.1 steht PowerShell in verschiedenen Editionen zur Verfügung, die unterschiedliche Featuregruppen und Plattformkompatibilität bieten.</span><span class="sxs-lookup"><span data-stu-id="717f8-106">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="717f8-107">**Desktop-Edition:** Diese Edition basiert auf .NET Framework und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter Vollversionen von Windows wie Server Core und Windows Desktop ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="717f8-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="717f8-108">**Core-Edition:** Diese Edition basiert auf .NET Core und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter funktionsreduzierten Versionen von Windows wie Nano Server und Windows IoT ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="717f8-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="717f8-109">**Weitere Informationen zur Verwendung von PowerShell-Editionen**</span><span class="sxs-lookup"><span data-stu-id="717f8-109">**Learn more about using PowerShell Editions**</span></span>
- [<span data-ttu-id="717f8-110">Bestimmen der ausgeführten Edition von PowerShell</span><span class="sxs-lookup"><span data-stu-id="717f8-110">Determine running edition of PowerShell</span></span>]()
- [<span data-ttu-id="717f8-111">Deklarieren der Kompatibilität eines Moduls mit bestimmten Versionen von PowerShell</span><span class="sxs-lookup"><span data-stu-id="717f8-111">Declare a module's compatibility to specific PowerShell versions</span></span>]()
- [<span data-ttu-id="717f8-112">Der Filter „Get-Module“ hat „CompatiblePSEditions“ als Ergebnis</span><span class="sxs-lookup"><span data-stu-id="717f8-112">Filter Get-Module results by CompatiblePSEditions</span></span>]()
- [<span data-ttu-id="717f8-113">Verhindern der Ausführung von Skripts außer bei Ausführung in einer kompatiblen Edition von PowerShell</span><span class="sxs-lookup"><span data-stu-id="717f8-113">Prevent script execution unless run on a compatible edition of PowerShell</span></span>]()

## <a name="catalog-cmdlets"></a><span data-ttu-id="717f8-114">Katalog-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="717f8-114">Catalog Cmdlets</span></span>  

<span data-ttu-id="717f8-115">Dem [Microsoft.PowerShell.Security](https://technet.microsoft.com/en-us/library/hh847877.aspx)-Modul wurden zwei neue Cmdlets hinzugefügt, die Windows-Katalogdateien generieren und überprüfen.</span><span class="sxs-lookup"><span data-stu-id="717f8-115">Two new cmdlets have been added in the [Microsoft.PowerShell.Security](https://technet.microsoft.com/en-us/library/hh847877.aspx) module; these generate and validate Windows catalog files.</span></span>  

###<a name="new-filecatalog"></a><span data-ttu-id="717f8-116">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="717f8-116">New-FileCatalog</span></span> 
--------------------------------

<span data-ttu-id="717f8-117">„New-FileCatalog“ erstellt eine Windows-Katalogdatei für eine Gruppe von Ordnern und Dateien.</span><span class="sxs-lookup"><span data-stu-id="717f8-117">New-FileCatalog creates a Windows catalog file for set of folders and files.</span></span> <span data-ttu-id="717f8-118">Diese Katalogdatei enthält die Hashes aller Dateien in bestimmten Pfaden.</span><span class="sxs-lookup"><span data-stu-id="717f8-118">This catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="717f8-119">Benutzer können den Satz von Ordnern zusammen mit den entsprechenden Katalogdateien verteilen, die diese Ordner darstellen.</span><span class="sxs-lookup"><span data-stu-id="717f8-119">Users can distribute the set of folders along with corresponding catalog file representing those folders.</span></span> <span data-ttu-id="717f8-120">Diese Informationen helfen bei der Überprüfung, ob seit der Erstellung des Katalogs Änderungen an den Ordnern vorgenommen wurden.</span><span class="sxs-lookup"><span data-stu-id="717f8-120">This information is useful to validate whether any changes have been made to the folders since catalog creation time.</span></span>    

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="717f8-121">Die Katalogversionen 1 und 2 werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="717f8-121">Catalog versions 1 and 2 are supported.</span></span> <span data-ttu-id="717f8-122">Version 1 verwendet den SHA1-Hashalgorithmus, um Dateihashes zu erstellen, Version 2 verwendet SHA256.</span><span class="sxs-lookup"><span data-stu-id="717f8-122">Version 1 uses the SHA1 hashing algorithm to create file hashes; version 2 uses SHA256.</span></span> <span data-ttu-id="717f8-123">Katalogversion 2 wird weder auf *Windows Server 2008 R2* noch auf *Windows 7* unterstützt.</span><span class="sxs-lookup"><span data-stu-id="717f8-123">Catalog version 2 is not supported on *Windows Server 2008 R2* or *Windows 7*.</span></span> <span data-ttu-id="717f8-124">Daher sollten Sie die Katalogversion 2 mit *Windows 8*, *Windows Server 2012* und späteren Betriebssystemen verwenden.</span><span class="sxs-lookup"><span data-stu-id="717f8-124">You should use catalog version 2 on *Windows 8*, *Windows Server 2012*, and later operating systems.</span></span>  

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="717f8-125">Dadurch wird die Katalogdatei erstellt.</span><span class="sxs-lookup"><span data-stu-id="717f8-125">This creates the catalog file.</span></span> 

![](../images/CatalogFile1.jpg)  

![](../images/CatalogFile2.jpg) 

<span data-ttu-id="717f8-126">Melden Sie sich mit dem Cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) an, um die Integrität der Katalogdatei zu überprüfen (im obigen Beispiel: „pester.cat“).</span><span class="sxs-lookup"><span data-stu-id="717f8-126">To verify the integrity of catalog file (Pester.cat in above example), sign it using [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>   


###<a name="test-filecatalog"></a><span data-ttu-id="717f8-127">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="717f8-127">Test-FileCatalog</span></span> 
--------------------------------

<span data-ttu-id="717f8-128">„Test-FileCatalog“ überprüft den Katalog, der einen Satz von Ordnern darstellt.</span><span class="sxs-lookup"><span data-stu-id="717f8-128">Test-FileCatalog validates the catalog representing a set of folders.</span></span> 

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="717f8-129">Dieses Cmdlet vergleicht alle Dateihashes und deren im *Katalog* enthaltenen relativen Pfade mit denen auf dem *Datenträger*.</span><span class="sxs-lookup"><span data-stu-id="717f8-129">This cmdlet compares all the files hashes and their relative paths found in *catalog* with ones on *disk*.</span></span> <span data-ttu-id="717f8-130">Wenn das Cmdlet eine Unstimmigkeit zwischen den Dateihashes und den Pfaden entdeckt, gibt es den Status *ValidationFailed* zurück.</span><span class="sxs-lookup"><span data-stu-id="717f8-130">If it detects any mismatch between file hashes and paths it returns the status as *ValidationFailed*.</span></span> <span data-ttu-id="717f8-131">Benutzer können alle diese Informationen mithilfe des Parameters *-Detailed* abrufen.</span><span class="sxs-lookup"><span data-stu-id="717f8-131">Users can retrieve all this information by using the *-Detailed* parameter.</span></span> <span data-ttu-id="717f8-132">Dieser Parameter zeigt in der Eigenschaft *Signature* auch den Signierstatus des Katalogs an, was dem Aufruf des Cmdlets [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) in der Katalogdatei entspricht.</span><span class="sxs-lookup"><span data-stu-id="717f8-132">It also displays signing status of catalog in *Signature* property which is equivalent to calling [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet on the catalog file.</span></span> <span data-ttu-id="717f8-133">Benutzer können außerdem jede Datei während der Überprüfung mithilfe des Parameters *-FilesToSkip* überspringen.</span><span class="sxs-lookup"><span data-stu-id="717f8-133">Users can also skip any file during validation by using the *-FilesToSkip* parameter.</span></span> 


## <a name="module-analysis-cache"></a><span data-ttu-id="717f8-134">Die Datei „ModuleAnalysisCache“</span><span class="sxs-lookup"><span data-stu-id="717f8-134">Module Analysis Cache</span></span> ##
<span data-ttu-id="717f8-135">Ab Version 5.1 bietet PowerShell Kontrolle über die Datei, die zum Zwischenspeichern von Daten zu einem Modul verwendet wird, z. B. der Befehle, die es exportiert.</span><span class="sxs-lookup"><span data-stu-id="717f8-135">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="717f8-136">Standardmäßig wird dieser Cache in der Datei `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="717f8-136">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="717f8-137">Der Cache wird in der Regel beim Start der Suche nach einem Befehl gelesen und einige Zeit nach dem Import des Moduls in einem Hintergrundthread geschrieben.</span><span class="sxs-lookup"><span data-stu-id="717f8-137">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="717f8-138">Um den Standardspeicherort des Caches zu ändern, legen Sie die Umgebungsvariable `$env:PSModuleAnalysisCachePath` vor dem Starten von PowerShell fest.</span><span class="sxs-lookup"><span data-stu-id="717f8-138">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="717f8-139">Änderungen an dieser Umgebungsvariablen betreffen nur untergeordnete Prozesse.</span><span class="sxs-lookup"><span data-stu-id="717f8-139">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="717f8-140">Der Wert muss einen vollständigen Pfad (samt Dateiname) definieren, in dem PowerShell die Berechtigung zum Erstellen und Schreiben von Dateien hat.</span><span class="sxs-lookup"><span data-stu-id="717f8-140">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="717f8-141">Zum Deaktivieren des Dateicaches kann dieser Wert auf einen ungültigen Speicherort festgelegt werden. Beispiel:</span><span class="sxs-lookup"><span data-stu-id="717f8-141">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="717f8-142">Hiermit wird der Pfad auf ein ungültiges Gerät festgelegt.</span><span class="sxs-lookup"><span data-stu-id="717f8-142">This sets the path to an invalid device.</span></span> <span data-ttu-id="717f8-143">Wenn PowerShell nicht in den Pfad schreiben kann, wird keine Fehlermeldung zurückgegeben. Mithilfe eines Ablaufverfolgungstools können Sie jedoch einen Fehlerbericht anzeigen:</span><span class="sxs-lookup"><span data-stu-id="717f8-143">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="717f8-144">Bei der Ausgabe aus dem Cache sucht PowerShell nach Modulen, die nicht mehr vorhanden sind, um einen unnötig großen Cache zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="717f8-144">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span>
<span data-ttu-id="717f8-145">Mitunter sind diese Überprüfungen nicht wünschenswert, weshalb Sie sie deaktivieren können, indem Sie Folgendes festlegen:</span><span class="sxs-lookup"><span data-stu-id="717f8-145">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="717f8-146">Das Festlegen dieser Umgebungsvariablen wird im aktuellen Prozess sofort wirksam.</span><span class="sxs-lookup"><span data-stu-id="717f8-146">Setting this environment variable will take effect immediately in the current process.</span></span>

##<a name="specifying-module-version"></a><span data-ttu-id="717f8-147">Angeben der Modulversion</span><span class="sxs-lookup"><span data-stu-id="717f8-147">Specifying module version</span></span>

<span data-ttu-id="717f8-148">In WMF 5.1 verhält sich `using module` genauso wie andere modulbezogene Konstruktionen in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="717f8-148">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span> <span data-ttu-id="717f8-149">Zuvor gab es keine Möglichkeit, eine bestimmte Modulversion anzugeben. Wenn mehrere Versionen vorhanden waren, führte dies zu einem Fehler.</span><span class="sxs-lookup"><span data-stu-id="717f8-149">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>


<span data-ttu-id="717f8-150">In WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="717f8-150">In WMF 5.1:</span></span>

* <span data-ttu-id="717f8-151">Sie können den [Konstruktor „ModuleSpecification“ (Hashtabelle)](https://msdn.microsoft.com/library/jj136290) verwenden.</span><span class="sxs-lookup"><span data-stu-id="717f8-151">You can use [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290).</span></span> <span data-ttu-id="717f8-152">Diese Hashtabelle hat das gleiche Format wie `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="717f8-152">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

<span data-ttu-id="717f8-153">**Beispiel:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="717f8-153">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

* <span data-ttu-id="717f8-154">Wenn mehrere Versionen des Moduls vorhanden sind, verwendet PowerShell **dieselbe Auflösungslogik** wie `Import-Module` und gibt keinen Fehler zurück, was dem Verhalten von `Import-Module` und `Import-DscResource` entspricht.</span><span class="sxs-lookup"><span data-stu-id="717f8-154">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>


##<a name="improvements-to-pester"></a><span data-ttu-id="717f8-155">Verbesserungen an Pester</span><span class="sxs-lookup"><span data-stu-id="717f8-155">Improvements to Pester</span></span>
<span data-ttu-id="717f8-156">In WMF 5.1 wurde die in PowerShell mitgelieferte Pester-Version von 3.3.5 auf 3.4.0 aktualisiert und um eine „commit“-Funktion ergänzt, die die Funktionsweise von Pester auf Nano Server verbessert (https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e).</span><span class="sxs-lookup"><span data-stu-id="717f8-156">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0, with the addition of commit https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, which enables better behavior for Pester on Nano Server.</span></span> 

<span data-ttu-id="717f8-157">Die Änderungen, die in Version 3.4.0 hinsichtlich der Version 3.3.5 gemacht wurden, können Sie in der Datei „ChangeLog.md“ unter „https://github.com/pester/Pester/blob/master/CHANGELOG.md“ einsehen.</span><span class="sxs-lookup"><span data-stu-id="717f8-157">You can review the changes in versions 3.3.5 to 3.4.0 by inspecting the ChangeLog.md file at: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span></span>

