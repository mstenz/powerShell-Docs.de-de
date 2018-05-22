---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: d4168640f67cb1dd44e91d1867e87fd7a6b7f549
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="8f8ee-102">Unterstützung der gleichzeitigen Ausführung unterschiedlicher Versionen für PowerShell 5.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="8f8ee-102">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="8f8ee-103">Für die in Windows PowerShell 5.0 oder höher ausgeführten Cmdlets „Install-Module“ „Update-Module“ und „Publish-Module“ wird nun die gleichzeitige Ausführung unterschiedlicher Versionen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8f8ee-103">There is now side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>
<span data-ttu-id="8f8ee-104">Außerdem haben wir dem Cmdlet „Publish-Module“ den Parameter „-RequiredVersion“ hinzugefügt, um die Version anzugeben, die veröffentlicht werden soll.</span><span class="sxs-lookup"><span data-stu-id="8f8ee-104">Also, we have added a -RequiredVersion parameter to the Publish-Module cmdlet to specify the version to be published.</span></span> <span data-ttu-id="8f8ee-105">Der „Path“-Parameter unterstützt jetzt den Modulbasispfad mit dem Ordner „version“.</span><span class="sxs-lookup"><span data-stu-id="8f8ee-105">The Path parameter now supports the module base path with the version folder.</span></span>

<span data-ttu-id="8f8ee-106">**Beispiele für „Install-Module“:**</span><span class="sxs-lookup"><span data-stu-id="8f8ee-106">**Install-Module examples:**</span></span>
```powershell
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

Get-InstalledModule -Name PSScriptAnalyzer -AllVersions

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.1.0      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
1.1.1      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
```
