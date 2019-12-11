---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC für Linux-Resource „nxPackage“
ms.openlocfilehash: 4091cbbd5e34a84b9011870da4bda93281378347
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954817"
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="69411-103">DSC für Linux-Resource „nxPackage“</span><span class="sxs-lookup"><span data-stu-id="69411-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="69411-104">Die Ressource **nxPackage** in PowerShell DSC bietet einen Mechanismus zum Verwalten von Paketen auf einem Linux-Knoten.</span><span class="sxs-lookup"><span data-stu-id="69411-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="69411-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="69411-105">Syntax</span></span>

```Syntax
nxPackage <string> #ResourceName
{
    Name = <string>
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ FilePath = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="69411-106">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="69411-106">Properties</span></span>

|<span data-ttu-id="69411-107">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="69411-107">Property</span></span> |<span data-ttu-id="69411-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="69411-108">Description</span></span> |
|---|---|
|<span data-ttu-id="69411-109">Name</span><span class="sxs-lookup"><span data-stu-id="69411-109">Name</span></span> |<span data-ttu-id="69411-110">Der Name des Pakets, für das Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="69411-110">The name of the package for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="69411-111">PackageManager</span><span class="sxs-lookup"><span data-stu-id="69411-111">PackageManager</span></span> |<span data-ttu-id="69411-112">Unterstützte Werte sind **yum**, **apt** und **zypper**.</span><span class="sxs-lookup"><span data-stu-id="69411-112">Supported values are **yum**, **apt**, and **zypper**.</span></span> <span data-ttu-id="69411-113">Gibt den Paket-Manager an, der zum Installieren von Paketen verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="69411-113">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="69411-114">Wenn **FilePath** angegeben ist, dient der angegebene Pfad zum Installieren des Pakets.</span><span class="sxs-lookup"><span data-stu-id="69411-114">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="69411-115">Andernfalls wird ein Paket-Manager zum Installieren des Pakets aus einem vorkonfigurierten Repository verwendet.</span><span class="sxs-lookup"><span data-stu-id="69411-115">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="69411-116">Wenn weder **PackageManager** noch **FilePath** angegeben ist, wird der standardmäßige Paket-Manager für das System verwendet.</span><span class="sxs-lookup"><span data-stu-id="69411-116">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span> |
|<span data-ttu-id="69411-117">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="69411-117">PackageGroup</span></span> |<span data-ttu-id="69411-118">Falls `$true`, soll **Name** dem Namen einer Paketgruppe für die Verwendung mit einem **PackageManager** entsprechen.</span><span class="sxs-lookup"><span data-stu-id="69411-118">If `$true`, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="69411-119">**PackageGroup** ist ungültig, wenn **FilePath** angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="69411-119">**PackageGroup** is not valid when providing a **FilePath**.</span></span> |
|<span data-ttu-id="69411-120">Arguments</span><span class="sxs-lookup"><span data-stu-id="69411-120">Arguments</span></span> |<span data-ttu-id="69411-121">Eine Zeichenfolge mit Argumenten, die exakt wie angegeben an das Paket übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="69411-121">A string of arguments that will be passed to the package exactly as provided.</span></span> |
|<span data-ttu-id="69411-122">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="69411-122">ReturnCode</span></span> |<span data-ttu-id="69411-123">Der erwartete Rückgabecode.</span><span class="sxs-lookup"><span data-stu-id="69411-123">The expected return code.</span></span> <span data-ttu-id="69411-124">Wenn der tatsächliche Rückgabecode nicht dem erwarteten Wert entspricht, gibt die Konfiguration einen Fehler zurück.</span><span class="sxs-lookup"><span data-stu-id="69411-124">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span> |
|<span data-ttu-id="69411-125">FilePath</span><span class="sxs-lookup"><span data-stu-id="69411-125">FilePath</span></span> |<span data-ttu-id="69411-126">Der Dateipfad, in dem das Paket gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="69411-126">The file path where the package resides.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="69411-127">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="69411-127">Common properties</span></span>

|<span data-ttu-id="69411-128">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="69411-128">Property</span></span> |<span data-ttu-id="69411-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="69411-129">Description</span></span> |
|---|---|
|<span data-ttu-id="69411-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="69411-130">DependsOn</span></span> |<span data-ttu-id="69411-131">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="69411-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="69411-132">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="69411-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="69411-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="69411-133">Ensure</span></span> |<span data-ttu-id="69411-134">Bestimmt, ob das Vorhandensein des Pakets geprüft werden soll.</span><span class="sxs-lookup"><span data-stu-id="69411-134">Determines whether to check if the package exists.</span></span> <span data-ttu-id="69411-135">Legen Sie diese Eigenschaft auf **Present** fest, um sicherzustellen, dass das Paket vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="69411-135">Set this property to **Present** to ensure the package exists.</span></span> <span data-ttu-id="69411-136">Legen Sie sie auf **Absent** fest, um sicherzustellen, dass das Paket nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="69411-136">Set it to **Absent** to ensure the package does not exist.</span></span> <span data-ttu-id="69411-137">Der Standardwert ist **Present**.</span><span class="sxs-lookup"><span data-stu-id="69411-137">The default value is **Present**.</span></span> |

## <a name="example"></a><span data-ttu-id="69411-138">Beispiel</span><span class="sxs-lookup"><span data-stu-id="69411-138">Example</span></span>

<span data-ttu-id="69411-139">Im folgende Beispiel wird sichergestellt, dass das Paket mit dem Namen „httpd“ mit dem Paket-Manager „Yum“ auf einem Linux-Computer installiert wird.</span><span class="sxs-lookup"><span data-stu-id="69411-139">The following example ensures that the package named "httpd" is installed on a Linux computer, using the "Yum" package manager.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxPackage httpd
    {
        Name = "httpd"
        Ensure = "Present"
        PackageManager = "Yum"
    }
}
```