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
# <a name="declare-implemented-interface"></a><span data-ttu-id="c3b7a-102">Deklarieren der implementierten Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="c3b7a-102">Declare Implemented Interface</span></span>

<span data-ttu-id="c3b7a-103">Sie können implementierte Schnittstellen nach Basistypen oder unmittelbar nach einem Doppelpunkt (:) deklarieren, wenn kein Basistyp angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="c3b7a-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="c3b7a-104">Trennen Sie alle Typnamen durch Kommas.</span><span class="sxs-lookup"><span data-stu-id="c3b7a-104">Separate all type names by using commas.</span></span> <span data-ttu-id="c3b7a-105">Dies entspricht der C#-Syntax.</span><span class="sxs-lookup"><span data-stu-id="c3b7a-105">It’s very similar to C# syntax.</span></span>

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
