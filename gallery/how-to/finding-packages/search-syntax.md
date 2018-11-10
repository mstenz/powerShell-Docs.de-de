---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Syntax für die Katalogsuche
ms.openlocfilehash: 9aadb6771c85845cc3fa05cb56f0194b060d1c1b
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003779"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="014d4-103">Syntax für die Katalogsuche</span><span class="sxs-lookup"><span data-stu-id="014d4-103">Gallery Search Syntax</span></span>

<span data-ttu-id="014d4-104">Der PowerShell-Katalog bietet ein Textsuchfeld in das Sie Wörter, Ausdrücke und Schlüsselwortausdrücke schreiben können, um die Suchergebnisse einzugrenzen.</span><span class="sxs-lookup"><span data-stu-id="014d4-104">PowerShell Gallery offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="014d4-105">Suche nach Schlüsselwörtern</span><span class="sxs-lookup"><span data-stu-id="014d4-105">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="014d4-106">Die Suche tut ihr Möglichstes, um relevante Dokumente zu finden, die alle drei Schlüsselwörter enthalten, und zugehörige Dokumente zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="014d4-106">Search will do its best effort to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="014d4-107">Suchen mithilfe von Ausdrücken und Schlüsselwörtern</span><span class="sxs-lookup"><span data-stu-id="014d4-107">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="014d4-108">Die Eingabe eines Ausdrucks zwischen Anführungszeichen ("") ändert den Suchvorgang. Es wird nun nach dem bestimmten Ausdruck statt nach einzelnen Schlüsselwörter gesucht.</span><span class="sxs-lookup"><span data-stu-id="014d4-108">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="014d4-109">Übereinstimmende Dokumente sollten in der Regel den exakten Ausdruck "azure sql", einschließlich der Varianten bezüglich Groß-/Kleinschreibung enthalten, z.B. "Azure SQL" und sollten auch in der Regel das Wort „deployment“ (Bereitstellung) enthalten.</span><span class="sxs-lookup"><span data-stu-id="014d4-109">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="014d4-110">Filtern nach Feldern</span><span class="sxs-lookup"><span data-stu-id="014d4-110">Filtering on fields</span></span>

<span data-ttu-id="014d4-111">Sie können nach einer bestimmten Paket-ID (bzw. „Id“ oder „id“) oder nach bestimmten anderen Feldern suchen, indem Sie den Suchbegriffen den Feldnamen voranstellen.</span><span class="sxs-lookup"><span data-stu-id="014d4-111">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="014d4-112">Aktuell lauten die durchsuchbaren Felder „Id“, „Version“, „Tags“, „Author“ (Autor), „Owner“,(Besitzer) „Functions“ (Funktionen), „Cmdlets“, „DscResources“ und „PowerShellVersion“.</span><span class="sxs-lookup"><span data-stu-id="014d4-112">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="014d4-113">[Was ist der Unterschied zwischen ID und Titel?</span><span class="sxs-lookup"><span data-stu-id="014d4-113">[What's the difference between ID and Title?</span></span> <span data-ttu-id="014d4-114">Die ID ist der Name, den Sie in der Konsole verwenden.</span><span class="sxs-lookup"><span data-stu-id="014d4-114">ID is the name you use in the console.</span></span> <span data-ttu-id="014d4-115">Der Titel ist das, was oben auf der Paketseite in den Suchergebnissen angezeigt wird.]</span><span class="sxs-lookup"><span data-stu-id="014d4-115">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="014d4-116">Beispiele</span><span class="sxs-lookup"><span data-stu-id="014d4-116">Examples</span></span>

    ID:"PSReadline"
    id:"AzureRM.Profile"

<span data-ttu-id="014d4-117">So werden Pakete mit „PSReadline“ oder „AzureRM.Profile“ im jeweiligen ID-Feld gefunden.</span><span class="sxs-lookup"><span data-stu-id="014d4-117">finds packages with "PSReadline" or "AzureRM.Profile" in their ID field respectively.</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="014d4-118">Dies ist eine andere Möglichkeit, Pakete mit „AzureRM.Profile“ im ID-Feld zu suchen.</span><span class="sxs-lookup"><span data-stu-id="014d4-118">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="014d4-119">Der Filter „Id“ ist eine Übereinstimmung bei Teilzeichenfolge, Sie suchen also nach Folgendem:</span><span class="sxs-lookup"><span data-stu-id="014d4-119">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="014d4-120">Daraufhin erhalten Sie die Ergebnisse, wie z.B. „AzureRM.Profile“ und „Azure.Storage“.</span><span class="sxs-lookup"><span data-stu-id="014d4-120">You'll get results like 'AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="014d4-121">Sie können auch nach mehreren Schlüsselwörtern in einem einzelnen Feld suchen.</span><span class="sxs-lookup"><span data-stu-id="014d4-121">You can also search for multiple keywords in a single field.</span></span> <span data-ttu-id="014d4-122">Oder kombinieren Sie Felder.</span><span class="sxs-lookup"><span data-stu-id="014d4-122">Or mix and match fields.</span></span>

    id:azure tags:intellisense
    id:azure id:storage

<span data-ttu-id="014d4-123">Sie können auch nach Ausdrücken suchen:</span><span class="sxs-lookup"><span data-stu-id="014d4-123">And you can perform phrase searches:</span></span>

    id:"azure.storage"


<span data-ttu-id="014d4-124">So suchen Sie alle Pakete mit DSC-Tag:</span><span class="sxs-lookup"><span data-stu-id="014d4-124">To search all packages with DSC tag.</span></span>

    Tags:"DSC"

<span data-ttu-id="014d4-125">So suchen Sie alle Pakete mit der angegebenen Funktion:</span><span class="sxs-lookup"><span data-stu-id="014d4-125">To search all packages with the specified function.</span></span>

    Functions:"Update-AzureRM"

<span data-ttu-id="014d4-126">So suchen Sie alle Pakete mit dem angegebenen Cmdlet:</span><span class="sxs-lookup"><span data-stu-id="014d4-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:"Get-AzureRmEnvironment"

<span data-ttu-id="014d4-127">So suchen Sie alle Pakete mit dem angegebenen DSC-Ressourcennamen:</span><span class="sxs-lookup"><span data-stu-id="014d4-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:"xArchive"

<span data-ttu-id="014d4-128">So suchen Sie alle Pakete mit der angegebenen PowerShellVersion:</span><span class="sxs-lookup"><span data-stu-id="014d4-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


<span data-ttu-id="014d4-129">Wenn Sie anschließend ein Feld verwenden, das nicht unterstützt wird, wie z.B. „commands“ (Befehle), wird es einfach ignoriert, und alle Felder werden durchsucht.</span><span class="sxs-lookup"><span data-stu-id="014d4-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="014d4-130">Das folgende Query</span><span class="sxs-lookup"><span data-stu-id="014d4-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="014d4-131">wird genau wie diese Abfrage interpretiert:</span><span class="sxs-lookup"><span data-stu-id="014d4-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage
