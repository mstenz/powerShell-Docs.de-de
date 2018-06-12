---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery,psget
title: Der PowerShell-Katalog | MSDN
ms.openlocfilehash: dc7e8dd7e4d96d8424a62cb3256c3164b63a3684
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482929"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="97d5d-103">Der PowerShell-Katalog | MSDN</span><span class="sxs-lookup"><span data-stu-id="97d5d-103">The PowerShell Gallery</span></span>

<span data-ttu-id="97d5d-104">Der PowerShell-Katalog ist das zentrale Repository für PowerShell-Inhalte.</span><span class="sxs-lookup"><span data-stu-id="97d5d-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="97d5d-105">Sie finden darin nützliche PowerShell-Module, die PowerShell-Befehle und Desired State Configuration-Ressourcen (DSC) enthalten.</span><span class="sxs-lookup"><span data-stu-id="97d5d-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="97d5d-106">Sie finden dort auch PowerShell-Skripts, von denen einige PowerShell-Workflows enthalten, eine Reihe von Aufgaben umreißen und Sequenzierungen für diese Aufgaben bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="97d5d-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="97d5d-107">Einige dieser Elemente wurden von Microsoft erstellt, andere stammen aus der PowerShell-Community.</span><span class="sxs-lookup"><span data-stu-id="97d5d-107">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="97d5d-108">Übersicht über PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="97d5d-108">PowerShellGet Overview</span></span>

<span data-ttu-id="97d5d-109">Das PowerShellGet-Modul enthält Cmdlets zum Ermitteln, Installieren, Aktualisieren und Veröffentlichen von PowerShell-Artefakten wie Modulen, DSC-Ressourcen, Rollenfunktionen und Skripts über den [PowerShell-Katalog](https://www.PowerShellGallery.com) und andere private Repositorys.</span><span class="sxs-lookup"><span data-stu-id="97d5d-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="97d5d-110">Erste Schritte mit dem Katalog</span><span class="sxs-lookup"><span data-stu-id="97d5d-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="97d5d-111">Zur Installation von Elementen aus dem Katalog wird die neueste Version des PowerShellGet-Moduls benötigt.</span><span class="sxs-lookup"><span data-stu-id="97d5d-111">Installing items from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="97d5d-112">Eine vollständige Anleitung finden Sie unter [Installieren von PowerShellGet](installing-psget.md).</span><span class="sxs-lookup"><span data-stu-id="97d5d-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="97d5d-113">Sehen Sie sich die Seite [Erste Schritte](getting-started.md) an, um weitere Informationen zur Verwendung von PowerShellGet-Befehlen mit dem Katalog zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="97d5d-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="97d5d-114">Sie können auch *Update-Help -Module PowerShellGet* ausführen, um die lokale Hilfe für diese Befehle zu installieren.</span><span class="sxs-lookup"><span data-stu-id="97d5d-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="97d5d-115">Unterstützte Betriebssysteme</span><span class="sxs-lookup"><span data-stu-id="97d5d-115">Supported Operating Systems</span></span>

<span data-ttu-id="97d5d-116">Das Modul **PowerShellGet** erfordert **Windows PowerShell 3.0 oder höher** oder **PowerShell Core 6.0 oder höher**.</span><span class="sxs-lookup"><span data-stu-id="97d5d-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="97d5d-117">Eine geeignete Version von **Windows PowerShell** ist für folgende Betriebssysteme verfügbar:</span><span class="sxs-lookup"><span data-stu-id="97d5d-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="97d5d-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="97d5d-118">Windows 10</span></span>
- <span data-ttu-id="97d5d-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="97d5d-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="97d5d-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="97d5d-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="97d5d-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="97d5d-121">Windows 7 SP1</span></span>
- <span data-ttu-id="97d5d-122">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="97d5d-122">Windows Server 2016</span></span>
- <span data-ttu-id="97d5d-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="97d5d-123">Windows Server 2012 R2</span></span>
- <span data-ttu-id="97d5d-124">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="97d5d-124">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="97d5d-125">Für **PowerShellGet** ist außerdem .NET Framework 4.5 oder höher erforderlich.</span><span class="sxs-lookup"><span data-stu-id="97d5d-125">**PowerShellGet** also requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="97d5d-126">Von [hier](https://msdn.microsoft.com/library/5a4x27ek.aspx) können Sie .NET Framework 4.5 oder höher installieren.</span><span class="sxs-lookup"><span data-stu-id="97d5d-126">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="97d5d-127">**PowerShell Core** unterstützt viele Betriebssysteme.</span><span class="sxs-lookup"><span data-stu-id="97d5d-127">**PowerShell Core** supports many operating systems.</span></span> <span data-ttu-id="97d5d-128">Eine vollständige Liste finden Sie in [diesem Artikel](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/).</span><span class="sxs-lookup"><span data-stu-id="97d5d-128">See [this article](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/) for a full list.</span></span>

<span data-ttu-id="97d5d-129">Viele Module, die im Katalog aufgeführt sind, unterstützen andere Betriebssysteme und haben zusätzliche Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="97d5d-129">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="97d5d-130">Weitere Informationen finden Sie in der Dokumentation der jeweiligen Module.</span><span class="sxs-lookup"><span data-stu-id="97d5d-130">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="97d5d-131">Sie haben eine Frage?</span><span class="sxs-lookup"><span data-stu-id="97d5d-131">Got a question?</span></span> <span data-ttu-id="97d5d-132">Haben Sie Feedback?</span><span class="sxs-lookup"><span data-stu-id="97d5d-132">Have feedback?</span></span>

<span data-ttu-id="97d5d-133">Weitere Informationen zum PowerShell-Katalog und zu PowerShellGet finden Sie auf der Seite [Erste Schritte](getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="97d5d-133">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="97d5d-134">Stellen Sie Feedback bereit, und melden Sie Probleme über [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="97d5d-134">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
