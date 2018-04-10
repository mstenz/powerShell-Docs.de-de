---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: Registerkarte „Elemente“ | MSDN
ms.openlocfilehash: 5058253678a4f996b080e43820fee06b35b681f4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="items-tab"></a><span data-ttu-id="57679-103">Registerkarte „Elemente“</span><span class="sxs-lookup"><span data-stu-id="57679-103">Items Tab</span></span>

<span data-ttu-id="57679-104">Die Registerkarte [Elemente](https://www.powershellgallery.com/items) zeigt alle verfügbaren Elemente im PowerShell-Katalog an.</span><span class="sxs-lookup"><span data-stu-id="57679-104">The [Items tab](https://www.powershellgallery.com/items) displays all available items in the PowerShell Gallery.</span></span>

<span data-ttu-id="57679-105">Es gibt verschiedene Möglichkeiten, die Elemente zu filtern, zu sortieren und zu durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="57679-105">There are several ways to filter, sort, and search the items.</span></span>
<span data-ttu-id="57679-106">Um weitere Details zu einem bestimmten Element anzuzeigen, klicken Sie auf das Element.</span><span class="sxs-lookup"><span data-stu-id="57679-106">To see more details about a particular item, click the item.</span></span>

## <a name="filter-by"></a><span data-ttu-id="57679-107">Filtern nach</span><span class="sxs-lookup"><span data-stu-id="57679-107">Filter By</span></span>

<span data-ttu-id="57679-108">Mit der Dropdownliste „Filtern nach“ können Benutzer die Ergebnisse nach folgenden Kriterien filtern:</span><span class="sxs-lookup"><span data-stu-id="57679-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
* <span data-ttu-id="57679-109">Vorabversion einbeziehen</span><span class="sxs-lookup"><span data-stu-id="57679-109">Include Prerelease</span></span>
* <span data-ttu-id="57679-110">Nur stabile</span><span class="sxs-lookup"><span data-stu-id="57679-110">Stable Only</span></span>

<span data-ttu-id="57679-111">Informationen zu „Vorabversion“ und „stabil“ finden Sie im PowerShell-Teamblog unter [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) (Versionsverwaltung von Vorabversionen zu PowerShellGet und dem PowerShell-Katalog hinzugefügt).</span><span class="sxs-lookup"><span data-stu-id="57679-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="57679-112">Mithilfe der Kontrollkästchen unter der Dropdownliste können Benutzer die Ergebnisse nach folgenden Kriterien filtern:</span><span class="sxs-lookup"><span data-stu-id="57679-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
* <span data-ttu-id="57679-113">Elementtypen</span><span class="sxs-lookup"><span data-stu-id="57679-113">Item Types</span></span>
  - <span data-ttu-id="57679-114">Modul</span><span class="sxs-lookup"><span data-stu-id="57679-114">Module</span></span>
  - <span data-ttu-id="57679-115">Skript</span><span class="sxs-lookup"><span data-stu-id="57679-115">Script</span></span>
* <span data-ttu-id="57679-116">Kategorien</span><span class="sxs-lookup"><span data-stu-id="57679-116">Categories</span></span>
  - <span data-ttu-id="57679-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="57679-117">Cmdlet</span></span>
  - <span data-ttu-id="57679-118">DSC-Ressource</span><span class="sxs-lookup"><span data-stu-id="57679-118">DSC Resource</span></span>
  - <span data-ttu-id="57679-119">Funktion</span><span class="sxs-lookup"><span data-stu-id="57679-119">Function</span></span>
  - <span data-ttu-id="57679-120">Rollenfunktion</span><span class="sxs-lookup"><span data-stu-id="57679-120">Role Capability</span></span>
  - <span data-ttu-id="57679-121">Workflow</span><span class="sxs-lookup"><span data-stu-id="57679-121">Workflow</span></span>

<span data-ttu-id="57679-122">Um im PowerShell-Katalog nur Module anzuzeigen, aktivieren Sie unter „Elementtypen“ die Option „Module“.</span><span class="sxs-lookup"><span data-stu-id="57679-122">To see only modules in the PowerShell Gallery, check Module in the Item Types.</span></span>
<span data-ttu-id="57679-123">Um im PowerShell-Katalog nur Skripts anzuzeigen, aktivieren Sie unter „Elementtypen“ die Option „Skript“.</span><span class="sxs-lookup"><span data-stu-id="57679-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Item Types.</span></span>

> [!NOTE]
> <span data-ttu-id="57679-124">Filter sind inklusiv.</span><span class="sxs-lookup"><span data-stu-id="57679-124">Filters are inclusive.</span></span>
> <span data-ttu-id="57679-125">Beispiel: Ein Element, das sowohl Cmdlets als auch Funktionen erhält, wird angezeigt, wenn entweder „Cmdlet“ oder „Funktion“ (oder beides) aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="57679-125">Example: An item containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="57679-126">Wenn nichts davon ausgewählt ist, wird das Element nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="57679-126">If neither are selected, the item will not appear.</span></span>
> <span data-ttu-id="57679-127">Wenn auf ähnliche Weise Kategorien ausgewählt werden, erscheinen nur Elemente, die eine dieser Kategorien enthält.</span><span class="sxs-lookup"><span data-stu-id="57679-127">Similarly, if all categories are selected, only items containing one of those categories will appear.</span></span>
> <span data-ttu-id="57679-128">**Elemente, die zu keiner dieser Kategorie gehören, werden nicht angezeigt.**</span><span class="sxs-lookup"><span data-stu-id="57679-128">**Items that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="57679-129">Sortieren nach</span><span class="sxs-lookup"><span data-stu-id="57679-129">Sort By</span></span>

<span data-ttu-id="57679-130">Mithilfe der Dropdownliste „Sortieren nach“ können Benutzer die Ergebnisse nach folgenden Kriterien filtern:</span><span class="sxs-lookup"><span data-stu-id="57679-130">The Sort By drop-down allows users to sort the results by:</span></span>
* <span data-ttu-id="57679-131">Beliebtheit: Die Beliebtheit wird durch die Anzahl der Downloads bestimmt.</span><span class="sxs-lookup"><span data-stu-id="57679-131">Popularity - Popularity is determined by Download Count</span></span>
* <span data-ttu-id="57679-132">A-Z: Alphabetisch nach Elementname.</span><span class="sxs-lookup"><span data-stu-id="57679-132">A-Z - Alphabetically by item name</span></span>
* <span data-ttu-id="57679-133">Aktuell: Elemente werden in der Reihenfolge der Veröffentlichungsdaten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="57679-133">Recent - Items appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="57679-134">Suchfeld</span><span class="sxs-lookup"><span data-stu-id="57679-134">Search Box</span></span>

<span data-ttu-id="57679-135">Mit dem Suchfeld können Benutzer Elemente nach Schlüsselwort suchen.</span><span class="sxs-lookup"><span data-stu-id="57679-135">The Search Box allows users to search the items on keywords.</span></span>
<span data-ttu-id="57679-136">Weitere Informationen finden Sie unter [Syntax für die Katalogsuche](psgallery_search_syntax.md).</span><span class="sxs-lookup"><span data-stu-id="57679-136">For more information, see [Gallery Search Syntax](psgallery_search_syntax.md).</span></span>