---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 4def20aa95f66ab23c9eee575150bc3db02541d8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="612b8-102">Klassenbasierte DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="612b8-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="612b8-103">Definieren von DSC-Ressourcen mit Klassen</span><span class="sxs-lookup"><span data-stu-id="612b8-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="612b8-104">Basierend auf Feedback haben wir das Erstellen klassenbasierter DSC-Ressourcen vereinfacht und leichter verständlich gemacht.</span><span class="sxs-lookup"><span data-stu-id="612b8-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="612b8-105">Es folgen die wichtigsten Unterschiede zwischen einer klassenbasierten DSC-Ressource und einem DSC-Ressourcenanbieter für ein Cmdlet:</span><span class="sxs-lookup"><span data-stu-id="612b8-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="612b8-106">Eine MOF-Datei für das Schema ist nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="612b8-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="612b8-107">Der Unterordner **DSCResource** im Ordner „module“ ist nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="612b8-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="612b8-108">Eine PowerShell-Moduldatei kann mehrere DSC-Ressourcenklassen enthalten.</span><span class="sxs-lookup"><span data-stu-id="612b8-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="612b8-109">Weitere Informationen finden Sie unter [Schreiben einer benutzerdefinierten DSC-Ressource mit PowerShell-Klassen](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="612b8-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>