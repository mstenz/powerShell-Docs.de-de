---
ms.date: 12/14/2018
keywords: powershell,cmdlet
title: Schreiben von portablen Modulen
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: d396d0e4cfe3d279f399c17e7337380a31d373ac
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747720"
---
# <a name="portable-modules"></a>Portable Module

Windows PowerShell geschrieben wird, [.NET Framework][] beim Schreiben von PowerShell Core für ist [.NET Core][]. Portable Module sind Module, die in Windows PowerShell und PowerShell Core funktionieren. Während .NET Framework und .NET Core hoch kompatibel sind, gibt es Unterschiede in den APIs zur Verfügung. Es gibt auch Unterschiede in den APIs in Windows PowerShell und PowerShell Core verfügbar. Module, die in beiden Umgebungen verwendet werden soll, müssen sich dieser Unterschiede bewusst sein.

## <a name="porting-an-existing-module"></a>Portieren eines vorhandenen Moduls

### <a name="porting-a-pssnapin"></a>Portieren ein PSSnapIn

PowerShell SnapIns (PSSnapIn) werden in PowerShell Core nicht unterstützt. Es ist jedoch einfach um ein PSSnapIn in ein PowerShell-Modul zu konvertieren. In der Regel die PSSnapIn-Registrierungscode wird in eine einzelne Quelldatei von einer Klasse, die von abgeleitet [PSSnapIn][]. Entfernen Sie diese Quelldatei aus dem Build; Es ist nicht mehr erforderlich.

Verwendung [New-ModuleManifest][] ein neues modulmanifest zu erstellen, müssen die PSSnapIn-Registrierungscode ersetzt. Einige der Werte aus den PSSnapIn (z. B. Beschreibung) kann innerhalb des modulmanifests wiederverwendet werden.

Die `RootModule` Eigenschaft im modulmanifest sollte auf den Namen der Assembly (Dll) implementiert die Cmdlets festgelegt werden.

### <a name="the-net-portability-analyzer-aka-apiport"></a>.NET Portability Analyzer (auch bekannt als APIPort)

Port-Modulen, geschrieben für Windows PowerShell zum Arbeiten mit PowerShell Core, beginnen Sie mit der [.NET Portability Analyzer][]. Führen Sie dieses Tool, für die kompilierte Assembly zu bestimmen, ob die im Modul verwendet APIs von .NET mit .NET Framework, .NET Core und anderen Laufzeiten .NET kompatibel sind. Das Tool schlägt alternative APIs vor, wenn sie vorhanden sind. Andernfalls unter Umständen müssen Sie hinzuzufügende [Überprüfungen zur Laufzeit][] und Einschränken von Funktionen in bestimmten Laufzeiten nicht verfügbar sind.

## <a name="creating-a-new-module"></a>Erstellen eines neuen Moduls

Wenn Sie ein neues Modul zu erstellen, es wird empfohlen, verwenden Sie die [.NET CLI][].

### <a name="installing-the-powershell-standard-module-template"></a>Installieren der PowerShell-Standard-Modul-Vorlage

Sobald die .NET CLI installiert ist, installieren Sie eine Vorlagenbibliothek, die zum Generieren von einem einfachen PowerShell-Modul.
Das Modul wird mit Windows PowerShell, PowerShell Core, Windows, Linux und MacOS kompatibel sein.

Das folgende Beispiel zeigt, wie Sie die Vorlage zu installieren:

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
```

```output
  Restoring packages for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj...
  Installing Microsoft.PowerShell.Standard.Module.Template 0.1.3.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.targets.
  Restore completed in 1.66 sec for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj.

Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.
  -n, --name          The name for the output being created. If no name is specified, the name of the current directory is used.
  -o, --output        Location to place the generated output.
  -i, --install       Installs a source or a template pack.
  -u, --uninstall     Uninstalls a source or a template pack.
  --nuget-source      Specifies a NuGet source to use during install.
  --type              Filters templates based on available types. Predefined values are "project", "item" or "other".
  --force             Forces content to be generated even if it would change existing files.
  -lang, --language   Filters templates based on language and specifies the language of the template to create.


