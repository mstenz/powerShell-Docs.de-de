---
ms.date: 10/17/2017
contributor: keithb
keywords: gallery,powershell,cmdlet,psget
title: Vorabskriptversionen
ms.openlocfilehash: c0198c2f575d2c004949ccebab49d93ce54716be
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328481"
---
# <a name="prerelease-versions-of-scripts"></a>Vorabskriptversionen

Ab Version 1.6.0 unterstützen PowerShellGet und der PowerShell-Katalog das Kennzeichnen von Versionen ab 1.0.0 als Vorabversion. Vor der Einführung dieses Features waren Vorabversionspakete auf Versionen beschränkt, die mit 0 beginnen. Ziel dieser Features ist es, eine größere Unterstützung für die Versionsverwaltungsspezifikation [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) bereitzustellen, ohne die Abwärtskompatibilität mit PowerShell Version 3 und höher oder vorhandenen PowerShellGet-Versionen einzuschränken. Der Schwerpunkt dieses Themas liegt auf skriptspezifischen Features. Eine Erläuterung der entsprechenden Features für Module finden Sie im Thema [Vorabmodulversionen](module-prerelease-support.md). Mit diesen Features können Herausgeber ein Skript als Version 2.5.0-alpha identifizieren und später eine für die Produktion freigegebene 2.5.0-Version veröffentlichen, die die Vorabversion ablöst.

Allgemein umfassen die Vorabversions-Skriptfeatures u.a. Folgendes:

- Hinzufügen eines PrereleaseString-Suffixes zur Versionszeichenfolge im Skriptmanifest. Wenn die Skripts im PowerShell-Katalog veröffentlicht wurden, werden diese Daten aus dem Manifest extrahiert und zum Identifizieren von Vorabversionspaketen verwendet.
- Zum Abrufen von Vorabversionspaketen müssen Sie den PowerShellGet-Befehlen „Find-Script“, „Install-Script“, „Update-Script“ und „Save-Script“ den „-AllowPrerelease“-Flag hinzufügen. Wenn das Flag nicht angegeben ist, werden keine Vorabversionspakete angezeigt.
- Die durch „Find-Script“ und „Get-InstalledScript“ sowie im PowerShell-Katalog angezeigten Skriptversionen werden mit dem PrereleaseString-Parameter angezeigt (z.B. „2.5.0-alpha“).

Einzelheiten zu den Features finden Sie weiter unten.

## <a name="identifying-a-script-version-as-a-prerelease"></a>Identifizieren einer Skriptversion als Vorabversion

Es ist einfacher, PowerShellGet-Unterstützung für Vorabversionen bei Skripts bereitzustellen als bei Modulen. Die Skriptversionsverwaltung wird nur von PowerShellGet unterstützt, sodass durch das Hinzufügen der Vorabversionszeichenfolge keine Kompatibilitätsprobleme verursacht werden. Um ein Skript im PowerShell-Katalog als Vorabversion zu identifizieren, fügen Sie ein Vorabversionssuffix zu einer ordnungsgemäß formatierten Versionszeichenfolge in den Skriptmetadaten hinzu.

Ein Beispielabschnitt eines Skriptmanifests mit einer Vorabversion sieht etwa wie folgt aus:

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

Für die Verwendung eines Vorabversionssuffixes muss die Versionszeichenfolge die folgenden Voraussetzungen erfüllen:

- Ein Vorabversionssuffix darf nur angegeben werden, wenn die Versionsnummer 3 Ziffern enthält, nämlich „Hauptversion.Nebenversion.Build“.
  Dies entspricht SemVer v1.0.0.
- Das Vorabversionssuffix ist eine Zeichenfolge, die mit einem Bindestrich beginnt und nur alphanumerische ASCII-Zeichen [0-9, A-Z, a-z] enthalten darf.
- Da zurzeit nur SemVer v1.0.0-Vorabversionszeichenfolgen unterstützt werden, darf das Vorabversionssuffix **keine** Punkte oder Pluszeichen [.+] enthalten, die in SemVer 2.0 zulässig sind.
- Zu den unterstützten PrereleaseString-Zeichenfolgen zählen beispielsweise „-alpha“, „-alpha1“, „-BETA“ und „-update20171020“.

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>Auswirkung der Vorabversionsverwaltung auf die Sortierreihenfolge und Installationsordner

