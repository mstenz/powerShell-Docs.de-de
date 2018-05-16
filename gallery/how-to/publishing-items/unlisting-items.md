---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: Entfernen von Elementen aus der Liste
ms.openlocfilehash: 35dcd283ddace5aec62d692b0ede12ae0bada765
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="unlisting-items"></a><span data-ttu-id="6adb9-103">Entfernen von Elementen aus der Liste</span><span class="sxs-lookup"><span data-stu-id="6adb9-103">Unlisting items</span></span>

<span data-ttu-id="6adb9-104">**Weshalb ist keine Option zum Entfernen von Elementen aus dem PowerShell-Katalog verfügbar?**</span><span class="sxs-lookup"><span data-stu-id="6adb9-104">**Why is removing an item from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="6adb9-105">Der PowerShell-Katalog bietet keine Unterstützung für das endgültige Löschen von Elementen durch Benutzer.</span><span class="sxs-lookup"><span data-stu-id="6adb9-105">The PowerShell Gallery does not support users permanently deleting their items.</span></span>
<span data-ttu-id="6adb9-106">So können andere Benutzer Abhängigkeiten von Ihren Elementen festlegen, ohne sich Gedanken darüber machen zu müssen, ob diese Elemente in der Zukunft verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="6adb9-106">This enables others to take dependencies on your items without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="6adb9-107">Wenn das Pester-Modul z. B. vom Azure-Modul abhängt und das Azure-Modul aus dem Katalog entfernt wird, kann der Benutzer das Pester-Modul nicht mehr verwenden.</span><span class="sxs-lookup"><span data-stu-id="6adb9-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="6adb9-108">Anstatt ein Element zu löschen, können Sie es jedoch aus der Liste entfernen.</span><span class="sxs-lookup"><span data-stu-id="6adb9-108">Instead of removing an item, however, you can unlist it instead.</span></span>

<span data-ttu-id="6adb9-109">**Was geschieht, wenn ein Element aus der Liste im PowerShell-Katalog entfernt wird?**</span><span class="sxs-lookup"><span data-stu-id="6adb9-109">**What does unlisting an item on PowerShell Gallery do?**</span></span>

<span data-ttu-id="6adb9-110">Wenn ein Element, z. B. ein Modul oder ein Skript, aus der Liste des PowerShell-Katalogs entfernt wird, wird es nicht länger auf der Registerkarte „Elemente“ angezeigt. Außerdem können Elemente, die aus der Liste entfernt wurden, nicht mehr über die Suchleiste gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="6adb9-110">Unlisting an item such as module or script on PowerShell Gallery will remove it from the Items tab. In addition, unlisted items will not be discoverable using the search bar.</span></span>
<span data-ttu-id="6adb9-111">Elemente, die aus der Liste entfernt wurden, können lediglich herunterladen werden, wenn der exakte Name und die Version des Elements angeben werden.</span><span class="sxs-lookup"><span data-stu-id="6adb9-111">The only way to download an unlisted item is to specify the exact name and version of the item.</span></span>
<span data-ttu-id="6adb9-112">Folglich hat das Entfernen eines Elements aus der Liste nicht zur Folge, dass Probleme bei Modulen oder Skripts auftreten, die von diesem Element abhängen.</span><span class="sxs-lookup"><span data-stu-id="6adb9-112">Because of this, the unlisting of an item will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="6adb9-113">Um Ihr Element aus der Liste zu entfernen, wechseln Sie zur Seite mit den Elementdetails, und wählen Sie „Element löschen“.</span><span class="sxs-lookup"><span data-stu-id="6adb9-113">To unlist your item, visit the item details page and select 'Delete Item'.</span></span> <span data-ttu-id="6adb9-114">Deaktivieren Sie das Kontrollkästchen „Aufgelistet“, und klicken Sie auf „Speichern“.</span><span class="sxs-lookup"><span data-stu-id="6adb9-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="6adb9-115">**Wie kann ich ein Element entfernen?**</span><span class="sxs-lookup"><span data-stu-id="6adb9-115">**How can I remove an item?**</span></span>

<span data-ttu-id="6adb9-116">Wenn ein Element gelöscht werden muss, wenden Sie sich an die PowerShell-Katalogadministratoren.</span><span class="sxs-lookup"><span data-stu-id="6adb9-116">If you experience a scenario where item deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="6adb9-117">In folgenden Fällen ist das Löschen eines Elements zulässig:</span><span class="sxs-lookup"><span data-stu-id="6adb9-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="6adb9-118">Probleme aufgrund von Urheberrechtsverletzungen.</span><span class="sxs-lookup"><span data-stu-id="6adb9-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="6adb9-119">Das Element enthält potenziell schädlichen Inhalt.</span><span class="sxs-lookup"><span data-stu-id="6adb9-119">Item contains potentially harmful content.</span></span>
- <span data-ttu-id="6adb9-120">Das Element enthält sensible Daten.</span><span class="sxs-lookup"><span data-stu-id="6adb9-120">Item contains sensitive data.</span></span>

<span data-ttu-id="6adb9-121">Um eine Anforderung zum Löschen eines Elements an die PowerShell-Katalogadministratoren zu senden, wählen Sie auf der Seite mit den Elementdetails die Option „Support kontaktieren“.</span><span class="sxs-lookup"><span data-stu-id="6adb9-121">To submit a Delete Item Request to the PowerShell Gallery Administrators, visit your item's detail page and select Contact Support.</span></span>