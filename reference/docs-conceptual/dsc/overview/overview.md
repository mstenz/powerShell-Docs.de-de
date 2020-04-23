---
ms.date: 06/12/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: Windows PowerShell DSC – Übersicht
ms.openlocfilehash: 5c4853cb059ca0cf063a9450f97230732bc56b10
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953637"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a><span data-ttu-id="50b74-103">Windows PowerShell DSC – Übersicht</span><span class="sxs-lookup"><span data-stu-id="50b74-103">Windows PowerShell Desired State Configuration Overview</span></span>

> <span data-ttu-id="50b74-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="50b74-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="50b74-105">DSC ist eine Verwaltungsplattform in PowerShell, die es Ihnen ermöglicht, Ihre IT- und Entwicklungsinfrastruktur mit der Konfiguration als Code zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="50b74-105">DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code.</span></span>

- <span data-ttu-id="50b74-106">Eine Übersicht über Vorteile, die DSC Ihrem Unternehmen bietet, finden Sie unter [Desired State Configuration (DSC): Übersicht für Entscheidungsträger](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="50b74-106">For an overview of the business benefits of using DSC, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>
- <span data-ttu-id="50b74-107">Eine Übersicht über die Vorteile, die DSC Ihren Ingenieuren bietet, finden Sie unter [Desired State Configuration (DSC): Übersicht für Ingenieure](DscForEngineers.md).</span><span class="sxs-lookup"><span data-stu-id="50b74-107">For an overview of the engineering benefits of using DSC, see [Desired State Configuration Overview for Engineers](DscForEngineers.md).</span></span>
- <span data-ttu-id="50b74-108">Informationen zum Schnelleinstieg in DSC finden Sie unter [DSC Schnellstart](../quickstarts/website-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="50b74-108">To start using DSC quickly, see [DSC quick start](../quickstarts/website-quickstart.md).</span></span>

## <a name="key-concepts"></a><span data-ttu-id="50b74-109">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="50b74-109">Key Concepts</span></span>

<span data-ttu-id="50b74-110">DSC ist eine deklarative Plattform für die Konfiguration, Bereitstellung und Verwaltung von Systemen,</span><span class="sxs-lookup"><span data-stu-id="50b74-110">DSC is a declarative platform used for configuration, deployment, and management of systems.</span></span> <span data-ttu-id="50b74-111">die aus drei Hauptkomponenten besteht:</span><span class="sxs-lookup"><span data-stu-id="50b74-111">It consists of three primary components:</span></span>

- <span data-ttu-id="50b74-112">[Konfigurationen](../configurations/configurations.md) sind deklarative PowerShell-Skripts, mit denen Instanzen von Ressourcen definiert und konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="50b74-112">[Configurations](../configurations/configurations.md) are declarative PowerShell scripts which define and configure instances of resources.</span></span>
    <span data-ttu-id="50b74-113">Bei Ausführung der Konfiguration wird der gewünschte Zustand entsprechend den Vorgaben in der Konfiguration von DSC eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="50b74-113">Upon running the configuration, DSC (and the resources being called by the configuration) will simply "make it so", ensuring that the system exists in the state laid out by the configuration.</span></span>
    <span data-ttu-id="50b74-114">DSC-Konfigurationen sind auch idempotent, d. h. vom lokalen Konfigurations-Manager (LCM) wird weiter sicherstellt, dass Computer entsprechend der Deklaration in der Konfiguration konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="50b74-114">DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.</span></span>
- <span data-ttu-id="50b74-115">[Ressourcen](../resources/resources.md) sind der „Mach es so“-Teil von DSC.</span><span class="sxs-lookup"><span data-stu-id="50b74-115">[Resources](../resources/resources.md) are the "make it so" part of DSC.</span></span> <span data-ttu-id="50b74-116">Sie enthalten den Code, der das Ziel einer Konfiguration in den angegebenen Zustand versetzt und dort hält.</span><span class="sxs-lookup"><span data-stu-id="50b74-116">They contain the code that put and keep the target of a configuration in the specified state.</span></span>
    <span data-ttu-id="50b74-117">Ressourcen befinden sich in PowerShell-Modulen und können geschrieben werden, um etwas Allgemeines wie eine Datei oder einen Windows-Prozess oder etwas Spezifisches wie einen IIS-Server oder eine in Azure ausgeführte VM zu modellieren.</span><span class="sxs-lookup"><span data-stu-id="50b74-117">Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.</span></span>
- <span data-ttu-id="50b74-118">Der [lokale Konfigurations-Manager (Local Configuration Manager, LCM)](../managing-nodes/metaConfig.md) ist die Engine, die DSC die Interaktion zwischen Ressourcen und Konfigurationen erleichtert.</span><span class="sxs-lookup"><span data-stu-id="50b74-118">The [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md) is the engine by which DSC facilitates the interaction between resources and configurations.</span></span>
    <span data-ttu-id="50b74-119">Der LCM fragt das System mithilfe der von Ressourcen implementierten Ablaufsteuerung ab, um sicherzustellen, dass der von einer Konfiguration definierte Zustand beibehalten wird.</span><span class="sxs-lookup"><span data-stu-id="50b74-119">The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained.</span></span>
    <span data-ttu-id="50b74-120">Ist dies nicht der Fall, führt der LCM Aufrufe an Code in den Ressourcen aus, um eine Korrektur entsprechend der Konfiguration vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="50b74-120">If the system is out of state, the LCM makes calls to the code in resources to "make it so" according to the configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="50b74-121">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="50b74-121">See Also</span></span>

- [<span data-ttu-id="50b74-122">DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="50b74-122">DSC Configurations</span></span>](../configurations/configurations.md)
- [<span data-ttu-id="50b74-123">DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="50b74-123">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="50b74-124">Konfigurieren des lokalen Konfigurations-Managers</span><span class="sxs-lookup"><span data-stu-id="50b74-124">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
