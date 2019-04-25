---
title: 'Gewusst wie: Schreiben Sie ein PowerShell-Modulmanifest | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 93a8c11099a9883127bca87422e1acaebfd2c093
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082295"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>Schreiben eines PowerShell-Binärmoduls

Einmal haben Sie Ihre Windows PowerShell-Modul geschrieben, Sie optional ein modulmanifest hinzufügen können. Ein modulmanifest ist ein PowerShell-Skriptdatei, die Sie verwenden können, um Informationen über das Modul einzuschließen. Sie können z. B. den Autor zu beschreiben, geben Sie Dateien in das Modul (z. B. geschachtelte Module), Ausführen von Skripts zum Anpassen der Umgebung des Benutzers, Typ und Formatierungsdateien geladen, definieren die Systemanforderungen und begrenzen die Elemente, die das Modul exportiert.

## <a name="creating-a-module-manifest"></a>Erstellen ein Modulmanifest

Ein *modulmanifest* ist eine Windows PowerShell-Datendatei (. psd1), die den Inhalt eines Moduls beschreibt und bestimmt, wie ein Modul verarbeitet wird. Die manifest-Datei selbst ist eine Textdatei, die eine Hashtabelle mit Schlüsseln und Werten enthält. Sie verknüpfen eine Manifestdatei auf ein Modul, indem identisch mit dem Modul benennen, und diese im Stammverzeichnis des Modulverzeichnisses.

Für einfache Module, die nur einen einzigen. psm1 oder eine binäre Assembly enthalten, ist ein modulmanifest optional. Allerdings empfiehlt es sich, dass Sie ein modulmanifest nach Möglichkeit verwenden, wie sie Ihren Code zu organisieren und Verwalten von zeilenversionsverwaltungs-Informationen nützlich sind. Darüber hinaus ist ein modulmanifest erforderlich, um eine Assembly zu exportieren, die im globalen Assemblycache installiert ist. Ein modulmanifest ist auch erforderlich, damit die Module, die die aktualisierbare Hilfefunktion unterstützen. D. h. der aktualisierbaren Hilfe verwendet die **HelpInfoUri** -Schlüssels im modulmanifest die hilfeinformationsdatei (HelpInfo XML) zu finden, die den Speicherort der aktualisierten Hilfedateien für das Modul enthält. Weitere Informationen zur aktualisierbaren Hilfe finden Sie unter [unterstützen aktualisierbarer Hilfe](./supporting-updatable-help.md).

### <a name="to-create-and-use-a-module-manifest"></a>Erstellen und verwenden ein modulmanifest

1. Um ein modulmanifest zu erstellen, haben Sie mehrere Optionen:

   1. Direkt erstellt die Hashtabelle mit den minimal erforderlichen Informationen ein, und speichern Sie sie in einer psd1-Datei, die den gleichen Namen wie Ihr Modul verfügt. Sobald Sie dies getan haben, können Sie öffnen Sie die Datei und die entsprechenden Werte manuell hinzufügen.

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. Oder rufen Sie die [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) -Cmdlet mit einem oder mehreren der Standardwerte als Parameter übergeben. (Beachten Sie, dass die nur der Namen der Datei erforderlich, um ein Manifest zu generieren, jedoch ist.) Dadurch wird ein modulmanifest erstellt, mit allen die modulmanifest-Werte, die Sie angegeben explizit angegeben und mit dem Rest mit den entsprechenden Standardwert.

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. Schließlich können Sie auch erstellen eine leere psd1-Datei, und kopieren Sie die Vorlage unten in diesem Thema in der Datei und geben Sie die relevanten Werte. Die einzige wirkliche Anforderung wäre in diesem Fall stellen Sie sicher, dass die Datei, die das Modul identisch benannt wurde.

