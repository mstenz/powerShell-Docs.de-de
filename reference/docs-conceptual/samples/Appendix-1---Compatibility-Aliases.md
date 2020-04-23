---
ms.date: 09/09/2019
keywords: powershell,cmdlet
title: Anhang 1 – Kompatibilitätsaliase
ms.openlocfilehash: 2351fdf23711fe1417f7e3fc3cca5b642d5a59fc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "70848159"
---
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="7481a-103">Anhang 1: Kompatibilitätsaliase</span><span class="sxs-lookup"><span data-stu-id="7481a-103">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="7481a-104">PowerShell verfügt über mehrere Aliase, die **UNIX**- und **cmd.exe**-Benutzern ermöglichen, vertraute Befehle zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="7481a-104">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="7481a-105">Die Befehle, das zugehörige PowerShell-Cmdlet und der PowerShell-Alias sind in der folgenden Tabelle aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="7481a-105">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|<span data-ttu-id="7481a-106">Befehl „cmd. exe“</span><span class="sxs-lookup"><span data-stu-id="7481a-106">cmd.exe command</span></span>|<span data-ttu-id="7481a-107">UNIX-Befehl</span><span class="sxs-lookup"><span data-stu-id="7481a-107">UNIX command</span></span>|<span data-ttu-id="7481a-108">PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7481a-108">PowerShell cmdlet</span></span>|<span data-ttu-id="7481a-109">PowerShell-Alias</span><span class="sxs-lookup"><span data-stu-id="7481a-109">PowerShell alias</span></span>|
|---------------|----------------|--------------|------------|
|<span data-ttu-id="7481a-110">**cls**</span><span class="sxs-lookup"><span data-stu-id="7481a-110">**cls**</span></span>|<span data-ttu-id="7481a-111">**Löschen**</span><span class="sxs-lookup"><span data-stu-id="7481a-111">**clear**</span></span>|<span data-ttu-id="7481a-112">`Clear-Host` (Funktion)</span><span class="sxs-lookup"><span data-stu-id="7481a-112">`Clear-Host` (function)</span></span>|`cls`|
|<span data-ttu-id="7481a-113">**copy**</span><span class="sxs-lookup"><span data-stu-id="7481a-113">**copy**</span></span>|<span data-ttu-id="7481a-114">**cp**</span><span class="sxs-lookup"><span data-stu-id="7481a-114">**cp**</span></span>|`Copy-Item`|`cpi`|
|<span data-ttu-id="7481a-115">**dir**</span><span class="sxs-lookup"><span data-stu-id="7481a-115">**dir**</span></span>|<span data-ttu-id="7481a-116">**ls**</span><span class="sxs-lookup"><span data-stu-id="7481a-116">**ls**</span></span>|`Get-ChildItem`|`gci`|
|<span data-ttu-id="7481a-117">**type**</span><span class="sxs-lookup"><span data-stu-id="7481a-117">**type**</span></span>|<span data-ttu-id="7481a-118">**cat**</span><span class="sxs-lookup"><span data-stu-id="7481a-118">**cat**</span></span>|`Get-Content`|`gc`|
|<span data-ttu-id="7481a-119">**move**</span><span class="sxs-lookup"><span data-stu-id="7481a-119">**move**</span></span>|<span data-ttu-id="7481a-120">**mv**</span><span class="sxs-lookup"><span data-stu-id="7481a-120">**mv**</span></span>|`Move-Item`|`mi`|
|<span data-ttu-id="7481a-121">**md**</span><span class="sxs-lookup"><span data-stu-id="7481a-121">**md**</span></span>|<span data-ttu-id="7481a-122">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="7481a-122">**mkdir**</span></span>|`New-Item`|`ni`|
|<span data-ttu-id="7481a-123">**pushd**</span><span class="sxs-lookup"><span data-stu-id="7481a-123">**pushd**</span></span>|<span data-ttu-id="7481a-124">**pushd**</span><span class="sxs-lookup"><span data-stu-id="7481a-124">**pushd**</span></span>|`Push-Location`|`pushd`|
|<span data-ttu-id="7481a-125">**popd**</span><span class="sxs-lookup"><span data-stu-id="7481a-125">**popd**</span></span>|<span data-ttu-id="7481a-126">**popd**</span><span class="sxs-lookup"><span data-stu-id="7481a-126">**popd**</span></span>|`Pop-Location`|`popd`|
|<span data-ttu-id="7481a-127">**del**, **erase**, **rd**, **rmdir**</span><span class="sxs-lookup"><span data-stu-id="7481a-127">**del**, **erase**, **rd**, **rmdir**</span></span>|<span data-ttu-id="7481a-128">**rm**</span><span class="sxs-lookup"><span data-stu-id="7481a-128">**rm**</span></span>|`Remove-Item`|`ri`|
|<span data-ttu-id="7481a-129">**ren**</span><span class="sxs-lookup"><span data-stu-id="7481a-129">**ren**</span></span>|<span data-ttu-id="7481a-130">**mv**</span><span class="sxs-lookup"><span data-stu-id="7481a-130">**mv**</span></span>|`Rename-Item`|`rni`|
|<span data-ttu-id="7481a-131">**cd**, **chdir**</span><span class="sxs-lookup"><span data-stu-id="7481a-131">**cd**, **chdir**</span></span>|<span data-ttu-id="7481a-132">**cd**</span><span class="sxs-lookup"><span data-stu-id="7481a-132">**cd**</span></span>|`Set-Location`|`sl`|

<span data-ttu-id="7481a-133">Verwenden Sie das [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias)-Cmdlet, um die PowerShell-Aliase zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="7481a-133">To find the PowerShell aliases, use the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet.</span></span> <span data-ttu-id="7481a-134">Um die Aliase eines Cmdlets anzuzeigen, verwenden Sie den **Definition**-Parameter, und geben Sie den Namen des Cmdlets an.</span><span class="sxs-lookup"><span data-stu-id="7481a-134">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="7481a-135">Verwenden Sie alternativ den **Name**-Parameter, um den Cmdlet-Namen eines Alias zu suchen.</span><span class="sxs-lookup"><span data-stu-id="7481a-135">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```
