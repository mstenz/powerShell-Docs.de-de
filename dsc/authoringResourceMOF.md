---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Schreiben einer benutzerdefinierten DSC-Ressource mit MOF
ms.openlocfilehash: 50b5f2eddbac4571f5351b32648d45c54ded167e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a><span data-ttu-id="97ea6-103">Schreiben einer benutzerdefinierten DSC-Ressource mit MOF</span><span class="sxs-lookup"><span data-stu-id="97ea6-103">Writing a custom DSC resource with MOF</span></span>

> <span data-ttu-id="97ea6-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="97ea6-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="97ea6-105">In diesem Thema wird das Schema für eine benutzerdefinierte Windows PowerShell DSC-Ressource in einer MOF-Datei definiert und die Ressource in einer Windows PowerShell-Skriptdatei implementiert.</span><span class="sxs-lookup"><span data-stu-id="97ea6-105">In this topic, we will define the schema for a Windows PowerShell Desired State Configuration (DSC) custom resource in a MOF file, and implement the resource in a Windows PowerShell script file.</span></span> <span data-ttu-id="97ea6-106">Diese benutzerdefinierte Ressource dient zum Erstellen und Verwalten einer Website.</span><span class="sxs-lookup"><span data-stu-id="97ea6-106">This custom resource is for creating and maintaining a web site.</span></span>

## <a name="creating-the-mof-schema"></a><span data-ttu-id="97ea6-107">Schreiben des MOF-Schemas</span><span class="sxs-lookup"><span data-stu-id="97ea6-107">Creating the MOF schema</span></span>

<span data-ttu-id="97ea6-108">Das Schema definiert die Eigenschaften der Ressource, die durch ein DSC-Konfigurationsskript konfiguriert werden können.</span><span class="sxs-lookup"><span data-stu-id="97ea6-108">The schema defines the properties of your resource that can be configured by a DSC configuration script.</span></span>

### <a name="folder-structure-for-a-mof-resource"></a><span data-ttu-id="97ea6-109">Ordnerstruktur für eine MOF-Ressource</span><span class="sxs-lookup"><span data-stu-id="97ea6-109">Folder structure for a MOF resource</span></span>

<span data-ttu-id="97ea6-110">Um eine benutzerdefinierte DSC-Ressource mit einem MOF-Schema zu implementieren, erstellen Sie die folgende Ordnerstruktur.</span><span class="sxs-lookup"><span data-stu-id="97ea6-110">To implement a DSC custom resource with a MOF schema, create the following folder structure.</span></span> <span data-ttu-id="97ea6-111">Das MOF-Schema ist in der Datei „Demo_IISWebsite.schema.mof“ definiert und das Ressourcenskript in „Demo_IISWebsite.psm1“.</span><span class="sxs-lookup"><span data-stu-id="97ea6-111">The MOF schema is defined in the file Demo_IISWebsite.schema.mof, and the resource script is defined in Demo_IISWebsite.psm1.</span></span> <span data-ttu-id="97ea6-112">Optional können Sie eine Modulmanifestdatei (psd1) erstellen.</span><span class="sxs-lookup"><span data-stu-id="97ea6-112">Optionally, you can create a module manifest (psd1) file.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

<span data-ttu-id="97ea6-113">Beachten Sie, dass im Ordner der obersten Ebene ein Ordner mit dem Namen „DSCResources“ erstellt werden muss, und dass die Ordnernamen für die einzelnen Ressourcen den Namen der jeweiligen Ressourcen entsprechen müssen.</span><span class="sxs-lookup"><span data-stu-id="97ea6-113">Note that it is necessary to create a folder named DSCResources under the top-level folder, and that the folder for each resource must have the same name as the resource.</span></span>

### <a name="the-contents-of-the-mof-file"></a><span data-ttu-id="97ea6-114">Inhalt der MOF-Datei</span><span class="sxs-lookup"><span data-stu-id="97ea6-114">The contents of the MOF file</span></span>

<span data-ttu-id="97ea6-115">Die folgende MOF-Beispieldatei kann für eine benutzerdefinierte Websiteressource verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="97ea6-115">Following is an example MOF file that can be used for a custom website resource.</span></span> <span data-ttu-id="97ea6-116">Um dieses Beispiel anzuwenden, speichern Sie das Schema in einer Datei, und rufen Sie die Datei *Demo_IISWebsite.schema.mof* auf.</span><span class="sxs-lookup"><span data-stu-id="97ea6-116">To follow this example, save this schema to a file, and call the file *Demo_IISWebsite.schema.mof*.</span></span>

