---
title: Eingabe Filter Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 7a1582031d27f78bad069f5539408312ccabb3f2
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563873"
---
# <a name="input-filter-parameters"></a>Eingabe von Filterparametern

Ein Cmdlet kann `Filter` -, `Include` -und-Parameter definieren, die `Exclude` den Satz von Eingabe Objekten filtern, auf die sich das Cmdlet auswirkt.

In der Regel wird der Satz von Eingabe Objekten durch einen- `InputObject` ,-oder-Parameter angegeben `Path` `Name` . Ein Cmdlet kann z. b. über einen Parameter verfügen, der `Path` mehrere Pfade mithilfe von Platzhalter Zeichen annimmt, und jeder Pfad verweist auf ein Eingabe Objekt. `Filter` `Include` Mit den Parametern, und werden `Exclude` die Pfade, die das Cmdlet bei jedem Aufruf verwendet, weiter qualifiziert.

## <a name="include-and-exclude-parameters"></a>Einschließen und Ausschließen von Parametern

Der `Include` -Parameter und der- `Exclude` Parameter identifizieren die Objekte, die in den Satz der an das Cmdlet weiter gegebenen Eingabe Objekte eingeschlossen oder ausgeschlossen werden. Verwenden Sie diese Parameter, wenn der Filter in der standardmäßigen Platzhalter Sprache ausgedrückt werden kann. (Weitere Informationen zu Platzhalter Zeichen finden Sie [unter unterstützen von Platzhaltern in Cmdlet-Parametern](./supporting-wildcard-characters-in-cmdlet-parameters.md).) Der- `Include` Parameter enthält alle-Objekte, deren Namen dem Inklusions Filter entsprechen. Der- `Exclude` Parameter schließt alle Objekte aus, deren Namen dem Filter entsprechen.

## <a name="filter-parameter"></a>Filter Parameter

Der- `Filter` Parameter gibt einen Filter an, der nicht in der standardmäßigen Platzhalter Sprache ausgedrückt wird. Beispielsweise können Active Directory Service Interfaces (ADSI) oder SQL-Filter über den Parameter an das Cmdlet übergeben werden `Filter` . In den Cmdlets, die von Windows PowerShell bereitgestellt werden, werden diese Filter von den Windows PowerShell-Anbietern angegeben, die das Cmdlet für den Zugriff auf einen Datenspeicher verwenden. Jeder Anbieter definiert in der Regel seinen eigenen Filter.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>Filterung, wenn kein Satz von Eingabe Objekten angegeben ist

Wenn kein Satz von Eingabe Objekten angegeben ist, bedeutet dies normalerweise, dass alle Objekte gefiltert werden. Weitere Informationen finden Sie unter[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
