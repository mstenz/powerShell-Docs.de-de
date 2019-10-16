---
title: Schreiben eines PowerShell-Modul Manifests | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 1265855b82b0bfaa7b2717c8eb348b822c19f561
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367099"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>Schreiben eines PowerShell-Binärmoduls

Nachdem Sie Ihr Windows PowerShell-Modul geschrieben haben, können Sie optional ein Modul Manifest hinzufügen. Ein Modul Manifest ist eine PowerShell-Skriptdatei, die Sie verwenden können, um Informationen zum Modul einzuschließen. Sie können z. b. den Autor beschreiben, Dateien im Modul angeben (z. b. in Form von Netz Modulen), Skripts ausführen, um die Benutzerumgebung anzupassen, den Auslastungstyp und die Formatierungs Dateien zu definieren, Systemanforderungen zu definieren und die vom Modul exportierte Member einzuschränken.

## <a name="creating-a-module-manifest"></a>Erstellen eines Modul Manifests

Ein *Modul Manifest* ist eine Windows PowerShell-Datendatei (. psd1), die den Inhalt eines Moduls beschreibt und bestimmt, wie ein Modul verarbeitet wird. Die Manifest-Datei selbst ist eine Textdatei, die eine Hash Tabelle mit Schlüsseln und Werten enthält. Wenn Sie eine Manifest-Datei mit einem Modul verknüpfen, benennen Sie Sie wie das Modul, und platzieren Sie Sie im Stammverzeichnis des Modul Verzeichnisses.

Für einfache Module, die nur eine einzelne. psm1-oder binäre Assembly enthalten, ist ein Modul Manifest optional. Es wird jedoch empfohlen, nach Möglichkeit ein Modul Manifest zu verwenden, da Sie hilfreich sind, um den Code zu organisieren und Versionsinformationen beizubehalten. Außerdem ist ein Modul Manifest erforderlich, um eine Assembly zu exportieren, die im globalen Assemblycache installiert ist. Ein Modul Manifest ist auch für Module erforderlich, die die aktualisierbare Hilfe Funktion unterstützen. Das heißt, die aktualisierbare Hilfe verwendet den **helpinfouri** -Schlüssel im Modul Manifest, um die Hilfe Informationsdatei (helpinfo XML) zu suchen, die den Speicherort der aktualisierten Hilfedateien für das Modul enthält. Weitere Informationen zur aktualisierbaren Hilfe finden Sie [unter unterstützen der aktualisierbaren Hilfe](./supporting-updatable-help.md).

### <a name="to-create-and-use-a-module-manifest"></a>So erstellen und verwenden Sie ein Modul Manifest

1. Zum Erstellen eines Modul Manifests haben Sie mehrere Möglichkeiten:

   1. Erstellen Sie die Hash Tabelle direkt mit den minimal erforderlichen Informationen, und speichern Sie Sie in einer psd1-Datei, die denselben Namen wie Ihr Modul hat. Nachdem Sie dies abgeschlossen haben, können Sie die Datei öffnen und die entsprechenden Werte manuell hinzufügen.

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. Sie können auch das [New-modulemanifest-](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) Cmdlet mit einem oder mehreren Standardwerten, die als Parameter übergeben werden, aufzurufen. (Beachten Sie, dass nur der Name der Datei erforderlich ist, um ein Manifest zu generieren.) Dadurch wird ein Modul Manifest erstellt, in dem alle von Ihnen explizit angegebenen manifestresswerte angegeben sind, und mit dem Rest, der den entsprechenden Standardwert enthält.

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. Schließlich können Sie auch eine leere psd1-Datei erstellen und die Vorlage am Ende dieses Themas in die Datei kopieren und die relevanten Werte eingeben. In diesem Fall besteht die einzige wirkliche Anforderung darin, sicherzustellen, dass die Datei mit dem Modul identisch benannt wurde.