```
[ClassVersion("1.0.0"), FriendlyName("Website")]
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

<span data-ttu-id="97ea6-117">Beachten Sie Folgendes im Zusammenhang mit dem vorherigen Code:</span><span class="sxs-lookup"><span data-stu-id="97ea6-117">Note the following about the previous code:</span></span>

* <span data-ttu-id="97ea6-118">`FriendlyName` definiert den Namen, den Sie verwenden können, um auf diese benutzerdefinierte Ressource in DSC-Konfigurationsskripts zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="97ea6-118">`FriendlyName` defines the name you can use to refer to this custom resource in DSC configuration scripts.</span></span> <span data-ttu-id="97ea6-119">In diesem Beispiel entspricht `Website` dem Anzeigenamen `Archive` für die integrierten Ressource „Archive“.</span><span class="sxs-lookup"><span data-stu-id="97ea6-119">In this example, `Website` is equivalent to the friendly name `Archive` for the built-in Archive resource.</span></span>
* <span data-ttu-id="97ea6-120">Die Klasse, die Sie für die benutzerdefinierte Ressource definieren, muss von `OMI_BaseResource` abgeleitet sein.</span><span class="sxs-lookup"><span data-stu-id="97ea6-120">The class you define for your custom resource must derive from `OMI_BaseResource`.</span></span>
* <span data-ttu-id="97ea6-121">Der Typqualifizierer `[Key]` für eine Eigenschaft gibt an, dass die Ressourceninstanz durch diese Eigenschaft eindeutig identifiziert wird.</span><span class="sxs-lookup"><span data-stu-id="97ea6-121">The type qualifier, `[Key]`, on a property indicates that this property will uniquely identify the resource instance.</span></span> <span data-ttu-id="97ea6-122">Mindestens eine `[Key]`-Eigenschaft ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="97ea6-122">At least one `[Key]` property is required.</span></span>
* <span data-ttu-id="97ea6-123">Der Qualifizierer `[Required]` gibt an, dass die Eigenschaft erforderlich ist (der Wert muss in jedem Konfigurationsskript, in dem die Ressource verwendet wird, angegeben werden).</span><span class="sxs-lookup"><span data-stu-id="97ea6-123">The `[Required]` qualifier indicates that the property is required (a value must be specified in any configuration script that uses this resource).</span></span>
* <span data-ttu-id="97ea6-124">Der Qualifizierer `[write]` gibt an, dass diese Eigenschaft bei Verwendung der benutzerdefinierten Ressource in einem Konfigurationsskript optional ist.</span><span class="sxs-lookup"><span data-stu-id="97ea6-124">The `[write]` qualifier indicates that this property is optional when using the custom resource in a configuration script.</span></span> <span data-ttu-id="97ea6-125">Der Qualifizierer `[read]` gibt an, dass eine Eigenschaft nicht durch eine Konfiguration festgelegt werden kann und nur zu Berichtszwecken dient.</span><span class="sxs-lookup"><span data-stu-id="97ea6-125">The `[read]` qualifier indicates that a property cannot be set by a configuration, and is for reporting purposes only.</span></span>
* <span data-ttu-id="97ea6-126">`Values` schränkt die Werte, die der Eigenschaft zugewiesen werden können, auf die in `ValueMap` definierte Werteliste ein.</span><span class="sxs-lookup"><span data-stu-id="97ea6-126">`Values` restricts the values that can be assigned to the property to the list of values defined in `ValueMap`.</span></span> <span data-ttu-id="97ea6-127">Weitere Informationen finden Sie unter [Die Qualifizierer „ValueMap“ und „Value“](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).</span><span class="sxs-lookup"><span data-stu-id="97ea6-127">For more information, see [ValueMap and Value Qualifiers](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).</span></span>
* <span data-ttu-id="97ea6-128">Eine empfohlene Methode, einen konsistenten Stil mit integrierten DSC-Ressourcen beizubehalten, ist das Hinzufügen einer Eigenschaft namens `Ensure`, die die Werte `Present` und `Absent` aufweist, zu Ihrer Ressource.</span><span class="sxs-lookup"><span data-stu-id="97ea6-128">Including a property called `Ensure` with values `Present` and `Absent` in your resource is recommended as a way to maintain a consistent style with built-in DSC resources.</span></span>
* <span data-ttu-id="97ea6-129">Benennen Sie die Schemadatei für die benutzerdefinierte Ressource wie folgt: `classname.schema.mof`, wobei `classname` der Bezeichner ist, der dem Schlüsselwort `class` in der Schemadefinition folgt.</span><span class="sxs-lookup"><span data-stu-id="97ea6-129">Name the schema file for your custom resource as follows: `classname.schema.mof`, where `classname` is the identifier that follows the `class` keyword in your schema definition.</span></span>

### <a name="writing-the-resource-script"></a><span data-ttu-id="97ea6-130">Schreiben des Ressourcenskripts</span><span class="sxs-lookup"><span data-stu-id="97ea6-130">Writing the resource script</span></span>

<span data-ttu-id="97ea6-131">Das Ressourcenskript implementiert die Logik der Ressource.</span><span class="sxs-lookup"><span data-stu-id="97ea6-131">The resource script implements the logic of the resource.</span></span> <span data-ttu-id="97ea6-132">In diesem Modul fügen Sie die drei Funktionen **Get-TargetResource**, **Set-TargetResource**, und **Test-TargetResource** hinzu.</span><span class="sxs-lookup"><span data-stu-id="97ea6-132">In this module, you must include three functions called **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource**.</span></span> <span data-ttu-id="97ea6-133">Alle drei Funktionen verwenden einen Parametersatz, der identisch mit dem Satz von Eigenschaften ist, die im MOF-Schema definiert wurden, das Sie für die Ressource erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="97ea6-133">All three functions must take a parameter set that is identical to the set of properties defined in the MOF schema that you created for your resource.</span></span> <span data-ttu-id="97ea6-134">In diesem Dokument wird dieser Eigenschaftensatz als die „Ressourceneigenschaften“ bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="97ea6-134">In this document, this set of properties is referred to as the “resource properties.”</span></span> <span data-ttu-id="97ea6-135">Speichern Sie die drei Funktionen in einer Datei namens „<ResourceName>.psm1“.</span><span class="sxs-lookup"><span data-stu-id="97ea6-135">Store these three functions in a file called <ResourceName>.psm1.</span></span> <span data-ttu-id="97ea6-136">Im folgenden Beispiel werden die Funktionen in einer Datei namens „Demo_IISWebsite.psm1“ gespeichert.</span><span class="sxs-lookup"><span data-stu-id="97ea6-136">In the following example, the functions are stored in a file called Demo_IISWebsite.psm1.</span></span>

> <span data-ttu-id="97ea6-137">**Hinweis**: Wenn Sie das gleiche Konfigurationsskript mehrfach für Ihre Ressource ausführen, sollten keine Fehler ausgegeben werden, und die Ressource sollte sich im gleichen Zustand wie nach der einmaligen Ausführung des Skripts befinden.</span><span class="sxs-lookup"><span data-stu-id="97ea6-137">**Note**: When you run the same configuration script on your resource more than once, you should receive no errors and the resource should remain in the same state as running the script once.</span></span> <span data-ttu-id="97ea6-138">Stellen Sie dazu sicher, dass Ihre Funktionen **Get-TargetResource** und **Test-TargetResource** die Ressource unverändert verlassen, und dass das Ergebnis der Funktion **Set-TargetResource** mit denselben Parameterwerten immer identisch ist, egal, ob Sie die Funktion einmal oder mehrfach aufrufen.</span><span class="sxs-lookup"><span data-stu-id="97ea6-138">To accomplish this, ensure that your **Get-TargetResource** and **Test-TargetResource** functions leave the resource unchanged, and that invoking the **Set-TargetResource** function more than once in a sequence with the same parameter values is always equivalent to invoking it once.</span></span>

<span data-ttu-id="97ea6-139">Verwenden Sie in der Implementierung der Funktion **Get-TargetResource** die Schlüsselressourcen-Eigenschaftswerte, die als Parameter bereitgestellt werden, um den Status der angegebenen Ressourceninstanz zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="97ea6-139">In the **Get-TargetResource** function implementation, use the key resource property values that are provided as parameters to check the status of the specified resource instance.</span></span> <span data-ttu-id="97ea6-140">Diese Funktion muss eine Hashtabelle zurückgeben, in der alle Ressourceneigenschaften als Schlüssel und die tatsächlichen Werte dieser Eigenschaften als die entsprechende Werte aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="97ea6-140">This function must return a hash table that lists all the resource properties as keys and the actual values of these properties as the corresponding values.</span></span> <span data-ttu-id="97ea6-141">Der folgende Code gibt ein Beispiel.</span><span class="sxs-lookup"><span data-stu-id="97ea6-141">The following code provides an example.</span></span>

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance specified in the parameters for the target machine
function Get-TargetResource
{
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <# Insert logic that uses the mandatory parameter values to get the website and assign it to a variable called $Website #>
        <# Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
                                      Name = $Website.Name;
                                        Ensure = $ensureResult;
                                        PhysicalPath = $Website.physicalPath;
                                        State = $Website.state;
                                        ID = $Website.id;
                                        ApplicationPool = $Website.applicationPool;
                                        Protocol = $Website.bindings.Collection.protocol;
                                        Binding = $Website.bindings.Collection.bindingInformation;
                                    }

        $getTargetResourceResult;
}
```

