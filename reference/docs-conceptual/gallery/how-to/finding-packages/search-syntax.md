---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Syntax für die Katalogsuche
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328451"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="30ea9-103">Syntax für die Katalogsuche</span><span class="sxs-lookup"><span data-stu-id="30ea9-103">Gallery Search Syntax</span></span>

<span data-ttu-id="30ea9-104">Sie können den PowerShell-Katalog mit der [Website des PowerShell-Katalogs](https://www.powershellgallery.com/) durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="30ea9-104">You can search the PowerShell Gallery using the [PowerShell Gallery's web site](https://www.powershellgallery.com/).</span></span>
<span data-ttu-id="30ea9-105">Die Website des PowerShell-Katalogs bietet ein Textsuchfeld in das Sie Wörter, Ausdrücke und Schlüsselwortausdrücke schreiben können, um die Suchergebnisse einzugrenzen.</span><span class="sxs-lookup"><span data-stu-id="30ea9-105">PowerShell Gallery web site offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="30ea9-106">Suche nach Schlüsselwörtern</span><span class="sxs-lookup"><span data-stu-id="30ea9-106">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="30ea9-107">Die Suche versucht, relevante Dokumente zu finden, die alle drei Schlüsselwörter enthalten, und zugehörige Dokumente zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="30ea9-107">Search attempts to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="30ea9-108">Suchen mithilfe von Ausdrücken und Schlüsselwörtern</span><span class="sxs-lookup"><span data-stu-id="30ea9-108">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="30ea9-109">Die Eingabe eines Ausdrucks zwischen Anführungszeichen ("") ändert den Suchvorgang. Es wird nun nach dem bestimmten Ausdruck statt nach einzelnen Schlüsselwörter gesucht.</span><span class="sxs-lookup"><span data-stu-id="30ea9-109">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="30ea9-110">Übereinstimmende Dokumente sollten in der Regel den exakten Ausdruck "azure sql", einschließlich der Varianten bezüglich Groß-/Kleinschreibung enthalten, z.B. "Azure SQL" und sollten auch in der Regel das Wort „deployment“ (Bereitstellung) enthalten.</span><span class="sxs-lookup"><span data-stu-id="30ea9-110">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="30ea9-111">Filtern nach Feldern</span><span class="sxs-lookup"><span data-stu-id="30ea9-111">Filtering on fields</span></span>

<span data-ttu-id="30ea9-112">Sie können nach einer bestimmten Paket-ID (bzw. „Id“ oder „id“) oder nach bestimmten anderen Feldern suchen, indem Sie den Suchbegriffen den Feldnamen voranstellen.</span><span class="sxs-lookup"><span data-stu-id="30ea9-112">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="30ea9-113">Aktuell lauten die durchsuchbaren Felder „Id“, „Version“, „Tags“, „Author“ (Autor), „Owner“,(Besitzer) „Functions“ (Funktionen), „Cmdlets“, „DscResources“ und „PowerShellVersion“.</span><span class="sxs-lookup"><span data-stu-id="30ea9-113">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="30ea9-114">[Was ist der Unterschied zwischen ID und Titel?</span><span class="sxs-lookup"><span data-stu-id="30ea9-114">[What's the difference between ID and Title?</span></span> <span data-ttu-id="30ea9-115">Die ID ist der Name, den Sie in der Konsole verwenden.</span><span class="sxs-lookup"><span data-stu-id="30ea9-115">ID is the name you use in the console.</span></span> <span data-ttu-id="30ea9-116">Der Titel ist das, was oben auf der Paketseite in den Suchergebnissen angezeigt wird.]</span><span class="sxs-lookup"><span data-stu-id="30ea9-116">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="30ea9-117">Beispiele</span><span class="sxs-lookup"><span data-stu-id="30ea9-117">Examples</span></span>

    ID:PSReadline
    
<span data-ttu-id="30ea9-118">sucht nach Paketen mit einer ID, die „PSReadline“ enthält.</span><span class="sxs-lookup"><span data-stu-id="30ea9-118">finds packages with an ID containing "PSReadline".</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="30ea9-119">Dies ist eine andere Möglichkeit, Pakete mit „AzureRM.Profile“ im ID-Feld zu suchen.</span><span class="sxs-lookup"><span data-stu-id="30ea9-119">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="30ea9-120">Der Filter „Id“ ist eine Übereinstimmung bei Teilzeichenfolge, Sie suchen also nach Folgendem:</span><span class="sxs-lookup"><span data-stu-id="30ea9-120">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="30ea9-121">Es werden Ergebnisse bereitgestellt, die „AzureRM.Profile“ und “Azure.Storage“ enthalten.</span><span class="sxs-lookup"><span data-stu-id="30ea9-121">This provides results that include AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="30ea9-122">Sie können auch nach mehreren Schlüsselwörtern in einem einzelnen Feld suchen.</span><span class="sxs-lookup"><span data-stu-id="30ea9-122">You can also search for multiple keywords in a single field.</span></span> 

    id:azure tags:intellisense

<span data-ttu-id="30ea9-123">Und Sie können die Suche nach Ausdrücken mit doppelten Anführungszeichen durchführen:</span><span class="sxs-lookup"><span data-stu-id="30ea9-123">And you can perform phrase searches using double quotes:</span></span>

    id:"azure.storage"

<span data-ttu-id="30ea9-124">So suchen Sie alle Pakete mit DSC-Tag:</span><span class="sxs-lookup"><span data-stu-id="30ea9-124">To search all packages with DSC tag.</span></span>

    Tags:DSC

<span data-ttu-id="30ea9-125">So suchen Sie alle Pakete mit der angegebenen Funktion:</span><span class="sxs-lookup"><span data-stu-id="30ea9-125">To search all packages with the specified function.</span></span>

    Functions:Get-TreeSize

<span data-ttu-id="30ea9-126">So suchen Sie alle Pakete mit dem angegebenen Cmdlet:</span><span class="sxs-lookup"><span data-stu-id="30ea9-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:Get-AzureRmEnvironment

<span data-ttu-id="30ea9-127">So suchen Sie alle Pakete mit dem angegebenen DSC-Ressourcennamen:</span><span class="sxs-lookup"><span data-stu-id="30ea9-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:xArchive

<span data-ttu-id="30ea9-128">So suchen Sie alle Pakete mit der angegebenen PowerShellVersion:</span><span class="sxs-lookup"><span data-stu-id="30ea9-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:2.0

<span data-ttu-id="30ea9-129">Wenn Sie anschließend ein Feld verwenden, das nicht unterstützt wird, wie z.B. „commands“ (Befehle), wird es einfach ignoriert, und alle Felder werden durchsucht.</span><span class="sxs-lookup"><span data-stu-id="30ea9-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="30ea9-130">Das folgende Query</span><span class="sxs-lookup"><span data-stu-id="30ea9-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="30ea9-131">wird genau wie diese Abfrage interpretiert:</span><span class="sxs-lookup"><span data-stu-id="30ea9-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage
