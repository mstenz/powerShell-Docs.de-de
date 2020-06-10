---
title: Erstellen eines binären Standardbibliotheksmoduls
description: Die PowerShell-Standardbibliothek ermöglicht uns, plattformübergreifende Module zu erstellen, die sowohl mit PowerShell Core als auch mit Windows PowerShell 5.1 funktionieren.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 51734fd9232e7c33b11c6c5a6abddbcc1f28413c
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149413"
---
# <a name="how-to-create-a-standard-library-binary-module"></a><span data-ttu-id="a93f3-103">Erstellen eines binären Standardbibliotheksmoduls</span><span class="sxs-lookup"><span data-stu-id="a93f3-103">How to create a Standard Library binary module</span></span>

<span data-ttu-id="a93f3-104">Vor Kurzem hatte ich eine Idee für ein Modul, das ich als binäres Modul implementieren wollte.</span><span class="sxs-lookup"><span data-stu-id="a93f3-104">I recently had an idea for module that I wanted to implement as a binary module.</span></span> <span data-ttu-id="a93f3-105">Ich habe noch keines mithilfe der [PowerShell-Standardbibliothek][] erstellt, weshalb ich dies als gute Gelegenheit empfand.</span><span class="sxs-lookup"><span data-stu-id="a93f3-105">I have yet to create one using the [PowerShell Standard Library][] so this felt like a good opportunity.</span></span> <span data-ttu-id="a93f3-106">Ich habe die Anleitung zum [Erstellen eines plattformübergreifenden binären Moduls][] befolgt und konnte dieses Modul ohne jegliche Schwierigkeiten erstellen.</span><span class="sxs-lookup"><span data-stu-id="a93f3-106">I used the [Creating a cross-platform binary module][] guide to create this module without any roadblocks.</span></span>
<span data-ttu-id="a93f3-107">Wir werden den gleichen Prozess durchlaufen, wobei ich zwischendurch noch den einen oder anderen zusätzlichen Kommentar hinzufügen werde.</span><span class="sxs-lookup"><span data-stu-id="a93f3-107">We're going to walk that same process and I'll add a little extra commentary along the way.</span></span>

