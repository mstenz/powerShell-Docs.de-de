# Find-RoleCapability

Sucht nach Rollenfunktionen in Modulen.

## Beschreibung
Das Cmdlet Find-RoleCapability sucht PowerShell-Rollenfunktionen in Modulen. Find-RoleCapability sucht Module in registrierten Repositorys. Für jede Rollenfunktion, die von diesem Cmdlet gefunden wird, wird ein PSGetRoleCapabilityInfo-Objekt von diesem zurückgegeben. Sie können ein PSGetRoleCapabilityInfo-Objekt an das Install-Module-Cmdlet übergeben, um das Modul zu installieren, das die Rollenfunktion enthält.
PowerShell-Rollenfunktionen definieren, welche Befehle, Anwendungen usw. für einen Benutzer an einem Just Enough Administration-Endpunkt (JEA) verfügbar sind. Rollenfunktionen werden durch Dateien mit der Erweiterung PSRC definiert.

- Find-RoleCapability kann mit Versionsparametern filtern: MinimumVersion, RequiredVersion, AllVersions.
  - Die Parameter schließen sich gegenseitig aus.
  - Diese Versionsparameter sind nur mit dem einzigen Modulnamen ohne Platzhalter erlaubt.
  - Wenn der RequiredVersion-Parameter nicht angegeben wird, gibt Find-RoleCapability die neueste Version des Moduls zurück, das gleich oder größer als die angegebene minimale Version oder die neueste Version des Moduls ist, wenn keine Mindestversion angegeben wird.
  - Wenn der RequiredVersion-Parameter angegeben ist, gibt Find-RoleCapability nur die Version des Moduls zurück, die genau mit der angegebenen Version übereinstimmt.
- Find-RoleCapability kann Modulmetadaten anhand des „-Tag“-Parameters filtern.
- Find-RoleCapability kann mit dem „-Filter“-Parameter nach einer repositoryspezifischen Suchsprache filtern.
- Find-RoleCapability kann Module von allen oder einigen registrierten Repositorys filtern.

## Cmdlet-Syntax
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## Cmdlet-Onlinehilfe

[Find-RoleCapability](http://go.microsoft.com/fwlink/?LinkId=718029)

## Beispiele für Befehle
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```

<!--HONumber=Aug16_HO3-->


