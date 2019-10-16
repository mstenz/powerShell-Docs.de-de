---
title: Formatieren angezeigter Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38971643-2a3d-4f5b-a1fa-6334c162b8ed
caps.latest.revision: 4
ms.openlocfilehash: e915ac71feb50cb58cfa9195f0de94763affdb77
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363699"
---
# <a name="formatting-displayed-data"></a>Formatieren von angezeigten Daten

Sie können angeben, wie die einzelnen Datenpunkte in der Listen-, Tabellen-oder breiten Ansicht angezeigt werden. Sie können das `FormatString`-Element verwenden, wenn Sie die Elemente der Ansicht definieren, oder Sie können das `ScriptBlock`-Element verwenden, um die `FormatString`-Methode für die Daten aufzurufen.

## <a name="using-the-formatstring-element"></a>Verwenden des FormatString-Elements

Im folgenden Beispiel wird der Wert der `TotalProcessorTime`-Eigenschaft des [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekts mit dem FormatString-Element formatiert. die `TotalProcessorTime`-Eigenschaft

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



