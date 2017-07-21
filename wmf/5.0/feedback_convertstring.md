---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 6caff8c06174a1dcb990ed8e5062ccca5848dbb8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="convert-string"></a><span data-ttu-id="e4723-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="e4723-102">Convert-String</span></span>
<span data-ttu-id="e4723-103">**Convert-String** bietet „magische“ Ersetzungsfunktionalität.</span><span class="sxs-lookup"><span data-stu-id="e4723-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="e4723-104">Geben Sie „Vorher“- und „Nachher“-Beispiele an, wie Text aussehen soll. Anschließend wird Ihr Text von **Convert-String** automatisch formatiert.</span><span class="sxs-lookup"><span data-stu-id="e4723-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="e4723-105">Bei der folgenden Demo wird der Vor- und Nachname einer Person gewählt und durch den Nachnamen, ein Komma, den ersten Buchstaben des Vornamens und einen Punkt ersetzt.</span><span class="sxs-lookup"><span data-stu-id="e4723-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="e4723-106">Probieren Sie es mit einem regulären Ausdruck, und prüfen Sie, wie lange Sie brauchen.</span><span class="sxs-lookup"><span data-stu-id="e4723-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```