<span data-ttu-id="97ea6-142">Abhängig von den Werten, die für die Ressourceneigenschaften im Konfigurationsskript angegeben sind, muss die Funktion **Set-TargetResource** eine der folgenden Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="97ea6-142">Depending on the values that are specified for the resource properties in the configuration script, the **Set-TargetResource** must do one of the following:</span></span>

* <span data-ttu-id="97ea6-143">Erstellen einer neuen Website</span><span class="sxs-lookup"><span data-stu-id="97ea6-143">Create a new website</span></span>
* <span data-ttu-id="97ea6-144">Aktualisieren einer vorhandenen Website</span><span class="sxs-lookup"><span data-stu-id="97ea6-144">Update an existing website</span></span>
* <span data-ttu-id="97ea6-145">Löschen einer vorhandenen Website</span><span class="sxs-lookup"><span data-stu-id="97ea6-145">Delete an existing website</span></span>

<span data-ttu-id="97ea6-146">Das folgende Beispiel veranschaulicht dies.</span><span class="sxs-lookup"><span data-stu-id="97ea6-146">The following example illustrates this.</span></span>

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine.
function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

    <# If Ensure is set to "Present" and the website specified in the mandatory input parameters does not exist, then create it using the specified parameter values #>
    <# Else, if Ensure is set to "Present" and the website does exist, then update its properties to match the values provided in the non-mandatory parameter values #>
    <# Else, if Ensure is set to "Absent" and the website does not exist, then do nothing #>
    <# Else, if Ensure is set to "Absent" and the website does exist, then delete the website #>
}
```

<span data-ttu-id="97ea6-147">Schließlich muss die Funktion **Test-TargetResource** den gleichen Parametersatz verwenden wie **Get-TargetResource** und **Set-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="97ea6-147">Finally, the **Test-TargetResource** function must take the same parameter set as **Get-TargetResource** and **Set-TargetResource**.</span></span> <span data-ttu-id="97ea6-148">Überprüfen Sie in der Implementierung von **Test-TargetResource** den Status der in den Schlüsselparametern angegebenen Ressourceninstanz.</span><span class="sxs-lookup"><span data-stu-id="97ea6-148">In your implementation of **Test-TargetResource**, check the status of the resource instance that is specified in the key parameters.</span></span> <span data-ttu-id="97ea6-149">Wenn der aktuelle Status der Ressourceninstanz nicht mit den im Parametersatz angegebenen Werten übereinstimmt, wird **$false** zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="97ea6-149">If the actual status of the resource instance does not match the values specified in the parameter set, return **$false**.</span></span> <span data-ttu-id="97ea6-150">Andernfalls wird **$true** zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="97ea6-150">Otherwise, return **$true**.</span></span>

<span data-ttu-id="97ea6-151">Der folgende Code implementiert die Funktion **Test-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="97ea6-151">The following code implements the **Test-TargetResource** function.</span></span>

```powershell
function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[parameter(Mandatory = $true)]
[System.String]
$Name,

