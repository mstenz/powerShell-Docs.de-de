# Save-Module

Speichert ein Modul lokal, ohne es zu installieren

## Beschreibung

Das Cmdlet „Save-Module“ speichert ein Modul aus dem angegebenen Repository zur Prüfung lokal. Das Modul wird nicht installiert.

## Cmdlet-Syntax
```powershell
Get-Command -Name Save-Module -Module PowerShellGet -Syntax
```

## Cmdlet-Onlinehilfe

[Save-Module](http://go.microsoft.com/fwlink/?LinkId=531351)

## Beispiele für Befehle

```powershell
Save-Module -Repository MSPSGallery -Name ModuleWithDependencies2 -Path C:\MySavedModuleLocation
dir C:\MySavedModuleLocation

Directory: C:\MySavedModuleLocation

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 4/21/2015 5:40 PM ModuleWithDependencies2
d----- 4/21/2015 5:40 PM NestedRequiredModule1
d----- 4/21/2015 5:40 PM NestedRequiredModule2
d----- 4/21/2015 5:40 PM NestedRequiredModule3
d----- 4/21/2015 5:40 PM RequiredModule1
d----- 4/21/2015 5:40 PM RequiredModule2
d----- 4/21/2015 5:40 PM RequiredModule3


# Find a command and save its module
# This command finds the specified command, and then passes it to Save-Module to save it to the C:\temp folder.
Find-Command -Name "Get-NestedRequiredModule4" -Repository "INT" | Save-Module -Path "C:\temp\" -Verbose


# Save the role capability modules by piping the Find-RoleCapability output to Save-Module cmdlet.
Find-RoleCapability -Name Maintenance,MyJeaRole | Save-Module -Path C:\MyModulesPath

```


<!--HONumber=Aug16_HO3-->


