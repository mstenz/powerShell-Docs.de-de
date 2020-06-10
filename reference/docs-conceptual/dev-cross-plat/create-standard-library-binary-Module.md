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
# <a name="how-to-create-a-standard-library-binary-module"></a>Erstellen eines binären Standardbibliotheksmoduls

Vor Kurzem hatte ich eine Idee für ein Modul, das ich als binäres Modul implementieren wollte. Ich habe noch keines mithilfe der [PowerShell-Standardbibliothek][] erstellt, weshalb ich dies als gute Gelegenheit empfand. Ich habe die Anleitung zum [Erstellen eines plattformübergreifenden binären Moduls][] befolgt und konnte dieses Modul ohne jegliche Schwierigkeiten erstellen.
Wir werden den gleichen Prozess durchlaufen, wobei ich zwischendurch noch den einen oder anderen zusätzlichen Kommentar hinzufügen werde.

> [!NOTE]
> Die [Originalversion][] dieses Artikels ist im Blog von [@KevinMarquette][] erschienen. Das PowerShell-Team dankt Kevin Marquette, dass er diesen Inhalt mit uns teilt. Weitere Informationen finden Sie in seinem Blog auf [PowerShellExplained.com][].

## <a name="what-is-the-powershell-standard-library"></a>Was ist die PowerShell-Standardbibliothek?

Die PowerShell-Standardbibliothek ermöglicht uns, plattformübergreifende Module zu erstellen, die sowohl mit PowerShell Core als auch mit Windows PowerShell 5.1 (oder 3.0) funktionieren.

## <a name="planning-our-module"></a>Planen des Moduls

Der Plan für dieses Modul sieht vor, den Ordner `src` für den C#-Code anzulegen und den Rest wie für ein Skriptmodul zu strukturieren. Dazu gehört die Nutzung eines Buildskripts, um alles in den Ordner `output` zu kompilieren. Die Ordnerstruktur sieht folgendermaßen aus:

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

## <a name="getting-started"></a>Erste Schritte

Normalerweise arbeite ich mit einer Plaster-Vorlage, aber meine aktuelle bietet noch keine Unterstützung binärer Module. Das macht aber nichts. Dieses Mal werde ich sie von Hand erstellen.

Zuerst muss ich den Ordner und das Git-Repository erstellen. Ich verwende `$module` als Platzhalter für den Modulnamen. Dies erleichtert Ihnen, diese Beispiele bei Bedarf wiederzuverwenden.

```powershell
$module = 'MyModule'
New-Item -Path $module -Type Directory
Set-Location $module
git init
```

Dann werden die Ordner auf Stammebene erstellt.

```powershell
New-Item -Path 'src' -Type Directory
New-Item -Path 'Output' -Type Directory
New-Item -Path 'Tests' -Type Directory
New-Item -Path $module -Type Directory
```

### <a name="binary-module-setup"></a>Einrichtung des binären Moduls

In diesem Artikel konzentrieren wir uns auf das binäre Modul, womit wir auch beginnen wollen. In diesem Abschnitt werden Beispiele der Anleitung zum [Erstellen eines plattformübergreifenden binären Moduls][] entnommen. Lesen Sie diese Anleitung, wenn Sie weitere Einzelheiten benötigen oder Probleme haben.

Als Erstes überprüfen wir die installierte Version des [.NET Core SDK][]. Ich nutze 2.1.4, aber Sie sollten mindestens 2.0.0 haben, ehe Sie fortfahren.

```powershell
PS> dotnet --version
2.1.4
```

In diesem Abschnitt arbeite ich mit dem Inhalt des Ordners `src`.

```powershell
Set-Location 'src'
```

Erstellen Sie mit dem Befehl dotnet eine neue Klassenbibliothek.

```powershell
dotnet new classlib --name $module
```

Dadurch wird das Bibliotheksprojekt in einem Unterordner erstellt, aber ich möchte diese zusätzliche Schachtelungsebene nicht. Ich verschiebe diese Dateien deshalb um eine Ebene nach oben.

