---
ms.date: 06/12/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: Einrichten eines DSC-Pullclients
ms.openlocfilehash: 7c68f4c59170c672e7573de7e7e595a60a81c966
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561102"
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="71505-103">Einrichten eines DSC-Pullclients</span><span class="sxs-lookup"><span data-stu-id="71505-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="71505-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="71505-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="71505-105">Der Pull-Server (Windows-Feature *DSC-Dienst*) ist eine von Windows Server unterstützte Komponente, jedoch sollen keine neuen Features oder Funktionen angeboten werden.</span><span class="sxs-lookup"><span data-stu-id="71505-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="71505-106">Es wird empfohlen, verwaltete Clients auf [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) umzustellen (enthält Features zusätzlich zum Pull-Server unter Windows Server) oder auf eine der [hier](pullserver.md#community-solutions-for-pull-service) aufgeführten Communitylösungen.</span><span class="sxs-lookup"><span data-stu-id="71505-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="71505-107">Jeder Zielknoten muss angewiesen werden, den Pullmodus zu verwenden. Außerdem muss die URL oder der Dateispeicherort angegeben werden, unter der bzw. dem der Pullserver Konfigurationen und Ressourcen abrufen kann und an die bzw. den Berichtsdaten gesendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="71505-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="71505-108">In den folgenden Themen wird erläutert, wie Pullclients eingerichtet werden:</span><span class="sxs-lookup"><span data-stu-id="71505-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="71505-109">Einrichten eines Pullclients mithilfe von Konfigurationsnamen</span><span class="sxs-lookup"><span data-stu-id="71505-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="71505-110">Einrichten eines Pullclients mithilfe einer Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="71505-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> [!NOTE]
> <span data-ttu-id="71505-111">Diese Artikel beziehen sich auf PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="71505-111">These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="71505-112">Informationen zum Einrichten eines Pullclients in PowerShell 4.0 finden Sie unter [Einrichten eines Pullclients mithilfe der Konfigurations-ID in PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="71505-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>
