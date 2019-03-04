---
title: Geben Sie Filterparameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854466"
---
# <a name="input-filter-parameters"></a>Eingabe von Filterparametern

Ein Cmdlet definieren `Filter`, `Include`, und `Exclude` Parameter, die den Satz von Eingabeobjekten zu filtern, die das Cmdlet wirkt sich auf.

In der Regel wird der Satz von Eingabeobjekten angegeben, indem ein `InputObject`, `Path`, oder `Name` Parameter. Beispielsweise kann ein Cmdlet haben eine `Path` Parameter, der mehreren Pfaden akzeptiert wird, mithilfe von Platzhalterzeichen und jeder Pfad verweist auf ein Eingabeobjekt. Zusammen verwendet, die `Filter`, `Include`, und `Exclude` weitere Parameter qualifizieren Sie die Pfade, die das Cmdlet funktioniert in jedem Aufruf erfolgte.

## <a name="include-and-exclude-parameters"></a>Einschließen und Ausschließen von Parametern

Die `Include` und `Exclude` Parameter zu identifizieren, die Objekte, die aufgenommen werden oder nicht aus dem Satz von Eingabeobjekten an das Cmdlet übergeben. Verwenden Sie diese Parameter aus, wenn der Filter in der standard-Platzhalter-Sprache ausgedrückt werden kann. (Weitere Informationen zu Platzhalterzeichen finden Sie unter [unterstützen Platzhalter in der Cmdlet-Parameter](./supporting-wildcard-characters-in-cmdlet-parameters.md).) Die `Include` Parameter enthält alle Objekte, deren Namen den Filter einschließen entsprechen. Die `Exclude` Parameter schließt alle Objekte, deren Namen mit den Filter übereinstimmen.

## <a name="filter-parameter"></a>Filter-Parameter

Die `Filter` Parameter gibt einen Filter, der nicht ausgedrückt wird, in der standard-Platzhalter-Sprache. Z. B. für die Active Directory Service Interfaces (ADSI) oder SQL-Filter übergeben werden können, an das Cmdlet über die `Filter` Parameter. In den Cmdlets, die von Windows PowerShell bereitgestellt wird werden diese Filter durch die Windows PowerShell-Anbieter angegeben, die mit dem-Cmdlet zu verwenden, um einen Datenspeicher zugreifen. Jeder Anbieter definiert in der Regel einen eigenen Filter.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>Filtern, wenn kein Satz von Eingabeobjekten des Typs angegeben wird

Wenn kein Satz von Eingabeobjekten des Typs angegeben wird, bedeutet dies in der Regel für alle Objekte zu filtern. Weitere Informationen finden Sie unter[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)