---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: gallery,powershell,cmdlet,psgallery
title: Pakete mit kompatiblen PowerShell-Editionen oder Betriebssystem
ms.openlocfilehash: 8230866561d3021379a48cc2c83fb4104a4058c1
ms.sourcegitcommit: d396d0e4cfe3d279f399c17e7337380a31d373ac
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747703"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>Pakete mit kompatiblen PowerShell-Editionen oder Betriebssystemen

Ab Version 5.1 steht PowerShell in verschiedenen Editionen zur Verfügung, die unterschiedliche Featuregruppen und Plattformkompatibilität bieten.

## <a name="searching-by-powershell-edition"></a>Suchen nach PowerShell-Editionen 
Die zwei Editionen von Powershell sind:
- Desktop Edition Basiert auf .NET Framework und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter Vollversionen von Windows wie Server Core und Windows-Desktop ausgeführt wird.
- **Core-Edition:** Basiert auf .NET Core und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter funktionsreduzierten Versionen von Windows wie Nano Server und Windows IoT ausgeführt wird.

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>PowerShell-Katalog können Sie Pakete, die kompatibel für bestimmte PowerShell-Editionen filtern

Verfügt ein Paket kompatible angegebene PSEditions, sie als Teil des "PowerShell-Editionen" aufgeführt sind in der Seite für Pakete anzeigen und auch in Paketen Ergebnisse.
Sie können auch nach kompatiblen Paketen, die mithilfe von PowerShell suchen.

![Seite des Elements mit PSEditions](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>Suchen Sie nach Paketen in der Benutzeroberfläche des Katalogs, die auf PowerShell Core

Verwenden Sie die Tags „PSEdition_Desktop“ und „PSEdition_Core“, um die Pakete im PowerShell-Katalog zu filtern.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Verwenden Sie das Tag „PSEdition_Core“, um Elemente zu suchen, die mit der PowerShell Core-Edition kompatibel sind.

![Suchergebnisse für Elemente, die mit Core PSEdition kompatibel sind](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Verwenden Sie das Tag „PSEdition_Desktop“, um Elemente zu suchen, die mit der PowerShell Desktop Edition kompatibel sind.

![Suchergebnisse für Elemente, die mit Desktop PSEdition kompatibel sind](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>Suchen Sie nach Paketen kompatible mithilfe von PowerShell-Editionen zu finden
Sie können Tags für die PowerShell-Edition und Betriebssystem Filtern angeben. Sie verwenden die `Find-Package` Cmdlet angeben der `-Tag` Parameter zum Angeben der Edition (und Betriebssystem) Sie Anzielen.
So:

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>Suchen nach Betriebssystem 

Da PowerShell Core für Windows, Linux und MacOS verfügbar ist, können der Pakete im Katalog für eine beliebige Kombination dieser Betriebssysteme so entworfen werden. Verwenden Sie die folgenden Searchs Tags um Pakete, die vom Betriebssystem markiert zu suchen, in der Benutzeroberfläche des Katalogs:

- Tags: "Windows"
- Tags: "Linux"
- Tags: "MacOS" 

Sie können diese Tags angeben, auf `Find-Module` (und andere Cmdlets im PowerShellGet-Modul) wie folgt aus:

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>Für mehrere Probleme mit der Suche

Sie können für ein Paket anzeigen, die über mehrere Probleme mit der Syntax verfügt: 

Tags "Compatibility1" "Compatibility2" 

Wenn Sie ein Paket mit PowerShell Core Kompatibilität, die für meine Windows und Linux-Computer ausgeführt wird suchen, verwenden Sie z. B. die Markierungen suchen:

Tags "PSEdition_Core", "Windows", "Linux" 

Um mithilfe von PowerShell zu suchen, können Sie die `Find-Module` (und die anderen Cmdlets im PowerShellGet-Modul) wie folgt aus:

```powewrshell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Weitere Informationen zum Erstellen und Suchen von Paketen mit kompatiblen PowerShell-Editionen

- [Module mit PowerShell-Editionen](../../concepts/module-psedition-support.md)
- [Skripts mit PowerShell-Editionen](../../concepts/script-psedition-support.md)
