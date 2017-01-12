---
description: 
manager: dongill
ms.topic: article
author: rpsqrd
ms.author: ryanpu
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-12-05
title: Infodatei
ms.technology: powershell
ms.openlocfilehash: f9609f6eb7547c627bc23687c7eb242dd2f5f457
ms.sourcegitcommit: f75fc25411ce6a768596d3438e385c43c4f0bf71
translationtype: HT
---
# <a name="just-enough-administration"></a>Just Enough Administration

Just Enough Administration (JEA) ist eine Sicherheitstechnologie, die eine delegierte Verwaltung für sämtliche Elemente ermöglicht, die in PowerShell verwaltet werden können.
Mit JEA ist Folgendes möglich:

- **Reduzieren Sie die Anzahl von Administratoren auf Ihren Computern**, indem Sie virtuelle Konten nutzen, die privilegierte Aktionen für normale Benutzer ausführen.
- **Beschränken Sie Benutzeraktionen**, indem Sie die Cmdlets, Funktionen und externen Befehle festlegen, die von Benutzern ausgeführt werden dürfen.
- **Verschaffen Sie sich einen besseren Überblick über die Aktionen Ihrer Benutzer**, indem Sie Aufzeichnungen und Protokolle nutzen, die Ihnen genau zeigen, welche Befehle ein Benutzer während einer Sitzung ausgeführt hat.

**Warum ist das so wichtig?**

Konten, die mit weitreichenden Berechtigungen zum Verwalten der Server verwendet werden, stellen ein ernsthaftes Sicherheitsrisiko dar.
Sollte eines dieser Konten angegriffen werden, kann ihr gesamtes Unternehmen [weiteren Angriffen](http://aka.ms/pth) ausgesetzt sein.
Jedes angegriffene Konto eröffnet neue Zugriffsmöglichkeiten auf weitere Konten und Ressourcen. Der Diebstahl von Geschäftsgeheimnissen, ein Denial-of-Service-Angriff und viele weitere Gefahren lauern.

Administrative Berechtigungen sind jedoch nicht leicht zu entfernen.
Betrachten Sie das gängigen Szenario, in dem die DNS-Serverrolle auf dem gleichen Computer wie der Active Directory-Domänencontroller installiert ist.
Ihre DNS-Administratoren müssen lokale Administratorberechtigungen anfordern, um Probleme mit dem DNS-Server beheben zu können. Zu diesem Zweck müssen Sie sie zu Mitgliedern der Sicherheitsgruppe „Domänen-Admins“ machen, die über weitreichende Berechtigungen verfügt.
Damit erhalten DNS-Administratoren letztendlich Kontrolle über Ihre gesamte Domäne sowie Zugriff auf alle Ressourcen auf diesem Computer.

JEA kann Sie bei diesem Problem unterstützen, indem Sie das Prinzip der *geringsten Berechtigungen* befolgen.
Mit JEA können Sie einen Verwaltungsendpunkt für DNS-Administratoren konfigurieren, die dadurch über Zugriff auf alle Befehle verfügen, die sie für ihre Arbeit benötigen – mehr jedoch nicht.
Das bedeutet, dass Sie ihnen den entsprechenden Zugriff gewähren können, damit ein beschädigter DNS-Cache repariert oder der DNS-Server neu gestartet werden kann, ohne gleichzeitig unbeabsichtigt Berechtigungen für Active Directory, das Durchsuchen des Dateisystems oder die Ausführung potenziell gefährlicher Skripts zu erteilen.
Wenn die JEA-Sitzung so konfiguriert ist, dass temporäre privilegierte virtuelle Konten verwendet werden, können Ihre DNS-Administratoren sogar eine Verbindung mit dem Server mithilfe von *Nicht-Admin-*Anmeldeinformationen herstellen und trotzdem Befehle ausführen, für die normalerweise Administratorberechtigungen erforderlich sind.
Über diese Funktion können Sie Benutzer von stark privilegierten lokalen bzw. Administratorrollen der Domäne entfernen und stattdessen sorgfältig steuern, welche Aktionen sie auf jedem Computer ausführen dürfen.

## <a name="get-started-with-jea"></a>Erste Schritte mit JEA

Starten Sie noch heute mithilfe von JEA auf jedem Computer, auf dem Windows Server 2016 oder Windows 10 ausgeführt wird.
Sie können JEA auch unter älteren Betriebssystemen mit einem Windows Management Framework-Update ausführen.
Informationen zu den Anforderungen für die Verwendung von JEA sowie zum Erstellen, Verwenden und Überprüfen eines JEA-Endpunkts finden Sie unter folgenden Themen:

- [Voraussetzungen](prerequisites.md): In diesem Thema wird die Einrichtung Ihrer Umgebung für die Verwendung mit JEA erklärt.
- [Rollenfunktionen](role-capabilities.md): Dieses Thema erläutert, wie Sie Rollen erstellen, die festlegen, wozu ein Benutzer in einer JEA-Sitzung berechtigt ist.
- [JEA Session Configurations (JEA-Sitzungskonfigurationen)](session-configurations.md): Dieses Thema legt dar, wie Sie JEA-Endpunkte konfigurieren, die den Benutzer Rollen zuordnen und die JEA-Identität bestimmen.
- [Registering JEA Configurations (Registrieren von JEA-Konfigurationen)](register-jea.md): In diesem Thema erfahren Sie, wie Sie einen JEA-Endpunkt erstellen und für Benutzer zur Verfügung stellen, die eine Verbindung herstellen.
- [Verwenden von JEA](using-jea.md): In diesem Thema lernen Sie die verschiedenen Verwendungsmöglichkeiten von JEA kennen.
- [JEA Security Considerations (JEA-Sicherheitsaspekte)](security-considerations.md): Dieses Thema enthält bewährte Sicherheitsmethoden und Auswirkungen der einzelnen JEA-Konfigurationsoptionen.
- [Audit and Report on JEA (Überwachen und Erstellen von Berichten zu JEA)](audit-and-report.md): In diesem Thema erfahren Sie, wie Sie JEA-Endpunkte überwachen und Berichte dazu erstellen.