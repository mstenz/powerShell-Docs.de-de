---
ms.date: 12/14/2018
keywords: powershell,cmdlet
title: Schreiben von portablen Modulen
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086407"
---
# <a name="portable-modules"></a><span data-ttu-id="e05f7-103">Portable Module</span><span class="sxs-lookup"><span data-stu-id="e05f7-103">Portable Modules</span></span>

<span data-ttu-id="e05f7-104">Windows PowerShell ist für [.NET Framework][] geschrieben, PowerShell Core hingegen für [.NET Core][].</span><span class="sxs-lookup"><span data-stu-id="e05f7-104">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="e05f7-105">Portable Module sind Module, die sowohl in Windows PowerShell als auch PowerShell Core funktionieren.</span><span class="sxs-lookup"><span data-stu-id="e05f7-105">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="e05f7-106">.NET Framework und .NET Core sind zwar hoch kompatibel, doch gibt es zwischen beiden Unterschiede bei den verfügbaren APIs.</span><span class="sxs-lookup"><span data-stu-id="e05f7-106">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="e05f7-107">Es gibt auch Unterschiede bei den in Windows PowerShell und PowerShell Core verfügbaren APIs.</span><span class="sxs-lookup"><span data-stu-id="e05f7-107">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="e05f7-108">Bei Modulen, die in beiden Umgebungen verwendet werden sollen, müssen diese Unterschiede beachtet werden.</span><span class="sxs-lookup"><span data-stu-id="e05f7-108">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="e05f7-109">Portieren eines vorhandenen Moduls</span><span class="sxs-lookup"><span data-stu-id="e05f7-109">Porting an Existing Module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="e05f7-110">Portieren eines PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="e05f7-110">Porting a PSSnapIn</span></span>

<span data-ttu-id="e05f7-111">PowerShell SnapIns (PSSnapIn) werden in PowerShell Core nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e05f7-111">PowerShell SnapIns (PSSnapIn) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="e05f7-112">Es ist jedoch einfach, ein PSSnapIn in ein PowerShell-Modul zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="e05f7-112">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="e05f7-113">In der Regel befindet sich der PSSnapIn-Registrierungscode in einer einzelnen Quelldatei einer Klasse, die von [PSSnapIn][] abgeleitet ist.</span><span class="sxs-lookup"><span data-stu-id="e05f7-113">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span> <span data-ttu-id="e05f7-114">Entfernen Sie diese Quelldatei aus dem Build, denn sie ist nicht mehr erforderlich.</span><span class="sxs-lookup"><span data-stu-id="e05f7-114">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="e05f7-115">Erstellen Sie mit [New-ModuleManifest][] ein neues Modulmanifest, das den PSSnapIn-Registrierungscode überflüssig macht.</span><span class="sxs-lookup"><span data-stu-id="e05f7-115">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="e05f7-116">Einige der Werte aus dem PSSnapIn (z.B. „Description“) können innerhalb des Modulmanifests wiederverwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e05f7-116">Some of the values from the PSSnapIn (such as Description) can be reused within the module manifest.</span></span>

<span data-ttu-id="e05f7-117">Die `RootModule`-Eigenschaft im Modulmanifest sollte auf den Namen der Assembly (DLL) festgelegt werden, die die Cmdlets implementiert.</span><span class="sxs-lookup"><span data-stu-id="e05f7-117">The `RootModule` property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="e05f7-118">Der .NET Portability Analyzer (auch bekannt als APIPort)</span><span class="sxs-lookup"><span data-stu-id="e05f7-118">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="e05f7-119">Um für Windows PowerShell geschriebene Module zum Arbeiten mit PowerShell Core zu portieren, beginnen Sie mit dem [.NET Portability Analyzer][].</span><span class="sxs-lookup"><span data-stu-id="e05f7-119">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="e05f7-120">Führen Sie dieses Tool für die kompilierte Assembly aus, um zu bestimmen, ob die im Modul verwendeten .NET-APIs mit .NET Framework, .NET Core und anderen .NET-Runtimes kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="e05f7-120">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="e05f7-121">Das Tool schlägt alternative APIs vor, wenn sie vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="e05f7-121">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="e05f7-122">Andernfalls müssen Sie unter Umständen [Runtimeüberprüfungen][] hinzufügen und in bestimmten Runtimes nicht verfügbare Funktionen einschränken.</span><span class="sxs-lookup"><span data-stu-id="e05f7-122">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="e05f7-123">Erstellen eines neuen Moduls</span><span class="sxs-lookup"><span data-stu-id="e05f7-123">Creating a New Module</span></span>

