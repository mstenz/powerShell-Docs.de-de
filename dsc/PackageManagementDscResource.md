---
ms.date: 06/20/2018
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „PackageManagement“
ms.openlocfilehash: 18cbbfe0715c82dcfdf4a5fb6ee36ee814e43d3b
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268091"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="94bf2-103">DSC-Ressource „PackageManagement“</span><span class="sxs-lookup"><span data-stu-id="94bf2-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="94bf2-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="94bf2-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="94bf2-105">Die Ressource **PackageManagement** in Windows PowerShell Desired State Configuration (DSC) bietet einen Mechanismus zum Installieren oder Deinstallieren von Paketverwaltungspaketen auf einem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="94bf2-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="94bf2-106">Diese Ressource erfordert das Modul **PackageManagement**, das unter [http://PowerShellGallery.com](http://PowerShellGallery.com) verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="94bf2-106">This resource requires the **PackageManagement** module, available from [http://PowerShellGallery.com](http://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="94bf2-107">Die folgenden Eigenschaftsinformationen gelten nur für das **PackageManagement**-Modul Version 1.1.7.0 oder höher.</span><span class="sxs-lookup"><span data-stu-id="94bf2-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="94bf2-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="94bf2-108">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="94bf2-109">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="94bf2-109">Properties</span></span>

| <span data-ttu-id="94bf2-110">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="94bf2-110">Property</span></span> | <span data-ttu-id="94bf2-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="94bf2-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="94bf2-112">Name</span><span class="sxs-lookup"><span data-stu-id="94bf2-112">Name</span></span>| <span data-ttu-id="94bf2-113">Gibt den Namen des Pakets an, das installiert oder deinstalliert werden soll.</span><span class="sxs-lookup"><span data-stu-id="94bf2-113">Specifies the name of the Package to be installed or uninstalled.</span></span>|
| <span data-ttu-id="94bf2-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="94bf2-114">AdditionalParameters</span></span>| <span data-ttu-id="94bf2-115">Anbieterspezifische Hashtabelle mit Parametern, die an `Get-Package -AdditionalArguments` übergeben werden würden.</span><span class="sxs-lookup"><span data-stu-id="94bf2-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="94bf2-116">Für NuGet-Anbieter können Sie z. B. zusätzliche Parameter wie „DestinationPath“ übergeben.</span><span class="sxs-lookup"><span data-stu-id="94bf2-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>|
| <span data-ttu-id="94bf2-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="94bf2-117">Ensure</span></span>| <span data-ttu-id="94bf2-118">Bestimmt, ob das Paket installiert oder deinstalliert werden soll.</span><span class="sxs-lookup"><span data-stu-id="94bf2-118">Determines whether the package is to be installed or uninstalled.</span></span>|
| <span data-ttu-id="94bf2-119">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="94bf2-119">MaximumVersion</span></span>|<span data-ttu-id="94bf2-120">Gibt die zulässige Höchstversion für das zu suchende Paket an.</span><span class="sxs-lookup"><span data-stu-id="94bf2-120">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="94bf2-121">Wenn Sie diesen Parameter nicht hinzufügen, sucht die Ressource nach der höchsten verfügbaren Version des Pakets.</span><span class="sxs-lookup"><span data-stu-id="94bf2-121">If you do not add this parameter, the resource finds the highest available version of the package.</span></span>|
| <span data-ttu-id="94bf2-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="94bf2-122">MinimumVersion</span></span>|<span data-ttu-id="94bf2-123">Gibt die zulässige Mindestversion für das zu suchende Paket an.</span><span class="sxs-lookup"><span data-stu-id="94bf2-123">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="94bf2-124">Wenn Sie diesen Parameter nicht hinzufügen, installiert die Ressource die höchste verfügbare Version des Pakets, wobei die vom Parameter _MaximumVersion_ angegebene Höchstversion berücksichtigt wird.</span><span class="sxs-lookup"><span data-stu-id="94bf2-124">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="94bf2-125">ProviderName</span><span class="sxs-lookup"><span data-stu-id="94bf2-125">ProviderName</span></span>| <span data-ttu-id="94bf2-126">Gibt den Namen eines Paketanbieters an, auf den Ihre Paketsuche sich erstrecken soll.</span><span class="sxs-lookup"><span data-stu-id="94bf2-126">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="94bf2-127">Paketanbieternamen können Sie durch Ausführen des Cmdlets `Get-PackageProvider` abrufen.</span><span class="sxs-lookup"><span data-stu-id="94bf2-127">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>|
| <span data-ttu-id="94bf2-128">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="94bf2-128">RequiredVersion</span></span>| <span data-ttu-id="94bf2-129">Gibt die genaue Version des Pakets an, das Sie installieren möchten.</span><span class="sxs-lookup"><span data-stu-id="94bf2-129">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="94bf2-130">Wenn Sie diesen Parameter nicht angeben, installiert diese DSC-Ressource die neueste verfügbare Version des Pakets, wobei die vom Parameter _MaximumVersion_ angegebene Höchstversion berücksichtigt wird.</span><span class="sxs-lookup"><span data-stu-id="94bf2-130">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="94bf2-131">Source</span><span class="sxs-lookup"><span data-stu-id="94bf2-131">Source</span></span>| <span data-ttu-id="94bf2-132">Gibt den Namen der Paketquelle an, unter der sich das Paket befindet.</span><span class="sxs-lookup"><span data-stu-id="94bf2-132">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="94bf2-133">Dies kann entweder ein URI oder eine Quelle sein, die bei `Register-PackageSource` oder der DSC-Ressource „PackageManagementSource“ registriert ist.</span><span class="sxs-lookup"><span data-stu-id="94bf2-133">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span>|
| <span data-ttu-id="94bf2-134">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="94bf2-134">SourceCredential</span></span> | <span data-ttu-id="94bf2-135">Gibt ein Benutzerkonto an, das über Rechte zum Installieren eines Pakets für einen angegebenen Paketanbieter oder eine bestimmte Quelle verfügt.</span><span class="sxs-lookup"><span data-stu-id="94bf2-135">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>|

