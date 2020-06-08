---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Verwenden von Erweiterung mit der TAB-TASTE
ms.openlocfilehash: d96cbf848f464aff29a7bed9b70d0b6a000aa808
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438271"
---
# <a name="using-tab-expansion"></a>Verwenden von Erweiterung mit der TAB-TASTE

Befehlszeilenshells bieten häufig eine Möglichkeit, die Namen langer Dateien oder Befehle automatisch zu vervollständigen, wodurch die Befehlseingabe und das Bereitstellen von Hinweisen beschleunigt werden. PowerShell ermöglicht Ihnen das Ausfüllen von Dateinamen und Cmdletnamen durch Drücken der <kbd>TAB-TASTE</kbd>.

> [!NOTE]
> Die Erweiterung mit der TAB-TASTE wird durch die interne Funktion „TabExpansion“ oder „TabExpansion2“ gesteuert. Da diese Funktion geändert oder überschrieben werden kann, ist diese Erläuterung eine Anleitung für das Verhalten der Standardkonfiguration von PowerShell.

Soll ein Dateiname oder Pfad automatisch aus den verfügbaren Optionen ausgefüllt werden, geben Sie einen Teil des Namens ein, und drücken Sie die <kbd>TAB-TASTE</kbd>. PowerShell erweitert den Namen automatisch entsprechend der ersten gefundenen Übereinstimmung. Durch wiederholtes Drücken der <kbd>TAB-TASTE</kbd> werden alle verfügbaren Optionen durchlaufen.

Für Cmdletnamen funktioniert Erweiterung mit der TAB-TASTE etwas anders. Um Erweiterung mit der TAB-TASTE für einen Cmdletnamen zu verwenden, geben Sie den gesamten ersten Teil des Namens (das Verb) und den darauf folgenden Bindestrich ein. Sie können weitere Zeichen des Namens für eine Teilübereinstimmung eingeben. Wenn Sie beispielsweise `get-co` eingeben und dann die <kbd>TAB-TASTE</kbd> drücken, erweitert PowerShell diese Eingabe automatisch zu dem Cmdlet `Get-Command` (wie Sie sehen, wird auch die Groß-/Kleinschreibung der Buchstaben in die Standardform geändert). Wenn Sie die <kbd>TAB-TASTE</kbd> erneut drücken, ersetzt PowerShell diesen Cmdletnamen durch den einzigen anderen passenden Cmdletnamen, `Get-Content`.

Sie können Erweiterung mit der TAB-TASTE wiederholt in derselben Zeile verwenden. Beispielsweise können Sie die Erweiterung mit der TAB-TASTE für den Namen des Cmdlets `Get-Content` verwenden, indem Sie Folgendes eingeben:

```
PS> Get-Con<Tab>
```

Wenn Sie die <kbd>TAB-TASTE</kbd> drücken, wird der Befehlsname erweitert zu:

```
PS> Get-Content
```

Sie können dann den Pfad zur Protokolldatei für das aktive Setup teilweise eingeben und erneut Erweiterung mit der TAB-TASTE verwenden:

```
PS> Get-Content c:\windows\acts<Tab>
```

Wenn Sie die <kbd>TAB-TASTE</kbd> drücken, wird der Befehlsname erweitert zu:

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> Eine Einschränkung für Erweiterung mit der TAB-TASTE besteht darin, dass Tabulatorzeichen immer als Versuche interpretiert werden, ein Wort zu vervollständigen. Wenn Sie ein Befehlsbeispiel kopieren und in einer PowerShell-Konsole einfügen, sollten Sie sich vergewissern, dass das Beispiel keine Tabulatorzeichen enthält. Andernfalls sind die Ergebnisse unvorhersehbar und entsprechen mit großer Wahrscheinlichkeit nicht dem, was Sie beabsichtigen.
