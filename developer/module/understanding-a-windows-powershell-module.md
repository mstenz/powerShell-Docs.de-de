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
ms.openlocfilehash: cff50d415c4c90182fa1cf015a5a5ba84d4d613a
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470786"
---
# <a name="understanding-a-windows-powershell-module"></a>Grundlegendes zum Windows PowerShell-Modul

Ein *Modul* ist ein Satz von zugehörigen Windows PowerShell-Funktionalitäten, die als eine praktische Einheit, die (in der Regel in einem Verzeichnis gespeichert) gruppiert. Definieren Sie einen Satz von entsprechenden Skriptdateien, Assemblys und zugehörigen Ressourcen als ein Modul, können Sie verweisen, laden, speichern und teilen Sie Ihren Code viel einfacher, als würde Sie sonst.

Der Hauptzweck eines Moduls ist, um die modularisierung von Windows PowerShell-Code (z. B. Wiederverwendung und Abstraktion) zu ermöglichen. Beispielsweise ist die einfachste Möglichkeit zum Erstellen eines Moduls, um ein Windows PowerShell-Skript einfach als eine. psm1-Datei zu speichern. Somit können Sie steuern (z. B. öffentlich oder privat) die Funktionen und Variablen im Skript enthalten. Speichern das Skript als. psm1-Datei können Sie auch den Umfang der bestimmten Variablen steuern. Schließlich auch können Cmdlets wie z. B. [Install-Module](/powershell/module/PowershellGet/Install-Module) zum Organisieren, installieren und verwenden Sie das Skript als Bausteine für größere Lösungen.

## <a name="module-components-and-types"></a>Komponenten der Module und Typen

Ein Modul besteht aus vier grundlegenden Komponenten:

1. Einige Sortieren der Codedatei – in der Regel entweder ein PowerShell-Skript oder eine verwaltete Cmdlet-Assembly.

2. Die möglicherweise von den oben angegebenen Codedatei benötigen, z. B. zusätzliche Assemblys, Dateien oder Skripts helfen.

3. Eine Manifestdatei, die beschreibt, der oben genannten Dateien als auch auflisten, z. B. Autor und versionsverwaltung speichert...

4. Ein Verzeichnis, das alle von den oben angegebenen Inhalt enthält, und befindet, in dem PowerShell einigermaßen finden sie.

   Beachten Sie, dass keine dieser Komponenten, und auch wirklich erforderlich sind. Beispielsweise kann ein Modul aus technischer Sicht nur ein Skript in einer psm1-Datei gespeichert sein. Sie können auch ein Modul verwenden, die lediglich eine Manifestdatei wird hauptsächlich für organisatorische Zwecke verwendet wird. Sie können auch ein Skript schreiben, die dynamisch erstellt ein Modul, und daher nicht unbedingt ein Verzeichnis zum Speichern von in. Den folgenden Abschnitten werden die Arten von Modulen, die Sie durch das Mischen und Anpassen von die anderen Teile eines Moduls zusammen abrufen können.

### <a name="script-modules"></a>Script-Module

Wie der Name schon sagt, ein *Skriptmodul* ist eine Datei (. psm1), die alle gültigen Windows PowerShell-Code enthält. Skriptentwickler und Administratoren können diese Art von Modul Module erstellen, deren Member-Funktionen, Variablen usw. enthalten. Im Prinzip ist ein Skriptmodul einfach ein Windows PowerShell-Skript mit einer anderen Erweiterung, die Administratoren ermöglicht, Import, Export und Management-Funktionen auf ihn zu verwenden.

Darüber hinaus können Sie eine Manifestdatei zum Einbeziehen anderer Ressourcen in Ihrem Modul wie z. B. Dateien, andere abhängige Module oder Common Language Runtime-Skripts aus. Manifestdateien sind auch nützlich, für die nachverfolgung von Metadaten wie z. B. Informationen zu erstellen und die versionsverwaltung.

Schließlich muss ein Skriptmodul, wie andere Module, die nicht dynamisch erstellt wird, in einem Ordner gespeichert werden, die relativ PowerShell ermitteln kann. In der Regel ist dies für den Pfad der PowerShell-Modul. aber bei Bedarf Sie können explizit zu beschreiben, wo Ihr Modul installiert ist. Weitere Informationen finden Sie unter [Gewusst wie: Schreiben Sie ein PowerShell-Skriptmodul](./how-to-write-a-powershell-script-module.md).

### <a name="binary-modules"></a>Binäre Module