## <a name="additional-parameters"></a><span data-ttu-id="94bf2-136">Zusätzliche Parameter</span><span class="sxs-lookup"><span data-stu-id="94bf2-136">Additional Parameters</span></span>

<span data-ttu-id="94bf2-137">In der folgenden Tabelle sind die Optionen für die Eigenschaft „AdditionalParameters“ aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="94bf2-137">The following table lists options for the AdditionalParameters property.</span></span>

| <span data-ttu-id="94bf2-138">Parameter</span><span class="sxs-lookup"><span data-stu-id="94bf2-138">Parameter</span></span> | <span data-ttu-id="94bf2-139">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="94bf2-139">Description</span></span> |
| --- | --- |
| <span data-ttu-id="94bf2-140">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="94bf2-140">DestinationPath</span></span>| <span data-ttu-id="94bf2-141">Wird von Anbietern wie dem integrierten NuGet-Anbieter verwendet.</span><span class="sxs-lookup"><span data-stu-id="94bf2-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="94bf2-142">Gibt einen Dateispeicherort an, an dem das Paket installiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="94bf2-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="94bf2-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="94bf2-143">InstallationPolicy</span></span>| <span data-ttu-id="94bf2-144">Wird von Anbietern wie dem integrierten NuGet-Anbieter verwendet.</span><span class="sxs-lookup"><span data-stu-id="94bf2-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="94bf2-145">Bestimmt, ob Sie der Paketquelle vertrauen.</span><span class="sxs-lookup"><span data-stu-id="94bf2-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="94bf2-146">Enthält einen der folgenden Werte: `Untrusted`, `Trusted`.</span><span class="sxs-lookup"><span data-stu-id="94bf2-146">One of: `Untrusted`, `Trusted`.</span></span>|

## <a name="example"></a><span data-ttu-id="94bf2-147">Beispiel</span><span class="sxs-lookup"><span data-stu-id="94bf2-147">Example</span></span>

<span data-ttu-id="94bf2-148">In diesem Beispiel werden das NuGet-Paket **JQuery** und das PowerShell-Modul **GistProvider** mithilfe der DSC-Ressource **PackageManagement** installiert.</span><span class="sxs-lookup"><span data-stu-id="94bf2-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="94bf2-149">In diesem Beispiel wird zunächst sichergestellt, dass die erforderlichen Paketquellen verfügbar sind. Anschließend wird der erwartete Zustand der **JQuery**- und **GistProvider**-Pakete (NuGet bzw. PowerShell) definiert.</span><span class="sxs-lookup"><span data-stu-id="94bf2-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
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