---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „PackageManagementSource“
ms.openlocfilehash: 3e67cec9058ecb0e43f882f98f5ec8b92e261a09
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="e697d-103">DSC-Ressource „PackageManagementSource“</span><span class="sxs-lookup"><span data-stu-id="e697d-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="e697d-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e697d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e697d-105">Die Ressource **PackageManagementSource** in Windows PowerShell Desired State Configuration (DSC) bietet einen Mechanismus zum Registrieren von Paketverwaltungsquellen auf einem Zielknoten sowie zum Aufheben der Registrierung.</span><span class="sxs-lookup"><span data-stu-id="e697d-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="e697d-106">
  **Auf diese Weise registrierte Verwaltungspaketquellen werden im Systemkontext registriert und können vom Systemkonto oder der DSC-Engine verwendet werden.**</span><span class="sxs-lookup"><span data-stu-id="e697d-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="e697d-107">Diese Ressource erfordert das Modul **PackageManagement**, das unter http://PowerShellGallery.com verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="e697d-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="e697d-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="e697d-108">Syntax</span></span>

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="e697d-109">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="e697d-109">Properties</span></span>
|  <span data-ttu-id="e697d-110">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="e697d-110">Property</span></span>  |  <span data-ttu-id="e697d-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e697d-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="e697d-112">Name</span><span class="sxs-lookup"><span data-stu-id="e697d-112">Name</span></span>| <span data-ttu-id="e697d-113">Gibt den Namen der Paketquelle an, die auf Ihrem System registriert bzw. deren Registrierung aufgehoben werden soll.</span><span class="sxs-lookup"><span data-stu-id="e697d-113">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="e697d-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="e697d-114">Ensure</span></span>| <span data-ttu-id="e697d-115">Bestimmt, ob die Paketquelle registriert oder die Registrierung aufgehoben werden soll.</span><span class="sxs-lookup"><span data-stu-id="e697d-115">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="e697d-116">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="e697d-116">InstallationPolicy</span></span>| <span data-ttu-id="e697d-117">Bestimmt, ob Sie der Paketquelle vertrauen.</span><span class="sxs-lookup"><span data-stu-id="e697d-117">Determines whether you trust the package source.</span></span> <span data-ttu-id="e697d-118">Entweder „Nicht vertrauenswürdig“, oder „Vertrauenswürdig“.</span><span class="sxs-lookup"><span data-stu-id="e697d-118">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="e697d-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="e697d-119">ProviderName</span></span>| <span data-ttu-id="e697d-120">Gibt den Namen des OneGet-Anbieters an, über den Sie mit der Paketquelle zusammenarbeiten können.</span><span class="sxs-lookup"><span data-stu-id="e697d-120">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="e697d-121">SourceUri</span><span class="sxs-lookup"><span data-stu-id="e697d-121">SourceUri</span></span>| <span data-ttu-id="e697d-122">Gibt den URI der Paketquelle an.</span><span class="sxs-lookup"><span data-stu-id="e697d-122">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="e697d-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="e697d-123">SourceCredential</span></span>| <span data-ttu-id="e697d-124">Ermöglicht den Zugriff auf das Paket für eine Remotequelle.</span><span class="sxs-lookup"><span data-stu-id="e697d-124">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="e697d-125">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e697d-125">Example</span></span>

<span data-ttu-id="e697d-126">Dieses Beispiel registriert die Paketquelle http://nuget.org mithilfe der DSC-Ressource **PackageManagementSource**.</span><span class="sxs-lookup"><span data-stu-id="e697d-126">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceUri   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```