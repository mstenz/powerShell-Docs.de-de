---
title: Grundlegendes zu einem Windows PowerShell-Modul | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: b42ba6b2bf42a74213eb78f2db22e16de7e90583
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360639"
---
# <a name="understanding-a-windows-powershell-module"></a>Grundlegendes zum Windows PowerShell-Modul

Ein *Modul* ist ein Satz verwandter Windows PowerShell-Funktionen, die als bequeme Einheit gruppiert sind (in der Regel in einem einzigen Verzeichnis gespeichert). Wenn Sie einen Satz verwandter Skriptdateien, Assemblys und zugehöriger Ressourcen als Modul definieren, können Sie Ihren Code viel einfacher referenzieren, laden, speichern und freigeben, als andernfalls.

Der Hauptzweck eines Moduls besteht darin, die Modularisierung (IE, Wiederverwendung und Abstraktion) von Windows PowerShell-Code zuzulassen. Die einfachste Methode zum Erstellen eines Moduls ist beispielsweise, ein Windows PowerShell-Skript einfach als psm1-Datei zu speichern. Auf diese Weise können Sie die Funktionen und Variablen, die im Skript enthalten sind, Steuern (d.h. öffentlich oder privat). Wenn Sie das Skript als psm1-Datei speichern, können Sie auch den Bereich bestimmter Variablen steuern. Zum Schluss können Sie auch Cmdlets wie " [Install-Module](/powershell/module/PowershellGet/Install-Module) " verwenden, um Ihr Skript als Bausteine für größere Lösungen zu organisieren, zu installieren und zu verwenden.

## <a name="module-components-and-types"></a>Modulkomponenten und-Typen

Ein Modul besteht aus vier Grundkomponenten:

1. Eine Codedatei (in der Regel entweder ein PowerShell-Skript oder eine verwaltete Cmdlet-Assembly).

2. Alles, was die obige Codedatei benötigt, z. b. zusätzliche Assemblys, Hilfedateien oder Skripts.

3. Eine Manifest-Datei, in der die obigen Dateien beschrieben werden, sowie Metadaten wie Autoren und Versionsinformationen werden gespeichert.

4. Ein Verzeichnis, das den gesamten obigen Inhalt enthält und sich dort befindet, wo PowerShell Sie finden kann.

   Beachten Sie, dass keine dieser Komponenten tatsächlich notwendig ist. Ein Modul kann z. b. technisch gesehen nur ein Skript sein, das in einer psm1-Datei gespeichert ist. Sie können auch ein Modul verwenden, das nichts anderes als eine Manifest-Datei ist, das hauptsächlich für organisatorische Zwecke verwendet wird. Sie können auch ein Skript schreiben, mit dem ein Modul dynamisch erstellt wird. Daher ist es eigentlich nicht erforderlich, in ein Verzeichnis zu speichern. In den folgenden Abschnitten werden die Modultypen beschrieben, die Sie durch das kombinieren und Zuordnen der verschiedenen möglichen Teile eines Moduls erreichen können.

### <a name="script-modules"></a>Skript Module

Wie der Name schon sagt, ist ein *Skript Modul* eine Datei (. psm1), die einen beliebigen gültigen Windows PowerShell-Code enthält. Skriptentwickler und-Administratoren können mit diesem Modultyp Module erstellen, deren Member Funktionen, Variablen und mehr enthalten. Bei einem Skript Modul handelt es sich um ein Windows PowerShell-Skript mit einer anderen Erweiterung, mit der Administratoren Import-, Export-und Verwaltungsfunktionen verwenden können.

Außerdem können Sie eine Manifest-Datei verwenden, um andere Ressourcen in das Modul einzuschließen, z. b. Datendateien, andere abhängige Module oder Lauf Zeit Skripts. Manifestressourcen sind auch nützlich für die Nachverfolgung von Metadaten, wie z. b. das Erstellen von Informationen

Schließlich muss ein Skript Modul, wie ein beliebiges anderes Modul, das nicht dynamisch erstellt wird, in einem Ordner gespeichert werden, der von PowerShell angemessen ermittelt werden kann. Dies erfolgt in der Regel im PowerShell-Modulpfad. bei Bedarf können Sie jedoch explizit beschreiben, wo das Modul installiert ist. Weitere Informationen finden Sie unter Gewusst [wie: Schreiben eines PowerShell-Skript Moduls](./how-to-write-a-powershell-script-module.md).

### <a name="binary-modules"></a>Binäre Module