> [!NOTE]
> <span data-ttu-id="a93f3-108">Die [Originalversion][] dieses Artikels ist im Blog von [@KevinMarquette][] erschienen.</span><span class="sxs-lookup"><span data-stu-id="a93f3-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="a93f3-109">Das PowerShell-Team dankt Kevin Marquette, dass er diesen Inhalt mit uns teilt.</span><span class="sxs-lookup"><span data-stu-id="a93f3-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="a93f3-110">Weitere Informationen finden Sie in seinem Blog auf [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="a93f3-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="what-is-the-powershell-standard-library"></a><span data-ttu-id="a93f3-111">Was ist die PowerShell-Standardbibliothek?</span><span class="sxs-lookup"><span data-stu-id="a93f3-111">What is the PowerShell Standard Library?</span></span>

<span data-ttu-id="a93f3-112">Die PowerShell-Standardbibliothek ermöglicht uns, plattformübergreifende Module zu erstellen, die sowohl mit PowerShell Core als auch mit Windows PowerShell 5.1 (oder 3.0) funktionieren.</span><span class="sxs-lookup"><span data-stu-id="a93f3-112">The PowerShell Standard Library allows us to create cross platform modules that work in both PowerShell Core and with Windows PowerShell 5.1 (or 3.0).</span></span>

## <a name="planning-our-module"></a><span data-ttu-id="a93f3-113">Planen des Moduls</span><span class="sxs-lookup"><span data-stu-id="a93f3-113">Planning our module</span></span>

<span data-ttu-id="a93f3-114">Der Plan für dieses Modul sieht vor, den Ordner `src` für den C#-Code anzulegen und den Rest wie für ein Skriptmodul zu strukturieren.</span><span class="sxs-lookup"><span data-stu-id="a93f3-114">The plan for this module is to create a `src` folder for the C# code and structure the rest like I would for a script module.</span></span> <span data-ttu-id="a93f3-115">Dazu gehört die Nutzung eines Buildskripts, um alles in den Ordner `output` zu kompilieren.</span><span class="sxs-lookup"><span data-stu-id="a93f3-115">This includes using a build script to compile everything into an `output` folder.</span></span> <span data-ttu-id="a93f3-116">Die Ordnerstruktur sieht folgendermaßen aus:</span><span class="sxs-lookup"><span data-stu-id="a93f3-116">The folder structure looks like this:</span></span>

```
MyModule
├───src
├───Output
│   └───MyModule
├───MyModule
│   ├───Data
│   ├───Private
│   └───Public
└───Tests
```

## <a name="getting-started"></a><span data-ttu-id="a93f3-117">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="a93f3-117">Getting Started</span></span>

<span data-ttu-id="a93f3-118">Normalerweise arbeite ich mit einer Plaster-Vorlage, aber meine aktuelle bietet noch keine Unterstützung binärer Module.</span><span class="sxs-lookup"><span data-stu-id="a93f3-118">I normally use a Plaster template but my current template doesn't have any binary module support yet.</span></span> <span data-ttu-id="a93f3-119">Das macht aber nichts.</span><span class="sxs-lookup"><span data-stu-id="a93f3-119">Not a big deal.</span></span> <span data-ttu-id="a93f3-120">Dieses Mal werde ich sie von Hand erstellen.</span><span class="sxs-lookup"><span data-stu-id="a93f3-120">I'll create this one by hand this time.</span></span>

<span data-ttu-id="a93f3-121">Zuerst muss ich den Ordner und das Git-Repository erstellen.</span><span class="sxs-lookup"><span data-stu-id="a93f3-121">First I need to create the folder and create the git repo.</span></span> <span data-ttu-id="a93f3-122">Ich verwende `$module` als Platzhalter für den Modulnamen.</span><span class="sxs-lookup"><span data-stu-id="a93f3-122">I'm using `$module` as a placeholder for the module name.</span></span> <span data-ttu-id="a93f3-123">Dies erleichtert Ihnen, diese Beispiele bei Bedarf wiederzuverwenden.</span><span class="sxs-lookup"><span data-stu-id="a93f3-123">This should make it easier for you to reuse these examples if needed.</span></span>

```powershell
$module = 'MyModule'
New-Item -Path $module -Type Directory
Set-Location $module
git init
```

<span data-ttu-id="a93f3-124">Dann werden die Ordner auf Stammebene erstellt.</span><span class="sxs-lookup"><span data-stu-id="a93f3-124">Then create the root level folders.</span></span>

```powershell
New-Item -Path 'src' -Type Directory
New-Item -Path 'Output' -Type Directory
New-Item -Path 'Tests' -Type Directory
New-Item -Path $module -Type Directory
```

### <a name="binary-module-setup"></a><span data-ttu-id="a93f3-125">Einrichtung des binären Moduls</span><span class="sxs-lookup"><span data-stu-id="a93f3-125">Binary module setup</span></span>

<span data-ttu-id="a93f3-126">In diesem Artikel konzentrieren wir uns auf das binäre Modul, womit wir auch beginnen wollen.</span><span class="sxs-lookup"><span data-stu-id="a93f3-126">This article os focused on the binary module so that is where we'll start.</span></span> <span data-ttu-id="a93f3-127">In diesem Abschnitt werden Beispiele der Anleitung zum [Erstellen eines plattformübergreifenden binären Moduls][] entnommen.</span><span class="sxs-lookup"><span data-stu-id="a93f3-127">This section pulls examples from the [Creating a cross-platform binary module][] guide.</span></span> <span data-ttu-id="a93f3-128">Lesen Sie diese Anleitung, wenn Sie weitere Einzelheiten benötigen oder Probleme haben.</span><span class="sxs-lookup"><span data-stu-id="a93f3-128">Review that guide if you need more details or have any issues.</span></span>

<span data-ttu-id="a93f3-129">Als Erstes überprüfen wir die installierte Version des [.NET Core SDK][].</span><span class="sxs-lookup"><span data-stu-id="a93f3-129">First thing we want to do is check the version of the [dotnet core SDK][] that we installed.</span></span> <span data-ttu-id="a93f3-130">Ich nutze 2.1.4, aber Sie sollten mindestens 2.0.0 haben, ehe Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="a93f3-130">I'm using 2.1.4, but you should have 2.0.0 or newer before continuing.</span></span>

```powershell
PS> dotnet --version
2.1.4
```

<span data-ttu-id="a93f3-131">In diesem Abschnitt arbeite ich mit dem Inhalt des Ordners `src`.</span><span class="sxs-lookup"><span data-stu-id="a93f3-131">I'm working out of the `src` folder for this section.</span></span>

```powershell
Set-Location 'src'
```

<span data-ttu-id="a93f3-132">Erstellen Sie mit dem Befehl dotnet eine neue Klassenbibliothek.</span><span class="sxs-lookup"><span data-stu-id="a93f3-132">Using the dotnet command, create a new class library.</span></span>

```powershell
dotnet new classlib --name $module
```

<span data-ttu-id="a93f3-133">Dadurch wird das Bibliotheksprojekt in einem Unterordner erstellt, aber ich möchte diese zusätzliche Schachtelungsebene nicht.</span><span class="sxs-lookup"><span data-stu-id="a93f3-133">This created the library project in a subfolder but I don't want that extra level of nesting.</span></span> <span data-ttu-id="a93f3-134">Ich verschiebe diese Dateien deshalb um eine Ebene nach oben.</span><span class="sxs-lookup"><span data-stu-id="a93f3-134">I'm going to move those files up a level.</span></span>

```powershell
Move-Item -Path .\$module\* -Destination .\
Remove-Item $module -Recurse
```

<span data-ttu-id="a93f3-135">Legen Sie die .NET Core SDK-Version für das Projekt fest.</span><span class="sxs-lookup"><span data-stu-id="a93f3-135">Set the .NET core SDK version for the project.</span></span> <span data-ttu-id="a93f3-136">Ich arbeite mit dem SDK 2.1, weshalb ich 2.1.0 angebe.</span><span class="sxs-lookup"><span data-stu-id="a93f3-136">I have the 2.1 SDK so I'm going to specify 2.1.0.</span></span>
<span data-ttu-id="a93f3-137">Geben Sie 2.0.0 an, wenn Sie das SDK 2.0 verwenden.</span><span class="sxs-lookup"><span data-stu-id="a93f3-137">Use 2.0.0 if you're using the 2.0 SDK.</span></span>

```powershell
dotnet new globaljson --sdk-version 2.1.0
```

<span data-ttu-id="a93f3-138">Fügen Sie dem Projekt das NuGet-Paket [NuGet-Paket][] hinzu.</span><span class="sxs-lookup"><span data-stu-id="a93f3-138">Add the PowerShell Standard Library [NuGet package][] to the project.</span></span> <span data-ttu-id="a93f3-139">Vergewissern Sie sich, dass Sie die neueste verfügbare Version für den benötigten Kompatibilitätsgrad nutzen.</span><span class="sxs-lookup"><span data-stu-id="a93f3-139">Make sure you use the most recent version available for the level of compatibility that you need.</span></span> <span data-ttu-id="a93f3-140">Ich würde standardmäßig die neueste Version einsetzen, aber ich glaube nicht, dass in diesem Modul neuere Features als die von PowerShell 3.0 genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="a93f3-140">I would default to the latest version but I don't think this module leverages any features newer than PowerShell 3.0.</span></span>

```powershell
dotnet add package PowerShellStandard.Library --version 7.0.0-preview.1
```

<span data-ttu-id="a93f3-141">Unser Ordner „src“ sieht dann wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="a93f3-141">We should have a src folder that looks like this:</span></span>

```powershell
PS> Get-ChildItem
    Directory: \MyModule\src

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        7/14/2018   9:51 PM                obj
-a----        7/14/2018   9:51 PM             86 Class1.cs
-a----        7/14/2018  10:03 PM            259 MyModule.csproj
-a----        7/14/2018  10:05 PM             45 global.json
```

<span data-ttu-id="a93f3-142">Nun können wir dem Projekt unseren eigenen Code hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a93f3-142">Now we're ready to add our own code to the project.</span></span>

### <a name="building-a-binary-cmdlet"></a><span data-ttu-id="a93f3-143">Erstellen eines binären Cmdlets</span><span class="sxs-lookup"><span data-stu-id="a93f3-143">Building a binary cmdlet</span></span>

<span data-ttu-id="a93f3-144">Wir müssen die Datei `src\Class1.cs` so aktualisieren, dass sie dieses Start-Cmdlet enthält:</span><span class="sxs-lookup"><span data-stu-id="a93f3-144">We need to update the `src\Class1.cs` to contain this starter cmdlet:</span></span>

```csharp
using System;
using System.Management.Automation;

namespace MyModule
{
    [Cmdlet( VerbsDiagnostic.Resolve , "MyCmdlet")]
    public class ResolveMyCmdletCommand : PSCmdlet
    {
        [Parameter(Position=0)]
        public Object InputObject { get; set; }

        protected override void EndProcessing()
        {
            this.WriteObject(this.InputObject);
            base.EndProcessing();
        }
    }
}
```

<span data-ttu-id="a93f3-145">Benennen Sie die Datei entsprechend dem Klassennamen um.</span><span class="sxs-lookup"><span data-stu-id="a93f3-145">Rename the file to match the class name.</span></span>

```powershell
Rename-Item .\Class1.cs .\ResolveMyCmdletCommand.cs
```

<span data-ttu-id="a93f3-146">Anschließend können wir unser Modul erstellen.</span><span class="sxs-lookup"><span data-stu-id="a93f3-146">Then we can build our module.</span></span>

```powershell
PS> dotnet build

Microsoft (R) Build Engine version 15.5.180.51428 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

Restore completed in 18.19 ms for C:\workspace\MyModule\src\MyModule.csproj.
MyModule -> C:\workspace\MyModule\src\bin\Debug\netstandard2.0\MyModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:02.19
```

<span data-ttu-id="a93f3-147">Wir können `Import-Module` in der neuen DLL aufrufen, um unser neues Cmdlet zu laden.</span><span class="sxs-lookup"><span data-stu-id="a93f3-147">We can call `Import-Module` on the new dll to load our new CMDlet.</span></span>

```powershell
PS> Import-Module .\bin\Debug\netstandard2.0\$module.dll
PS> Get-Command -Module $module

CommandType Name                    Version Source
----------- ----                    ------- ------
Cmdlet      Resolve-MyCmdlet        1.0.0.0 MyModule
```

<span data-ttu-id="a93f3-148">Falls der Import auf Ihrem System fehlschlägt, versuchen Sie, .NET auf mindestens 4.7.1 zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="a93f3-148">If the import fails on your system, try updating .NET to 4.7.1 or newer.</span></span> <span data-ttu-id="a93f3-149">In der Anleitung zum [Erstellen eines plattformübergreifenden binären Moduls][] wird ausführlicher auf .NET-Unterstützung und Kompatibilität mit älteren .NET-Versionen eingegangen.</span><span class="sxs-lookup"><span data-stu-id="a93f3-149">The [Creating a cross-platform binary module][] guide goes into more details on .NET support and compatibility for older versions of .NET.</span></span>

### <a name="module-manifest"></a><span data-ttu-id="a93f3-150">Modulmanifest</span><span class="sxs-lookup"><span data-stu-id="a93f3-150">Module manifest</span></span>

<span data-ttu-id="a93f3-151">Es ist cool, dass wir die DLL importieren können und ein funktionierendes Modul haben.</span><span class="sxs-lookup"><span data-stu-id="a93f3-151">It's cool that we can import the dll and have a working module.</span></span> <span data-ttu-id="a93f3-152">Ich möchte damit weitermachen und ein Modulmanifest erstellen.</span><span class="sxs-lookup"><span data-stu-id="a93f3-152">I like to keep going with it and create a module manifest.</span></span> <span data-ttu-id="a93f3-153">Wir brauchen das Manifest, wenn wir es später in der PSGallery veröffentlichen möchten.</span><span class="sxs-lookup"><span data-stu-id="a93f3-153">We need the manifest if we want to publish to the PSGallery later.</span></span>

<span data-ttu-id="a93f3-154">Im Stammverzeichnis des Projekts können wir diesen Befehl ausführen, um das benötigte Modulmanifest zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a93f3-154">From the root of our project, we can run this command to create the module manifest that we need.</span></span>

```powershell
$manifestSplat = @{
    Path              = ".\$module\$module.psd1"
    Author            = 'Kevin Marquette'
    NestedModules     = @('bin\MyModule.dll')
    RootModule        = "$module.psm1"
    FunctionsToExport = @('Resolve-MyCmdlet')
}
New-ModuleManifest @manifestSplat
```

<span data-ttu-id="a93f3-155">Ich werde außerdem ein leeres Stammmodul für künftige PowerShell-Funktionen erstellen.</span><span class="sxs-lookup"><span data-stu-id="a93f3-155">I'm also going to create an empty root module for future PowerShell functions.</span></span>

```powershell
Set-Content -Value '' -Path ".\$module\$module.psm1"
```

<span data-ttu-id="a93f3-156">Dadurch kann ich sowohl normale PowerShell-Funktionen als auch binäre Cmdlets im selben Projekt kombinieren.</span><span class="sxs-lookup"><span data-stu-id="a93f3-156">This allows me to mix both normal PowerShell functions and binary Cmdlets in the same project.</span></span>

### <a name="building-the-full-module"></a><span data-ttu-id="a93f3-157">Erstellen des vollständigen Moduls</span><span class="sxs-lookup"><span data-stu-id="a93f3-157">Building the full module</span></span>

<span data-ttu-id="a93f3-158">Ich kompiliere alles zusammen in einem Ordner namens „Output“.</span><span class="sxs-lookup"><span data-stu-id="a93f3-158">I compile everything together into an output folder.</span></span> <span data-ttu-id="a93f3-159">Hierfür muss ein Buildskript erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="a93f3-159">We need to create a build script to do that.</span></span> <span data-ttu-id="a93f3-160">Normalerweise würde ich dies einem `Invoke-Build`-Skript hinzufügen, aber für dieses Beispiel halten wir es einfach.</span><span class="sxs-lookup"><span data-stu-id="a93f3-160">I would normally add this to an `Invoke-Build` script, but we can keep it simple for this example.</span></span> <span data-ttu-id="a93f3-161">Fügen Sie dies zur Datei `build.ps1` im Stammverzeichnis des Projekts hinzu.</span><span class="sxs-lookup"><span data-stu-id="a93f3-161">Add this to a `build.ps1` at the root of the project.</span></span>

```powershell
$module = 'MyModule'
Push-Location $PSScriptRoot

dotnet build $PSScriptRoot\src -o $PSScriptRoot\output\$module\bin
Copy-Item "$PSScriptRoot\$module\*" "$PSScriptRoot\output\$module" -Recurse -Force

Import-Module "$PSScriptRoot\Output\$module\$module.psd1"
Invoke-Pester "$PSScriptRoot\Tests"
```

<span data-ttu-id="a93f3-162">Mit diesen Befehlen erstellen wir unsere DLL und legen sie in unserem Ordner `output\$module\bin` ab.</span><span class="sxs-lookup"><span data-stu-id="a93f3-162">These commands build our DLL and place it into our `output\$module\bin` folder.</span></span> <span data-ttu-id="a93f3-163">Anschließend werden die anderen Moduldateien an die passende Stelle kopiert.</span><span class="sxs-lookup"><span data-stu-id="a93f3-163">It then copies the other module files into place.</span></span>

```
Output
└───MyModule
    │   MyModule.psd1
    │   MyModule.psm1
    │
    └───bin
            MyModule.deps.json
            MyModule.dll
            MyModule.pdb
```

<span data-ttu-id="a93f3-164">An diesem Punkt können wir das Modul mit der PSD1-Datei importieren.</span><span class="sxs-lookup"><span data-stu-id="a93f3-164">At this point, we can import our module with the psd1 file.</span></span>

```powershell
Import-Module ".\Output\$module\$module.psd1"
```

<span data-ttu-id="a93f3-165">Von hier aus können wir den Ordner `.\Output\$module` in unserem Verzeichnis `$env:PSModulePath` ablegen. Unser Befehl wird anschließend nach Bedarf automatisch geladen.</span><span class="sxs-lookup"><span data-stu-id="a93f3-165">From here, we can drop the `.\Output\$module` folder into our `$env:PSModulePath` directory and it autoloads our command whenever we need it.</span></span>

### <a name="update-dotnet-new-psmodule"></a><span data-ttu-id="a93f3-166">Update: neue Vorlage für PSModule im Befehl dotnet</span><span class="sxs-lookup"><span data-stu-id="a93f3-166">Update: dotnet new PSModule</span></span>

<span data-ttu-id="a93f3-167">Ich habe erfahren, dass das Tool `dotnet` die Vorlage `PSModule` enthält.</span><span class="sxs-lookup"><span data-stu-id="a93f3-167">I learned that the `dotnet` tool has a `PSModule` template.</span></span>

<span data-ttu-id="a93f3-168">Alle von mir beschriebenen Schritte sind immer noch gültig, aber diese Vorlage macht viele davon überflüssig. Es handelt sich nach wie vor um eine ziemlich neue Vorlage, die noch weiter aufpoliert wird.</span><span class="sxs-lookup"><span data-stu-id="a93f3-168">All the steps that I outlined above are still valid, but this template cuts many pf them out. It's still a fairly new template that is still getting some polish placed on it.</span></span> <span data-ttu-id="a93f3-169">Gehen Sie davon aus, dass sie immer besser wird.</span><span class="sxs-lookup"><span data-stu-id="a93f3-169">Expect it to keep getting better from here.</span></span>

<span data-ttu-id="a93f3-170">Die Vorlage PSModule wird folgendermaßen installiert und eingesetzt.</span><span class="sxs-lookup"><span data-stu-id="a93f3-170">This is how you use install and use the PSModule template.</span></span>

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
dotnet new psmodule
dotnet build
Import-Module "bin\Debug\netstandard2.0\$module.dll"
Get-Module $module
```

<span data-ttu-id="a93f3-171">Diese einfache Vorlage kümmert sich um das Hinzufügen des .NET SDK und der PowerShell-Standardbibliothek und erstellt eine Beispielklasse im Projekt.</span><span class="sxs-lookup"><span data-stu-id="a93f3-171">This minimally-viable template takes care of adding the .NET SDK, PowerShell Standard Library, and creates an example class in the project.</span></span> <span data-ttu-id="a93f3-172">Sie können sie unmittelbar erstellen und ausführen.</span><span class="sxs-lookup"><span data-stu-id="a93f3-172">You can build it and run it right away.</span></span>

## <a name="important-details"></a><span data-ttu-id="a93f3-173">Wichtige Details</span><span class="sxs-lookup"><span data-stu-id="a93f3-173">Important details</span></span>

<span data-ttu-id="a93f3-174">Bevor wir diesen Artikel abschließen, sollen noch ein paar weitere erwähnenswerte Details genannt werden.</span><span class="sxs-lookup"><span data-stu-id="a93f3-174">Before we end this article, here are a few other details worth mentioning.</span></span>

### <a name="unloading-dlls"></a><span data-ttu-id="a93f3-175">Entladen von DLLs</span><span class="sxs-lookup"><span data-stu-id="a93f3-175">Unloading DLLs</span></span>

<span data-ttu-id="a93f3-176">Sobald ein binäres Modul geladen wurde, kann es nicht mehr wirklich entladen werden.</span><span class="sxs-lookup"><span data-stu-id="a93f3-176">Once a binary module is loaded, you can't really unload it.</span></span> <span data-ttu-id="a93f3-177">Die DLL-Datei ist gesperrt, bis Sie sie entladen.</span><span class="sxs-lookup"><span data-stu-id="a93f3-177">The DLL file is locked until you unload it.</span></span> <span data-ttu-id="a93f3-178">Dies kann beim Entwickeln nervig sein, denn jedes Mal, wenn Sie eine Änderung vornehmen und diese umsetzen möchten, ist die Datei oftmals gesperrt.</span><span class="sxs-lookup"><span data-stu-id="a93f3-178">This can be annoying when developing because every time you make a change and want to build it, the file is often locked.</span></span> <span data-ttu-id="a93f3-179">Die einzige zuverlässige Möglichkeit zur Lösung dieses Problems besteht darin, die PowerShell-Sitzung zu schließen, die die DLL geladen hat.</span><span class="sxs-lookup"><span data-stu-id="a93f3-179">The only reliable way to resolve this is to close the PowerShell session that loaded the DLL.</span></span>

### <a name="vs-code-reload-window-action"></a><span data-ttu-id="a93f3-180">VS Code-Aktion „Fenster erneut laden“</span><span class="sxs-lookup"><span data-stu-id="a93f3-180">VS Code reload window action</span></span>

<span data-ttu-id="a93f3-181">Ich erledige den größten Teil meiner PowerShell-Entwicklungsarbeit in [VS Code][].</span><span class="sxs-lookup"><span data-stu-id="a93f3-181">I do most of my PowerShell dev work in [VS Code][].</span></span> <span data-ttu-id="a93f3-182">Wenn ich an einem binären Modul (oder einem Modul mit Klassen) arbeite, habe ich mir angewöhnt, VS Code jedes Mal neu zu laden, wenn ich einen Build erstelle.</span><span class="sxs-lookup"><span data-stu-id="a93f3-182">When I'm working on a binary module (or a module with classes), I've gotten into the habit of reloading VS Code every time I build.</span></span>
<span data-ttu-id="a93f3-183">Über <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd> wird das Befehlsfenster geöffnet, und `Reload Window` steht in meiner Liste immer ganz oben.</span><span class="sxs-lookup"><span data-stu-id="a93f3-183"><kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> pops the command window and `Reload Window` is always at the top of my list.</span></span>

### <a name="nested-powershell-sessions"></a><span data-ttu-id="a93f3-184">Geschachtelte PowerShell-Sitzungen</span><span class="sxs-lookup"><span data-stu-id="a93f3-184">Nested PowerShell sessions</span></span>

<span data-ttu-id="a93f3-185">Eine andere Möglichkeit ist eine gute Testabdeckung durch Pester.</span><span class="sxs-lookup"><span data-stu-id="a93f3-185">One other option is to have good Pester test coverage.</span></span> <span data-ttu-id="a93f3-186">Dann können Sie das Skript „build.ps1“ so anpassen, dass es eine neue PowerShell-Sitzung startet, den Build durchführt, die Tests ausführt und die Sitzung schließt.</span><span class="sxs-lookup"><span data-stu-id="a93f3-186">Then you can adjust the build.ps1 script to start a new PowerShell session, perform the build, run the tests, and close the session.</span></span>

### <a name="updating-installed-modules"></a><span data-ttu-id="a93f3-187">Aktualisieren installierter Module</span><span class="sxs-lookup"><span data-stu-id="a93f3-187">Updating installed modules</span></span>

<span data-ttu-id="a93f3-188">Diese Sperre kann lästig sein, wenn Sie versuchen, Ihr lokal installiertes Modul zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="a93f3-188">This locking can be annoying when trying to update your locally installed module.</span></span> <span data-ttu-id="a93f3-189">Wenn es in einer Sitzung geladen ist, müssen Sie es aufspüren und schließen.</span><span class="sxs-lookup"><span data-stu-id="a93f3-189">If any session has it loaded, you have to go hunt it down and close it.</span></span> <span data-ttu-id="a93f3-190">Dies ist weniger problematisch, wenn die Installation über eine PSGallery erfolgt, da die Modulversionsverwaltung die neue Version in einem anderen Ordner ablegt.</span><span class="sxs-lookup"><span data-stu-id="a93f3-190">This is less of an issue when installing from a PSGallery because module versioning places the new one in a different folder.</span></span>

<span data-ttu-id="a93f3-191">Sie können eine lokale PSGallery einrichten und diese als Teil Ihres Builds veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="a93f3-191">You can set up a local PSGallery and publish to that as part of your build.</span></span> <span data-ttu-id="a93f3-192">Anschließend führen Sie Ihre lokale Installation über diese PSGallery durch.</span><span class="sxs-lookup"><span data-stu-id="a93f3-192">Then do your local install from that PSGallery.</span></span> <span data-ttu-id="a93f3-193">Das klingt nach einer Menge Arbeit, kann aber so einfach sein wie das Starten eines Docker-Containers.</span><span class="sxs-lookup"><span data-stu-id="a93f3-193">This sounds like a lot of work, but this can be as simple as starting a docker container.</span></span> <span data-ttu-id="a93f3-194">Eine Möglichkeit dazu beschreibe ich in meinem Beitrag zum [Verwenden eines NuGet-Servers für ein PSRepository][].</span><span class="sxs-lookup"><span data-stu-id="a93f3-194">I cover a way to do that in my post on [Using a NuGet server for a PSRepository][].</span></span>

## <a name="why-binary-modules"></a><span data-ttu-id="a93f3-195">Gründe für binäre Module</span><span class="sxs-lookup"><span data-stu-id="a93f3-195">Why binary modules?</span></span>

<span data-ttu-id="a93f3-196">Ich habe mich sofort an die Erstellung eines binären Moduls gemacht, ohne auf die Gründe dafür einzugehen.</span><span class="sxs-lookup"><span data-stu-id="a93f3-196">I jumped right into how to make a binary module and didn't mention why you want to make one.</span></span> <span data-ttu-id="a93f3-197">In Wirklichkeit schreiben Sie C#-Code und geben den einfachen Zugriff auf PowerShell-Cmdlets und -Funktionen auf.</span><span class="sxs-lookup"><span data-stu-id="a93f3-197">In reality, you are writing C# and give up easy access to PowerShell Cmdlets and functions.</span></span> <span data-ttu-id="a93f3-198">Das ist der Hauptgrund, warum ich nicht schon früher zu binären Modulen übergegangen bin.</span><span class="sxs-lookup"><span data-stu-id="a93f3-198">That is the main reason why I have not shifted to binary modules sooner.</span></span>

<span data-ttu-id="a93f3-199">Doch wenn Sie ein Modul erstellen, das nicht von vielen anderen PowerShell-Befehlen abhängig ist, kann der Leistungszuwachs erheblich sein.</span><span class="sxs-lookup"><span data-stu-id="a93f3-199">But if you are creating a module that doesn't depend on a lot of other PowerShell commands, the performance benefit can be significant.</span></span> <span data-ttu-id="a93f3-200">Durch den Umstieg auf C# können Sie den von PowerShell hinzugefügten Zusatzaufwand vermeiden.</span><span class="sxs-lookup"><span data-stu-id="a93f3-200">By dropping into C#, you get to shed the overhead added by PowerShell.</span></span> <span data-ttu-id="a93f3-201">PowerShell wurde für Administratoren und nicht für den Computer optimiert, was ein wenig mehr Aufwand bedeutet.</span><span class="sxs-lookup"><span data-stu-id="a93f3-201">PowerShell was optimized for the administrator, not the computer, and that adds a little overhead.</span></span>

<span data-ttu-id="a93f3-202">Bei der Arbeit haben wir einen kritischen Prozess, der viele Aufgaben mithilfe von JSON und Hashtabellen erledigt.</span><span class="sxs-lookup"><span data-stu-id="a93f3-202">At work, we have a critical process that does a lot of work with JSON and Hashtables.</span></span> <span data-ttu-id="a93f3-203">Wir haben PowerShell nach Kräften optimiert, aber dieser Prozess dauerte immer noch 12 Minuten.</span><span class="sxs-lookup"><span data-stu-id="a93f3-203">We optimized the PowerShell as much as we could but this process was still running for 12 minutes.</span></span> <span data-ttu-id="a93f3-204">Das Modul enthielt bereits eine Menge PowerShell im C#-Stil.</span><span class="sxs-lookup"><span data-stu-id="a93f3-204">The module already contained a lot of C# style PowerShell.</span></span> <span data-ttu-id="a93f3-205">Dadurch wurde eine einfache und schnelle Umwandlung in ein binäres Modul möglich.</span><span class="sxs-lookup"><span data-stu-id="a93f3-205">This made the conversion to a binary module clean and easy to do.</span></span> <span data-ttu-id="a93f3-206">Durch diese Umwandlung konnte dieser Prozess von über 12 auf unter vier Minuten verkürzt werden.</span><span class="sxs-lookup"><span data-stu-id="a93f3-206">Our conversion cut that process down from over 12 minutes to under four minutes.</span></span>

### <a name="hybrid-modules"></a><span data-ttu-id="a93f3-207">Hybridmodule</span><span class="sxs-lookup"><span data-stu-id="a93f3-207">Hybrid modules</span></span>

<span data-ttu-id="a93f3-208">Sie können binäre Cmdlets mit erweiterten PowerShell-Funktionen kombinieren.</span><span class="sxs-lookup"><span data-stu-id="a93f3-208">You can mix binary Cmdlets with PowerShell advanced functions.</span></span> <span data-ttu-id="a93f3-209">Das ist genau das, was ich in dieser Anleitung mache.</span><span class="sxs-lookup"><span data-stu-id="a93f3-209">That is exactly what I'm doing in this guide.</span></span> <span data-ttu-id="a93f3-210">Sie können alles, was Sie über Skriptmodule wissen, übernehmen, wobei alles in gleicher Weise zutrifft.</span><span class="sxs-lookup"><span data-stu-id="a93f3-210">You can take everything you know about script modules and it all applies the same way.</span></span>
<span data-ttu-id="a93f3-211">Die leere Datei `psm1`, die ich heute erstellt habe, ist nur dazu da, damit Sie später andere PowerShell-Funktionen einfügen können.</span><span class="sxs-lookup"><span data-stu-id="a93f3-211">The empty `psm1` file that I created today is there just so you can drop in other PowerShell functions later.</span></span>

<span data-ttu-id="a93f3-212">Nahezu alle kompilierten Cmdlets, die wir erstellt haben, waren anfangs eine PowerShell-Funktion.</span><span class="sxs-lookup"><span data-stu-id="a93f3-212">Almost all of the compiled cmdlets that we created started out as a PowerShell function first.</span></span> <span data-ttu-id="a93f3-213">Alle unsere Binärmodule sind eigentlich Hybridmodule.</span><span class="sxs-lookup"><span data-stu-id="a93f3-213">All of our binary modules are really hybrid modules.</span></span>

### <a name="build-scripts"></a><span data-ttu-id="a93f3-214">Buildskripts</span><span class="sxs-lookup"><span data-stu-id="a93f3-214">Build scripts</span></span>

<span data-ttu-id="a93f3-215">Ich habe das Buildskript hier einfach gehalten.</span><span class="sxs-lookup"><span data-stu-id="a93f3-215">I kept the build script simple here.</span></span> <span data-ttu-id="a93f3-216">Im Allgemeinen nutze ich ein großes `Invoke-Build`-Skript als Teil meiner CI/CD-Pipeline.</span><span class="sxs-lookup"><span data-stu-id="a93f3-216">I generally use a large `Invoke-Build` script as part of my CI/CD pipeline.</span></span> <span data-ttu-id="a93f3-217">Es leistet mehr als das Ausführen von Pester-Tests und PSScriptAnalyzer, die Versionsverwaltung und die Veröffentlichung in der PSGallery.</span><span class="sxs-lookup"><span data-stu-id="a93f3-217">It does more magic like running Pester tests, running PSScriptAnalyzer, managing versioning, and publishing to the PSGallery.</span></span> <span data-ttu-id="a93f3-218">Nachdem ich angefangen hatte, ein Buildskript für meine Module zu nutzen, konnte ich viele Dinge finden, die ich ihm hinzufügen konnte.</span><span class="sxs-lookup"><span data-stu-id="a93f3-218">Once I started using a build script for my modules, I was able to find lots of things to add to it.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="a93f3-219">Schlussbemerkungen</span><span class="sxs-lookup"><span data-stu-id="a93f3-219">Final thoughts</span></span>

<span data-ttu-id="a93f3-220">Binäre Module können einfach erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="a93f3-220">Binary modules are easy to create.</span></span> <span data-ttu-id="a93f3-221">Ich habe die C#-Syntax zum Erstellen eines Cmdlets nicht angeschnitten, aber es gibt im [Windows PowerShell SDK][] reichlich Dokumentation dazu.</span><span class="sxs-lookup"><span data-stu-id="a93f3-221">I didn't touch on the C# syntax for creating a Cmdlet, but there is plenty of documentation on it in the [Windows PowerShell SDK][].</span></span> <span data-ttu-id="a93f3-222">Definitiv ist dies etwas, mit dem es sich lohnt, als Ausgangspunkt für einen ernsthafteren Einstieg in C# zu experimentieren.</span><span class="sxs-lookup"><span data-stu-id="a93f3-222">It is definitely something worth experimenting with as a stepping stone into more serious C#.</span></span>

<!-- link references -->
[Originalversion]: https://powershellexplained.com/2018-08-04-Powershell-Standard-Library-Binary-Module/
[original version]: https://powershellexplained.com/2018-08-04-Powershell-Standard-Library-Binary-Module/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[PowerShell-Standardbibliothek]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard Library]: https://github.com/PowerShell/PowerShellStandard
[Erstellen eines plattformübergreifenden binären Moduls]: https://github.com/PowerShell/PowerShell/blob/master/docs/cmdlet-example/command-line-simple-example.md
[Creating a cross-platform binary module]: https://github.com/PowerShell/PowerShell/blob/master/docs/cmdlet-example/command-line-simple-example.md
[.NET Core SDK]: https://www.microsoft.com/net/download/core
[dotnet core SDK]: https://www.microsoft.com/net/download/core
[Verwenden eines NuGet-Servers für ein PSRepository]: https://powershellexplained.com/2018-03-03-Powershell-Using-a-NuGet-server-for-a-PSRepository/
[Using a NuGet server for a PSRepository]: https://powershellexplained.com/2018-03-03-Powershell-Using-a-NuGet-server-for-a-PSRepository/
[Windows PowerShell SDK]: /powershell/scripting/developer/windows-powershell-reference
[VS Code]: https://code.visualstudio.com
[NuGet-Paket]: https://www.nuget.org/packages/PowerShellStandard.Library/
[nuget package]: https://www.nuget.org/packages/PowerShellStandard.Library/
