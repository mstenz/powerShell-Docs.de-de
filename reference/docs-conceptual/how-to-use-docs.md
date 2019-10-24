---
ms.date: 10/20/2019
keywords: powershell,cmdlet
title: Verwenden der PowerShell-Dokumentation
ms.openlocfilehash: 80f72bb89b3bb82ee7c4d16b8969395f02d7d4ca
ms.sourcegitcommit: ac1ccdd826f112a11db09af9c628cae013f947ab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2019
ms.locfileid: "72676156"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="96f44-103">Verwenden der PowerShell-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="96f44-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="96f44-104">Willkommen bei der PowerShell-Onlinedokumentation.</span><span class="sxs-lookup"><span data-stu-id="96f44-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="96f44-105">Auf dieser Website finden Sie die Cmdlet-Referenz für die folgenden PowerShell-Versionen:</span><span class="sxs-lookup"><span data-stu-id="96f44-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="96f44-106">PowerShell 7 (Vorschauversion)</span><span class="sxs-lookup"><span data-stu-id="96f44-106">PowerShell 7 (preview)</span></span>
- <span data-ttu-id="96f44-107">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="96f44-107">PowerShell 6</span></span>
- <span data-ttu-id="96f44-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="96f44-108">PowerShell 5.1</span></span>

## <a name="finding-articles-and-selecting-a-version"></a><span data-ttu-id="96f44-109">Suchen von Artikeln und Auswählen einer Version</span><span class="sxs-lookup"><span data-stu-id="96f44-109">Finding articles and selecting a version</span></span>

<span data-ttu-id="96f44-110">Es gibt zwei Möglichkeiten, um in der Dokumentation nach Inhalten zu suchen. Der einfachste Weg ist die Verwendung des Filterfelds unter der Versionsauswahl.</span><span class="sxs-lookup"><span data-stu-id="96f44-110">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="96f44-111">Geben Sie einfach ein Wort ein, das im Titel eines Artikels enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="96f44-111">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="96f44-112">Es wird eine Liste der passenden Artikel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="96f44-112">The page displays a list of matching articles.</span></span> <span data-ttu-id="96f44-113">Sie können auch festlegen, dass die gesamte Website anhand dieser Liste durchsucht werden soll.</span><span class="sxs-lookup"><span data-stu-id="96f44-113">You can also select the option to search the entire site from that list.</span></span>

<span data-ttu-id="96f44-114">Standardmäßig ist auf dieser Website die Dokumentation für die neueste veröffentlichte Version von PowerShell zu sehen.</span><span class="sxs-lookup"><span data-stu-id="96f44-114">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="96f44-115">Einige Cmdlets funktionieren in verschiedenen Versionen von PowerShell unterschiedlich.</span><span class="sxs-lookup"><span data-stu-id="96f44-115">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="96f44-116">Stellen Sie sicher, dass Sie die Dokumentation für die von Ihnen verwendete Version von PowerShell anzeigen.</span><span class="sxs-lookup"><span data-stu-id="96f44-116">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="96f44-117">Verwenden Sie die Versionsauswahl oben auf der Seite, um die gewünschte Version von PowerShell auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="96f44-117">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![Versionsauswahl](images/how-to-use-docs/version-search.gif)

<span data-ttu-id="96f44-119">Anhand des Werts `$PSversionTable.PSVersion` können Sie erkennen, welche Version von PowerShell Sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="96f44-119">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="96f44-120">Das folgende Beispiel zeigt die Ausgabe für Windows PowerShell v5.1.</span><span class="sxs-lookup"><span data-stu-id="96f44-120">The following example shows the output for Windows PowerShell v5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```
