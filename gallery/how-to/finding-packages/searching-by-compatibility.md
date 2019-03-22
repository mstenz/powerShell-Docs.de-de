---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: gallery,powershell,cmdlet,psgallery
title: Pakete mit kompatiblen PowerShell-Editionen oder Betriebssystemen
ms.openlocfilehash: 14038aa9b0453e1d06e6587e97da391b56297c75
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2019
ms.locfileid: "58057177"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a><span data-ttu-id="e56e2-103">Pakete mit kompatiblen PowerShell-Editionen oder Betriebssystemen</span><span class="sxs-lookup"><span data-stu-id="e56e2-103">Packages with compatible PowerShell Editions or Operating Systems</span></span>

<span data-ttu-id="e56e2-104">Ab Version 5.1 steht PowerShell in verschiedenen Editionen zur Verfügung, die unterschiedliche Featuregruppen und Plattformkompatibilität bieten.</span><span class="sxs-lookup"><span data-stu-id="e56e2-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibilities.</span></span>

## <a name="searching-by-powershell-edition"></a><span data-ttu-id="e56e2-105">Suchen nach PowerShell-Edition</span><span class="sxs-lookup"><span data-stu-id="e56e2-105">Searching by PowerShell Edition</span></span>

<span data-ttu-id="e56e2-106">Es gibt zwei PowerShell-Editionen:</span><span class="sxs-lookup"><span data-stu-id="e56e2-106">The two editions of PowerShell are:</span></span>
- <span data-ttu-id="e56e2-107">**Desktop-Edition:** Diese Edition basiert auf .NET Framework und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter Vollversionen von Windows wie Server Core und Windows Desktop ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="e56e2-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="e56e2-108">**Core-Edition:** Diese Edition basiert auf .NET Core und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter funktionsreduzierten Versionen von Windows wie Nano Server und Windows IoT ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="e56e2-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="e56e2-109">Der PowerShell-Katalog ermöglicht es, Pakete herauszufiltern, die mit bestimmten PowerShell-Editionen kompatibel sind</span><span class="sxs-lookup"><span data-stu-id="e56e2-109">PowerShell Gallery allows you to filter packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="e56e2-110">Wenn für ein Paket kompatible PSEditions angegeben sind, werden diese im Rahmen von „PowerShell-Editionen“ auf der Paketseite und in den Paketergebnissen aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="e56e2-110">If a package has compatible PSEditions specified, they are listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>
<span data-ttu-id="e56e2-111">Sie können auch mithilfe von PowerShell nach kompatiblen Paketen suchen.</span><span class="sxs-lookup"><span data-stu-id="e56e2-111">You can also search for compatible packages using PowerShell.</span></span>

