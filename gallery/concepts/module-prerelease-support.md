---
ms.date: 09/26/2017
contributor: keithb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Vorabmodulversionen
ms.openlocfilehash: e663a42092556ef1c43a7cf236616bf420171af6
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="d8f19-103">Vorabmodulversionen</span><span class="sxs-lookup"><span data-stu-id="d8f19-103">Prerelease Module Versions</span></span>

<span data-ttu-id="d8f19-104">Ab Version 1.6.0 unterstützen PowerShellGet und der PowerShell-Katalog das Kennzeichnen von Versionen ab 1.0.0 als Vorabversion.</span><span class="sxs-lookup"><span data-stu-id="d8f19-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="d8f19-105">Vor der Einführung dieses Features waren Vorabversionselemente auf Versionen, die mit 0 beginnen, beschränkt.</span><span class="sxs-lookup"><span data-stu-id="d8f19-105">Prior to this feature, prerelease items were limited to having a version beginning with 0.</span></span> <span data-ttu-id="d8f19-106">Ziel dieser Features ist es, eine größere Unterstützung für die Versionsverwaltungsspezifikation [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) bereitzustellen, ohne die Abwärtskompatibilität mit PowerShell Version 3 und höher oder vorhandenen PowerShellGet-Versionen einzuschränken.</span><span class="sxs-lookup"><span data-stu-id="d8f19-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="d8f19-107">Der Schwerpunkt dieses Themas liegt auf modulspezifischen Features.</span><span class="sxs-lookup"><span data-stu-id="d8f19-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="d8f19-108">Eine Erläuterung der entsprechenden Features für Skripts finden Sie im Thema [Vorabskriptversionen](script-prerelease-support.md).</span><span class="sxs-lookup"><span data-stu-id="d8f19-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](script-prerelease-support.md) topic.</span></span> <span data-ttu-id="d8f19-109">Mit diesen Features können Herausgeber ein Modul oder Skript als Version 2.5.0-alpha identifizieren und später eine für die Produktion freigegebene 2.5.0-Version veröffentlichen, die die Vorabversion ablöst.</span><span class="sxs-lookup"><span data-stu-id="d8f19-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="d8f19-110">Allgemein umfassen die Vorabversions-Modulfeatures u.a. Folgendes:</span><span class="sxs-lookup"><span data-stu-id="d8f19-110">At a high level, the prerelease module features include:</span></span>

- <span data-ttu-id="d8f19-111">Durch Hinzufügen einer Vorabversionszeichenfolge zum PSData-Abschnitt des Modulmanifests wird das Modul als Vorabversion identifiziert.</span><span class="sxs-lookup"><span data-stu-id="d8f19-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="d8f19-112">Wenn das Modul im PowerShell-Katalog veröffentlicht wurde, werden diese Daten aus dem Manifest extrahiert und zur Identifizierung von Vorabversionselementen verwendet.</span><span class="sxs-lookup"><span data-stu-id="d8f19-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease items.</span></span>
- <span data-ttu-id="d8f19-113">Zum Abrufen von Vorabversionselementen müssen Sie den -AllowPrerelease-Flag zu den PowerShellGet-Befehlen „Find-Module“, „Install-Module“, „Update-Module“ und „Save-Module“ hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="d8f19-113">Acquiring prerelease items requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Module, Install-Module, Update-Module, and Save-Module.</span></span> <span data-ttu-id="d8f19-114">Wenn das Flag nicht angegeben ist, werden keine Vorabversionselemente angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d8f19-114">If the flag is not specified, prerelease items will not be shown.</span></span>
- <span data-ttu-id="d8f19-115">Die durch „Find-Module“ und „Get-InstalledModule“ sowie im PowerShell-Katalog angezeigten Modulversionen werden als einzelne Zeichenfolge mit angefügter Vorabversionszeichenfolge angezeigt (z.B. „2.5.0-alpha“).</span><span class="sxs-lookup"><span data-stu-id="d8f19-115">Module versions displayed by Find-Module, Get-InstalledModule, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="d8f19-116">Einzelheiten zu den Features finden Sie weiter unten.</span><span class="sxs-lookup"><span data-stu-id="d8f19-116">Details for the features are included below.</span></span>

