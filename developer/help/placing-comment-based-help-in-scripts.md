---
title: Platzieren der Kommentarbasierten Hilfe in Skripts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083228"
---
# <a name="placing-comment-based-help-in-scripts"></a>Ablegen der kommentarbasierten Hilfe in Skripts

In diesem Thema wird erläutert, befehlsbasierte Hilfe für ein Skript zu platzieren, damit die `Get-Help` Cmdlet ordnet die Kommentar-basierte Hilfethema mit Skripts und alle Funktionen, die in das Skript möglicherweise nicht.

## <a name="where-to-place-comment-based-help-for-a-script"></a>Kommentarbasierte Hilfe für ein Skript zu platzieren

- Am Anfang der Skriptdatei. Hilfe zu Skript kann in das Skript nur durch Kommentare und Leerzeichen vorangestellt werden.

- Am Ende der Skriptdatei.

  Wenn das erste Element in der Skripttext (nach der-Hilfe) eine Funktionsdeklaration ist, muss über mindestens zwei Leerzeilen zwischen dem Ende des Skripts Hilfe und die Funktionsdeklaration vorhanden sein. Andernfalls wird die Hilfe als Hilfe bei der Funktion nicht die Hilfe für das Skript interpretiert.

## <a name="examples-of-help-placement-in-a-script"></a>Beispiele für die Platzierung von Hilfe in einem Skript

 Die folgenden Beispiele zeigen die Platzierung-Optionen für die kommentarbasierte Hilfe für ein Skript.

### <a name="help-at-the-beginning-of-a-script"></a>Am Anfang eines Skripts Hilfe

 Das folgende Beispiel zeigt Kommentar-basierte, am Anfang eines Skripts.

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>Am Ende eines Skripts Hilfe

 Das folgende Beispiel zeigt die Kommentar-basierte am Ende eines Skripts.

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```