Ein *binäres Modul* ist .NET Framework-Assembly (.dll), die kompilierten Code, z. B. enthält C#. Cmdlet-Entwickler können diese Art von Modul-Cmdlets, Anbietern und vieles mehr zu teilen. (Vorhandene-Snap-ins kann auch als binäre Module verwendet werden.) Im Vergleich zu einem Skriptmodul, ein binäres Modul ermöglicht Ihnen die Erstellung von Cmdlets, die schneller, oder verwenden Features (z. B. multithreading), die nicht einfach, Code in Windows PowerShell-Skripts sind.

Als können mit Skriptmodule, Sie enthalten eine Manifestdatei, um zusätzliche Ressourcen zu beschreiben, die Ihr Modul verwendet, und klicken Sie zum Nachverfolgen von Metadaten zu Ihrem Modul. Ebenso sollten Sie wahrscheinlich Ihre binäre Modul in einem Ordner an einer beliebigen Stelle entlang des Pfads der PowerShell-Modul installieren. Weitere Informationen finden Sie unter Vorgehensweise [zum Schreiben von einem binären Modul für PowerShell](./how-to-write-a-powershell-binary-module.md).

### <a name="manifest-modules"></a>Manifestmodule

Ein *Manifestmodul* ist ein Modul, das eine Manifestdatei verwendet, um alle zugehörigen Komponenten zu beschreiben, aber keine Art von Core-Assembly oder ein Skript verfügen. (Eine Manifestmodul formal, verlässt der `ModuleToProcess` oder `RootModule` -Element des Manifests leer.) Allerdings weiterhin können Sie die anderen Funktionen eines Moduls, z.B. die Möglichkeit, abhängige Assemblys laden, oder führen automatisch bestimmte vorab verarbeitete Skripts. Sie können auch ein manifest-Modul verwenden, wie eine einfache Möglichkeit, Ressourcen, die andere Module, z. B. geschachtelte Module, Assemblys, Typen oder Formate verwendet werden verpacken. Weitere Informationen finden Sie unter [Gewusst wie: Schreiben eines Modulmanifests PowerShell](./how-to-write-a-powershell-module-manifest.md).

### <a name="dynamic-modules"></a>Dynamische Module

Ein *dynamisches Modul* ist ein Modul, die nicht aus geladen wird, oder in einer Datei gespeichert. Stattdessen werden dynamisch erstellt, durch ein Skript, mit der [New-Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) Cmdlet. Diese Art des Moduls ermöglicht es sich um ein Skript zum Erstellen eines Moduls nach Bedarf, die nicht geladen oder in den permanenten Speicher gespeichert werden muss. Naturgemäß ein dynamisches Modul dient zum kurzlebig sein und aus diesem Grund kann nicht zugegriffen werden, indem die `Get-Module` Cmdlet. Auf ähnliche Weise, in der Regel benötigen keinen modulmanifeste, auch permanente Ordner zum Speichern von ihren zugehörigen Assemblys nicht wahrscheinlich erforderlich.

## <a name="module-manifests"></a>Modulmanifesten

Ein *modulmanifest* ist eine psd1-Datei, die eine Hashtabelle enthält. Die Schlüssel und Werte in der Hashtabelle gehen Sie folgendermaßen vor:

- Beschreiben Sie den Inhalt und die Attribute des Moduls.

- Definieren Sie die erforderlichen Komponenten.

- Bestimmen Sie, wie die Komponenten verarbeitet werden.

  Manifeste sind für ein Modul nicht erforderlich. Module können verweisen auf Skriptdateien (ps1), skriptmoduldateien (psm1), manifest-Dateien (psd1), Formatierung und geben Sie Dateien (. ps1xml), Cmdlets und Anbieter von Assemblys (.dll), Ressourcendateien, Hilfedateien, Lokalisierungsdateien oder einen anderen Typ von Datei oder Ressource, die ist als Teil des Moduls enthalten. Für eine internationale Skript enthält die Ordner "Module" auch einen Satz von Nachrichtendateien-Katalog. Wenn Sie den Ordner "Module" eine Manifestdatei hinzugefügt haben, können Sie mehrere Dateien als einzelne Einheit verweisen, durch einen Verweis auf das Manifest.

  Das Manifest selbst beschreibt die folgenden Kategorien von Informationen an:

- Metadaten über das Modul, wie z. B. die Versionsnummer des Moduls, dem Autor und die Beschreibung.

- Voraussetzungen zum Importieren des Moduls, wie die Windows PowerShell-Version, die Version der common Language Runtime (CLR) und die erforderlichen Module.

- Verarbeitungsrichtlinien, z. B. die Skripts, Formate und -Typen zu verarbeiten.

