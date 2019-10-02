---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Katalog,PowerShell,psgallery
title: Manuelles Herunterladen des Pakets
ms.openlocfilehash: c0a96e866dfd27f9b2170ea540ec6dd0c67701fd
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71327891"
---
# <a name="manual-package-download"></a>Manuelles Herunterladen des Pakets

Der PowerShell-Katalog unterstützt das direkte Herunterladen von Paketen von der Website, ohne dass dazu PowerShellGet-Cmdlets verwendet werden müssen. Sie können jedes Paket als NuGet-Paketdatei (`.nupkg`) herunterladen, die Sie dann in ein internes Repository kopieren können.

> [!NOTE]
> Das manuelle Herunterladen soll **nicht** als Ersatz für das `Install-Module`-Cmdlet dienen.
> Durch das Herunterladen des Pakets werden weder Modul noch Skript installiert. In dem heruntergeladenen NuGet-Paket sind keine Abhängigkeiten enthalten. Die folgenden Anweisungen sollen nur der Referenz dienen.

## <a name="using-manual-download-to-acquire-a-package"></a>Manuelles Herunterladen eines Pakets

Auf jeder Seite gibt es einen Link zum manuellen Download:

![Manueller Download](../../Images/packagedisplaypagewithpseditions.png)

Klicken Sie auf **Download the raw nupkg file** (NUPKG-Rohdatei herunterladen), um das Paket manuell herunterzuladen. Eine Kopie des Pakets mit dem Namen `<name>.<version>.nupkg` wird in den Downloadordner Ihres Browsers heruntergeladen.

Ein NuGet-Paket ist ein ZIP-Archiv mit zusätzlichen Dateien, die Informationen zum Inhalt des Pakets enthalten. Einige Browser, wie z.B. auch Internet Explorer, ersetzen die Erweiterung `.nupkg` automatisch durch `.zip`. Benennen Sie die `.nupkg`-Datei bei Bedarf in eine `.zip`-Datei um, um das Paket zu erweitern, und entpacken Sie dann den Inhalt in einen lokalen Ordner.

Eine NuGet-Paketdatei enthält die folgenden **NuGet-spezifischen Elemente**, die nicht Teil des ursprünglichen gepackten Codes sind:

- Einen Ordner mit dem Namen `_rels`. Dieser enthält eine `.rels`-Datei, in der die Abhängigkeiten aufgelistet sind.
- Einen Ordner mit dem Namen `package`. Dieser enthält NuGet-spezifische Daten.
- Eine Datei mit dem Namen `[Content_Types].xml`. In dieser wird beschrieben, wie Erweiterungen wie PowerShellGet mit NuGet funktionieren.
- Eine Datei mit dem Namen `<name>.nuspec`. Diese enthält die meisten Metadaten.

## <a name="installing-powershell-modules-from-a-nuget-package"></a>Installieren von PowerShell-Modulen aus einem NuGet-Paket

> [!NOTE]
> Diese Schritte führen **nicht** zu dem gleichen Ergebnis wie das Ausführen von `Install-Module`. Diese Anweisungen erfüllen die Mindestanforderungen. Sie sollen nicht als Ersatz für `Install-Module` dienen.
> Einige Schritte, die von `Install-Module` durchgeführt werden, sind nicht vorhanden.

Am unkompliziertesten ist es, die NuGet-spezifischen Elemente aus dem Ordner zu entfernen. Nach dem Entfernen der Elemente bleibt der vom Paketautor erstellte PowerShell-Code übrig.
Eine Liste der NuGet-spezifischen Elemente finden Sie unter [Manuelles Herunterladen eines Pakets](#using-manual-download-to-acquire-a-package).

Das Verfahren besteht aus folgenden Schritten:

1. Entpacken Sie den Inhalt des NuGet-Pakets in einen lokalen Ordner.
2. Löschen Sie die NuGet-spezifischen Elemente aus dem Ordner.
3. Benennen Sie den Ordner um. Der Standardname des Ordners ist für gewöhnlich `<name>.<version>`. Die Version kann `-prerelease` enthalten, wenn das Modul als Vorabversion gekennzeichnet ist. Benennen Sie den Ordner in den Modulnamen um. `azurerm.storage.5.0.4-preview` wird beispielsweise zu `azurerm.storage`.
4. Kopieren Sie den Ordner in einen der Ordner in `$env:PSModulePath value`. `$env:PSModulePath` ist eine durch Semikolons getrennte Reihe von Pfaden, in denen PowerShell nach Modulen suchen soll.

> [!IMPORTANT]
> Beim manuellen Download werden keine Abhängigkeiten heruntergeladen, die für das Modul erforderlich sind. Wenn das Paket über Abhängigkeiten verfügt, müssen diese auf dem System installiert werden, damit das Modul ordnungsgemäß funktioniert. Der PowerShell-Katalog zeigt alle Abhängigkeiten an, die für das Paket erforderlich sind.

## <a name="installing-powershell-scripts-from-a-nuget-package"></a>Installieren von PowerShell-Skripts aus einem NuGet-Paket

> [!NOTE]
> Diese Schritte führen **nicht** zu dem gleichen Ergebnis wie das Ausführen von `Install-Script`. Diese Anweisungen erfüllen die Mindestanforderungen. Sie sollen nicht als Ersatz für `Install-Script` dienen.

Es ist am unkompliziertesten, das NuGet-Paket zu entpacken und das Skript dann direkt zu verwenden.

Das Verfahren besteht aus folgenden Schritten:

1. Entpacken Sie den Inhalt des NuGet-Pakets.
2. Die `.PS1`-Datei im Ordner kann direkt von dort verwendet werden.
3. Sie können die NuGet-spezifischen Elemente aus dem Ordner löschen.

Eine Liste der NuGet-spezifischen Elemente finden Sie unter [Manuelles Herunterladen eines Pakets](#using-manual-download-to-acquire-a-package).

> [!IMPORTANT]
> Beim manuellen Download werden keine Abhängigkeiten heruntergeladen, die für das Modul erforderlich sind. Wenn das Paket über Abhängigkeiten verfügt, müssen diese auf dem System installiert werden, damit das Modul ordnungsgemäß funktioniert. Der PowerShell-Katalog zeigt alle Abhängigkeiten an, die für das Paket erforderlich sind.
