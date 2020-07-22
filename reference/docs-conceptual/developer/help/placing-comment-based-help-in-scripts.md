---
title: Ablegen der kommentarbasierten Hilfe in Skripts
ms.date: 09/12/2016
ms.openlocfilehash: a3ade6c3138826b924939056b9d1ffb233006d44
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893185"
---
# <a name="placing-comment-based-help-in-scripts"></a>Ablegen der kommentarbasierten Hilfe in Skripts

In diesem Thema wird erläutert, wo Sie eine Kommentar basierte Hilfe für ein Skript platzieren können, damit das `Get-Help` Cmdlet das Kommentar basierte Hilfethema Skripts und keine Funktionen zuordnet, die möglicherweise im Skript vorhanden sind.

## <a name="where-to-place-comment-based-help-for-a-script"></a>Platzieren der Kommentar basierten Hilfe für ein Skript

- Am Anfang der Skriptdatei.

  Der Skript Hilfe kann das Skript nur durch Kommentare und leere Zeilen vorangestellt werden.

- Am Ende der Skriptdatei.

  Wenn das erste Element im Skript Text (nach der Hilfe) eine Funktionsdeklaration ist, müssen zwischen dem Ende der Skript Hilfe und der Funktionsdeklaration mindestens zwei Leerzeilen vorhanden sein. Andernfalls wird die Hilfe als Hilfe für die Funktion interpretiert, nicht als Hilfe für das Skript.

## <a name="examples-of-help-placement-in-a-script"></a>Beispiele für die Platzierung von Hilfe in einem Skript

In den folgenden Beispielen werden die einzelnen Platzierungs Optionen für die Kommentar basierte Hilfe eines Skripts gezeigt.

### <a name="help-at-the-beginning-of-a-script"></a>Hilfe zu Beginn eines Skripts

Das folgende Beispiel zeigt einen Kommentar basierten am Anfang eines Skripts.

```powershell
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>Hilfe am Ende eines Skripts

 Das folgende Beispiel zeigt am Ende eines Skripts eine Kommentar basierte.

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>
```
