---
title: Platzieren der Kommentar basierten Hilfe in Functions | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367779"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="deab0-102">Ablegen der kommentarbasierten Hilfe in Funktionen</span><span class="sxs-lookup"><span data-stu-id="deab0-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="deab0-103">In diesem Thema wird erläutert, wo Sie eine Kommentar basierte Hilfe für eine Funktion platzieren können, damit das `Get-Help`-Cmdlet das Kommentar basierte Hilfethema der richtigen Funktion zuordnet.</span><span class="sxs-lookup"><span data-stu-id="deab0-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="deab0-104">Speicherort der Kommentar basierten Hilfe für eine Funktion</span><span class="sxs-lookup"><span data-stu-id="deab0-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="deab0-105">Am Anfang des Funktions Texts.</span><span class="sxs-lookup"><span data-stu-id="deab0-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="deab0-106">Am Ende des Funktions Texts.</span><span class="sxs-lookup"><span data-stu-id="deab0-106">At the end of the function body.</span></span>

- <span data-ttu-id="deab0-107">Vor dem `Function`-Schlüsselwort.</span><span class="sxs-lookup"><span data-stu-id="deab0-107">Before the `Function` keyword.</span></span> <span data-ttu-id="deab0-108">Wenn sich die Funktion in einem Skript-oder Skript Modul befindet, darf zwischen der letzten Zeile der Kommentar basierten Hilfe und dem `Function`-Schlüsselwort nicht mehr als eine Leerzeile vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="deab0-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="deab0-109">Andernfalls ordnet `Get-Help` die Hilfe dem Skript zu, nicht mit der-Funktion.</span><span class="sxs-lookup"><span data-stu-id="deab0-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="deab0-110">Beispiele für die Platzierung von Hilfe in einer Funktion</span><span class="sxs-lookup"><span data-stu-id="deab0-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="deab0-111">Die folgenden Beispiele zeigen jede der drei Platzierungs Optionen für die Kommentar basierte Hilfe für eine Funktion.</span><span class="sxs-lookup"><span data-stu-id="deab0-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="deab0-112">Hilfe am Anfang eines Funktions Texts</span><span class="sxs-lookup"><span data-stu-id="deab0-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="deab0-113">Das folgende Beispiel zeigt einen Kommentar basierten am Anfang eines Funktions Texts.</span><span class="sxs-lookup"><span data-stu-id="deab0-113">The following example shows comment-based at the beginning of a function body.</span></span>

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

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="deab0-114">Hilfe am Ende eines Funktions Texts</span><span class="sxs-lookup"><span data-stu-id="deab0-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="deab0-115">Das folgende Beispiel zeigt am Ende eines Funktions Texts einen Kommentar basierten Text.</span><span class="sxs-lookup"><span data-stu-id="deab0-115">The following example shows comment-based at the end of a function body.</span></span>

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

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="deab0-116">Hilfe vor dem Function-Schlüsselwort</span><span class="sxs-lookup"><span data-stu-id="deab0-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="deab0-117">In den folgenden Beispielen wird die Kommentar basierte Zeile vor dem Function-Schlüsselwort gezeigt.</span><span class="sxs-lookup"><span data-stu-id="deab0-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```