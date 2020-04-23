---
ms.date: 06/12/2017
contributor: Farehar
keywords: Katalog,PowerShell,psgallery
title: Erforderliche Zustimmung zur Lizenz
ms.openlocfilehash: 4b293ea693062cf9717fa4ca913c3eb9abaf7014
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278647"
---
# <a name="require-license-acceptance"></a><span data-ttu-id="361d6-103">Erforderliche Zustimmung zur Lizenz</span><span class="sxs-lookup"><span data-stu-id="361d6-103">Require license acceptance</span></span>

<span data-ttu-id="361d6-104">Der Text zum Anfordern der Zustimmung zur Lizenz wird auf der Seite mit den Elementdetails für Module angezeigt, für die die Zustimmung zur Lizenz erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="361d6-104">Require License Acceptance text shows up on item details page for modules that require license acceptance.</span></span> <span data-ttu-id="361d6-105">Die Lizenz für das Modul kann durch Klicken auf „‚License.txt‘ anzeigen“ angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="361d6-105">License for module can be viewed by clicking on 'View License.txt' link.</span></span>

![Erforderliche Zustimmung zur Lizenz](media/packages-that-require-license-acceptance/RequireLicenseAcceptance.png)

<span data-ttu-id="361d6-107">Benutzer werden beim Installieren, Speichern oder Aktualisieren des Moduls über PowerShellGet oder bei der Bereitstellung für Azure Automation aufgefordert, die Lizenz zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="361d6-107">Users will be prompted to accept the license when installing, saving or updating the module through PowerShellGet or when deploying to Azure Automation.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="361d6-108">Erforderliche Zustimmung zur Lizenz für die Bereitstellung in Azure Automation</span><span class="sxs-lookup"><span data-stu-id="361d6-108">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="361d6-109">Wenn für das Modul, das in Azure Automation bereitgestellt wird, die Zustimmung zur Lizenz erforderlich ist, wird auf der Portaloberfläche ein Haftungsausschluss mit folgender Meldung angezeigt: „Für dieses Modul muss der Lizenz zugestimmt werden.</span><span class="sxs-lookup"><span data-stu-id="361d6-109">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="361d6-110">Indem Sie auf ‚OK‘ klicken, akzeptieren Sie die Lizenzbedingungen.“</span><span class="sxs-lookup"><span data-stu-id="361d6-110">By clicking OK, you are accepting license terms.'</span></span>

![Für die Bereitstellung in Azure Automation ist die Zustimmung zur Lizenz erforderlich.](media/packages-that-require-license-acceptance/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="361d6-112">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="361d6-112">More details</span></span>

<span data-ttu-id="361d6-113">[Erforderliche Zustimmung zur Lizenz in PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation-Website](/azure/automation)</span><span class="sxs-lookup"><span data-stu-id="361d6-113">[Require License Acceptance in PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation website](/azure/automation)</span></span>
