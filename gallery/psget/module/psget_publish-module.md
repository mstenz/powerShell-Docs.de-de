---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Publish-Module
ms.openlocfilehash: 53fca3d6756ebf698023152ce5b58b45eb0ef757
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="publish-module"></a>Publish-Module

Veröffentlicht ein angegebenes Modul aus dem lokalen Computer in einem Onlinekatalog

## <a name="description"></a>Beschreibung

Das Cmdlet **Publish-Module** veröffentlicht ein Modul in einem NuGet-basierten Onlinekatalog unter Verwendung eines API-Schlüssels, der als Teil eines Benutzerprofils im Katalog gespeichert ist. Sie können entweder den Namen des Moduls angeben, das veröffentlicht werden soll, oder Sie geben den Pfad zum Ordner an, der das Modul enthält.

Wenn Sie ein Modul durch den Namen angeben, veröffentlicht **Publish-Module** das erste Modul, das unter Ausführung von `Get-Module -ListAvailable <Name>` gefunden werden würde. Wenn Sie eine Mindestversion eines Moduls angeben, das veröffentlicht werden soll, veröffentlicht **Publish-Module** das erste Modul mit einer Version, die höher als die von Ihnen angegebene Mindestversion ist oder gleich.

Die Veröffentlichung eines Moduls erfordert Metadaten, die auf der Seite „Katalog“ des Moduls angezeigt werden. Die erforderlichen Metadaten enthalten den Modulnamen, die Version, die Beschreibung und den Autor. Obwohl die meisten Metadaten aus dem Modulmanifest stammen, müssen manche Metadaten in den **Publish-Module**-Parametern angegeben werden, wie z.B. *Tag, ReleaseNote, IconUri, ProjectUri* und *LicenseUri*, da diese Parameter mit den Feldern in einem NuGet-basierten Katalog übereinstimmen.

Mit dem Parameter RequiredVersion können Sie die genaue Version eines Moduls angeben, die veröffentlicht werden soll.
Der „Path“-Parameter unterstützt auch den Modulbasispfad mit dem Ordner „version“.
Der Parameter „force switch“ im Cmdlet „Publish-Module“ startet „NuGet.exe“ ohne Eingabeaufforderung.

## <a name="cmdlet-syntax"></a>Cmdlet-Syntax
```powershell
Get-Command -Name Publish-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet-Onlinehilfe

[Publish-Module](http://go.microsoft.com/fwlink/?LinkID=398575)

## <a name="example-commands"></a>Beispiele für Befehle

```powershell
ContosoServer module with different versions to be published.
PS C:\\windows\\system32> Get-Module -Name ContosoServer -ListAvailable
Directory: C:\\Program Files\\WindowsPowerShell\\Modules
ModuleType Version Name ExportedCommands
---------- ------- ---- ----------------
Manifest 2.8 ContosoServer Get-ContosoServer
Manifest 2.0 ContosoServer Get-ContosoServer
Manifest 1.5 ContosoServer Get-ContosoServer
Manifest 1.0 ContosoServer Get-ContosoServer
PS C:\\windows\\system32> Publish-Module -Name ContosoServer -RequiredVersion 1.0 -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
PS C:\\windows\\system32> Publish-Module -Name ContosoServer -RequiredVersion 1.5 -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
1.5 ContosoServer LocalRepo ContosoServer module
PS C:\\windows\\system32> Publish-Module -Path "C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0" -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
_------ ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
1.5 ContosoServer LocalRepo ContosoServer module
2.0 ContosoServer LocalRepo ContosoServer module
```

## <a name="publishing-a-module-with-dependencies"></a>Veröffentlichen eines Moduls mit Abhängigkeiten

### <a name="create-a-module-with-dependencies-and-version-range-specified-in-requiredmodules-property-of-its-module-manifest"></a>Erstellen Sie ein Modul mit Abhängigkeiten und dem Versionsbereich, welche in den Eigenschaften „RequiredModules“ des Modulmanifests angegeben sind.

**Hinweis:**
  - \* wird nur in MaximumVersion unterstützt und sollte sich ebenso am Ende der Versionszeichenfolge befinden. 
  - \* wird durch 999999999 im Versionsobjekt ersetzt.

```powershell
PS C:\windows\system32> $requiredModules = @( @{ModuleName = 'RequiredModule1'; ModuleVersion = '0.1'; MaximumVersion = '1.9'; }, @{ModuleName = 'RequiredModule2'; MaximumVersion = '1.*'; })

PS C:\windows\system32> cd C:\MyModules\ModuleWithDependencies

