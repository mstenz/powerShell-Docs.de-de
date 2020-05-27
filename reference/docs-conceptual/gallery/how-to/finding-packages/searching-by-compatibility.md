---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: gallery,powershell,cmdlet,psgallery
title: Pakete mit kompatiblen PowerShell-Editionen oder Betriebssystemen
ms.openlocfilehash: fce1383fa604a555a40b050ce92c5cc45ca7054c
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83691455"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>Pakete mit kompatiblen PowerShell-Editionen oder Betriebssystemen

Ab Version 5.1 steht PowerShell in verschiedenen Editionen zur Verfügung, die unterschiedliche Featuregruppen und Plattformkompatibilität bieten.

## <a name="searching-by-powershell-edition"></a>Suchen nach PowerShell-Edition

Es gibt zwei PowerShell-Editionen:

- **Desktop-Edition:** Diese Edition basiert auf .NET Framework und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter Vollversionen von Windows wie Server Core und Windows Desktop ausgeführt werden.
- **Core-Edition:** Diese Edition basiert auf .NET Core und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter funktionsreduzierten Versionen von Windows wie Nano Server und Windows IoT ausgeführt werden.

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>Der PowerShell-Katalog ermöglicht es, Pakete herauszufiltern, die mit bestimmten PowerShell-Editionen kompatibel sind

Wenn für ein Paket kompatible PSEditions angegeben sind, werden diese im Rahmen von „PowerShell-Editionen“ auf der Paketseite und in den Paketergebnissen aufgelistet.
Sie können auch mithilfe von PowerShell nach kompatiblen Paketen suchen.

![Seite des Elements mit PSEditions](media/searching-by-compatibility/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>Suchen nach Paketen in der Katalogbenutzeroberfläche in PowerShell Core

Verwenden Sie die Tags „PSEdition_Desktop“ und „PSEdition_Core“, um die Pakete im PowerShell-Katalog zu filtern.

### <a name="use-tagspsedition_core-to-search-items-compatible-with-powershell-core-edition"></a>Verwenden Sie das Tag „PSEdition_Core“, um Elemente zu suchen, die mit der PowerShell Core-Edition kompatibel sind.

![Suchergebnisse für Elemente, die mit Core PSEdition kompatibel sind](media/searching-by-compatibility/searchresultswithpseditions.PNG)

### <a name="use-tagspsedition_desktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Verwenden Sie das Tag „PSEdition_Desktop“, um Elemente zu suchen, die mit der PowerShell Desktop Edition kompatibel sind.

![Suchergebnisse für Elemente, die mit Desktop PSEdition kompatibel sind](media/searching-by-compatibility/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>Suchen nach Paketen mithilfe von PowerShell, um kompatible Versionen zu finden
Sie können Tags angeben, um nach PowerShell-Edition und Betriebssystem zu filtern.
Sie verwenden das Cmdlet `Find-Package`, das die `-Tag`-Parameter angibt, um die Edition und das Betriebssystem anzugeben, auf das Sie abzielen.
Dies sieht folgendermaßen aus:

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>Suchen je Betriebssystem

Da PowerShell Core für Windows, Linux und MacOS verfügbar ist, können die Pakete im Katalog für alle Kombinationen dieser drei Betriebssysteme entworfen werden. Verwenden Sie in der Katalogbenutzeroberfläche je nach Betriebssystem die folgenden Suchtags, um Pakete zu finden, die mit einem Tag versehen wurden:

- Tags: "Windows"
- Tags: "Linux"
- Tags: "MacOS"

Sie können diese Tags folgendermaßen auf `Find-Module` (und anderen Cmdlets im PowerShellGet-Modul) angeben:

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>Suchen nach mehrfacher Kompatibilität

Sie können nach einem Paket suchen, das mehrere Kompatibilitäten hat, wenn Sie diese Syntax verwenden:

Tags: „Kompatibilität1“ „Kompatibilität2“

Wenn Sie beispielsweise nach einem Paket mit PowerShell Core-Kompatibilität suchen, das sowohl auf Windows- als auch auf Linux-Computern ausgeführt werden kann, verwenden Sie diese Suchtags:

Tags: „PSEdition_Core“ „Windows“ „Linux“

Wenn Sie über PowerShell suchen möchten, können Sie folgendermaßen `Find-Module` (und die anderen Cmdlets im PowerShellGet-Modul) verwenden:

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Weitere Informationen zum Erstellen und Suchen von Paketen mit kompatiblen PowerShell-Editionen

- [Module mit PowerShell-Editionen](../../concepts/module-psedition-support.md)
- [Skripts mit PowerShell-Editionen](../../concepts/script-psedition-support.md)
