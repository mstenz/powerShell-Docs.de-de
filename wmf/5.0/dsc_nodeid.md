---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7a1725e3858c59a6d31699add22b042359c48463
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678374"
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="2fdf5-102">Trennung von Knoten- und Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="2fdf5-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="2fdf5-103">Übersicht</span><span class="sxs-lookup"><span data-stu-id="2fdf5-103">Overview</span></span>

<span data-ttu-id="2fdf5-104">Um bei Verwenden von DSC im Pullmodus eine flexiblere und bessere Erfahrung zu bieten, haben wir in dieser Version verschiedene Features hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="2fdf5-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="2fdf5-105">Diese Features ermöglichen Ihnen ein flexibles Einrichten und Bereitstellen von Konfigurationen auf mehreren Knoten und zugleich das Nachverfolgen des Status und von Berichtsinformationen für jeden einzelnen Knoten.</span><span class="sxs-lookup"><span data-stu-id="2fdf5-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span>
<span data-ttu-id="2fdf5-106">Diese Features sind wie folgt:</span><span class="sxs-lookup"><span data-stu-id="2fdf5-106">These features are as follows:</span></span>

* <span data-ttu-id="2fdf5-107">Ein Konfigurationsname, der die Konfiguration für einen Computer identifiziert.</span><span class="sxs-lookup"><span data-stu-id="2fdf5-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="2fdf5-108">Dieser Name kann von mehreren Zielknoten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2fdf5-108">This name can be shared by multiple target nodes</span></span>
* <span data-ttu-id="2fdf5-109">Eine Agent-ID, die einen einzelnen Knoten eindeutig identifiziert.</span><span class="sxs-lookup"><span data-stu-id="2fdf5-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="2fdf5-110">Ein Registrierungsschritt, der nur erfolgt, wenn sich ein Zielknoten erstmals mit einem Pullserver verbindet.</span><span class="sxs-lookup"><span data-stu-id="2fdf5-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="2fdf5-111">**Hinweis:** Diese Features und Funktionen wurden hinzugefügt und ersetzen vorhandene Pullfeatures und -konzepte nicht.</span><span class="sxs-lookup"><span data-stu-id="2fdf5-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="2fdf5-112">Sie können diese neuen Features oder die älteren mit dem neuen Pullserver in dieser Version verwenden.</span><span class="sxs-lookup"><span data-stu-id="2fdf5-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="2fdf5-113">Weitere Informationen finden Sie unter [Einrichten eines Pullclients mithilfe von Konfigurationsnamen](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames).</span><span class="sxs-lookup"><span data-stu-id="2fdf5-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>