![Seite des Elements mit PSEditions](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a><span data-ttu-id="e56e2-113">Suchen nach Paketen in der Katalogbenutzeroberfläche in PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="e56e2-113">Search for packages in the gallery UI that work on PowerShell Core</span></span>

<span data-ttu-id="e56e2-114">Verwenden Sie die Tags „PSEdition_Desktop“ und „PSEdition_Core“, um die Pakete im PowerShell-Katalog zu filtern.</span><span class="sxs-lookup"><span data-stu-id="e56e2-114">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="e56e2-115">Verwenden Sie das Tag „PSEdition_Core“, um Elemente zu suchen, die mit der PowerShell Core-Edition kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="e56e2-115">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Suchergebnisse für Elemente, die mit Core PSEdition kompatibel sind](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="e56e2-117">Verwenden Sie das Tag „PSEdition_Desktop“, um Elemente zu suchen, die mit der PowerShell Desktop Edition kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="e56e2-117">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Suchergebnisse für Elemente, die mit Desktop PSEdition kompatibel sind](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a><span data-ttu-id="e56e2-119">Suchen nach Paketen mithilfe von PowerShell, um kompatible Versionen zu finden</span><span class="sxs-lookup"><span data-stu-id="e56e2-119">Search for packages to find compatible editions using PowerShell</span></span>
<span data-ttu-id="e56e2-120">Sie können Tags angeben, um nach PowerShell-Edition und Betriebssystem zu filtern.</span><span class="sxs-lookup"><span data-stu-id="e56e2-120">You can specify tags to filter for the PowerShell edition and OS.</span></span>
<span data-ttu-id="e56e2-121">Sie verwenden das Cmdlet `Find-Package`, das die `-Tag`-Parameter angibt, um die Edition und das Betriebssystem anzugeben, auf das Sie abzielen.</span><span class="sxs-lookup"><span data-stu-id="e56e2-121">You use the `Find-Package` cmdlet specifying the `-Tag` parameter to specify the edition (and OS) you are targeting.</span></span>
<span data-ttu-id="e56e2-122">Dies sieht folgendermaßen aus:</span><span class="sxs-lookup"><span data-stu-id="e56e2-122">Like this:</span></span>

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a><span data-ttu-id="e56e2-123">Suchen je Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="e56e2-123">Searching by Operating System</span></span>

<span data-ttu-id="e56e2-124">Da PowerShell Core für Windows, Linux und MacOS verfügbar ist, können die Pakete im Katalog für alle Kombinationen dieser drei Betriebssysteme entworfen werden.</span><span class="sxs-lookup"><span data-stu-id="e56e2-124">Since PowerShell Core is available for Windows, Linux, and MacOS, packages in the Gallery may be designed for any combination of these operating systems.</span></span> <span data-ttu-id="e56e2-125">Verwenden Sie in der Katalogbenutzeroberfläche je nach Betriebssystem die folgenden Suchtags, um Pakete zu finden, die mit einem Tag versehen wurden:</span><span class="sxs-lookup"><span data-stu-id="e56e2-125">In the gallery UI use the following searchs tags to find packages tagged by operating system:</span></span>

- <span data-ttu-id="e56e2-126">Tags: "Windows"</span><span class="sxs-lookup"><span data-stu-id="e56e2-126">Tags: "Windows"</span></span>
- <span data-ttu-id="e56e2-127">Tags: "Linux"</span><span class="sxs-lookup"><span data-stu-id="e56e2-127">Tags: "Linux"</span></span>
- <span data-ttu-id="e56e2-128">Tags: "MacOS"</span><span class="sxs-lookup"><span data-stu-id="e56e2-128">Tags: "MacOS"</span></span>

<span data-ttu-id="e56e2-129">Sie können diese Tags folgendermaßen auf `Find-Module` (und anderen Cmdlets im PowerShellGet-Modul) angeben:</span><span class="sxs-lookup"><span data-stu-id="e56e2-129">You can specify these tags on `Find-Module` (and other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a><span data-ttu-id="e56e2-130">Suchen nach mehrfacher Kompatibilität</span><span class="sxs-lookup"><span data-stu-id="e56e2-130">Searching for Multiple Compatibilities</span></span>

<span data-ttu-id="e56e2-131">Sie können nach einem Paket suchen, das mehrere Kompatibilitäten hat, wenn Sie diese Syntax verwenden:</span><span class="sxs-lookup"><span data-stu-id="e56e2-131">You can look for a package that has multiple compatibilities by using the syntax:</span></span>

<span data-ttu-id="e56e2-132">Tags: „Kompatibilität1“ „Kompatibilität2“</span><span class="sxs-lookup"><span data-stu-id="e56e2-132">Tags: "Compatibility1" "Compatibility2"</span></span>

<span data-ttu-id="e56e2-133">Wenn Sie beispielsweise nach einem Paket mit PowerShell Core-Kompatibilität suchen, das sowohl auf Windows- als auch auf Linux-Computern ausgeführt werden kann, verwenden Sie diese Suchtags:</span><span class="sxs-lookup"><span data-stu-id="e56e2-133">For example, if you are looking for a package with PowerShell Core Compatibility that runs on both my Windows and Linux machines, use the search tags:</span></span>

<span data-ttu-id="e56e2-134">Tags: „PSEdition_Core“ „Windows“ „Linux“</span><span class="sxs-lookup"><span data-stu-id="e56e2-134">Tags: "PSEdition_Core" "Windows" "Linux"</span></span>

<span data-ttu-id="e56e2-135">Wenn Sie über PowerShell suchen möchten, können Sie folgendermaßen `Find-Module` (und die anderen Cmdlets im PowerShellGet-Modul) verwenden:</span><span class="sxs-lookup"><span data-stu-id="e56e2-135">To search using PowerShell, you can use the `Find-Module` (and the other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="e56e2-136">Weitere Informationen zum Erstellen und Suchen von Paketen mit kompatiblen PowerShell-Editionen</span><span class="sxs-lookup"><span data-stu-id="e56e2-136">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="e56e2-137">Module mit PowerShell-Editionen</span><span class="sxs-lookup"><span data-stu-id="e56e2-137">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="e56e2-138">Skripts mit PowerShell-Editionen</span><span class="sxs-lookup"><span data-stu-id="e56e2-138">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
