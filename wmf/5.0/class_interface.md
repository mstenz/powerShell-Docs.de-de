---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 968e78beb8df77588a08a9ce8732e4abcadde4d0
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2017
---
# <a name="declare-implemented-interface"></a>Deklarieren der implementierten Schnittstelle

Sie können implementierte Schnittstellen nach Basistypen oder unmittelbar nach einem Doppelpunkt (:) deklarieren, wenn kein Basistyp angegeben ist. Trennen Sie alle Typnamen durch Kommas. Dies entspricht der C#-Syntax.

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

