---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7730912707bb14e90a9926b387fb3a859d7ca26d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219265"
---
# <a name="convert-string"></a><span data-ttu-id="9717b-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="9717b-102">Convert-String</span></span>
<span data-ttu-id="9717b-103">**Convert-String** bietet „magische“ Ersetzungsfunktionalität.</span><span class="sxs-lookup"><span data-stu-id="9717b-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="9717b-104">Geben Sie „Vorher“- und „Nachher“-Beispiele an, wie Text aussehen soll. Anschließend wird Ihr Text von **Convert-String** automatisch formatiert.</span><span class="sxs-lookup"><span data-stu-id="9717b-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="9717b-105">Bei der folgenden Demo wird der Vor- und Nachname einer Person gewählt und durch den Nachnamen, ein Komma, den ersten Buchstaben des Vornamens und einen Punkt ersetzt.</span><span class="sxs-lookup"><span data-stu-id="9717b-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="9717b-106">Probieren Sie es mit einem regulären Ausdruck, und prüfen Sie, wie lange Sie brauchen.</span><span class="sxs-lookup"><span data-stu-id="9717b-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
