---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 1fd6d80d6b7effb4bd98c1594d64e531c4e5c9b5
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2017
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

