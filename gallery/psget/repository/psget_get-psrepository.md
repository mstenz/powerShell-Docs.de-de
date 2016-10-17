# Get-PSRepository

Ruft die registrierten Repositorys auf einem Computer ab

## Beschreibung

Das Cmdlet „Get-PSRepository“ ruft PowerShell-Modulrepositorys ab, die für den aktuellen Benutzer auf einem Computer registriert sind.

Get-PSRepository gibt für jedes registrierte Repository ein PSRepository-Objekt zurück, das optional an Unregister-PSRepository zum Aufheben der Registrierung eines registrierten Repositorys übergeben werden kann.

## Cmdlet-Syntax
```powershell
Get-Command -Name Get-PSRepository -Module PowerShellGet -Syntax
```

## Cmdlet-Onlinehilfe

[Get-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517127)

## Beispiele für Befehle

```powershell

# Properties of Get-PSRepository returned object
Get-PSRepository PSGallery | Format-List * -Force

Name                      : PSGallery
SourceLocation            : https://www.powershellgallery.com/api/v2/
Trusted                   : False
Registered                : True
InstallationPolicy        : Untrusted
PackageManagementProvider : NuGet
PublishLocation           : https://www.powershellgallery.com/api/v2/package/
ScriptSourceLocation      : https://www.powershellgallery.com/api/v2/items/psscript/
ScriptPublishLocation     : https://www.powershellgallery.com/api/v2/package/
ProviderOptions           : {}

# Get all registered repositories
Get-PSRepository

# Get a specific registered repository
Get-PSRepository PSGallery

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
PSGallery                 Untrusted            https://www.powershellgallery.com/api/v2/

# Get registered repository with wildcards
Get-PSRepository *Gallery*

```

<!--HONumber=Aug16_HO3-->


