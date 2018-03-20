---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: Bereitstellen in Azure Automation | MSDN
ms.openlocfilehash: 223acbcc2f6cd4f15e1ee55d3f2f68df851cd902
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
<a name="deploy-to-azure-automation"></a><span data-ttu-id="86669-103">Bereitstellen in Azure Automation</span><span class="sxs-lookup"><span data-stu-id="86669-103">Deploy to Azure Automation</span></span>
===========================

<span data-ttu-id="86669-104">Mit der Schaltfläche „Deploy to Azure Automation“ (Bereitstellen in Azure Automation) auf der Seite mit den Elementdetails können Sie ein Element aus dem PowerShell-Katalog auf Azure Automation bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="86669-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Schaltfläche zum Bereitstellen in Azure Automation](Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="86669-106">Wenn Sie auf diese Schaltfläche klicken, werden Sie zum Azure-Verwaltungsportal umgeleitet, wo Sie sich mit den Anmeldeinformationen Ihres Azure-Kontos anmelden.</span><span class="sxs-lookup"><span data-stu-id="86669-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="86669-107">Wenn das Element Abhängigkeiten enthält, werden diese ebenfalls auf Azure Automation bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="86669-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

<span data-ttu-id="86669-108">WARNUNG: Wenn Element und Version bereits identisch in Ihrem Automation-Konto vorhanden sind, wird eine erneute Bereitstellung aus dem PowerShell-Katalog das Element in Ihrem Automation-Konto überschreiben.</span><span class="sxs-lookup"><span data-stu-id="86669-108">WARNING:  If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="86669-109">Wenn Sie ein Modul bereitstellen, wird es im Abschnitt „Module“ von Azure Automation angezeigt.</span><span class="sxs-lookup"><span data-stu-id="86669-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="86669-110">Wenn Sie ein Skript bereitstellen, wird es im Abschnitt „Runbooks“ von Azure Automation angezeigt.</span><span class="sxs-lookup"><span data-stu-id="86669-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="86669-111">Sie können die Schaltfläche „Deploy to Azure Automation“ (Bereitstellen in Azure Automation) deaktivieren, indem Sie den Elementmetadaten das Tag „AzureAutomationNotSupported“ hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="86669-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

<span data-ttu-id="86669-112">Weitere Informationen zu Azure Automation finden Sie auf der [Azure Automation-Website](http://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="86669-112">To learn more about Azure Automation, see the Azure Automation website [Azure Automation website](http://azure.microsoft.com/services/automation/).</span></span>

