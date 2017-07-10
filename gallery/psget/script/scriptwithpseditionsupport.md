---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Skript mit kompatiblen PowerShell-Editionen | MSDN
ms.openlocfilehash: e6994b994cb15903560f3dd89c21383fb2cd367d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="script-with-compatible-powershell-editions" class="xliff"></a>
# Skript mit kompatiblen PowerShell-Editionen
Ab Version 5.1 steht PowerShell in verschiedenen Editionen zur Verfügung, die unterschiedliche Featuregruppen und Plattformkompatibilität bieten.

- **Desktop-Edition:** Diese Edition basiert auf .NET Framework und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter Vollversionen von Windows wie Server Core und Windows Desktop ausgeführt werden.
- **Core-Edition:** Diese Edition basiert auf .NET Core und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter funktionsreduzierten Versionen von Windows wie Nano Server und Windows IoT ausgeführt werden.

Die ausgeführte Edition von PowerShell wird in der PSEdition-Eigenschaft von $PSVersionTable angezeigt.
```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

Skriptautoren können verhindern, dass ein Skript ausgeführt wird, sofern es nicht in einer kompatiblen Edition von PowerShell mithilfe des Parameters „PSEdition“ in einer „#requires“-Anweisung ausgeführt wird.
```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell Core edition. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

Benutzer des PowerShell-Katalogs können die Liste der Skripts suchen, die in einer bestimmten PowerShell-Edition unterstützt werden.
Skripts ohne „PSEdition_Desktop“ und „PSEditon_Core“ sollten in PowerShell Desktop keine Probleme bereiten.

```powershell

# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEditon_Desktop

# Find scripts supported on PowerShell Core editions
Find-Script -Tag PSEditon_Core

```

<a id="more-details" class="xliff"></a>
## Weitere Details
<a id="modules-with-pseditionsmodulemodulewithpseditionsupportmd" class="xliff"></a>
### [Module mit PowerShell-Editionen](../module/modulewithpseditionsupport.md)
<a id="pseditions-support-on-powershellgallerypsgallerypsgallerypseditionsmd" class="xliff"></a>
### [Unterstützung von PowerShell-Editionen im PowerShell-Katalog](../../psgallery/psgallery_pseditions.md)

