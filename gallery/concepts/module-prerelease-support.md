---
ms.date: 09/26/2017
contributor: keithb
keywords: gallery,powershell,cmdlet,psget
title: Vorabmodulversionen
ms.openlocfilehash: eced067dd21082de0db653daf3b838217154f1dd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2019
ms.locfileid: "58056242"
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="5f0f3-103">Vorabmodulversionen</span><span class="sxs-lookup"><span data-stu-id="5f0f3-103">Prerelease Module Versions</span></span>

<span data-ttu-id="5f0f3-104">Ab Version 1.6.0 unterstützen PowerShellGet und der PowerShell-Katalog das Kennzeichnen von Versionen ab 1.0.0 als Vorabversion.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="5f0f3-105">Vor der Einführung dieses Features waren Vorabversionspakete auf Versionen beschränkt, die mit 0 beginnen.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="5f0f3-106">Ziel dieser Features ist es, eine größere Unterstützung für die Versionsverwaltungsspezifikation [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) bereitzustellen, ohne die Abwärtskompatibilität mit PowerShell Version 3 und höher oder vorhandenen PowerShellGet-Versionen einzuschränken.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="5f0f3-107">Der Schwerpunkt dieses Themas liegt auf modulspezifischen Features.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="5f0f3-108">Eine Erläuterung der entsprechenden Features für Skripts finden Sie im Thema [Vorabskriptversionen](script-prerelease-support.md).</span><span class="sxs-lookup"><span data-stu-id="5f0f3-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](script-prerelease-support.md) topic.</span></span> <span data-ttu-id="5f0f3-109">Mit diesen Features können Herausgeber ein Modul oder Skript als Version 2.5.0-alpha identifizieren und später eine für die Produktion freigegebene 2.5.0-Version veröffentlichen, die die Vorabversion ablöst.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="5f0f3-110">Allgemein umfassen die Vorabversions-Modulfeatures u.a. Folgendes:</span><span class="sxs-lookup"><span data-stu-id="5f0f3-110">At a high level, the prerelease module features include:</span></span>

- <span data-ttu-id="5f0f3-111">Durch Hinzufügen einer Vorabversionszeichenfolge zum PSData-Abschnitt des Modulmanifests wird das Modul als Vorabversion identifiziert.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="5f0f3-112">Wenn das Modul im PowerShell-Katalog veröffentlicht wird, werden diese Daten aus dem Manifest extrahiert und zum Identifizieren von Vorabversionspaketen verwendet.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="5f0f3-113">Zum Abrufen von Vorabversionspaketen muss den PowerShellGet-Befehlen `Find-Module`, `Install-Module`, `Update-Module` und `Save-Module` das `-AllowPrerelease`-Flag hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-113">Acquiring prerelease packages requires adding `-AllowPrerelease` flag to the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span> <span data-ttu-id="5f0f3-114">Wenn das Flag nicht angegeben ist, werden keine Vorabversionspakete angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="5f0f3-115">Die durch `Find-Module` und `Get-InstalledModule` sowie im PowerShell-Katalog angezeigten Modulversionen werden als einzelne Zeichenfolge mit angefügter Vorabversionszeichenfolge angezeigt (z.B. „2.5.0-alpha“).</span><span class="sxs-lookup"><span data-stu-id="5f0f3-115">Module versions displayed by `Find-Module`, `Get-InstalledModule`, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="5f0f3-116">Einzelheiten zu den Features finden Sie weiter unten.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-116">Details for the features are included below.</span></span>

<span data-ttu-id="5f0f3-117">Diese Änderungen wirken sich nicht auf die in PowerShell integrierte Modulversionsunterstützung aus und sind mit PowerShell 3.0, 4.0 und 5 kompatibel.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span>

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="5f0f3-118">Identifizieren einer Modulversion als Vorabversion</span><span class="sxs-lookup"><span data-stu-id="5f0f3-118">Identifying a module version as a prerelease</span></span>

