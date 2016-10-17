# Starten des NuGet-Anbieters sowie der Datei „NuGet.exe“ für Veröffentlichungsvorgänge mit einer einzigen Aufforderungsmeldung und ausschließliches Starten des NuGet-Anbieters für Vorgänge ohne Veröffentlichung

„NuGet.exe“ wird im aktuellsten NuGet-Anbieter entfernt. PowerShellGet benötigt für die Veröffentlichung eines Moduls/Skripts „NuGet.exe“, um eine NUPKG-Datei zu erstellen und mithilfe von Push an das Repository zu übertragen. Der NuGet-Anbieter wird für Vorgänge ohne Veröffentlichung wie „Suchen“, „Installieren“, „Aktualisieren“ und „Speichern“ benötigt.
Es wurde die Logik zum Starten des NuGet-Anbieters sowie der Datei „NuGet.exe“ für Veröffentlichungsvorgänge mit einer einzigen Aufforderungsmeldung und zum ausschließlichen Starten des NuGet-Anbieters für Vorgänge ohne Veröffentlichung hinzugefügt.

## Wenn der NuGet-Anbieter nicht verfügbar ist

```powershell                                
PS C:\windows\system32> find-module -Repository dtlgalleryint -verbose -name contoso

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
find-module : NuGet provider is required to interact with NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ find-module -Repository dtlgalleryint -verbose -name contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module

PS C:\windows\system32> find-module -Repository dtlgalleryint -verbose -name contoso

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     dtlgalleryint        Contoso module
```

## Wenn der NuGet-Anbieter während des Veröffentlichungsvorgangs verfügbar ist und „NuGet.exe“ nicht verfügbar ist

```powershell
PS C:\windows\system32> Publish-Module -Name Contoso -Repository LocalRepo -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository LocalRepo -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module

PS C:\windows\system32> Publish-Module -Name Contoso -Repository LocalRepo -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'C:\LocalGallery'. Please allow few minutes for 'Contoso' to show up in the search results.
```
                   
## Wenn sowohl der NuGet-Anbieter als auch „NuGet.exe“ während des Veröffentlichungsvorgangs nicht verfügbar sind

```powershell
PS C:\windows\system32> Publish-Module -Name Contoso -Repository LocalRepo -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed and NuGet.exe is available under 
one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository LocalRepo -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetBinaries,Publish-Module

PS C:\windows\system32> Publish-Module -Name Contoso -Repository LocalRepo -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'C:\LocalGallery'. Please allow few minutes for 'Contoso' to show up in the search results.
```

<!--HONumber=Aug16_HO3-->


