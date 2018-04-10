---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 43b26426a76b6503a83e35ae0c02a0af69902ed6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="declare-base-class"></a><span data-ttu-id="a556b-102">Deklarieren der Basisklasse</span><span class="sxs-lookup"><span data-stu-id="a556b-102">Declare Base Class</span></span>
<span data-ttu-id="a556b-103">Sie können eine Windows PowerShell-Klasse als Basistyp für eine andere Windows PowerShell-Klasse deklarieren.</span><span class="sxs-lookup"><span data-stu-id="a556b-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

<span data-ttu-id="a556b-104">Sie können auch vorhandene .NET Framework-Typen als Basisklassen verwenden:</span><span class="sxs-lookup"><span data-stu-id="a556b-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```