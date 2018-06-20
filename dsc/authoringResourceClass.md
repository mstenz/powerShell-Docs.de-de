---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Schreiben einer benutzerdefinierten DSC-Ressource mit PowerShell-Klassen
ms.openlocfilehash: f2500bfb41302cbeaf3cb9d23b843f26f01c1d5b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189464"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a><span data-ttu-id="65e6b-103">Schreiben einer benutzerdefinierten DSC-Ressource mit PowerShell-Klassen</span><span class="sxs-lookup"><span data-stu-id="65e6b-103">Writing a custom DSC resource with PowerShell classes</span></span>

> <span data-ttu-id="65e6b-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="65e6b-104">Applies To: Windows Windows PowerShell 5.0</span></span>

<span data-ttu-id="65e6b-105">Mit der Einführung der PowerShell-Klassen in Windows PowerShell 5.0 können Sie jetzt eine DSC-Ressourcen durch Erstellen einer Klasse definieren.</span><span class="sxs-lookup"><span data-stu-id="65e6b-105">With the introduction of PowerShell classes in Windows PowerShell 5.0, you can now define a DSC resource by creating a class.</span></span> <span data-ttu-id="65e6b-106">Die Klasse definiert das Schema und die Implementierung der Ressource, daher besteht keine Notwendigkeit, eine separate MOF-Datei zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="65e6b-106">The class defines both the schema and the implementation of the resource, so there is no need to create a separate MOF file.</span></span> <span data-ttu-id="65e6b-107">Die Ordnerstruktur für eine klassenbasierte Ressource ist auch einfacher, da kein **DSCResources**-Ordner erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="65e6b-107">The folder structure for a class-based resource is also simpler, because a **DSCResources** folder is not necessary.</span></span>

