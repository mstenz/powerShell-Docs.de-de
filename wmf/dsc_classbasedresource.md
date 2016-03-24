# Klassenbasierte DSC-Ressourcen

## Definieren von DSC-Ressourcen mit Klassen

Basierend auf Feedback haben wir das Erstellen klassenbasierter DSC-Ressourcen vereinfacht und leichter verständlich gemacht. 
Es folgen die wichtigsten Unterschiede zwischen einer klassenbasierten DSC-Ressource und einem DSC-Ressourcenanbieter für ein Cmdlet:

* Eine MOF-Datei für das Schema ist nicht erforderlich.
* Der Unterordner **DSCResource** im Ordner „module“ ist nicht erforderlich.
* Eine PowerShell-Moduldatei kann mehrere DSC-Ressourcenklassen enthalten.

Es folgt ein Beispiel einer klassenbasierten DSC-Ressource, die die andere klassenbasierte DSC-Ressource in der gleichen Datei erweitert. Diese wird als Modul **MyDSCResource.psm1** gespeichert. 
Beachten Sie, dass Sie in eine klassenbasierte DSC-Ressource bzw. ihre Basisklassen mindestens eine „key“-Eigenschaft und „Get“-, „Set“- oder „Test“-Methode einbeziehen müssen.

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
class BaseFileResource
{
<#
This property is the fully qualified path to the file that is expected to be present or absent.

The [DscProperty(Key)] attribute indicates the property is a key and its value uniquely identifies a resource instance. Defining this attribute also means the property is required and DSC will ensure a value is set before calling the resource.

A DSC resource must define at least one key property.
#>

[DscProperty(Key)]
[string]$Path

<#
This property indicates if the settings should be present or absent on the system.

For present, the resource ensures the file pointed to by $Path exists. For absent, it ensures the file that $Path points to does not exist.

The [DscProperty(Mandatory)] attribute indicates the property is required and DSC will guarantee it is set.

If Mandatory is not specified or if it is defined as Mandatory=$false, the value is not guaranteed to be set when DSC calls the resource. This is appropriate for optional properties.
#>

[DscProperty(Mandatory)]
[Ensure] $Ensure

<#
This property defines the fully qualified path to a file that will be placed on the system if $Ensure = Present and $Path does not exist.
NOTE: This property is required because [DscProperty(Mandatory)] is set.
#>

[DscProperty(Mandatory)]
[string] $SourcePath

<#
This property reports the file's creation timestamp.

[DscProperty(NotConfigurable)] attribute indicates the property is not configurable in a DSC configuration. Properties marked this way are populated by the Get() method to report additional details about the resource when it is present.
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
    if($this.ensure -eq [Ensure]::Present)
    {
        if(-not $fileExists)
        {
            $this.CopyFile()
        }
    }

    else
    {
        if($fileExists)
        {
            Write-Verbose -Message "Deleting the file $($this.Path)"
            Remove-Item -LiteralPath $this.Path -Force
        }
    }
}

<#
This method is equivalent of the Test-TargetResource script function.
It should return True or False, showing whether the resource is in a desired state.
#>

[bool] Test()
{
    $present = $this.TestFilePath($this.Path)

    if($this.Ensure -eq [Ensure]::Present)
    {
        return $present
    }

    else
    {
        return -not $present
    }
}

<#
This method is equal to the Get-TargetResource script function.
The implementation should use the keys to find appropriate resources.
This method returns an instance of this class with the updated key properties.
#>

[BaseFileResource] Get()
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
Helper method to check if the file exists and it is the right file
#>

[bool] TestFilePath([string] $location)
{
    $present = $true
    $item = Get-ChildItem -LiteralPath $location -ea Ignore
    
    if ($item -eq $null)
    {
        $present = $false
    }
    elseif($item.PSProvider.Name -ne "FileSystem")
    {
        throw "Path $($location) is not a file path."
    }
    elseif($item.PSIsContainer)
    {
        throw "Path $($location) is a directory path."
    }

return $present
}

<#
Helper method to copy the file from source to path
#>

