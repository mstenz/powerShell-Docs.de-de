---
ms.date: 01/10/2020
keywords: powershell,cmdlet
title: Schreiben von portablen Modulen
ms.openlocfilehash: 124e6efadfd07b8c5214a5c0446b1589f7142388
ms.sourcegitcommit: cab4e4e67dbed024864887c7f8984abb4db3a78b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2020
ms.locfileid: "76022244"
---
# <a name="portable-modules"></a>Portable Module

Windows PowerShell ist für [.NET Framework][] geschrieben, PowerShell Core hingegen für [.NET Core][]. Portable Module sind Module, die sowohl in Windows PowerShell als auch PowerShell Core funktionieren. .NET Framework und .NET Core sind zwar hoch kompatibel, doch gibt es zwischen beiden Unterschiede bei den verfügbaren APIs. Es gibt auch Unterschiede bei den in Windows PowerShell und PowerShell Core verfügbaren APIs. Bei Modulen, die in beiden Umgebungen verwendet werden sollen, müssen diese Unterschiede beachtet werden.

## <a name="porting-an-existing-module"></a>Portieren eines vorhandenen Moduls

### <a name="porting-a-pssnapin"></a>Portieren eines PSSnapIn

PowerShell [SnapIns](/powershell/scripting/developer/cmdlet/modules-and-snap-ins) werden in PowerShell Core nicht unterstützt. Es ist jedoch einfach, ein PSSnapIn in ein PowerShell-Modul zu konvertieren. In der Regel befindet sich der PSSnapIn-Registrierungscode in einer einzelnen Quelldatei einer Klasse, die von [PSSnapIn][] abgeleitet ist.
Entfernen Sie diese Quelldatei aus dem Build, denn sie ist nicht mehr erforderlich.

Erstellen Sie mit [New-ModuleManifest][] ein neues Modulmanifest, das den PSSnapIn-Registrierungscode überflüssig macht. Einige der Werte aus dem **PSSnapIn** (z.B. **Description**) können innerhalb des Modulmanifests wiederverwendet werden.

Die **RootModule**-Eigenschaft im Modulmanifest sollte auf den Namen der Assembly (DLL) festgelegt werden, die die Cmdlets implementiert.

### <a name="the-net-portability-analyzer-aka-apiport"></a>Der .NET Portability Analyzer (auch bekannt als APIPort)

Um für Windows PowerShell geschriebene Module zum Arbeiten mit PowerShell Core zu portieren, beginnen Sie mit dem [.NET Portability Analyzer][]. Führen Sie dieses Tool für die kompilierte Assembly aus, um zu bestimmen, ob die im Modul verwendeten .NET-APIs mit .NET Framework, .NET Core und anderen .NET-Runtimes kompatibel sind. Das Tool schlägt alternative APIs vor, wenn sie vorhanden sind. Andernfalls müssen Sie unter Umständen [Runtimeüberprüfungen][] hinzufügen und in bestimmten Runtimes nicht verfügbare Funktionen einschränken.

## <a name="creating-a-new-module"></a>Erstellen eines neuen Moduls

Wenn Sie ein neues Modul erstellen, sollten Sie die [.NET CLI][] verwenden.

### <a name="installing-the-powershell-standard-module-template"></a>Installieren der PowerShell Standard-Modulvorlage

Sobald die .NET CLI installiert ist, installieren Sie eine Vorlagenbibliothek zum Generieren eines einfachen PowerShell-Moduls.
Das Modul wird mit Windows PowerShell, PowerShell Core, Windows, Linux und macOS kompatibel sein.

Im folgenden Beispiel wird veranschaulicht, wie Sie die Vorlage installieren:

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

Nachdem die Vorlage installiert ist, können Sie ein neues PowerShell-Modulprojekt mit der Vorlage erstellen. In diesem Beispiel wird das Beispielmodul „myModule“ genannt.

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

### <a name="building-the-module"></a>Erstellen des Moduls

Verwenden Sie standardmäßige .NET CLI-Befehle, um das Projekt zu erstellen.

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

Nach dem Erstellen des Moduls können Sie es importieren und das Beispielcmdlet ausführen.

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

In den folgenden Abschnitten werden einige der von dieser Vorlage verwendeten Technologien ausführlich beschrieben.

## <a name="net-standard-library"></a>.NET Standard-Bibliothek

[.NET Standard][] ist eine formale Spezifikation von .NET-APIs, die in allen .NET-Implementierungen verfügbar sind. Für .NET Standard bestimmter verwalteter Code kann mit den Versionen von .NET Framework und .NET Core verwendet werden, die mit dieser Version von .NET Standard kompatibel sind.

> [!NOTE]
> Weil die API-Implementierung in .NET Core auch dann eine `PlatformNotSupportedException` während der Runtime auslösen kann, wenn eine API in .NET Standard vorhanden ist, sollten Sie als bewährte Methode in beiden Umgebungen Tests für das Modul ausführen, um die Kompatibilität mit Windows PowerShell und PowerShell Core zu überprüfen.
> Führen Sie auch dann Tests unter Linux und macOS aus, wenn Ihr Modul plattformübergreifend verwendbar sein soll.

Die Orientierung an .NET Standard stellt sicher, dass bei der Weiterentwicklung des Moduls nicht versehentlich inkompatible APIs in das Modul eingeführt werden. Inkompatibilitäten werden zum Zeitpunkt der Kompilierung statt während der Runtime festgestellt.

