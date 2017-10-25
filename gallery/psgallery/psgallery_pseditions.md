---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: Elemente mit kompatiblen PowerShell-Editionen | MSDN
ms.openlocfilehash: 6634da5c2dadee9c0c6470b3d3e8883e6d02160f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="items-with-compatible-powershell-editions"></a>Elemente mit kompatiblen PowerShell-Editionen
Ab Version 5.1 steht PowerShell in verschiedenen Editionen zur Verfügung, die unterschiedliche Featuregruppen und Plattformkompatibilität bieten.

- **Desktop-Edition:** Diese Edition basiert auf .NET Framework und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter Vollversionen von Windows wie Server Core und Windows Desktop ausgeführt werden.
- **Core-Edition:** Diese Edition basiert auf .NET Core und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter funktionsreduzierten Versionen von Windows wie Nano Server und Windows IoT ausgeführt werden.

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a>Der PowerShell-Katalog extrahiert unterstützte PSEditions-Metadaten und erlaubt Ihnen, die für bestimmte PowerShell-Editionen kompatiblen Elemente zu filtern

Verfügt ein Element über kompatible angegebene PSEditions, werden diese als Teil von „PowerShell Editions“ (PowerShell-Editionen) auf der Seite des Elements und auch in den Elementergebnissen aufgelistet.
![Seite des Elements mit PowerShell-Editionen](Images/ItemDisplayPageWithPSEditions.PNG)

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a>Suchen nach Elementen in der Benutzeroberfläche des Katalogs, die auf PowerShellCore arbeitet
Verwenden Sie die Tags „PSEdition_Desktop“ und „PSEdition_Core“, um die Elemente im PowerShell-Katalog zu filtern.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Verwenden Sie das Tag „PSEdition_Core“, um Elemente zu suchen, die mit der PowerShell Core-Edition kompatibel sind.
![Suchergebnisse für Elemente, die mit Core PSEdition kompatibel sind](Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Verwenden Sie das Tag „PSEdition_Desktop“, um Elemente zu suchen, die mit der PowerShell Desktop Edition kompatibel sind.
![Suchergebnisse für Elemente, die mit Desktop PSEdition kompatibel sind](Images/SearchResultsWithPSEdition_Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a>Weitere Informationen zur Erstellung und zum Suchen der Element mit kompatiblen PowerShell-Editionen
### <a name="modules-with-pseditionspsgetmodulemodulewithpseditionsupportmd"></a>[Module mit PowerShell-Editionen](../psget/module/modulewithpseditionsupport.md)
### <a name="scripts-with-pseditionspsgetscriptscriptwithpseditionsupportmd"></a>[Skripts mit PowerShell-Editionen](../psget/script/scriptwithpseditionsupport.md)

