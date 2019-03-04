---
title: Formatieren der angezeigten Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38971643-2a3d-4f5b-a1fa-6334c162b8ed
caps.latest.revision: 4
ms.openlocfilehash: e915ac71feb50cb58cfa9195f0de94763affdb77
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854986"
---
# <a name="formatting-displayed-data"></a>Formatieren von angezeigten Daten

Sie können angeben, wie die einzelnen Datenpunkte in der Liste, eine Tabelle oder eine Breite Ansicht angezeigt werden. Können Sie die `FormatString` Element beim definieren die Elemente von der Ansicht, oder Sie können die `ScriptBlock` Element aufrufen, die `FormatString` Methode für die Daten.

## <a name="using-the-formatstring-element"></a>Verwenden die FormatString-Element

Im folgenden Beispiel den Wert von der `TotalProcessorTime` Eigenschaft der ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Objekt wird formatiert, mit dem FormatString-Element. Die `TotalProcessorTime` Eigenschaft

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



