---
ms.date: 06/12/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSCAutomationHostEnabled (Registrierungsschlüssel)
ms.openlocfilehash: 0f35a798e5b7d51fdfb66e4e79ceab0e36ccea5b
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808332"
---
# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="fae5d-103">DSCAutomationHostEnabled (Registrierungsschlüssel)</span><span class="sxs-lookup"><span data-stu-id="fae5d-103">DSCAutomationHostEnabled registry key</span></span>

> <span data-ttu-id="fae5d-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fae5d-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="fae5d-105">DSC verwendet den Registrierungsschlüssel **DSCAutomationHostEnabled** unter **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System**, um die Konfiguration des Computer beim ersten Start zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="fae5d-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="fae5d-106">**DSCAutomationHostEnabled** unterstützt drei Modi:</span><span class="sxs-lookup"><span data-stu-id="fae5d-106">**DSCAutomationHostEnabled** supports three modes:</span></span>

|  <span data-ttu-id="fae5d-107">DSCAutomationHostEnabled-Wert</span><span class="sxs-lookup"><span data-stu-id="fae5d-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="fae5d-108">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="fae5d-108">Description</span></span>   |
|---|---|
<span data-ttu-id="fae5d-109">0</span><span class="sxs-lookup"><span data-stu-id="fae5d-109">0</span></span> | <span data-ttu-id="fae5d-110">Konfiguration des Computers beim Hochfahren deaktivieren</span><span class="sxs-lookup"><span data-stu-id="fae5d-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="fae5d-111">1</span><span class="sxs-lookup"><span data-stu-id="fae5d-111">1</span></span> | <span data-ttu-id="fae5d-112">Konfiguration des Computers beim Hochfahren aktivieren</span><span class="sxs-lookup"><span data-stu-id="fae5d-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="fae5d-113">2</span><span class="sxs-lookup"><span data-stu-id="fae5d-113">2</span></span> | <span data-ttu-id="fae5d-114">Konfiguration des Computers nur dann aktivieren, wenn DSC sich im Status „ausstehend“ oder „aktuell“ befindet.</span><span class="sxs-lookup"><span data-stu-id="fae5d-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="fae5d-115">Dies ist der Standardwert.</span><span class="sxs-lookup"><span data-stu-id="fae5d-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="fae5d-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fae5d-116">See Also</span></span>

<span data-ttu-id="fae5d-117">Ein Beispiel dazu, wie Sie dieses Features zum Ausführen von Konfigurationen beim ersten Hochfahren verwenden, finden Sie unter [Konfigurieren eines virtuellen Computers beim ersten Hochfahren mithilfe von DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="fae5d-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
