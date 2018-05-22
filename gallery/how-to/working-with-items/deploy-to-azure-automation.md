---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Bereitstellen in Azure Automation
ms.openlocfilehash: ced67809387a85e089259edf6b091d68e58ba6a7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="6db80-103">Bereitstellen in Azure Automation</span><span class="sxs-lookup"><span data-stu-id="6db80-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="6db80-104">Mit der Schaltfläche „Deploy to Azure Automation“ (Bereitstellen in Azure Automation) auf der Seite mit den Elementdetails können Sie ein Element aus dem PowerShell-Katalog auf Azure Automation bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="6db80-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Schaltfläche zum Bereitstellen in Azure Automation](../../Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="6db80-106">Wenn Sie auf diese Schaltfläche klicken, werden Sie zum Azure-Verwaltungsportal umgeleitet, wo Sie sich mit den Anmeldeinformationen Ihres Azure-Kontos anmelden.</span><span class="sxs-lookup"><span data-stu-id="6db80-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="6db80-107">Wenn das Element Abhängigkeiten enthält, werden diese ebenfalls auf Azure Automation bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="6db80-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="6db80-108">Wenn Element und Version bereits identisch in Ihrem Automation-Konto vorhanden sind, wird eine erneute Bereitstellung aus dem PowerShell-Katalog das Element in Ihrem Automation-Konto überschreiben.</span><span class="sxs-lookup"><span data-stu-id="6db80-108">If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="6db80-109">Wenn Sie ein Modul bereitstellen, wird es im Abschnitt „Module“ von Azure Automation angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6db80-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="6db80-110">Wenn Sie ein Skript bereitstellen, wird es im Abschnitt „Runbooks“ von Azure Automation angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6db80-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="6db80-111">Sie können die Schaltfläche „Deploy to Azure Automation“ (Bereitstellen in Azure Automation) deaktivieren, indem Sie den Elementmetadaten das Tag „AzureAutomationNotSupported“ hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6db80-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="6db80-112">Erforderliche Zustimmung zur Lizenz für die Bereitstellung in Azure Automation</span><span class="sxs-lookup"><span data-stu-id="6db80-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="6db80-113">Wenn für das Modul, das in Azure Automation bereitgestellt wird, die Zustimmung zur Lizenz erforderlich ist, wird auf der Portaloberfläche ein Haftungsausschluss mit folgender Meldung angezeigt: „Für dieses Modul muss der Lizenz zugestimmt werden.</span><span class="sxs-lookup"><span data-stu-id="6db80-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="6db80-114">Indem Sie auf ‚OK‘ klicken, akzeptieren Sie die Lizenzbedingungen.“</span><span class="sxs-lookup"><span data-stu-id="6db80-114">By clicking OK, you are accepting license terms.'</span></span>

![Für die Bereitstellung in Azure Automation ist die Zustimmung zur Lizenz erforderlich.](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="6db80-116">Weitere Details</span><span class="sxs-lookup"><span data-stu-id="6db80-116">More details</span></span>

- [<span data-ttu-id="6db80-117">Erforderliche Zustimmung zur Lizenz in PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="6db80-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="6db80-118">Erforderliche Zustimmung zur Lizenz im PowerShell-Katalog</span><span class="sxs-lookup"><span data-stu-id="6db80-118">Require License Acceptance in PowerShell Gallery</span></span>](items-that-require-license-acceptance.md)
- [<span data-ttu-id="6db80-119">Azure Automation-Website</span><span class="sxs-lookup"><span data-stu-id="6db80-119">Azure Automation website</span></span>](http://azure.microsoft.com/services/automation/)
