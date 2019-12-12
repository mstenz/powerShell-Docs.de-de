---
title: Syntax der Kommentar basierten Hilfe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367759"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="39abf-102">Syntax der kommentarbasierten Hilfe</span><span class="sxs-lookup"><span data-stu-id="39abf-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="39abf-103">In diesem Abschnitt wird die Syntax der Kommentar basierten Hilfe beschrieben.</span><span class="sxs-lookup"><span data-stu-id="39abf-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="39abf-104">Syntax Diagramm</span><span class="sxs-lookup"><span data-stu-id="39abf-104">Syntax Diagram</span></span>

 <span data-ttu-id="39abf-105">Die Syntax für die Kommentar basierte Hilfe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="39abf-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="39abf-106">Syntaxbeschreibung</span><span class="sxs-lookup"><span data-stu-id="39abf-106">Syntax Description</span></span>

 <span data-ttu-id="39abf-107">Die Kommentar basierte Hilfe wird als eine Reihe von Kommentaren geschrieben.</span><span class="sxs-lookup"><span data-stu-id="39abf-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="39abf-108">Sie können ein Kommentar Symbol (#) vor jeder Zeile von Kommentaren eingeben, oder Sie können die Symbole "\<#" und "# >" verwenden, um einen Kommentar Block zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="39abf-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="39abf-109">Alle Zeilen innerhalb des Kommentar Blocks werden als Kommentare interpretiert.</span><span class="sxs-lookup"><span data-stu-id="39abf-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="39abf-110">Jeder Abschnitt der Kommentar basierten Hilfe wird durch ein Schlüsselwort definiert, und jedem Schlüsselwort wird ein Punkt (.) vorangestellt.</span><span class="sxs-lookup"><span data-stu-id="39abf-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="39abf-111">Die Schlüsselwörter können in beliebiger Reihenfolge angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="39abf-111">The keywords can appear in any order.</span></span> <span data-ttu-id="39abf-112">Beim Schlüsselwort Namen wird die Groß-/Kleinschreibung nicht beachtet.</span><span class="sxs-lookup"><span data-stu-id="39abf-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="39abf-113">Ein Kommentar Block muss mindestens ein Hilfe Schlüsselwort enthalten.</span><span class="sxs-lookup"><span data-stu-id="39abf-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="39abf-114">Einige der Schlüsselwörter (z. b. beispielsweise) können mehrmals im gleichen Kommentar Block vorkommen.</span><span class="sxs-lookup"><span data-stu-id="39abf-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="39abf-115">Der Hilfe Inhalt für jedes Schlüsselwort beginnt in der Zeile nach dem-Schlüsselwort und kann sich über mehrere Zeilen erstrecken.</span><span class="sxs-lookup"><span data-stu-id="39abf-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="39abf-116">Alle Zeilen in einem Kommentar basierten Hilfethema müssen zusammenhängend sein.</span><span class="sxs-lookup"><span data-stu-id="39abf-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="39abf-117">Wenn ein Kommentar basiertes Hilfethema einem Kommentar folgt, der nicht Teil des Hilfe Themas ist, muss mindestens eine Leerzeile zwischen der letzten nicht-Hilfe Kommentarzeile und dem Anfang der Kommentar basierten Hilfe vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="39abf-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="39abf-118">Beispielsweise enthält das folgende Kommentar basierte Hilfethema die. Description-Schlüsselwort und sein Wert, eine Beschreibung einer Funktion oder eines Skripts.</span><span class="sxs-lookup"><span data-stu-id="39abf-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```