2. Fügen Sie dem Manifest, das Sie in der Datei enthalten möchten, weitere Elemente hinzu.

   Im Allgemeinen wird dies wahrscheinlich in einem beliebigen Text-Editor, z. b. in Notepad, durchgeführt. Dabei handelt es sich technisch gesehen um eine Skriptdatei, die Code enthält, sodass Sie Sie in einer tatsächlichen Skript-oder Entwicklungsumgebung wie Visual Studio Code bearbeiten können. Beachten Sie, dass alle Elemente einer Manifestressource optional sind, mit Ausnahme der moduleversion-Nummer.

   Beschreibungen der Schlüssel und Werte, die Sie in einem Modul Manifest haben können, finden Sie unten in den **Modul Manifest-Elementen** . Weitere Informationen finden Sie in den Beschreibungen der Parameter im Cmdlet " [New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) ".

3. Optional können Sie dem Modul Manifest zusätzlichen Code hinzufügen, um alle Szenarios zu behandeln, die nicht von den Manifest-Elementen des Basismoduls abgedeckt werden.

   Aufgrund von Sicherheitsbedenken führt PowerShell nur eine kleine Teilmenge der verfügbaren Vorgänge in einer Modul Manifest-Datei aus. Im Allgemeinen können Sie die **if** -Anweisung, die arithmetischen Operatoren und die Vergleichs Operatoren sowie die grundlegenden PowerShell-Datentypen verwenden.

4. Nachdem Sie das Modul Manifest erstellt haben, können Sie es testen (um sicherzustellen, dass alle im Manifest beschriebenen Pfade korrekt sind), indem Sie " [Test-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest)" aufgerufen haben.

   `Test-ModuleManifest myModuleName.psd1`

5. Stellen Sie sicher, dass sich das Modul Manifest auf der obersten Ebene des Verzeichnisses befindet, das das Modul enthält.

   Wenn Sie das Modul auf ein System kopieren und es importieren, verwendet PowerShell das Modul Manifest, um das Modul zu importieren.

6. Optional können Sie das Modul Manifest direkt mit einem [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) -Befehl überprüfen, indem Sie das Manifest selbst durch die Punkt Ermittlung abrufen.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Modul Manifest-Elemente

In der folgenden Tabelle werden die Elemente beschrieben, die in einem Modul Manifest enthalten sein können.

