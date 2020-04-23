---
ms.date: 09/26/2017
contributor: keithb
keywords: gallery,powershell,cmdlet,psget
title: Vorabmodulversionen
ms.openlocfilehash: eced067dd21082de0db653daf3b838217154f1dd
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328141"
---
# <a name="prerelease-module-versions"></a>Vorabmodulversionen

Ab Version 1.6.0 unterstützen PowerShellGet und der PowerShell-Katalog das Kennzeichnen von Versionen ab 1.0.0 als Vorabversion. Vor der Einführung dieses Features waren Vorabversionspakete auf Versionen beschränkt, die mit 0 beginnen. Ziel dieser Features ist es, eine größere Unterstützung für die Versionsverwaltungsspezifikation [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) bereitzustellen, ohne die Abwärtskompatibilität mit PowerShell Version 3 und höher oder vorhandenen PowerShellGet-Versionen einzuschränken. Der Schwerpunkt dieses Themas liegt auf modulspezifischen Features. Eine Erläuterung der entsprechenden Features für Skripts finden Sie im Thema [Vorabskriptversionen](script-prerelease-support.md). Mit diesen Features können Herausgeber ein Modul oder Skript als Version 2.5.0-alpha identifizieren und später eine für die Produktion freigegebene 2.5.0-Version veröffentlichen, die die Vorabversion ablöst.

Allgemein umfassen die Vorabversions-Modulfeatures u.a. Folgendes:

- Durch Hinzufügen einer Vorabversionszeichenfolge zum PSData-Abschnitt des Modulmanifests wird das Modul als Vorabversion identifiziert. Wenn das Modul im PowerShell-Katalog veröffentlicht wird, werden diese Daten aus dem Manifest extrahiert und zum Identifizieren von Vorabversionspaketen verwendet.
- Zum Abrufen von Vorabversionspaketen muss den PowerShellGet-Befehlen `-AllowPrerelease`, `Find-Module`, `Install-Module` und `Update-Module` das `Save-Module`-Flag hinzugefügt werden. Wenn das Flag nicht angegeben ist, werden keine Vorabversionspakete angezeigt.
- Die durch `Find-Module` und `Get-InstalledModule` sowie im PowerShell-Katalog angezeigten Modulversionen werden als einzelne Zeichenfolge mit angefügter Vorabversionszeichenfolge angezeigt (z.B. „2.5.0-alpha“).

Einzelheiten zu den Features finden Sie weiter unten.

Diese Änderungen wirken sich nicht auf die in PowerShell integrierte Modulversionsunterstützung aus und sind mit PowerShell 3.0, 4.0 und 5 kompatibel.

## <a name="identifying-a-module-version-as-a-prerelease"></a>Identifizieren einer Modulversion als Vorabversion

Um PowerShellGet-Unterstützung für Vorabversionen bereitzustellen, müssen die folgenden zwei Felder innerhalb des Modulmanifests verwendet werden:

- Der im Modulmanifest enthaltene ModuleVersion-Schlüssel muss bei Verwendung einer Vorabversion eine Versionsnummer bestehend aus 3 Ziffern enthalten und mit der vorhandenen PowerShell-Versionsverwaltung übereinstimmen. Das Versionsformat würde „A.B.C“ lauten, wobei „A“, „B“ und „C“ für ganze Zahlen stehen.
- Die Vorabversionszeichenfolge wird im Modulmanifest im PSData-Abschnitt von „PrivateData“ angegeben.

Die Anforderungen für die Vorabversionszeichenfolge werden nachfolgend ausführlich erläutert.

Ein Beispielabschnitt eines Modulmanifests, das ein Modul als Vorabversion definiert, sieht etwa wie folgt aus:

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

Die Anforderungen für die Vorabversionszeichenfolge werden nachfolgend im Einzelnen erläutert:

- Die Vorabversionszeichenfolge darf nur angegeben werden, wenn der ModuleVersion-Schlüssel 3 Ziffern enthält, nämlich „Hauptversion.Nebenversion.Build“. Dies entspricht SemVer v1.0.0.
- Ein Bindestrich fungiert als Trennzeichen zwischen der Buildnummer und der Vorabversionszeichenfolge. Ein Bindestrich darf nur als erstes Zeichen in die Vorabversionszeichenfolge eingefügt werden.
- Die Vorabversionszeichenfolge darf nur alphanumerische ASCII-Zeichen [0-9, A-Z, a-z] enthalten. Es wird empfohlen, dass die Vorabversionszeichenfolge mit einem alphanumerischen Zeichen beginnt. So wird beim Prüfen einer Liste von Paketen einfacher erkannt, dass es sich um eine Vorabversion handelt.
- Zurzeit werden nur SemVer v1.0.0-Vorabversionszeichenfolgen unterstützt. Diese Zeichenfolge darf **keine** Punkte oder Pluszeichen [.+] enthalten, die in SemVer 2.0 zulässig sind.
- Zu den unterstützten Vorabversionszeichenfolgen zählen beispielsweise „-alpha“, „-alpha1“, „-BETA“ und „-update20171020“.

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>Auswirkung der Vorabversionsverwaltung auf die Sortierreihenfolge und Installationsordner

