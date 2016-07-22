---
title: Verbesserte Pull-Serverregistrierungen
author: jaimeo
contributor: Indhu Sivaramakrishnan
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: d9f7dea63e6541b673ac6be5ccad59368b301440

---

## Verbesserte Pull-Serverregistrierung ##

In früheren Versionen von WMF führten gleichzeitige Registrierungen/Berichterstellungsanfragen an einen DSC-Pull-Server während der Verwendung der ESENT-Datenbank zu einem LCM-Registrierungs- und/oder Berichterstellungsfehler. In solchen Fällen tritt bei den Ereignisprotokollen auf dem Pull-Server der Fehler „Der Instanzname wird bereits verwendet.“ auf.
Die Ursache hierfür ist die Verwendung eines falschen Musters für den Zugriff auf die ESENT-Datenbank in einem Multithread-Szenario. In WMF 5.1 wurde dieses Problem behoben. Gleichzeitige Registrierungen oder Berichterstellungen (mit ESENT-Datenbank) funktionieren einwandfrei in WMF 5.1. Dieses Problem gilt nur für die ESENT-Datenbank und nicht für die OLE DB-Datenbank. 



<!--HONumber=Jul16_HO3-->