|Element|Standardwert|Description|
|-------------|-------------|-----------------|
|RootModule<br /><br /> Typ: Zeichenfolge|' '|Skript Modul oder binäre Modul Datei, die diesem Manifest zugeordnet ist. In früheren Versionen von PowerShell wurde dieses Element als "moduletoprocess" bezeichnet.<br /><br /> Mögliche Typen für das Stamm Modul können leer sein (wodurch dies ein **Manifest** -Modul ist), der Name eines Skript Moduls (. psm1, bei dem es sich um ein **Skript** Modul handelt) oder der Name eines binären Moduls (. exe oder. dll), das als **binäres** Modul verwendet wird. Wenn Sie den Namen eines Modul Manifests (. psd1) oder eine Skriptdatei (. ps1) in diesem Element platzieren, tritt ein Fehler auf.|
|ModuleVersion<br /><br /> Typ: Zeichenfolge|1.0|Versionsnummer dieses Moduls. Die Zeichenfolge muss in [System. Version] konvertiert werden können. Das heißt, "#. #. #. #. #". `Import-Module` lädt das erste Modul, das auf dem **$psModulePath** gefunden wird, das mit dem Namen übereinstimmt, und verfügt mindestens über eine "moduleversion", wie der `-MinimumVersion`-Parameter. Verwenden Sie stattdessen den @ no__t-0-Parameter, um eine bestimmte Version zu importieren.<br /><br /> Beispiel: `ModuleVersion = '1.0'`|
|GUID<br /><br /> Typ: Zeichenfolge|Automatisch generierte GUID|ID, die zur eindeutigen Identifizierung dieses Moduls verwendet wird. Beachten Sie, dass Sie zurzeit kein Modul nach GUID importieren können.<br /><br /> Beispiel: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|Autor<br /><br /> Typ: Zeichenfolge|Keine|Autor dieses Moduls.<br /><br /> Beispiel: `Author = 'AuthorNameHere'`|
|CompanyName<br /><br /> Typ: Zeichenfolge|Unbekannt|Unternehmen oder Hersteller dieses Moduls.<br /><br /> Beispiel: `CompanyName = 'Fabrikam'`|
|Urheberrecht<br /><br /> Typ: Zeichenfolge|(c) [currentyear] [Author]. Alle Rechte vorbehalten.|Copyright-Anweisung für dieses Modul.<br /><br /> Beispiel: `Copyright = '2016 AuthorName. All rights reserved.'`|
|Description<br /><br /> Typ: Zeichenfolge|' '|Beschreibung der von diesem Modul bereitgestellten Funktionalität.<br /><br /> Beispiel: `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> Typ: Zeichenfolge|' '|Mindestens erforderliche Version der Windows PowerShell-Engine, die von diesem Modul benötigt wird. Aktuelle gültige Werte sind 1,0, 2,0, 3,0, 4,0 und 5,0.<br /><br /> Beispiel: `PowerShellVersion = '5.0'`|
|Powershellhostname<br /><br /> Typ: Zeichenfolge|' '|Gibt den Namen des Windows PowerShell-Hosts an, der für das Modul erforderlich ist. Dieser Name wird von Windows PowerShell bereitgestellt. Um den Namen eines Host Programms zu suchen, geben Sie im Programm Folgendes ein: `$host.name`.<br /><br /> Beispiel: `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|Powershellhostversion<br /><br /> Typ: Zeichenfolge|' '|Mindestens erforderliche Version des Windows PowerShell-Hosts, die von diesem Modul benötigt wird.<br /><br /> Beispiel: `PowerShellHostVersion = '2.0'`|
|Dotnetframeworkversion<br /><br /> Typ: Zeichenfolge|' '|Mindestens erforderliche Version Microsoft .NET Frameworks, die von diesem Modul benötigt wird.<br /><br /> Beispiel: `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> Typ: Zeichenfolge|' '|Die für dieses Modul erforderliche Mindestversion des Common Language Runtime (CLR).<br /><br /> Beispiel: `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> Typ: Zeichenfolge|' '|Die Prozessorarchitektur (None, x86, amd64), die für dieses Modul erforderlich ist. Gültige Werte sind x86, AMD64, IA64 und None (unbekannt oder nicht angegeben).<br /><br /> Beispiel: `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> Type: [String []]|@()|Module, die vor dem Importieren dieses Moduls in die globale Umgebung importiert werden müssen. Dadurch werden alle aufgeführten Module geladen, sofern Sie nicht bereits geladen wurden. (Beispielsweise könnten einige Module bereits durch ein anderes Modul geladen worden sein.) Es ist auch möglich, eine bestimmte Version anzugeben, die mit `RequiredVersion` geladen werden soll, anstatt `ModuleVersion`. Wenn Sie `ModuleVersion` verwenden, wird die neueste Version geladen, die mindestens mit der angegebenen Version verfügbar ist.<br /><br /> Beispiel: `RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> Beispiel: `RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|Requirements dassemblys<br /><br /> Type: [String []]|@()|Assemblys, die vor dem Importieren dieses Moduls geladen werden müssen.<br /><br /> Beachten Sie, dass PowerShell im Gegensatz zu Requirements dmodules die Requirements dassemblys lädt, wenn Sie nicht bereits geladen sind.|
|ScriptsToProcess<br /><br /> Type: [String []]|@()|Skriptdateien (. ps1), die im Sitzungszustand des Aufrufers ausgeführt werden, wenn das Modul importiert wird. Dabei kann es sich um den globalen Sitzungs Status oder, bei genetzten Modulen, um den Sitzungszustand eines anderen Moduls handeln. Sie können diese Skripts verwenden, um eine Umgebung so vorzubereiten, wie Sie ein Anmelde Skript verwenden können.<br /><br /> Diese Skripts werden ausgeführt, bevor eines der im Manifest aufgelisteten Module geladen wird.|
|Typestoprocess<br /><br /> Type: [String []]|@()|Geben Sie beim Importieren dieses Moduls Dateien (. ps1xml) ein, die geladen werden sollen.|
|Formatstoprocess<br /><br /> Type: [String []]|@()|Format Dateien (. ps1xml), die beim Importieren dieses Moduls geladen werden.|
|NestedModules<br /><br /> Type: [String []]|@()|Module, die als geclusterte Module des Moduls importiert werden sollen, das in rootmodule/moduletoprocess angegeben ist.<br /><br /> Das Hinzufügen eines Modulnamens zu diesem Element ähnelt dem Aufrufen von `Import-Module` innerhalb Ihres Skripts oder Assemblycodes. Der Hauptunterschied besteht darin, dass Sie leichter erkennen können, was Sie hier in der Manifest-Datei laden. Wenn ein Modul hier nicht geladen werden kann, haben Sie das eigentliche Modul noch nicht geladen.<br /><br /> Zusätzlich zu anderen Modulen können Sie auch Skriptdateien (. ps1) hier laden. Diese Dateien werden im Kontext des root-Moduls ausgeführt. (Dies entspricht der Punkt Beschaffung des Skripts in ihrem Stamm Modul.)|
|"Functionstoexport"<br /><br /> Type: [String []]|@()|Gibt die Funktionen an, die das Modul exportiert (Platzhalter Zeichen sind zulässig, aber davon abgeraten), in den Sitzungszustand des Aufrufers Standardmäßig werden keine Funktionen exportiert. Sie können diesen Schlüssel verwenden, um die Funktionen aufzulisten, die vom Modul exportiert werden.<br /><br /> Der Sitzungszustand des Aufrufers kann der globale Sitzungs Status oder, bei einem anderen Modul, der Sitzungszustand eines anderen Moduls sein. Beim Verketten von geschachtelte-Modulen werden alle Funktionen, die von einem geschachtelte-Modul exportiert werden, in den globalen Sitzungszustand exportiert, es sei denn, ein Modul in der Kette schränkt die Funktion mit dem functionstoexport-Schlüssel ein.<br /><br /> Wenn das Manifest auch Aliase für die Funktionen exportiert, kann dieser Schlüsselfunktionen entfernen, deren Aliase im Schlüssel "aliasestoexport" aufgeführt sind, aber dieser Schlüssel kann der Liste keine Funktions Aliase hinzufügen.|
|"Cmdletstoexport"<br /><br /> Type: [String []]|@()|Gibt die Cmdlets an, die das Modul exportiert (Platzhalter Zeichen sind zulässig, werden jedoch nicht empfohlen). Standardmäßig werden keine Cmdlets exportiert. Mit diesem Schlüssel können Sie die Cmdlets auflisten, die vom Modul exportiert werden.<br /><br /> Der Sitzungszustand des Aufrufers kann der globale Sitzungs Status oder, bei einem anderen Modul, der Sitzungszustand eines anderen Moduls sein. Beim Verketten von geschachtelte-Modulen werden alle Cmdlets, die von einem geschachtelte-Modul exportiert werden, letztendlich in den globalen Sitzungs Status exportiert, es sei denn, ein Modul in der Kette schränkt das Cmdlet mit dem cmdletstoexport-Schlüssel ein.<br /><br /> Wenn das Manifest auch Aliase für die Cmdlets exportiert, kann dieser Schlüssel Cmdlets entfernen, deren Aliase im Schlüssel "aliasestoexport" aufgeführt sind. dieser Schlüssel kann jedoch keine Cmdlet-Aliase zur Liste hinzufügen.|
|Variablestoexport<br /><br /> Typ: Zeichenfolge|'*'|Gibt die Variablen an, die das Modul exportiert (Platzhalter Zeichen sind zulässig), in den Sitzungszustand des Aufrufers. Standardmäßig werden alle Variablen exportiert. Sie können diesen Schlüssel verwenden, um die Variablen einzuschränken, die vom Modul exportiert werden.<br /><br /> Der Sitzungszustand des Aufrufers kann der globale Sitzungs Status oder, bei einem anderen Modul, der Sitzungszustand eines anderen Moduls sein. Beim Verketten von geschachtelte-Modulen werden alle Variablen, die von einem geschachtelte-Modul exportiert werden, in den globalen Sitzungszustand exportiert, es sei denn, ein Modul in der Kette schränkt die Variable mit dem variablestoexport-Schlüssel ein.<br /><br /> Wenn das Manifest auch Aliase für die Variablen exportiert, kann dieser Schlüsselvariablen entfernen, deren Aliase im Schlüssel "aliasestoexport" aufgeführt sind, aber dieser Schlüssel kann der Liste keine Variablen Aliase hinzufügen.|
|AliasesToExport<br /><br /> Type: [String []]|@()|Gibt die Aliase an, die das Modul exportiert (Platzhalter Zeichen sind zulässig, aber davon abgeraten), in den Sitzungszustand des Aufrufers. Standardmäßig werden keine Aliase exportiert. Mit diesem Schlüssel können Sie die Aliase auflisten, die vom Modul exportiert werden.<br /><br /> Der Sitzungszustand des Aufrufers kann der globale Sitzungs Status oder, bei einem anderen Modul, der Sitzungszustand eines anderen Moduls sein. Beim Verketten von geschachtelte-Modulen werden alle Aliase, die von einem geschachtelte-Modul exportiert werden, letztendlich in den globalen Sitzungs Status exportiert, es sei denn, ein Modul in der Kette schränkt den Alias mithilfe des aliasestoexport-Schlüssels ein.|
|Modulliste<br /><br /> Type: [String []]|@()|Gibt alle Module an, die mit diesem Modul verpackt werden. Diese Module können anhand des Namens (eine durch Trennzeichen getrennte Zeichenfolge) oder als Hash Tabelle mit ModuleName-und GUID-Schlüsseln eingegeben werden. Die Hash Tabelle kann auch einen optionalen moduleversion-Schlüssel aufweisen. Der moduelist-Schlüssel ist so konzipiert, dass er als Modul bestand fungiert. Diese Module werden nicht automatisch verarbeitet.|
|FileList<br /><br /> Type: [String []]|@()|Liste aller mit diesem Modul verpackten Dateien. Wie bei modulelist ist FileList, Sie als Inventarliste zu unterstützen, und wird andernfalls nicht verarbeitet.|
|PrivateData<br /><br /> Type: [Object]|@{...}|Gibt alle privaten Daten an, die an das Stamm Modul übergeben werden müssen, das durch den Schlüssel rootmodule/moduletoprocess angegeben wird.|
|HelpInfoURI<br /><br /> Typ: Zeichenfolge|' '|Helpinfo-URI dieses Moduls.|
|DefaultCommandPrefix<br /><br /> Typ: Zeichenfolge|' '|Standard Präfix für Befehle, die von diesem Modul exportiert werden. Überschreiben Sie das Standard Präfix mithilfe `Import-Module`-Präfix.|

## <a name="sample-module-manifest"></a>Beispielmodul Manifest

Im folgenden Beispielmodul Manifest werden die Schlüssel und die Standardwerte in einem Modul Manifest angezeigt. Dieses Beispiel wurde mit dem Cmdlet "`New-ModuleManifest`" in Windows PowerShell 3,0 erstellt. Wenn Sie mehrere Module erstellen, können Sie mit diesem Cmdlet eine Manifest-Vorlage erstellen, die dann für verschiedene Module geändert werden kann.

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 2019-10-09
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'b888e5a2-8578-4c0b-938d-0cd9b5b836ba'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2019 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of Microsoft .NET Framework required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module.
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no functions to export.
FunctionsToExport = @()

# Cmdlets to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no cmdlets to export.
CmdletsToExport = @()

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no aliases to export.
AliasesToExport = @()

# DSC resources to export from this module
# DscResourcesToExport = @()

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{

    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Moduls](./writing-a-windows-powershell-module.md)
