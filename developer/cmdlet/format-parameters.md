---
title: Formatieren von Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068112"
---
# <a name="format-parameters"></a>Formatparameter

Die folgende Tabelle enthält die empfohlenen Namen und Funktionen für Parameter, die zum Formatieren von oder zum Generieren von Daten verwendet werden.

|Parameter|Funktion|
|---|---|
|**als**<br>Datentyp: Schlüsselwort|Implementieren Sie diesen Parameter, um die Cmdlet-Ausgabeformat angeben. Mögliche Werte möglicherweise z. B. Text oder ein Skript.|
|**Binary**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, um anzugeben, dass das Cmdlet binäre Werte behandelt.|
|**Encoding**<br>Datentyp: Schlüsselwort|Implementieren Sie diesen Parameter, um den Typ der Codierung angeben, der unterstützt wird. Mögliche Werte möglicherweise z. B. ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte und Zeichenfolge.|
|**NewLine**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass die neue Zeilenumbruchzeichen unterstützt werden, wenn der Parameter angegeben wird.|
|**ShortName**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass Kurznamen unterstützt werden, wenn der Parameter angegeben wird.|
|**Width**<br>Datentyp: Int32|Implementieren Sie diesen Parameter, damit der Benutzer die Breite des Ausgabegeräts angeben kann.|
|**wickeln**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass Umbrechen von Text unterstützt, wenn der Parameter angegeben wird.|
## <a name="see-also"></a>Weitere Informationen

[Cmdlet-Parameter](./cmdlet-parameters.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
