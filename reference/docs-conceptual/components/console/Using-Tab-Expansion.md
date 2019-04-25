---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Verwenden von Erweiterung mit der TAB-TASTE
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: 3d047bf0691c8a304d7637aa50fba6ae99709a82
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086934"
---
# <a name="using-tab-expansion"></a>Verwenden von Erweiterung mit der TAB-TASTE

Befehlszeilenshells bieten häufig eine Möglichkeit, die Namen langer Dateien oder Befehle automatisch zu vervollständigen, wodurch die Eingabe und das Bereitstellen von Befehlen beschleunigt werden. Windows PowerShell ermöglicht Ihnen das Ausfüllen von Dateinamen und Cmdletnamen durch Drücken der **TAB-TASTE**.

> [!NOTE]
> Die Erweiterung mit der TAB-TASTE wird durch die interne Funktion „TabExpansion“ oder „TabExpansion2“ gesteuert. Da diese Funktion geändert oder überschrieben werden kann, ist diese Erläuterung eine Anleitung für das Verhalten der Standardkonfiguration von PowerShell.

Soll ein Dateiname oder Pfad automatisch aus den verfügbaren Optionen ausgefüllt werden, geben Sie einen Teil des Namens ein, und drücken Sie die **TAB-TASTE**. PowerShell erweitert den Namen automatisch entsprechend der ersten gefundenen Übereinstimmung. Durch wiederholtes Drücken der **TAB-TASTE** werden alle verfügbaren Optionen durchlaufen.

Für Cmdletnamen funktioniert Erweiterung mit der TAB-TASTE etwas anders. Um Erweiterung mit der TAB-TASTE für einen Cmdletnamen zu verwenden, geben Sie den gesamten ersten Teil des Namens (das Verb) und den darauf folgenden Bindestrich ein. Sie können weitere Zeichen des Namens für eine Teilübereinstimmung eingeben. Wenn Sie beispielsweise **get-co** eingeben und dann die **TAB-TASTE** drücken, erweitert PowerShell diese Eingabe automatisch zu dem Cmdlet **Get-Command** (wie Sie sehen, wird auch die Groß-/Kleinschreibung der Buchstaben in die Standardform geändert). Wenn Sie die **TAB-TASTE** erneut drücken, ersetzt PowerShell diesen Cmdletnamen durch den einzigen anderen passenden Cmdletnamen, **Get-Content**.

Sie können Erweiterung mit der TAB-TASTE wiederholt in derselben Zeile verwenden. Beispielsweise können Sie Erweiterung mit der TAB-TASTE für den Namen des Cmdlets **Get-Content** verwenden, indem Sie Folgendes eingeben:

```
PS> Get-Con<Tab>
```

Wenn Sie die **TAB-TASTE** drücken, wird der Befehlsname erweitert zu:

```
PS> Get-Content
```

Sie können dann den Pfad zur Protokolldatei für das aktive Setup teilweise eingeben und erneut Erweiterung mit der TAB-TASTE verwenden:

```
PS> Get-Content c:\windows\acts<Tab>
```

Wenn Sie die **TAB-TASTE** drücken, wird der Befehlsname erweitert zu:

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> Eine Einschränkung für Erweiterung mit der TAB-TASTE besteht darin, dass Tabulatorzeichen immer als Versuche interpretiert werden, ein Wort zu vervollständigen. Wenn Sie ein Befehlsbeispiel kopieren und in einer PowerShell-Konsole einfügen, sollten Sie sich vergewissern, dass das Beispiel keine Tabulatorzeichen enthält. Andernfalls sind die Ergebnisse unvorhersehbar und entsprechen mit großer Wahrscheinlichkeit nicht dem, was Sie beabsichtigen.