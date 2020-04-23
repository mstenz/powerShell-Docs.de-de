---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Löschen von Paketen
ms.openlocfilehash: 6bfb43b95e51d38bd606198cb8d2d9af0aa0be1e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71327931"
---
# <a name="deleting-packages"></a><span data-ttu-id="ee3eb-103">Löschen von Paketen</span><span class="sxs-lookup"><span data-stu-id="ee3eb-103">Deleting Packages</span></span>

<span data-ttu-id="ee3eb-104">Der PowerShell-Katalog unterstützt nicht das permanente Löschen von Paketen, da es dadurch bei jedem Benutzer zu Fehlern kommt, der diese Pakete unbedingt benötigt.</span><span class="sxs-lookup"><span data-stu-id="ee3eb-104">The PowerShell Gallery does not support permanent deletion of packages, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="ee3eb-105">Stattdessen unterstützt der PowerShell-Katalog eine Möglichkeit zum Entfernen eines Pakets aus den Listen – dies erfolgt über die Paketverwaltungsseite auf der Website.</span><span class="sxs-lookup"><span data-stu-id="ee3eb-105">Instead, the PowerShell Gallery supports a way to 'unlist' a package, which can be done in the package management page on the web site.</span></span>
<span data-ttu-id="ee3eb-106">Wenn ein Paket aus den Listen entfernt ist, wird es in der Suche und den Paketlisten nicht mehr angezeigt. Dies gilt sowohl für den PowerShell-Katalog als auch für die PowerShellGet-Befehle.</span><span class="sxs-lookup"><span data-stu-id="ee3eb-106">When a package is unlisted, it no longer shows up in search and in any package listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="ee3eb-107">Durch Angabe der genauen Version kann es jedoch weiterhin heruntergeladen werden, sodass automatisierte Skripts weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="ee3eb-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="ee3eb-108">Wenn Sie in einer besonderen Situation der Ansicht sind, dass eines Ihrer Pakete gelöscht werden muss, kann dies durch das PowerShell-Katalogteam manuell durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="ee3eb-108">If you run into an exceptional situation where you think one of your packages must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="ee3eb-109">Wenn beispielsweise ein Problem mit einer Urheberrechtsverletzung oder mit potenziell schädlichen Inhalten vorliegt, könnte ein berechtigter Grund für das Löschen des Elements vorliegen.</span><span class="sxs-lookup"><span data-stu-id="ee3eb-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="ee3eb-110">In diesem Fall sollten Sie über den [PowerShell-Katalog](https://www.PowerShellGallery.com) eine Supportanfrage senden.</span><span class="sxs-lookup"><span data-stu-id="ee3eb-110">You should submit a support request through [PowerShell Gallery](https://www.PowerShellGallery.com) in that case.</span></span>
