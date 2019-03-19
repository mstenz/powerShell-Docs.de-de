---
ms.date: 10/17/2017
contributor: keithb
keywords: gallery,powershell,cmdlet,psget
title: Vorabskriptversionen
ms.openlocfilehash: c0198c2f575d2c004949ccebab49d93ce54716be
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2019
ms.locfileid: "58055885"
---
# <a name="prerelease-versions-of-scripts"></a><span data-ttu-id="302f8-103">Vorabskriptversionen</span><span class="sxs-lookup"><span data-stu-id="302f8-103">Prerelease versions of scripts</span></span>

<span data-ttu-id="302f8-104">Ab Version 1.6.0 unterstützen PowerShellGet und der PowerShell-Katalog das Kennzeichnen von Versionen ab 1.0.0 als Vorabversion.</span><span class="sxs-lookup"><span data-stu-id="302f8-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="302f8-105">Vor der Einführung dieses Features waren Vorabversionspakete auf Versionen beschränkt, die mit 0 beginnen.</span><span class="sxs-lookup"><span data-stu-id="302f8-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="302f8-106">Ziel dieser Features ist es, eine größere Unterstützung für die Versionsverwaltungsspezifikation [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) bereitzustellen, ohne die Abwärtskompatibilität mit PowerShell Version 3 und höher oder vorhandenen PowerShellGet-Versionen einzuschränken.</span><span class="sxs-lookup"><span data-stu-id="302f8-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="302f8-107">Der Schwerpunkt dieses Themas liegt auf skriptspezifischen Features.</span><span class="sxs-lookup"><span data-stu-id="302f8-107">This topic focuses on the script-specific features.</span></span> <span data-ttu-id="302f8-108">Eine Erläuterung der entsprechenden Features für Module finden Sie im Thema [Vorabmodulversionen](module-prerelease-support.md).</span><span class="sxs-lookup"><span data-stu-id="302f8-108">The equivalent features for modules are in the [Prerelease Module Versions](module-prerelease-support.md) topic.</span></span> <span data-ttu-id="302f8-109">Mit diesen Features können Herausgeber ein Skript als Version 2.5.0-alpha identifizieren und später eine für die Produktion freigegebene 2.5.0-Version veröffentlichen, die die Vorabversion ablöst.</span><span class="sxs-lookup"><span data-stu-id="302f8-109">Using these features, publishers can identify a script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="302f8-110">Allgemein umfassen die Vorabversions-Skriptfeatures u.a. Folgendes:</span><span class="sxs-lookup"><span data-stu-id="302f8-110">At a high level, the prerelease script features include:</span></span>

- <span data-ttu-id="302f8-111">Hinzufügen eines PrereleaseString-Suffixes zur Versionszeichenfolge im Skriptmanifest.</span><span class="sxs-lookup"><span data-stu-id="302f8-111">Adding a PrereleaseString suffix to the version string in the script manifest.</span></span> <span data-ttu-id="302f8-112">Wenn die Skripts im PowerShell-Katalog veröffentlicht wurden, werden diese Daten aus dem Manifest extrahiert und zum Identifizieren von Vorabversionspaketen verwendet.</span><span class="sxs-lookup"><span data-stu-id="302f8-112">When the scripts is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="302f8-113">Zum Abrufen von Vorabversionspaketen müssen Sie den PowerShellGet-Befehlen „Find-Script“, „Install-Script“, „Update-Script“ und „Save-Script“ den „-AllowPrerelease“-Flag hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="302f8-113">Acquiring prerelease packages requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Script, Install-Script, Update-Script, and Save-Script.</span></span> <span data-ttu-id="302f8-114">Wenn das Flag nicht angegeben ist, werden keine Vorabversionspakete angezeigt.</span><span class="sxs-lookup"><span data-stu-id="302f8-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="302f8-115">Die durch „Find-Script“ und „Get-InstalledScript“ sowie im PowerShell-Katalog angezeigten Skriptversionen werden mit dem PrereleaseString-Parameter angezeigt (z.B. „2.5.0-alpha“).</span><span class="sxs-lookup"><span data-stu-id="302f8-115">Script versions displayed by Find-Script, Get-InstalledScript, and in the PowerShell Gallery will be displayed with the PrereleaseString, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="302f8-116">Einzelheiten zu den Features finden Sie weiter unten.</span><span class="sxs-lookup"><span data-stu-id="302f8-116">Details for the features are included below.</span></span>

