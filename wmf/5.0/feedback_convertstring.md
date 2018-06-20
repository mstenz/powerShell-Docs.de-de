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
# <a name="convert-string"></a>Convert-String
**Convert-String** bietet „magische“ Ersetzungsfunktionalität. Geben Sie „Vorher“- und „Nachher“-Beispiele an, wie Text aussehen soll. Anschließend wird Ihr Text von **Convert-String** automatisch formatiert. Bei der folgenden Demo wird der Vor- und Nachname einer Person gewählt und durch den Nachnamen, ein Komma, den ersten Buchstaben des Vornamens und einen Punkt ersetzt. Probieren Sie es mit einem regulären Ausdruck, und prüfen Sie, wie lange Sie brauchen.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
