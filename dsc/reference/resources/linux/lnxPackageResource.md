---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC für Linux-Resource „nxPackage“
ms.openlocfilehash: 64bb89a95bd6cbaea4e74b8a9979de52428fef3f
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047287"
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="5b7e6-103">DSC für Linux-Resource „nxPackage“</span><span class="sxs-lookup"><span data-stu-id="5b7e6-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="5b7e6-104">Die Ressource **nxPackage** in PowerShell DSC bietet einen Mechanismus zum Verwalten von Paketen auf einem Linux-Knoten.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="5b7e6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5b7e6-105">Syntax</span></span>

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="5b7e6-106">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="5b7e6-106">Properties</span></span>

|  <span data-ttu-id="5b7e6-107">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="5b7e6-107">Property</span></span> |  <span data-ttu-id="5b7e6-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5b7e6-108">Description</span></span> |
|---|---|
| <span data-ttu-id="5b7e6-109">Name</span><span class="sxs-lookup"><span data-stu-id="5b7e6-109">Name</span></span>| <span data-ttu-id="5b7e6-110">Der Name des Pakets, für das Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-110">The name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="5b7e6-111">Ensure</span><span class="sxs-lookup"><span data-stu-id="5b7e6-111">Ensure</span></span>| <span data-ttu-id="5b7e6-112">Bestimmt, ob das Vorhandensein des Pakets geprüft werden soll.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-112">Determines whether to check if the package exists.</span></span> <span data-ttu-id="5b7e6-113">Legen Sie diese Eigenschaft auf „Present“ fest, um sicherzustellen, dass das Paket vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-113">Set this property to "Present" to ensure the package exists.</span></span> <span data-ttu-id="5b7e6-114">Legen Sie sie auf „Absent“ fest, um sicherzustellen, dass das Paket nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-114">Set it to "Absent" to ensure the package does not exist.</span></span> <span data-ttu-id="5b7e6-115">Der Standardwert ist „Present“.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-115">The default value is "Present".</span></span>|
| <span data-ttu-id="5b7e6-116">PackageManager</span><span class="sxs-lookup"><span data-stu-id="5b7e6-116">PackageManager</span></span>| <span data-ttu-id="5b7e6-117">Unterstützte Werte sind „yum“, „apt“ und „zypper“.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-117">Supported values are "yum", "apt", and "zypper".</span></span> <span data-ttu-id="5b7e6-118">Gibt den Paket-Manager an, der zum Installieren von Paketen verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-118">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="5b7e6-119">Wenn **FilePath** angegeben ist, dient der angegebene Pfad zum Installieren des Pakets.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-119">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="5b7e6-120">Andernfalls wird ein Paket-Manager zum Installieren des Pakets aus einem vorkonfigurierten Repository verwendet.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-120">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="5b7e6-121">Wenn weder **PackageManager** noch **FilePath** angegeben ist, wird der standardmäßige Paket-Manager für das System verwendet.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-121">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span>|
| <span data-ttu-id="5b7e6-122">FilePath</span><span class="sxs-lookup"><span data-stu-id="5b7e6-122">FilePath</span></span>| <span data-ttu-id="5b7e6-123">Der Dateipfad, in dem das Paket gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-123">The file path where the package resides</span></span>|
| <span data-ttu-id="5b7e6-124">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="5b7e6-124">PackageGroup</span></span>| <span data-ttu-id="5b7e6-125">Falls **$true**, soll **Name** dem Namen einer Paketgruppe für die Verwendung mit einem **PackageManager** entsprechen.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-125">If **$true**, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="5b7e6-126">**PackageGroup** ist ungültig, wenn **FilePath** angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-126">**PacakgeGroup** is not valid when providing a **FilePath**.</span></span>|
| <span data-ttu-id="5b7e6-127">Arguments</span><span class="sxs-lookup"><span data-stu-id="5b7e6-127">Arguments</span></span>| <span data-ttu-id="5b7e6-128">Eine Zeichenfolge mit Argumenten, die exakt wie angegeben an das Paket übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-128">A string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="5b7e6-129">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="5b7e6-129">ReturnCode</span></span>| <span data-ttu-id="5b7e6-130">Der erwartete Rückgabecode.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-130">The expected return code.</span></span> <span data-ttu-id="5b7e6-131">Wenn der tatsächliche Rückgabecode nicht dem erwarteten Wert entspricht, gibt die Konfiguration einen Fehler zurück.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-131">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|
| <span data-ttu-id="5b7e6-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5b7e6-132">DependsOn</span></span> | <span data-ttu-id="5b7e6-133">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5b7e6-134">Wenn beispielsweise die **ID** des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="5b7e6-135">Beispiel</span><span class="sxs-lookup"><span data-stu-id="5b7e6-135">Example</span></span>

<span data-ttu-id="5b7e6-136">Im folgende Beispiel wird sichergestellt, dass das Paket mit dem Namen „httpd“ mit dem Paket-Manager „Yum“ auf einem Linux-Computer installiert wird.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-136">The following example ensures that the package named "httpd" is installed on a Linux computer, using the “Yum” package manager.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```