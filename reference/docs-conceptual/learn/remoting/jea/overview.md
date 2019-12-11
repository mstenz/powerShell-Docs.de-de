---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Übersicht über Just Enough Administration
ms.openlocfilehash: 4b74e5be9558810748a8844a325c8213e1b3ebc9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "70017701"
---
# <a name="just-enough-administration"></a>Just Enough Administration

Just Enough Administration (JEA) ist eine Sicherheitstechnologie, die eine delegierte Verwaltung für sämtliche Elemente ermöglicht, die von PowerShell verwaltet werden. Mit JEA ist Folgendes möglich:

- **Reduzieren Sie die Anzahl von Administratoren auf Ihren Computern**, indem Sie virtuelle Konten oder gruppenverwaltete Dienstkonten nutzen, um privilegierte Aktionen für normale Benutzer auszuführen.
- **Beschränken Sie Benutzeraktionen**, indem Sie die Cmdlets, Funktionen und externen Befehle festlegen, die von Benutzern ausgeführt werden dürfen.
- **Verschaffen Sie sich einen besseren Überblick über die Aktionen Ihrer Benutzer**, indem Sie Aufzeichnungen und Protokolle nutzen, die Ihnen genau zeigen, welche Befehle ein Benutzer während einer Sitzung ausgeführt hat.

**Warum ist JEA wichtig?**

Konten, die mit weitreichenden Berechtigungen zum Verwalten der Server verwendet werden, stellen ein ernsthaftes Sicherheitsrisiko dar. Sollte eines dieser Konten angegriffen werden, kann ihr gesamtes Unternehmen [weiteren Angriffen](https://aka.ms/pth) ausgesetzt sein. Jedes angegriffene Konto eröffnet einem Angreifer neue Zugriffsmöglichkeiten auf weitere Konten und Ressourcen. Dieser kann so unter anderem Geschäftsgeheimnisse stehlen oder einen Denial-of-Service-Angriff starten.

Administrative Berechtigungen sind jedoch nicht leicht zu entfernen. Betrachten Sie das gängigen Szenario, in dem die DNS-Serverrolle auf dem gleichen Computer wie der Active Directory-Domänencontroller installiert ist. Ihre DNS-Administratoren benötigen lokale Administratorrechte zum Beheben von Problemen mit dem DNS-Server. Zu diesem Zweck müssen Sie jedoch Mitglied der Sicherheitsgruppe **Domänenadministratoren** mit weitreichenden Berechtigungen sein. Damit erhalten DNS-Administratoren letztendlich Kontrolle über Ihre gesamte Domäne sowie Zugriff auf alle Ressourcen auf diesem Computer.

JEA löst dieses Problem durch das Prinzip der **geringsten Rechte**. Mit JEA können Sie einen Verwaltungsendpunkt für DNS-Administratoren konfigurieren, die dadurch über Zugriff nur auf PowerShell-Befehle verfügen, die sie für ihre Arbeit benötigen. Das bedeutet, dass Sie ihnen den entsprechenden Zugriff gewähren können, damit ein beschädigter DNS-Cache repariert oder der DNS-Server neu gestartet werden kann, ohne gleichzeitig unbeabsichtigt Berechtigungen für Active Directory, das Durchsuchen des Dateisystems oder die Ausführung potenziell gefährlicher Skripts zu erteilen. Wenn die JEA-Sitzung so konfiguriert ist, dass temporäre privilegierte virtuelle Konten verwendet werden, können Ihre DNS-Administratoren sogar eine Verbindung mit dem Server mithilfe von **Nicht-Admin-** Anmeldeinformationen herstellen und trotzdem Befehle ausführen, für die normalerweise Administratorberechtigungen erforderlich sind. Über JEA können Sie Benutzer von stark privilegierten lokalen bzw. Administratorrollen der Domäne entfernen und sorgfältig steuern, welche Aktionen sie auf jedem Computer ausführen können.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den Anforderungen für die Verwendung von JEA finden Sie im Artikel zu den [Voraussetzungen](prerequisites.md).

## <a name="samples-and-dsc-resource"></a>Beispiele und DSC-Ressource

Beispielkonfigurationen von JEA und die JEA DSC-Ressource finden Sie im [JEA GitHub-Repository](https://github.com/PowerShell/JEA).
