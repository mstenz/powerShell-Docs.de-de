---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, Cmdlet, Katalog
ms.date: 2016-10-14
contributor: manikb
title: "Registerkarte „Elemente“ | MSDN"
ms.technology: powershell
ms.openlocfilehash: 32f28df7318472f34f79c61f19f33016cf73f517
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
<a name="items-tab"></a>Registerkarte „Elemente“
==========

Die Registerkarte „Elemente“ zeigt alle verfügbaren Elemente im PowerShell-Katalog an.

Um nur die Module im PowerShell-Katalog anzuzeigen, klicken Sie in der Dropdownliste der Registerkarte „Elemente“ auf „Module“.  Wenn Sie nur Skripts im PowerShell-Katalog anzuzeigen, klicken Sie in der Dropdownliste der Registerkarte „Elemente“ auf „Skripts“.  

Um weitere Details zu einem bestimmten Element anzuzeigen, klicken Sie auf das Element.

Es gibt mehrere Methoden zum Sortieren der Elemente:

##<a name="filter-by"></a>Filtern nach##
Der Abschnitt „Filtern nach“ ermöglicht es Benutzern die Ergebnisse nach Folgendem zu filtern:
* Elementtyp:
    * Module
    * Scripts
* Kategorie:
    * Cmdlet
    * DSC-Ressource
    * Funktion
    * Workflow

Hinweis: Filter sind inklusiv.  
Beispiel: Ein Element, das jeweils Cmdlets und Funktionen erhält, erscheint, wenn entweder ein Cmdlet oder eine Funktion (oder beides) aktiviert ist.  Wenn nichts davon ausgewählt ist, wird das Element nicht angezeigt.  
Wenn auf ähnliche Weise Kategorien ausgewählt werden, erscheinen nur Elemente, die eine dieser Kategorien enthält. **Elemente, die zu keiner dieser Kategorie gehören, werden nicht angezeigt.**

##<a name="sort-by"></a>Sortieren nach## 
Die Dropdownliste „Sortieren nach“ erlaubt Benutzern, die Ergebnisse nach Folgendem zu sortieren:
* Beliebtheit – Die Beliebtheit wird durch die Anzahl der Downloads bestimmt.
* A-Z – Alphabetisch nach Elementname.
* Aktuell – Elemente werden in der Reihenfolge des Veröffentlichungsdatums angezeigt.


##<a name="search-box"></a>Suchfeld##
Mit dem Suchfeld können Benutzer Elemente nach Schlüsselwort suchen.  
Weitere Details finden Sie unter [Search Syntax (Suchsyntax)](./psgallery_search_syntax.md).

