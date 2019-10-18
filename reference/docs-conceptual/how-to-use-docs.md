---
ms.date: 09/25/2019
keywords: powershell,cmdlet
title: Verwenden der PowerShell-Dokumentation
ms.openlocfilehash: 9e3d5828d6bdb4ef14701994f146354a041efaea
ms.sourcegitcommit: a80bb79b85deab8ae3c21de56d1ee432fdd92628
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72281647"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="4b1c7-103">Verwenden der PowerShell-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="4b1c7-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="4b1c7-104">Willkommen bei der PowerShell-Onlinedokumentation.</span><span class="sxs-lookup"><span data-stu-id="4b1c7-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="4b1c7-105">Auf dieser Website finden Sie die Cmdlet-Referenz für die folgenden PowerShell-Versionen:</span><span class="sxs-lookup"><span data-stu-id="4b1c7-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="4b1c7-106">PowerShell 7 (Vorschauversion)</span><span class="sxs-lookup"><span data-stu-id="4b1c7-106">PowerShell 7 (preview)</span></span>
- <span data-ttu-id="4b1c7-107">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="4b1c7-107">PowerShell 6</span></span>
- <span data-ttu-id="4b1c7-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="4b1c7-108">PowerShell 5.1</span></span>
- <span data-ttu-id="4b1c7-109">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4b1c7-109">PowerShell 5.0</span></span>
- <span data-ttu-id="4b1c7-110">PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="4b1c7-110">PowerShell 4.0</span></span>
- <span data-ttu-id="4b1c7-111">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="4b1c7-111">PowerShell 3.0</span></span>

## <a name="selecting-your-version"></a><span data-ttu-id="4b1c7-112">Auswahl Ihrer Version</span><span class="sxs-lookup"><span data-stu-id="4b1c7-112">Selecting your version</span></span>

<span data-ttu-id="4b1c7-113">Standardmäßig ist auf dieser Website die Dokumentation für die neueste veröffentlichte Version von PowerShell zu sehen.</span><span class="sxs-lookup"><span data-stu-id="4b1c7-113">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="4b1c7-114">Einige Cmdlets funktionieren in verschiedenen Versionen von PowerShell unterschiedlich.</span><span class="sxs-lookup"><span data-stu-id="4b1c7-114">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="4b1c7-115">Stellen Sie sicher, dass Sie die Dokumentation für die von Ihnen verwendete Version von PowerShell anzeigen.</span><span class="sxs-lookup"><span data-stu-id="4b1c7-115">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="4b1c7-116">Verwenden Sie die Versionsauswahl oben auf der Seite, um die gewünschte Version von PowerShell auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="4b1c7-116">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![Versionsauswahl](images/how-to-use-docs/picker-vall.gif)

<span data-ttu-id="4b1c7-118">Anhand des Werts `$PSversionTable.PSVersion` können Sie erkennen, welche Version von PowerShell Sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="4b1c7-118">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="4b1c7-119">Das folgende Beispiel zeigt die Ausgabe für Windows PowerShell v5.1.</span><span class="sxs-lookup"><span data-stu-id="4b1c7-119">The following example shows the output for Windows PowerShell v5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```

## <a name="searching-for-articles"></a><span data-ttu-id="4b1c7-120">Suche nach Artikeln</span><span class="sxs-lookup"><span data-stu-id="4b1c7-120">Searching for articles</span></span>

<span data-ttu-id="4b1c7-121">Es gibt zwei Möglichkeiten, um in der Dokumentation nach Inhalten zu suchen. Der einfachste Weg ist die Verwendung des Filterfelds unter der Versionsauswahl.</span><span class="sxs-lookup"><span data-stu-id="4b1c7-121">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="4b1c7-122">Geben Sie einfach ein Wort ein, das im Titel eines Artikels enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="4b1c7-122">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="4b1c7-123">Es wird eine Liste der passenden Artikel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4b1c7-123">The page displays a list of matching articles.</span></span> <span data-ttu-id="4b1c7-124">Sie können auch festlegen, dass die gesamte Website anhand dieser Liste durchsucht werden soll.</span><span class="sxs-lookup"><span data-stu-id="4b1c7-124">You can also select the option to search the entire site from that list.</span></span>

![Filterfeld](images/how-to-use-docs/filter-search.gif)
