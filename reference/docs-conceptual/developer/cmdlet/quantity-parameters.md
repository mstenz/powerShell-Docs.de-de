---
title: Mengen Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c0bd8a9-1749-4885-ab24-38c0a4d9f2cb
caps.latest.revision: 6
ms.openlocfilehash: 7a3efc60fcc8729d833f6de070016cfd08cc9b88
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369559"
---
# <a name="quantity-parameters"></a>Mengenparameter

In der folgenden Tabelle werden die empfohlenen Namen und Funktionen für die Anzahl von Parametern aufgelistet.

|Parameter|Funktion|
|---|---|
|**Allen**<br>Datentyp: Boolescher Wert|Implementieren Sie diesen Parameter, sodass `true` angibt, dass statt einer Standard Teilmenge von Ressourcen auf alle Ressourcen reagiert werden soll. Implementieren Sie diesen Parameter, sodass `false` eine Teilmenge der Ressourcen angibt.|
|**Schichtung**<br>Datentyp: Int32|Implementieren Sie diesen Parameter, sodass der Benutzer die Anzahl der zuzuordnenden Elemente angeben kann.|
|**Blockcount**<br>Datentyp: Int64|Implementieren Sie diesen Parameter, sodass der Benutzer die Anzahl der Blöcke angeben kann.|
|**Countdown**<br>Datentyp: Int64|Implementieren Sie diesen Parameter, sodass der Benutzer die Anzahl angeben kann.|
|**Umfang**<br>Datentyp: Schlüsselwort|Implementieren Sie diesen Parameter, sodass der Benutzer den Bereich angeben kann, der verarbeitet werden soll.|

## <a name="see-also"></a>Weitere Informationen

[Cmdlet-Parameter](./cmdlet-parameters.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
