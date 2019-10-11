---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSCAutomationHostEnabled (Registrierungsschlüssel)
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954267"
---
><span data-ttu-id="15904-103">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="15904-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="15904-104">DSCAutomationHostEnabled (Registrierungsschlüssel)</span><span class="sxs-lookup"><span data-stu-id="15904-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="15904-105">DSC verwendet den Registrierungsschlüssel **DSCAutomationHostEnabled** unter **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System**, um die Konfiguration des Computer beim ersten Start zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="15904-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="15904-106">**DSCAutomationHostEnabled** unterstützt drei Modi:</span><span class="sxs-lookup"><span data-stu-id="15904-106">**DSCAutomationHostEnabled** supports three modes:</span></span>

|  <span data-ttu-id="15904-107">DSCAutomationHostEnabled-Wert</span><span class="sxs-lookup"><span data-stu-id="15904-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="15904-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="15904-108">Description</span></span>   |
|---|---|
<span data-ttu-id="15904-109">0</span><span class="sxs-lookup"><span data-stu-id="15904-109">0</span></span> | <span data-ttu-id="15904-110">Konfiguration des Computers beim Hochfahren deaktivieren</span><span class="sxs-lookup"><span data-stu-id="15904-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="15904-111">1</span><span class="sxs-lookup"><span data-stu-id="15904-111">1</span></span> | <span data-ttu-id="15904-112">Konfiguration des Computers beim Hochfahren aktivieren</span><span class="sxs-lookup"><span data-stu-id="15904-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="15904-113">2</span><span class="sxs-lookup"><span data-stu-id="15904-113">2</span></span> | <span data-ttu-id="15904-114">Konfiguration des Computers nur dann aktivieren, wenn DSC sich im Status „ausstehend“ oder „aktuell“ befindet.</span><span class="sxs-lookup"><span data-stu-id="15904-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="15904-115">Dies ist der Standardwert.</span><span class="sxs-lookup"><span data-stu-id="15904-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="15904-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="15904-116">See Also</span></span>

<span data-ttu-id="15904-117">Ein Beispiel dazu, wie Sie dieses Features zum Ausführen von Konfigurationen beim ersten Hochfahren verwenden, finden Sie unter [Konfigurieren eines virtuellen Computers beim ersten Hochfahren mithilfe von DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="15904-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