<span data-ttu-id="e05f7-124">Wenn Sie ein neues Modul erstellen, sollten Sie die [.NET CLI][] verwenden.</span><span class="sxs-lookup"><span data-stu-id="e05f7-124">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="e05f7-125">Installieren der PowerShell Standard-Modulvorlage</span><span class="sxs-lookup"><span data-stu-id="e05f7-125">Installing the PowerShell Standard Module Template</span></span>

<span data-ttu-id="e05f7-126">Sobald die .NET CLI installiert ist, installieren Sie eine Vorlagenbibliothek zum Generieren eines einfachen PowerShell-Moduls.</span><span class="sxs-lookup"><span data-stu-id="e05f7-126">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="e05f7-127">Das Modul wird mit Windows PowerShell, PowerShell Core, Windows, Linux und macOS kompatibel sein.</span><span class="sxs-lookup"><span data-stu-id="e05f7-127">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="e05f7-128">Im folgenden Beispiel wird veranschaulicht, wie Sie die Vorlage installieren:</span><span class="sxs-lookup"><span data-stu-id="e05f7-128">The following example shows how to install the template:</span></span>

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

### <a name="creating-a-new-module-project"></a><span data-ttu-id="e05f7-129">Erstellen eines neuen Modulprojekts</span><span class="sxs-lookup"><span data-stu-id="e05f7-129">Creating a New Module Project</span></span>

<span data-ttu-id="e05f7-130">Nachdem die Vorlage installiert ist, können Sie ein neues PowerShell-Modulprojekt mit der Vorlage erstellen.</span><span class="sxs-lookup"><span data-stu-id="e05f7-130">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="e05f7-131">In diesem Beispiel wird das Beispielmodul „myModule“ genannt.</span><span class="sxs-lookup"><span data-stu-id="e05f7-131">In this example, the sample module is called 'myModule'.</span></span>

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

### <a name="building-the-module"></a><span data-ttu-id="e05f7-132">Erstellen des Moduls</span><span class="sxs-lookup"><span data-stu-id="e05f7-132">Building the Module</span></span>

<span data-ttu-id="e05f7-133">Verwenden Sie standardmäßige .NET CLI-Befehle, um das Projekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e05f7-133">Use standard .NET CLI commands to build the project.</span></span>

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

### <a name="testing-the-module"></a><span data-ttu-id="e05f7-134">Testen des Moduls</span><span class="sxs-lookup"><span data-stu-id="e05f7-134">Testing the Module</span></span>

<span data-ttu-id="e05f7-135">Nach dem Erstellen des Moduls können Sie es importieren und das Beispielcmdlet ausführen.</span><span class="sxs-lookup"><span data-stu-id="e05f7-135">After building the module, you can import it and execute the sample cmdlet.</span></span>

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

<span data-ttu-id="e05f7-136">In den folgenden Abschnitten werden einige der von dieser Vorlage verwendeten Technologien ausführlich beschrieben.</span><span class="sxs-lookup"><span data-stu-id="e05f7-136">The following sections describe in detail some of the technologies used by this template.</span></span>

## <a name="net-standard-library"></a><span data-ttu-id="e05f7-137">.NET Standard-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="e05f7-137">.NET Standard Library</span></span>

