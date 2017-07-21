---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: d40e5475c4132d6377c9a4559262a41b4842180a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="43df3-102">Klassenbasierte DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="43df3-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="43df3-103">Definieren von DSC-Ressourcen mit Klassen</span><span class="sxs-lookup"><span data-stu-id="43df3-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="43df3-104">Basierend auf Feedback haben wir das Erstellen klassenbasierter DSC-Ressourcen vereinfacht und leichter verständlich gemacht.</span><span class="sxs-lookup"><span data-stu-id="43df3-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span> <span data-ttu-id="43df3-105">Es folgen die wichtigsten Unterschiede zwischen einer klassenbasierten DSC-Ressource und einem DSC-Ressourcenanbieter für ein Cmdlet:</span><span class="sxs-lookup"><span data-stu-id="43df3-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="43df3-106">Eine MOF-Datei für das Schema ist nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="43df3-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="43df3-107">Der Unterordner **DSCResource** im Ordner „module“ ist nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="43df3-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="43df3-108">Eine PowerShell-Moduldatei kann mehrere DSC-Ressourcenklassen enthalten.</span><span class="sxs-lookup"><span data-stu-id="43df3-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="43df3-109">Weitere Informationen finden Sie unter [Schreiben einer benutzerdefinierten DSC-Ressource mit PowerShell-Klassen](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="43df3-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>

