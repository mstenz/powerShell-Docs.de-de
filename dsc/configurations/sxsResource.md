---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Importieren einer spezifischen Version einer installierten Ressource
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079998"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a>Importieren einer spezifischen Version einer installierten Ressource

> Gilt für: Windows PowerShell 5.0

In PowerShell 5.0 können separate Versionen von DSC-Ressourcen auf einem Computer parallel installiert werden. Ein Ressourcenmodul kann separate Versionen einer Ressource in nach der Version benannten Ordnern speichern.

## <a name="installing-separate-resource-versions-side-by-side"></a>Paralleles Installieren separater Ressourcenversionen

Sie können die Parameter **MinimumVersion**, **MaximumVersion** und **RequiredVersion** des Cmdlets [Install-Module](/powershell/module/PowershellGet/Install-Module) verwenden, um anzugeben, welche Version eines Moduls installiert werden soll. Wenn Sie **Install-Module** ohne Angabe eine Version aufrufen, wird die neueste Version installiert.

So gibt es beispielsweise mehrere Versionen des **xFailOverCluster**-Moduls, von denen jede eine **xCluster**-Ressource enthält. Wenn Sie **Install-Module** ohne Angabe der Versionsnummer aufrufen, wird die neueste Version des Moduls installiert.

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Um eine bestimmte Version eines Moduls zu installieren, geben Sie eine **RequiredVersion** von 1.1.0.0 an. Dadurch wird die angegebene Version parallel mit der installierten Version installiert.

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

Nun sehen Sie, dass beide Versionen des Moduls aufgelistet werden, wenn Sie `Get-DSCResource` verwenden.

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

Wenn Sie separate Ressourcenversionen auf einem Computer installiert haben, müssen Sie die Version dieser Ressource angeben, wenn Sie sie in einer Konfiguration verwenden. Hierzu geben Sie den Parameter **ModuleVersion** des Schlüsselworts **Import-DscResource** an. Wenn Sie bei einer Ressource, von der Sie mehr als eine Version installiert haben, keine Version des Ressourcenmoduls angeben, generiert die Konfiguration einen Fehler.

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

>Hinweis: Der Parameter „ModuleVersion“ von „Import-DscResource“ ist in PowerShell 4.0 nicht verfügbar. In PowerShell 4.0 können Sie eine Modulversion angeben, indem Sie ein Modulspezifikationsobjekt an den Parameter „ModuleName“ von „Import-DscResource“ übergeben. Ein Modulspezifikationsobjekt ist eine Hashtabelle, die die Schlüssel „ModuleName“ und „RequiredVersion“ enthält. Beispiel:

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