<span data-ttu-id="d8f19-117">Diese Änderungen wirken sich nicht auf die in PowerShell integrierte Modulversionsunterstützung aus und sind mit PowerShell 3.0, 4.0 und 5 kompatibel.</span><span class="sxs-lookup"><span data-stu-id="d8f19-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span>

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="d8f19-118">Identifizieren einer Modulversion als Vorabversion</span><span class="sxs-lookup"><span data-stu-id="d8f19-118">Identifying a module version as a prerelease</span></span>

<span data-ttu-id="d8f19-119">Um PowerShellGet-Unterstützung für Vorabversionen bereitzustellen, müssen die folgenden zwei Felder innerhalb des Modulmanifests verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="d8f19-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

- <span data-ttu-id="d8f19-120">Der im Modulmanifest enthaltene ModuleVersion-Schlüssel muss bei Verwendung einer Vorabversion eine Versionsnummer bestehend aus 3 Ziffern enthalten und mit der vorhandenen PowerShell-Versionsverwaltung übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="d8f19-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="d8f19-121">Das Versionsformat würde „A.B.C“ lauten, wobei „A“, „B“ und „C“ für ganze Zahlen stehen.</span><span class="sxs-lookup"><span data-stu-id="d8f19-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span>
- <span data-ttu-id="d8f19-122">Die Vorabversionszeichenfolge wird im Modulmanifest im PSData-Abschnitt von „PrivateData“ angegeben.</span><span class="sxs-lookup"><span data-stu-id="d8f19-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span>

<span data-ttu-id="d8f19-123">Die Anforderungen für die Vorabversionszeichenfolge werden nachfolgend ausführlich erläutert.</span><span class="sxs-lookup"><span data-stu-id="d8f19-123">Detailed requirements on the Prerelease string are below.</span></span>

<span data-ttu-id="d8f19-124">Ein Beispielabschnitt eines Modulmanifests, das ein Modul als Vorabversion definiert, sieht etwa wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="d8f19-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>

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

<span data-ttu-id="d8f19-125">Die Anforderungen für die Vorabversionszeichenfolge werden nachfolgend im Einzelnen erläutert:</span><span class="sxs-lookup"><span data-stu-id="d8f19-125">The detailed requirements for Prerelease string are:</span></span>

- <span data-ttu-id="d8f19-126">Die Vorabversionszeichenfolge darf nur angegeben werden, wenn der ModuleVersion-Schlüssel 3 Ziffern enthält, nämlich „Hauptversion.Nebenversion.Build“.</span><span class="sxs-lookup"><span data-stu-id="d8f19-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="d8f19-127">Dies entspricht SemVer v1.0.0.</span><span class="sxs-lookup"><span data-stu-id="d8f19-127">This aligns with SemVer v1.0.0.</span></span>
- <span data-ttu-id="d8f19-128">Ein Bindestrich fungiert als Trennzeichen zwischen der Buildnummer und der Vorabversionszeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="d8f19-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="d8f19-129">Ein Bindestrich darf nur als erstes Zeichen in die Vorabversionszeichenfolge eingefügt werden.</span><span class="sxs-lookup"><span data-stu-id="d8f19-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
- <span data-ttu-id="d8f19-130">Die Vorabversionszeichenfolge darf nur alphanumerische ASCII-Zeichen [0-9, A-Z, a-z] enthalten.</span><span class="sxs-lookup"><span data-stu-id="d8f19-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="d8f19-131">Die Vorabversionszeichenfolge sollte mit einem Buchstaben beginnen, da es beim Prüfen einer Liste von Elementen einfacher zu erkennen ist, dass es sich um eine Vorabversion handelt.</span><span class="sxs-lookup"><span data-stu-id="d8f19-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of items.</span></span>
- <span data-ttu-id="d8f19-132">Zurzeit werden nur SemVer v1.0.0-Vorabversionszeichenfolgen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d8f19-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="d8f19-133">Diese Zeichenfolge darf __keine__ Punkte oder Pluszeichen [.+] enthalten, die in SemVer 2.0 zulässig sind.</span><span class="sxs-lookup"><span data-stu-id="d8f19-133">Prerelease string __must not__ contain either period or + [.+], which are allowed in SemVer 2.0.</span></span>
- <span data-ttu-id="d8f19-134">Zu den unterstützten Vorabversionszeichenfolgen zählen beispielsweise „-alpha“, „-alpha1“, „-BETA“ und „-update20171020“.</span><span class="sxs-lookup"><span data-stu-id="d8f19-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

