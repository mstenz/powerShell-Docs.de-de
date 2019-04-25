---
title: Ressourcenparameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 460c43aa-f5c5-4a1a-a6f2-5e07db143de1
caps.latest.revision: 5
ms.openlocfilehash: 9752570e5c997ef4da56a08df14f39b77ba37a4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067449"
---
# <a name="resource-parameters"></a>Ressourcenparameter

Die folgende Tabelle enthält die empfohlenen Namen und die Funktionen für die Ressourcenparameter. Für diese Parameter können möglicherweise die Ressourcen der Assembly, die die Cmdlet-Klasse enthält die hostanwendung, die das Cmdlet ausgeführt wird.

|Parameter|Funktion|
|---|---|
|**Application**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer eine Anwendung angeben kann.|
|**Assembly**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer auf eine Assembly angeben kann.|
|**Attribut**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer auf ein Attribut angeben kann.|
|**Klasse**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer auf Microsoft .NET Framework-Klasse angeben kann.|
|**Cluster**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer einen Cluster angeben kann.|
|**Kultur**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer die Kultur, in dem das Cmdlet ausführen, angeben kann.|
|**Domain**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer den Domänennamen angeben kann.|
|**Drive**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer einen Laufwerknamen angeben kann.|
|**Ereignis**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer einen Ereignisnamen angeben kann.|
|**Schnittstelle**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer eine Netzwerkschnittstellenname angeben kann.|
|**IpAddress**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer eine IP-Adresse angeben kann.|
|**Job**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer einen Auftrag angeben kann.|
|**LiteralPath**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer den Pfad zu einer Ressource angeben kann, wenn Platzhalterzeichen nicht unterstützt werden. (Verwenden der **Pfad** Parameter an, wenn ein Platzhalterzeichen unterstützt werden.)|
|**Mac**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer eine Media Access-Controller (MAC)-Adresse angeben kann.|
|**ParentId**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer den übergeordneten Bezeichner angeben kann.|
|**Pfad**<br>Datentyp: String, String[]|Implementieren Sie diesen Parameter, sodass der Benutzer die Pfade für eine Ressource angeben kann, wenn Platzhalterzeichen unterstützt werden. (Verwenden der **LiteralPath** Parameter an, wenn Platzhalterzeichen nicht unterstützt werden.) Es wird empfohlen, diesen Parameter zu entwickeln, damit sie die vollständige unterstützt `provider:path` Syntax, die von Anbietern verwendet. Außerdem wird empfohlen, dass Sie es entwickeln, die Funktionsweise mit wie vielen Anbietern wie möglich.|
|**Port**<br>Datentyp: Ganze Zahl, Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer einen ganzzahligen Wert für das Netzwerk oder ein String-Wert, z. B. "Biztalk" für andere Typen über Port angeben kann.|
|**Printer**<br>Datentyp: Ganze Zahl, Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer auf den Drucker, für das-Cmdlet verwenden angeben kann.|
|**Größe**<br>Datentyp: Int32|Implementieren Sie diesen Parameter, damit der Benutzer auf eine Größe angeben kann.|
|**TID**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer eine Transaktions-ID (TID) für das Cmdlet angeben kann.|
|**Typ**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer den Typ der Ressource, mit denen Sie arbeiten angeben kann.|
|**URL**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer einen Uniform Resource Locator (URL) angeben kann.|
|**User**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit die Benutzer ihren Namen oder den Namen eines anderen Benutzers angeben können.|

## <a name="see-also"></a>Weitere Informationen

[Cmdlet-Parameter](./cmdlet-parameters.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