<span data-ttu-id="65e6b-108">In einer klassenbasierten DSC-Ressource wird das Schema als Eigenschaften der Klasse definiert, die mit Attributen für den Eigenschaftstyp geändert werden können.</span><span class="sxs-lookup"><span data-stu-id="65e6b-108">In a class-based DSC resource, the schema is defined as properties of the class which can be modified with attributes to specify the property type..</span></span> <span data-ttu-id="65e6b-109">Die Ressource wird mit den Methoden **Get()**, **Set()** und **Test()** implementiert (entspricht den Funktionen **Get-TargetResource**, **Set-TargetResource** und **Test-TargetResource** in einer Skriptressource.</span><span class="sxs-lookup"><span data-stu-id="65e6b-109">The resource is implemented by **Get()**, **Set()**, and **Test()** methods (equivalent to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="65e6b-110">In diesem Thema wird eine einfache Ressource mit dem Namen **FileResource** erstellt, die eine Datei unter einem angegebenen Pfad verwaltet.</span><span class="sxs-lookup"><span data-stu-id="65e6b-110">In this topic, we will create a simple resource named **FileResource** that manages a file in a specified path.</span></span>

<span data-ttu-id="65e6b-111">Weitere Informationen zu DSC-Ressourcen finden Sie unter [Erstellen von benutzerdefinierten Windows PowerShell DSC-Ressourcen](authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="65e6b-111">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md)</span></span>

><span data-ttu-id="65e6b-112">**Hinweis:** Generische Sammlungen werden nicht in auf Klassen basierenden Ressourcen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="65e6b-112">**Note:** Generic collections are not supported in class-based resources.</span></span>

## <a name="folder-structure-for-a-class-resource"></a><span data-ttu-id="65e6b-113">Ordnerstruktur für eine Klassenressource</span><span class="sxs-lookup"><span data-stu-id="65e6b-113">Folder structure for a class resource</span></span>

<span data-ttu-id="65e6b-114">Um eine benutzerdefinierte DSC-Ressource mit einer PowerShell-Klasse zu implementieren, erstellen Sie die folgende Ordnerstruktur.</span><span class="sxs-lookup"><span data-stu-id="65e6b-114">To implement a DSC custom resource with a PowerShell class, create the following folder structure.</span></span> <span data-ttu-id="65e6b-115">Die Klasse wird in **MyDscResource.psm1** und das Modulmanifest in **MyDscResource.psd1** definiert.</span><span class="sxs-lookup"><span data-stu-id="65e6b-115">The class is defined in **MyDscResource.psm1** and the module manifest is defined in **MyDscResource.psd1**.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        |- MyDscResource.psm1
           MyDscResource.psd1
```

## <a name="create-the-class"></a><span data-ttu-id="65e6b-116">Erstellen einer Klasse</span><span class="sxs-lookup"><span data-stu-id="65e6b-116">Create the class</span></span>

<span data-ttu-id="65e6b-117">Sie verwenden das Schlüsselwort „class“ zum Erstellen einer PowerShell-Klasse.</span><span class="sxs-lookup"><span data-stu-id="65e6b-117">You use the class keyword to create a PowerShell class.</span></span> <span data-ttu-id="65e6b-118">Um anzugeben, dass eine Klasse eine DSC-Ressource ist, verwenden Sie das Attribut **DscResource()**.</span><span class="sxs-lookup"><span data-stu-id="65e6b-118">To specify that a class is a DSC resource, use the **DscResource()** attribute.</span></span> <span data-ttu-id="65e6b-119">Der Name der Klasse ist der Name der DSC-Ressource.</span><span class="sxs-lookup"><span data-stu-id="65e6b-119">The name of the class is the name of the DSC resource.</span></span>

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a><span data-ttu-id="65e6b-120">Deklarieren von Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="65e6b-120">Declare properties</span></span>

<span data-ttu-id="65e6b-121">Das DSC-Ressourcenschema wird als Eigenschaften der Klasse definiert.</span><span class="sxs-lookup"><span data-stu-id="65e6b-121">The DSC resource schema is defined as properties of the class.</span></span> <span data-ttu-id="65e6b-122">Es wurden die folgenden drei Eigenschaften deklariert.</span><span class="sxs-lookup"><span data-stu-id="65e6b-122">We declare three properties as follows.</span></span>

```powershell
[DscProperty(Key)]
[string]$Path

[DscProperty(Mandatory)]
[Ensure] $Ensure

[DscProperty(Mandatory)]
[string] $SourcePath

[DscProperty(NotConfigurable)]
[Nullable[datetime]] $CreationTime
```

<span data-ttu-id="65e6b-123">Beachten Sie, dass die Eigenschaften durch Attribute geändert werden.</span><span class="sxs-lookup"><span data-stu-id="65e6b-123">Notice that the properties are modified by attributes.</span></span> <span data-ttu-id="65e6b-124">Die Attribute haben folgende Bedeutungen:</span><span class="sxs-lookup"><span data-stu-id="65e6b-124">The meaning of the attributes is as follows:</span></span>

- <span data-ttu-id="65e6b-125">**DscProperty(Key)**: Die Eigenschaft ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="65e6b-125">**DscProperty(Key)**: The property is required.</span></span> <span data-ttu-id="65e6b-126">Die Eigenschaft ist ein Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="65e6b-126">The property is a key.</span></span> <span data-ttu-id="65e6b-127">Die Werte aller als Schlüssel gekennzeichneten Eigenschaften in Kombination müssen eine Ressourceninstanz in einer Konfiguration eindeutig identifizieren.</span><span class="sxs-lookup"><span data-stu-id="65e6b-127">The values of all properties marked as keys must combine to uniquely identify a resource instance within a configuration.</span></span>
- <span data-ttu-id="65e6b-128">**DscProperty(Mandatory)**: Die Eigenschaft ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="65e6b-128">**DscProperty(Mandatory)**: The property is required.</span></span>
- <span data-ttu-id="65e6b-129">**DscProperty(NotConfigurable)**: Die Eigenschaft ist schreibgeschützt.</span><span class="sxs-lookup"><span data-stu-id="65e6b-129">**DscProperty(NotConfigurable)**: The property is read-only.</span></span> <span data-ttu-id="65e6b-130">Eigenschaften, die mit diesem Attribut gekennzeichnet sind, können nicht von einer Konfiguration festgelegt werden, sondern werden durch die Methode **Get()**, wenn vorhanden, aufgefüllt.</span><span class="sxs-lookup"><span data-stu-id="65e6b-130">Properties marked with this attribute cannot be set by a configuration, but are populated by the **Get()** method when present.</span></span>
- <span data-ttu-id="65e6b-131">**DscProperty()**: Die Eigenschaft ist konfigurierbar, aber nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="65e6b-131">**DscProperty()**: The property is configurable, but it is not required.</span></span>

<span data-ttu-id="65e6b-132">Die Eigenschaften **$Path** und **$SourcePath** sind Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="65e6b-132">The **$Path** and **$SourcePath** properties are both strings.</span></span> <span data-ttu-id="65e6b-133">**$CreationTime** ist eine [DateTime](https://technet.microsoft.com/library/system.datetime.aspx)-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="65e6b-133">The **$CreationTime** is a [DateTime](https://technet.microsoft.com/library/system.datetime.aspx) property.</span></span> <span data-ttu-id="65e6b-134">Die Eigenschaft **$Ensure** ist ein Enumerationstyp, der wie folgt definiert ist:</span><span class="sxs-lookup"><span data-stu-id="65e6b-134">The **$Ensure** property is an enumeration type, defined as follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a><span data-ttu-id="65e6b-135">Implementieren der Methoden</span><span class="sxs-lookup"><span data-stu-id="65e6b-135">Implementing the methods</span></span>

<span data-ttu-id="65e6b-136">Die Methoden **Get()**, **Set()** und **Test()** werden analog zu den Funktionen **Get-TargetResource**, **Set-TargetResource** und **Test-TargetResource** in einer Skriptressource implementiert.</span><span class="sxs-lookup"><span data-stu-id="65e6b-136">The **Get()**, **Set()**, and **Test()** methods are analogous to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="65e6b-137">Dieser Code umfasst auch die Funktion „CopyFile()“, eine Hilfsfunktion, die die Datei von **$SourcePath** nach **$Path** kopiert.</span><span class="sxs-lookup"><span data-stu-id="65e6b-137">This code also includes the CopyFile() function, a helper function that copies the file from **$SourcePath** to **$Path**.</span></span>

```powershell

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)

        if ($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ErrorAction Ignore

        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = New-Object -TypeName System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
```

### <a name="the-complete-file"></a><span data-ttu-id="65e6b-138">Die vollständige Datei</span><span class="sxs-lookup"><span data-stu-id="65e6b-138">The complete file</span></span>
<span data-ttu-id="65e6b-139">Die vollständige Klassendatei folgt.</span><span class="sxs-lookup"><span data-stu-id="65e6b-139">The complete class file follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}

<#
   This resource manages the file in a specific path.
   [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
       This property is the fully qualified path to the file that is
       expected to be present or absent.

       The [DscProperty(Key)] attribute indicates the property is a
       key and its value uniquely identifies a resource instance.
       Defining this attribute also means the property is required
       and DSC will ensure a value is set before calling the resource.

       A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
       This property defines the fully qualified path to a file that will
       be placed on the system if $Ensure = Present and $Path does not
        exist.

       NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
       This property reports the file's create timestamp.

       [DscProperty(NotConfigurable)] attribute indicates the property is
       not configurable in DSC configuration.  Properties marked this way
       are populated by the Get() method to report additional details
       about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                 to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
} # This module defines a class for a DSC "FileResource" provider.
```


## <a name="create-a-manifest"></a><span data-ttu-id="65e6b-140">Erstellen eines Manifests</span><span class="sxs-lookup"><span data-stu-id="65e6b-140">Create a manifest</span></span>

<span data-ttu-id="65e6b-141">Um eine klassenbasierte Ressource für die DSC-Engine verfügbar zu machen, müssen Sie eine **DscResourcesToExport**-Anweisung zur Manifestdatei hinzufügen, die die Engine anweist, die Ressource zu exportieren.</span><span class="sxs-lookup"><span data-stu-id="65e6b-141">To make a class-based resource available to the DSC engine, you must include a **DscResourcesToExport** statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="65e6b-142">Unser Manifest sieht folgendermaßen aus:</span><span class="sxs-lookup"><span data-stu-id="65e6b-142">Our manifest looks like this:</span></span>

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''
}
```

## <a name="test-the-resource"></a><span data-ttu-id="65e6b-143">Testen der Ressource</span><span class="sxs-lookup"><span data-stu-id="65e6b-143">Test the resource</span></span>

<span data-ttu-id="65e6b-144">Nachdem Sie die Klasse und die Manifestdateien, wie zuvor beschrieben, in der Ordnerstruktur gespeichert haben, können Sie eine Konfiguration erstellen, die die neue Ressource verwendet.</span><span class="sxs-lookup"><span data-stu-id="65e6b-144">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="65e6b-145">Informationen dazu, wie Sie eine DSC-Konfiguration ausführen, finden Sie unter [Inkraftsetzung von Konfigurationen](enactingConfigurations.md).</span><span class="sxs-lookup"><span data-stu-id="65e6b-145">For information about how to run a DSC configuration, see [Enacting configurations](enactingConfigurations.md).</span></span> <span data-ttu-id="65e6b-146">Die folgende Konfiguration überprüft, ob die Datei unter `c:\test\test.txt` vorhanden ist, und kopiert sie bei Bedarf aus `c:\test.txt` (Sie sollten `c:\test.txt` vor dem Ausführen der Konfiguration erstellen).</span><span class="sxs-lookup"><span data-stu-id="65e6b-146">The following configuration will check to see whether the file at `c:\test\test.txt` exists, and, if not, copies the file from `c:\test.txt` (you should create `c:\test.txt` before you run the configuration).</span></span>

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    }
}
Test
Start-DscConfiguration -Wait -Force Test
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="65e6b-147">Unterstützung von PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="65e6b-147">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="65e6b-148">**Hinweis:** **PsDscRunAsCredential** wird in PowerShell 5.0 und höheren Versionen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="65e6b-148">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="65e6b-149">Mithilfe der Eigenschaft **PsDscRunAsCredential** kann im Ressourcenblock [DSC configurations](configurations.md) angegeben werden, dass die Ressource mit einem festgelegten Satz an Anmeldeinformationen ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="65e6b-149">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="65e6b-150">Weitere Informationen finden Sie unter [Ausführen von DSC mit Benutzeranmeldeinformationen](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="65e6b-150">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a><span data-ttu-id="65e6b-151">Anfordern oder Untersagen von PsDscRunAsCredential für Ihre Ressource</span><span class="sxs-lookup"><span data-stu-id="65e6b-151">Require or disallow PsDscRunAsCredential for your resource</span></span>

<span data-ttu-id="65e6b-152">Das Attribut **DscResource()** verwendet einen optionalen Parameter **RunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="65e6b-152">The **DscResource()** attribute takes an optional parameter **RunAsCredential**.</span></span>
<span data-ttu-id="65e6b-153">Dieser Parameter kann einen von drei Werten annehmen:</span><span class="sxs-lookup"><span data-stu-id="65e6b-153">This parameter takes one of three values:</span></span>

- <span data-ttu-id="65e6b-154">`Optional` **PsDscRunAsCredential** ist optional für Ressourcen, die diese Ressource aufrufen.</span><span class="sxs-lookup"><span data-stu-id="65e6b-154">`Optional` **PsDscRunAsCredential** is optional for configurations that call this resource.</span></span> <span data-ttu-id="65e6b-155">Dies ist der Standardwert.</span><span class="sxs-lookup"><span data-stu-id="65e6b-155">This is the default value.</span></span>
- <span data-ttu-id="65e6b-156">`Mandatory` **PsDscRunAsCredential** muss für alle Konfigurationen verwendet werden, die diese Ressource aufrufen.</span><span class="sxs-lookup"><span data-stu-id="65e6b-156">`Mandatory` **PsDscRunAsCredential** must be used for any configuration that calls this resource.</span></span>
- <span data-ttu-id="65e6b-157">`NotSupported`Konfigurationen, die diese Ressource aufrufen, können **PsDscRunAsCredential** nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="65e6b-157">`NotSupported` Configurations that call this resource cannot use **PsDscRunAsCredential**.</span></span>
- <span data-ttu-id="65e6b-158">`Default` Identisch mit `Optional`.</span><span class="sxs-lookup"><span data-stu-id="65e6b-158">`Default` Same as `Optional`.</span></span>

<span data-ttu-id="65e6b-159">Verwenden Sie beispielsweise das folgende Attribut, um anzugeben, dass Ihre benutzerdefinierte Ressource die Verwendung von **PsDscRunAsCredential** nicht unterstützt:</span><span class="sxs-lookup"><span data-stu-id="65e6b-159">For example, use the following attribute to specify that your custom resource does not support using **PsDscRunAsCredential**:</span></span>

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="access-the-user-context"></a><span data-ttu-id="65e6b-160">Zugriff auf den Benutzerkontext</span><span class="sxs-lookup"><span data-stu-id="65e6b-160">Access the user context</span></span>

<span data-ttu-id="65e6b-161">Um aus einer benutzerdefinierten Ressource auf den Benutzerkontext zuzugreifen, können Sie die automatische Variable `$global:PsDscContext` verwenden.</span><span class="sxs-lookup"><span data-stu-id="65e6b-161">To access the user context from within a custom resource, you can use the automatic variable `$global:PsDscContext`.</span></span>

<span data-ttu-id="65e6b-162">Beispielsweise wird mit dem folgenden Code der Benutzerkontext für die Ressourcenausführung in den ausführlichen Ausgabestream geschrieben:</span><span class="sxs-lookup"><span data-stu-id="65e6b-162">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="65e6b-163">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="65e6b-163">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="65e6b-164">Konzepte</span><span class="sxs-lookup"><span data-stu-id="65e6b-164">Concepts</span></span>
[<span data-ttu-id="65e6b-165">Erstellen von benutzerdefinierten Windows PowerShell DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="65e6b-165">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)