[void] CopyFile()
{
    if(-not $this.TestFilePath($this.SourcePath))
    {
        throw "SourcePath $($this.SourcePath) is not found."
    }

    [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
    if (-not $destFileInfo.Directory.Exists)
    {
        Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"
    
        # use CreateDirectory instead of New-Item to avoid code
        # to handle the non-terminating error
        [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
    }

    if(Test-Path -LiteralPath $this.Path -PathType Container)
    {
        throw "Path $($this.Path) is a directory path"
    }

    Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"
    # DSC engine catches and reports any error that occurs
    Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
}
}

<#
This resource inherits from the [BaseFileResource]
It reports additional information in Get method
#>

[DscResource()]
class FileResource : BaseFileResource
{
    <#
    This property reports if it is a readonly file
    #>
    [DscProperty(NotConfigurable)]
    [bool] $IsReadOnly

    <#
    This property reports the file's LastAccessTime timestamp.
    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $LastAccessTime

    <#
    This property reports the file's LastWriteTime timestamp.
    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $LastWriteTime

    <#
    This method overrides the Get method in the base class.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)
        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.IsReadOnly = $file.IsReadOnly
            $this.LastAccessTime = $file.LastAccessTime
            $this.LastWriteTime = $file.LastWriteTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.LastAccessTime = $null
            $this.LastWriteTime = $null
            $this.Ensure = [Ensure]::Absent
        }

    return $this
}

}
```

Nach dem Erstellen des klassenbasierten DSC-Ressourcenanbieters und dessen Speicherung als Modul erstellen Sie ein Modulmanifest für das Modul. Bei diesem Beispiel wird das folgende Modulmanifest als **MyDscResource.psd1** gespeichert.

```powershell
@{
# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to identify this module uniquely
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2015 User01. All rights reserved.'

# Description of the functionality provided by this module
Description = 'DSC resource provider for FileResource.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Required for DSC to detect PS class-based resources.
DscResourcesToExport = @('BaseFileResource','FileResource')
}
```

Stellen Sie den neuen DSC-Ressourcenanbieter bereit, indem Sie unter `$env:SystemDrive\Program Files\WindowsPowerShell\Modules` den Ordner **MyDscResource** erstellen.
Sie müssen nicht den Unterordner „DSCResource“ erstellen.
Kopieren Sie die Modul- und Modulmanifestdatei (**MyDscResource.psm1** und **MyDscResource.psd1**) in den Ordner **MyDscResource**.

Anschließend muss wie bei allen anderen DSC-Ressourcen ein Konfigurationsskript erstellt und ausgeführt werden. 
Es folgt eine Konfiguration, die auf das Modul „MyDSCResource“ verweist. 
Speichern Sie diese als das Skript **MyResource.ps1**.

```powershell
Configuration MyConfig
{
    Import-Dscresource -ModuleName MyDscResource
    BaseFileResource file
    {
        Path = "C:\test\baseFile.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    }

    FileResource file
    {
        Path = "C:\test\File.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    }
}

MyConfig
```

Führen Sie es wie ein übliches DSC-Konfigurationsskript aus. Führen Sie zum Starten der Konfiguration in einer Windows PowerShell-Konsole mit erhöhten Rechten das folgende Cmdlet aus. 
Sie sehen, dass die Ausgabe von „Get-DscConfiguration“ aus „FileResource“ mehr Informationen als „BaseFileResource“ enthält.

```powershell
.\MyResource.ps1
Start-DscConfiguration c:\test\MyConfig –Wait –Verbose
Get-DscConfiguration
```

## Bekannte Probleme

Diese Version weist die folgenden bekannten Probleme bei klassenbasierten DSC-Ressourcen auf:

* „Get-DscConfiguration“ gibt möglicherweise leere Werte (NULL) oder Fehler zurück, wenn von der „Get()“-Funktion einer klassenbasierten DSC-Ressource ein komplexer Typ zurückgegeben wird.
* Zusammengesetzte Ressourcen können nicht als klassenbasierte Ressource geschrieben werden.
<!--HONumber=Mar16_HO2-->