```powershell
Move-Item -Path .\$module\* -Destination .\
Remove-Item $module -Recurse
```

Legen Sie die .NET Core SDK-Version für das Projekt fest. Ich arbeite mit dem SDK 2.1, weshalb ich 2.1.0 angebe.
Geben Sie 2.0.0 an, wenn Sie das SDK 2.0 verwenden.

```powershell
dotnet new globaljson --sdk-version 2.1.0
```

Fügen Sie dem Projekt das NuGet-Paket [NuGet-Paket][] hinzu. Vergewissern Sie sich, dass Sie die neueste verfügbare Version für den benötigten Kompatibilitätsgrad nutzen. Ich würde standardmäßig die neueste Version einsetzen, aber ich glaube nicht, dass in diesem Modul neuere Features als die von PowerShell 3.0 genutzt werden.

```powershell
dotnet add package PowerShellStandard.Library --version 7.0.0-preview.1
```

Unser Ordner „src“ sieht dann wie folgt aus:

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

Nun können wir dem Projekt unseren eigenen Code hinzufügen.

### <a name="building-a-binary-cmdlet"></a>Erstellen eines binären Cmdlets

Wir müssen die Datei `src\Class1.cs` so aktualisieren, dass sie dieses Start-Cmdlet enthält:

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

Benennen Sie die Datei entsprechend dem Klassennamen um.

```powershell
Rename-Item .\Class1.cs .\ResolveMyCmdletCommand.cs
```

Anschließend können wir unser Modul erstellen.

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

Wir können `Import-Module` in der neuen DLL aufrufen, um unser neues Cmdlet zu laden.

```powershell
PS> Import-Module .\bin\Debug\netstandard2.0\$module.dll
PS> Get-Command -Module $module

CommandType Name                    Version Source
----------- ----                    ------- ------
Cmdlet      Resolve-MyCmdlet        1.0.0.0 MyModule
```

Falls der Import auf Ihrem System fehlschlägt, versuchen Sie, .NET auf mindestens 4.7.1 zu aktualisieren. In der Anleitung zum [Erstellen eines plattformübergreifenden binären Moduls][] wird ausführlicher auf .NET-Unterstützung und Kompatibilität mit älteren .NET-Versionen eingegangen.

### <a name="module-manifest"></a>Modulmanifest

Es ist cool, dass wir die DLL importieren können und ein funktionierendes Modul haben. Ich möchte damit weitermachen und ein Modulmanifest erstellen. Wir brauchen das Manifest, wenn wir es später in der PSGallery veröffentlichen möchten.

Im Stammverzeichnis des Projekts können wir diesen Befehl ausführen, um das benötigte Modulmanifest zu erstellen.

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

Ich werde außerdem ein leeres Stammmodul für künftige PowerShell-Funktionen erstellen.

```powershell
Set-Content -Value '' -Path ".\$module\$module.psm1"
```

Dadurch kann ich sowohl normale PowerShell-Funktionen als auch binäre Cmdlets im selben Projekt kombinieren.

### <a name="building-the-full-module"></a>Erstellen des vollständigen Moduls

Ich kompiliere alles zusammen in einem Ordner namens „Output“. Hierfür muss ein Buildskript erstellt werden. Normalerweise würde ich dies einem `Invoke-Build`-Skript hinzufügen, aber für dieses Beispiel halten wir es einfach. Fügen Sie dies zur Datei `build.ps1` im Stammverzeichnis des Projekts hinzu.

```powershell
$module = 'MyModule'
Push-Location $PSScriptRoot

dotnet build $PSScriptRoot\src -o $PSScriptRoot\output\$module\bin
Copy-Item "$PSScriptRoot\$module\*" "$PSScriptRoot\output\$module" -Recurse -Force

Import-Module "$PSScriptRoot\Output\$module\$module.psd1"
Invoke-Pester "$PSScriptRoot\Tests"
```

