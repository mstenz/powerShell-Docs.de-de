---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: gallery,powershell,cmdlet,psgallery
title: Pakete mit kompatiblen PowerShell-Editionen oder Betriebssystem
ms.openlocfilehash: 8230866561d3021379a48cc2c83fb4104a4058c1
ms.sourcegitcommit: d396d0e4cfe3d279f399c17e7337380a31d373ac
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747703"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a><span data-ttu-id="2571c-103">Pakete mit kompatiblen PowerShell-Editionen oder Betriebssystemen</span><span class="sxs-lookup"><span data-stu-id="2571c-103">Packages with compatible PowerShell Editions or Operating Systems</span></span>

<span data-ttu-id="2571c-104">Ab Version 5.1 steht PowerShell in verschiedenen Editionen zur Verfügung, die unterschiedliche Featuregruppen und Plattformkompatibilität bieten.</span><span class="sxs-lookup"><span data-stu-id="2571c-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibilities.</span></span>

## <a name="searching-by-powershell-edition"></a><span data-ttu-id="2571c-105">Suchen nach PowerShell-Editionen</span><span class="sxs-lookup"><span data-stu-id="2571c-105">Searching by PowerShell Edition</span></span> 
<span data-ttu-id="2571c-106">Die zwei Editionen von Powershell sind:</span><span class="sxs-lookup"><span data-stu-id="2571c-106">The two editions of Powershell are:</span></span>
- <span data-ttu-id="2571c-107">Desktop Edition Basiert auf .NET Framework und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter Vollversionen von Windows wie Server Core und Windows-Desktop ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2571c-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="2571c-108">**Core-Edition:** Basiert auf .NET Core und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter funktionsreduzierten Versionen von Windows wie Nano Server und Windows IoT ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2571c-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="2571c-109">PowerShell-Katalog können Sie Pakete, die kompatibel für bestimmte PowerShell-Editionen filtern</span><span class="sxs-lookup"><span data-stu-id="2571c-109">PowerShell Gallery allows you to filter packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="2571c-110">Verfügt ein Paket kompatible angegebene PSEditions, sie als Teil des "PowerShell-Editionen" aufgeführt sind in der Seite für Pakete anzeigen und auch in Paketen Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="2571c-110">If a package has compatible PSEditions specified, they are listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>
<span data-ttu-id="2571c-111">Sie können auch nach kompatiblen Paketen, die mithilfe von PowerShell suchen.</span><span class="sxs-lookup"><span data-stu-id="2571c-111">You can also search for compatible packages using PowerShell.</span></span>

