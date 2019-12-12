---
title: Platzieren der Kommentar basierten Hilfe in Functions | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367779"
---
# <a name="placing-comment-based-help-in-functions"></a>Ablegen der kommentarbasierten Hilfe in Funktionen

In diesem Thema wird erläutert, wo Sie eine Kommentar basierte Hilfe für eine Funktion platzieren können, damit das `Get-Help`-Cmdlet das Kommentar basierte Hilfethema der richtigen Funktion zuordnet.

## <a name="where-to-place-comment-based-help-for-a-function"></a>Speicherort der Kommentar basierten Hilfe für eine Funktion

- Am Anfang des Funktions Texts.

- Am Ende des Funktions Texts.

- Vor dem `Function`-Schlüsselwort. Wenn sich die Funktion in einem Skript-oder Skript Modul befindet, darf zwischen der letzten Zeile der Kommentar basierten Hilfe und dem `Function`-Schlüsselwort nicht mehr als eine Leerzeile vorhanden sein. Andernfalls ordnet `Get-Help` die Hilfe dem Skript zu, nicht mit der-Funktion.

## <a name="examples-of-help-placement-in-a-function"></a>Beispiele für die Platzierung von Hilfe in einer Funktion

 Die folgenden Beispiele zeigen jede der drei Platzierungs Optionen für die Kommentar basierte Hilfe für eine Funktion.

### <a name="help-at-the-beginning-of-a-function-body"></a>Hilfe am Anfang eines Funktions Texts

 Das folgende Beispiel zeigt einen Kommentar basierten am Anfang eines Funktions Texts.

```powershell

function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}

```

### <a name="help-at-the-end-of-a-function-body"></a>Hilfe am Ende eines Funktions Texts

 Das folgende Beispiel zeigt am Ende eines Funktions Texts einen Kommentar basierten Text.

```powershell

function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}

```

### <a name="help-before-the-function-keyword"></a>Hilfe vor dem Function-Schlüsselwort

 In den folgenden Beispielen wird die Kommentar basierte Zeile vor dem Function-Schlüsselwort gezeigt.

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```