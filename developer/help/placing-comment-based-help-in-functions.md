---
title: Platzieren der Kommentarbasierten Hilfe in Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857946"
---
# <a name="placing-comment-based-help-in-functions"></a>Ablegen der kommentarbasierten Hilfe in Funktionen

In diesem Thema wird erläutert, befehlsbasierte Hilfe für eine Funktion zu platzieren, damit die `Get-Help` Cmdlet ordnet die ordnungsgemäße Funktion das Kommentar-basierte Hilfethema.

## <a name="where-to-place-comment-based-help-for-a-function"></a>Kommentarbasierte Hilfe für eine Funktion platzieren

- Zu Beginn des Funktionstexts.

- Am Ende der Hauptteil der Funktion.

- Bevor Sie die `Function` Schlüsselwort. Wenn die Funktion in einem Skript oder das Modul "Script" ist, gibt es nicht mehr als eine Leerzeile zwischen der letzten Zeile der kommentarbasierten Hilfe und die `Function` Schlüsselwort. Andernfalls `Get-Help` ordnet die Hilfe, mit dem Skript, nicht mit der Funktion.

## <a name="examples-of-help-placement-in-a-function"></a>Beispiele für die Platzierung von Hilfe in einer Funktion

 Die folgenden Beispiele zeigen jeweils der der drei Platzierungsoptionen für die kommentarbasierte Hilfe für eine Funktion.

### <a name="help-at-the-beginning-of-a-function-body"></a>Am Anfang eines Funktionsrumpfs-Hilfe

 Das folgende Beispiel zeigt Kommentar-basierte, am Anfang eines Funktionsrumpfs.

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

### <a name="help-at-the-end-of-a-function-body"></a>Am Ende eines Funktionsrumpfs-Hilfe

 Das folgende Beispiel zeigt die am Ende eines Funktionsrumpfs Kommentar-basierte.

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

### <a name="help-before-the-function-keyword"></a>Helfen Sie vor dem Function-Schlüsselwort

 Die folgenden Beispiele zeigen Kommentar-basierte, auf die Zeile vor dem Function-Schlüsselwort.

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```