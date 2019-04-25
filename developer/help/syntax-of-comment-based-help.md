---
title: Syntax für die Kommentarbasierte Hilfe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083211"
---
# <a name="syntax-of-comment-based-help"></a>Syntax der kommentarbasierten Hilfe

Dieser Abschnitt beschreibt die Syntax für die kommentarbasierte Hilfe.

## <a name="syntax-diagram"></a>Syntaxdiagramm

 Die Syntax für die kommentarbasierte Hilfe wird wie folgt aus:

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

 Kommentarbasierte Hilfe wird als eine Reihe von Kommentaren geschrieben. Können Sie ein Kommentarsymbol (#) vor jeder Zeile der Kommentare eingeben, oder Sie können die "\<#" und "#>" Symbole, erstellen Sie einen Kommentarblock. Alle Zeilen in den Kommentarblock, die als Kommentare interpretiert werden.

 Jeder Abschnitt kommentarbasierte Hilfe wird definiert, indem ein Schlüsselwort aus, und jedes Schlüsselwort wird durch einen Punkt (.) vorangestellt. Die Schlüsselwörter können in beliebiger Reihenfolge angezeigt werden. Die Namen von Schlüsselwörtern werden nicht beachtet.

 Kommentarblock muss mindestens ein Hilfeschlüsselwort enthalten. Einige der Schlüsselwörter, wie BEISPIELSWEISE können oft in demselben Kommentarblock angezeigt werden. Der Inhalt der Hilfe für jedes Schlüsselwort in der Zeile nach dem Schlüsselwort beginnt und kann mehrere Zeilen umfassen.

 Alle Zeilen in einem Hilfethema befehlsbasierte müssen zusammenhängend sein. Wenn ein Kommentar-basierte Hilfethema einen Kommentar, der nicht Teil des Hilfethemas ist folgt, muss mindestens eine Leerzeile zwischen der letzten Kommentarzeile des nicht-Help-und dem Beginn der kommentarbasierten Hilfe vorhanden sein.

 Im folgende Kommentar-basierte Hilfethema enthält beispielsweise die. Description-Schlüsselwort und der Wert, das eine Beschreibung einer Funktion oder ein Skript.

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```