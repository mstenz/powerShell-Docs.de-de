---
title: Ablegen der kommentarbasierten Hilfe in Funktionen
ms.date: 09/12/2016
ms.openlocfilehash: c7a8f8db6c71fa2ef12aaa4df0f78815626ec8d6
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893202"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="c1e58-102">Ablegen der kommentarbasierten Hilfe in Funktionen</span><span class="sxs-lookup"><span data-stu-id="c1e58-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="c1e58-103">In diesem Thema wird erläutert, wo Sie eine Kommentar basierte Hilfe für eine Funktion platzieren können, damit das `Get-Help` Cmdlet das Kommentar basierte Hilfethema der richtigen Funktion zuordnet.</span><span class="sxs-lookup"><span data-stu-id="c1e58-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="c1e58-104">Speicherort der Kommentar basierten Hilfe für eine Funktion</span><span class="sxs-lookup"><span data-stu-id="c1e58-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="c1e58-105">Am Anfang des Funktions Texts.</span><span class="sxs-lookup"><span data-stu-id="c1e58-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="c1e58-106">Am Ende des Funktions Texts.</span><span class="sxs-lookup"><span data-stu-id="c1e58-106">At the end of the function body.</span></span>

- <span data-ttu-id="c1e58-107">Vor dem- `Function` Schlüsselwort.</span><span class="sxs-lookup"><span data-stu-id="c1e58-107">Before the `Function` keyword.</span></span> <span data-ttu-id="c1e58-108">Wenn sich die Funktion in einem Skript-oder Skript Modul befindet, darf zwischen der letzten Zeile der Kommentar basierten Hilfe und dem-Schlüsselwort nicht mehr als eine Leerzeile vorhanden sein `Function` .</span><span class="sxs-lookup"><span data-stu-id="c1e58-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="c1e58-109">Andernfalls ordnet die `Get-Help` Hilfe dem Skript und nicht der-Funktion zu.</span><span class="sxs-lookup"><span data-stu-id="c1e58-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="c1e58-110">Beispiele für die Platzierung von Hilfe in einer Funktion</span><span class="sxs-lookup"><span data-stu-id="c1e58-110">Examples of Help Placement in a Function</span></span>

<span data-ttu-id="c1e58-111">Die folgenden Beispiele zeigen jede der drei Platzierungs Optionen für die Kommentar basierte Hilfe für eine Funktion.</span><span class="sxs-lookup"><span data-stu-id="c1e58-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="c1e58-112">Hilfe am Anfang eines Funktions Texts</span><span class="sxs-lookup"><span data-stu-id="c1e58-112">Help at the Beginning of a Function Body</span></span>

<span data-ttu-id="c1e58-113">Das folgende Beispiel zeigt einen Kommentar basierten am Anfang eines Funktions Texts.</span><span class="sxs-lookup"><span data-stu-id="c1e58-113">The following example shows comment-based at the beginning of a function body.</span></span>

```powershell
function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}
```

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="c1e58-114">Hilfe am Ende eines Funktions Texts</span><span class="sxs-lookup"><span data-stu-id="c1e58-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="c1e58-115">Das folgende Beispiel zeigt am Ende eines Funktions Texts einen Kommentar basierten Text.</span><span class="sxs-lookup"><span data-stu-id="c1e58-115">The following example shows comment-based at the end of a function body.</span></span>

```powershell
function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}
```

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="c1e58-116">Hilfe vor dem Function-Schlüsselwort</span><span class="sxs-lookup"><span data-stu-id="c1e58-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="c1e58-117">In den folgenden Beispielen wird die Kommentar basierte Zeile vor dem Function-Schlüsselwort gezeigt.</span><span class="sxs-lookup"><span data-stu-id="c1e58-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell
<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}
```