![Seite des Elements mit PSEditions](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a><span data-ttu-id="2571c-113">Suchen Sie nach Paketen in der Benutzeroberfläche des Katalogs, die auf PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="2571c-113">Search for packages in the gallery UI that work on PowerShell Core</span></span>

<span data-ttu-id="2571c-114">Verwenden Sie die Tags „PSEdition_Desktop“ und „PSEdition_Core“, um die Pakete im PowerShell-Katalog zu filtern.</span><span class="sxs-lookup"><span data-stu-id="2571c-114">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="2571c-115">Verwenden Sie das Tag „PSEdition_Core“, um Elemente zu suchen, die mit der PowerShell Core-Edition kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="2571c-115">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Suchergebnisse für Elemente, die mit Core PSEdition kompatibel sind](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="2571c-117">Verwenden Sie das Tag „PSEdition_Desktop“, um Elemente zu suchen, die mit der PowerShell Desktop Edition kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="2571c-117">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Suchergebnisse für Elemente, die mit Desktop PSEdition kompatibel sind](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a><span data-ttu-id="2571c-119">Suchen Sie nach Paketen kompatible mithilfe von PowerShell-Editionen zu finden</span><span class="sxs-lookup"><span data-stu-id="2571c-119">Search for packages to find compatible editions using PowerShell</span></span>
<span data-ttu-id="2571c-120">Sie können Tags für die PowerShell-Edition und Betriebssystem Filtern angeben.</span><span class="sxs-lookup"><span data-stu-id="2571c-120">You can specify tags to filter for the PowerShell edition and OS.</span></span> <span data-ttu-id="2571c-121">Sie verwenden die `Find-Package` Cmdlet angeben der `-Tag` Parameter zum Angeben der Edition (und Betriebssystem) Sie Anzielen.</span><span class="sxs-lookup"><span data-stu-id="2571c-121">You use the `Find-Package` cmdlet specifying the `-Tag` parameter to specify the edition (and OS) you are targeting.</span></span>
<span data-ttu-id="2571c-122">So:</span><span class="sxs-lookup"><span data-stu-id="2571c-122">Like this:</span></span>

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a><span data-ttu-id="2571c-123">Suchen nach Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="2571c-123">Searching by Operating System</span></span> 

<span data-ttu-id="2571c-124">Da PowerShell Core für Windows, Linux und MacOS verfügbar ist, können der Pakete im Katalog für eine beliebige Kombination dieser Betriebssysteme so entworfen werden.</span><span class="sxs-lookup"><span data-stu-id="2571c-124">Since PowerShell Core is available for Windows, Linux, and MacOS, packages in the Gallery may be designed for any combination of these operating systems.</span></span> <span data-ttu-id="2571c-125">Verwenden Sie die folgenden Searchs Tags um Pakete, die vom Betriebssystem markiert zu suchen, in der Benutzeroberfläche des Katalogs:</span><span class="sxs-lookup"><span data-stu-id="2571c-125">In the gallery UI use the following searchs tags to find packages tagged by operating system:</span></span>

- <span data-ttu-id="2571c-126">Tags: "Windows"</span><span class="sxs-lookup"><span data-stu-id="2571c-126">Tags: "Windows"</span></span>
- <span data-ttu-id="2571c-127">Tags: "Linux"</span><span class="sxs-lookup"><span data-stu-id="2571c-127">Tags: "Linux"</span></span>
- <span data-ttu-id="2571c-128">Tags: "MacOS"</span><span class="sxs-lookup"><span data-stu-id="2571c-128">Tags: "MacOS"</span></span> 

<span data-ttu-id="2571c-129">Sie können diese Tags angeben, auf `Find-Module` (und andere Cmdlets im PowerShellGet-Modul) wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="2571c-129">You can specify these tags on `Find-Module` (and other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a><span data-ttu-id="2571c-130">Für mehrere Probleme mit der Suche</span><span class="sxs-lookup"><span data-stu-id="2571c-130">Searching for Multiple Compatibilities</span></span>

<span data-ttu-id="2571c-131">Sie können für ein Paket anzeigen, die über mehrere Probleme mit der Syntax verfügt:</span><span class="sxs-lookup"><span data-stu-id="2571c-131">You can look for a package that has multiple compatibilities by using the syntax:</span></span> 

<span data-ttu-id="2571c-132">Tags "Compatibility1" "Compatibility2"</span><span class="sxs-lookup"><span data-stu-id="2571c-132">Tags: "Compatibility1" "Compatibility2"</span></span> 

<span data-ttu-id="2571c-133">Wenn Sie ein Paket mit PowerShell Core Kompatibilität, die für meine Windows und Linux-Computer ausgeführt wird suchen, verwenden Sie z. B. die Markierungen suchen:</span><span class="sxs-lookup"><span data-stu-id="2571c-133">For example, if you are looking for a package with PowerShell Core Compatibility that runs on both my Windows and Linux machines, use the search tags:</span></span>

<span data-ttu-id="2571c-134">Tags "PSEdition_Core", "Windows", "Linux"</span><span class="sxs-lookup"><span data-stu-id="2571c-134">Tags: "PSEdition_Core" "Windows" "Linux"</span></span> 

<span data-ttu-id="2571c-135">Um mithilfe von PowerShell zu suchen, können Sie die `Find-Module` (und die anderen Cmdlets im PowerShellGet-Modul) wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="2571c-135">To search using PowerShell, you can use the `Find-Module` (and the other cmdlets in the PowerShellGet module), like this:</span></span>

```powewrshell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="2571c-136">Weitere Informationen zum Erstellen und Suchen von Paketen mit kompatiblen PowerShell-Editionen</span><span class="sxs-lookup"><span data-stu-id="2571c-136">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="2571c-137">Module mit PowerShell-Editionen</span><span class="sxs-lookup"><span data-stu-id="2571c-137">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="2571c-138">Skripts mit PowerShell-Editionen</span><span class="sxs-lookup"><span data-stu-id="2571c-138">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
