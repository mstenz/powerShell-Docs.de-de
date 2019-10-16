---
title: Ressourcen Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 460c43aa-f5c5-4a1a-a6f2-5e07db143de1
caps.latest.revision: 5
ms.openlocfilehash: 9752570e5c997ef4da56a08df14f39b77ba37a4a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369509"
---
# <a name="resource-parameters"></a>Ressourcenparameter

In der folgenden Tabelle sind die empfohlenen Namen und Funktionen für Ressourcen Parameter aufgeführt. Bei diesen Parametern kann es sich bei den Ressourcen um die Assembly handeln, die die Cmdlet-Klasse enthält, oder um die Host Anwendung, die das Cmdlet ausgeführt hat.

|Parameter|Funktion|
|---|---|
|**Asyl**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer eine Anwendung angeben kann.|
|**Stadtverordneten**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer eine Assembly angeben kann.|
|**Versehen**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer ein Attribut angeben kann.|
|**Klassi**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer eine Microsoft .NET Framework-Klasse angeben kann.|
|**Kombi**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer einen Cluster angeben kann.|
|**Kulturell**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer die Kultur angeben kann, in der das Cmdlet ausgeführt werden soll.|
|**-**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer den Domänen Namen angeben kann.|
|**Antrie**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer einen Laufwerks Namen angeben kann.|
|**Veranstalter**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer einen Ereignis Namen angeben kann.|
|**Berfläche**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer einen Netzwerkschnittstellen Namen angeben kann.|
|**IPAddress**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer eine IP-Adresse angeben kann.|
|**Auftrag**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer einen Auftrag angeben kann.|
|**LiteralPath**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer den Pfad zu einer Ressource angeben kann, wenn Platzhalter Zeichen nicht unterstützt werden. (Verwenden Sie den **path** -Parameter, wenn Platzhalter Zeichen unterstützt werden.)|
|**Mac**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer eine Mac-Adresse (Media Access Controller) angeben kann.|
|**ParentID**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer den übergeordneten Bezeichner angeben kann.|
|**ADS**<br>Datentyp: String, String []|Implementieren Sie diesen Parameter, sodass der Benutzer die Pfade zu einer Ressource angeben kann, wenn Platzhalter Zeichen unterstützt werden. (Verwenden Sie den **literalpath** -Parameter, wenn Platzhalter Zeichen nicht unterstützt werden.) Es wird empfohlen, diesen Parameter zu entwickeln, damit er die vollständige von den Anbietern verwendete `provider:path`-Syntax unterstützt. Außerdem wird empfohlen, dass Sie Sie so entwickeln, dass Sie mit so vielen Anbietern wie möglich funktioniert.|
|**Port**<br>Datentyp: Integer, String|Implementieren Sie diesen Parameter, sodass der Benutzer einen ganzzahligen Wert für das Netzwerk oder einen Zeichen folgen Wert, z. b. "BizTalk", für andere Port Typen angeben kann.|
|**Drucker**<br>Datentyp: Integer, String|Implementieren Sie diesen Parameter, sodass der Benutzer den Drucker angeben kann, den das Cmdlet verwenden soll.|
|**Größe**<br>Datentyp: Int32|Implementieren Sie diesen Parameter, sodass der Benutzer eine Größe angeben kann.|
|**Drüse**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer einen Transaktions Bezeichner (TID) für das Cmdlet angeben kann.|
|**Sorte**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer den Typ der Ressource angeben kann, für die der Betrieb ausgeführt werden soll.|
|**Urne**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer einen Uniform Resource Locator (URL) angeben kann.|
|**User**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer seinen Namen oder den Namen eines anderen Benutzers angeben kann.|

## <a name="see-also"></a>Weitere Informationen

[Cmdlet-Parameter](./cmdlet-parameters.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