<span data-ttu-id="e05f7-138">[.NET Standard][] ist eine formale Spezifikation von .NET-APIs, die in allen .NET-Implementierungen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="e05f7-138">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="e05f7-139">Für .NET Standard bestimmter verwalteter Code kann mit den Versionen von .NET Framework und .NET Core verwendet werden, die mit dieser Version von .NET Standard kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="e05f7-139">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="e05f7-140">Weil die API-Implementierung in .NET Core auch dann eine `PlatformNotSupportedException` während der Runtime auslösen kann, wenn eine API in .NET Standard vorhanden ist, sollten Sie als bewährte Methode in beiden Umgebungen Tests für das Modul ausführen, um die Kompatibilität mit Windows PowerShell und PowerShell Core zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="e05f7-140">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="e05f7-141">Führen Sie auch dann Tests unter Linux und macOS aus, wenn Ihr Modul plattformübergreifend verwendbar sein soll.</span><span class="sxs-lookup"><span data-stu-id="e05f7-141">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="e05f7-142">Die Orientierung an .NET Standard stellt sicher, dass bei der Weiterentwicklung des Moduls nicht versehentlich inkompatible APIs in das Modul eingeführt werden.</span><span class="sxs-lookup"><span data-stu-id="e05f7-142">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="e05f7-143">Inkompatibilitäten werden zum Zeitpunkt der Kompilierung statt während der Runtime festgestellt.</span><span class="sxs-lookup"><span data-stu-id="e05f7-143">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="e05f7-144">Solange Sie kompatible APIs verwenden, ist eine Orientierung an .NET Standard allerdings nicht erforderlich, damit ein Modul mit Windows PowerShell und PowerShell Core funktioniert.</span><span class="sxs-lookup"><span data-stu-id="e05f7-144">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="e05f7-145">Die Zwischensprache (Intermediate Language, IL) ist mit beiden Runtimes kompatibel.</span><span class="sxs-lookup"><span data-stu-id="e05f7-145">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="e05f7-146">Sie können sich an .NET Framework 4.6.1 orientieren, das mit .NET Standard 2.0 kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="e05f7-146">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="e05f7-147">Wenn Sie außerhalb von .NET Standard 2.0 keine APIs verwenden, funktioniert Ihr Modul ohne erneute Kompilierung mit PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="e05f7-147">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

## <a name="powershell-standard-library"></a><span data-ttu-id="e05f7-148">PowerShell Standard-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="e05f7-148">PowerShell Standard Library</span></span>

<span data-ttu-id="e05f7-149">Die [PowerShell Standard][]-Bibliothek ist eine formale Spezifikation von PowerShell-APIs, die in allen PowerShell-Versionen verfügbar sind, die der Version dieses Standards entsprechen oder höher sind.</span><span class="sxs-lookup"><span data-stu-id="e05f7-149">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="e05f7-150">[PowerShell Standard 5.1][] ist z.B. sowohl mit Windows PowerShell 5.1 als auch mit PowerShell Core 6.0 oder höher kompatibel.</span><span class="sxs-lookup"><span data-stu-id="e05f7-150">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="e05f7-151">Sie sollten Ihr Modul mit der PowerShell Standard-Bibliothek kompilieren.</span><span class="sxs-lookup"><span data-stu-id="e05f7-151">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="e05f7-152">Die Bibliothek stellt sicher, dass die APIs verfügbar und sowohl in Windows PowerShell als auch PowerShell Core 6 implementiert sind.</span><span class="sxs-lookup"><span data-stu-id="e05f7-152">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="e05f7-153">PowerShell Standard soll stets aufwärtskompatibel sein.</span><span class="sxs-lookup"><span data-stu-id="e05f7-153">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="e05f7-154">Ein mithilfe der PowerShell Standard-Bibliothek 5.1 erstelltes Modul ist immer mit zukünftigen Versionen von PowerShell kompatibel.</span><span class="sxs-lookup"><span data-stu-id="e05f7-154">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