<span data-ttu-id="d8f19-135">__Auswirkung der Vorabversionsverwaltung auf die Sortierreihenfolge und Installationsordner__</span><span class="sxs-lookup"><span data-stu-id="d8f19-135">__Prerelease versioning impact on sort order and installation folders__</span></span>

<span data-ttu-id="d8f19-136">Die Sortierreihenfolge ändert sich bei der Verwendung einer Vorabversion, was für die Veröffentlichung von Inhalten im PowerShell-Katalog und der Installation von Modulen mit PowerShellGet-Befehlen relevant ist.</span><span class="sxs-lookup"><span data-stu-id="d8f19-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="d8f19-137">Wenn die Vorabversionszeichenfolge für zwei Module angegeben ist, basiert die Sortierreihenfolge auf dem Zeichenfolgenteil nach dem Bindestrich.</span><span class="sxs-lookup"><span data-stu-id="d8f19-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="d8f19-138">Deshalb ist Version 2.5.0-alpha niedriger als 2.5.0-beta, die wiederum niedriger als 2.5.0-gamma ist.</span><span class="sxs-lookup"><span data-stu-id="d8f19-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="d8f19-139">Wenn zwei Module den gleichen ModuleVersion-Schlüssel und nur eine Vorabversionszeichenfolge aufweisen, wird das Modul ohne die Vorabversionszeichenfolge als für die Produktion freigegebene Version behandelt und gegenüber der Vorabversion (die die Vorabversionszeichenfolge enthält) als höhere Version sortiert.</span><span class="sxs-lookup"><span data-stu-id="d8f19-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="d8f19-140">Beispiel: Beim Vergleich der Versionen 2.5.0 und 2.5.0-beta wird die Version 2.5.0 als die höhere der beiden Versionen betrachtet.</span><span class="sxs-lookup"><span data-stu-id="d8f19-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="d8f19-141">Beim Veröffentlichen von Inhalten im PowerShell-Katalog muss die Version des Moduls, das veröffentlicht wird, standardmäßig eine höhere Version aufweisen als zuvor veröffentlichte Versionen, die nicht im PowerShell-Katalog vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="d8f19-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a><span data-ttu-id="d8f19-142">Suchen und Abrufen von Vorabversionselementen mithilfe von PowerShellGet-Befehlen</span><span class="sxs-lookup"><span data-stu-id="d8f19-142">Finding and acquiring prerelease items using PowerShellGet commands</span></span>

<span data-ttu-id="d8f19-143">Bei der Verwendung von Vorabversionselementen mit den PowerShellGet-Befehlen „Find-Module“, „Install-Module“, „Update-Module“ und „Save-Module“ muss das -AllowPrerelease-Flag hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="d8f19-143">Dealing with prerelease items using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="d8f19-144">Bei der Angabe von -AllowPrerelease werden Vorabversionselemente eingeschlossen, sofern diese vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="d8f19-144">If -AllowPrerelease is specified, prerelease items will be included if they are present.</span></span> <span data-ttu-id="d8f19-145">Wenn das -AllowPrerelease-Flag nicht angegeben ist, werden keine Vorabversionselemente angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d8f19-145">If -AllowPrerelease flag is not specified, prerelease items will not be shown.</span></span>

<span data-ttu-id="d8f19-146">Die einzigen Ausnahmen hierfür in Bezug auf PowerShellGet-Modulbefehle sind „Get-InstalledModule“ und in einigen Fällen „Uninstall-Module“.</span><span class="sxs-lookup"><span data-stu-id="d8f19-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span>

- <span data-ttu-id="d8f19-147">Mit „Get-InstalledModule“ werden immer automatisch die Vorabversionsinformationen in der Versionszeichenfolge für Module angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d8f19-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span>
- <span data-ttu-id="d8f19-148">Mit „Uninstall-Module“ wird standardmäßig die neueste Version eines Moduls deinstalliert, wenn __keine Version__ angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="d8f19-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="d8f19-149">Dieses Verhalten wurde nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="d8f19-149">That behavior has not changed.</span></span> <span data-ttu-id="d8f19-150">Wenn jedoch mit „-RequiredVersion“ eine Vorabversion angegeben wird, ist „-AllowPrerelease“ erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d8f19-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="d8f19-151">Beispiele</span><span class="sxs-lookup"><span data-stu-id="d8f19-151">Examples</span></span>