## <a name="identifying-a-script-version-as-a-prerelease"></a><span data-ttu-id="302f8-117">Identifizieren einer Skriptversion als Vorabversion</span><span class="sxs-lookup"><span data-stu-id="302f8-117">Identifying a script version as a prerelease</span></span>

<span data-ttu-id="302f8-118">Es ist einfacher, PowerShellGet-Unterstützung für Vorabversionen bei Skripts bereitzustellen als bei Modulen.</span><span class="sxs-lookup"><span data-stu-id="302f8-118">PowerShellGet support for prerelease versions is easier for scripts than modules.</span></span> <span data-ttu-id="302f8-119">Die Skriptversionsverwaltung wird nur von PowerShellGet unterstützt, sodass durch das Hinzufügen der Vorabversionszeichenfolge keine Kompatibilitätsprobleme verursacht werden.</span><span class="sxs-lookup"><span data-stu-id="302f8-119">Script versioning is only supported by PowerShellGet, so there are no compatibility issues caused by adding the prerelease string.</span></span> <span data-ttu-id="302f8-120">Um ein Skript im PowerShell-Katalog als Vorabversion zu identifizieren, fügen Sie ein Vorabversionssuffix zu einer ordnungsgemäß formatierten Versionszeichenfolge in den Skriptmetadaten hinzu.</span><span class="sxs-lookup"><span data-stu-id="302f8-120">To identify a script in the PowerShell Gallery as a prerelease, add a prerelease suffix to a properly-formatted version string in the script metadata.</span></span>

<span data-ttu-id="302f8-121">Ein Beispielabschnitt eines Skriptmanifests mit einer Vorabversion sieht etwa wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="302f8-121">An example section of a script manifest with a prerelease version would look like the following:</span></span>

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

<span data-ttu-id="302f8-122">Für die Verwendung eines Vorabversionssuffixes muss die Versionszeichenfolge die folgenden Voraussetzungen erfüllen:</span><span class="sxs-lookup"><span data-stu-id="302f8-122">To use a prerelease suffix, the version string must meet the following requirements:</span></span>

- <span data-ttu-id="302f8-123">Ein Vorabversionssuffix darf nur angegeben werden, wenn die Versionsnummer 3 Ziffern enthält, nämlich „Hauptversion.Nebenversion.Build“.</span><span class="sxs-lookup"><span data-stu-id="302f8-123">A prerelease suffix may only be specified when the Version is 3 segments for Major.Minor.Build.</span></span>
  <span data-ttu-id="302f8-124">Dies entspricht SemVer v1.0.0.</span><span class="sxs-lookup"><span data-stu-id="302f8-124">This aligns with SemVer v1.0.0</span></span>
