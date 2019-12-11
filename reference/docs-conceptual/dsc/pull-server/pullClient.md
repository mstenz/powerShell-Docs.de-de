---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Einrichten eines DSC-Pullclients
ms.openlocfilehash: 54c68ac26e5388260e252ce01418170e26ddecde
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71955167"
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="57474-103">Einrichten eines DSC-Pullclients</span><span class="sxs-lookup"><span data-stu-id="57474-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="57474-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="57474-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="57474-105">Der Pull-Server (Windows-Feature *DSC-Dienst*) ist eine von Windows Server unterstützte Komponente, jedoch sollen keine neuen Features oder Funktionen angeboten werden.</span><span class="sxs-lookup"><span data-stu-id="57474-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="57474-106">Es wird empfohlen, verwaltete Clients auf [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) umzustellen (enthält Features zusätzlich zum Pull-Server unter Windows Server) oder auf eine der [hier](pullserver.md#community-solutions-for-pull-service) aufgeführten Communitylösungen.</span><span class="sxs-lookup"><span data-stu-id="57474-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="57474-107">Jeder Zielknoten muss angewiesen werden, den Pullmodus zu verwenden. Außerdem muss die URL oder der Dateispeicherort angegeben werden, unter der bzw. dem der Pullserver Konfigurationen und Ressourcen abrufen kann und an die bzw. den Berichtsdaten gesendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="57474-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="57474-108">In den folgenden Themen wird erläutert, wie Pullclients eingerichtet werden:</span><span class="sxs-lookup"><span data-stu-id="57474-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="57474-109">Einrichten eines Pullclients mithilfe von Konfigurationsnamen</span><span class="sxs-lookup"><span data-stu-id="57474-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="57474-110">Einrichten eines Pullclients mithilfe einer Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="57474-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> [!NOTE]
> <span data-ttu-id="57474-111">Diese Artikel beziehen sich auf PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="57474-111">These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="57474-112">Informationen zum Einrichten eines Pullclients in PowerShell 4.0 finden Sie unter [Einrichten eines Pullclients mithilfe der Konfigurations-ID in PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="57474-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>