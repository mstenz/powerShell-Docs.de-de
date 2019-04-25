---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5b31fe833fb0f9d0f3f2733e777e4608a697d583
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057926"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="18b21-102">Unterstützung der gleichzeitigen Ausführung unterschiedlicher Versionen für DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="18b21-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="18b21-103">Module unterschiedlicher Versionen mit DSC-Ressourcen können parallel installiert werden, und DSC-Konfigurationen können eine bestimmte Version der Ressource verwenden, die auf dem System installiert ist.</span><span class="sxs-lookup"><span data-stu-id="18b21-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="18b21-104">Weitere Informationen finden Sie unter [Verwenden von Ressourcen mit mehreren Versionen](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span><span class="sxs-lookup"><span data-stu-id="18b21-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="18b21-105">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="18b21-105">Known issues</span></span>

<span data-ttu-id="18b21-106">In dieser Version sind die folgenden Probleme bei paralleler Installation unterschiedlicher Versionen bekannt:</span><span class="sxs-lookup"><span data-stu-id="18b21-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="18b21-107">Das Verwenden zweier verschiedener Versionen der DSC-Ressourcen innerhalb der gleichen Konfiguration wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="18b21-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>
