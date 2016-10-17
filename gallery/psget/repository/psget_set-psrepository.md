# Set-PSRepository

Set-PSRepository legt Werte für ein registriertes Repository fest.

## Beschreibung

Das Cmdlet „Set-PSRepository“ legt Werte für ein registriertes Modulrepository fest.

## Cmdlet-Syntax

```powershell
Get-Command -Name Set-PSRepository -Module PowerShellGet -Syntax
```
## Cmdlet-Onlinehilfe

[Set-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517128)

## Beispiele für Befehle

```powershell
PS C:\> Register-PSRepository -Name myRepository -SourceLocation "https://www.myget.org/F/powershellgetdemo/api/v2" -InstallationPolicy Trusted
PS C:\> Get-PSRepository
Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
myRepository              Trusted              https://www.myget.org/F/powershellgetdemo/api/v2

# Set installation Policy for a repository
PS C:\> Set-PSRepository -Name myRepository -InstallationPolicy Untrusted
PS C:\> Get-PSRepository

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
myRepository              Untrusted            https://www.myget.org/F/powershellgetdemo/api/v2
```


### Das Cmdlet „Set-PSRepository“ mit Unterstützung der Skriptfreigabe

Verwenden Sie die „Set-PSRepository“-Cmdlets zum Hinzufügen von **ScriptSourceLocation** und **ScriptPublishLocation** zu „PSRepository“.
```powershell
# Add script sharing locations to an existing PSRepository using Set-PSRepository object.
Set-PSRepository -Name MyGallery `
                 -ScriptSourceLocation https://MyGallery.com/api/v2/items/psscript/ `
                 -ScriptPublishLocation https://MyGallery.com/api/v2/package/

Get-PSRepository -Name GalleryINT | Format-List * -Force

Name : GalleryINT
SourceLocation : https://MyGallery.com/api/v2/
Trusted : True
Registered : True
InstallationPolicy : Trusted
PackageManagementProvider : NuGet
PublishLocation : https://MyGallery.com/api/v2/package/
ScriptSourceLocation : https://MyGallery.com/api/v2/items/psscript/
ScriptPublishLocation : https://MyGallery.com/api/v2/package/
ProviderOptions : {}

```


<!--HONumber=Aug16_HO3-->


