---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 2c007321789ae22b4a2e048d2d64162b065f9a75
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="f56d8-102">Deklarieren der implementierten Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="f56d8-102">Declare Implemented Interface</span></span>

<span data-ttu-id="f56d8-103">Sie können implementierte Schnittstellen nach Basistypen oder unmittelbar nach einem Doppelpunkt (:) deklarieren, wenn kein Basistyp angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="f56d8-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="f56d8-104">Trennen Sie alle Typnamen durch Kommas.</span><span class="sxs-lookup"><span data-stu-id="f56d8-104">Separate all type names by using commas.</span></span> <span data-ttu-id="f56d8-105">Dies entspricht der C#-Syntax.</span><span class="sxs-lookup"><span data-stu-id="f56d8-105">It’s very similar to C# syntax.</span></span>

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