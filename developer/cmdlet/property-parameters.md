---
title: "\"Property\"-Parameter | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d17e0d66-42ea-4e4c-a85b-3ca09b146492
caps.latest.revision: 6
ms.openlocfilehash: cc0742b86a7a36e5712707c077fd1952691f3f4b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067568"
---
# <a name="property-parameters"></a>Eigenschaftenparameter

Die folgende Tabelle enthält die empfohlenen Namen und die Funktionen für "Property"-Parameter an.

|Parameter|Funktion|
|---|---|
|**Count**<br>Datentyp: Int32|Implementieren Sie diesen Parameter, damit der Benutzer auf die Anzahl der zu verarbeitende Objekt angeben kann.|
|**Beschreibung**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer eine Beschreibung für eine Ressource angeben kann.|
|**Von**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer die Verweis-Objekt, rufen Sie Informationen aus angeben kann.|
|**Id**<br>Datentyp: Abhängige Ressourcen|Implementieren Sie diesen Parameter, damit der Benutzer den Bezeichner einer Ressource angeben kann.|
|**Eingabe**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer die Eingabedatei-Spezifikation angeben kann.|
|**Speicherort**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer den Speicherort der Ressource angeben kann.|
|**LogName**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer den Namen der zu verarbeiten, oder verwenden Sie die Protokolldatei angeben kann.|
|**Name**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer den Namen der Ressource angeben kann.|
|**Ausgabe**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer die Ausgabedatei angeben kann.|
|**Besitzer**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer den Namen des Besitzers der Ressource angeben kann.|
|**Eigenschaft**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit die Benutzer angeben können, den Namen oder den Namen der Eigenschaften verwenden.|
|**Reason**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass die Benutzer angeben können, warum dieses Cmdlet aufgerufen wird.|
|**Regex**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass reguläre Ausdrücke verwendet werden, wenn der Parameter angegeben wird. Wenn dieser Parameter angegeben wird, werden Platzhalterzeichen nicht aufgelöst werden.|
|**Geschwindigkeit**<br>Datentyp: Int32|Implementieren Sie diesen Parameter, damit der Benutzer die Baudrate angeben kann. Der Benutzer legt dieser Parameter auf die Geschwindigkeit der Ressource an.|
|**Zustand**<br>Datentyp: Schlüsselwort-array|Implementieren Sie diesen Parameter, damit der Benutzer die Namen der Status, z. B. KEYDOWN angeben kann.|
|**Wert**<br>Datentyp: Objekt|Implementieren Sie diesen Parameter, damit der Benutzer einen Wert, der an das Cmdlet bereitgestellt angeben kann.|
|**Version**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer auf die Version der Eigenschaft angeben kann.|

## <a name="see-also"></a>Weitere Informationen

[Cmdlet-Parameter](./cmdlet-parameters.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
