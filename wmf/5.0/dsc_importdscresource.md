---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 46a278b83edb9d8e3d75b0874603710d416be3b5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677942"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a><span data-ttu-id="5d4b3-102">Das Schlüsselwort „Import-DscResource“ unterstützt den „-ModuleVersion“-Parameter</span><span class="sxs-lookup"><span data-stu-id="5d4b3-102">Import-DscResource keyword supports -ModuleVersion parameter</span></span>

<span data-ttu-id="5d4b3-103">Wir haben dem dynamischen Schlüsselwort `Import-DscResource` für das Erstellen von DSC-Konfigurationen einen neuen Parameter hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="5d4b3-103">We have added a new parameter to the `Import-DscResource` dynamic keyword available when authoring DSC configurations.</span></span> <span data-ttu-id="5d4b3-104">Ersteller von Konfigurationen können nun genau angeben, aus welcher Modulversion die DSC-Ressourcen geladen werden können.</span><span class="sxs-lookup"><span data-stu-id="5d4b3-104">Configuration authors can now specify exactly which module version to load the DSC resources from.</span></span> <span data-ttu-id="5d4b3-105">Die neue Syntax des Schlüsselworts lautet:</span><span class="sxs-lookup"><span data-stu-id="5d4b3-105">The new syntax of the keyword is:</span></span>

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* <span data-ttu-id="5d4b3-106">**Name**: Der Name von mindestens einer zu importierenden Ressource.</span><span class="sxs-lookup"><span data-stu-id="5d4b3-106">**Name**: Names of one or more resources to import.</span></span>
* <span data-ttu-id="5d4b3-107">**ModuleName**: Modulnamen oder „ModuleSpecification“-Objekte von einem oder mehreren zu importierenden Modulen.</span><span class="sxs-lookup"><span data-stu-id="5d4b3-107">**ModuleName**: Module names or ModuleSpecification objects of one or more modules to import.</span></span>
* <span data-ttu-id="5d4b3-108">**ModuleVersion**: Version des zu importierenden Moduls.</span><span class="sxs-lookup"><span data-stu-id="5d4b3-108">**ModuleVersion**: Version of module to import.</span></span> <span data-ttu-id="5d4b3-109">Falls verwendet, darf „ModuleName“ nur ein Modul darstellen.</span><span class="sxs-lookup"><span data-stu-id="5d4b3-109">If used, ModuleName must represent only one module by name.</span></span>

<span data-ttu-id="5d4b3-110">In Windows PowerShell ISE wird dessen Name mithilfe von IntelliSense angezeigt:</span><span class="sxs-lookup"><span data-stu-id="5d4b3-110">In the Windows PowerShell ISE, it shows up with IntelliSense:</span></span>

![](../images/Import-DscResource-Modversion.jpg)

<span data-ttu-id="5d4b3-111">**Hinweis:**: Der `–ModuleVersion`-Parameter kann nur in Kombination mit dem `–ModuleName`-Parameter verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5d4b3-111">**Note**: the `–ModuleVersion` parameter can only be used in combination with the `–ModuleName` parameter.</span></span> <span data-ttu-id="5d4b3-112">Er kann nicht nur mit dem `–Name`-Parameter mit Ressourcennamen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5d4b3-112">It cannot be used with resource names using only the `–Name` parameter.</span></span>

<span data-ttu-id="5d4b3-113">Bisher war die einzige Möglichkeit der Angabe der Modulversion beim Laden von DSC-Ressourcen das Verwenden des Spezifikationsobjekts „Module“, z. B.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span><span class="sxs-lookup"><span data-stu-id="5d4b3-113">Before this, the only way to specify the module version when loading DSC resources was by using the Module specification object e.g.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span></span>
