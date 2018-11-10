---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 'ScriptAnalyzer-Regel: Profil für den Katalog'
ms.openlocfilehash: d91a88981cc2f3269a1f8b6ee864f8333a2f097c
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002495"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="5b5dd-103">ScriptAnalyzer-Regel: Profil für den Katalog</span><span class="sxs-lookup"><span data-stu-id="5b5dd-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="5b5dd-104">Um die Qualität der im PowerShell-Katalog veröffentlichen Pakete sicherzustellen, werden [PowerShell ScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer)-Regeln ausgeführt, die die übermittelten Skripts auf Verstöße überprüfen.</span><span class="sxs-lookup"><span data-stu-id="5b5dd-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="5b5dd-105">Eine Liste der ausgeführte Regeln finden Sie auf der [GitHub-Seite von ScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span><span class="sxs-lookup"><span data-stu-id="5b5dd-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="5b5dd-106">Bei Bedenken bezüglich der ausgeführten Regeln wenden Sie sich bitte an die Administratoren des PowerShell-Katalogs oder melden Sie ein Problem mit ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="5b5dd-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="5b5dd-107">Die ScriptAnalyzer-Ergebnisse werden im kommenden Release auf jeder einzelnen Paketseite des Katalogs angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5b5dd-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="5b5dd-108">Paketbesitzern wird empfohlen, ihre Pakete zu überprüfen, damit veröffentlichte Pakete keine schwerwiegenden Fehler enthalten.</span><span class="sxs-lookup"><span data-stu-id="5b5dd-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
