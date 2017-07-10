---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Uninstall-Module
ms.openlocfilehash: 3c4d8faa63aba6b4434d42a19a219baf84122591
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="uninstall-module" class="xliff"></a>
# Uninstall-Module

Deinstalliert ein Modul, das mithilfe der „PowerShellGet“-Cmdlets installiert wurde

<a id="description" class="xliff"></a>
## Beschreibung

Das Cmdlet „Uninstall-Module“ deinstalliert das angegebene Modul auf dem lokalen Computer. Sie können ein Modul nicht deinstallieren, wenn einige andere Module von ihm abhängig sind.
Das Cmdlet „Uninstall-Module“ überprüft zudem, ob das Modul, das deinstalliert wird, gerade verwendet wird oder nicht. Wenn das Modul gerade verwendet wird, wird ein Fehler ausgelöst.

<a id="cmdlet-syntax" class="xliff"></a>
## Cmdlet-Syntax
```powershell
Get-Command -Name Uninstall-Module -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>
## Cmdlet-Onlinehilfe

[Uninstall-Module](http://go.microsoft.com/fwlink/?LinkId=526864)


<a id="example-commands" class="xliff"></a>
## Beispiele für Befehle

<a id="run-the-uninstall-module-cmdlet-to-uninstall-a-module-that-you-installed-by-using-powershellget" class="xliff"></a>
###  Führen Sie das Cmdlet „Uninstall-Module“ zum Deinstallieren eines Moduls aus, das Sie mit PowerShellGet installiert haben.
Wenn ein anderes Modul von dem Modul abhängt, das Sie löschen möchten, löst PowerShellGet einen Fehler aus.
```powershell
Get-InstalledModule -Name RequiredModule1 | Uninstall-Module

PackageManagement\Uninstall-Package : The module 'RequiredModule1' of version '2.5' in module base folder 'C:\Program Files\WindowsPowerShell\Modules\RequiredModule1\2.5' cannot be uninstalled, because one or more other modules 'ModuleWithDependencies2' are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'RequiredModule1'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\PSGet.psm1:1303 char:25
+ ... $null = PackageManagement\\Uninstall-Package @PSBoundParameters
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Package], Exception
+ FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.UninstallPackage
```

<a id="uninstalling-a-module-when-some-other-modules-have-a-dependency-on-it" class="xliff"></a>
### Deinstallieren eines Moduls, wenn einige andere Module von ihm abhängig sind

```powershell
Uninstall-Module SnippetPx

PackageManagement\Uninstall-Package : The module 'SnippetPx' of version '1.0.5.18' in module base folder 'C:\ProgramFiles\WindowsPowerShell\Modules\SnippetPx\1.0.5.18' cannot be uninstalled, because one or more other modules 'TypePx' are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'SnippetPx'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.3\PSModule.psm1:1803 char:21
+ ...        $null = PackageManagement\Uninstall-Package @PSBoundParameters
+                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Packag
   e], Exception
    + FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.Pac
   kageManagement.Cmdlets.UninstallPackage
```

<a id="you-can-override-this-by-specify--force-option-on-uninstall-module-cmdlet" class="xliff"></a>
### Sie können es überschreiben, indem Sie die Option „-Force“ im Cmdlet „Uninstall-Module“ angeben
**HINWEIS:** Dies wird nicht empfohlen. Bei dieser Aktion werden andere Module unterbrochen.

```powershell
Uninstall-Module SnippetPx -Force
```

<a id="uninstall-a-module-which-is-already-in-use" class="xliff"></a>
### Deinstallieren eines Moduls, das bereits verwendet wird

```powershell
Get-InstalledModule TypePx,SnippetPx

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to...
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experi...
```

<a id="uninstall-snippetpx-fails-due-to-the-dependent-module" class="xliff"></a>
### Fehler beim Deinstallieren von SnippetPx aufgrund des abhängigen Moduls

```powershell
Uninstall-Module SnippetPx

PackageManagement\Uninstall-Package : The module 'SnippetPx' of version '1.0.5.18' in module base folder 'C:\Program
Files\WindowsPowerShell\Modules\SnippetPx\1.0.5.18' cannot be uninstalled, because one or more other modules 'TypePx'
are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'SnippetPx'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1914 char:21
+ ...        $null = PackageManagement\Uninstall-Package @PSBoundParameters
+                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Packag
   e], Exception
    + FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.Pac
   kageManagement.Cmdlets.UninstallPackage
```

<a id="uninstall-typepx-then-uninstall-the-snippetpx" class="xliff"></a>
### Deinstallieren von TypePx, anschließend Deinstallieren von SnippetPx

```powershell
Uninstall-Module TypePx
Uninstall-Module SnippetPx

WARNING: The version '1.0.5.18' of module 'SnippetPx' is currently in use. Retry the operation after closing the
applications.
PackageManagement\Uninstall-Package : Module 'SnippetPx' is in currently in use.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1914 char:21
+ ...        $null = PackageManagement\Uninstall-Package @PSBoundParameters
+                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Packag
   e], Exception
    + FullyQualifiedErrorId : ModuleIsInUse,Uninstall-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.Uninstall
   Package
```


<a id="for-a-module-name-which-is-not-installed-using-powershellget-cmdlets" class="xliff"></a>
### Bei einem Modul, das nicht mithilfe der „PowerShellGet“-Cmdlets installiert wurde

```powershell
Uninstall-Module SnipptPx

PackageManagement\Uninstall-Package : No match was found for the specified search criteria and module names 'SnipptPx'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1914 char:21
+ ...        $null = PackageManagement\Uninstall-Package @PSBoundParameters
+                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Package]
   , Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.UninstallPackage
```

