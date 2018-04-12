---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „PackageManagement“
ms.openlocfilehash: e6eea9f0bae42e131976dacb9813da759ff31239
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="235b9-103">DSC-Ressource „PackageManagement“</span><span class="sxs-lookup"><span data-stu-id="235b9-103">DSC PackageManagement Resource</span></span>

> <span data-ttu-id="235b9-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="235b9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="235b9-105">Die Ressource **PackageManagement** in Windows PowerShell Desired State Configuration (DSC) bietet einen Mechanismus zum Installieren oder Deinstallieren von Paketverwaltungspaketen auf einem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="235b9-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="235b9-106">Diese Ressource erfordert das Modul **PackageManagement**, das unter http://PowerShellGallery.com verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="235b9-106">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="235b9-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="235b9-107">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="235b9-108">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="235b9-108">Properties</span></span>
|  <span data-ttu-id="235b9-109">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="235b9-109">Property</span></span>  |  <span data-ttu-id="235b9-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="235b9-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="235b9-111">Name</span><span class="sxs-lookup"><span data-stu-id="235b9-111">Name</span></span>| <span data-ttu-id="235b9-112">Gibt den Namen des Pakets an, das installiert oder deinstalliert werden soll.</span><span class="sxs-lookup"><span data-stu-id="235b9-112">Specifies the name of the Package to be installed or uninstalled.</span></span>|
| <span data-ttu-id="235b9-113">Source</span><span class="sxs-lookup"><span data-stu-id="235b9-113">Source</span></span>| <span data-ttu-id="235b9-114">Gibt den Namen der Paketquelle an, unter der sich das Paket befindet.</span><span class="sxs-lookup"><span data-stu-id="235b9-114">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="235b9-115">Dies kann entweder ein URI oder eine Quelle sein, die bei der DSC-Ressource „Register-PackageSource“ oder „PackageManagementSource“ registriert ist.</span><span class="sxs-lookup"><span data-stu-id="235b9-115">This can either be a URI or a source registered with Register-PackageSource or PackageManagementSource DSC resource.</span></span> <span data-ttu-id="235b9-116">Die DSC-Ressourcen „MSFT_PackageManagementSource“ kann ebenfalls eine Paketquelle registrieren.</span><span class="sxs-lookup"><span data-stu-id="235b9-116">The DSC resource MSFT_PackageManagementSource can also register a package source.</span></span>|
| <span data-ttu-id="235b9-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="235b9-117">Ensure</span></span>| <span data-ttu-id="235b9-118">Bestimmt, ob das Paket installiert oder deinstalliert werden soll.</span><span class="sxs-lookup"><span data-stu-id="235b9-118">Determines whether the package is to be installed or uninstalled.</span></span>|
| <span data-ttu-id="235b9-119">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="235b9-119">RequiredVersion</span></span>| <span data-ttu-id="235b9-120">Gibt die genaue Version des Pakets an, das Sie installieren möchten.</span><span class="sxs-lookup"><span data-stu-id="235b9-120">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="235b9-121">Wenn Sie diesen Parameter nicht angeben, installiert diese DSC-Ressource die neueste verfügbare Version des Pakets, wobei Einstellung des Parameters „MaximumVersion“ berücksichtigt wird.</span><span class="sxs-lookup"><span data-stu-id="235b9-121">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the MaximumVersion parameter.</span></span>|
| <span data-ttu-id="235b9-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="235b9-122">MinimumVersion</span></span>| <span data-ttu-id="235b9-123">Gibt die zulässige Mindestversion für das zu installierende Paket an.</span><span class="sxs-lookup"><span data-stu-id="235b9-123">Specifies the minimum allowed version of the package that you want to install.</span></span> <span data-ttu-id="235b9-124">Wenn Sie diesen Parameter nicht hinzufügen, installiert diese DSC-Ressource die höchste verfügbare Version des Pakets, wobei Einstellung des Parameters „MaximumVersion“ berücksichtigt wird.</span><span class="sxs-lookup"><span data-stu-id="235b9-124">If you do not add this parameter, this DSC resource intalls the highest available version of the package that also satisfies any maximum specified version specified by the MaximumVersion parameter.</span></span>|
| <span data-ttu-id="235b9-125">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="235b9-125">MaximumVersion</span></span>| <span data-ttu-id="235b9-126">Gibt die zulässige Höchstversion für das zu installierende Paket an.</span><span class="sxs-lookup"><span data-stu-id="235b9-126">Specifies the maximum allowed version of the package that you want to install.</span></span> <span data-ttu-id="235b9-127">Wenn Sie diesen Parameter nicht angeben, installiert diese DSC-Ressource die höchste verfügbare Version des Pakets.</span><span class="sxs-lookup"><span data-stu-id="235b9-127">If you do not specify this parameter, this DSC resource installs the highest-numbered available version of the package.</span></span>|
| <span data-ttu-id="235b9-128">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="235b9-128">SourceCredential</span></span> | <span data-ttu-id="235b9-129">Gibt ein Benutzerkonto an, das über Rechte zum Installieren eines Pakets für einen angegebenen Paketanbieter oder eine bestimmte Quelle verfügt.</span><span class="sxs-lookup"><span data-stu-id="235b9-129">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>|
| <span data-ttu-id="235b9-130">ProviderName</span><span class="sxs-lookup"><span data-stu-id="235b9-130">ProviderName</span></span>| <span data-ttu-id="235b9-131">Gibt den Namen eines Paketanbieters an, auf den Ihre Paketsuche sich erstrecken soll.</span><span class="sxs-lookup"><span data-stu-id="235b9-131">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="235b9-132">Paketanbieternamen können Sie durch Ausführen des Cmdlets „Get-PackageProvider“ abrufen.</span><span class="sxs-lookup"><span data-stu-id="235b9-132">You can get package provider names by running the Get-PackageProvider cmdlet.</span></span>|
| <span data-ttu-id="235b9-133">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="235b9-133">AdditionalParameters</span></span>| <span data-ttu-id="235b9-134">Anbieterspezifische Parameter, die als eine Hashtabelle übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="235b9-134">Provider specific parameters that are passed as an Hashtable.</span></span> <span data-ttu-id="235b9-135">Für NuGet-Anbieter können Sie z. B. zusätzliche Parameter wie „DestinationPath“ übergeben.</span><span class="sxs-lookup"><span data-stu-id="235b9-135">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>|

