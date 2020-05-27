---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Filtern von Suchergebnissen
ms.openlocfilehash: 51f8d243cb9b1f4ff7413eec8839697299e8dd52
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83691468"
---
# <a name="filtering-search-results"></a>Filtern von Suchergebnissen

Die Registerkarte [Pakete](https://www.powershellgallery.com/packages) zeigt alle verfügbaren Pakete im PowerShell-Katalog an.

Es gibt verschiedene Möglichkeiten, die Pakete zu filtern, zu sortieren und zu durchsuchen.
Um weitere Details zu einem bestimmten Paket anzuzeigen, klicken Sie auf das Paket.

## <a name="filter-by"></a>Filtern nach

Mit der Dropdownliste „Filtern nach“ können Benutzer die Ergebnisse nach folgenden Kriterien filtern:

- Vorabversion einbeziehen
- Nur stabile

Informationen zu „Vorabversion“ und „stabil“ finden Sie im PowerShell-Teamblog unter [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) (Versionsverwaltung von Vorabversionen zu PowerShellGet und dem PowerShell-Katalog hinzugefügt).

Mithilfe der Kontrollkästchen unter der Dropdownliste können Benutzer die Ergebnisse nach folgenden Kriterien filtern:

- Pakettypen
  - Modul
  - Skript
- Kategorien
  - Cmdlet
  - DSC-Ressource
  - Funktion
  - Rollenfunktion
  - Workflow

Um im PowerShell-Katalog nur Module anzuzeigen, aktivieren Sie unter „Pakettypen“ die Option „Modul“.
Um im PowerShell-Katalog nur Skripts anzuzeigen, aktivieren Sie unter „Pakettypen“ die Option „Skript“.

> [!NOTE]
> Filter sind inklusiv.
> Beispiel: Ein Paket, das sowohl Cmdlets als auch Funktionen erhält, wird angezeigt, wenn entweder „Cmdlet“ oder „Funktion“ (oder beides) aktiviert ist.
> Wenn keine der Optionen ausgewählt ist, wird das Paket nicht angezeigt.
> Ähnliches gilt, wenn Kategorien ausgewählt werden: Es werden nur Pakete angezeigt, die zu einer dieser Kategorien gehören.
> **Pakete, die zu keiner dieser Kategorie gehören, werden nicht angezeigt.**

## <a name="sort-by"></a>Sortieren nach

Mithilfe der Dropdownliste „Sortieren nach“ können Benutzer die Ergebnisse nach folgenden Kriterien filtern:

- Beliebtheit: Die Beliebtheit wird durch die Anzahl der Downloads bestimmt.
- A-Z: Alphabetisch nach Paketname.
- Aktuell: Pakete werden in der Reihenfolge der Veröffentlichungsdaten angezeigt.

## <a name="search-box"></a>Suchfeld

Mit dem Suchfeld können Benutzer Pakete nach Schlüsselwort suchen.
Weitere Informationen finden Sie unter [Syntax für die Katalogsuche](search-syntax.md).
