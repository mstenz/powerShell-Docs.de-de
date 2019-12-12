---
title: Datums-und Uhrzeit Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 5b1f093de5db364ac806e58c4ed8dbf2948cb6c6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369789"
---
# <a name="date-and-time-parameters"></a>Datums- und Zeitparameter

In der folgenden Tabelle werden die empfohlenen Namen und Funktionen für Parameter aufgelistet, die Datums-und Uhrzeit Informationen verarbeiten. Datums-und Uhrzeit Parameter werden normalerweise verwendet, um aufzuzeichnen, wann etwas erstellt oder auf das zugegriffen wird.

|Parameter|Funktion|
|---|---|
|**Auf**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, sodass das Cmdlet bei Angabe des-Cmdlets mit den Ressourcen arbeiten kann, auf die basierend auf dem von den Parametern **before** und **after** angegebenen Datum und der angegebenen Uhrzeit zugegriffen wurde. Wenn dieser Parameter angegeben wird, dürfen die **erstellten** und **geänderten** Parameter nicht angegeben werden.|
|**Nach**<br>Datentyp: DateTime|Implementieren Sie diesen Parameter, um das Datum und die Uhrzeit anzugeben, nach der das Cmdlet verwendet wurde. Damit der **after** -Parameter funktioniert, muss das Cmdlet auch über einen Parameter verfügen, auf den **zugegriffen**, **erstellt**oder **geändert** wurde. Und dieser Parameter muss auf **true** festgelegt werden, wenn das Cmdlet aufgerufen wird.|
|**vor**<br>Datentyp: DateTime|Implementieren Sie diesen Parameter, um das Datum und die Uhrzeit anzugeben, zu der das Cmdlet verwendet wurde. Damit der **before** -Parameter funktioniert, muss das Cmdlet auch über einen **Zugriffs**-, **Erstellungs** **-oder Änderungs** Parameter verfügen. Und dieser Parameter muss auf **true** festgelegt werden, wenn das Cmdlet aufgerufen wird.|
|**Created** (Erstellt)<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, sodass das Cmdlet bei Angabe des-Cmdlets mit den Ressourcen arbeitet, die basierend auf dem von den Parametern **before** und **after** angegebenen Datum und der angegebenen Uhrzeit erstellt wurden. Wenn dieser Parameter angegeben wird, dürfen **die Parameter,** auf die **zugegriffen** wird, nicht angegeben werden.|
|**Exact**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, sodass der Ressourcen Begriff bei der Angabe genau mit dem Ressourcennamen übereinstimmen muss. Wenn der-Parameter nicht angegeben wird, müssen der Ressourcen Begriff und der Name nicht exakt übereinstimmen.|
|**Geändert**<br>Datentyp: DateTime|Implementieren Sie diesen Parameter, sodass das Cmdlet bei Angabe des Datums und der Uhrzeit, die durch die Parameter **before** und **after** festgelegt wurden, auf Ressourcen angewendet wird, die geändert wurden. Wenn dieser Parameter angegeben wird, dürfen **die Parameter,** auf die **zugegriffen** wird, nicht angegeben werden.|
## <a name="see-also"></a>Weitere Informationen

[Cmdlet-Parameter](./cmdlet-parameters.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
