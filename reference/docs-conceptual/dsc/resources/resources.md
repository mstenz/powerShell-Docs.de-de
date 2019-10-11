---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: DSC-Ressourcen
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954247"
---
# <a name="dsc-resources"></a><span data-ttu-id="174f7-103">DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="174f7-103">DSC Resources</span></span>

><span data-ttu-id="174f7-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="174f7-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="174f7-105">DSC-Ressourcen sind die Bausteine einer DSC-Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="174f7-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="174f7-106">Eine Ressource macht Eigenschaften verfügbar, die konfiguriert werden können (Schema), und enthält die PowerShell-Skriptfunktionen, die der lokale Konfigurations-Manager wie gewünscht ausführt.</span><span class="sxs-lookup"><span data-stu-id="174f7-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="174f7-107">Mit einer Ressource kann etwas Allgemeines wie eine Datei oder Spezifisches wie eine IIS-Servereinstellung modelliert werden.</span><span class="sxs-lookup"><span data-stu-id="174f7-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="174f7-108">Gruppen ähnlicher Ressourcen werden in einem DSC-Modul kombiniert, das alle erforderlichen Dateien in einer Struktur organisiert, die portierbar ist und Metadaten zum Bestimmen des Zwecks der Ressourcen enthält.</span><span class="sxs-lookup"><span data-stu-id="174f7-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="174f7-109">Jede Ressource verfügt über ein \*schema, das die Syntax bestimmt, die für die Verwendung der Ressource in einer [Konfiguration](../configurations/configurations.md) erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="174f7-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="174f7-110">Das Schema einer Ressource kann auf folgende Weise definiert werden:</span><span class="sxs-lookup"><span data-stu-id="174f7-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="174f7-111">Datei **„Schema.Mof“** : Die meisten Ressourcen definieren ihr *Schema* in einer Datei „schema.mof“ mithilfe des [Managed Object Format (MOF)](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="174f7-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="174f7-112">**Datei „\<Ressourcenname\>.schema.psm1“** : [Zusammengesetzte Ressourcen](../configurations/compositeConfigs.md) definieren ihr *Schema* in einer Datei „<ResourceName>.schema.psm1“ unter Verwendung eines [Parameterblocks](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="174f7-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="174f7-113">**Datei „\<Ressourcenname\>.psm1“** : Klassenbasierte DSC-Ressourcen definieren ihr *Schema* in der Klassendefinition.</span><span class="sxs-lookup"><span data-stu-id="174f7-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="174f7-114">Syntaxelemente werden als Eigenschaften der Klasse angegeben.</span><span class="sxs-lookup"><span data-stu-id="174f7-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="174f7-115">Weitere Informationen finden Sie unter [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span><span class="sxs-lookup"><span data-stu-id="174f7-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="174f7-116">Um die Syntax für eine DSC-Ressource abzurufen, verwenden Sie das Cmdlet [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) mit dem Parameter `-Syntax`.</span><span class="sxs-lookup"><span data-stu-id="174f7-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="174f7-117">Diese Syntax ist ähnlich wie die Verwendung von [Get-Command](/powershell/module/microsoft.powershell.core/get-command) mit dem Parameter `-Syntax`, um die Cmdlet-Syntax abzurufen.</span><span class="sxs-lookup"><span data-stu-id="174f7-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="174f7-118">Die Ausgabe, die Sie sehen, zeigt die Vorlage für einen Ressourcenblock für die Ressource an, die Sie angeben.</span><span class="sxs-lookup"><span data-stu-id="174f7-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="174f7-119">Die Ausgabe, die Sie sehen, sollte der folgenden Ausgabe ähneln, obwohl sich die Syntax dieser Ressource in Zukunft ändern kann.</span><span class="sxs-lookup"><span data-stu-id="174f7-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="174f7-120">Wie bei der Cmdlet-Syntax sind die *Schlüssel* in eckigen Klammern optional.</span><span class="sxs-lookup"><span data-stu-id="174f7-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="174f7-121">Die Typen geben den Typ der Daten an, die jeder Schlüssel erwartet.</span><span class="sxs-lookup"><span data-stu-id="174f7-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="174f7-122">Der Schlüssel **Ensure** ist optional, da er standardmäßig auf „Present“ (Vorhanden) festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="174f7-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

<span data-ttu-id="174f7-123">Innerhalb einer Konfiguration könnte ein **Service**-Ressourcenblock wie folgt aussehen, um sicherzustellen (**Ensure**), dass der Spoolerdienst ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="174f7-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="174f7-124">Bevor Sie eine Ressource in einer Konfiguration verwenden, müssen Sie sie mit [Import-DSCResource](../configurations/import-dscresource.md) importieren.</span><span class="sxs-lookup"><span data-stu-id="174f7-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

<span data-ttu-id="174f7-125">Konfigurationen können mehrere Instanzen desselben Ressourcentyps enthalten.</span><span class="sxs-lookup"><span data-stu-id="174f7-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="174f7-126">Jede Instanz muss eindeutig benannt sein.</span><span class="sxs-lookup"><span data-stu-id="174f7-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="174f7-127">Im folgenden Beispiel wird ein zweiter **Service**-Ressourcenblock zum Konfigurieren des „DHCP“-Diensts hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="174f7-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="174f7-128">Ab PowerShell 5.0 wurde IntelliSense für DSC hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="174f7-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="174f7-129">Diese neue Funktion ermöglicht es Ihnen, die \<TAB-TASTE\> und \<STRG+LEERTASTE\> zum automatischen Vervollständigen von Schlüsselnamen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="174f7-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![Vervollständigung der Ressource mit der TAB-TASTE](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a><span data-ttu-id="174f7-131">Integrierte Ressourcen</span><span class="sxs-lookup"><span data-stu-id="174f7-131">Built-in resources</span></span>

<span data-ttu-id="174f7-132">Zusätzlich zu den Communityressourcen gibt es integrierte Ressourcen für Windows, Ressourcen für Linux und Ressourcen für knotenübergreifende Abhängigkeiten.</span><span class="sxs-lookup"><span data-stu-id="174f7-132">In addition to community resources, there are built-in resources for Windows, resources for Linux, and resources for cross-node dependency.</span></span> <span data-ttu-id="174f7-133">Mit den oben genannten Schritten können Sie die Syntax dieser Ressourcen und deren Verwendung festlegen.</span><span class="sxs-lookup"><span data-stu-id="174f7-133">You can use the steps above to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="174f7-134">Die Seiten, die diese Ressourcen verarbeiten, wurden unter **Reference** archiviert.</span><span class="sxs-lookup"><span data-stu-id="174f7-134">The pages that serve these resources have been archived under **Reference**.</span></span>

<span data-ttu-id="174f7-135">Integrierte Windows-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="174f7-135">Windows built-in resources</span></span>

* [<span data-ttu-id="174f7-136">Archive-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-136">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
* [<span data-ttu-id="174f7-137">Environment-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-137">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
* [<span data-ttu-id="174f7-138">File-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-138">File Resource</span></span>](../reference/resources/windows/fileResource.md)
* [<span data-ttu-id="174f7-139">Group-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-139">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
* [<span data-ttu-id="174f7-140">GroupSet-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-140">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
* [<span data-ttu-id="174f7-141">Log-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-141">Log Resource</span></span>](../reference/resources/windows/logResource.md)
* [<span data-ttu-id="174f7-142">Package-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-142">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
* [<span data-ttu-id="174f7-143">ProcessSet-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-143">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
* [<span data-ttu-id="174f7-144">Registry-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-144">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
* [<span data-ttu-id="174f7-145">Script-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-145">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
* [<span data-ttu-id="174f7-146">Service-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-146">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
* [<span data-ttu-id="174f7-147">ServiceSet-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-147">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
* [<span data-ttu-id="174f7-148">User-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-148">User Resource</span></span>](../reference/resources/windows/userResource.md)
* [<span data-ttu-id="174f7-149">WindowsFeature-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-149">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
* [<span data-ttu-id="174f7-150">WindowsFeatureSet-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-150">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
* [<span data-ttu-id="174f7-151">WindowsOptionalFeature-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-151">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [<span data-ttu-id="174f7-152">WindowsOptionalFeatureSet-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-152">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [<span data-ttu-id="174f7-153">WindowsPackageCabResource-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-153">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
* [<span data-ttu-id="174f7-154">WindowsProcess-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-154">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

<span data-ttu-id="174f7-155">Ressourcen für [knotenübergreifende Abhängigkeiten](../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="174f7-155">[Cross-Node dependency](../configurations/crossNodeDependencies.md) resources</span></span>

* [<span data-ttu-id="174f7-156">WaitForAll-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-156">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
* [<span data-ttu-id="174f7-157">WaitForSome-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-157">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
* [<span data-ttu-id="174f7-158">WaitForAny-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-158">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

<span data-ttu-id="174f7-159">Paketverwaltungsressourcen</span><span class="sxs-lookup"><span data-stu-id="174f7-159">Package Management resources</span></span>

* [<span data-ttu-id="174f7-160">PackageManagement-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-160">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [<span data-ttu-id="174f7-161">PackageManagementSource-Ressource</span><span class="sxs-lookup"><span data-stu-id="174f7-161">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

<span data-ttu-id="174f7-162">Linux-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="174f7-162">Linux resources</span></span>

* [<span data-ttu-id="174f7-163">Linux-Ressource „Archive“</span><span class="sxs-lookup"><span data-stu-id="174f7-163">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
* [<span data-ttu-id="174f7-164">Linux-Resource „Environment“</span><span class="sxs-lookup"><span data-stu-id="174f7-164">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
* [<span data-ttu-id="174f7-165">Linux-Ressource „FileLine“</span><span class="sxs-lookup"><span data-stu-id="174f7-165">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
* [<span data-ttu-id="174f7-166">Linux-Ressource „File“</span><span class="sxs-lookup"><span data-stu-id="174f7-166">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
* [<span data-ttu-id="174f7-167">Linux-Ressource „Group“</span><span class="sxs-lookup"><span data-stu-id="174f7-167">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
* [<span data-ttu-id="174f7-168">Linux-Ressource „Package“</span><span class="sxs-lookup"><span data-stu-id="174f7-168">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
* [<span data-ttu-id="174f7-169">Linux-Ressource „Script“</span><span class="sxs-lookup"><span data-stu-id="174f7-169">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
* [<span data-ttu-id="174f7-170">Linux-Ressource „Service“</span><span class="sxs-lookup"><span data-stu-id="174f7-170">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
* [<span data-ttu-id="174f7-171">Linux-Ressource „SshAuthorizedKeys“</span><span class="sxs-lookup"><span data-stu-id="174f7-171">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [<span data-ttu-id="174f7-172">Linux-Ressource „User“</span><span class="sxs-lookup"><span data-stu-id="174f7-172">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
