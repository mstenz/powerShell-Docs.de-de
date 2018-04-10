---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: DSC für Linux-Resource „nxFileLine“
ms.openlocfilehash: 798bfa4150996622c33c77d6a5aa3be4af342f1b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="0a5b7-103">DSC für Linux-Resource „nxFileLine“</span><span class="sxs-lookup"><span data-stu-id="0a5b7-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="0a5b7-104">Die Ressource **nxFileLine** in PowerShell DSC bietet einen Mechanismus zum Verwalten von Zeilen in einer Konfigurationsdatei auf einem Linux-Knoten.</span><span class="sxs-lookup"><span data-stu-id="0a5b7-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="0a5b7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0a5b7-105">Syntax</span></span>

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="0a5b7-106">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="0a5b7-106">Properties</span></span>

|  <span data-ttu-id="0a5b7-107">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="0a5b7-107">Property</span></span> |  <span data-ttu-id="0a5b7-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0a5b7-108">Description</span></span> |
|---|---|
| <span data-ttu-id="0a5b7-109">FilePath</span><span class="sxs-lookup"><span data-stu-id="0a5b7-109">FilePath</span></span>| <span data-ttu-id="0a5b7-110">Der vollständige Pfad zu der Datei zum Verwalten von Zeilen auf dem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="0a5b7-110">The full path to the file to manage lines in on the target node.</span></span>|
| <span data-ttu-id="0a5b7-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="0a5b7-111">ContainsLine</span></span>| <span data-ttu-id="0a5b7-112">Eine Zeile, um sicherzustellen, dass sie in der Datei vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="0a5b7-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="0a5b7-113">Diese Zeile wird an die Datei angefügt, wenn sie in der Datei nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="0a5b7-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="0a5b7-114">**ContainsLine** ist obligatorisch, kann jedoch auf eine leere Zeichenfolge festgelegt werden (\`ContainsLine = ‘’\`\`), falls nicht benötigt.</span><span class="sxs-lookup"><span data-stu-id="0a5b7-114">**ContainsLine** is mandatory, but can be set to an empty string (\`ContainsLine = ‘’\`\`) if it is not needed.</span></span>|
| <span data-ttu-id="0a5b7-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="0a5b7-115">DoesNotContainPattern</span></span>| <span data-ttu-id="0a5b7-116">Muster eines regulären Ausdrucks für Zeilen, die in der Datei nicht vorhanden sein dürfen.</span><span class="sxs-lookup"><span data-stu-id="0a5b7-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="0a5b7-117">Alle in der Datei vorhandenen Zeilen, die mit diesem regulären Ausdruck übereinstimmen, werden aus der Datei entfernt.</span><span class="sxs-lookup"><span data-stu-id="0a5b7-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span>|
| <span data-ttu-id="0a5b7-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0a5b7-118">DependsOn</span></span> | <span data-ttu-id="0a5b7-119">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="0a5b7-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0a5b7-120">Wenn beispielsweise die **ID** des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0a5b7-120">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="0a5b7-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="0a5b7-121">Example</span></span>

<span data-ttu-id="0a5b7-122">Dieses Beispiel veranschaulicht die Verwendung der Ressource **nxFileLine** zum Konfigurieren der Datei `/etc/sudoers`, um sicherzustellen, dass der Benutzer „monuser“ nicht mit „requiretty“ konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="0a5b7-122">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```
Import-DSCResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```