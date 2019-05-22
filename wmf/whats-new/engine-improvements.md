---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Verbesserungen an der PowerShell-Engine in WMF 5.1
ms.openlocfilehash: a0af702832c0a90c994650e25918ecacdc33fc4b
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855455"
---
# <a name="powershell-engine-improvements"></a>Verbesserungen an der PowerShell-Engine

Die folgenden Verbesserungen an der PowerShell-Kern-Engine wurden in WMF 5.1 implementiert:

## <a name="performance"></a>Leistung

In einigen wichtigen Bereichen wurde die Leistung verbessert:

- Start
- Das Pipelining bei Cmdlets wie `ForEach-Object` und `Where-Object` erfolgt etwa 50 % schneller.

Einige Beispiele für Verbesserungen (die Ergebnisse variieren je nach Hardware):

| Szenario | Zeit (ms) in 5.0 | Zeit (ms) in 5.1 |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Erste Ausführung von PowerShell überhaupt: `powershell -command "Unknown-Command"` | 30.000 | 13.000 |
| Erstellung des Caches für die Befehlsanalyse: `powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |

> [!NOTE]
> Eine Änderung im Zusammenhang mit dem Start kann sich möglicherweise auf einige (nicht unterstützte) Szenarien auswirken. PowerShell liest nicht mehr die Dateien des Typs `$pshome\*.ps1xml`. Diese Dateien wurden in C# konvertiert, um den Datei- und CPU-Overhead beim Verarbeiten der XML-Dateien zu reduzieren. Die Dateien sind zur Unterstützung der parallelen Verwendung von Version 2 noch vorhanden. Wenn Sie also den Inhalt der Dateien ändern, hat dies keine Auswirkung auf Version 5, sondern nur auf Version 2. Beachten Sie, dass das Ändern dieser Dateien zu keiner Zeit ein unterstütztes Szenario war.

Eine andere sichtbare Änderung ist, wie PowerShell die exportierten Befehle und andere Informationen für Module zwischenspeichert, die auf einem System installiert sind. Zuvor wurde dieser Cache im Verzeichnis `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis` gespeichert. In WMF 5.1 befindet sich der Cache ausschließlich in der Datei `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`. Unter [Die Datei „ModuleAnalysisCache“](release-notes.md#module-analysis-cache) finden Sie weitere Details.