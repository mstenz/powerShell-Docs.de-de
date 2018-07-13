---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Löschen von Elementen
ms.openlocfilehash: 454cd404437bf1c31b9a1b81cd9dd0ac81e6b0f6
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893092"
---
# <a name="deleting-items"></a><span data-ttu-id="55174-103">Löschen von Elementen</span><span class="sxs-lookup"><span data-stu-id="55174-103">Deleting items</span></span>

<span data-ttu-id="55174-104">Der PowerShell-Katalog unterstützt nicht das permanente Löschen von Objekten, da es dadurch bei jedem zu Fehlern kommt, der von deren Verfügbarkeit abhängig ist.</span><span class="sxs-lookup"><span data-stu-id="55174-104">The PowerShell Gallery does not support permanent deletion of items, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="55174-105">Stattdessen unterstützt der PowerShell-Katalog über die Elementverwaltungsseite auf der Website eine Möglichkeit zum Entfernen eines Elements aus den Listen.</span><span class="sxs-lookup"><span data-stu-id="55174-105">Instead, the PowerShell Gallery supports a way to 'unlist' an item, which can be done in the item management page on the web site.</span></span>
<span data-ttu-id="55174-106">Wenn ein Element aus den Listen entfernt wird, wird es in der Suche und in den Elementlisten nicht mehr angezeigt. Dies gilt sowohl für den PowerShell-Katalog als auch für die PowerShellGet-Befehle.</span><span class="sxs-lookup"><span data-stu-id="55174-106">When an item is unlisted, it no longer shows up in search and in any item listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="55174-107">Durch Angabe der genauen Version kann es jedoch weiterhin heruntergeladen werden, sodass automatisierte Skripts weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="55174-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="55174-108">Wenn Sie in eine besonderen Situation der Ansicht sind, dass eines Ihrer Elemente gelöscht werden muss, kann dies durch das PowerShell-Katalogteam manuell erledigt werden.</span><span class="sxs-lookup"><span data-stu-id="55174-108">If you run into an exceptional situation where you think one of your items must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="55174-109">Wenn beispielsweise ein Problem mit einer Urheberrechtsverletzung oder mit potenziell schädlichen Inhalten vorliegt, könnte ein berechtigter Grund für das Löschen des Elements vorliegen.</span><span class="sxs-lookup"><span data-stu-id="55174-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="55174-110">In diesem Fall sollten Sie über den [PowerShell-Katalog](http://www.PowerShellGallery.com) eine Supportanfrage senden.</span><span class="sxs-lookup"><span data-stu-id="55174-110">You should submit a support request through [PowerShell Gallery](http://www.PowerShellGallery.com) in that case.</span></span>