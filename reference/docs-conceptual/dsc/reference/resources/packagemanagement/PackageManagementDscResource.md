---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC-Ressource „PackageManagement“
ms.openlocfilehash: ba8ab1e6c2d79e98084a52e3cffec39d57d800c9
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557157"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="05750-103">DSC-Ressource „PackageManagement“</span><span class="sxs-lookup"><span data-stu-id="05750-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="05750-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="05750-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="05750-105">Die Ressource **PackageManagement** in Windows PowerShell Desired State Configuration (DSC) bietet einen Mechanismus zum Installieren oder Deinstallieren von Paketverwaltungspaketen auf einem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="05750-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="05750-106">Diese Ressource erfordert das Modul **PackageManagement**, das unter [https://PowerShellGallery.com](https://PowerShellGallery.com) verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="05750-106">This resource requires the **PackageManagement** module, available from [https://PowerShellGallery.com](https://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="05750-107">Die folgenden Eigenschaftsinformationen gelten nur für das **PackageManagement**-Modul Version 1.1.7.0 oder höher.</span><span class="sxs-lookup"><span data-stu-id="05750-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="05750-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="05750-108">Syntax</span></span>

```Syntax
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ AdditionalParameters = [HashTable] ]
    [ MaximumVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ ProviderName = [string] ]
    [ RequiredVersion = [string] ]
    [ Source = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="05750-109">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="05750-109">Properties</span></span>

|<span data-ttu-id="05750-110">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="05750-110">Property</span></span> |<span data-ttu-id="05750-111">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="05750-111">Description</span></span> |
|---|---|
|<span data-ttu-id="05750-112">Name</span><span class="sxs-lookup"><span data-stu-id="05750-112">Name</span></span> |<span data-ttu-id="05750-113">Gibt den Namen des Pakets an, das installiert oder deinstalliert werden soll.</span><span class="sxs-lookup"><span data-stu-id="05750-113">Specifies the name of the Package to be installed or uninstalled.</span></span> |
|<span data-ttu-id="05750-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="05750-114">AdditionalParameters</span></span> |<span data-ttu-id="05750-115">Anbieterspezifische Hashtabelle mit Parametern, die an `Get-Package -AdditionalArguments` übergeben werden würden.</span><span class="sxs-lookup"><span data-stu-id="05750-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="05750-116">Für NuGet-Anbieter können Sie z. B. zusätzliche Parameter wie „DestinationPath“ übergeben.</span><span class="sxs-lookup"><span data-stu-id="05750-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span> |
|<span data-ttu-id="05750-117">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="05750-117">MaximumVersion</span></span> |<span data-ttu-id="05750-118">Gibt die zulässige Höchstversion für das zu suchende Paket an.</span><span class="sxs-lookup"><span data-stu-id="05750-118">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="05750-119">Wenn Sie diesen Parameter nicht hinzufügen, sucht die Ressource nach der höchsten verfügbaren Version des Pakets.</span><span class="sxs-lookup"><span data-stu-id="05750-119">If you do not add this parameter, the resource finds the highest available version of the package.</span></span> |
|<span data-ttu-id="05750-120">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="05750-120">MinimumVersion</span></span> |<span data-ttu-id="05750-121">Gibt die zulässige Mindestversion für das zu suchende Paket an.</span><span class="sxs-lookup"><span data-stu-id="05750-121">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="05750-122">Wenn Sie diesen Parameter nicht hinzufügen, installiert die Ressource die höchste verfügbare Version des Pakets, wobei die vom Parameter **MaximumVersion** angegebene Höchstversion berücksichtigt wird.</span><span class="sxs-lookup"><span data-stu-id="05750-122">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the **MaximumVersion** parameter.</span></span> |
|<span data-ttu-id="05750-123">ProviderName</span><span class="sxs-lookup"><span data-stu-id="05750-123">ProviderName</span></span> |<span data-ttu-id="05750-124">Gibt den Namen eines Paketanbieters an, auf den Ihre Paketsuche sich erstrecken soll.</span><span class="sxs-lookup"><span data-stu-id="05750-124">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="05750-125">Paketanbieternamen können Sie durch Ausführen des Cmdlets `Get-PackageProvider` abrufen.</span><span class="sxs-lookup"><span data-stu-id="05750-125">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span> |
|<span data-ttu-id="05750-126">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="05750-126">RequiredVersion</span></span> |<span data-ttu-id="05750-127">Gibt die genaue Version des Pakets an, das Sie installieren möchten.</span><span class="sxs-lookup"><span data-stu-id="05750-127">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="05750-128">Wenn Sie diesen Parameter nicht angeben, installiert diese DSC-Ressource die neueste verfügbare Version des Pakets, wobei die vom Parameter **MaximumVersion** angegebene Höchstversion berücksichtigt wird.</span><span class="sxs-lookup"><span data-stu-id="05750-128">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the **MaximumVersion** parameter.</span></span> |
|<span data-ttu-id="05750-129">`Source`</span><span class="sxs-lookup"><span data-stu-id="05750-129">Source</span></span> |<span data-ttu-id="05750-130">Gibt den Namen der Paketquelle an, unter der sich das Paket befindet.</span><span class="sxs-lookup"><span data-stu-id="05750-130">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="05750-131">Dies kann entweder ein URI oder eine Quelle sein, die bei `Register-PackageSource` oder der DSC-Ressource „PackageManagementSource“ registriert ist.</span><span class="sxs-lookup"><span data-stu-id="05750-131">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span> |
|<span data-ttu-id="05750-132">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="05750-132">SourceCredential</span></span> |<span data-ttu-id="05750-133">Gibt ein Benutzerkonto an, das über Rechte zum Installieren eines Pakets für einen angegebenen Paketanbieter oder eine bestimmte Quelle verfügt.</span><span class="sxs-lookup"><span data-stu-id="05750-133">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span> |

## <a name="additional-parameters"></a><span data-ttu-id="05750-134">Zusätzliche Parameter</span><span class="sxs-lookup"><span data-stu-id="05750-134">Additional Parameters</span></span>

<span data-ttu-id="05750-135">In der folgenden Tabelle sind die Optionen für die Eigenschaft „AdditionalParameters“ aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="05750-135">The following table lists options for the AdditionalParameters property.</span></span>

|<span data-ttu-id="05750-136">Parameter</span><span class="sxs-lookup"><span data-stu-id="05750-136">Parameter</span></span> |<span data-ttu-id="05750-137">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="05750-137">Description</span></span> |
|---|---|
|<span data-ttu-id="05750-138">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="05750-138">DestinationPath</span></span> |<span data-ttu-id="05750-139">Wird von Anbietern wie dem integrierten NuGet-Anbieter verwendet.</span><span class="sxs-lookup"><span data-stu-id="05750-139">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="05750-140">Gibt einen Dateispeicherort an, an dem das Paket installiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="05750-140">Specifies a file location where you want the package to be installed.</span></span> |
|<span data-ttu-id="05750-141">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="05750-141">InstallationPolicy</span></span> |<span data-ttu-id="05750-142">Wird von Anbietern wie dem integrierten NuGet-Anbieter verwendet.</span><span class="sxs-lookup"><span data-stu-id="05750-142">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="05750-143">Bestimmt, ob Sie der Paketquelle vertrauen.</span><span class="sxs-lookup"><span data-stu-id="05750-143">Determines whether you trust the package's source.</span></span> <span data-ttu-id="05750-144">Enthält einen der folgenden Werte: **Untrusted** (Nicht vertrauenswürdig) oder **Trusted** (Vertrauenswürdig).</span><span class="sxs-lookup"><span data-stu-id="05750-144">One of: **Untrusted** or **Trusted**.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="05750-145">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="05750-145">Common properties</span></span>

|<span data-ttu-id="05750-146">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="05750-146">Property</span></span> |<span data-ttu-id="05750-147">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="05750-147">Description</span></span> |
|---|---|
|<span data-ttu-id="05750-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="05750-148">DependsOn</span></span> |<span data-ttu-id="05750-149">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="05750-149">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="05750-150">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="05750-150">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="05750-151">Ensure</span><span class="sxs-lookup"><span data-stu-id="05750-151">Ensure</span></span> |<span data-ttu-id="05750-152">Bestimmt, ob das Paket installiert oder deinstalliert werden soll.</span><span class="sxs-lookup"><span data-stu-id="05750-152">Determines whether the package is to be installed or uninstalled.</span></span> <span data-ttu-id="05750-153">Der Standardwert ist **Present**.</span><span class="sxs-lookup"><span data-stu-id="05750-153">The default value is **Present**.</span></span> |
|<span data-ttu-id="05750-154">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="05750-154">PsDscRunAsCredential</span></span> |<span data-ttu-id="05750-155">Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest.</span><span class="sxs-lookup"><span data-stu-id="05750-155">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="05750-156">Die allgemeine Eigenschaft **PsDscRunAsCredential** wurde in WMF 5.0 hinzugefügt, um das Ausführen einer beliebigen DSC-Ressource in Verbindung mit anderen Anmeldeinformationen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="05750-156">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="05750-157">Weitere Informationen finden Sie unter [Use Credentials with DSC Resources](../../../configurations/runasuser.md) (Verwenden von Anmeldeinformationen mit DSC-Ressourcen).</span><span class="sxs-lookup"><span data-stu-id="05750-157">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="05750-158">Beispiel</span><span class="sxs-lookup"><span data-stu-id="05750-158">Example</span></span>

<span data-ttu-id="05750-159">In diesem Beispiel werden das NuGet-Paket **JQuery** und das PowerShell-Modul **GistProvider** mithilfe der DSC-Ressource **PackageManagement** installiert.</span><span class="sxs-lookup"><span data-stu-id="05750-159">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="05750-160">In diesem Beispiel wird zunächst sichergestellt, dass die erforderlichen Paketquellen verfügbar sind. Anschließend wird der erwartete Zustand der **JQuery**- und **GistProvider**-Pakete (NuGet bzw. PowerShell) definiert.</span><span class="sxs-lookup"><span data-stu-id="05750-160">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

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
        SourceLocation   = "https://www.powershellgallery.com/api/v2"
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
