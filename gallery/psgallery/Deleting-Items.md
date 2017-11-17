---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: "Löschen von Elementen | MSDN"
ms.openlocfilehash: 00452f9b6625a51e95f3f46dbd66291fa20e17ad
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="deleting-items"></a><span data-ttu-id="59ac1-103">Löschen von Elementen</span><span class="sxs-lookup"><span data-stu-id="59ac1-103">Deleting items</span></span>

<span data-ttu-id="59ac1-104">Der PowerShell-Katalog unterstützt nicht das permanente Löschen von Objekten, da es dadurch bei jedem zu Fehlern kommt, der von deren Verfügbarkeit abhängig ist.</span><span class="sxs-lookup"><span data-stu-id="59ac1-104">The PowerShell Gallery does not support permanent deletion of items, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="59ac1-105">Stattdessen unterstützt der PowerShell-Katalog über die Elementverwaltungsseite auf der Website eine Möglichkeit zum Entfernen eines Elements aus den Listen.</span><span class="sxs-lookup"><span data-stu-id="59ac1-105">Instead, the PowerShell Gallery supports a way to 'unlist' an item, which can be done in the item management page on the web site.</span></span> <span data-ttu-id="59ac1-106">Wenn ein Element aus den Listen entfernt wird, wird es in der Suche und in den Elementlisten nicht mehr angezeigt. Dies gilt sowohl für den PowerShell-Katalog als auch für die PowerShellGet-Befehle.</span><span class="sxs-lookup"><span data-stu-id="59ac1-106">When an item is unlisted, it no longer shows up in search and in any item listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span> <span data-ttu-id="59ac1-107">Durch Angabe der genauen Version kann es jedoch weiterhin heruntergeladen werden, sodass automatisierte Skripts weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="59ac1-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="59ac1-108">Wenn Sie in eine besonderen Situation der Ansicht sind, dass eines Ihrer Elemente gelöscht werden muss, kann dies durch das PowerShell-Katalogteam manuell erledigt werden.</span><span class="sxs-lookup"><span data-stu-id="59ac1-108">If you run into an exceptional situation where you think one of your items must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span> <span data-ttu-id="59ac1-109">Wenn beispielsweise ein Problem mit einer Urheberrechtsverletzung oder mit potenziell schädlichen Inhalten vorliegt, könnte ein berechtigter Grund für das Löschen des Elements vorliegen.</span><span class="sxs-lookup"><span data-stu-id="59ac1-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span> <span data-ttu-id="59ac1-110">In diesem Fall sollten Sie über den [PowerShell-Katalog] (http://www.PowerShellGallery.com) eine Supportanfrage senden.</span><span class="sxs-lookup"><span data-stu-id="59ac1-110">You should submit a support request through [PowerShell Gallery] (http://www.PowerShellGallery.com) in that case.</span></span>

