---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC-Ressource „PackageManagementSource“
ms.openlocfilehash: 20b7851e44751d4bd0add718d2f7294d5215ab70
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954787"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="fe20b-103">DSC-Ressource „PackageManagementSource“</span><span class="sxs-lookup"><span data-stu-id="fe20b-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="fe20b-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="fe20b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="fe20b-105">Die Ressource **PackageManagementSource** in Windows PowerShell Desired State Configuration (DSC) bietet einen Mechanismus zum Registrieren von Paketverwaltungsquellen auf einem Zielknoten sowie zum Aufheben der Registrierung.</span><span class="sxs-lookup"><span data-stu-id="fe20b-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span>
<span data-ttu-id="fe20b-106">**Auf diese Weise registrierte Verwaltungspaketquellen werden im Systemkontext registriert und können vom Systemkonto oder der DSC-Engine verwendet werden.**</span><span class="sxs-lookup"><span data-stu-id="fe20b-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="fe20b-107">Diese Ressource erfordert das Modul **PackageManagement**, das im [PowerShell-Katalog](https://PowerShellGallery.com) verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="fe20b-107">This resource requires the **PackageManagement** module, available from the [PowerShell Gallery](https://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fe20b-108">Die folgenden Eigenschaftsinformationen gelten nur für das **PackageManagement**-Modul Version 1.1.7.0 oder höher.</span><span class="sxs-lookup"><span data-stu-id="fe20b-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="fe20b-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="fe20b-109">Syntax</span></span>

```Syntax
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [ InstallationPolicy = [string]{ Trusted | Untrusted } ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="fe20b-110">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="fe20b-110">Properties</span></span>

|<span data-ttu-id="fe20b-111">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="fe20b-111">Property</span></span> |<span data-ttu-id="fe20b-112">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="fe20b-112">Description</span></span> |
|---|---|
|<span data-ttu-id="fe20b-113">Name</span><span class="sxs-lookup"><span data-stu-id="fe20b-113">Name</span></span> |<span data-ttu-id="fe20b-114">Gibt den Namen der Paketquelle an, die auf Ihrem System registriert bzw. deren Registrierung aufgehoben werden soll.</span><span class="sxs-lookup"><span data-stu-id="fe20b-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span> |
|<span data-ttu-id="fe20b-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="fe20b-115">ProviderName</span></span> |<span data-ttu-id="fe20b-116">Gibt den Namen des OneGet-Anbieters an, über den Sie mit der Paketquelle zusammenarbeiten können.</span><span class="sxs-lookup"><span data-stu-id="fe20b-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span> |
|<span data-ttu-id="fe20b-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="fe20b-117">SourceLocation</span></span> |<span data-ttu-id="fe20b-118">Gibt den URI der Paketquelle an.</span><span class="sxs-lookup"><span data-stu-id="fe20b-118">Specifies the URI of the package source.</span></span> |
|<span data-ttu-id="fe20b-119">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="fe20b-119">InstallationPolicy</span></span> |<span data-ttu-id="fe20b-120">Wird von Anbietern wie dem integrierten NuGet-Anbieter verwendet.</span><span class="sxs-lookup"><span data-stu-id="fe20b-120">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="fe20b-121">Bestimmt, ob Sie der Paketquelle vertrauen.</span><span class="sxs-lookup"><span data-stu-id="fe20b-121">Determines whether you trust the package's source.</span></span> <span data-ttu-id="fe20b-122">Enthält einen der folgenden Werte: **Untrusted** (Nicht vertrauenswürdig) oder **Trusted** (Vertrauenswürdig).</span><span class="sxs-lookup"><span data-stu-id="fe20b-122">One of: **Untrusted** or **Trusted**.</span></span> |
|<span data-ttu-id="fe20b-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="fe20b-123">SourceCredential</span></span> |<span data-ttu-id="fe20b-124">Ermöglicht den Zugriff auf das Paket für eine Remotequelle.</span><span class="sxs-lookup"><span data-stu-id="fe20b-124">Provides access to the package on a remote source.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="fe20b-125">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="fe20b-125">Common properties</span></span>

|<span data-ttu-id="fe20b-126">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="fe20b-126">Property</span></span> |<span data-ttu-id="fe20b-127">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="fe20b-127">Description</span></span> |
|---|---|
|<span data-ttu-id="fe20b-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="fe20b-128">DependsOn</span></span> |<span data-ttu-id="fe20b-129">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="fe20b-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="fe20b-130">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="fe20b-130">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="fe20b-131">Ensure</span><span class="sxs-lookup"><span data-stu-id="fe20b-131">Ensure</span></span> |<span data-ttu-id="fe20b-132">Bestimmt, ob die Paketquelle registriert oder die Registrierung aufgehoben werden soll.</span><span class="sxs-lookup"><span data-stu-id="fe20b-132">Determines whether the package source is to be registered or unregistered.</span></span> <span data-ttu-id="fe20b-133">Der Standardwert ist **Present**.</span><span class="sxs-lookup"><span data-stu-id="fe20b-133">The default value is **Present**.</span></span> |
|<span data-ttu-id="fe20b-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="fe20b-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="fe20b-135">Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest.</span><span class="sxs-lookup"><span data-stu-id="fe20b-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="fe20b-136">Die allgemeine Eigenschaft **PsDscRunAsCredential** wurde in WMF 5.0 hinzugefügt, um das Ausführen einer beliebigen DSC-Ressource in Verbindung mit anderen Anmeldeinformationen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="fe20b-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="fe20b-137">Weitere Informationen finden Sie unter [Use Credentials with DSC Resources](../../../configurations/runasuser.md) (Verwenden von Anmeldeinformationen mit DSC-Ressourcen).</span><span class="sxs-lookup"><span data-stu-id="fe20b-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="fe20b-138">Beispiel</span><span class="sxs-lookup"><span data-stu-id="fe20b-138">Example</span></span>

<span data-ttu-id="fe20b-139">Dieses Beispiel registriert die Paketquelle `https://nuget.org` mithilfe der DSC-Ressource **PackageManagementSource**.</span><span class="sxs-lookup"><span data-stu-id="fe20b-139">This example registers the `https://nuget.org` package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "https://api.nuget.org/api/v3/"
        InstallationPolicy ="Trusted"
    }
}
```