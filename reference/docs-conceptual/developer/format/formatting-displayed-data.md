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
ms.openlocfilehash: 9f3a3176ae16ac7c014cadce6b4e856f9bd3b5da
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560388"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="99f84-102">Formatieren von angezeigten Daten</span><span class="sxs-lookup"><span data-stu-id="99f84-102">Formatting Displayed Data</span></span>

<span data-ttu-id="99f84-103">Sie können angeben, wie die einzelnen Datenpunkte in der Listen-, Tabellen-oder breiten Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="99f84-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="99f84-104">Sie können das- `FormatString` Element verwenden, wenn Sie die Elemente der Ansicht definieren, oder Sie können das- `ScriptBlock` Element verwenden, um die- `FormatString` Methode für die Daten aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="99f84-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="99f84-105">Verwenden des FormatString-Elements</span><span class="sxs-lookup"><span data-stu-id="99f84-105">Using the FormatString Element</span></span>

<span data-ttu-id="99f84-106">Im folgenden Beispiel wird der Wert der- `TotalProcessorTime` Eigenschaft des [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekts mit dem FormatString-Element formatiert.</span><span class="sxs-lookup"><span data-stu-id="99f84-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="99f84-107">die- `TotalProcessorTime` Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="99f84-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```
