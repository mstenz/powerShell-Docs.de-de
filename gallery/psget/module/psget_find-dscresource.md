# Find-DscResource

Sucht DSC-Ressourcen in Modulen.

## Beschreibung

Das Cmdlet „Find-DscResource“ sucht Ressourcen von [Desired State Configuration (DSC)](https://msdn.microsoft.com/en-us/PowerShell/dsc/overview), die in Modulen enthalten sind, die mit bestimmten Kriterien von registrierten Repositorys übereinstimmen.
Find-DscResource gibt für jedes Modul, das von diesem Cmdlet gefunden wird, ein PSGetDscResourceInfo-Objekt zurück, das Sie an Install-Module übergeben können, um die Module zu installieren, die die von diesem Cmdlet zurückgegebenen Ressourcen enthalten.

DSC ist eine neue Verwaltungsplattform in Windows PowerShell, die es ermöglicht, Konfigurationsdaten für Softwaredienste bereitzustellen und zu verwalten und die Umgebung zu verwalten, in der diese Dienste ausgeführt werden.

DSC-Ressourcen sind die Bausteine einer DSC-Konfiguration. Eine Ressource macht Eigenschaften verfügbar, die konfiguriert werden können (Schema), und enthält die PowerShell-Skriptfunktionen, die der lokale Konfigurations-Manager wie gewünscht ausführt.

Mit einer Ressource kann etwas Allgemeines wie eine Datei oder Spezifisches wie eine IIS-Servereinstellung modelliert werden. Gruppen ähnlicher Ressourcen werden in einem DSC-Modul kombiniert, das alle erforderlichen Dateien in einer Struktur organisiert, die portierbar ist und Metadaten zum Bestimmen des Zwecks der Ressourcen enthält.

- Find-DscResource kann mit Versionsparametern filtern: MinimumVersion, RequiredVersion, AllVersions.
  - Die Parameter schließen sich gegenseitig aus.
  - Diese Versionsparameter sind nur mit dem einzigen Modulnamen ohne Platzhalter erlaubt.
  - Wenn der RequiredVersion-Parameter nicht angegeben wird, gibt Find-DscResource die neueste Version des Moduls zurück, das gleich oder größer als die angegebene minimale Version oder die neueste Version des Moduls ist, wenn keine Mindestversion angegeben wird.
  - Wenn der RequiredVersion-Parameter angegeben ist, gibt Find-DscResource nur die Version des Moduls zurück, die genau mit der angegebenen Version übereinstimmt.
- Find-DscResource kann Modulmetadaten anhand des „-Tag“-Parameters filtern.
- Find-DscResource kann mit dem „-Filter“-Parameter nach einer repositoryspezifischen Suchsprache filtern.
- Find-DscResource kann Module von allen oder einigen registrierten Repositorys filtern.

## Cmdlet-Syntax
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## Cmdlet-Onlinehilfe

[Find-DscResource](http://go.microsoft.com/fwlink/?LinkId=517196)

## Beispiele für Befehle
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```


<!--HONumber=Aug16_HO3-->


