---
ms.date: 10/20/2019
keywords: powershell,cmdlet
title: Verwenden der PowerShell-Dokumentation
ms.openlocfilehash: 50b054ddc21d55946969414688306fc0d15a5adf
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80082830"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="93ab4-103">Verwenden der PowerShell-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="93ab4-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="93ab4-104">Willkommen bei der PowerShell-Onlinedokumentation.</span><span class="sxs-lookup"><span data-stu-id="93ab4-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="93ab4-105">Auf dieser Website finden Sie die Cmdlet-Referenz für die folgenden PowerShell-Versionen:</span><span class="sxs-lookup"><span data-stu-id="93ab4-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="93ab4-106">PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="93ab4-106">PowerShell 7</span></span>
- <span data-ttu-id="93ab4-107">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="93ab4-107">PowerShell 6</span></span>
- <span data-ttu-id="93ab4-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="93ab4-108">PowerShell 5.1</span></span>

## <a name="finding-articles-and-selecting-a-version"></a><span data-ttu-id="93ab4-109">Suchen von Artikeln und Auswählen einer Version</span><span class="sxs-lookup"><span data-stu-id="93ab4-109">Finding articles and selecting a version</span></span>

<span data-ttu-id="93ab4-110">Es gibt zwei Möglichkeiten, um in der Dokumentation nach Inhalten zu suchen. Der einfachste Weg ist die Verwendung des Filterfelds unter der Versionsauswahl.</span><span class="sxs-lookup"><span data-stu-id="93ab4-110">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="93ab4-111">Geben Sie einfach ein Wort ein, das im Titel eines Artikels enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="93ab4-111">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="93ab4-112">Es wird eine Liste der passenden Artikel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="93ab4-112">The page displays a list of matching articles.</span></span> <span data-ttu-id="93ab4-113">Sie können auch festlegen, dass die gesamte Website anhand dieser Liste durchsucht werden soll.</span><span class="sxs-lookup"><span data-stu-id="93ab4-113">You can also select the option to search the entire site from that list.</span></span>

<span data-ttu-id="93ab4-114">Standardmäßig ist auf dieser Website die Dokumentation für die neueste veröffentlichte Version von PowerShell zu sehen.</span><span class="sxs-lookup"><span data-stu-id="93ab4-114">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="93ab4-115">Einige Cmdlets funktionieren in verschiedenen Versionen von PowerShell unterschiedlich.</span><span class="sxs-lookup"><span data-stu-id="93ab4-115">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="93ab4-116">Stellen Sie sicher, dass Sie die Dokumentation für die von Ihnen verwendete Version von PowerShell anzeigen.</span><span class="sxs-lookup"><span data-stu-id="93ab4-116">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="93ab4-117">Verwenden Sie die Versionsauswahl oben auf der Seite, um die gewünschte Version von PowerShell auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="93ab4-117">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![Versionsauswahl](media/how-to-use-docs/version-search.gif)

<span data-ttu-id="93ab4-119">Anhand des Werts `$PSversionTable.PSVersion` können Sie erkennen, welche Version von PowerShell Sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="93ab4-119">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="93ab4-120">Das folgende Beispiel zeigt die Ausgabe für Windows PowerShell v5.1.</span><span class="sxs-lookup"><span data-stu-id="93ab4-120">The following example shows the output for Windows PowerShell v5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```