- <span data-ttu-id="302f8-125">Das Vorabversionssuffix ist eine Zeichenfolge, die mit einem Bindestrich beginnt und nur alphanumerische ASCII-Zeichen [0-9, A-Z, a-z] enthalten darf.</span><span class="sxs-lookup"><span data-stu-id="302f8-125">The prerelease suffix is a string which begins with a hyphen, and may contain ASCII alphanumerics [0-9A-Za-z-]</span></span>
- <span data-ttu-id="302f8-126">Da zurzeit nur SemVer v1.0.0-Vorabversionszeichenfolgen unterstützt werden, darf das Vorabversionssuffix **keine** Punkte oder Pluszeichen [.+] enthalten, die in SemVer 2.0 zulässig sind.</span><span class="sxs-lookup"><span data-stu-id="302f8-126">Only SemVer v1.0.0 prerelease strings are supported at this time, so the prerelease suffix **must not** contain either period or + [.+], which are allowed in SemVer 2.0</span></span>
- <span data-ttu-id="302f8-127">Zu den unterstützten PrereleaseString-Zeichenfolgen zählen beispielsweise „-alpha“, „-alpha1“, „-BETA“ und „-update20171020“.</span><span class="sxs-lookup"><span data-stu-id="302f8-127">Examples of supported PrereleaseString strings are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="302f8-128">Auswirkung der Vorabversionsverwaltung auf die Sortierreihenfolge und Installationsordner</span><span class="sxs-lookup"><span data-stu-id="302f8-128">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="302f8-129">Die Sortierreihenfolge ändert sich bei der Verwendung einer Vorabversion, was für die Veröffentlichung von Inhalten im PowerShell-Katalog und der Installation von Skripts mit PowerShellGet-Befehlen relevant ist.</span><span class="sxs-lookup"><span data-stu-id="302f8-129">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing scripts using PowerShellGet commands.</span></span> <span data-ttu-id="302f8-130">Wenn zwei Skriptversionen mit der Versionsnummer vorhanden sind, erfolgt die Sortierreihenfolge basierend auf dem Zeichenfolgenteil nach dem Bindestrich.</span><span class="sxs-lookup"><span data-stu-id="302f8-130">If two scripts versions with the version number exist, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="302f8-131">Deshalb ist Version 2.5.0-alpha niedriger als 2.5.0-beta, die wiederum niedriger als 2.5.0-gamma ist.</span><span class="sxs-lookup"><span data-stu-id="302f8-131">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="302f8-132">Wenn zwei Skripts die gleiche Versionsnummer und nur einen PrereleaseString-Parameter aufweisen, wird das Skript **ohne** das Vorabversionssuffix als für die Produktion freigegebene Version behandelt und gegenüber der Vorabversion als höhere Version sortiert.</span><span class="sxs-lookup"><span data-stu-id="302f8-132">If two scripts have the same version number, and only one has a PrereleaseString, the script **without** the prerelease suffix is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version.</span></span> <span data-ttu-id="302f8-133">Beispiel: Beim Vergleich der Versionen 2.5.0 und 2.5.0-beta wird die Version 2.5.0 als die höhere der beiden Versionen betrachtet.</span><span class="sxs-lookup"><span data-stu-id="302f8-133">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="302f8-134">Beim Veröffentlichen von Inhalten im PowerShell-Katalog muss die Version des Skripts, das veröffentlicht wird, standardmäßig eine höhere Version aufweisen als zuvor veröffentlichte Versionen, die nicht im PowerShell-Katalog vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="302f8-134">When publishing to the PowerShell Gallery, by default the version of the script being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span> <span data-ttu-id="302f8-135">Ein Herausgeber kann Version 2.5.0-alpha auf 2.5.0-beta oder 2.5.0 (ohne Vorabversionssuffix) aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="302f8-135">A publisher may update version 2.5.0-alpha with 2.5.0-beta, or with 2.5.0 (with no prerelease suffix).</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="302f8-136">Suchen und Abrufen von Vorabversionspaketen mit PowerShellGet-Befehlen</span><span class="sxs-lookup"><span data-stu-id="302f8-136">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="302f8-137">Wenn Sie Vorabversionspakete mit den PowerShellGet-Befehlen „Find-Script“, „Install-Script“, „Update-Script“ und „Save-Script“ verwenden, müssen Sie das „-AllowPrerelease“-Flag hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="302f8-137">Dealing with prerelease packages using PowerShellGet Find-Script, Install-Script, Update-Script, and Save-Script commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="302f8-138">Bei der Angabe von „-AllowPrerelease“ werden vorhandene Vorabversionspakete eingeschlossen.</span><span class="sxs-lookup"><span data-stu-id="302f8-138">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="302f8-139">Wenn das „-AllowPrerelease“-Flag nicht angegeben ist, werden keine Vorabversionspakete angezeigt.</span><span class="sxs-lookup"><span data-stu-id="302f8-139">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="302f8-140">Die einzigen Ausnahmen hierfür in den PowerShellGet-Skriptbefehlen sind „Get-InstalledScript“ und in einigen Fällen „Uninstall-Script“.</span><span class="sxs-lookup"><span data-stu-id="302f8-140">The only exceptions to this in the PowerShellGet script commands are Get-InstalledScript, and some cases with Uninstall-Script.</span></span>