<span data-ttu-id="5f0f3-119">Um PowerShellGet-Unterstützung für Vorabversionen bereitzustellen, müssen die folgenden zwei Felder innerhalb des Modulmanifests verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="5f0f3-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

- <span data-ttu-id="5f0f3-120">Der im Modulmanifest enthaltene ModuleVersion-Schlüssel muss bei Verwendung einer Vorabversion eine Versionsnummer bestehend aus 3 Ziffern enthalten und mit der vorhandenen PowerShell-Versionsverwaltung übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="5f0f3-121">Das Versionsformat würde „A.B.C“ lauten, wobei „A“, „B“ und „C“ für ganze Zahlen stehen.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span>
- <span data-ttu-id="5f0f3-122">Die Vorabversionszeichenfolge wird im Modulmanifest im PSData-Abschnitt von „PrivateData“ angegeben.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span>

<span data-ttu-id="5f0f3-123">Die Anforderungen für die Vorabversionszeichenfolge werden nachfolgend ausführlich erläutert.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-123">Detailed requirements on the Prerelease string are below.</span></span>

<span data-ttu-id="5f0f3-124">Ein Beispielabschnitt eines Modulmanifests, das ein Modul als Vorabversion definiert, sieht etwa wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="5f0f3-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>

```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

<span data-ttu-id="5f0f3-125">Die Anforderungen für die Vorabversionszeichenfolge werden nachfolgend im Einzelnen erläutert:</span><span class="sxs-lookup"><span data-stu-id="5f0f3-125">The detailed requirements for Prerelease string are:</span></span>

- <span data-ttu-id="5f0f3-126">Die Vorabversionszeichenfolge darf nur angegeben werden, wenn der ModuleVersion-Schlüssel 3 Ziffern enthält, nämlich „Hauptversion.Nebenversion.Build“.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="5f0f3-127">Dies entspricht SemVer v1.0.0.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-127">This aligns with SemVer v1.0.0.</span></span>
- <span data-ttu-id="5f0f3-128">Ein Bindestrich fungiert als Trennzeichen zwischen der Buildnummer und der Vorabversionszeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="5f0f3-129">Ein Bindestrich darf nur als erstes Zeichen in die Vorabversionszeichenfolge eingefügt werden.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
- <span data-ttu-id="5f0f3-130">Die Vorabversionszeichenfolge darf nur alphanumerische ASCII-Zeichen [0-9, A-Z, a-z] enthalten.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="5f0f3-131">Es wird empfohlen, dass die Vorabversionszeichenfolge mit einem alphanumerischen Zeichen beginnt. So wird beim Prüfen einer Liste von Paketen einfacher erkannt, dass es sich um eine Vorabversion handelt.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of packages.</span></span>
- <span data-ttu-id="5f0f3-132">Zurzeit werden nur SemVer v1.0.0-Vorabversionszeichenfolgen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="5f0f3-133">Diese Zeichenfolge darf **keine** Punkte oder Pluszeichen [.+] enthalten, die in SemVer 2.0 zulässig sind.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-133">Prerelease string **must not** contain either period or + [.+], which are allowed in SemVer 2.0.</span></span>
- <span data-ttu-id="5f0f3-134">Zu den unterstützten Vorabversionszeichenfolgen zählen beispielsweise „-alpha“, „-alpha1“, „-BETA“ und „-update20171020“.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="5f0f3-135">Auswirkung der Vorabversionsverwaltung auf die Sortierreihenfolge und Installationsordner</span><span class="sxs-lookup"><span data-stu-id="5f0f3-135">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="5f0f3-136">Die Sortierreihenfolge ändert sich bei der Verwendung einer Vorabversion, was für die Veröffentlichung von Inhalten im PowerShell-Katalog und der Installation von Modulen mit PowerShellGet-Befehlen relevant ist.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="5f0f3-137">Wenn die Vorabversionszeichenfolge für zwei Module angegeben ist, basiert die Sortierreihenfolge auf dem Zeichenfolgenteil nach dem Bindestrich.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="5f0f3-138">Deshalb ist Version 2.5.0-alpha niedriger als 2.5.0-beta, die wiederum niedriger als 2.5.0-gamma ist.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="5f0f3-139">Wenn zwei Module den gleichen ModuleVersion-Schlüssel und nur eine Vorabversionszeichenfolge aufweisen, wird das Modul ohne die Vorabversionszeichenfolge als für die Produktion freigegebene Version behandelt und gegenüber der Vorabversion (die die Vorabversionszeichenfolge enthält) als höhere Version sortiert.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="5f0f3-140">Beispiel: Beim Vergleich der Versionen 2.5.0 und 2.5.0-beta wird die Version 2.5.0 als die höhere der beiden Versionen betrachtet.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="5f0f3-141">Beim Veröffentlichen von Inhalten im PowerShell-Katalog muss die Version des Moduls, das veröffentlicht wird, standardmäßig eine höhere Version aufweisen als zuvor veröffentlichte Versionen, die nicht im PowerShell-Katalog vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="5f0f3-142">Suchen und Abrufen von Vorabversionspaketen mit PowerShellGet-Befehlen</span><span class="sxs-lookup"><span data-stu-id="5f0f3-142">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="5f0f3-143">Wenn Sie Vorabversionspakete mit den PowerShellGet-Befehlen „Find-Module“, „Install-Module“, „Update-Module“ und „Save-Module“ verwenden, müssen Sie das „-AllowPrerelease“-Flag hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-143">Dealing with prerelease packages using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="5f0f3-144">Bei der Angabe von „-AllowPrerelease“ werden vorhandene Vorabversionspakete eingeschlossen.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-144">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="5f0f3-145">Wenn das „-AllowPrerelease“-Flag nicht angegeben ist, werden keine Vorabversionspakete angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-145">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="5f0f3-146">Die einzigen Ausnahmen hierfür in Bezug auf PowerShellGet-Modulbefehle sind „Get-InstalledModule“ und in einigen Fällen „Uninstall-Module“.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span>

- <span data-ttu-id="5f0f3-147">Mit „Get-InstalledModule“ werden immer automatisch die Vorabversionsinformationen in der Versionszeichenfolge für Module angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span>
- <span data-ttu-id="5f0f3-148">Mit „Uninstall-Module“ wird standardmäßig die neueste Version eines Moduls deinstalliert, wenn __keine Version__ angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="5f0f3-149">Dieses Verhalten wurde nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-149">That behavior has not changed.</span></span> <span data-ttu-id="5f0f3-150">Wenn jedoch mit „-RequiredVersion“ eine Vorabversion angegeben wird, ist „-AllowPrerelease“ erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="5f0f3-151">Beispiele</span><span class="sxs-lookup"><span data-stu-id="5f0f3-151">Examples</span></span>

<span data-ttu-id="5f0f3-152">Nehmen Sie an, der PowerShell-Katalog weist die TestPackage-Modulversionen 1.8.0 und 1.9.0-alpha auf.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-152">Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.</span></span> <span data-ttu-id="5f0f3-153">Wenn `-AllowPrerelease` nicht angegeben ist, wird nur Version 1.8.0 zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-153">If `-AllowPrerelease` is not specified, only version 1.8.0 will be returned.</span></span>

```powershell
find-module TestPackage
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.8.0          TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

