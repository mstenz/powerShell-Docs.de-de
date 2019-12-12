---
title: Syntax der Kommentar basierten Hilfe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367759"
---
# <a name="syntax-of-comment-based-help"></a>Syntax der kommentarbasierten Hilfe

In diesem Abschnitt wird die Syntax der Kommentar basierten Hilfe beschrieben.

## <a name="syntax-diagram"></a>Syntax Diagramm

 Die Syntax für die Kommentar basierte Hilfe lautet wie folgt:

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a>Syntaxbeschreibung

 Die Kommentar basierte Hilfe wird als eine Reihe von Kommentaren geschrieben. Sie können ein Kommentar Symbol (#) vor jeder Zeile von Kommentaren eingeben, oder Sie können die Symbole "\<#" und "# >" verwenden, um einen Kommentar Block zu erstellen. Alle Zeilen innerhalb des Kommentar Blocks werden als Kommentare interpretiert.

 Jeder Abschnitt der Kommentar basierten Hilfe wird durch ein Schlüsselwort definiert, und jedem Schlüsselwort wird ein Punkt (.) vorangestellt. Die Schlüsselwörter können in beliebiger Reihenfolge angezeigt werden. Beim Schlüsselwort Namen wird die Groß-/Kleinschreibung nicht beachtet.

 Ein Kommentar Block muss mindestens ein Hilfe Schlüsselwort enthalten. Einige der Schlüsselwörter (z. b. beispielsweise) können mehrmals im gleichen Kommentar Block vorkommen. Der Hilfe Inhalt für jedes Schlüsselwort beginnt in der Zeile nach dem-Schlüsselwort und kann sich über mehrere Zeilen erstrecken.

 Alle Zeilen in einem Kommentar basierten Hilfethema müssen zusammenhängend sein. Wenn ein Kommentar basiertes Hilfethema einem Kommentar folgt, der nicht Teil des Hilfe Themas ist, muss mindestens eine Leerzeile zwischen der letzten nicht-Hilfe Kommentarzeile und dem Anfang der Kommentar basierten Hilfe vorhanden sein.

 Beispielsweise enthält das folgende Kommentar basierte Hilfethema die. Description-Schlüsselwort und sein Wert, eine Beschreibung einer Funktion oder eines Skripts.

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```