## <a name="module-manifest"></a><span data-ttu-id="e05f7-155">Modulmanifest</span><span class="sxs-lookup"><span data-stu-id="e05f7-155">Module Manifest</span></span>

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="e05f7-156">Angeben der Kompatibilität mit Windows PowerShell und PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="e05f7-156">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="e05f7-157">Nachdem Sie überprüft haben, ob Ihr Modul sowohl mit Windows PowerShell als auch PowerShell Core funktioniert, sollte das Modulmanifest explizit mit der [CompatiblePSEditions][]-Eigenschaft die Kompatibilität angeben.</span><span class="sxs-lookup"><span data-stu-id="e05f7-157">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="e05f7-158">Der Wert `Desktop` bedeutet, dass das Modul mit Windows PowerShell kompatibel ist, während der Wert `Core` bedeutet, dass das Modul mit PowerShell Core kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="e05f7-158">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="e05f7-159">Sowohl `Desktop` als auch `Core` einzubeziehen bedeutet, dass das Modul mit Windows PowerShell und PowerShell Core kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="e05f7-159">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="e05f7-160">`Core` bedeutet nicht automatisch, dass das Modul mit Windows, Linux und macOS kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="e05f7-160">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="e05f7-161">Die **CompatiblePSEditions**-Eigenschaft wurde in PowerShell v5 eingeführt.</span><span class="sxs-lookup"><span data-stu-id="e05f7-161">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="e05f7-162">Bei Modulmanifesten, die die **CompatiblePSEditions**-Eigenschaft verwenden, tritt in Versionen vor PowerShell v5 beim Laden ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="e05f7-162">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="e05f7-163">Angeben der Betriebssystemkompatibilität</span><span class="sxs-lookup"><span data-stu-id="e05f7-163">Indicating OS Compatibility</span></span>

<span data-ttu-id="e05f7-164">Überprüfen Sie zunächst, ob Ihr Modul unter Linux und macOS funktioniert.</span><span class="sxs-lookup"><span data-stu-id="e05f7-164">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="e05f7-165">Geben Sie als Nächstes die Kompatibilität mit diesen Betriebssystemen im Modulmanifest an.</span><span class="sxs-lookup"><span data-stu-id="e05f7-165">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="e05f7-166">Dies erleichtert den Benutzern, die mit ihren Betriebssystemen kompatiblen Versionen Ihres Moduls zu finden, wenn es im [PowerShell Gallery][] veröffentlicht wird.</span><span class="sxs-lookup"><span data-stu-id="e05f7-166">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="e05f7-167">Im Modulmanifest hat die `PrivateData`-Eigenschaft eine `PSData`-Untereigenschaft.</span><span class="sxs-lookup"><span data-stu-id="e05f7-167">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="e05f7-168">Die optionale `Tags`-Eigenschaft von `PSData` akzeptiert ein Array von Werten, die im PowerShell-Katalog angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e05f7-168">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="e05f7-169">Der PowerShell-Katalog unterstützt die folgenden Kompatibilitätswerte:</span><span class="sxs-lookup"><span data-stu-id="e05f7-169">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="e05f7-170">Tag</span><span class="sxs-lookup"><span data-stu-id="e05f7-170">Tag</span></span>               | <span data-ttu-id="e05f7-171">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e05f7-171">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="e05f7-172">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="e05f7-172">PSEdition_Core</span></span>    | <span data-ttu-id="e05f7-173">Kompatibel mit PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="e05f7-173">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="e05f7-174">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="e05f7-174">PSEdition_Desktop</span></span> | <span data-ttu-id="e05f7-175">Kompatibel mit Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e05f7-175">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="e05f7-176">Windows</span><span class="sxs-lookup"><span data-stu-id="e05f7-176">Windows</span></span>           | <span data-ttu-id="e05f7-177">Kompatibel mit Windows</span><span class="sxs-lookup"><span data-stu-id="e05f7-177">Compatible with Windows</span></span>                    |
| <span data-ttu-id="e05f7-178">Linux</span><span class="sxs-lookup"><span data-stu-id="e05f7-178">Linux</span></span>             | <span data-ttu-id="e05f7-179">Kompatibel mit Linux (keine spezifische Distribution)</span><span class="sxs-lookup"><span data-stu-id="e05f7-179">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="e05f7-180">macOS</span><span class="sxs-lookup"><span data-stu-id="e05f7-180">macOS</span></span>             | <span data-ttu-id="e05f7-181">Kompatibel mit macOS</span><span class="sxs-lookup"><span data-stu-id="e05f7-181">Compatible with macOS</span></span>                      |

<span data-ttu-id="e05f7-182">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="e05f7-182">Example:</span></span>

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
[Runtimeüberprüfungen]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[runtime checks]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
