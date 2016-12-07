---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, Cmdlet, Katalog
ms.date: 2016-10-14
contributor: manikb
title: Get-PSRepository | MSDN
ms.technology: powershell
ms.openlocfilehash: b1d5172232f0c2916382b6c35093a238f6b2cb4d
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="get-psrepository"></a>Get-PSRepository

Ruft die registrierten Repositorys auf einem Computer ab

## <a name="description"></a>Beschreibung

Das Cmdlet „Get-PSRepository“ ruft PowerShell-Modulrepositorys ab, die für den aktuellen Benutzer auf einem Computer registriert sind.

Get-PSRepository gibt für jedes registrierte Repository ein PSRepository-Objekt zurück, das optional an Unregister-PSRepository zum Aufheben der Registrierung eines registrierten Repositorys übergeben werden kann.

## <a name="cmdlet-syntax"></a>Cmdlet-Syntax
```powershell
Get-Command -Name Get-PSRepository -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet-Onlinehilfe

[Get-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517127)

## <a name="example-commands"></a>Beispiele für Befehle

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