PS C:\MyModules\ModuleWithDependencies> New-ModuleManifest -Path .\ModuleWithDependencies.psd1 -ModuleVersion 1.0 -RequiredModules $requiredModules -Description 'ModuleWithDependencies demo module'
```

### <a name="publish-modulewithdependencies-module-with-dependencies-to-the-repository"></a>Veröffentlichen Sie das Modul „ModuleWithDependencies“ im Repository.

```powershell
PS C:\MyModules\ModuleWithDependencies> Publish-Module -Path C:\MyModules\ModuleWithDependencies -Repository LocalRepo
```

### <a name="find-modulewithdependencies-module-with-its-dependencies-by-specifying--includedependencies"></a>Suchen Sie das Modul „ModuleWithDependencies“ mit seinen Abhängigkeiten, indem Sie „-IncludeDependencies“ angeben.

```powershell
PS C:\MyModules\ModuleWithDependencies> Find-Module -Name ModuleWithDependencies -Repository LocalRepo -IncludeDependencies

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        ModuleWithDependencies              Module     localrepo            ModuleWithDependencies demo module
1.5        RequiredModule1                     Module     localrepo            RequiredModule1 module
1.5        RequiredModule2                     Module     localrepo            RequiredModule2 module
```

### <a name="install-the-modulewithdependencies-module-with-dependencies"></a>Installieren Sie das Modul „ModuleWithDependencies“ mit Abhängigkeiten.
Beachten Sie, dass während der Installation der Abhängigkeit die Versionsbereiche berücksichtigt werden.

```powershell
PS C:\windows\system32> Get-InstalledModule
PS C:\windows\system32>
PS C:\windows\system32> Install-Module -Name ModuleWithDependencies -Repository LocalRepo
PS C:\windows\system32>
PS C:\windows\system32> Get-InstalledModule

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        ModuleWithDependencies              Module     localrepo            ModuleWithDependencies demo module
1.5        RequiredModule1                     Module     localrepo            RequiredModule1 module
1.5        RequiredModule2                     Module     localrepo            RequiredModule2 module
```

### <a name="contents-of-modulewithdependencies2-module-manifest-file"></a>Inhalt der Modulmanifestdatei „ModuleWithDependencies2“

```powershell
@{
# Version number of this module.
ModuleVersion = '2.0'
# ID used to uniquely identify this module
GUID = '0eae34da-99dd-4608-8d28-c614fe7b0841'
# Author of this module
Author = 'manikb'
# Company or vendor of this module
CompanyName = 'Unknown'
# Copyright statement for this module
Copyright = '(c) 2015 manikb. All rights reserved.'
# Description of the functionality provided by this module
Description = 'ModuleWithDependencies2 module'
# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @('RequiredModule1',
@{ModuleName = 'RequiredModule2'; ModuleVersion = '2.0'; },
@{ModuleName = 'RequiredModule3'; RequiredVersion = '2.5'; },
@{ModuleName = 'RequiredModule4'; ModuleVersion = '1.1'; MaximumVersion = '2.0'; },
@{ModuleName = 'RequiredModule5'; MaximumVersion = '1.5'; })
# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @('NestedRequiredModule1',
@{ModuleName = 'NestedRequiredModule2'; ModuleVersion = '2.0'; },
@{ModuleName = 'NestedRequiredModule3'; RequiredVersion = '2.5'; },
@{ModuleName = 'NestedRequiredModule4'; ModuleVersion = '0.7'; MaximumVersion = '2.4'; },
@{ModuleName = 'NestedRequiredModule5'; MaximumVersion = '1.6'; },'ModuleWithDependencies2.psm1')
# Functions to export from this module
FunctionsToExport = '\*'
# Cmdlets to export from this module
CmdletsToExport = '\*'
# Variables to export from this module
VariablesToExport = '\*'
# Aliases to export from this module
AliasesToExport = '\*'
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
      # Tags applied to this module. These help with module discovery in online galleries.
      Tags = 'Tag1', 'Tag2', 'Tag-ModuleWithDependencies2-2.0'
      # A URL to the license for this module.
      LicenseUri = 'http://modulewithdependencies2.com/license'
      # A URL to the main website for this project.
      ProjectUri = 'http://modulewithdependencies2.com/'
      # A URL to an icon representing this module.
      IconUri = 'http://modulewithdependencies2.com/icon'
      # ReleaseNotes of this module
      ReleaseNotes = 'ModuleWithDependencies2 release notes'
    } # End of PSData hashtable
} # End of PrivateData hashtable
}
```


### <a name="external-dependencies"></a>Externe Abhängigkeiten
Einige Modulabhängigkeiten können extern verwaltet werden. In diesem Fall müssen sie dem Eintrag ExternalModuleDependencies im PSData-Abschnitt des Modulmanifests hinzugefügt werden.

Wenn „SnippetPx“ nicht auf dem Repository verfügbar ist, wird der unten dargestellte Fehler ausgegeben.
```powershell
Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
```

