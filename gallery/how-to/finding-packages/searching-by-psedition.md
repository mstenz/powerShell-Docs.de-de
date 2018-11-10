---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Pakete mit kompatiblen PowerShell-Editionen
ms.openlocfilehash: e16cfb0ee30e344c9399bec2985baafc5a252fd7
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003787"
---
# <a name="packages-with-compatible-powershell-editions"></a>Pakete mit kompatiblen PowerShell-Editionen

Ab Version 5.1 steht PowerShell in verschiedenen Editionen zur Verfügung, die unterschiedliche Featuregruppen und Plattformkompatibilität bieten.

- **Desktop-Edition:** Diese Edition basiert auf .NET Framework und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter Vollversionen von Windows wie Server Core und Windows Desktop ausgeführt werden.
- **Core-Edition:** Diese Edition basiert auf .NET Core und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter funktionsreduzierten Versionen von Windows wie Nano Server und Windows IoT ausgeführt werden.

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-packages-compatible-for-specific-powershell-editions"></a>Der PowerShell-Katalog extrahiert unterstützte PSEditions-Metadaten und ermöglicht Ihnen das Filtern nach Paketen, die mit bestimmten PowerShell-Editionen kompatibel sind.

Wenn für ein Paket kompatible PSEditions angegeben sind, werden diese im Rahmen von „PowerShell-Editionen“ auf der Paketseite und in den Paketergebnissen aufgelistet.

![Seite des Elements mit PSEditions](../../Images/manual_package_download.png)

## <a name="search-for-packages-in-the-gallery-ui-which-works-on-powershellcore"></a>Suchen nach Paketen in der Katalogbenutzeroberfläche in PowerShellCore

Verwenden Sie die Tags „PSEdition_Desktop“ und „PSEdition_Core“, um die Pakete im PowerShell-Katalog zu filtern.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Verwenden Sie das Tag „PSEdition_Core“, um Elemente zu suchen, die mit der PowerShell Core-Edition kompatibel sind.

![Suchergebnisse für Elemente, die mit Core PSEdition kompatibel sind](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Verwenden Sie das Tag „PSEdition_Desktop“, um Elemente zu suchen, die mit der PowerShell Desktop Edition kompatibel sind.

![Suchergebnisse für Elemente, die mit Desktop PSEdition kompatibel sind](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Weitere Informationen zum Erstellen und Suchen von Paketen mit kompatiblen PowerShell-Editionen

- [Module mit PowerShell-Editionen](../../concepts/module-psedition-support.md)
- [Skripts mit PowerShell-Editionen](../../concepts/script-psedition-support.md)
