---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Bootstrapping von NuGet
ms.openlocfilehash: f707e23737361ee7f82a16150402c9e719ee0ae1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221798"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a>Bootstrapping des NuGet-Anbieters und von „NuGet.exe“

„NuGet.exe“ ist im neuesten NuGet-Anbieter nicht enthalten.
Für die Veröffentlichung eines Moduls oder Skripts benötigt PowerShell die binäre ausführbare Datei „NuGet.exe“.
Für alle weiteren Vorgänge, darunter *find*, *install*, *save* und *uninstall*, ist nur der NuGet-Anbieter erforderlich.
PowerShell umfasst Logik für ein kombiniertes Bootstrappings des NuGet-Anbieters und der Datei „NuGet.exe“ oder ein ausschließliches Bootstrapping des NuGet-Anbieters.
In beiden Fällen sollte nur eine einzige Aufforderungsmeldung erfolgen.
Wenn der Computer nicht mit dem Internet verbunden ist, muss der Benutzer oder Administrator eine vertrauenswürdige Instanz des NuGet-Anbieters und/oder der Datei „NuGet.exe“ auf den getrennten Computer kopieren.

>**Hinweis**: Ab Version 6 ist der NuGet-Anbieter in der Installation von PowerShell enthalten. [http://github.com/powershell/powershell](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a>Fehlerbehebung, wenn der NuGet-Anbieter auf einem Computer ohne Internetverbindung nicht installiert ist

```powershell
PS> Find-Module -Repository PSGallery -Verbose -Name Contoso

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ Find-Module -Repository PSGallery -Verbose -Name Contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module

PS> Find-Module -Repository PSGallery -Verbose -Name Contoso

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Fehlerbehebung, wenn der NuGet-Anbieter zur Verfügung steht, aber „NuGet.exe“ während eines Veröffentlichungsvorgangs auf einem Computer ohne Internetverbindung nicht verfügbar ist

```powershell
PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module

PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Fehlerbehebung, wenn sowohl der NuGet-Anbieter als auch „NuGet.exe“ während eines Veröffentlichungsvorgangs auf einem Computer ohne Internetverbindung nicht verfügbar sind

```powershell
PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed and NuGet.exe is available under
one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetBinaries,Publish-Module

PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a>Manuelles Bootstrapping des NuGet-Anbieters auf einem Computer ohne Internetverbindung

Die oben gezeigten Prozesse setzen voraus, dass der Computer mit dem Internet verbunden ist und dass Dateien von einem öffentlichen Speicherort heruntergeladen werden können.
Wenn dies nicht möglich ist, kann für einen Computer nur mithilfe der oben gezeigten Prozesse ein Bootstrapping durchgeführt werden, und der Anbieter muss über einen vertrauenswürdigen Offlineprozess auf den isolierten Knoten kopiert werden.
Der gängigste Anwendungsfall für dieses Szenario ist die Verwendung eines privaten Katalogs zur Unterstützung einer isolierten Umgebung.

Nach der Durchführung des Prozesses für das Bootstrapping eines Computers mit Internetverbindung finden Sie Anbieterdateien in diesem Verzeichnis:

```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

Die Ordner-/Dateistruktur des NuGet-Anbieters sieht folgendermaßen aus (die Versionsnummer weicht wahrscheinlich ab):

NuGet<br>
--2.8.5.208<br>
----Microsoft.PackageManagement.NuGetProvider.dll

Kopieren Sie diese Ordner und Dateien unter Verwendung eines vertrauenswürdigen Prozesses auf den Offlinecomputer.

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a>Manuelles Bootstrapping von „NuGet.exe“ zur Unterstützung von Veröffentlichungsvorgängen auf einem Computer ohne Internetverbindung

Zusätzlich zum Prozess des manuellen Bootstrappings des NuGet-Anbieters ist die binäre ausführbare Datei „NuGet.exe“ erforderlich, wenn mit dem Computer unter Verwendung der Cmdlets *Publish-Module* oder *Publish-Script* Module oder Skripts in einem privaten Katalog veröffentlicht werden sollen.
Der gängigste Anwendungsfall für dieses Szenario ist die Verwendung eines privaten Katalogs zur Unterstützung einer isolierten Umgebung.
Es gibt zwei Optionen zum Abrufen der Datei „NuGet.exe“.

Die erste Option besteht darin, ein Bootstrapping für einen Computer mit Internetverbindung durchzuführen und die Dateien unter Verwendung eines vertrauenswürdigen Prozesses auf die Offlinecomputer zu kopieren.
Nach dem Bootstrapping des Computers mit Internetverbindung befindet sich die binäre Datei „NuGet.exe“ in einem dieser zwei Ordner:

Wenn die Cmdlets *Publish-Module* oder *Publish-Script* mit erhöhten Rechten (als Administrator) ausgeführt wurden:

```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Wenn die Cmdlets als Benutzer ohne erhöhte Rechte ausgeführt wurden:

```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

Eine zweite Option besteht darin, „NuGet.exe“ von der NuGet.Org-Website herunterzuladen: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)<br>
Bei Auswahl einer NuGet-Version für Produktionscomputer müssen Sie sicherstellen, eine höhere Version als 2.8.5.208 zu verwenden und die Version zu ermitteln, die als „empfohlen“ gekennzeichnet ist.
Denken Sie daran, die Datei zu entsperren, wenn sie mit einem Browser heruntergeladen wurde.
Sie können die Entsperrung mit dem Cmdlet *Unblock-File* durchführen.

In beiden Fällen kann die Datei „NuGet.exe“ an einen beliebigen Speicherort unter *$env:path* kopiert werden, aber dies sind die Standardspeicherorte:

So machen Sie die ausführbare Datei für alle Benutzer verfügbar und ermöglichen ihnen die Verwendung der Cmdlets *Publish-Module* und *Publish-Script*:

```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Um die ausführbare Datei nur für einen bestimmten Benutzer verfügbar zu machen, kopieren Sie sie nur an den Speicherort innerhalb des Profils dieses Benutzers:

```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```