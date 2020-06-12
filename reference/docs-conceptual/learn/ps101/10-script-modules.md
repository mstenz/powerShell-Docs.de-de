---
title: Skriptmodule
description: Skriptmodule sind eine einfache Möglichkeit, Skripts und Funktionen in einem wiederverwendbaren Tool zu verpacken.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 661ba725764e1f31df628f6c5f2d58d760656e37
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438281"
---
# <a name="chapter-10---script-modules"></a>Kapitel 10: Skriptmodule

Die Umwandlung Ihrer Einzeiler und Skripts in PowerShell in wiederverwendbare Tools wird sogar noch wichtiger, wenn es sich um etwas handelt, das Sie häufig verwenden werden. Wenn Sie Ihre Funktionen in ein Skriptmodul packen, sieht dies professioneller aus, fühlt sich auch so an, und Sie können die Funktionen leichter teilen.

## <a name="dot-sourcing-functions"></a>Dot-Sourcing-Funktionen

Etwas, das wir im vorherigen Kapitel nicht besprochen haben, sind Dot-Sourcing-Funktionen. Wenn eine Funktion in einem Skript nicht Teil eines Moduls ist, besteht die einzige Möglichkeit, sie in den Arbeitsspeicher zu laden, darin, ein Dot-Sourcing der Datei `.PS1` vorzunehmen, in der sie gespeichert ist.

Die folgende Funktion wurde als `Get-MrPSVersion.ps1` gespeichert.

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}
```

Wenn Sie das Skript ausführen, geschieht nichts.

```powershell
.\Get-MrPSVersion.ps1
```

Wenn Sie versuchen, die-Funktion aufzurufen, wird eine Fehlermeldung generiert.

```powershell
Get-MrPSVersion
```

```Output
Get-MrPSVersion : The term 'Get-MrPSVersion' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [], CommandNotFou
   ndException
    + FullyQualifiedErrorId : CommandNotFoundException

```

Sie können bestimmen, ob Funktionen in den Arbeitsspeicher geladen wurden, indem Sie überprüfen, ob sie im PSDrive der **Funktion** vorhanden sind.

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
Get-ChildItem : Cannot find path 'Get-MrPSVersion' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path Function:\Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [Get-ChildItem],
   ItemNotFoundException
    + FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
```

Das Problem beim Aufrufen des Skripts, das die Funktion enthält, besteht darin, dass die Funktionen in den Gültigkeitsbereich _Skript_ geladen werden. Wenn das Skript abgeschlossen ist, wird dieser Gültigkeitsbereich entfernt, und zusammen damit die Funktion.

Die Funktion muss in den Gültigkeitsbereich _Global_ geladen werden. Dies kann durch Dot-Sourcing des Skripts erreicht werden, das die Funktion enthält. Der relative Pfad kann verwendet werden.

```powershell
. .\Get-MrPSVersion.ps1
```

Ebenso kann der vollqualifizierte Pfad verwendet werden.

```powershell
. C:\Demo\Get-MrPSVersion.ps1
```

Wenn ein Teil des Pfads in einer Variablen gespeichert ist, kann er mit dem Rest des Pfads kombiniert werden.
Es gibt keinen Grund, Zeichenfolgenverkettung zu verwenden, um die Variable mit dem Rest des Pfads zu kombinieren.

```powershell
$Path = 'C:\'
. $Path\Get-MrPSVersion.ps1
```

Wenn ich nun das PSDrive der **Funktion** überprüfe, ist die Funktion `Get-MrPSVersion` vorhanden.

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-MrPSVersion
```

## <a name="script-modules"></a>Skriptmodule

Ein Skriptmodul in PowerShell ist lediglich eine Datei, die eine oder mehrere Funktionen enthält, die als `.PSM1`-Datei gespeichert wurden, nicht als `.PS1`-Datei.

Wie erstellen Sie ein Skriptmodul? Wahrscheinlich vermuten Sie schon mit einem Befehl, der ungefähr einen Namen wie `New-Module` trägt. Ihre Annahme wäre leider falsch. Zwar gibt es einen Befehl namens `New-Module` in PowerShell, doch erstellt dieser Befehl ein dynamisches Modul, kein Skriptmodul. Lesen Sie also immer unbedingt die Hilfe für einen Befehl, auch wenn Sie der Ansicht sind, dass Sie den benötigten Befehl gefunden haben.

```powershell
help New-Module
```

```Output
NAME
    New-Module

