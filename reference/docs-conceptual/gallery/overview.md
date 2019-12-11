---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery,psget
title: Der PowerShell-Katalog | MSDN
ms.openlocfilehash: d3e3b9d8bb3d6cefd3a3bfe79b012bb1dc1d8a2d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71327861"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="73c3b-103">Der PowerShell-Katalog | MSDN</span><span class="sxs-lookup"><span data-stu-id="73c3b-103">The PowerShell Gallery</span></span>

<span data-ttu-id="73c3b-104">Der PowerShell-Katalog ist das zentrale Repository für PowerShell-Inhalte.</span><span class="sxs-lookup"><span data-stu-id="73c3b-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="73c3b-105">Sie finden darin nützliche PowerShell-Module, die PowerShell-Befehle und Desired State Configuration-Ressourcen (DSC) enthalten.</span><span class="sxs-lookup"><span data-stu-id="73c3b-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="73c3b-106">Sie finden dort auch PowerShell-Skripts, von denen einige PowerShell-Workflows enthalten, eine Reihe von Aufgaben umreißen und Sequenzierungen für diese Aufgaben bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="73c3b-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="73c3b-107">Einige dieser Pakete wurden von Microsoft erstellt, andere stammen aus der PowerShell-Community.</span><span class="sxs-lookup"><span data-stu-id="73c3b-107">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="73c3b-108">Übersicht über PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="73c3b-108">PowerShellGet Overview</span></span>

<span data-ttu-id="73c3b-109">Das PowerShellGet-Modul enthält Cmdlets zum Ermitteln, Installieren, Aktualisieren und Veröffentlichen von PowerShell-Paketen mit Artefakten wie Modulen, DSC-Ressourcen, Rollenfunktionen und Skripts über den [PowerShell-Katalog](https://www.PowerShellGallery.com) und andere private Repositorys.</span><span class="sxs-lookup"><span data-stu-id="73c3b-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell packages which contain artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="73c3b-110">Erste Schritte mit dem Katalog</span><span class="sxs-lookup"><span data-stu-id="73c3b-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="73c3b-111">Zur Installation von Paketen aus dem Katalog wird die neueste Version des PowerShellGet-Moduls benötigt.</span><span class="sxs-lookup"><span data-stu-id="73c3b-111">Installing packages from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="73c3b-112">Eine vollständige Anleitung finden Sie unter [Installieren von PowerShellGet](installing-psget.md).</span><span class="sxs-lookup"><span data-stu-id="73c3b-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="73c3b-113">Sehen Sie sich die Seite [Erste Schritte](getting-started.md) an, um weitere Informationen zur Verwendung von PowerShellGet-Befehlen mit dem Katalog zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="73c3b-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="73c3b-114">Sie können auch *Update-Help -Module PowerShellGet* ausführen, um die lokale Hilfe für diese Befehle zu installieren.</span><span class="sxs-lookup"><span data-stu-id="73c3b-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="73c3b-115">Unterstützte Betriebssysteme</span><span class="sxs-lookup"><span data-stu-id="73c3b-115">Supported Operating Systems</span></span>

<span data-ttu-id="73c3b-116">Das Modul **PowerShellGet** erfordert **Windows PowerShell 3.0 oder höher** oder **PowerShell Core 6.0 oder höher**.</span><span class="sxs-lookup"><span data-stu-id="73c3b-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="73c3b-117">Eine geeignete Version von **Windows PowerShell** ist für folgende Betriebssysteme verfügbar:</span><span class="sxs-lookup"><span data-stu-id="73c3b-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="73c3b-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="73c3b-118">Windows 10</span></span>
- <span data-ttu-id="73c3b-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="73c3b-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="73c3b-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="73c3b-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="73c3b-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="73c3b-121">Windows 7 SP1</span></span>
- <span data-ttu-id="73c3b-122">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="73c3b-122">Windows Server 2019</span></span>
- <span data-ttu-id="73c3b-123">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="73c3b-123">Windows Server 2016</span></span>
- <span data-ttu-id="73c3b-124">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="73c3b-124">Windows Server 2012 R2</span></span>
- <span data-ttu-id="73c3b-125">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="73c3b-125">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="73c3b-126">Für **PowerShellGet** ist .NET Framework 4.5 oder höher erforderlich.</span><span class="sxs-lookup"><span data-stu-id="73c3b-126">**PowerShellGet** requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="73c3b-127">Von [hier](https://msdn.microsoft.com/library/5a4x27ek.aspx) können Sie .NET Framework 4.5 oder höher installieren.</span><span class="sxs-lookup"><span data-stu-id="73c3b-127">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="73c3b-128">Da **PowerShell Core** plattformübergreifend ist – was bedeutet, dass es unter Windows, Linux und macOS funktioniert –, ist auch **PowerShellGet** auf diesen Systemen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="73c3b-128">Since **PowerShell Core** is cross-platform and that means it works on Windows, Linux and MacOS, that also makes **PowerShellGet** available on those systems.</span></span> <span data-ttu-id="73c3b-129">Eine vollständige Liste der von **PowerShell Core** unterstützten Systeme finden Sie unter [Installieren von PowerShell](/powershell/scripting/setup/installing-powershell).</span><span class="sxs-lookup"><span data-stu-id="73c3b-129">For a full list of systems supported by **PowerShell Core** see [Installing PowerShell](/powershell/scripting/setup/installing-powershell).</span></span>

<span data-ttu-id="73c3b-130">Viele Module, die im Katalog aufgeführt sind, unterstützen andere Betriebssysteme und haben zusätzliche Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="73c3b-130">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="73c3b-131">Weitere Informationen finden Sie in der Dokumentation der jeweiligen Module.</span><span class="sxs-lookup"><span data-stu-id="73c3b-131">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="73c3b-132">Sie haben eine Frage?</span><span class="sxs-lookup"><span data-stu-id="73c3b-132">Got a question?</span></span> <span data-ttu-id="73c3b-133">Haben Sie Feedback?</span><span class="sxs-lookup"><span data-stu-id="73c3b-133">Have feedback?</span></span>

<span data-ttu-id="73c3b-134">Weitere Informationen zum PowerShell-Katalog und zu PowerShellGet finden Sie auf der Seite [Erste Schritte](getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="73c3b-134">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="73c3b-135">Stellen Sie Feedback bereit, und melden Sie Probleme über [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="73c3b-135">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
