---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, Cmdlet, Katalog
ms.date: 2016-10-14
contributor: manikb
title: Unregister-PSRepository | MSDN
ms.technology: powershell
ms.openlocfilehash: c90710db47dbfdc58e1ca7f84c6d6fd8f04b5109
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="unregister-psrepository"></a>Unregister-PSRepository

Hebt die Registrierung eines Repositorys auf

## <a name="description"></a>Beschreibung

Das Cmdlet „Unregister-PSRepository“ hebt die Registrierung für ein Repository für den aktuellen Benutzer auf.
- Das Aufheben der Registrierung und das erneute Registrieren des Repositorys „PSGallery“ ist für ein Großunternehmen und getrennte Szenarios zulässig.
- Benutzer können die PSGallery erneut registrieren, indem sie einfach `Register-PSRepository -Default` ausführen.
- Da PSGallery das Standard-Veröffentlichungsrepository in den Cmdlets „Publish-Module“ und „Publish-Script“ ist, wird ein Fehler ausgegeben, wenn PSGallery in der Liste der registrierten Repositorys nicht verfügbar ist.

## <a name="cmdlet-syntax"></a>Cmdlet-Syntax

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Cmdlet-Onlinehilfe

[Unregister-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517130)

## <a name="example-commands"></a>Beispiele für Befehle

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### <a name="unregistration-and-re-registration-of-the-psgallery-repository-is-allowed-for-an-enterprise-and-disconnected-scenarios"></a>Das Aufheben der Registrierung und das erneute Registrieren des Repositorys „PSGallery“ ist für ein Großunternehmen und getrennte Szenarios zulässig.
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