```powershell
find-module TestPackage -AllowPrerelease
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.9.0-alpha    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="5f0f3-154">Um eine Vorabversion zu installieren, müssen Sie immer „-AllowPrerelease“ angeben.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-154">To install a prerelease, always specify -AllowPrerelease.</span></span> <span data-ttu-id="5f0f3-155">Es reicht nicht aus, eine Vorabversionszeichenfolge anzugeben.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-155">Specifying a prerelease version string is not sufficient.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha
```

```output
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage
```

<span data-ttu-id="5f0f3-156">Bei dem vorherigen Befehl ist ein Fehler aufgetreten, da „-AllowPrerelease“ nicht angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-156">The previous command failed because -AllowPrerelease was not specified.</span></span> <span data-ttu-id="5f0f3-157">Durch Hinzufügen von `-AllowPrerelease` kann dies behoben werden.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-157">Adding `-AllowPrerelease` will result in success.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="5f0f3-158">Die parallele Installation von Modulversionen, die sich lediglich durch die angegebene Vorabversion unterscheiden, wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-158">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="5f0f3-159">Bei der Installation eines Moduls mit PowerShellGet werden verschiedene Versionen desselben Moduls parallel installiert, indem mit dem ModuleVersion-Schlüssel ein Ordnername erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-159">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="5f0f3-160">Für den Ordnernamen wird der ModuleVersion-Schlüssel ohne die Vorabversionszeichenfolge verwendet.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-160">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="5f0f3-161">Wenn ein Benutzer MyModule Version 2.5.0-alpha installiert, wird das Modul im Ordner `MyModule\2.5.0` installiert.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-161">If a user installs MyModule version 2.5.0-alpha, it will be installed to the `MyModule\2.5.0` folder.</span></span> <span data-ttu-id="5f0f3-162">Wenn der Benutzer dann 2.5.0-beta installiert, **überschreibt** die Version 2.5.0-beta den Inhalt des Ordners `MyModule\2.5.0`.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-162">If the user then installs 2.5.0-beta, the 2.5.0-beta version will **overwrite** the contents of the folder `MyModule\2.5.0`.</span></span> <span data-ttu-id="5f0f3-163">Ein Vorteil bei dieser Vorgehensweise besteht darin, dass nach der Installation der für die Produktion freigegebenen Version die Vorabversion nicht deinstalliert werden muss.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-163">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="5f0f3-164">Im folgenden Beispiel wird gezeigt, wie dies aussieht:</span><span class="sxs-lookup"><span data-stu-id="5f0f3-164">The example below shows what to expect:</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-alpha     TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name            Repository  Description
-------        ----            ----------  -----------
1.9.0-beta     TestPackage     PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

