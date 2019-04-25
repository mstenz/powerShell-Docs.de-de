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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065664"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="24e1f-102">Formatieren von angezeigten Daten</span><span class="sxs-lookup"><span data-stu-id="24e1f-102">Formatting Displayed Data</span></span>

<span data-ttu-id="24e1f-103">Sie können angeben, wie die einzelnen Datenpunkte in der Liste, eine Tabelle oder eine Breite Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="24e1f-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="24e1f-104">Können Sie die `FormatString` Element beim definieren die Elemente von der Ansicht, oder Sie können die `ScriptBlock` Element aufrufen, die `FormatString` Methode für die Daten.</span><span class="sxs-lookup"><span data-stu-id="24e1f-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="24e1f-105">Verwenden die FormatString-Element</span><span class="sxs-lookup"><span data-stu-id="24e1f-105">Using the FormatString Element</span></span>

<span data-ttu-id="24e1f-106">Im folgenden Beispiel den Wert von der `TotalProcessorTime` Eigenschaft der ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Objekt wird formatiert, mit dem FormatString-Element.</span><span class="sxs-lookup"><span data-stu-id="24e1f-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="24e1f-107">Die `TotalProcessorTime` Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="24e1f-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



