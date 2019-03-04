---
title: Platzieren der Kommentarbasierten Hilfe in Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857946"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="62b7e-102">Ablegen der kommentarbasierten Hilfe in Funktionen</span><span class="sxs-lookup"><span data-stu-id="62b7e-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="62b7e-103">In diesem Thema wird erläutert, befehlsbasierte Hilfe für eine Funktion zu platzieren, damit die `Get-Help` Cmdlet ordnet die ordnungsgemäße Funktion das Kommentar-basierte Hilfethema.</span><span class="sxs-lookup"><span data-stu-id="62b7e-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="62b7e-104">Kommentarbasierte Hilfe für eine Funktion platzieren</span><span class="sxs-lookup"><span data-stu-id="62b7e-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="62b7e-105">Zu Beginn des Funktionstexts.</span><span class="sxs-lookup"><span data-stu-id="62b7e-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="62b7e-106">Am Ende der Hauptteil der Funktion.</span><span class="sxs-lookup"><span data-stu-id="62b7e-106">At the end of the function body.</span></span>

- <span data-ttu-id="62b7e-107">Bevor Sie die `Function` Schlüsselwort.</span><span class="sxs-lookup"><span data-stu-id="62b7e-107">Before the `Function` keyword.</span></span> <span data-ttu-id="62b7e-108">Wenn die Funktion in einem Skript oder das Modul "Script" ist, gibt es nicht mehr als eine Leerzeile zwischen der letzten Zeile der kommentarbasierten Hilfe und die `Function` Schlüsselwort.</span><span class="sxs-lookup"><span data-stu-id="62b7e-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="62b7e-109">Andernfalls `Get-Help` ordnet die Hilfe, mit dem Skript, nicht mit der Funktion.</span><span class="sxs-lookup"><span data-stu-id="62b7e-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="62b7e-110">Beispiele für die Platzierung von Hilfe in einer Funktion</span><span class="sxs-lookup"><span data-stu-id="62b7e-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="62b7e-111">Die folgenden Beispiele zeigen jeweils der der drei Platzierungsoptionen für die kommentarbasierte Hilfe für eine Funktion.</span><span class="sxs-lookup"><span data-stu-id="62b7e-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="62b7e-112">Am Anfang eines Funktionsrumpfs-Hilfe</span><span class="sxs-lookup"><span data-stu-id="62b7e-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="62b7e-113">Das folgende Beispiel zeigt Kommentar-basierte, am Anfang eines Funktionsrumpfs.</span><span class="sxs-lookup"><span data-stu-id="62b7e-113">The following example shows comment-based at the beginning of a function body.</span></span>

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

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="62b7e-114">Am Ende eines Funktionsrumpfs-Hilfe</span><span class="sxs-lookup"><span data-stu-id="62b7e-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="62b7e-115">Das folgende Beispiel zeigt die am Ende eines Funktionsrumpfs Kommentar-basierte.</span><span class="sxs-lookup"><span data-stu-id="62b7e-115">The following example shows comment-based at the end of a function body.</span></span>

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

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="62b7e-116">Helfen Sie vor dem Function-Schlüsselwort</span><span class="sxs-lookup"><span data-stu-id="62b7e-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="62b7e-117">Die folgenden Beispiele zeigen Kommentar-basierte, auf die Zeile vor dem Function-Schlüsselwort.</span><span class="sxs-lookup"><span data-stu-id="62b7e-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```