---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: a565f2befddc32f5088fa3e158f58d2dd78d41b4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="a2390-102">Unterstützung der gleichzeitigen Ausführung unterschiedlicher Versionen für DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="a2390-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="a2390-103">Module unterschiedlicher Versionen mit DSC-Ressourcen können parallel installiert werden, und DSC-Konfigurationen können eine bestimmte Version der Ressource verwenden, die auf dem System installiert ist.</span><span class="sxs-lookup"><span data-stu-id="a2390-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="a2390-104">Weitere Informationen finden Sie unter [Verwenden von Ressourcen mit mehreren Versionen](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span><span class="sxs-lookup"><span data-stu-id="a2390-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="a2390-105">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="a2390-105">Known issues</span></span>

<span data-ttu-id="a2390-106">In dieser Version sind die folgenden Probleme bei paralleler Installation unterschiedlicher Versionen bekannt:</span><span class="sxs-lookup"><span data-stu-id="a2390-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="a2390-107">Das Verwenden zweier verschiedener Versionen der DSC-Ressourcen innerhalb der gleichen Konfiguration wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a2390-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>