Ein *binäres Modul* ist eine .NET Framework Assembly (. dll), die kompilierten Code enthält C#, z. b. Cmdlet-Entwickler können diese Art von Modul verwenden, um Cmdlets, Anbieter und vieles mehr gemeinsam zu nutzen. (Vorhandene Snap-Ins können auch als binäre Module verwendet werden.) Im Vergleich zu einem Skript Modul können Sie mit einem binären Modul Cmdlets erstellen, die schneller sind oder Funktionen verwenden (z. b. Multithreading), die in Windows PowerShell-Skripts nicht so einfach zu programmieren sind.

Wie bei Skript Modulen können Sie eine Manifest-Datei einschließen, um zusätzliche Ressourcen zu beschreiben, die das Modul verwendet, und um Metadaten zu Ihrem Modul zu überprüfen. Ebenso sollten Sie das binäre Modul wahrscheinlich in einem Ordner irgendwo im PowerShell-Modulpfad installieren. Weitere Informationen finden Sie unter How to [Write a PowerShell Binary Module](./how-to-write-a-powershell-binary-module.md).

### <a name="manifest-modules"></a>Manifest-Module

Ein *Manifest-Modul* ist ein Modul, das eine Manifest-Datei verwendet, um alle Komponenten zu beschreiben, aber keine Art von Kernassembly oder Skript. (Formal lässt ein Manifest-Modul das `ModuleToProcess`-oder `RootModule`-Element des Manifests leer.) Sie können jedoch weiterhin die anderen Features eines Moduls verwenden, z. b. die Möglichkeit, abhängige Assemblys zu laden oder bestimmte vorab verarbeitete Skripts automatisch auszuführen. Sie können auch ein Manifest-Modul als bequeme Methode zum Verpacken von Ressourcen verwenden, die von anderen Modulen verwendet werden, wie z. b. geschaltete Module, Assemblys, Typen oder Formate. Weitere Informationen finden Sie unter Gewusst [wie: Schreiben eines PowerShell-Modul Manifests](./how-to-write-a-powershell-module-manifest.md).

### <a name="dynamic-modules"></a>Dynamische Module

Ein *dynamisches Modul* ist ein Modul, das nicht aus einer Datei geladen oder in eine Datei gespeichert wird. Stattdessen werden Sie mithilfe des [New-Module-](/powershell/module/Microsoft.PowerShell.Core/New-Module) Cmdlets dynamisch von einem Skript erstellt. Dieser Modultyp ermöglicht einem Skript, bei Bedarf ein Modul zu erstellen, das nicht geladen oder im persistenten Speicher gespeichert werden muss. Ein dynamisches Modul ist naturgemäß kurzlebig und kann daher nicht über das Cmdlet "`Get-Module`" aufgerufen werden. Analog dazu benötigen Sie in der Regel keine Modul Manifeste, und Sie benötigen wahrscheinlich keine permanenten Ordner zum Speichern der zugehörigen Assemblys.

## <a name="module-manifests"></a>Modul Manifeste

Ein *Modul Manifest* ist eine. psd1-Datei, die eine Hash Tabelle enthält. Die Schlüssel und Werte in der Hash Tabelle führen die folgenden Schritte aus:

- Beschreiben Sie den Inhalt und die Attribute des Moduls.

- Definieren Sie die Voraussetzungen.

- Bestimmen Sie, wie die Komponenten verarbeitet werden.

  Manifeste sind für ein Modul nicht erforderlich. Module können auf Skriptdateien (. ps1), Skript Moduldateien (. psm1), Manifest-Dateien (. psd1), Formatierungs-und Typdateien (. ps1xml), Cmdlets und Anbieterassemblys (DLL-Dateien), Ressourcen Dateien, Hilfedateien, Lokalisierungsdateien oder beliebige andere Datei-oder Ressourcentypen verweisen, die wird als Teil des Moduls gebündelt. Für ein internationalisiertes Skript enthält der Modul Ordner auch einen Satz von Nachrichten Katalogdateien. Wenn Sie dem Modul Ordner eine Manifest-Datei hinzufügen, können Sie auf die verschiedenen Dateien als einzelne Einheit verweisen, indem Sie auf das Manifest verweisen.

  Das Manifest selbst beschreibt die folgenden Kategorien von Informationen:

- Metadaten zum Modul, z. b. die Modulversionsnummer, der Autor und die Beschreibung.

- Erforderliche Komponenten zum Importieren des Moduls, wie z. b. die Windows PowerShell-Version, die Common Language Runtime-Version (CLR) und die erforderlichen Module.

- Verarbeitungs Direktiven, wie z. b. die zu verarbeitenden Skripts, Formate und Typen.

- Einschränkungen für die zu exportierenden Member des Moduls, z. b. die Aliase, Funktionen, Variablen und Cmdlets, die exportiert werden sollen.

  Weitere Informationen finden Sie unter Gewusst [wie: Schreiben eines PowerShell-Modul Manifests](./how-to-write-a-powershell-module-manifest.md).