```

<span data-ttu-id="5f0f3-165">Mit „Uninstall-Module“ wird die neueste Version eines Moduls entfernt, wenn „-RequiredVersion“ nicht angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-165">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="5f0f3-166">Wenn „-RequiredVersion“ angegeben ist und es sich um eine Vorabversion handelt, muss „-AllowPrerelease“ zum Befehl hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="5f0f3-166">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
2.0.0-alpha1    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta

Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-Module

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
2.0.0-alpha1    TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...
```

## <a name="more-details"></a><span data-ttu-id="5f0f3-167">Weitere Details</span><span class="sxs-lookup"><span data-stu-id="5f0f3-167">More details</span></span>

- [<span data-ttu-id="5f0f3-168">Vorabskriptversionen</span><span class="sxs-lookup"><span data-stu-id="5f0f3-168">Prerelease Script Versions</span></span>](script-prerelease-support.md)
- [<span data-ttu-id="5f0f3-169">Find-Module</span><span class="sxs-lookup"><span data-stu-id="5f0f3-169">Find-Module</span></span>](/powershell/module/powershellget/find-module)
- [<span data-ttu-id="5f0f3-170">Install-Module</span><span class="sxs-lookup"><span data-stu-id="5f0f3-170">Install-Module</span></span>](/powershell/module/powershellget/install-module)
- [<span data-ttu-id="5f0f3-171">Save-Module</span><span class="sxs-lookup"><span data-stu-id="5f0f3-171">Save-Module</span></span>](/powershell/module/powershellget/save-module)
- [<span data-ttu-id="5f0f3-172">Update-Module</span><span class="sxs-lookup"><span data-stu-id="5f0f3-172">Update-Module</span></span>](/powershell/module/powershellget/Update-Module)
- [<span data-ttu-id="5f0f3-173">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="5f0f3-173">Get-InstalledModule</span></span>](/powershell/module/powershellget/get-installedmodule)
- [<span data-ttu-id="5f0f3-174">UnInstall-Module</span><span class="sxs-lookup"><span data-stu-id="5f0f3-174">UnInstall-Module</span></span>](/powershell/module/powershellget/uninstall-module)