Solange Sie kompatible APIs verwenden, ist eine Orientierung an .NET Standard allerdings nicht erforderlich, damit ein Modul mit Windows PowerShell und PowerShell Core funktioniert. Die Zwischensprache (Intermediate Language, IL) ist mit beiden Runtimes kompatibel. Sie können sich an .NET Framework 4.6.1 orientieren, das mit .NET Standard 2.0 kompatibel ist. Wenn Sie außerhalb von .NET Standard 2.0 keine APIs verwenden, funktioniert Ihr Modul ohne erneute Kompilierung mit PowerShell Core 6.

## <a name="powershell-standard-library"></a>PowerShell Standard-Bibliothek

Die [PowerShell Standard][]-Bibliothek ist eine formale Spezifikation von PowerShell-APIs, die in allen PowerShell-Versionen verfügbar sind, die der Version dieses Standards entsprechen oder höher sind.

[PowerShell Standard 5.1][] ist z.B. sowohl mit Windows PowerShell 5.1 als auch mit PowerShell Core 6.0 oder höher kompatibel.

Sie sollten Ihr Modul mit der PowerShell Standard-Bibliothek kompilieren. Die Bibliothek stellt sicher, dass die APIs verfügbar und sowohl in Windows PowerShell als auch PowerShell Core 6 implementiert sind.
PowerShell Standard soll stets aufwärtskompatibel sein. Ein mithilfe der PowerShell Standard-Bibliothek 5.1 erstelltes Modul ist immer mit zukünftigen Versionen von PowerShell kompatibel.

## <a name="module-manifest"></a>Modulmanifest

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a>Angeben der Kompatibilität mit Windows PowerShell und PowerShell Core

Nachdem Sie überprüft haben, ob Ihr Modul sowohl mit Windows PowerShell als auch PowerShell Core funktioniert, sollte das Modulmanifest explizit mit der [CompatiblePSEditions][]-Eigenschaft die Kompatibilität angeben. Der Wert `Desktop` bedeutet, dass das Modul mit Windows PowerShell kompatibel ist, während der Wert `Core` bedeutet, dass das Modul mit PowerShell Core kompatibel ist. Sowohl `Desktop` als auch `Core` einzubeziehen bedeutet, dass das Modul mit Windows PowerShell und PowerShell Core kompatibel ist.

> [!NOTE]
> `Core` bedeutet nicht automatisch, dass das Modul mit Windows, Linux und macOS kompatibel ist.
> Die **CompatiblePSEditions**-Eigenschaft wurde in PowerShell v5 eingeführt. Bei Modulmanifesten, die die **CompatiblePSEditions**-Eigenschaft verwenden, tritt in Versionen vor PowerShell v5 beim Laden ein Fehler auf.

### <a name="indicating-os-compatibility"></a>Angeben der Betriebssystemkompatibilität

Überprüfen Sie zunächst, ob Ihr Modul unter Linux und macOS funktioniert. Geben Sie als Nächstes die Kompatibilität mit diesen Betriebssystemen im Modulmanifest an. Dies erleichtert den Benutzern, die mit ihren Betriebssystemen kompatiblen Versionen Ihres Moduls zu finden, wenn es im [PowerShell Gallery][] veröffentlicht wird.

Im Modulmanifest hat die `PrivateData`-Eigenschaft eine `PSData`-Untereigenschaft. Die optionale `Tags`-Eigenschaft von `PSData` akzeptiert ein Array von Werten, die im PowerShell-Katalog angezeigt werden. Der PowerShell-Katalog unterstützt die folgenden Kompatibilitätswerte:

| Tag               | Beschreibung                                |
|-------------------|--------------------------------------------|
| PSEdition_Core    | Kompatibel mit PowerShell Core 6          |
| PSEdition_Desktop | Kompatibel mit Windows PowerShell         |
| Windows           | Kompatibel mit Windows                    |
| Linux             | Kompatibel mit Linux (keine spezifische Distribution) |
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

## <a name="dependency-on-native-libraries"></a>Abhängigkeit von nativen Bibliotheken

Bei Modulen, die für die Verwendung über verschiedene Betriebssysteme oder Prozessorarchitekturen hinweg konzipiert sind, besteht möglicherweise eine Abhängigkeit von einer verwalteten Bibliothek, die ihrerseits selbst von einigen nativen Bibliotheken abhängig ist.

Vor PowerShell 7 war benutzerdefinierter Code erforderlich, um die entsprechende native DLL zu laden, damit sie von der verwalteten Bibliothek gefunden werden kann.

Ab PowerShell 7 wird in Unterordnern des Speicherorts der verwalteten Bibliothek nach nativen Binärdateien gesucht, die geladen werden sollen. Die Suche erfolgt gemäß einer Teilmenge der [.NET-RID-Katalog][]-Notation.

```
managed.dll folder
                |
                |--- 'win-x64' folder
                |       |--- native.dll
                |
                |--- 'win-x86' folder
                |       |--- native.dll
                |
                |--- 'win-arm' folder
                |       |--- native.dll
                |
                |--- 'win-arm64' folder
                |       |--- native.dll
                |
                |--- 'linux-x64' folder
                |       |--- native.so
                |
                |--- 'linux-x86' folder
                |       |--- native.so
                |
                |--- 'linux-arm' folder
                |       |--- native.so
                |
                |--- 'linux-arm64' folder
                |       |--- native.so
                |
                |--- 'osx-x64' folder
                |       |--- native.dylib
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Runtimeüberprüfungen]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/scripting/gallery/concepts/module-psedition-support
[.NET-RID-Katalog]: https://docs.microsoft.com/dotnet/core/rid-catalog
