---
title: Format Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369749"
---
# <a name="format-parameters"></a>Formatparameter

In der folgenden Tabelle sind die empfohlenen Namen und Funktionen für Parameter aufgeführt, die zum Formatieren von oder zum Generieren von Daten verwendet werden.

|Parameter|Funktion|
|---|---|
|**Möglichst**<br>Datentyp: Schlüsselwort|Implementieren Sie diesen Parameter, um das Cmdlet-Ausgabeformat anzugeben. Mögliche Werte sind z. b. Text oder Skripts.|
|**Ärer**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, um anzugeben, dass das Cmdlet binäre Werte verarbeitet.|
|**Kodierung**<br>Datentyp: Schlüsselwort|Implementieren Sie diesen Parameter, um den Codierungstyp anzugeben, der unterstützt wird. Mögliche Werte sind z. b. ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte und String.|
|**Zeilenumbruch**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, sodass die Zeilen Umleitungs Zeichen unterstützt werden, wenn der-Parameter angegeben wird.|
|**Kurznamen**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, damit Kurznamen unterstützt werden, wenn der-Parameter angegeben wird.|
|**Breite**<br>Datentyp: Int32|Implementieren Sie diesen Parameter, sodass der Benutzer die Breite des Ausgabegeräts angeben kann.|
|**Anfield**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, sodass Text Wrapping unterstützt wird, wenn der-Parameter angegeben wird.|
## <a name="see-also"></a>Weitere Informationen

[Cmdlet-Parameter](./cmdlet-parameters.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