2. Das Manifest, das Sie auch in der Datei in dem alle zusätzlichen Elemente hinzugefügt.

   Im Allgemeinen ist dies wahrscheinlich in den Text-Editor erfolgen, die Sie bevorzugen, können Sie z. B. Editor. Jedoch ist dies technisch gesehen eine Skriptdatei, die Code enthält, damit Sie es in einer tatsächlichen scripting oder Entwicklungsumgebung, z. B. den PowerShell-ISE bearbeiten möchten. In diesem Fall Beachten Sie, dass alle Elemente einer Manifestdatei optional, mit Ausnahme der ModuleVersion-Anzahl.

   Beschreibungen der Schlüssel und Werte, die Sie in einem modulmanifest haben können, finden Sie unter den **Modul Manifest Elemente** unten. Weitere Informationen finden Sie unter den parameterbeschreibungen in der [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) Cmdlet.

3. Optional können Sie zusätzlichen Code hinzufügen, um Ihre modulmanifest ist für alle Szenarien, die nicht durch die Manifestdatei Basismodul-Elemente behandelt werden würde.

   Aus Gründen der Sicherheit wird PowerShell nur eine kleine Teilmenge der verfügbaren Vorgänge in eine modulmanifestdatei ausgeführt. Im Allgemeinen können Sie die **Wenn** -Anweisung, arithmetische Operatoren und Vergleichsoperatoren und die grundlegende PowerShell-Datentypen.

4. Nachdem Sie Ihre modulmanifest erstellt haben, können Sie testen (um zu bestätigen, dass alle Pfade, die in den Manifesten sind beschrieben korrigieren) mit einem Aufruf von [Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest).

   `Test-ModuleManifest myModuleName.psd1`

5. Achten Sie darauf, dass Ihre modulmanifest in der obersten Ebene des Verzeichnisses befindet, die Ihr Modul enthält.

   Beim Kopieren des Moduls auf einem System und importieren, werden PowerShell modulmanifest verwenden, um Ihr Modul zu importieren.

6. Optional können Sie direkt testen, Ihre modulmanifest mit einem Aufruf von [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) von Dot-quellentnahme das Manifest selbst.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Modul-Manifest-Elemente

Die folgende Tabelle beschreibt die Elemente, was in einem modulmanifest man

