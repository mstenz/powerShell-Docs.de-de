---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Skript mit kompatiblen PowerShell-Editionen
ms.openlocfilehash: 3cb82fe56e17d0bc41d75f6db69fa7b3b0fdf3f6
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="script-with-compatible-powershell-editions"></a><span data-ttu-id="925a7-103">Skript mit kompatiblen PowerShell-Editionen</span><span class="sxs-lookup"><span data-stu-id="925a7-103">Script with compatible PowerShell editions</span></span>

<span data-ttu-id="925a7-104">Ab Version 5.1 steht PowerShell in verschiedenen Editionen zur Verfügung, die unterschiedliche Featuregruppen und Plattformkompatibilität bieten.</span><span class="sxs-lookup"><span data-stu-id="925a7-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="925a7-105">**Desktop-Edition:** Diese Edition basiert auf .NET Framework und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter Vollversionen von Windows wie Server Core und Windows Desktop ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="925a7-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="925a7-106">**Core-Edition:** Diese Edition basiert auf .NET Core und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter funktionsreduzierten Versionen von Windows wie Nano Server und Windows IoT ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="925a7-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="925a7-107">Die ausgeführte Edition von PowerShell wird in der PSEdition-Eigenschaft von $PSVersionTable angezeigt.</span><span class="sxs-lookup"><span data-stu-id="925a7-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

<span data-ttu-id="925a7-108">Skriptautoren können verhindern, dass ein Skript ausgeführt wird, sofern es nicht in einer kompatiblen Edition von PowerShell mithilfe des Parameters „PSEdition“ in einer „#requires“-Anweisung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="925a7-108">Script authors can prevent a script from executing unless it is run on a compatible edition of PowerShell using the PSEdition parameter on a #requires statement.</span></span>

```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell Core edition. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

<span data-ttu-id="925a7-109">Benutzer des PowerShell-Katalogs können die Liste der Skripts suchen, die in einer bestimmten PowerShell-Edition unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="925a7-109">PowerShell Gallery users can find the list of scripts supported on a specific PowerShell Edition.</span></span>
<span data-ttu-id="925a7-110">Skripts ohne „PSEdition_Desktop“ und „PSEditon_Core“ sollten in PowerShell Desktop keine Probleme bereiten.</span><span class="sxs-lookup"><span data-stu-id="925a7-110">Scripts without PSEdition_Desktop and PSEditon_Core are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell

# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEditon_Desktop

# Find scripts supported on PowerShell Core editions
Find-Script -Tag PSEditon_Core

```

## <a name="more-details"></a><span data-ttu-id="925a7-111">Weitere Details</span><span class="sxs-lookup"><span data-stu-id="925a7-111">More details</span></span>

- [<span data-ttu-id="925a7-112">Module mit PowerShell-Editionen</span><span class="sxs-lookup"><span data-stu-id="925a7-112">Modules with PSEditions</span></span>](module-psedition-support.md)
- [<span data-ttu-id="925a7-113">Unterstützung von PowerShell-Editionen im PowerShell-Katalog</span><span class="sxs-lookup"><span data-stu-id="925a7-113">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-items/searching-by-psedition.md)