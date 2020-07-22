---
title: Ablegen der kommentarbasierten Hilfe in Skripts
ms.date: 09/12/2016
ms.openlocfilehash: a3ade6c3138826b924939056b9d1ffb233006d44
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893185"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="b8af2-102">Ablegen der kommentarbasierten Hilfe in Skripts</span><span class="sxs-lookup"><span data-stu-id="b8af2-102">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="b8af2-103">In diesem Thema wird erläutert, wo Sie eine Kommentar basierte Hilfe für ein Skript platzieren können, damit das `Get-Help` Cmdlet das Kommentar basierte Hilfethema Skripts und keine Funktionen zuordnet, die möglicherweise im Skript vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="b8af2-103">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="b8af2-104">Platzieren der Kommentar basierten Hilfe für ein Skript</span><span class="sxs-lookup"><span data-stu-id="b8af2-104">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="b8af2-105">Am Anfang der Skriptdatei.</span><span class="sxs-lookup"><span data-stu-id="b8af2-105">At the beginning of the script file.</span></span>

  <span data-ttu-id="b8af2-106">Der Skript Hilfe kann das Skript nur durch Kommentare und leere Zeilen vorangestellt werden.</span><span class="sxs-lookup"><span data-stu-id="b8af2-106">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="b8af2-107">Am Ende der Skriptdatei.</span><span class="sxs-lookup"><span data-stu-id="b8af2-107">At the end of the script file.</span></span>

  <span data-ttu-id="b8af2-108">Wenn das erste Element im Skript Text (nach der Hilfe) eine Funktionsdeklaration ist, müssen zwischen dem Ende der Skript Hilfe und der Funktionsdeklaration mindestens zwei Leerzeilen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="b8af2-108">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="b8af2-109">Andernfalls wird die Hilfe als Hilfe für die Funktion interpretiert, nicht als Hilfe für das Skript.</span><span class="sxs-lookup"><span data-stu-id="b8af2-109">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="b8af2-110">Beispiele für die Platzierung von Hilfe in einem Skript</span><span class="sxs-lookup"><span data-stu-id="b8af2-110">Examples of Help Placement in a Script</span></span>

<span data-ttu-id="b8af2-111">In den folgenden Beispielen werden die einzelnen Platzierungs Optionen für die Kommentar basierte Hilfe eines Skripts gezeigt.</span><span class="sxs-lookup"><span data-stu-id="b8af2-111">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="b8af2-112">Hilfe zu Beginn eines Skripts</span><span class="sxs-lookup"><span data-stu-id="b8af2-112">Help at the Beginning of a Script</span></span>

<span data-ttu-id="b8af2-113">Das folgende Beispiel zeigt einen Kommentar basierten am Anfang eines Skripts.</span><span class="sxs-lookup"><span data-stu-id="b8af2-113">The following example shows comment-based at the beginning of a script.</span></span>

```powershell
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="b8af2-114">Hilfe am Ende eines Skripts</span><span class="sxs-lookup"><span data-stu-id="b8af2-114">Help at the End of a Script</span></span>

 <span data-ttu-id="b8af2-115">Das folgende Beispiel zeigt am Ende eines Skripts eine Kommentar basierte.</span><span class="sxs-lookup"><span data-stu-id="b8af2-115">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>
```