Mit diesen Befehlen erstellen wir unsere DLL und legen sie in unserem Ordner `output\$module\bin` ab. Anschließend werden die anderen Moduldateien an die passende Stelle kopiert.

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

An diesem Punkt können wir das Modul mit der PSD1-Datei importieren.

```powershell
Import-Module ".\Output\$module\$module.psd1"
```

Von hier aus können wir den Ordner `.\Output\$module` in unserem Verzeichnis `$env:PSModulePath` ablegen. Unser Befehl wird anschließend nach Bedarf automatisch geladen.

### <a name="update-dotnet-new-psmodule"></a>Update: neue Vorlage für PSModule im Befehl dotnet

Ich habe erfahren, dass das Tool `dotnet` die Vorlage `PSModule` enthält.

Alle von mir beschriebenen Schritte sind immer noch gültig, aber diese Vorlage macht viele davon überflüssig. Es handelt sich nach wie vor um eine ziemlich neue Vorlage, die noch weiter aufpoliert wird. Gehen Sie davon aus, dass sie immer besser wird.

Die Vorlage PSModule wird folgendermaßen installiert und eingesetzt.

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
dotnet new psmodule
dotnet build
Import-Module "bin\Debug\netstandard2.0\$module.dll"
Get-Module $module
```

Diese einfache Vorlage kümmert sich um das Hinzufügen des .NET SDK und der PowerShell-Standardbibliothek und erstellt eine Beispielklasse im Projekt. Sie können sie unmittelbar erstellen und ausführen.

## <a name="important-details"></a>Wichtige Details

Bevor wir diesen Artikel abschließen, sollen noch ein paar weitere erwähnenswerte Details genannt werden.

### <a name="unloading-dlls"></a>Entladen von DLLs

Sobald ein binäres Modul geladen wurde, kann es nicht mehr wirklich entladen werden. Die DLL-Datei ist gesperrt, bis Sie sie entladen. Dies kann beim Entwickeln nervig sein, denn jedes Mal, wenn Sie eine Änderung vornehmen und diese umsetzen möchten, ist die Datei oftmals gesperrt. Die einzige zuverlässige Möglichkeit zur Lösung dieses Problems besteht darin, die PowerShell-Sitzung zu schließen, die die DLL geladen hat.

### <a name="vs-code-reload-window-action"></a>VS Code-Aktion „Fenster erneut laden“

Ich erledige den größten Teil meiner PowerShell-Entwicklungsarbeit in [VS Code][]. Wenn ich an einem binären Modul (oder einem Modul mit Klassen) arbeite, habe ich mir angewöhnt, VS Code jedes Mal neu zu laden, wenn ich einen Build erstelle.
Über <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd> wird das Befehlsfenster geöffnet, und `Reload Window` steht in meiner Liste immer ganz oben.

### <a name="nested-powershell-sessions"></a>Geschachtelte PowerShell-Sitzungen

Eine andere Möglichkeit ist eine gute Testabdeckung durch Pester. Dann können Sie das Skript „build.ps1“ so anpassen, dass es eine neue PowerShell-Sitzung startet, den Build durchführt, die Tests ausführt und die Sitzung schließt.

### <a name="updating-installed-modules"></a>Aktualisieren installierter Module

Diese Sperre kann lästig sein, wenn Sie versuchen, Ihr lokal installiertes Modul zu aktualisieren. Wenn es in einer Sitzung geladen ist, müssen Sie es aufspüren und schließen. Dies ist weniger problematisch, wenn die Installation über eine PSGallery erfolgt, da die Modulversionsverwaltung die neue Version in einem anderen Ordner ablegt.

Sie können eine lokale PSGallery einrichten und diese als Teil Ihres Builds veröffentlichen. Anschließend führen Sie Ihre lokale Installation über diese PSGallery durch. Das klingt nach einer Menge Arbeit, kann aber so einfach sein wie das Starten eines Docker-Containers. Eine Möglichkeit dazu beschreibe ich in meinem Beitrag zum [Verwenden eines NuGet-Servers für ein PSRepository][].

## <a name="why-binary-modules"></a>Gründe für binäre Module

Ich habe mich sofort an die Erstellung eines binären Moduls gemacht, ohne auf die Gründe dafür einzugehen. In Wirklichkeit schreiben Sie C#-Code und geben den einfachen Zugriff auf PowerShell-Cmdlets und -Funktionen auf. Das ist der Hauptgrund, warum ich nicht schon früher zu binären Modulen übergegangen bin.

Doch wenn Sie ein Modul erstellen, das nicht von vielen anderen PowerShell-Befehlen abhängig ist, kann der Leistungszuwachs erheblich sein. Durch den Umstieg auf C# können Sie den von PowerShell hinzugefügten Zusatzaufwand vermeiden. PowerShell wurde für Administratoren und nicht für den Computer optimiert, was ein wenig mehr Aufwand bedeutet.

Bei der Arbeit haben wir einen kritischen Prozess, der viele Aufgaben mithilfe von JSON und Hashtabellen erledigt. Wir haben PowerShell nach Kräften optimiert, aber dieser Prozess dauerte immer noch 12 Minuten. Das Modul enthielt bereits eine Menge PowerShell im C#-Stil. Dadurch wurde eine einfache und schnelle Umwandlung in ein binäres Modul möglich. Durch diese Umwandlung konnte dieser Prozess von über 12 auf unter vier Minuten verkürzt werden.

### <a name="hybrid-modules"></a>Hybridmodule

Sie können binäre Cmdlets mit erweiterten PowerShell-Funktionen kombinieren. Das ist genau das, was ich in dieser Anleitung mache. Sie können alles, was Sie über Skriptmodule wissen, übernehmen, wobei alles in gleicher Weise zutrifft.
Die leere Datei `psm1`, die ich heute erstellt habe, ist nur dazu da, damit Sie später andere PowerShell-Funktionen einfügen können.

Nahezu alle kompilierten Cmdlets, die wir erstellt haben, waren anfangs eine PowerShell-Funktion. Alle unsere Binärmodule sind eigentlich Hybridmodule.

### <a name="build-scripts"></a>Buildskripts

Ich habe das Buildskript hier einfach gehalten. Im Allgemeinen nutze ich ein großes `Invoke-Build`-Skript als Teil meiner CI/CD-Pipeline. Es leistet mehr als das Ausführen von Pester-Tests und PSScriptAnalyzer, die Versionsverwaltung und die Veröffentlichung in der PSGallery. Nachdem ich angefangen hatte, ein Buildskript für meine Module zu nutzen, konnte ich viele Dinge finden, die ich ihm hinzufügen konnte.

## <a name="final-thoughts"></a>Schlussbemerkungen

Binäre Module können einfach erstellt werden. Ich habe die C#-Syntax zum Erstellen eines Cmdlets nicht angeschnitten, aber es gibt im [Windows PowerShell SDK][] reichlich Dokumentation dazu. Definitiv ist dies etwas, mit dem es sich lohnt, als Ausgangspunkt für einen ernsthafteren Einstieg in C# zu experimentieren.

<!-- link references -->
[Originalversion]: https://powershellexplained.com/2018-08-04-Powershell-Standard-Library-Binary-Module/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[PowerShell-Standardbibliothek]: https://github.com/PowerShell/PowerShellStandard
[Erstellen eines plattformübergreifenden binären Moduls]: https://github.com/PowerShell/PowerShell/blob/master/docs/cmdlet-example/command-line-simple-example.md
[.NET Core SDK]: https://www.microsoft.com/net/download/core
[Verwenden eines NuGet-Servers für ein PSRepository]: https://powershellexplained.com/2018-03-03-Powershell-Using-a-NuGet-server-for-a-PSRepository/
[Windows PowerShell SDK]: /powershell/scripting/developer/windows-powershell-reference
[VS Code]: https://code.visualstudio.com
[NuGet-Paket]: https://www.nuget.org/packages/PowerShellStandard.Library/
