---
title: Schreiben eines PowerShell-Modul Manifests | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/16/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 4aa6c020cf0e82a4ffcad6f6c7540688d3369aa6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72561282"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>Schreiben eines PowerShell-Modul Manifests

Nachdem Sie das PowerShell-Modul geschrieben haben, können Sie ein optionales Modul Manifest hinzufügen, das Informationen über das Modul enthält. Sie können z. b. den Autor beschreiben, Dateien im Modul angeben (z. b. in Form von Netz Modulen), Skripts ausführen, um die Benutzerumgebung anzupassen, den Auslastungstyp und die Formatierungs Dateien zu definieren, Systemanforderungen zu definieren und die vom Modul exportierte Member einzuschränken.

## <a name="creating-a-module-manifest"></a>Erstellen eines Modul Manifests

Ein **Modul Manifest** ist eine PowerShell-Datendatei (`.psd1`), die den Inhalt eines Moduls beschreibt und bestimmt, wie ein Modul verarbeitet wird. Bei der Manifest-Datei handelt es sich um eine Textdatei, die eine Hash Tabelle mit Schlüsseln und Werten enthält. Sie verknüpfen eine Manifest-Datei mit einem Modul, indem Sie das Manifest mit dem Modul benennen und das Manifest im Stammverzeichnis des Moduls speichern.

Für einfache Module, die nur ein einzelnes `.psm1` oder eine binäre Assembly enthalten, ist ein Modul Manifest optional. Es wird jedoch empfohlen, nach Möglichkeit ein Modul Manifest zu verwenden, da Sie hilfreich sind, um den Code zu organisieren und Versionsinformationen zu verwalten. Außerdem ist ein Modul Manifest erforderlich, um eine Assembly zu exportieren, die im [globalen Assemblycache](/dotnet/framework/app-domains/gac)installiert ist. Ein Modul Manifest ist auch für Module erforderlich, die die aktualisierbare Hilfe Funktion unterstützen. Bei der aktualisierbaren Hilfe wird die **helpinfouri** -Taste im Modul Manifest verwendet, um die Hilfe Informationsdatei (helpinfo XML) zu suchen, die den Speicherort der aktualisierten Hilfedateien für das Modul enthält. Weitere Informationen zur aktualisierbaren Hilfe finden Sie [unter unterstützen der aktualisierbaren Hilfe](./supporting-updatable-help.md).

### <a name="to-create-and-use-a-module-manifest"></a>So erstellen und verwenden Sie ein Modul Manifest

