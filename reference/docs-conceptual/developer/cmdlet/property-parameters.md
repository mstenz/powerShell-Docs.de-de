---
title: Eigenschafts Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d17e0d66-42ea-4e4c-a85b-3ca09b146492
caps.latest.revision: 6
ms.openlocfilehash: cc0742b86a7a36e5712707c077fd1952691f3f4b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369579"
---
# <a name="property-parameters"></a>Eigenschaftenparameter

In der folgenden Tabelle sind die empfohlenen Namen und Funktionen für Eigenschafts Parameter aufgeführt.

|Parameter|Funktion|
|---|---|
|**Countdown**<br>Datentyp: Int32|Implementieren Sie diesen Parameter, sodass der Benutzer die Anzahl der zu verarbeitenden Objekte angeben kann.|
|**Beschreibung**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer eine Beschreibung für eine Ressource angeben kann.|
|**Von**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer das Verweis Objekt angeben kann, aus dem Informationen abgeleitet werden sollen.|
|**Name**<br>Datentyp: Ressourcen abhängig|Implementieren Sie diesen Parameter, sodass der Benutzer den Bezeichner einer Ressource angeben kann.|
|**Der**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer die Eingabedatei Spezifikation angeben kann.|
|**Speicherort**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer den Speicherort der Ressource angeben kann.|
|**LogName**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer den Namen der Protokolldatei angeben kann, die verarbeitet oder verwendet werden soll.|
|**Benennen**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer den Namen der Ressource angeben kann.|
|**Ausgeben**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer die Ausgabedatei angeben kann.|
|**Eigentor**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer den Namen des Besitzers der Ressource angeben kann.|
|**Property**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer den Namen oder die Namen der zu verwendenden Eigenschaften angeben kann.|
|**Weshalb**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer angeben kann, warum dieses Cmdlet aufgerufen wird.|
|**Regex**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, sodass reguläre Ausdrücke verwendet werden, wenn der-Parameter angegeben wird. Wenn dieser Parameter angegeben wird, werden Platzhalter Zeichen nicht aufgelöst.|
|**Beschleunigt**<br>Datentyp: Int32|Implementieren Sie diesen Parameter, sodass der Benutzer die Baudrate angeben kann. Der Benutzer legt diesen Parameter auf die Geschwindigkeit der Ressource fest.|
|**Land**<br>Datentyp: Schlüsselwort Array|Implementieren Sie diesen Parameter, sodass der Benutzer die Namen von Zuständen angeben kann, z. b. KeyDown.|
|**Wert**<br>Datentyp: Object|Implementieren Sie diesen Parameter, sodass der Benutzer einen Wert angeben kann, der für das Cmdlet bereitgestellt werden soll.|
|**Version**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer die Version der Eigenschaft angeben kann.|

## <a name="see-also"></a>Weitere Informationen

[Cmdlet-Parameter](./cmdlet-parameters.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
