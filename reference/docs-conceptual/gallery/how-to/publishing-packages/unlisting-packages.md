---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Entfernen von Paketen aus der Liste
ms.openlocfilehash: 4291b910dcea65b2ca241e55838ea00d4ec53ee4
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692366"
---
# <a name="unlisting-packages"></a><span data-ttu-id="ece94-103">Entfernen von Paketen aus der Liste</span><span class="sxs-lookup"><span data-stu-id="ece94-103">Unlisting Packages</span></span>

<span data-ttu-id="ece94-104">**Weshalb wird keine Option zum Entfernen von Paketen aus dem PowerShell-Katalog angezeigt?**</span><span class="sxs-lookup"><span data-stu-id="ece94-104">**Why is removing a package from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="ece94-105">Der PowerShell-Katalog unterstützt nicht das endgültige Löschen von Paketen durch Benutzer.</span><span class="sxs-lookup"><span data-stu-id="ece94-105">The PowerShell Gallery does not support users permanently deleting their packages.</span></span>
<span data-ttu-id="ece94-106">So können andere Benutzer Abhängigkeiten von Ihren Paketen festlegen, ohne darauf zu achten, ob diese in Zukunft verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="ece94-106">This enables others to take dependencies on your packages without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="ece94-107">Wenn das Pester-Modul z. B. vom Azure-Modul abhängig ist und das Azure-Modul aus dem Katalog entfernt wird, können Benutzer das Pester-Modul nicht mehr verwenden.</span><span class="sxs-lookup"><span data-stu-id="ece94-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then users can no longer use the Pester module.</span></span>

<span data-ttu-id="ece94-108">Anstatt ein Paket zu entfernen, können Sie die Auflistung aufheben.</span><span class="sxs-lookup"><span data-stu-id="ece94-108">Instead of removing a package you can unlist it.</span></span>

<span data-ttu-id="ece94-109">**Was geschieht, wenn ein Paket aus der Liste im PowerShell-Katalog entfernt wird?**</span><span class="sxs-lookup"><span data-stu-id="ece94-109">**What does unlisting a package on PowerShell Gallery do?**</span></span>

<span data-ttu-id="ece94-110">Wenn ein Paket, z. B. ein Modul oder ein Skript, aus der Liste im PowerShell-Katalog entfernt wird, wird es nicht länger auf der Registerkarte „Pakete“ angezeigt. Außerdem werden aus der Liste entfernte Pakete nicht mehr über die Suchleiste gefunden.</span><span class="sxs-lookup"><span data-stu-id="ece94-110">Unlisting a package such as a module or script in the PowerShell Gallery removes it from the Packages tab. In addition, unlisted packages will not be discoverable using the search bar.</span></span>
<span data-ttu-id="ece94-111">Pakete, die aus der Liste entfernt wurden, können nur bei Angabe des genauen Namens und der Version des Pakets herunterladen werden.</span><span class="sxs-lookup"><span data-stu-id="ece94-111">The only way to download an unlisted package is to specify the exact name and version of the package.</span></span>
<span data-ttu-id="ece94-112">Folglich treten infolge des Entfernens eines Pakets aus der Liste keine Probleme bei Modulen oder Skripts auf, die von diesem Paket abhängen.</span><span class="sxs-lookup"><span data-stu-id="ece94-112">Because of this, the unlisting of a package will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="ece94-113">Um Ihr Paket aus der Liste zu entfernen, rufen Sie die Seite „Paketdetails“ auf, und wählen Sie „Modul löschen“ aus.</span><span class="sxs-lookup"><span data-stu-id="ece94-113">To unlist your package, visit the package details page and select 'Delete Module'.</span></span> <span data-ttu-id="ece94-114">Deaktivieren Sie das Kontrollkästchen „Aufgelistet“, und wählen Sie „Speichern“ aus.</span><span class="sxs-lookup"><span data-stu-id="ece94-114">Uncheck the 'Listed' checkbox, and select 'Save'.</span></span>

<span data-ttu-id="ece94-115">**Wie kann ich ein Paket entfernen?**</span><span class="sxs-lookup"><span data-stu-id="ece94-115">**How can I remove a package?**</span></span>

<span data-ttu-id="ece94-116">Wenn ein Paket gelöscht werden muss, wenden Sie sich an die PowerShell-Katalogadministratoren.</span><span class="sxs-lookup"><span data-stu-id="ece94-116">If you experience a scenario where package deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="ece94-117">In folgenden Fällen ist das Löschen eines Elements zulässig:</span><span class="sxs-lookup"><span data-stu-id="ece94-117">Valid deletion scenarios are:</span></span>

- <span data-ttu-id="ece94-118">Probleme aufgrund von Urheberrechtsverletzungen.</span><span class="sxs-lookup"><span data-stu-id="ece94-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="ece94-119">Das Paket enthält potenziell schädlichen Inhalt.</span><span class="sxs-lookup"><span data-stu-id="ece94-119">Package contains potentially harmful content.</span></span>
- <span data-ttu-id="ece94-120">Das Paket enthält sensible Daten.</span><span class="sxs-lookup"><span data-stu-id="ece94-120">Package contains sensitive data.</span></span>

<span data-ttu-id="ece94-121">Um eine Anforderung zum Löschen eines Pakets an die PowerShell-Katalogadministratoren zu senden, wählen Sie auf der Seite „Paketdetails“ die Option „Support kontaktieren“ aus.</span><span class="sxs-lookup"><span data-stu-id="ece94-121">To submit a Delete Package Request to the PowerShell Gallery Administrators, visit your package's detail page and select Contact Support.</span></span>
