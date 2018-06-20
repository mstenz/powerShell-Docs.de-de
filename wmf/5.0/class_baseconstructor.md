---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9486fdbaeca66c83551564c76ce47482f77c36b9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225605"
---
# <a name="call-base-class-constructor"></a>Aufrufen des Basisklassenkonstruktors

Um einen Basisklassenkonstruktor aus einer Unterklasse aufzurufen, verwenden Sie das Schlüsselwort **base**:

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

Wenn eine Basisklasse einen Standardkonstruktor (ohne Parameter) hat, können Sie einen expliziten Konstruktoraufruf weglassen:

```powershell
class C : B
{
    C([int]$c) {}
}
```
