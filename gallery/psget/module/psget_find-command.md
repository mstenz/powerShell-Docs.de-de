---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Find-Command
ms.openlocfilehash: f867f12b1c6efad30a04581c6f36c5a77a2fb2ae
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="find-command" class="xliff"></a>
# Find-Command

Sucht PowerShell-Befehle in Modulen.

<a id="description" class="xliff"></a>
## Beschreibung
Das Cmdlet Find-Command sucht PowerShell-Befehle wie z.B. Cmdlets, Aliase, Funktionen und Workflows. Find-Command sucht Module in registrierten Repositorys.
Für jeden Befehl, den dieses Cmdlet findet, gibt es ein PSGetCommandInfo-Objekt zurück. Sie können ein PSGetCommandInfo-Objekt an das Install-Module-Cmdlet übergeben, um das Modul zu installieren, das den Befehl enthält.

- Find-Command kann mit Versionsparametern filtern: MinimumVersion, RequiredVersion, AllVersions.
  - Die Parameter schließen sich gegenseitig aus.
  - Diese Versionsparameter sind nur mit dem einzigen Modulnamen ohne Platzhalter erlaubt.
  - Wenn der RequiredVersion-Parameter nicht angegeben wird, gibt Find-Command die neueste Version des Moduls zurück, das gleich oder größer als die angegebene minimale Version oder die neueste Version des Moduls ist, wenn keine Mindestversion angegeben wird.
  - Wenn der RequiredVersion-Parameter angegeben ist, gibt Find-Command nur die Version des Moduls zurück, die genau mit der angegebenen Version übereinstimmt.
- Find-Command kann Modulmetadaten anhand des „-Tag“-Parameters filtern.
- Find-Command kann mit dem „-Filter“-Parameter nach einer repositoryspezifischen Suchsprache filtern.
- Find-Command kann Module von allen oder einigen registrierten Repositorys filtern.

<a id="cmdlet-syntax" class="xliff"></a>
## Cmdlet-Syntax
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>
## Cmdlet-Onlinehilfe

[Find-Command](http://go.microsoft.com/fwlink/?LinkId=733636)

<a id="example-commands" class="xliff"></a>
## Beispiele für Befehle
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```