|Element|Standardwert|Beschreibung|
|-------------|-------------|-----------------|
|RootModule<br /><br /> Typ: Zeichenfolge|' '|Modul "oder" Binary skriptmoduldatei dieses Manifest zugeordnet. Frühere Versionen von PowerShell wird dieses Element die "moduletoprocess" aufgerufen.<br /><br /> Mögliche Typen für das stammmodul können leer sein (die dies veranlasst einen **Manifest** Modul), den Namen des ein Skriptmodul (. psm1, wodurch dies eine **Skript** Modul), oder der Name eines binären Moduls (.exe oder .dll, Das macht dies eine **binäre** Modul). Platzieren den Namen des ein modulmanifest (psd1) oder eine Skriptdatei (ps1) in diesem Element bewirkt, dass einen Fehler auftritt.|
|ModuleVersion<br /><br /> Typ: Zeichenfolge|1.0|Die Versionsnummer dieses Moduls. Die Zeichenfolge muss in [System.Version] konvertiert werden können. D.h., ' #. #. #. #. #'. `Import-Module` Lädt das erste Modul, das es in findet der **$psModulePath** , die mit dem Namen übereinstimmt, und verfügt über mindestens so hoch ein moduleversion-Schlüssel als die `-MinimumVersion` Parameter. Um eine bestimmte Version zu importieren, verwenden Sie die`-RequiredVersion` Parameter stattdessen.<br /><br /> Beispiel: `ModuleVersion = '1.0'`|
|GUID<br /><br /> Typ: Zeichenfolge|Automatisch generierte GUID|Die ID zur eindeutigen Identifizierung dieses Modul verwendet. Beachten Sie, dass derzeit Importieren eines Moduls GUID nicht möglich.<br /><br /> Beispiel: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|Autor<br /><br /> Typ: Zeichenfolge|Keine|Der Autor dieses Moduls.<br /><br /> Beispiel: `Author = 'AuthorNameHere'`|
|CompanyName<br /><br /> Typ: Zeichenfolge|Unbekannt|Unternehmen oder den Hersteller dieses Moduls.<br /><br /> Beispiel: `CompanyName = 'Fabrikam'`|
|Copyright<br /><br /> Typ: Zeichenfolge|(c) [CurrentYear] [Autor]. Alle Rechte vorbehalten.|Urheberrechtserklärung für dieses Modul.<br /><br /> Beispiel: `Copyright = '2016 AuthorName. All rights reserved.'`|
|Beschreibung<br /><br /> Typ: Zeichenfolge|' '|Beschreibung der von diesem Modul bereitgestellten Funktionen.<br /><br /> Beispiel: `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> Typ: Zeichenfolge|' '|Die Mindestversion von der Windows PowerShell-Engine, die von diesem Modul erforderlich. Aktuell gültigen Werte sind 1.0, 2.0, 3.0, 4.0 und 5.0.<br /><br /> Beispiel: `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> Typ: Zeichenfolge|' '|Gibt den Namen des Windows PowerShell-Hosts, die vom Modul erforderlich ist. Dieser Name wird von Windows PowerShell bereitgestellt. Um den Namen des Hostprogramms in der Anwendung suchen, geben: `$host.name` .<br /><br /> Beispiel: `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> Typ: Zeichenfolge|' '|Die Mindestversion des Windows PowerShell-Hosts, die von diesem Modul erforderlich.<br /><br /> Beispiel: `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> Typ: Zeichenfolge|' '|Die Mindestversion von Microsoft .NET Framework, die von diesem Modul erforderlich.<br /><br /> Beispiel: `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> Typ: Zeichenfolge|' '|Die Mindestversion von die common Language Runtime (CLR), das von diesem Modul erforderlich.<br /><br /> Beispiel: `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> Typ: Zeichenfolge|' '|Prozessorarchitektur (keiner, X86, Amd64) von diesem Modul erforderlich. Gültige Werte sind x86, AMD64, IA64 und None (unbekannt oder nicht angegeben).<br /><br /> Beispiel: `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> Typ: [String []]|@()|Module, die in der globalen Umgebung vor dem Importieren dieses Modul importiert werden müssen. Dies lädt die Module aufgeführt, es sei denn, sie bereits geladen wurden. (Z. B. möglicherweise einige Module bereits von einem anderen Modul geladen werden.). Es ist auch möglich, an eine bestimmte Version zu laden, indem `RequiredVersion` statt `ModuleVersion`. Bei Verwendung `ModuleVersion` lädt die neueste Version, die mit einem Minimum an die angegebene Version zur Verfügung.<br /><br /> Beispiel: `RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> Beispiel: `RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> Typ: [String []]|@()|Assemblys, die vor dem Importieren dieses Modul geladen werden müssen.<br /><br /> Beachten Sie, dass im Gegensatz zu der RequiredModules, PowerShell die RequiredAssemblies geladen werden, wenn sie nicht bereits geladen sind.|
|ScriptsToProcess<br /><br /> Typ: [String []]|@()|Skript (ps1)-Dateien, die im Sitzungsstatus des Aufrufers ausgeführt werden, wenn das Modul importiert wird. Dies ist möglicherweise die globale Sitzungen, Status oder, bei geschachtelten Modulen, die den Sitzungsstatus eines anderen Moduls. Sie können diese Skripts verwenden, um eine Umgebung vorbereiten, wie Sie ein Anmeldeskript verwenden würden.<br /><br /> Diese Skripts werden ausgeführt, bevor eines der Module, die im Manifest aufgelisteten geladen werden.|
|TypesToProcess<br /><br /> Typ: [Object []]|@()|Geben Sie die Dateien (. ps1xml) geladen werden, wenn Sie dieses Modul zu importieren.|
|FormatsToProcess<br /><br /> Typ: [Object []]|@()|Formatdateien Sie (. ps1xml) geladen werden, wenn Sie dieses Modul zu importieren.|
|NestedModules<br /><br /> Typ: [Object []]|@()|Module, die als geschachtelte Module des Moduls im RootModule / "moduletoprocess" angegebenen importieren.<br /><br /> Hinzufügen einen Modulnamen für dieses Element ist vergleichbar mit einem Aufruf `Import-Module` aus dem Skript oder eine Assembly Code heraus. Der Hauptunterschied besteht darin, dass es leichter ist zu erkennen, was Sie hier in der Manifestdatei laden. Auch wenn ein Modul nicht laden hier, werden Sie noch nicht Ihre tatsächliche Modul geladen haben.<br /><br /> Zusätzlich zu anderen Modulen können Sie auch hier die Skripts (ps1)-Dateien laden. Diese Dateien werden im Rahmen der stammmodul ausgeführt. (Dies entspricht Dot-sourcing das Skript in Ihrem Stammverzeichnis-Modul.)|
|FunctionsToExport<br /><br /> Typ: Zeichenfolge|'*'|Gibt die Funktionen, die das Modul exportiert (Platzhalterzeichen Zeichen sind zulässig), den Sitzungsstatus des Aufrufers an. Standardmäßig werden alle Funktionen exportiert. Sie können diesen Schlüssel verwenden, um die Funktionen einzuschränken, die vom Modul exportiert werden.<br /><br /> Sitzungsstatus des Aufrufers kann es sich um die globale Sitzungen, Status oder, bei geschachtelten Modulen, die den Sitzungsstatus eines anderen Moduls sein. Wenn geschachtelte Module zu verketten, werden alle Funktionen, die durch ein geschachteltes Modul exportiert werden, wenn ein Modul in der Kette die Funktion beschränkt, mit dem Schlüssel "functionstoexport" in den globalen Sitzungsstatus exportiert.<br /><br /> Wenn das Manifest auch Aliase für die Funktionen exportiert, diesen Schlüssel kann Funktionen, deren Aliase aufgeführt sind, werden, im AliasesToExport Schlüssel entfernen, aber dieser Schlüssel kann nicht funktionsaliase zur Liste hinzugefügt.|
|CmdletsToExport<br /><br /> Typ: Zeichenfolge|'*'|Gibt an, die Cmdlets, die das Modul exportiert (Platzhalterzeichen Zeichen sind zulässig). Standardmäßig werden alle Cmdlets exportiert. Sie können diesen Schlüssel verwenden, um die Cmdlets einzuschränken, die vom Modul exportiert werden.<br /><br /> Sitzungsstatus des Aufrufers kann es sich um die globale Sitzungen, Status oder, bei geschachtelten Modulen, die den Sitzungsstatus eines anderen Moduls sein. Wenn Sie geschachtelte Module Verkettung sind, werden alle Cmdlets, die durch ein geschachteltes Modul exportiert werden, wenn ein Modul in der Kette das-Cmdlet beschränkt, mit dem Schlüssel CmdletsToExport letztendlich auf den globalen Sitzungsstatus exportiert.<br /><br /> Wenn das Manifest auch Aliase für die Cmdlets exportiert, diesen Schlüssel kann Cmdlets, deren Aliasnamen aufgelistet sind, im AliasesToExport Schlüssel entfernen, aber dieser Schlüssel kann nicht das Cmdlet-Aliase zur Liste hinzufügen.|
|VariablesToExport<br /><br /> Typ: Zeichenfolge|'*'|Gibt die Variablen, die das Modul exportiert (Platzhalterzeichen Zeichen sind zulässig), den Sitzungsstatus des Aufrufers an. Standardmäßig werden alle Variablen exportiert. Sie können diesen Schlüssel verwenden, um die Variablen einzuschränken, die vom Modul exportiert werden.<br /><br /> Sitzungsstatus des Aufrufers kann es sich um die globale Sitzungen, Status oder, bei geschachtelten Modulen, die den Sitzungsstatus eines anderen Moduls sein. Wenn Sie geschachtelte Module Verkettung sind, werden alle Variablen, die durch ein geschachteltes Modul exportiert werden, wenn ein Modul in der Kette der Variablen beschränkt, mit dem Schlüssel VariablesToExport auf den globalen Sitzungsstatus exportiert.<br /><br /> Wenn das Manifest auch Aliase für Variablen exportiert, diesen Schlüssel kann Variablen, deren Aliasnamen aufgelistet sind, im AliasesToExport Schlüssel entfernen, aber dieser Schlüssel kann nicht Variable Aliase zur Liste hinzugefügt.|
|AliasesToExport<br /><br /> Typ: Zeichenfolge|'*'|Gibt die Aliase, die das Modul exportiert (Platzhalterzeichen Zeichen sind zulässig), den Sitzungsstatus des Aufrufers an. Standardmäßig werden alle Aliase exportiert. Sie können diesen Schlüssel verwenden, um die Aliase einzuschränken, die vom Modul exportiert werden.<br /><br /> Sitzungsstatus des Aufrufers kann es sich um die globale Sitzungen, Status oder, bei geschachtelten Modulen, die den Sitzungsstatus eines anderen Moduls sein. Wenn Sie geschachtelte Module Verkettung sind, werden alle Aliase, die durch ein geschachteltes Modul exportiert werden, wenn ein Modul in der Kette den Alias beschränkt, mit dem Schlüssel AliasesToExport letztendlich auf den globalen Sitzungsstatus exportiert.|
|ModuleList<br /><br /> Typ: [String []]|@()|Gibt alle Module, die verpackt werden mit diesem Modul an. Diese Module können anhand des Namens (eine durch Trennzeichen getrennte Zeichenfolge) oder als eine Hashtabelle mit Schlüsseln von ModuleName "und" GUID eingegeben werden. Die Hashtabelle kann außerdem einen optionalen ModuleVersion-Schlüssel haben. Der Schlüssel ModuleList dient, die als eine Inventur Modul fungiert. Diese Module werden nicht automatisch verarbeitet.|
|Dateiliste<br /><br /> Typ: [String []]|@()|Liste aller Dateien, die mit diesem Modul verpackt. Als mit ModuleList, FileList ist, die Sie als eine Inventarliste zu unterstützen, und andernfalls nicht verarbeitet.|
|PrivateData<br /><br /> Typ: [Objekt]|' '|Gibt alle privaten Daten, die für das stammmodul durch den RootModule / "moduletoprocess"-Schlüssel angegebene übergeben werden müssen.|
|HelpInfoURI<br /><br /> Typ: Zeichenfolge|' '|HelpInfo-URI dieses Moduls.|
|DefaultCommandPrefix<br /><br /> Typ: Zeichenfolge|' '|Das Standardpräfix für Befehle, die aus diesem Modul exportiert werden. Überschreiben der Standard-Präfix mit `Import-Module` -Präfix.|

## <a name="sample-module-manifest"></a>Beispiel-Modulmanifest

Das folgende Beispiel modulmanifest zeigt die Schlüssel und die Standardwerte in einem modulmanifest an. In diesem Beispiel wurde mithilfe der `New-ModuleManifest` Cmdlets in Windows PowerShell 3.0. Wenn Sie mehrere Module zu erstellen, können Sie dieses Cmdlet verwenden, um Manifestvorlage zu erstellen, die für unterschiedliche Module anschließend geändert werden können.

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 1/24/2012
#

@{

# Script module or binary module file associated with this manifest
#RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = 'd0a9150d-b6a4-4b17-a325-e3a24fed0aa9'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2012 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of the .NET Framework required by this module
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module
FunctionsToExport = '*'

# Cmdlets to export from this module
CmdletsToExport = '*'

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module
AliasesToExport = '*'

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess
# PrivateData = ''

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Moduls](./writing-a-windows-powershell-module.md)
