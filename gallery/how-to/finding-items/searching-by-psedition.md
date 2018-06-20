---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Elemente mit kompatiblen PowerShell-Editionen
ms.openlocfilehash: f661c2cd076acb9c11394ba0b752ebd154965ff4
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189498"
---
# <a name="items-with-compatible-powershell-editions"></a><span data-ttu-id="b1046-103">Elemente mit kompatiblen PowerShell-Editionen</span><span class="sxs-lookup"><span data-stu-id="b1046-103">Items with compatible PowerShell Editions</span></span>

<span data-ttu-id="b1046-104">Ab Version 5.1 steht PowerShell in verschiedenen Editionen zur Verfügung, die unterschiedliche Featuregruppen und Plattformkompatibilität bieten.</span><span class="sxs-lookup"><span data-stu-id="b1046-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="b1046-105">**Desktop-Edition:** Diese Edition basiert auf .NET Framework und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter Vollversionen von Windows wie Server Core und Windows Desktop ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="b1046-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="b1046-106">**Core-Edition:** Diese Edition basiert auf .NET Core und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter funktionsreduzierten Versionen von Windows wie Nano Server und Windows IoT ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="b1046-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a><span data-ttu-id="b1046-107">Der PowerShell-Katalog extrahiert unterstützte PSEditions-Metadaten und erlaubt Ihnen, die für bestimmte PowerShell-Editionen kompatiblen Elemente zu filtern</span><span class="sxs-lookup"><span data-stu-id="b1046-107">PowerShell Gallery extracts supported PSEditions metadata and allows you to filters the items compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="b1046-108">Verfügt ein Element über kompatible angegebene PSEditions, werden diese als Teil von „PowerShell Editions“ (PowerShell-Editionen) auf der Seite des Elements und auch in den Elementergebnissen aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="b1046-108">If an item has compatible PSEditions specified, they will be listed as part of 'PowerShell Editions' in the item display page and also in items results.</span></span>

![Seite des Elements mit PSEditions](../../Images/ItemDisplayPageWithPSEditions.PNG)

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a><span data-ttu-id="b1046-110">Suchen nach Elementen in der Benutzeroberfläche des Katalogs, die auf PowerShellCore arbeitet</span><span class="sxs-lookup"><span data-stu-id="b1046-110">Search for items in the gallery UI which works on PowerShellCore</span></span>

<span data-ttu-id="b1046-111">Verwenden Sie die Tags „PSEdition_Desktop“ und „PSEdition_Core“, um die Elemente im PowerShell-Katalog zu filtern.</span><span class="sxs-lookup"><span data-stu-id="b1046-111">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the items on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="b1046-112">Verwenden Sie das Tag „PSEdition_Core“, um Elemente zu suchen, die mit der PowerShell Core-Edition kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="b1046-112">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Suchergebnisse für Elemente, die mit Core PSEdition kompatibel sind](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="b1046-114">Verwenden Sie das Tag „PSEdition_Desktop“, um Elemente zu suchen, die mit der PowerShell Desktop Edition kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="b1046-114">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Suchergebnisse für Elemente, die mit Desktop PSEdition kompatibel sind](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a><span data-ttu-id="b1046-116">Weitere Informationen zur Erstellung und zum Suchen der Element mit kompatiblen PowerShell-Editionen</span><span class="sxs-lookup"><span data-stu-id="b1046-116">More details on authoring and finding the items with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="b1046-117">Module mit PowerShell-Editionen</span><span class="sxs-lookup"><span data-stu-id="b1046-117">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="b1046-118">Skripts mit PowerShell-Editionen</span><span class="sxs-lookup"><span data-stu-id="b1046-118">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)