---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC für Linux-Resource „nxFileLine“
ms.openlocfilehash: 6b927839c23478aa9916a5d23836b31fccc58484
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219632"
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="8e07a-103">DSC für Linux-Resource „nxFileLine“</span><span class="sxs-lookup"><span data-stu-id="8e07a-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="8e07a-104">Die Ressource **nxFileLine** in PowerShell DSC bietet einen Mechanismus zum Verwalten von Zeilen in einer Konfigurationsdatei auf einem Linux-Knoten.</span><span class="sxs-lookup"><span data-stu-id="8e07a-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="8e07a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8e07a-105">Syntax</span></span>

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="8e07a-106">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="8e07a-106">Properties</span></span>

|  <span data-ttu-id="8e07a-107">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="8e07a-107">Property</span></span> |  <span data-ttu-id="8e07a-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8e07a-108">Description</span></span> |
|---|---|
| <span data-ttu-id="8e07a-109">FilePath</span><span class="sxs-lookup"><span data-stu-id="8e07a-109">FilePath</span></span>| <span data-ttu-id="8e07a-110">Der vollständige Pfad zu der Datei zum Verwalten von Zeilen auf dem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="8e07a-110">The full path to the file to manage lines in on the target node.</span></span>|
| <span data-ttu-id="8e07a-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="8e07a-111">ContainsLine</span></span>| <span data-ttu-id="8e07a-112">Eine Zeile, um sicherzustellen, dass sie in der Datei vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="8e07a-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="8e07a-113">Diese Zeile wird an die Datei angefügt, wenn sie in der Datei nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="8e07a-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="8e07a-114">**ContainsLine** ist obligatorisch, kann jedoch auf eine leere Zeichenfolge festgelegt werden (\`ContainsLine = ‘’\`\`), falls nicht benötigt.</span><span class="sxs-lookup"><span data-stu-id="8e07a-114">**ContainsLine** is mandatory, but can be set to an empty string (\`ContainsLine = ‘’\`\`) if it is not needed.</span></span>|
| <span data-ttu-id="8e07a-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="8e07a-115">DoesNotContainPattern</span></span>| <span data-ttu-id="8e07a-116">Muster eines regulären Ausdrucks für Zeilen, die in der Datei nicht vorhanden sein dürfen.</span><span class="sxs-lookup"><span data-stu-id="8e07a-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="8e07a-117">Alle in der Datei vorhandenen Zeilen, die mit diesem regulären Ausdruck übereinstimmen, werden aus der Datei entfernt.</span><span class="sxs-lookup"><span data-stu-id="8e07a-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span>|
| <span data-ttu-id="8e07a-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="8e07a-118">DependsOn</span></span> | <span data-ttu-id="8e07a-119">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="8e07a-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8e07a-120">Wenn beispielsweise die **ID** des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="8e07a-120">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="8e07a-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8e07a-121">Example</span></span>

<span data-ttu-id="8e07a-122">Dieses Beispiel veranschaulicht die Verwendung der Ressource **nxFileLine** zum Konfigurieren der Datei `/etc/sudoers`, um sicherzustellen, dass der Benutzer „monuser“ nicht mit „requiretty“ konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="8e07a-122">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```
Import-DSCResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```