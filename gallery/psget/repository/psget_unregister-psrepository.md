# Unregister-PSRepository

Hebt die Registrierung eines Repositorys auf

## Beschreibung

Das Cmdlet „Unregister-PSRepository“ hebt die Registrierung für ein Repository für den aktuellen Benutzer auf.
- Das Aufheben der Registrierung und das erneute Registrieren des Repositorys „PSGallery“ ist für ein Großunternehmen und getrennte Szenarios zulässig.
- Benutzer können die PSGallery erneut registrieren, indem sie einfach ausführen. `Register-PSRepository -Default`
- Da PSGallery das Standard-Veröffentlichungsrepository in den Cmdlets „Publish-Module“ und „Publish-Script“ ist, wird ein Fehler ausgegeben, wenn PSGallery in der Liste der registrierten Repositorys nicht verfügbar ist.

## Cmdlet-Syntax

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## Cmdlet-Onlinehilfe

[Unregister-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517130)

## Beispiele für Befehle

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### Das Aufheben der Registrierung und das erneute Registrieren des Repositorys „PSGallery“ ist für ein Großunternehmen und getrennte Szenarios zulässig.
```powershell

# Unregister PSGallery repository
Unregister-PSRepository PSGallery

# Publish-Module throws an error when PSGallery is not a registered repository
Publish-Module -Name MyModule
publish-module : Unable to find repository 'PSGallery'. Use Get-PSRepository to see all available repositories. Try again after specifying a valid repository name. You can use 'Register-PSRepository -Default' to register the PSGallery repository.
At line:1 char:1
+ publish-module -name mymodule
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (PSGallery:String) [Publish-Module], ArgumentException
    + FullyQualifiedErrorId : PSGalleryNotFound,Publish-Module

# Re-register PSGallery repository
Register-PSRepository -Default
```

<!--HONumber=Aug16_HO3-->


