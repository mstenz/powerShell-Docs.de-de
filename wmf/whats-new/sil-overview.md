---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Protokollierung des Softwarebestands (Software Inventory Logging, SIL)
ms.openlocfilehash: b12cfc4ae1e505bbc4d47596bed9352ce53a98f2
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855435"
---
# <a name="software-inventory-logging-sil"></a>Protokollierung des Softwarebestands (Software Inventory Logging, SIL)

> [!IMPORTANT]
> Beim Installieren von WMF 5.x auf einem Server mit Windows Server 2012 R2, auf dem die Protokollierung des Softwarebestands (SIL) bereits ausgeführt wird, muss das Cmdlet „Start-SilLogging“ nach der Installation von WMF ein Mal ausgeführt werden, da der Installationsvorgang das Feature „Protokollierung des Softwarebestands“ fälschlicherweise beendet.

Durch die Protokollierung des Softwarebestands sollen die Betriebskosten für das Abrufen genauer Informationen zu der lokal auf einem Server bereitgestellten Microsoft-Software reduziert werden, vor allem aber für das Abrufen dieser Informationen von zahlreichen Servern in einer IT-Umgebung (sofern die Software in der gesamten IT-Umgebung installiert ist und ausgeführt wird). Sofern eingerichtet, können Sie diese Daten an einen Aggregationsserver weiterleiten und die Protokolldaten mittels eines einheitlichen, automatischen Prozesses zentral sammeln.

Sie können Daten zum Softwarebestand auch über ein direktes Abfragen aller Computer protokollieren. Doch mit der Protokollierung des Softwarebestands können (durch die Nutzung einer von jedem Server ausgelösten Weiterleitung) Probleme bei der Serverermittlung überwunden werden, die für viele Software-Inventur- und Ressourcenverwaltungsszenarien typisch sind. Die Software-Inventurprotokollierung verwendet SSL, um Daten zu schützen, die über HTTPS an einen Aggregationsserver weitergeleitet werden. Da die Daten an zentraler Stelle gespeichert werden, können sie einfacher analysiert, bearbeitet und freigegeben werden.

Im Rahmen der Funktionalität des Features werden keine Daten an Microsoft gesendet. Die Daten und die Funktionalität der Softwareinventurprotokollierung sind ausschließlich zur Verwendung durch den lizenzierten Besitzer der Serversoftware und durch Administratoren gedacht.

Weitere Informationen und Dokumentation zu Cmdlets zur Protokollierung des Softwarebestands finden Sie unter [Verwalten der Protokollierung des Softwarebestands in Windows Server 2012 R2](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11)).
