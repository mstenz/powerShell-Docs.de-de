---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Verwenden von Erweiterung mit der TAB-TASTE
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: c158e544d79bf6010690160eea71630a1981e8a5
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="using-tab-expansion"></a><span data-ttu-id="34a2e-103">Verwenden von Erweiterung mit der TAB-TASTE</span><span class="sxs-lookup"><span data-stu-id="34a2e-103">Using Tab Expansion</span></span>
<span data-ttu-id="34a2e-104">Befehlszeilenshells bieten häufig eine Möglichkeit, die Namen langer Dateien oder Befehle automatisch zu vervollständigen, wodurch die Befehlseingabe und das Bereitstellen von Hinweisen beschleunigt werden.</span><span class="sxs-lookup"><span data-stu-id="34a2e-104">Command-line shells often provide a way to complete the names of long files or commands automatically, speeding up command entry and providing hints.</span></span> <span data-ttu-id="34a2e-105">Windows PowerShell ermöglicht Ihnen das Ausfüllen von Dateinamen und Cmdletnamen durch Drücken der **TAB-TASTE**.</span><span class="sxs-lookup"><span data-stu-id="34a2e-105">Windows PowerShell allows you to fill in file names and cmdlet names by pressing the **Tab** key.</span></span>

> [!NOTE]
> <span data-ttu-id="34a2e-106">Die Erweiterung mit der TAB-TASTE wird durch die interne Funktion „TabExpansion“ oder „TabExpansion2“ gesteuert.</span><span class="sxs-lookup"><span data-stu-id="34a2e-106">Tab expansion is controlled by the internal function TabExpansion or TabExpansion2.</span></span> <span data-ttu-id="34a2e-107">Da diese Funktion geändert oder überschrieben werden kann, ist diese Erläuterung eine Anleitung für das Verhalten der Standardkonfiguration von Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="34a2e-107">Since this function can be modified or overridden, this discussion is a guide to the behavior of the default Windows PowerShell configuration.</span></span>

<span data-ttu-id="34a2e-108">Soll ein Dateiname oder Pfad automatisch aus den verfügbaren Optionen ausgefüllt werden, geben Sie einen Teil des Namens ein, und drücken Sie die **TAB-TASTE**.</span><span class="sxs-lookup"><span data-stu-id="34a2e-108">To fill in a filename or path from the available choices automatically, type part of the name and press the **Tab** key.</span></span> <span data-ttu-id="34a2e-109">Windows PowerShell erweitert den Namen automatisch entsprechend der ersten gefundenen Übereinstimmung.</span><span class="sxs-lookup"><span data-stu-id="34a2e-109">Windows PowerShell will automatically expand the name to the first match that it finds.</span></span> <span data-ttu-id="34a2e-110">Durch wiederholtes Drücken der **TAB-TASTE** werden alle verfügbaren Optionen durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="34a2e-110">Pressing the **Tab** key repeatedly will cycle through all of the available choices.</span></span>

<span data-ttu-id="34a2e-111">Für Cmdletnamen funktioniert Erweiterung mit der TAB-TASTE etwas anders.</span><span class="sxs-lookup"><span data-stu-id="34a2e-111">The tab expansion of cmdlet names is slightly different.</span></span> <span data-ttu-id="34a2e-112">Um Erweiterung mit der TAB-TASTE für einen Cmdletnamen zu verwenden, geben Sie den gesamten ersten Teil des Namens (das Verb) und den darauf folgenden Bindestrich ein.</span><span class="sxs-lookup"><span data-stu-id="34a2e-112">To use tab expansion on a cmdlet name, type the entire first part of the name (the verb) and the hyphen that follows it.</span></span> <span data-ttu-id="34a2e-113">Sie können weitere Zeichen des Namens für eine Teilübereinstimmung eingeben.</span><span class="sxs-lookup"><span data-stu-id="34a2e-113">You can fill in more of the name for a partial match.</span></span> <span data-ttu-id="34a2e-114">Wenn Sie beispielsweise **get-co** eingeben und dann die **TAB-TASTE** drücken, erweitert Windows PowerShell diese Eingabe automatisch zu dem Cmdlet **Get-Command** (wie Sie sehen, wird auch die Groß-/Kleinschreibung der Buchstaben in die Standardform geändert).</span><span class="sxs-lookup"><span data-stu-id="34a2e-114">For example, if you type **get-co** and then press the **Tab** key, Windows PowerShell will automatically expand this to the **Get-Command** cmdlet (notice that it also changes the case of letters to their standard form).</span></span> <span data-ttu-id="34a2e-115">Wenn Sie die **TAB-TASTE** erneut drücken, ersetzt Windows PowerShell diesen Cmdletnamen durch den einzigen anderen passenden Cmdletnamen, **Get-Content**.</span><span class="sxs-lookup"><span data-stu-id="34a2e-115">If you press **Tab** key again, Windows PowerShell replaces this with the only other matching cmdlet name, **Get-Content**.</span></span>

<span data-ttu-id="34a2e-116">Sie können Erweiterung mit der TAB-TASTE wiederholt in derselben Zeile verwenden.</span><span class="sxs-lookup"><span data-stu-id="34a2e-116">You can use tab expansion repeatedly on the same line.</span></span> <span data-ttu-id="34a2e-117">Beispielsweise können Sie Erweiterung mit der TAB-TASTE für den Namen des Cmdlets **Get-Content** verwenden, indem Sie Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="34a2e-117">For example, you can use tab expansion on the name of the **Get-Content** cmdlet by entering:</span></span>

```
PS> Get-Con<Tab>
```

<span data-ttu-id="34a2e-118">Wenn Sie die **TAB-TASTE** drücken, wird der Befehlsname erweitert zu:</span><span class="sxs-lookup"><span data-stu-id="34a2e-118">When you press the **Tab** key, the command expands to:</span></span>

```
PS> Get-Content
```

<span data-ttu-id="34a2e-119">Sie können dann den Pfad zur Protokolldatei für das aktive Setup teilweise eingeben und erneut Erweiterung mit der TAB-TASTE verwenden:</span><span class="sxs-lookup"><span data-stu-id="34a2e-119">You can then partially specify the path to the Active Setup log file and use tab expansion again:</span></span>

```
PS> Get-Content c:\windows\acts<Tab>
```

<span data-ttu-id="34a2e-120">Wenn Sie die **TAB-TASTE** drücken, wird der Befehlsname erweitert zu:</span><span class="sxs-lookup"><span data-stu-id="34a2e-120">When you press the **Tab** key, the command expands to:</span></span>

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> <span data-ttu-id="34a2e-121">Eine Einschränkung für Erweiterung mit der TAB-TASTE besteht darin, dass Tabulatorzeichen immer als Versuche interpretiert werden, ein Wort zu vervollständigen.</span><span class="sxs-lookup"><span data-stu-id="34a2e-121">One limitation of the tab expansion process is that tabs are always interpreted as attempts to complete a word.</span></span> <span data-ttu-id="34a2e-122">Wenn Sie ein Befehlsbeispiel kopieren und in einer Windows PowerShell-Konsole einfügen, sollten Sie sich vergewissern, dass das Beispiel keine Tabulatorzeichen enthält. Andernfalls sind die Ergebnisse unvorhersehbar und entsprechen mit großer Wahrscheinlichkeit nicht dem, was Sie beabsichtigen.</span><span class="sxs-lookup"><span data-stu-id="34a2e-122">If you copy and paste command examples into a Windows PowerShell console, make sure that the sample does not contain tabs; if it does, the results will be unpredictable and will almost certainly not be what you intended.</span></span>

