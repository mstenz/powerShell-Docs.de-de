---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Importieren einer spezifischen Version einer installierten Ressource
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401169"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a>Importieren einer spezifischen Version einer installierten Ressource

> Gilt für: Windows PowerShell 5.0

In PowerShell 5.0 können jeweils eine Version der DSC-Ressourcen auf einem Computer parallel installiert werden. Ein Ressourcenmodul kann separate Versionen einer Ressource in Version, die mit dem Namen Ordner speichern.

## <a name="installing-separate-resource-versions-side-by-side"></a>Separate Ressource Versionen parallel installieren

Sie können die Parameter **MinimumVersion**, **MaximumVersion** und **RequiredVersion** des Cmdlets [Install-Module](/powershell/module/PowershellGet/Install-Module) verwenden, um anzugeben, welche Version eines Moduls installiert werden soll. Wenn Sie **Install-Module** ohne Angabe eine Version aufrufen, wird die neueste Version installiert.

So gibt es beispielsweise mehrere Versionen des **xFailOverCluster**-Moduls, von denen jede eine **xCluster**-Ressource enthält. Aufrufen von **Install-Module** ohne Angabe der Versionsnummer Anzahl die neueste Version des Moduls wird installiert.

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Um eine bestimmte Version eines Moduls zu installieren, geben Sie einen **"requiredversion"** von 1.1.0.0. Dadurch wird die angegebene Version parallel mit der installierten Version installiert.

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

Sie sehen Sie sich sowohl Version des Moduls aufgeführt, bei der Verwendung `Get-DSCResource`.

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>Angeben einer Ressourcenversion in einer Konfiguration

Wenn Sie eine separate Ressource-Versionen, die auf einem Computer installiert haben, müssen Sie die Version der Ressource, die bei Verwendung in einer Konfiguration angeben. Hierzu geben Sie den Parameter **ModuleVersion** des Schlüsselworts **Import-DscResource** an. Wenn Sie bei einer Ressource, von der Sie mehr als eine Version installiert haben, keine Version des Ressourcenmoduls angeben, generiert die Konfiguration einen Fehler.

Die folgende Konfiguration zeigt, wie Sie die Version der aufzurufenden Ressource angeben:

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

>Hinweis: Der Parameter "ModuleVersion" des Import-DscResource ist nicht in PowerShell 4.0 verfügbar. In PowerShell 4.0 können Sie eine Modulversion angeben, indem Sie ein Modulspezifikationsobjekt an den Parameter „ModuleName“ von „Import-DscResource“ übergeben. Ein Modulspezifikationsobjekt ist eine Hashtabelle, die die Schlüssel „ModuleName“ und „RequiredVersion“ enthält. Beispiel:

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

Dies funktioniert auch in PowerShell 5.0, aber es wird empfohlen, dass Sie den Parameter **ModuleVersion** verwenden.

## <a name="see-also"></a>Siehe auch

- [DSC-Konfigurationen](configurations.md)
- [DSC-Ressourcen](../resources/resources.md)