- <span data-ttu-id="302f8-141">Mit „Get-InstalledScript“ werden immer automatisch die Vorabversionsinformationen in der Versionszeichenfolge angezeigt, sofern diese vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="302f8-141">Get-InstalledScript always will automatically show the prerelease information in the version string if it is present.</span></span>
- <span data-ttu-id="302f8-142">Mit „Uninstall-Script“ wird standardmäßig die neueste Version eines Skripts deinstalliert, wenn **keine Version** angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="302f8-142">Uninstall-Script will by default uninstall the most recent version of a script, if **no version** is specified.</span></span> <span data-ttu-id="302f8-143">Dieses Verhalten wurde nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="302f8-143">That behavior has not changed.</span></span> <span data-ttu-id="302f8-144">Wenn jedoch mit `-RequiredVersion` eine Vorabversion angegeben wird, ist `-AllowPrerelease` erforderlich.</span><span class="sxs-lookup"><span data-stu-id="302f8-144">However, if a prerelease version is specified using `-RequiredVersion`, `-AllowPrerelease` will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="302f8-145">Beispiele</span><span class="sxs-lookup"><span data-stu-id="302f8-145">Examples</span></span>

```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> Find-Script TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Find-Script TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# To install a prerelease, you must specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha

PackageManagement\Find-Package : No match was found for the specified search criteria and script name 'TestPackage'.
Try Get-PSRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage)[Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# Note that Get-InstalledScript shows the prerelease version.
# If -RequiredVersion is not specified, all installed scripts will be displayed by Get-InstalledScript
```

<span data-ttu-id="302f8-146">Mit „Uninstall-Script“ wird die aktuelle Version eines Skripts entfernt, wenn „-RequiredVersion“ nicht angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="302f8-146">Uninstall-Script will remove the current version of a script when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="302f8-147">Wenn „-RequiredVersion“ angegeben ist und es sich um eine Vorabversion handelt, muss „-AllowPrerelease“ zum Befehl hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="302f8-147">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-script


C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
# Since script versions are not installed side-by-side, the above could be simply "Uninstall-Script TestPackage"

C:\windows\system32> Get-Installedscript TestPackage
PackageManagement\Get-Package : No match was found for the specified search criteria and script names 'testpackage'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.5.0.0\PSModule.psm1:4088 char:9
+         PackageManagement\Get-Package @PSBoundParameters | Microsoft. ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...lets.GetPackage:GetPackage) [Get-Package], Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.GetPackage
```

## <a name="more-details"></a><span data-ttu-id="302f8-148">Weitere Details</span><span class="sxs-lookup"><span data-stu-id="302f8-148">More details</span></span>

- [<span data-ttu-id="302f8-149">Vorabmodulversionen</span><span class="sxs-lookup"><span data-stu-id="302f8-149">Prerelease Module Versions</span></span>](module-prerelease-support.md)
- [<span data-ttu-id="302f8-150">Find-Script</span><span class="sxs-lookup"><span data-stu-id="302f8-150">Find-script</span></span>](/powershell/module/powershellget/find-script)
- [<span data-ttu-id="302f8-151">Install-Script</span><span class="sxs-lookup"><span data-stu-id="302f8-151">Install-script</span></span>](/powershell/module/powershellget/install-script)
- [<span data-ttu-id="302f8-152">Save-Script</span><span class="sxs-lookup"><span data-stu-id="302f8-152">Save-script</span></span>](/powershell/module/powershellget/save-script)
- [<span data-ttu-id="302f8-153">Update-Script</span><span class="sxs-lookup"><span data-stu-id="302f8-153">Update-script</span></span>](/powershell/module/powershellget/update-script)
- [<span data-ttu-id="302f8-154">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="302f8-154">Get-Installedscript</span></span>](/powershell/module/powershellget/get-installedscript)
- [<span data-ttu-id="302f8-155">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="302f8-155">UnInstall-script</span></span>](/powershell/module/powershellget/uninstall-script)
