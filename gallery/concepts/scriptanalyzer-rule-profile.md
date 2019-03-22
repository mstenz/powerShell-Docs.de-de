---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 'ScriptAnalyzer-Regel: Profil für den Katalog'
ms.openlocfilehash: 939f01dece56b283dbe6e03c888f42ff866707af
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2019
ms.locfileid: "58059591"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="a4402-103">ScriptAnalyzer-Regel: Profil für den Katalog</span><span class="sxs-lookup"><span data-stu-id="a4402-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="a4402-104">Um die Qualität der im PowerShell-Katalog veröffentlichen Pakete sicherzustellen, werden [PowerShell ScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer)-Regeln ausgeführt, die die übermittelten Skripts auf Verstöße überprüfen.</span><span class="sxs-lookup"><span data-stu-id="a4402-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="a4402-105">Eine Liste der ausgeführte Regeln finden Sie auf der [GitHub-Seite von ScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span><span class="sxs-lookup"><span data-stu-id="a4402-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="a4402-106">Bei Bedenken bezüglich der ausgeführten Regeln wenden Sie sich bitte an die Administratoren des PowerShell-Katalogs oder melden Sie ein Problem mit ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="a4402-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalyzer.</span></span>

<span data-ttu-id="a4402-107">Die ScriptAnalyzer-Ergebnisse werden im kommenden Release auf jeder einzelnen Paketseite des Katalogs angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a4402-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="a4402-108">Paketbesitzern wird empfohlen, ihre Pakete zu überprüfen, damit veröffentlichte Pakete keine schwerwiegenden Fehler enthalten.</span><span class="sxs-lookup"><span data-stu-id="a4402-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