Templates                                         Short Name         Language          Tags
----------------------------------------------------------------------------------------------------------------------------
Console Application                               console            [C#], F#, VB      Common/Console
Class library                                     classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module                        psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a>Erstellen eines neuen Modulprojekts

Nachdem die Vorlage installiert ist, können Sie ein neues PowerShell-Modul-Projekt mit der Vorlage erstellen. In diesem Beispiel wird das Beispiel-Modul 'MyModule' aufgerufen.

```
PS> mkdir myModule

    Directory: C:\Users\Steve

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 8/3/2018 2:41 PM myModule

PS> cd myModule
PS C:\Users\Steve\myModule> dotnet new psmodule

The template "PowerShell Standard Module" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Steve\myModule\myModule.csproj...
  Restoring packages for C:\Users\Steve\myModule\myModule.csproj...
  Installing PowerShellStandard.Library 5.1.0.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.targets.
  Restore completed in 1.76 sec for C:\Users\Steve\myModule\myModule.csproj.

Restore succeeded.
```

### <a name="building-the-module"></a>Erstellen das Modul

Verwenden Sie standard .NET CLI-Befehle, um das Projekt zu erstellen.

```powershell
dotnet build
```

```output
PS C:\Users\Steve\myModule> dotnet build
Microsoft (R) Build Engine version 15.7.179.6572 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 76.85 ms for C:\Users\Steve\myModule\myModule.csproj.
  myModule -> C:\Users\Steve\myModule\bin\Debug\netstandard2.0\myModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:05.40
```

### <a name="testing-the-module"></a>Testen des Moduls

Nach dem Erstellen des Moduls, können Sie ihn importieren und führen Sie das beispielcmdlet.

```powershell
ipmo .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
PS C:\Users\Steve\myModule> ipmo .\bin\Debug\netstandard2.0\myModule.dll
PS C:\Users\Steve\myModule> Test-SampleCmdlet -?

NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


PS C:\Users\Steve\myModule> Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat

FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

Die folgenden Abschnitte beschreiben ausführlich einige der Technologien, die von dieser Vorlage verwendet.

## <a name="net-standard-library"></a>.NET standard-Bibliothek

[.NET standard][] ist eine formale Spezifikation von .NET-APIs, die in allen .NET-Implementierungen verfügbar sind. Verwalteter Code für .NET Standard kann mit der .NET Framework und .NET Core-Versionen, die mit dieser Version von .NET Standard kompatibel sind.

> [!NOTE]
> Zwar eine API in .NET Standard vorhanden sein kann, kann die API-Implementierung in .NET Core Auslösen einer `PlatformNotSupportedException` zur Laufzeit, also zum Überprüfen der Kompatibilität mit Windows PowerShell und PowerShell Core, die bewährte Methode ist zum Ausführen von Tests für das Modul in beiden Umgebungen.
> Führen Sie Tests auch unter Linux und MacOS, wenn Ihr Modul plattformübergreifend verwendbar sein soll.

Stellen Sie sicher, dass der Weiterentwicklung des Moduls, inkompatible APIs versehentlich in das Modul eingeführt, nicht von .NET Standard unterstützt werden. Inkompatibilitäten werden zum Zeitpunkt der Kompilierung nicht Runtime ermittelt.

Allerdings nicht erforderlich, um auf .NET Standard für ein Modul mit Windows PowerShell und PowerShell Core funktioniert, solange Sie kompatible APIs verwenden. Die Intermediate Language (IL), die zwischen den zwei Laufzeiten kompatibel ist. Sie können .NET Framework 4.6.1 abzielen, die mit .NET Standard 2.0 kompatibel ist. Wenn Sie APIs außerhalb von .NET Standard 2.0 nicht verwenden, funktioniert Ihr Modul mit PowerShell Core 6 ohne erneute Kompilierung aus.

## <a name="powershell-standard-library"></a>PowerShell-Standardbibliothek

Die [PowerShell-Standard][] -Bibliothek ist eine formale Spezifikation von PowerShell-APIs in allen PowerShell-Versionen, die größer als oder gleich der Version dieses Standards zur Verfügung.

Z. B. [Standard für PowerShell 5.1][] ist kompatibel mit sowohl PowerShell Core 6.0 als auch Windows PowerShell 5.1 oder höher.

Es wird empfohlen, dass Sie Kompilieren des Moduls mit PowerShell-Standard-Bibliothek. Die Bibliothek wird sichergestellt, dass die APIs in Windows PowerShell und PowerShell Core 6 implementiert und verfügbar sind.
PowerShell-Standard ist immer leitet-kompatibel sein soll. Ein Modul mithilfe von PowerShell 5.1 für Standard-Bibliothek erstellt werden immer für zukünftige Versionen von PowerShell.

## <a name="module-manifest"></a>Modulmanifest

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a>Gibt an, Kompatibilität mit Windows PowerShell und PowerShell Core

Nachdem Sie bestätigt haben, dass Ihr Modul für Windows PowerShell und PowerShell Core funktioniert, das modulmanifest sollten explizit angeben Kompatibilität mit der [CompatiblePSEditions][] Eigenschaft. Der Wert `Desktop` bedeutet, dass das Modul kompatibel mit Windows PowerShell, während ein Wert von `Core` bedeutet, dass das Modul mit PowerShell Core kompatibel ist. Einschließlich `Desktop` und `Core` bedeutet, dass das Modul mit Windows PowerShell und PowerShell Core kompatibel ist.

> [!NOTE]
> `Core` automatisch bedeutet nicht, dass das Modul mit Windows, Linux und MacOS kompatibel ist.
> Die **CompatiblePSEditions** Eigenschaft wurde in PowerShell 5.x eingeführt. Modul-Manifeste, verwenden die **CompatiblePSEditions** Eigenschaft nicht in Versionen vor PowerShell 5.x geladen.

### <a name="indicating-os-compatibility"></a>Gibt an, Betriebssystemkompatibilität

Überprüfen Sie zunächst, dass Ihre Module unter Linux und MacOS funktioniert. Geben Sie als Nächstes die Kompatibilität mit diesen Betriebssystemen im modulmanifest an. Dies erleichtert es für Benutzer Ihres Moduls für ihr Betriebssystem bei der Veröffentlichung, finden die [PowerShell Gallery][].

Im modulmanifest den `PrivateData` Eigenschaft verfügt über eine `PSData` Untereigenschaft. Der optionale `Tags` Eigenschaft `PSData` akzeptiert ein Array von Werten, die im PowerShell-Katalog werden angezeigt. PowerShell-Katalog unterstützt die folgenden Werte für die Anwendungskompatibilität:

| Tag               | Beschreibung                                |
|-------------------|--------------------------------------------|
| PSEdition_Core    | Mit PowerShell Core 6 kompatibel          |
| "Psedition_desktop" | Kompatibel mit Windows PowerShell         |
| Windows           | Kompatibel mit Windows                    |
| Linux             | Kompatibel mit Linux (keine spezifischen Distribution) |
| macOS             | Kompatibel mit macOS                      |

Beispiel:

```powershell
@{
    GUID = "4ae9fd46-338a-459c-8186-07f910774cb8"
    Author = "Microsoft Corporation"
    CompanyName = "Microsoft Corporation"
    Copyright = "(C) Microsoft Corporation. All rights reserved."
    HelpInfoUri = "https://go.microsoft.com/fwlink/?linkid=855962"
    ModuleVersion = "1.2.4"
    PowerShellVersion = "3.0"
    ClrVersion = "4.0"
    RootModule = "PackageManagement.psm1"
    Description = 'PackageManagement (a.k.a. OneGet) is a new way to discover and install software packages from around the web.
 It is a manager or multiplexer of existing package managers (also called package providers) that unifies Windows package management with a single Windows PowerShell interface. With PackageManagement, you can do the following.
  - Manage a list of software repositories in which packages can be searched, acquired and installed
  - Discover software packages
  - Seamlessly install, uninstall, and inventory packages from one or more software repositories'

    CmdletsToExport = @(
        'Find-Package',
        'Get-Package',
        'Get-PackageProvider',
        'Get-PackageSource',
        'Install-Package',
        'Import-PackageProvider'
        'Find-PackageProvider'
        'Install-PackageProvider'
        'Register-PackageSource',
        'Set-PackageSource',
        'Unregister-PackageSource',
        'Uninstall-Package'
        'Save-Package'
    )

    FormatsToProcess  = @('PackageManagement.format.ps1xml')

    PrivateData = @{
        PSData = @{
            Tags = @('PackageManagement', 'PSEdition_Core', 'PSEdition_Desktop', 'Windows', 'Linux', 'macOS')
            ProjectUri = 'https://oneget.org'
        }
    }
}
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Überprüfungen zur Laufzeit]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell-Standard]: https://github.com/PowerShell/PowerShellStandard
[Standard für PowerShell 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