```powershell
# Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> find-module TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

# To install a prerelease, always specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

<span data-ttu-id="d8f19-152">Die parallele Installation von Modulversionen, die sich lediglich durch die angegebene Vorabversion unterscheiden, wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d8f19-152">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="d8f19-153">Bei der Installation eines Moduls mit PowerShellGet werden verschiedene Versionen desselben Moduls parallel installiert, indem mit dem ModuleVersion-Schlüssel ein Ordnername erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="d8f19-153">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="d8f19-154">Für den Ordnernamen wird der ModuleVersion-Schlüssel ohne die Vorabversionszeichenfolge verwendet.</span><span class="sxs-lookup"><span data-stu-id="d8f19-154">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="d8f19-155">Wenn ein Benutzer MyModule Version 2.5.0-alpha installiert, wird das Modul im Ordner „MyModule\2.5.0“ installiert.</span><span class="sxs-lookup"><span data-stu-id="d8f19-155">If a user installs MyModule version 2.5.0-alpha, it will be installed to the MyModule\2.5.0 folder.</span></span> <span data-ttu-id="d8f19-156">Wenn der Benutzer dann 2.5.0-beta installiert, __überschreibt__ die Version 2.5.0-beta den Inhalt des Ordners „MyModule\2.5.0“.</span><span class="sxs-lookup"><span data-stu-id="d8f19-156">If the user then installs 2.5.0-beta, the 2.5.0-beta version will __over-write__ the contents of the folder MyModule\2.5.0.</span></span> <span data-ttu-id="d8f19-157">Ein Vorteil bei dieser Vorgehensweise besteht darin, dass nach der Installation der für die Produktion freigegebenen Version die Vorabversion nicht deinstalliert werden muss.</span><span class="sxs-lookup"><span data-stu-id="d8f19-157">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="d8f19-158">Im folgenden Beispiel wird gezeigt, wie dies aussieht:</span><span class="sxs-lookup"><span data-stu-id="d8f19-158">The example below shows what to expect:</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-beta     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

<span data-ttu-id="d8f19-159">Mit „Uninstall-Module“ wird die neueste Version eines Moduls entfernt, wenn „-RequiredVersion“ nicht angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="d8f19-159">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="d8f19-160">Wenn „-RequiredVersion“ angegeben ist und es sich um eine Vorabversion handelt, muss „-AllowPrerelease“ zum Befehl hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="d8f19-160">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-Module



C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...


```

## <a name="more-details"></a><span data-ttu-id="d8f19-161">Weitere Details</span><span class="sxs-lookup"><span data-stu-id="d8f19-161">More details</span></span>

- [<span data-ttu-id="d8f19-162">Vorabskriptversionen</span><span class="sxs-lookup"><span data-stu-id="d8f19-162">Prerelease Script Versions</span></span>](script-prerelease-support.md)
- [<span data-ttu-id="d8f19-163">Find-Module</span><span class="sxs-lookup"><span data-stu-id="d8f19-163">Find-Module</span></span>](/powershell/module/powershellget/find-module)
- [<span data-ttu-id="d8f19-164">Install-Module</span><span class="sxs-lookup"><span data-stu-id="d8f19-164">Install-Module</span></span>](/powershell/module/powershellget/install-module)
- [<span data-ttu-id="d8f19-165">Save-Module</span><span class="sxs-lookup"><span data-stu-id="d8f19-165">Save-Module</span></span>](/powershell/module/powershellget/save-module)
- [<span data-ttu-id="d8f19-166">Update-Module</span><span class="sxs-lookup"><span data-stu-id="d8f19-166">Update-Module</span></span>](/powershell/module/powershellget/Update-Module)
- [<span data-ttu-id="d8f19-167">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="d8f19-167">Get-InstalledModule</span></span>](/powershell/module/powershellget/get-installedmodule)
- [<span data-ttu-id="d8f19-168">UnInstall-Module</span><span class="sxs-lookup"><span data-stu-id="d8f19-168">UnInstall-Module</span></span>](/powershell/gallery/psget/module/psget_uninstall-module)