---
ms.date: 03/15/2018
keywords: dsc,powershell,configuration,setup
title: Verwenden von DSC in Microsoft Azure
ms.openlocfilehash: 54a317a415ff12c3d270897f414cba88716f0728
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953957"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="691fc-103">Verwenden von DSC in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="691fc-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="691fc-104">Desired State Configuration (Konfiguration des gewünschten Zustands, DSC) wird in Microsoft Azure über den [Azure DSC-Erweiterungshandler](/azure/virtual-machines/extensions/dsc-overview) und über [Azure Automation DSC](/azure/automation/automation-dsc-overview) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="691fc-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="691fc-105">Azure DSC-Erweiterungshandler</span><span class="sxs-lookup"><span data-stu-id="691fc-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="691fc-106">Die Azure DSC-Erweiterung ermöglicht, dass in Microsoft Azure gehostete virtuelle Computer mit DSC verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="691fc-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span>
<span data-ttu-id="691fc-107">Weitere Informationen finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="691fc-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="691fc-108">Azure DSC-Erweiterungshandler</span><span class="sxs-lookup"><span data-stu-id="691fc-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="691fc-109">Windows VMSS und DSC mit Azure Resource Manager-Vorlagen</span><span class="sxs-lookup"><span data-stu-id="691fc-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="691fc-110">Übergeben von Anmeldeinformationen an den Azure DSC-Erweiterungshandler</span><span class="sxs-lookup"><span data-stu-id="691fc-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="691fc-111">Versionsgeschichte der Azure Desired State Configuration-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="691fc-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="691fc-112">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="691fc-112">Azure Automation DSC</span></span>

<span data-ttu-id="691fc-113">Der [Azure Automation-Dienst](https://azure.microsoft.com/en-us/services/automation/) ermöglicht Ihnen die Verwaltung von DSC-Konfigurationen, Ressourcen und verwalteten Knoten in Azure.</span><span class="sxs-lookup"><span data-stu-id="691fc-113">The [Azure Automation service](https://azure.microsoft.com/en-us/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="691fc-114">Weitere Informationen finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="691fc-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="691fc-115">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="691fc-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="691fc-116">Erste Schritte mit Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="691fc-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="691fc-117">Onboarding von Computern für die Verwaltung von Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="691fc-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)