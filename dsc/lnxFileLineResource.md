---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC für Linux-Resource „nxFileLine“
ms.openlocfilehash: 6a91db25638b09659adfabcec78f91bcb2e69dd9
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225589"
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="bf849-103">DSC für Linux-Resource „nxFileLine“</span><span class="sxs-lookup"><span data-stu-id="bf849-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="bf849-104">Die Ressource **nxFileLine** in PowerShell DSC (Desired State Configuration) bietet einen Mechanismus zum Verwalten von Zeilen in einer Konfigurationsdatei auf einem Linux-Knoten.</span><span class="sxs-lookup"><span data-stu-id="bf849-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="bf849-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bf849-105">Syntax</span></span>

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="bf849-106">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="bf849-106">Properties</span></span>

|  <span data-ttu-id="bf849-107">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="bf849-107">Property</span></span> |  <span data-ttu-id="bf849-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bf849-108">Description</span></span> |
|---|---|
| <span data-ttu-id="bf849-109">FilePath</span><span class="sxs-lookup"><span data-stu-id="bf849-109">FilePath</span></span>| <span data-ttu-id="bf849-110">Der vollständige Pfad zu der Datei zum Verwalten von Zeilen auf dem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="bf849-110">The full path to the file to manage lines in on the target node.</span></span>|
| <span data-ttu-id="bf849-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="bf849-111">ContainsLine</span></span>| <span data-ttu-id="bf849-112">Eine Zeile, um sicherzustellen, dass sie in der Datei vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="bf849-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="bf849-113">Diese Zeile wird an die Datei angefügt, wenn sie in der Datei nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="bf849-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="bf849-114">**ContainsLine** ist obligatorisch, kann jedoch auf eine leere Zeichenfolge (`ContainsLine = ""`) festgelegt werden, falls nicht benötigt.</span><span class="sxs-lookup"><span data-stu-id="bf849-114">**ContainsLine** is mandatory, but can be set to an empty string (`ContainsLine = ""`) if it is not needed.</span></span>|
| <span data-ttu-id="bf849-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="bf849-115">DoesNotContainPattern</span></span>| <span data-ttu-id="bf849-116">Muster eines regulären Ausdrucks für Zeilen, die in der Datei nicht vorhanden sein dürfen.</span><span class="sxs-lookup"><span data-stu-id="bf849-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="bf849-117">Alle in der Datei vorhandenen Zeilen, die mit diesem regulären Ausdruck übereinstimmen, werden aus der Datei entfernt.</span><span class="sxs-lookup"><span data-stu-id="bf849-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span>|
| <span data-ttu-id="bf849-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="bf849-118">DependsOn</span></span> | <span data-ttu-id="bf849-119">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="bf849-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="bf849-120">Wenn beispielsweise die **ID** des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="bf849-120">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="bf849-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="bf849-121">Example</span></span>

<span data-ttu-id="bf849-122">Dieses Beispiel veranschaulicht die Verwendung der Ressource **nxFileLine** zum Konfigurieren der Datei `/etc/sudoers`, um sicherzustellen, dass der Benutzer „monuser“ nicht mit „requiretty“ konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="bf849-122">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```