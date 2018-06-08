---
ms.date: 06/20/2018
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „PackageManagementSource“
ms.openlocfilehash: 5d049b05c387cafe27edb202d569852b10852dce
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753769"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="15650-103">DSC-Ressource „PackageManagementSource“</span><span class="sxs-lookup"><span data-stu-id="15650-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="15650-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="15650-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="15650-105">Die Ressource **PackageManagementSource** in Windows PowerShell Desired State Configuration (DSC) bietet einen Mechanismus zum Registrieren von Paketverwaltungsquellen auf einem Zielknoten sowie zum Aufheben der Registrierung.</span><span class="sxs-lookup"><span data-stu-id="15650-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="15650-106">
  **Auf diese Weise registrierte Verwaltungspaketquellen werden im Systemkontext registriert und können vom Systemkonto oder der DSC-Engine verwendet werden.**</span><span class="sxs-lookup"><span data-stu-id="15650-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="15650-107">Diese Ressource erfordert das Modul **PackageManagement**, das unter http://PowerShellGallery.com verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="15650-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="15650-108">Die folgenden Eigenschaftsinformationen gelten nur für das **PackageManagement**-Modul Version 1.1.7.0 oder höher.</span><span class="sxs-lookup"><span data-stu-id="15650-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="15650-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="15650-109">Syntax</span></span>

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="15650-110">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="15650-110">Properties</span></span>

|  <span data-ttu-id="15650-111">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="15650-111">Property</span></span>  |  <span data-ttu-id="15650-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="15650-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="15650-113">Name</span><span class="sxs-lookup"><span data-stu-id="15650-113">Name</span></span>| <span data-ttu-id="15650-114">Gibt den Namen der Paketquelle an, die auf Ihrem System registriert bzw. deren Registrierung aufgehoben werden soll.</span><span class="sxs-lookup"><span data-stu-id="15650-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="15650-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="15650-115">ProviderName</span></span>| <span data-ttu-id="15650-116">Gibt den Namen des OneGet-Anbieters an, über den Sie mit der Paketquelle zusammenarbeiten können.</span><span class="sxs-lookup"><span data-stu-id="15650-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="15650-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="15650-117">SourceLocation</span></span>| <span data-ttu-id="15650-118">Gibt den URI der Paketquelle an.</span><span class="sxs-lookup"><span data-stu-id="15650-118">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="15650-119">Ensure</span><span class="sxs-lookup"><span data-stu-id="15650-119">Ensure</span></span>| <span data-ttu-id="15650-120">Bestimmt, ob die Paketquelle registriert oder die Registrierung aufgehoben werden soll.</span><span class="sxs-lookup"><span data-stu-id="15650-120">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="15650-121">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="15650-121">InstallationPolicy</span></span>| <span data-ttu-id="15650-122">Wird von Anbietern wie dem integrierten NuGet-Anbieter verwendet.</span><span class="sxs-lookup"><span data-stu-id="15650-122">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="15650-123">Bestimmt, ob Sie der Paketquelle vertrauen.</span><span class="sxs-lookup"><span data-stu-id="15650-123">Determines whether you trust the package's source.</span></span> <span data-ttu-id="15650-124">Entweder „Nicht vertrauenswürdig“, oder „Vertrauenswürdig“.</span><span class="sxs-lookup"><span data-stu-id="15650-124">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="15650-125">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="15650-125">SourceCredential</span></span>| <span data-ttu-id="15650-126">Ermöglicht den Zugriff auf das Paket für eine Remotequelle.</span><span class="sxs-lookup"><span data-stu-id="15650-126">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="15650-127">Beispiel</span><span class="sxs-lookup"><span data-stu-id="15650-127">Example</span></span>

<span data-ttu-id="15650-128">Dieses Beispiel registriert die Paketquelle http://nuget.org mithilfe der DSC-Ressource **PackageManagementSource**.</span><span class="sxs-lookup"><span data-stu-id="15650-128">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```