Die Sortierreihenfolge ändert sich bei der Verwendung einer Vorabversion, was für die Veröffentlichung von Inhalten im PowerShell-Katalog und der Installation von Skripts mit PowerShellGet-Befehlen relevant ist. Wenn zwei Skriptversionen mit der Versionsnummer vorhanden sind, erfolgt die Sortierreihenfolge basierend auf dem Zeichenfolgenteil nach dem Bindestrich. Deshalb ist Version 2.5.0-alpha niedriger als 2.5.0-beta, die wiederum niedriger als 2.5.0-gamma ist. Wenn zwei Skripts die gleiche Versionsnummer und nur einen PrereleaseString-Parameter aufweisen, wird das Skript **ohne** das Vorabversionssuffix als für die Produktion freigegebene Version behandelt und gegenüber der Vorabversion als höhere Version sortiert. Beispiel: Beim Vergleich der Versionen 2.5.0 und 2.5.0-beta wird die Version 2.5.0 als die höhere der beiden Versionen betrachtet.

Beim Veröffentlichen von Inhalten im PowerShell-Katalog muss die Version des Skripts, das veröffentlicht wird, standardmäßig eine höhere Version aufweisen als zuvor veröffentlichte Versionen, die nicht im PowerShell-Katalog vorhanden sind. Ein Herausgeber kann Version 2.5.0-alpha auf 2.5.0-beta oder 2.5.0 (ohne Vorabversionssuffix) aktualisieren.

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>Suchen und Abrufen von Vorabversionspaketen mit PowerShellGet-Befehlen

Wenn Sie Vorabversionspakete mit den PowerShellGet-Befehlen „Find-Script“, „Install-Script“, „Update-Script“ und „Save-Script“ verwenden, müssen Sie das „-AllowPrerelease“-Flag hinzufügen. Bei der Angabe von „-AllowPrerelease“ werden vorhandene Vorabversionspakete eingeschlossen. Wenn das „-AllowPrerelease“-Flag nicht angegeben ist, werden keine Vorabversionspakete angezeigt.

Die einzigen Ausnahmen hierfür in den PowerShellGet-Skriptbefehlen sind „Get-InstalledScript“ und in einigen Fällen „Uninstall-Script“.

- Mit „Get-InstalledScript“ werden immer automatisch die Vorabversionsinformationen in der Versionszeichenfolge angezeigt, sofern diese vorhanden sind.
- Mit „Uninstall-Script“ wird standardmäßig die neueste Version eines Skripts deinstalliert, wenn **keine Version** angegeben ist. Dieses Verhalten wurde nicht geändert. Wenn jedoch mit `-RequiredVersion` eine Vorabversion angegeben wird, ist `-AllowPrerelease` erforderlich.

## <a name="examples"></a>Beispiele

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

Mit „Uninstall-Script“ wird die aktuelle Version eines Skripts entfernt, wenn „-RequiredVersion“ nicht angegeben ist.
Wenn „-RequiredVersion“ angegeben ist und es sich um eine Vorabversion handelt, muss „-AllowPrerelease“ zum Befehl hinzugefügt werden.

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

## <a name="more-details"></a>Weitere Details

- [Vorabmodulversionen](module-prerelease-support.md)
- [Find-Script](/powershell/module/powershellget/find-script)
- [Install-Script](/powershell/module/powershellget/install-script)
- [Save-Script](/powershell/module/powershellget/save-script)
- [Update-Script](/powershell/module/powershellget/update-script)
- [Get-InstalledScript](/powershell/module/powershellget/get-installedscript)
- [Uninstall-Script](/powershell/module/powershellget/uninstall-script)
