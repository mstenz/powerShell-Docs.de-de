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
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364389"
---
# <a name="input-filter-parameters"></a>Eingabe von Filterparametern

Ein Cmdlet kann die Parameter "`Filter`", "`Include`" und "`Exclude`" definieren, die den Satz von Eingabe Objekten filtern, auf die das Cmdlet wirkt.

In der Regel wird der Satz von Eingabe Objekten von einem `InputObject`-, `Path`-oder `Name`-Parameter angegeben. Beispielsweise kann ein Cmdlet über einen `Path`-Parameter verfügen, der mehrere Pfade mithilfe von Platzhalter Zeichen annimmt, und jeder Pfad verweist auf ein Eingabe Objekt. Wenn die Parameter "`Filter`", "`Include`" und "`Exclude`" zusammen verwendet werden, qualifizieren Sie die Pfade, die das Cmdlet bei jedem Aufruf verwendet.

## <a name="include-and-exclude-parameters"></a>Einschließen und Ausschließen von Parametern

Mit den Parametern "`Include`" und "`Exclude`" werden die Objekte identifiziert, die in den an das Cmdlet weiter gegebenen Satz von Eingabe Objekten eingeschlossen oder ausgeschlossen werden. Verwenden Sie diese Parameter, wenn der Filter in der standardmäßigen Platzhalter Sprache ausgedrückt werden kann. (Weitere Informationen zu Platzhalter Zeichen finden Sie [unter unterstützen von Platzhaltern in Cmdlet-Parametern](./supporting-wildcard-characters-in-cmdlet-parameters.md).) Der `Include`-Parameter schließt alle Objekte ein, deren Namen dem Inklusions Filter entsprechen. Der Parameter "`Exclude`" schließt alle Objekte aus, deren Namen dem Filter entsprechen.

## <a name="filter-parameter"></a>Filter Parameter

Der Parameter "`Filter`" gibt einen Filter an, der nicht in der standardmäßigen Platzhalter Sprache ausgedrückt wird. Beispielsweise können Active Directory-Dienst Schnittstellen (ADSI) oder SQL-Filter über den `Filter`-Parameter an das Cmdlet übergeben werden. In den Cmdlets, die von Windows PowerShell bereitgestellt werden, werden diese Filter von den Windows PowerShell-Anbietern angegeben, die das Cmdlet für den Zugriff auf einen Datenspeicher verwenden. Jeder Anbieter definiert in der Regel seinen eigenen Filter.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>Filterung, wenn kein Satz von Eingabe Objekten angegeben ist

Wenn kein Satz von Eingabe Objekten angegeben ist, bedeutet dies normalerweise, dass alle Objekte gefiltert werden. Weitere Informationen finden Sie unter[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)