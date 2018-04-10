---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: Registerkarte „Elemente“ | MSDN
ms.openlocfilehash: 5058253678a4f996b080e43820fee06b35b681f4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="items-tab"></a>Registerkarte „Elemente“

Die Registerkarte [Elemente](https://www.powershellgallery.com/items) zeigt alle verfügbaren Elemente im PowerShell-Katalog an.

Es gibt verschiedene Möglichkeiten, die Elemente zu filtern, zu sortieren und zu durchsuchen.
Um weitere Details zu einem bestimmten Element anzuzeigen, klicken Sie auf das Element.

## <a name="filter-by"></a>Filtern nach

Mit der Dropdownliste „Filtern nach“ können Benutzer die Ergebnisse nach folgenden Kriterien filtern:
* Vorabversion einbeziehen
* Nur stabile

Informationen zu „Vorabversion“ und „stabil“ finden Sie im PowerShell-Teamblog unter [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) (Versionsverwaltung von Vorabversionen zu PowerShellGet und dem PowerShell-Katalog hinzugefügt).

Mithilfe der Kontrollkästchen unter der Dropdownliste können Benutzer die Ergebnisse nach folgenden Kriterien filtern:
* Elementtypen
  - Modul
  - Skript
* Kategorien
  - Cmdlet
  - DSC-Ressource
  - Funktion
  - Rollenfunktion
  - Workflow

Um im PowerShell-Katalog nur Module anzuzeigen, aktivieren Sie unter „Elementtypen“ die Option „Module“.
Um im PowerShell-Katalog nur Skripts anzuzeigen, aktivieren Sie unter „Elementtypen“ die Option „Skript“.

> [!NOTE]
> Filter sind inklusiv.
> Beispiel: Ein Element, das sowohl Cmdlets als auch Funktionen erhält, wird angezeigt, wenn entweder „Cmdlet“ oder „Funktion“ (oder beides) aktiviert ist.
> Wenn nichts davon ausgewählt ist, wird das Element nicht angezeigt.
> Wenn auf ähnliche Weise Kategorien ausgewählt werden, erscheinen nur Elemente, die eine dieser Kategorien enthält.
> **Elemente, die zu keiner dieser Kategorie gehören, werden nicht angezeigt.**

## <a name="sort-by"></a>Sortieren nach

Mithilfe der Dropdownliste „Sortieren nach“ können Benutzer die Ergebnisse nach folgenden Kriterien filtern:
* Beliebtheit: Die Beliebtheit wird durch die Anzahl der Downloads bestimmt.
* A-Z: Alphabetisch nach Elementname.
* Aktuell: Elemente werden in der Reihenfolge der Veröffentlichungsdaten angezeigt.

## <a name="search-box"></a>Suchfeld

Mit dem Suchfeld können Benutzer Elemente nach Schlüsselwort suchen.
Weitere Informationen finden Sie unter [Syntax für die Katalogsuche](psgallery_search_syntax.md).