---
ms.date: 03/15/2018
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Verwenden von DSC in Microsoft Azure
ms.openlocfilehash: 5b0d577e1fecdeac38c2c5f8e955a2d23b1eb707
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="1e83d-103">Verwenden von DSC in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="1e83d-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="1e83d-104">Desired State Configuration (Konfiguration des gewünschten Zustands, DSC) wird in Microsoft Azure über den [Azure DSC-Erweiterungshandler](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) und über [Azure Automation DSC](/azure/automation/automation-dsc-overview) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="1e83d-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="1e83d-105">Azure DSC-Erweiterungshandler</span><span class="sxs-lookup"><span data-stu-id="1e83d-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="1e83d-106">Die Azure DSC-Erweiterung ermöglicht, dass in Microsoft Azure gehostete virtuelle Computer mit DSC verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="1e83d-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span>
<span data-ttu-id="1e83d-107">Weitere Informationen finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="1e83d-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="1e83d-108">Azure DSC-Erweiterungshandler</span><span class="sxs-lookup"><span data-stu-id="1e83d-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview)
- [<span data-ttu-id="1e83d-109">Windows VMSS und DSC mit Azure Resource Manager-Vorlagen</span><span class="sxs-lookup"><span data-stu-id="1e83d-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-template)
- [<span data-ttu-id="1e83d-110">Übergeben von Anmeldeinformationen an den Azure DSC-Erweiterungshandler</span><span class="sxs-lookup"><span data-stu-id="1e83d-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-credentials)
- [<span data-ttu-id="1e83d-111">Versionsgeschichte der Azure Desired State Configuration-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="1e83d-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="1e83d-112">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="1e83d-112">Azure Automation DSC</span></span>

<span data-ttu-id="1e83d-113">Der [Azure Automation-Dienst](https://azure.microsoft.com/services/automation/) ermöglicht Ihnen die Verwaltung von DSC-Konfigurationen, Ressourcen und verwalteten Knoten in Azure.</span><span class="sxs-lookup"><span data-stu-id="1e83d-113">The [Azure Automation service](https://azure.microsoft.com/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="1e83d-114">Weitere Informationen finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="1e83d-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="1e83d-115">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="1e83d-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="1e83d-116">Erste Schritte mit Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="1e83d-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="1e83d-117">Onboarding von Computern für die Verwaltung von Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="1e83d-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)