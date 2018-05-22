---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 42f323590609319388e9a0a2c7c305dfa80c2d49
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="d507d-102">Klassenbasierte DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="d507d-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="d507d-103">Definieren von DSC-Ressourcen mit Klassen</span><span class="sxs-lookup"><span data-stu-id="d507d-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="d507d-104">Basierend auf Feedback haben wir das Erstellen klassenbasierter DSC-Ressourcen vereinfacht und leichter verständlich gemacht.</span><span class="sxs-lookup"><span data-stu-id="d507d-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="d507d-105">Es folgen die wichtigsten Unterschiede zwischen einer klassenbasierten DSC-Ressource und einem DSC-Ressourcenanbieter für ein Cmdlet:</span><span class="sxs-lookup"><span data-stu-id="d507d-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="d507d-106">Eine MOF-Datei für das Schema ist nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d507d-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="d507d-107">Der Unterordner **DSCResource** im Ordner „module“ ist nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d507d-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="d507d-108">Eine PowerShell-Moduldatei kann mehrere DSC-Ressourcenklassen enthalten.</span><span class="sxs-lookup"><span data-stu-id="d507d-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="d507d-109">Weitere Informationen finden Sie unter [Schreiben einer benutzerdefinierten DSC-Ressource mit PowerShell-Klassen](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="d507d-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>