1. Die bewährte Vorgehensweise zum Erstellen eines Modul Manifests ist die Verwendung des [New-modulemanifest-](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) Cmdlets. Mit Parametern können Sie einen oder mehrere Standardschlüssel und-Werte des Manifests angeben. Die einzige Anforderung besteht darin, die Datei zu benennen. `New-ModuleManifest` erstellt ein Modul Manifest mit den angegebenen Werten und schließt die restlichen Schlüssel und deren Standardwerte ein. Wenn Sie mehrere Module erstellen müssen, verwenden Sie `New-ModuleManifest`, um eine Modul Manifest-Vorlage zu erstellen, die für die verschiedenen Module geändert werden kann. Ein Beispiel für ein Standardmodul Manifest finden Sie im Beispiel [Modul Manifest](#sample-module-manifest).

   `New-ModuleManifest -Path C:\myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   Eine Alternative besteht darin, die Hash Tabelle des Modul Manifests mithilfe der minimalen erforderlichen Informationen, der **moduleversion**, manuell zu erstellen. Speichern Sie die Datei mit dem gleichen Namen wie das Modul, und verwenden Sie die Dateierweiterung `.psd1`. Anschließend können Sie die Datei bearbeiten und die entsprechenden Schlüssel und Werte hinzufügen.

1. Fügen Sie alle weiteren Elemente hinzu, die Sie in der Manifest-Datei wünschen.

   Um die Manifest-Datei zu bearbeiten, verwenden Sie einen beliebigen Texteditor, den Sie bevorzugen. Die Manifest-Datei ist jedoch eine Skriptdatei, die Code enthält, sodass Sie Sie in einer Skript-oder Entwicklungsumgebung wie Visual Studio Code bearbeiten möchten. Alle Elemente einer Manifest-Datei sind optional, mit Ausnahme der **moduleversion** -Nummer.

   Beschreibungen der Schlüssel und Werte, die Sie in ein Modul Manifest einschließen können, finden Sie in der Tabelle [Modul Manifest-Elemente](#module-manifest-elements) . Weitere Informationen finden Sie in den Beschreibungen der Parameter im Cmdlet " [New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) ".

1. Um Szenarios zu berücksichtigen, die möglicherweise nicht von den Manifest-Elementen des Basismoduls abgedeckt werden, haben Sie die Möglichkeit, dem Modul Manifest zusätzlichen Code hinzuzufügen.

   Aus Sicherheitsgründen führt PowerShell nur eine kleine Teilmenge der verfügbaren Vorgänge in einer Modul Manifest-Datei aus. Im Allgemeinen können Sie die `if`-Anweisung, arithmetische Operatoren und Vergleichs Operatoren sowie die grundlegenden PowerShell-Datentypen verwenden.

1. Nachdem Sie das Modul Manifest erstellt haben, können Sie es testen, um sicherzustellen, dass alle im Manifest beschriebenen Pfade korrekt sind. Verwenden Sie [Test-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest), um das Modul Manifest zu testen.

   `Test-ModuleManifest myModuleName.psd1`

1. Stellen Sie sicher, dass sich das Modul Manifest auf der obersten Ebene des Verzeichnisses befindet, das das Modul enthält.

   Wenn Sie das Modul auf ein System kopieren und es importieren, verwendet PowerShell das Modul Manifest, um das Modul zu importieren.

1. Optional können Sie das Modul Manifest direkt mit einem [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) -Befehl überprüfen, indem Sie das Manifest selbst durch die Punkt Ermittlung abrufen.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Modul Manifest-Elemente

In der folgenden Tabelle werden die Elemente beschrieben, die in einem Modul Manifest enthalten sein können.

|Element|Standardwert|Description|
|-------------|-------------|-----------------|
|**RootModule**<br /> Typ: `String`|`<empty string>`|Skript Modul oder binäre Modul Datei, die diesem Manifest zugeordnet ist. In früheren Versionen von PowerShell wurde dieses Element als " **moduletoprocess**" bezeichnet.<br /> Mögliche Typen für das Stamm Modul können leer sein, wodurch ein **Manifest** -Modul, der Name eines Skript Moduls (`.psm1`) oder der Name eines binären Moduls (`.exe` oder `.dll`) erstellt wird. Wenn Sie den Namen eines Modul Manifests (`.psd1`) oder einer Skriptdatei (`.ps1`) in diesem Element platzieren, wird ein Fehler verursacht. <br /> Beispiel: `RootModule = 'ScriptModule.psm1'`|
|**ModuleVersion**<br /> Typ: `Version`|`'0.0.1'`|Versionsnummer dieses Moduls. Wenn kein Wert angegeben ist, verwendet `New-ModuleManifest` den Standardwert. Die Zeichenfolge muss in den-Typ konvertieren können `Version` z. b. `#.#.#.#.#`. `Import-Module` lädt das erste Modul, das auf dem **$PSModulePath** gefunden wird, das mit dem Namen übereinstimmt, und verfügt mindestens über eine " **moduleversion**" als **Minimum Version** -Parameter. Um eine bestimmte Version zu importieren, verwenden Sie den Parameter "Requirements **dversion** " des `Import-Module` Cmdlets.<br /> Beispiel: `ModuleVersion = '1.0'`|
|**GUID**<br /> Typ: `GUID`|`'<GUID>'`|ID, die zur eindeutigen Identifizierung dieses Moduls verwendet wird. Wenn kein Wert angegeben ist, generiert `New-ModuleManifest` automatisch den Wert. Ein Modul kann zurzeit nicht nach **GUID**importiert werden. <br /> Beispiel: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|**Autor**<br /> Typ: `String`|`'<Current user>'`|Autor dieses Moduls. Wenn kein Wert angegeben ist, wird `New-ModuleManifest` den aktuellen Benutzer verwendet. <br /> Beispiel: `Author = 'AuthorNameHere'`|
|**CompanyName**<br /> Typ: `String`|`'Unknown'`|Unternehmen oder Hersteller dieses Moduls. Wenn kein Wert angegeben ist, verwendet `New-ModuleManifest` den Standardwert.<br /> Beispiel: `CompanyName = 'Fabrikam'`|
|**Copyright**<br /> Typ: `String`|`'(c) <Author>. All rights reserved.'`| Copyright-Anweisung für dieses Modul. Wenn kein Wert angegeben ist, verwendet `New-ModuleManifest` den Standardwert mit dem aktuellen Benutzer als `<Author>`. Um einen Autor anzugeben, verwenden Sie den **Author** -Parameter. <br /> Beispiel: `Copyright = '2019 AuthorName. All rights reserved.'`|
|**Beschreibung**<br /> Typ: `String`|`<empty string>`|Beschreibung der von diesem Modul bereitgestellten Funktionalität.<br /> Beispiel: `Description = 'This is the module's description.'`|
|**PowerShellVersion**<br /> Typ: `Version`|`<empty string>`|Mindestens erforderliche Version der PowerShell-Engine, die für dieses Modul erforderlich ist. Gültige Werte sind 1,0, 2,0, 3,0, 4,0, 5,0, 5,1, 6 und 7.<br /> Beispiel: `PowerShellVersion = '5.0'`|
|**Powershellhostname**<br /> Typ: `String`|`<empty string>`|Der Name des PowerShell-Hosts, der von diesem Modul benötigt wird. Dieser Name wird von PowerShell bereitgestellt. Um den Namen eines Host Programms zu suchen, geben Sie im Programm Folgendes ein: `$host.name`.<br /> Beispiel: `PowerShellHostName = 'ConsoleHost'`|
|**Powershellhostversion**<br /> Typ: `Version`|`<empty string>`|Mindestens erforderliche Version des PowerShell-Hosts, die von diesem Modul benötigt wird.<br /> Beispiel: `PowerShellHostVersion = '2.0'`|
|**Dotnetframeworkversion**<br /> Typ: `Version`|`<empty string>`|Mindestens erforderliche Version Microsoft .NET Frameworks, die von diesem Modul benötigt wird. Diese Voraussetzung gilt nur für die PowerShell-Desktop Edition, z. b. PowerShell 5,1.<br /> Beispiel: `DotNetFrameworkVersion = '3.5'`|
|**CLRVersion**<br /> Typ: `Version`|`<empty string>`|Die für dieses Modul erforderliche Mindestversion des Common Language Runtime (CLR). Diese Voraussetzung gilt nur für die PowerShell-Desktop Edition, z. b. PowerShell 5,1.<br /> Beispiel: `CLRVersion = '3.5'`|
|**ProcessorArchitecture**<br /> Typ: `ProcessorArchitecture`|`<empty string>`|Die Prozessorarchitektur (None, x86, amd64), die für dieses Modul erforderlich ist. Gültige Werte sind x86, amd64, arm, ia64, MSIL und None (unbekannt oder nicht angegeben).<br /> Beispiel: `ProcessorArchitecture = 'x86'`|
|**RequiredModules**<br /> Typ: `Object[]`|`@()`|Module, die vor dem Importieren dieses Moduls in die globale Umgebung importiert werden müssen. Dadurch werden alle aufgeführten Module geladen, sofern Sie nicht bereits geladen wurden. Einige Module könnten beispielsweise bereits durch ein anderes Modul geladen worden sein. Es ist möglich, eine bestimmte Version anzugeben, die mit `RequiredVersion` anstatt `ModuleVersion`geladen werden soll. Wenn `ModuleVersion` verwendet wird, wird die neueste Version geladen, die mindestens mit der angegebenen Version verfügbar ist. Sie können Zeichenfolgen und Hashtabellen im Parameterwert kombinieren.<br /> Beispiel: `RequiredModules = @("MyModule", @{ModuleName="MyDependentModule"; ModuleVersion="2.0"; GUID="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /> Beispiel: `RequiredModules = @("MyModule", @{ModuleName="MyDependentModule"; RequiredVersion="1.5"; GUID="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|**Requirements dassemblys**<br /> Typ: `String[]`|`@()`|Assemblys, die vor dem Importieren dieses Moduls geladen werden müssen. Gibt die Dateinamen der Assembly (`.dll`) an, die das Modul benötigt.<br /> PowerShell lädt die angegebenen Assemblys vor dem Aktualisieren von Typen oder Formaten, dem Importieren von geschbten Modulen oder dem Importieren der Modul Datei, die im Wert des rootmodule-Schlüssels angegeben ist. Verwenden Sie diesen Parameter, um alle Assemblys aufzulisten, die das Modul erfordert.<br /> Beispiel: `RequiredAssemblies = @("assembly1.dll", "assembly2.dll", "assembly3.dll")`|
|**ScriptsToProcess**<br /> Typ: `String[]`|`@()`|Skriptdateien (`.ps1`), die im Sitzungszustand des Aufrufers ausgeführt werden, wenn das Modul importiert wird. Dabei kann es sich um den globalen Sitzungs Status oder, bei genetzten Modulen, um den Sitzungszustand eines anderen Moduls handeln. Sie können diese Skripts verwenden, um eine Umgebung so vorzubereiten, wie Sie ein Skript für die Anmeldung verwenden können.<br /> Diese Skripts werden ausgeführt, bevor eines der im Manifest aufgelisteten Module geladen wird. <br /> Beispiel: `ScriptsToProcess = @("script1.ps1", "script2.ps1", "script3.ps1")`|
|**Typestoprocess**<br /> Typ: `String[]`|`@()`|Geben Sie beim Importieren dieses Moduls Dateien (`.ps1xml`) ein, die geladen werden sollen. <br /> Beispiel: `TypesToProcess = @("type1.ps1xml", "type2.ps1xml", "type3.ps1xml")`|
|**Formatstoprocess**<br /> Typ: `String[]`|`@()`|Format Dateien (`.ps1xml`), die beim Importieren dieses Moduls geladen werden. <br /> Beispiel: `FormatsToProcess = @("format1.ps1xml", "format2.ps1xml", "format3.ps1xml")`|
|**NestedModules**<br /> Typ: `Object[]`|`@()`|Module, die als geclusterte Module des Moduls importiert werden sollen, das in **rootmodule** (alias:**moduletoprocess**) angegeben ist.<br /> Das Hinzufügen eines Modulnamens zu diesem Element ähnelt dem Aufrufen von `Import-Module` innerhalb Ihres Skripts oder Assemblycodes. Der Hauptunterschied bei der Verwendung einer Manifestressource besteht darin, dass Sie leichter erkennen können, was Sie gerade laden. Wenn ein Modul nicht geladen werden kann, haben Sie das eigentliche Modul noch nicht geladen.<br /> Zusätzlich zu anderen Modulen können Sie auch Skriptdateien (`.ps1`) hier laden. Diese Dateien werden im Kontext des root-Moduls ausgeführt. Dies entspricht der Punkt Ermittlung des Skripts in ihrem Stamm Modul. <br /> Beispiel: `NestedModules = @("script.ps1", @{ModuleName="MyModule"; ModuleVersion="1.0.0.0"; GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"})`|
|**"Functionstoexport"**<br /> Typ: `String[]`|`@()`|Gibt die Funktionen an, die aus diesem Modul exportiert werden sollen. um eine optimale Leistung zu erzielen, verwenden Sie keine Platzhalter, und löschen Sie den Eintrag nicht. verwenden Sie ein leeres Array, wenn keine zu exportierenden Funktionen vorhanden sind. Standardmäßig werden keine Funktionen exportiert. Sie können diesen Schlüssel verwenden, um die Funktionen aufzulisten, die vom Modul exportiert werden.<br /> Das Modul exportiert die Funktionen in den Sitzungszustand des Aufrufers. Der Sitzungszustand des Aufrufers kann der globale Sitzungs Status oder, bei einem anderen Modul, der Sitzungszustand eines anderen Moduls sein. Beim Verketten von geschachtelte-Modulen werden alle Funktionen, die von einem geschachtelte-Modul exportiert werden, in den globalen Sitzungszustand exportiert, es sei denn, ein Modul in der Kette schränkt die Funktion mit dem **functionstoexport** -Schlüssel ein.<br /> Wenn das Manifest Aliase für die Funktionen exportiert, kann dieser Schlüsselfunktionen entfernen, deren Aliase im Schlüssel " **aliasestoexport** " aufgeführt sind, aber dieser Schlüssel kann der Liste keine Funktions Aliase hinzufügen. <br /> Beispiel: `FunctionsToExport = @("function1", "function2", "function3")`|
|**"Cmdletstoexport"**<br /> Typ: `String[]`|`@()`|Gibt die Cmdlets an, die aus diesem Modul exportiert werden sollen. um eine optimale Leistung zu erzielen, verwenden Sie keine Platzhalter, und löschen Sie den Eintrag nicht. verwenden Sie ein leeres Array, wenn keine zu exportierenden Cmdlets vorhanden sind. Standardmäßig werden keine Cmdlets exportiert. Mit diesem Schlüssel können Sie die Cmdlets auflisten, die vom Modul exportiert werden.<br /> Der Sitzungszustand des Aufrufers kann der globale Sitzungs Status oder, bei einem anderen Modul, der Sitzungszustand eines anderen Moduls sein. Beim Verketten von geschachtelte-Modulen werden alle Cmdlets, die von einem geschachtelte-Modul exportiert werden, in den globalen Sitzungs Status exportiert, es sei denn, ein Modul in der Kette schränkt das Cmdlet mit dem **cmdletstoexport** -Schlüssel ein.<br /> Wenn das Manifest Aliase für die Cmdlets exportiert, kann dieser Schlüssel Cmdlets entfernen, deren Aliase im Schlüssel " **aliasestoexport** " aufgeführt sind. dieser Schlüssel kann jedoch keine Cmdlet-Aliase zur Liste hinzufügen. <br /> Beispiel: `CmdletsToExport = @("Get-MyCmdlet", "Set-MyCmdlet", "Test-MyCmdlet")`|
|**Variablestoexport**<br /> Typ: `String[]`|`'*'`|Gibt die Variablen an, die das Modul in den Sitzungszustand des Aufrufers exportiert. Platzhalterzeichen sind zulässig. Standardmäßig werden alle Variablen (`'*'`) exportiert. Sie können diesen Schlüssel verwenden, um die Variablen einzuschränken, die vom Modul exportiert werden.<br /> Der Sitzungszustand des Aufrufers kann der globale Sitzungs Status oder, bei einem anderen Modul, der Sitzungszustand eines anderen Moduls sein. Beim Verketten von geschachtelte-Modulen werden alle Variablen, die von einem geschachtelte-Modul exportiert werden, in den globalen Sitzungszustand exportiert, es sei denn, ein Modul in der Kette schränkt die Variable mit dem **variablestoexport** -Schlüssel ein.<br /> Wenn das Manifest auch Aliase für die Variablen exportiert, kann dieser Schlüsselvariablen entfernen, deren Aliase im Schlüssel " **aliasestoexport** " aufgeführt sind, aber dieser Schlüssel kann der Liste keine Variablen Aliase hinzufügen. <br /> Beispiel: `VariablesToExport = @('$MyVariable1', '$MyVariable2', '$MyVariable3')`|
|**AliasesToExport**<br /> Typ: `String[]`|`@()`|Gibt die Aliase an, die aus diesem Modul exportiert werden sollen. um eine optimale Leistung zu erzielen, verwenden Sie keine Platzhalter, und löschen Sie den Eintrag nicht. verwenden Sie ein leeres Array, wenn keine zu exportierenden Aliase vorhanden sind. Standardmäßig werden keine Aliase exportiert. Mit diesem Schlüssel können Sie die Aliase auflisten, die vom Modul exportiert werden.<br /> Das Modul exportiert die Aliase in den Sitzungs Status des Aufrufers. Der Sitzungszustand des Aufrufers kann der globale Sitzungs Status oder, bei einem anderen Modul, der Sitzungszustand eines anderen Moduls sein. Beim Verketten von geschachtelte-Modulen werden alle Aliase, die von einem geschachtelte-Modul exportiert werden, letztendlich in den globalen Sitzungs Status exportiert, es sei denn, ein Modul in der Kette schränkt den Alias mithilfe des **aliasestoexport** -Schlüssels ein. <br /> Beispiel: `AliasesToExport = @("MyAlias1", "MyAlias2", "MyAlias3")`|
|**DscResourcesToExport**<br /> Typ: `String[]`|`@()`|Gibt DSC-Ressourcen an, die aus diesem Modul exportiert werden sollen. Platzhalter sind zulässig. <br /> Beispiel: `DscResourcesToExport = @("DscResource1", "DscResource2", "DscResource3")`|
|**Modulliste**<br /> Typ: `Object[]`|`@()`|Gibt alle Module an, die mit diesem Modul verpackt werden. Diese Module können mithilfe einer durch Trennzeichen getrennten Zeichenfolge oder als Hash Tabelle mit **ModuleName** -und **GUID** -Schlüsseln eingegeben werden. Die Hash Tabelle kann auch einen optionalen **moduleversion** -Schlüssel aufweisen. Der **moduelist** -Schlüssel ist so konzipiert, dass er als Modul bestand fungiert. Diese Module werden nicht automatisch verarbeitet. <br /> Beispiel: `ModuleList = @("SampleModule", "MyModule", @{ModuleName="MyModule"; ModuleVersion="1.0.0.0"; GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"})`|
|**FileList**<br /> Typ: `String[]`|`@()`|Liste aller mit diesem Modul verpackten Dateien. Wie bei **modulelist**ist **FileList** eine Inventur Liste und wird andernfalls nicht verarbeitet. <br /> Beispiel: `FileList = @("File1", "File2", "File3")`|
|**PrivateData**<br /> Typ: `Object`|`@{...}`|Gibt alle privaten Daten an, die an das Stamm Modul übergeben werden müssen, das durch den Schlüssel **rootmodule** (alias: **moduletoprocess**) angegeben wird. **PRIVATEDATA** ist eine Hash Tabelle, die mehrere Elemente umfasst: **Tags**, **licentaruri**, **projecturi**, **iconuri**, **ReleaseNotes**, **Prerelease**, **requirelicenabacceptance**und **externalmoduledependen.** |
|**Tags** <br /> Typ: `String[]` |`@()`| Tags helfen bei der Modul Ermittlung in Online Galerien. <br /> Beispiel: `Tags = "PackageManagement", "PowerShell", "Manifest"`|
|**LicenseUri**<br /> Typ: `Uri` |`<empty string>`| Eine URL zur Lizenz für dieses Modul. <br /> Beispiel: `LicenseUri = 'https://www.contoso.com/license'`|
|**ProjectUri**<br /> Typ: `Uri` |`<empty string>`| Eine URL zur Hauptwebsite für dieses Projekt. <br /> Beispiel: `ProjectUri = 'https://www.contoso.com/project'`|
|**IconUri**<br /> Typ: `Uri` |`<empty string>`| Eine URL zu einem Symbol, das dieses Modul darstellt. <br /> Beispiel: `IconUri = 'https://www.contoso.com/icons/icon.png'`|
|**Releasenotes**<br /> Typ: `String` |`<empty string>`| Gibt die Anmerkungen zu dieser Version des Moduls an. <br /> Beispiel: `ReleaseNotes = 'The release notes provide information about the module.`|
|**Vorab**<br /> Typ: `String` |`<empty string>`| Dieser Parameter wurde in PowerShell 7 hinzugefügt. Eine Vorabversions **Zeichenfolge,** die das Modul als Vorabversion in Online Galerien identifiziert. <br /> Beispiel: `PreRelease = 'This module is a prerelease version.`|
|**RequireLicenseAcceptance**<br /> Typ: `Boolean`|`$true`| Dieser Parameter wurde in PowerShell 7 hinzugefügt. Flag, das angibt, ob das Modul eine explizite Benutzer Akzeptanz für die Installation, Aktualisierung oder Speicherung erfordert. <br /> Beispiel: `RequireLicenseAcceptance = $false`|
|**Externalmoduledependen**<br /> Typ: `String[]` |`@()`| Dieser Parameter wurde in PowerShell 7 hinzugefügt. Eine Liste externer Module, von denen dieses Modul abhängig ist. <br /> Beispiel: `ExternalModuleDependencies =  @("ExtModule1", "ExtModule2", "ExtModule3")`|
|**HelpInfoURI**<br /> Typ: `String`|`<empty string>`|Helpinfo-URI dieses Moduls. <br /> Beispiel: `HelpInfoURI = 'https://www.contoso.com/help'`|
|**DefaultCommandPrefix**<br /> Typ: `String`|`<empty string>`|Standard Präfix für Befehle, die von diesem Modul exportiert werden. Überschreiben Sie das Standard Präfix mithilfe von `Import-Module -Prefix`. <br /> Beispiel: `DefaultCommandPrefix = 'My'`|

## <a name="sample-module-manifest"></a>Beispielmodul Manifest

Das folgende Beispielmodul Manifest wurde mit `New-ModuleManifest` in PowerShell 7 erstellt und enthält die Standardschlüssel und-Werte.

```powershell
#
# Module manifest for module 'SampleModuleManifest'
#
# Generated by: User01
#
# Generated on: 10/15/2019
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '0.0.1'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'b632e90c-df3d-4340-9f6c-3b832646bf87'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the PowerShell host required by this module
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

        # Prerelease string of this module
        # Prerelease = ''

        # Flag to indicate whether the module requires explicit user acceptance for install/update/save
        RequireLicenseAcceptance = $true

        # External dependent modules of this module
        # ExternalModuleDependencies = @()

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}
```

## <a name="see-also"></a>Siehe auch

[about_Comparison_Operators](/powershell/module/microsoft.powershell.core/about/about_comparison_operators)

[about_If](/powershell/module/microsoft.powershell.core/about/about_if)

[Globaler Assemblycache](/dotnet/framework/app-domains/gac)

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[New-ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest)

[Test-ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest)

[Update-ModuleManifest](/powershell/module/powershellget/update-modulemanifest)

[Schreiben eines Windows PowerShell-Moduls](./writing-a-windows-powershell-module.md)
