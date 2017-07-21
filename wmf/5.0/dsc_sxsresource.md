---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 3261e5a07b8181190a04de3f210da50f23bb2953
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="90092-102">Unterstützung der gleichzeitigen Ausführung unterschiedlicher Versionen für DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="90092-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="90092-103">Module unterschiedlicher Versionen mit DSC-Ressourcen können parallel installiert werden, und DSC-Konfigurationen können eine bestimmte Version der Ressource verwenden, die auf dem System installiert ist.</span><span class="sxs-lookup"><span data-stu-id="90092-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="90092-104">Weitere Informationen finden Sie unter [Verwenden von Ressourcen mit mehreren Versionen](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span><span class="sxs-lookup"><span data-stu-id="90092-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="90092-105">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="90092-105">Known issues</span></span>

<span data-ttu-id="90092-106">In dieser Version sind die folgenden Probleme bei paralleler Installation unterschiedlicher Versionen bekannt:</span><span class="sxs-lookup"><span data-stu-id="90092-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="90092-107">Das Verwenden zweier verschiedener Versionen der DSC-Ressourcen innerhalb der gleichen Konfiguration wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="90092-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>

