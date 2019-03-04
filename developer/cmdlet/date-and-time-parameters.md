---
title: Datums- und Zeitparametern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 5b1f093de5db364ac806e58c4ed8dbf2948cb6c6
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251352"
---
# <a name="date-and-time-parameters"></a>Datums- und Zeitparameter

Die folgende Tabelle enthält die empfohlenen Namen und Funktionen für Parameter, die Datums-und Uhrzeitinformationen behandelt. Datums- und Uhrzeitparameter werden normalerweise verwendet, um aufzuzeichnen, wenn etwas erstellt oder auf die zugegriffen wird.

|Parameter|Funktion|
|---|---|
|**Accessed**<br>Datentyp: SwitchParameter|Dieser Parameter implementiert, sodass wenn er angegeben wird, mit dem Cmdlet funktionieren auf die Ressourcen, die auf die zugegriffen wurde, die auf das Datum und die angegebene Zeit basiert die **vor** und **nach** Parameter. Wenn dieser Parameter angegeben wird, die **erstellt** und **"geändert"** müssen der Parameter nicht angegeben werden.|
|**After**<br>Datentyp: DateTime|Implementieren Sie diesen Parameter zum Angeben von Datum und Uhrzeit, nach dem das Cmdlet verwendet wurde. Für die **nach** Parameter funktioniert, muss auch das Cmdlet eine **Accessed**, **erstellt**, oder **"geändert"** Parameter. Und, diesen Parameter muss festgelegt werden, um **"true"** Wenn das-Cmdlet aufgerufen wird.|
|**Vor dem**<br>Datentyp: DateTime|Implementieren Sie diesen Parameter zum Angeben von Datum und Uhrzeit, die vor dem das Cmdlet verwendet wurde. Für die **vor** Parameter funktioniert, muss auch das Cmdlet eine **Accessed**, **erstellt**, oder **"geändert"** Parameter. Und, diesen Parameter muss festgelegt werden, um **"true"** Wenn das-Cmdlet aufgerufen wird.|
|**Erstellt**<br>Datentyp: SwitchParameter|Dieser Parameter implementiert, sodass wenn er angegeben wird, mit dem Cmdlet funktionieren auf die Ressourcen, die erstellt wurden, die auf das Datum und die angegebene Zeit basiert die **vor** und **nach** Parameter. Wenn dieser Parameter angegeben wird, die **Accessed** und **"geändert"** Parameter darf nicht angegeben werden.|
|**Genaue**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass wenn er den Begriff der Ressource angegeben ist der Ressourcenname genau übereinstimmen muss. Wenn der Parameter nicht angegeben ist müssen den Begriff der Ressource und den Namen nicht exakt übereinstimmen.|
|**Geändert**<br>Datentyp: DateTime|Dieser Parameter implementiert, sodass wenn er angegeben wird, mit dem Cmdlet funktionieren für Ressourcen, die geändert wurden, die auf das Datum und die angegebene Zeit basiert die **vor** und **nach** Parameter. Wenn dieser Parameter angegeben wird, die **Accessed** und **erstellt** Parameter darf nicht angegeben werden.|
## <a name="see-also"></a>Weitere Informationen

[Cmdlet-Parameter](./cmdlet-parameters.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
