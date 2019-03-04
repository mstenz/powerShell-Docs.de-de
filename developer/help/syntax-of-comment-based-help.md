---
title: Syntax für die Kommentarbasierte Hilfe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855546"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="e755a-102">Syntax der kommentarbasierten Hilfe</span><span class="sxs-lookup"><span data-stu-id="e755a-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="e755a-103">Dieser Abschnitt beschreibt die Syntax für die kommentarbasierte Hilfe.</span><span class="sxs-lookup"><span data-stu-id="e755a-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="e755a-104">Syntaxdiagramm</span><span class="sxs-lookup"><span data-stu-id="e755a-104">Syntax Diagram</span></span>

 <span data-ttu-id="e755a-105">Die Syntax für die kommentarbasierte Hilfe wird wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="e755a-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="e755a-106">Syntaxbeschreibung</span><span class="sxs-lookup"><span data-stu-id="e755a-106">Syntax Description</span></span>

 <span data-ttu-id="e755a-107">Kommentarbasierte Hilfe wird als eine Reihe von Kommentaren geschrieben.</span><span class="sxs-lookup"><span data-stu-id="e755a-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="e755a-108">Können Sie ein Kommentarsymbol (#) vor jeder Zeile der Kommentare eingeben, oder Sie können die "\<#" und "#>" Symbole, erstellen Sie einen Kommentarblock.</span><span class="sxs-lookup"><span data-stu-id="e755a-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="e755a-109">Alle Zeilen in den Kommentarblock, die als Kommentare interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="e755a-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="e755a-110">Jeder Abschnitt kommentarbasierte Hilfe wird definiert, indem ein Schlüsselwort aus, und jedes Schlüsselwort wird durch einen Punkt (.) vorangestellt.</span><span class="sxs-lookup"><span data-stu-id="e755a-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="e755a-111">Die Schlüsselwörter können in beliebiger Reihenfolge angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e755a-111">The keywords can appear in any order.</span></span> <span data-ttu-id="e755a-112">Die Namen von Schlüsselwörtern werden nicht beachtet.</span><span class="sxs-lookup"><span data-stu-id="e755a-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="e755a-113">Kommentarblock muss mindestens ein Hilfeschlüsselwort enthalten.</span><span class="sxs-lookup"><span data-stu-id="e755a-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="e755a-114">Einige der Schlüsselwörter, wie BEISPIELSWEISE können oft in demselben Kommentarblock angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e755a-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="e755a-115">Der Inhalt der Hilfe für jedes Schlüsselwort in der Zeile nach dem Schlüsselwort beginnt und kann mehrere Zeilen umfassen.</span><span class="sxs-lookup"><span data-stu-id="e755a-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="e755a-116">Alle Zeilen in einem Hilfethema befehlsbasierte müssen zusammenhängend sein.</span><span class="sxs-lookup"><span data-stu-id="e755a-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="e755a-117">Wenn ein Kommentar-basierte Hilfethema einen Kommentar, der nicht Teil des Hilfethemas ist folgt, muss mindestens eine Leerzeile zwischen der letzten Kommentarzeile des nicht-Help-und dem Beginn der kommentarbasierten Hilfe vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="e755a-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="e755a-118">Im folgende Kommentar-basierte Hilfethema enthält beispielsweise die. Description-Schlüsselwort und der Wert, das eine Beschreibung einer Funktion oder ein Skript.</span><span class="sxs-lookup"><span data-stu-id="e755a-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```