- Einschränkungen für die Elemente des Moduls zu exportieren, z. B. die Aliase, Funktionen, Variablen und -Cmdlets exportieren.

  Weitere Informationen finden Sie unter [Gewusst wie: Schreiben eines Modulmanifests PowerShell](./how-to-write-a-powershell-module-manifest.md).

## <a name="storing-and-installing-a-module"></a>Speichern und das Installieren eines Moduls

Nachdem Sie ein Skript, Binär- oder manifest-Modul erstellt haben, können Sie Ihre Arbeit an einem Ort speichern, andere darauf zugreifen können. Beispielsweise kann Ihr Modul oder gespeichert werden im Ordner "System", in denen Windows PowerShell installiert ist, können Sie in einem Benutzerordner gespeichert werden.

Im Allgemeinen können Sie bestimmen, in dem Ihr Modul installiert werden soll, mithilfe einer der Pfade gespeichert, der `$ENV:PSModulePath` Variable. Mit einem dieser Pfade also PowerShell automatisch finden und Laden Ihr Modul aus, wenn ein Benutzer es in ihrem Code aufruft. Wenn Sie Ihr Modul, das an anderer Stelle gespeichert werden, explizit lassen Sie PowerShell, wissen übergeben den Speicherort Ihres Moduls als Parameter beim Aufrufen `Install-Module`.

Unabhängig davon, der Pfad des Ordners wird als bezeichnet die *Basis* des Moduls (ModuleBase), und den Namen des Skripts, Binär- oder manifest Moduldatei muss identisch mit dem Modul Ordnernamen ein, mit Ausnahme der folgenden:

- Dynamische Module, die vom erstellten der `New-Module` Cmdlet kann mit benannt werden die `Name` -Parameter des Cmdlets.

- Module, die aus der Assemblyobjekte nach importiert die  **`Import-Module` -Assembly** Befehl entsprechend der folgenden Syntax benannt werden: `"dynamic_code_module_" + assembly.GetName()`.

  Weitere Informationen finden Sie unter [Installieren eines PowerShell-Moduls](./installing-a-powershell-module.md) und [ändern den Installationspfad PSModulePath](./modifying-the-psmodulepath-installation-path.md).

## <a name="module-cmdlets-and-variables"></a>Module-Cmdlets und Variablen

Die folgenden Cmdlets und Variablen werden von Windows PowerShell für die Erstellung und Verwaltung von Modulen bereitgestellt.

[Neues Modul](/powershell/module/Microsoft.PowerShell.Core/New-Module) Cmdlet dieses Cmdlet erstellt ein neues dynamisches Modul, das vorhanden ist nur im Arbeitsspeicher. Das Modul aus einen Skriptblock erstellt wird, und ihre exportierten Member, z. B. Funktionen und Variablen sind in der Sitzung sofort verfügbar und verfügbar bleiben, bis die Sitzung geschlossen wird.

[Neue-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) Cmdlets mit diesem Cmdlet erstellt eine neue Datei des Moduls-modulmanifestdatei (psd1), füllt die Werte und speichert die Manifestdatei in den angegebenen Pfad. Dieses Cmdlet kann auch verwendet werden, Manifestvorlage Modul zu erstellen, die manuell ausgefüllt werden können.

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet dieses Cmdlet Fügt ein oder mehrere Module für die aktuelle Sitzung.

[Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet dieses Cmdlet Ruft Informationen zu den Modulen, die wurden oder in die aktuelle Sitzung importiert werden können.

[Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) Cmdlet dieses Cmdlet gibt die modulmitglieder (z. B. Cmdlets, Funktionen, Variablen und Aliase) an, die aus einer skriptmoduldatei (. psm1) oder aus einem dynamischen Modul, das mithilfe von erstellt exportiert werden die `New-Module` Cmdlet.

[Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) Cmdlets mit diesem Cmdlet werden die Module aus der aktuellen Sitzung entfernt.

[Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) Cmdlet dieses Cmdlet stellt sicher, dass ein modulmanifest die Komponenten eines Moduls genau beschreibt überprüfen Sie, dass die Dateien, die in der modulmanifestdatei (psd1) aufgeführten tatsächlich in den angegebenen Pfaden vorhanden sind.

$PSScriptRoot enthält diese Variable das Verzeichnis, die aus dem Skriptmodul ausgeführt wird. Skripts, um die Modulpfad verwenden, um auf andere Ressourcen zugreifen können.

$env: PSModulePath diese Umgebungsvariable enthält eine Liste der Verzeichnisse in dem das Windows PowerShell Modules gespeichert werden. Windows PowerShell verwendet den Wert dieser Variablen, die beim Importieren von Modulen wird automatisch ein, und aktualisieren die Hilfethemen für Module an.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Moduls](./writing-a-windows-powershell-module.md)