SYNOPSIS
    Creates a new dynamic module that exists only in memory.

SYNTAX
    New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-ArgumentList <Object[]>]
    [-AsCustomObject] [-Cmdlet <String[]>] [-Function <String[]>] [-ReturnResult]
    [<CommonParameters>]

DESCRIPTION
    The New-Module cmdlet creates a dynamic module from a script block. The members of
    the dynamic module, such as functions and variables, are immediately available in
    the session and remain available until you close the session.

    Like static modules, by default, the cmdlets and functions in a dynamic module are
    exported and the variables and aliases are not. However, you can use the
    Export-ModuleMember cmdlet and the parameters of New-Module to override the defaults.

    You can also use the AsCustomObject parameter of New-Module to return the dynamic
    module as a custom object. The members of the modules, such as functions, are
    implemented as script methods of the custom object instead of being imported into
    the session.

    Dynamic modules exist only in memory, not on disk. Like all modules, the members of
    dynamic modules run in a private module scope that is a child of the global scope.
    Get-Module cannot get a dynamic module, but Get-Command can get the exported members.

    To make a dynamic module available to Get-Module , pipe a New-Module command to
    Import-Module, or pipe the module object that New-Module returns to Import-Module .
    This action adds the dynamic module to the Get-Module list, but it does not save the
    module to disk or make it persistent.

RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821495
    Export-ModuleMember
    Get-Module
    Import-Module
    Remove-Module

REMARKS
    To see the examples, type: "get-help New-Module -examples".
    For more information, type: "get-help New-Module -detailed".
    For technical information, type: "get-help New-Module -full".
    For online help, type: "get-help New-Module -online"
```

Im vorherigen Kapitel habe ich erwähnt, dass Funktionen genehmigte Verben verwenden sollten, da sie sonst eine Warnmeldung generieren, wenn das Modul importiert wird. Der folgende Code verwendet das Cmdlet `New-Module`, um ein dynamisches Modul im Arbeitsspeicher zu erstellen. Dieses Modul veranschaulicht die Warnung wegen nicht genehmigter Verben.

```powershell
New-Module -Name MyModule -ScriptBlock {

    function Return-MrOsVersion {
        Get-CimInstance -ClassName Win32_OperatingSystem |
        Select-Object -Property @{label='OperatingSystem';expression={$_.Caption}}
    }

    Export-ModuleMember -Function Return-MrOsVersion

} | Import-Module
```

```Output
WARNING: The names of some imported commands from the module 'MyModule' include
unapproved verbs that might make them less discoverable. To find the commands with
unapproved verbs, run the Import-Module command again with the Verbose parameter. For a
list of approved verbs, type Get-Verb.
```

Um dies noch mal zu wiederholen: Obwohl das Cmdlet `New-Module` im vorherigen Beispiel verwendet wurde, ist dies nicht der Befehl zum Erstellen von Skriptmodulen in PowerShell.

Speichern Sie die folgenden zwei Funktionen in einer Datei namens `MyScriptModule.psm1`.

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}
```

Versuchen Sie, eine der Funktionen aufzurufen.

```powershell
Get-MrComputerName
```