## <a name="additional-parameters"></a><span data-ttu-id="235b9-136">Zusätzliche Parameter</span><span class="sxs-lookup"><span data-stu-id="235b9-136">Additional Parameters</span></span>
<span data-ttu-id="235b9-137">In der folgenden Tabelle sind die Optionen für die Eigenschaft „AdditionalParameters“ aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="235b9-137">The following table lists options for the AdditionalParameters property.</span></span>
|  <span data-ttu-id="235b9-138">Parameter</span><span class="sxs-lookup"><span data-stu-id="235b9-138">Parameter</span></span>  | <span data-ttu-id="235b9-139">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="235b9-139">Description</span></span>   |
|---|---|
| <span data-ttu-id="235b9-140">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="235b9-140">DestinationPath</span></span>| <span data-ttu-id="235b9-141">Wird von Anbietern wie dem integrierten NuGet-Anbieter verwendet.</span><span class="sxs-lookup"><span data-stu-id="235b9-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="235b9-142">Gibt einen Dateispeicherort an, an dem das Paket installiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="235b9-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="235b9-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="235b9-143">InstallationPolicy</span></span>| <span data-ttu-id="235b9-144">Wird von Anbietern wie dem integrierten NuGet-Anbieter verwendet.</span><span class="sxs-lookup"><span data-stu-id="235b9-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="235b9-145">Bestimmt, ob Sie der Paketquelle vertrauen.</span><span class="sxs-lookup"><span data-stu-id="235b9-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="235b9-146">Entweder „Nicht vertrauenswürdig“, oder „Vertrauenswürdig“.</span><span class="sxs-lookup"><span data-stu-id="235b9-146">One of: "Untrusted", "Trusted".</span></span>|

## <a name="example"></a><span data-ttu-id="235b9-147">Beispiel</span><span class="sxs-lookup"><span data-stu-id="235b9-147">Example</span></span>

<span data-ttu-id="235b9-148">In diesem Beispiel werden das NuGet-Paket **JQuery** und das PowerShell-Modul **GistProvider** mithilfe der DSC-Ressource **PackageManagement** installiert.</span><span class="sxs-lookup"><span data-stu-id="235b9-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="235b9-149">In diesem Beispiel wird zunächst sichergestellt, dass die erforderlichen Paketquellen verfügbar sind. Anschließend wird der erwartete Zustand der **JQuery**- und **GistProvider**-Pakete (NuGet bzw. PowerShell) definiert.</span><span class="sxs-lookup"><span data-stu-id="235b9-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceUri   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceUri   = "https://www.powershellgallery.com/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```