---
title: Platzieren der Kommentarbasierten Hilfe in Skripts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083228"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="ece84-102">Ablegen der kommentarbasierten Hilfe in Skripts</span><span class="sxs-lookup"><span data-stu-id="ece84-102">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="ece84-103">In diesem Thema wird erläutert, befehlsbasierte Hilfe für ein Skript zu platzieren, damit die `Get-Help` Cmdlet ordnet die Kommentar-basierte Hilfethema mit Skripts und alle Funktionen, die in das Skript möglicherweise nicht.</span><span class="sxs-lookup"><span data-stu-id="ece84-103">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="ece84-104">Kommentarbasierte Hilfe für ein Skript zu platzieren</span><span class="sxs-lookup"><span data-stu-id="ece84-104">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="ece84-105">Am Anfang der Skriptdatei.</span><span class="sxs-lookup"><span data-stu-id="ece84-105">At the beginning of the script file.</span></span> <span data-ttu-id="ece84-106">Hilfe zu Skript kann in das Skript nur durch Kommentare und Leerzeichen vorangestellt werden.</span><span class="sxs-lookup"><span data-stu-id="ece84-106">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="ece84-107">Am Ende der Skriptdatei.</span><span class="sxs-lookup"><span data-stu-id="ece84-107">At the end of the script file.</span></span>

  <span data-ttu-id="ece84-108">Wenn das erste Element in der Skripttext (nach der-Hilfe) eine Funktionsdeklaration ist, muss über mindestens zwei Leerzeilen zwischen dem Ende des Skripts Hilfe und die Funktionsdeklaration vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="ece84-108">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="ece84-109">Andernfalls wird die Hilfe als Hilfe bei der Funktion nicht die Hilfe für das Skript interpretiert.</span><span class="sxs-lookup"><span data-stu-id="ece84-109">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="ece84-110">Beispiele für die Platzierung von Hilfe in einem Skript</span><span class="sxs-lookup"><span data-stu-id="ece84-110">Examples of Help Placement in a Script</span></span>

 <span data-ttu-id="ece84-111">Die folgenden Beispiele zeigen die Platzierung-Optionen für die kommentarbasierte Hilfe für ein Skript.</span><span class="sxs-lookup"><span data-stu-id="ece84-111">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="ece84-112">Am Anfang eines Skripts Hilfe</span><span class="sxs-lookup"><span data-stu-id="ece84-112">Help at the Beginning of a Script</span></span>

 <span data-ttu-id="ece84-113">Das folgende Beispiel zeigt Kommentar-basierte, am Anfang eines Skripts.</span><span class="sxs-lookup"><span data-stu-id="ece84-113">The following example shows comment-based at the beginning of a script.</span></span>

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="ece84-114">Am Ende eines Skripts Hilfe</span><span class="sxs-lookup"><span data-stu-id="ece84-114">Help at the End of a Script</span></span>

 <span data-ttu-id="ece84-115">Das folgende Beispiel zeigt die Kommentar-basierte am Ende eines Skripts.</span><span class="sxs-lookup"><span data-stu-id="ece84-115">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```