```Output
Get-MrComputerName : The term 'Get-MrComputerName' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrComputerName
    + CategoryInfo          : ObjectNotFound: (Get-MrComputerName:String) [], CommandNot
   FoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

Es wird eine Fehlermeldung generiert, die besagt, dass die Funktion nicht gefunden wurde. Sie könnten auch das PSDrive der **Funktion** wie bereits zuvor überprüfen, und Sie werden feststellen, dass sie dort auch nicht vorhanden ist.

Sie könnten die Datei manuell mit dem Cmdlet `Import-Module` importieren.

```powershell
Import-Module C:\MyScriptModule.psm1
```

Die Funktion für das automatische Laden von Modulen wurde in PowerShell-Version 3 eingeführt. Um das automatische Laden von Modulen zu nutzen, muss ein Skriptmodul in einem Ordner mit demselben Basisnamen wie die Datei `.PSM1` sowie an einem in `$env:PSModulePath` angegebenen Speicherort gespeichert werden.

```powershell
$env:PSModulePath
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules;C:\Program Files\WindowsPowerShell\
Modules;C:\Windows\system32\WindowsPowerShell\v1.0\Modules;C:\Program Files (x86)\Microsof
t SQL Server\130\Tools\PowerShell\Modules\
```

Die Ergebnisse sind schwer zu lesen. Da die Pfade durch ein Semikolon getrennt sind, können Sie die Ergebnisse so aufteilen, dass jeder Pfad in einer separaten Zeile zurückgegeben wird. Dies vereinfacht das Lesen.

```powershell
$env:PSModulePath -split ';'
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules
C:\Program Files\WindowsPowerShell\Modules
C:\Windows\system32\WindowsPowerShell\v1.0\Modules
C:\Program Files (x86)\Microsoft SQL Server\130\Tools\PowerShell\Modules\
```

Die ersten drei Pfade in der Liste sind die Standardwerte. Wenn SQL Server Management Studio installiert ist, wurde der letzte Pfad davon hinzugefügt. Damit das automatische Laden von Modulen funktioniert, muss sich die Datei `MyScriptModule.psm1` in einem Ordner namens `MyScriptModule` direkt innerhalb eines dieser Pfade befinden.

Nicht so schnell. Bei mir ist mein aktueller Benutzerpfad nicht der erste in der Liste. Ich verwende diesen Pfad fast nie, da ich mich bei Windows mit einem anderen Benutzer anmelde als dem, den ich zum Ausführen von PowerShell verwende. Dies bedeutet, dass er sich nicht in meinem normalen Ordner „Dokumente“ befindet.

Der zweite Pfad ist der Pfad **AllUsers**. Dies ist der Speicherort, an dem ich alle meine Module speichere.

Der dritte Pfad befindet sich unter `C:\Windows\System32`. Nur Microsoft sollte Module an diesem Speicherort speichern, da es sich im Betriebssystemordner befindet.

Sobald sich die Datei `.PSM1` im richtigen Pfad befindet, wird das Modul automatisch geladen, wenn einer seiner Befehle aufgerufen wird.

## <a name="module-manifests"></a>Modulmanifeste

Alle Module sollten über ein Modulmanifest verfügen. Ein Modulmanifest enthält Metadaten zu Ihrem Modul.
Die Dateierweiterung für eine Modulmanifestdatei lautet `.PSD1`. Nicht alle Dateien mit einer `.PSD1`-Erweiterung sind Modulmanifeste. Sie können auch für Dinge verwendet werden wie das Speichern des Umgebungsteils einer DSC-Konfiguration. `New-ModuleManifest` wird verwendet, um ein Modulmanifest zu erstellen. **Path** ist der einzige erforderliche Wert. Das Modul funktioniert jedoch nicht, wenn **RootModule** nicht angegeben ist. Es empfiehlt sich, **Author** und **Description** anzugeben für den Fall, dass Sie sich entschließen, das Modul mit „PowerShellGet“ in ein NuGet-Repository hochzuladen, da diese Werte in diesem Szenario erforderlich sind.

Die Version eines Moduls ohne Manifest ist 0.0. Dies ist ein untrügliches Zeichen dafür, dass das Modul kein Manifest besitzt.

```powershell
Get-Module -Name MyScriptModule
```

```Output
ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Script     0.0        myscriptmodule                      {Get-MrComputerName, Get-MrP...
```

Das Modulmanifest kann mit allen empfohlenen Informationen erstellt werden.

```powershell
New-ModuleManifest -Path $env:ProgramFiles\WindowsPowerShell\Modules\MyScriptModule\MyScriptModule.psd1 -RootModule MyScriptModule -Author 'Mike F Robbins' -Description 'MyScriptModule' -CompanyName 'mikefrobbins.com'
```

Fehlt eine dieser Informationen bei der anfänglichen Erstellung des Modulmanifests, kann sie später mithilfe von `Update-ModuleManifest` hinzugefügt oder aktualisiert werden. Erstellen Sie das Manifest nicht mit `New-ModuleManifest` neu, nachdem es bereits erstellt wurde, weil sich sonst die GUID ändert.

## <a name="defining-public-and-private-functions"></a>Definieren öffentlicher und privater Funktionen

Möglicherweise verfügen Sie über Hilfsfunktionen, die privat sein sollen und auf die nur Funktionen innerhalb des Moduls zugreifen können sollen. Benutzer Ihres Moduls sollen nicht darauf zugreifen können. Dies kann auf unterschiedliche Arten erreicht werden.

Wenn Sie die bewährten Methoden nicht befolgen und nur eine `.PSM1`-Datei besitzen, besteht Ihre einzige Möglichkeit darin, das Cmdlet `Export-ModuleMember` zu verwenden.

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}

Export-ModuleMember -Function Get-MrPSVersion
```

Im vorherigen Beispiel ist nur die Funktion `Get-MrPSVersion` für die Benutzer Ihres Moduls verfügbar, aber die Funktion `Get-MrComputerName` steht anderen Funktionen im Modul selbst zur Verfügung.

```powershell
Get-Command -Module MyScriptModule

CommandType     Name                        Version    Source
-----------     ----                        -------    ------
Function        Get-MrPSVersion             1.0        MyScript...
```

Wenn Sie Ihrem Modul ein Modulmanifest hinzugefügt haben (und dies sollten Sie), empfehle ich, die einzelnen Funktionen, die Sie exportieren möchten, im Abschnitt **FunctionsToExport** des Modulmanifests anzugeben.

```powershell
FunctionsToExport = 'Get-MrPSVersion'
```

Es ist nicht erforderlich, `Export-ModuleMember` sowohl in der `.PSM1`-Datei als auch im Abschnitt **FunctionsToExport** des Modulmanifests zu verwenden. Das eine oder das andere ist ausreichend.

## <a name="summary"></a>Zusammenfassung

In diesem Kapitel haben Sie erfahren, wie Sie Ihre Funktionen in ein Skriptmodul in PowerShell umwandeln. Sie haben außerdem einige bewährte Methoden zum Erstellen von Skriptmodulen kennen gelernt, wie das Erstellen eines Modulmanifests für Ihr Skriptmodul.

## <a name="review"></a>Überprüfung

1. Wie erstellen Sie ein Skriptmodul in PowerShell?
1. Warum ist es wichtig, dass ihre Funktionen ein genehmigtes Verb verwenden?
1. Wie erstellen Sie ein Modulmanifest in PowerShell?
1. Welche zwei Optionen sind zum Exportieren von nur bestimmten Funktionen aus Ihrem Modul verfügbar?
1. Was ist erforderlich, damit Ihre Module automatisch geladen werden, wenn ein Befehl aufgerufen wird?

## <a name="recommended-reading"></a>Empfohlene Lektüre

- [Erstellen von PowerShell-Skriptmodulen und Modulmanifesten][]
- [about_Modules][]
- [New-ModuleManifest][]
- [Export-ModuleMember][]

<!-- link references -->
[Erstellen von PowerShell-Skriptmodulen und Modulmanifesten]: https://mikefrobbins.com/2013/07/04/how-to-create-powershell-script-modules-and-module-manifests/
[about_Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Export-ModuleMember]: /powershell/module/microsoft.powershell.core/export-modulemember