## <a name="storing-and-installing-a-module"></a>Speichern und Installieren eines Moduls

Nachdem Sie ein Skript-, Binär-oder Manifest-Modul erstellt haben, können Sie Ihre Arbeit an einem Speicherort speichern, an dem andere Benutzer darauf zugreifen können. Das Modul kann z. b. im Systemordner gespeichert werden, in dem Windows PowerShell installiert ist, oder es kann in einem Benutzerordner gespeichert werden.

Im Allgemeinen können Sie mithilfe eines der Pfade, die in der `$ENV:PSModulePath`-Variablen gespeichert werden, bestimmen, wo Sie das Modul installieren sollten. Die Verwendung eines dieser Pfade bedeutet, dass PowerShell das Modul automatisch suchen und laden kann, wenn ein Benutzer in seinem Code einen aufzurufenden Vorgang ausführt. Wenn Sie das Modul an einem anderen Speicherort speichern, können Sie PowerShell explizit mitteilen, indem Sie den Speicherort des Moduls als Parameter übergeben, wenn Sie `Install-Module` aufrufen.

Unabhängig davon wird der Pfad des Ordners als *Basis* des Moduls (modulebase) bezeichnet, und der Name der Skript-, Binär-oder Manifest-Modul Datei sollte mit dem Namen des Modul Ordners übereinstimmen, mit den folgenden Ausnahmen:

- Dynamische Module, die mit dem Cmdlet "`New-Module`" erstellt werden, können mit dem Parameter "`Name`" des Cmdlets benannt werden.

- Module, die vom Befehl " **`Import-Module`-Assembly** " aus assemblyobjekten importiert werden, werden gemäß der folgenden Syntax benannt: `"dynamic_code_module_" + assembly.GetName()`.

  Weitere Informationen finden Sie unter [Installieren eines PowerShell-Moduls](./installing-a-powershell-module.md) und [Ändern des psmodulepath-Installations Pfads](./modifying-the-psmodulepath-installation-path.md).

## <a name="module-cmdlets-and-variables"></a>Module-Cmdlets und-Variablen

Die folgenden Cmdlets und Variablen werden von Windows PowerShell zum Erstellen und Verwalten von Modulen bereitgestellt.

[New-Module-](/powershell/module/Microsoft.PowerShell.Core/New-Module) Cmdlet dieses Cmdlet erstellt ein neues dynamisches Modul, das nur im Arbeitsspeicher vorhanden ist. Das Modul wird aus einem Skriptblock erstellt, und seine exportierten Member, z. b. die zugehörigen Funktionen und Variablen, sind in der Sitzung sofort verfügbar und bleiben verfügbar, bis die Sitzung geschlossen wird.

[New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) -Cmdlet: Dieses Cmdlet erstellt eine neue Modul Manifest-Datei (. psd1), füllt ihre Werte auf und speichert die Manifest-Datei im angegebenen Pfad. Dieses Cmdlet kann auch verwendet werden, um eine Modul Manifest-Vorlage zu erstellen, die manuell ausgefüllt werden kann.

Cmdlet " [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) ": Dieses Cmdlet fügt der aktuellen Sitzung ein oder mehrere Module hinzu.

[Get-Module-](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet dieses Cmdlet ruft Informationen über die Module ab, die in die aktuelle Sitzung importiert wurden oder importiert werden können.

[Export-modulemember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) -Cmdlet dieses Cmdlet gibt die Modulmember (z. b. Cmdlets, Funktionen, Variablen und Aliase) an, die aus einer Skript Modul Datei (. psm1) oder aus einem dynamischen Modul exportiert werden, das mit dem Cmdlet "`New-Module`" erstellt wurde.

Cmdlet " [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) ": Dieses Cmdlet entfernt Module aus der aktuellen Sitzung.

[Test-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) -Cmdlet dieses Cmdlet überprüft, ob ein Modul Manifest die Komponenten eines Moduls genau beschreibt, indem überprüft wird, ob die in der Modul Manifest-Datei (. psd1) aufgeführten Dateien tatsächlich in den angegebenen Pfaden vorhanden sind.

$PSScriptRoot diese Variable das Verzeichnis enthält, aus dem das Skript Modul ausgeführt wird. Sie ermöglicht es Skripts, den Modulpfad für den Zugriff auf andere Ressourcen zu verwenden.

$ENV:P smodulepath diese Umgebungsvariable enthält eine Liste der Verzeichnisse, in denen Windows PowerShell-Module gespeichert werden. Windows PowerShell verwendet den Wert dieser Variablen beim automatischen Importieren von Modulen und zum Aktualisieren der Hilfe Themen für Module.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Moduls](./writing-a-windows-powershell-module.md)