Die Sortierreihenfolge ändert sich bei der Verwendung einer Vorabversion, was für die Veröffentlichung von Inhalten im PowerShell-Katalog und der Installation von Modulen mit PowerShellGet-Befehlen relevant ist. Wenn die Vorabversionszeichenfolge für zwei Module angegeben ist, basiert die Sortierreihenfolge auf dem Zeichenfolgenteil nach dem Bindestrich. Deshalb ist Version 2.5.0-alpha niedriger als 2.5.0-beta, die wiederum niedriger als 2.5.0-gamma ist. Wenn zwei Module den gleichen ModuleVersion-Schlüssel und nur eine Vorabversionszeichenfolge aufweisen, wird das Modul ohne die Vorabversionszeichenfolge als für die Produktion freigegebene Version behandelt und gegenüber der Vorabversion (die die Vorabversionszeichenfolge enthält) als höhere Version sortiert. Beispiel: Beim Vergleich der Versionen 2.5.0 und 2.5.0-beta wird die Version 2.5.0 als die höhere der beiden Versionen betrachtet.

Beim Veröffentlichen von Inhalten im PowerShell-Katalog muss die Version des Moduls, das veröffentlicht wird, standardmäßig eine höhere Version aufweisen als zuvor veröffentlichte Versionen, die nicht im PowerShell-Katalog vorhanden sind.

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>Suchen und Abrufen von Vorabversionspaketen mit PowerShellGet-Befehlen

Wenn Sie Vorabversionspakete mit den PowerShellGet-Befehlen „Find-Module“, „Install-Module“, „Update-Module“ und „Save-Module“ verwenden, müssen Sie das „-AllowPrerelease“-Flag hinzufügen. Bei der Angabe von „-AllowPrerelease“ werden vorhandene Vorabversionspakete eingeschlossen. Wenn das „-AllowPrerelease“-Flag nicht angegeben ist, werden keine Vorabversionspakete angezeigt.

Die einzigen Ausnahmen hierfür in Bezug auf PowerShellGet-Modulbefehle sind „Get-InstalledModule“ und in einigen Fällen „Uninstall-Module“.

- Mit „Get-InstalledModule“ werden immer automatisch die Vorabversionsinformationen in der Versionszeichenfolge für Module angezeigt.
- Mit „Uninstall-Module“ wird standardmäßig die neueste Version eines Moduls deinstalliert, wenn __keine Version__ angegeben ist. Dieses Verhalten wurde nicht geändert. Wenn jedoch mit „-RequiredVersion“ eine Vorabversion angegeben wird, ist „-AllowPrerelease“ erforderlich.

## <a name="examples"></a>Beispiele

Nehmen Sie an, der PowerShell-Katalog weist die TestPackage-Modulversionen 1.8.0 und 1.9.0-alpha auf. Wenn `-AllowPrerelease` nicht angegeben ist, wird nur Version 1.8.0 zurückgegeben.

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

Um eine Vorabversion zu installieren, müssen Sie immer „-AllowPrerelease“ angeben. Es reicht nicht aus, eine Vorabversionszeichenfolge anzugeben.

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

Bei dem vorherigen Befehl ist ein Fehler aufgetreten, da „-AllowPrerelease“ nicht angegeben wurde. Durch Hinzufügen von `-AllowPrerelease` kann dies behoben werden.

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

Die parallele Installation von Modulversionen, die sich lediglich durch die angegebene Vorabversion unterscheiden, wird nicht unterstützt. Bei der Installation eines Moduls mit PowerShellGet werden verschiedene Versionen desselben Moduls parallel installiert, indem mit dem ModuleVersion-Schlüssel ein Ordnername erstellt wird. Für den Ordnernamen wird der ModuleVersion-Schlüssel ohne die Vorabversionszeichenfolge verwendet. Wenn ein Benutzer MyModule Version 2.5.0-alpha installiert, wird das Modul im Ordner `MyModule\2.5.0` installiert. Wenn der Benutzer dann 2.5.0-beta installiert, **überschreibt** die Version 2.5.0-beta den Inhalt des Ordners `MyModule\2.5.0`. Ein Vorteil bei dieser Vorgehensweise besteht darin, dass nach der Installation der für die Produktion freigegebenen Version die Vorabversion nicht deinstalliert werden muss. Im folgenden Beispiel wird gezeigt, wie dies aussieht:

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

Mit „Uninstall-Module“ wird die neueste Version eines Moduls entfernt, wenn „-RequiredVersion“ nicht angegeben ist.
Wenn „-RequiredVersion“ angegeben ist und es sich um eine Vorabversion handelt, muss „-AllowPrerelease“ zum Befehl hinzugefügt werden.

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

## <a name="more-details"></a>Weitere Informationen

- [Vorabskriptversionen](script-prerelease-support.md)
- [Find-Module](/powershell/module/powershellget/find-module)
- [Install-Module](/powershell/module/powershellget/install-module)
- [Save-Module](/powershell/module/powershellget/save-module)
- [Update-Module](/powershell/module/powershellget/Update-Module)
- [Get-InstalledModule](/powershell/module/powershellget/get-installedmodule)
- [UnInstall-Module](/powershell/module/powershellget/uninstall-module)
