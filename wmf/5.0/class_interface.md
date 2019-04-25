---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4b593e9a1eca43ee7ad85fc921ae3c1d62722db9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085860"
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