[parameter(Mandatory = $true)]
[System.String]
$PhysicalPath,

[ValidateSet("Started","Stopped")]
[System.String]
$State,

[System.String[]]
$Protocol,

[System.String[]]
$BindingData,

[System.String]
$ApplicationPool
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


#Include logic to
$result = [System.Boolean]
#Add logic to test whether the website is present and its status mathes the supplied parameter values. If it does, return true. If it does not, return false.
$result
}
```

<span data-ttu-id="97ea6-152">**Hinweis**: Zum einfacheren Debuggen verwenden Sie in Ihrer Implementierung der vorherigen drei Funktionen das Cmdlet **Write-Verbose**.</span><span class="sxs-lookup"><span data-stu-id="97ea6-152">**Note**: For easier debugging, use the **Write-Verbose** cmdlet in your implementation of the previous three functions.</span></span>
><span data-ttu-id="97ea6-153">Dieses Cmdlet schreibt Text in den Stream für ausführliche Meldungen.</span><span class="sxs-lookup"><span data-stu-id="97ea6-153">This cmdlet writes text to the verbose message stream.</span></span>
><span data-ttu-id="97ea6-154">Standardmäßig wird der Stream für ausführliche Meldungen nicht angezeigt. Sie können ihn jedoch anzeigen, indem Sie den Wert der Variablen **$VerbosePreference** ändern den Parameter **Verbose** in „DSC cmdlets = new“ verwenden.</span><span class="sxs-lookup"><span data-stu-id="97ea6-154">By default, the verbose message stream is not displayed, but you can display it by changing the value of the **$VerbosePreference** variable or by using the **Verbose** parameter in the DSC cmdlets = new.</span></span>

### <a name="creating-the-module-manifest"></a><span data-ttu-id="97ea6-155">Erstellen das Modulmanifest</span><span class="sxs-lookup"><span data-stu-id="97ea6-155">Creating the module manifest</span></span>

<span data-ttu-id="97ea6-156">Verwenden Sie abschließend das Cmdlet **New-ModuleManifest**, um eine „<ResourceName>psd1“-Datei für das benutzerdefinierte Ressourcenmodul zu definieren.</span><span class="sxs-lookup"><span data-stu-id="97ea6-156">Finally, use the **New-ModuleManifest** cmdlet to define a <ResourceName>.psd1 file for your custom resource module.</span></span> <span data-ttu-id="97ea6-157">Wenn Sie dieses Cmdlet aufrufen, verweisen Sie auf die im vorherigen Abschnitt beschriebene Skriptmoduldatei (.psm1).</span><span class="sxs-lookup"><span data-stu-id="97ea6-157">When you invoke this cmdlet, reference the script module (.psm1) file described in the previous section.</span></span> <span data-ttu-id="97ea6-158">Fügen Sie **Get-TargetResource**, **Set-TargetResource** und **Test-TargetResource** zur Liste der zu exportierenden Funktionen hinzu.</span><span class="sxs-lookup"><span data-stu-id="97ea6-158">Include **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** in the list of functions to export.</span></span> <span data-ttu-id="97ea6-159">Im Folgenden finden Sie eine Beispielmanifestdatei.</span><span class="sxs-lookup"><span data-stu-id="97ea6-159">Following is an example manifest file.</span></span>

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="97ea6-160">Unterstützung von PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="97ea6-160">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="97ea6-161">**Hinweis:** **PsDscRunAsCredential** wird in PowerShell 5.0 und höheren Versionen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="97ea6-161">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="97ea6-162">Mithilfe der Eigenschaft **PsDscRunAsCredential** kann im Ressourcenblock [DSC configurations](configurations.md) angegeben werden, dass die Ressource mit einem festgelegten Satz an Anmeldeinformationen ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="97ea6-162">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="97ea6-163">Weitere Informationen finden Sie unter [Ausführen von DSC mit Benutzeranmeldeinformationen](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="97ea6-163">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

<span data-ttu-id="97ea6-164">Um aus einer benutzerdefinierten Ressource auf den Benutzerkontext zuzugreifen, können Sie die automatische Variable `$PsDscContext` verwenden.</span><span class="sxs-lookup"><span data-stu-id="97ea6-164">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="97ea6-165">Beispielsweise wird mit dem folgenden Code der Benutzerkontext für die Ressourcenausführung in den ausführlichen Ausgabestream geschrieben:</span><span class="sxs-lookup"><span data-stu-id="97ea6-165">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```