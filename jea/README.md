---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: Infodatei
ms.technology: powershell
ms.openlocfilehash: b0ef4ff685b82e1a4e9ab83a45736720df7b39a2
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="just-enough-administration"></a>Just Enough Administration
Just Enough Administration (JEA) ist eine Sicherheitstechnologie, die eine delegierte Verwaltung für sämtliche Elemente ermöglicht, die in PowerShell verwaltet werden können.
Mit JEA ist Folgendes möglich:
- **Reduzieren Sie die Anzahl von Administratoren auf Ihren Computern**, indem Sie virtuelle Konten nutzen, die privilegierte Aktionen für normale Benutzer ausführen.
- **Beschränken Sie Benutzeraktionen**, indem Sie die Cmdlets, Funktionen und externen Befehle festlegen, die von Benutzern ausgeführt werden dürfen.
- **Verschaffen Sie sich genauere Kenntnis darüber, was Ihre Benutzer tun**, indem Sie Aufzeichnungen mitschneiden, die Ihnen genau zeigen, welche Befehle ein Benutzer während einer Sitzung ausgeführt hat.

**Warum ist das so wichtig?**  
Betrachten Sie das gängige Szenario, bei dem Ihre DNS-Server mit Ihren Active Directory-Domänencontrollern zusammengestellt sind.
Ihre DNS-Administratoren müssen lokale Administratorrechte besitzen, um Probleme mit dem DNS-Server beheben zu können. Zu diesem Zweck müssen Sie sie zu Mitgliedern der Sicherheitsgruppe „Domänen-Admins“ machen, die über weit reichende Berechtigungen verfügt.
Damit erhalten DNS-Administratoren letztendlich Kontrolle über Ihre gesamte Domäne sowie Zugriff auf alle Ressourcen auf diesem Computer.

Mit JEA können Sie eine Rolle für die DNS-Administratoren konfigurieren, die ihnen Zugriff auf alle Befehle gewährt, die sie für ihre Arbeit benötigen – mehr jedoch nicht.
Das bedeutet, dass Sie ihnen den entsprechenden Zugriff gewähren können, damit ein beschädigter DNS-Cache repariert werden kann, ohne gleichzeitig unbeabsichtigt Berechtigungen für Active Directory, das Durchsuchen des Dateisystems oder die Ausführung potenziell gefährlicher Skripts zu erteilen.
Wenn die JEA-Sitzung so konfiguriert ist, dass einmalige privilegierte virtuelle Konten verwendet werden, können Ihre DNS-Administratoren überdies eine Verbindung mit dem Server als *nicht privilegierte* Benutzer herstellen und trotzdem Befehle ausführen, für die Berechtigungen erforderlich sind.

## <a name="availability"></a>Verfügbarkeit
JEA wird parallel zu Windows Server 2016 entwickelt und steht in älteren Windows-Versionen über Updates des Windows Management Frameworks zur Verfügung.
Das aktuelle JEA-Release ist auf den folgenden Plattformen verfügbar:

**Windows Server**
- Windows Server 2016 Technical Preview 4 und höher
- Windows Server 2012 R2, 2012 und 2008 R2\* mit installiertem [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395)

**Windows Client**
- Windows 10 mit installiertem November-Update (1511)
- Windows 8.1, 8 und 7\* mit installiertem [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395)

\* Unterstützung für virtuelle JEA-Sitzungen steht in Windows Server 2008 R2 und Windows 7 derzeit nicht zur Verfügung.


## <a name="explore-the-experience-guide"></a>Einführungsleitfaden zu JEA
Sind Sie bereit zu erfahren, wie Sie selbst einen JEA-Endpunkt erstellen, bereitstellen und verwenden?

Dieser Leitfaden bietet einen schnellen Einstieg und vermittelt anhand eines vorgefertigten JEA-Endpunkts eine Vorstellung von der Endbenutzererfahrung. Anschließend führt der Leitfaden Sie durch den Prozess der Neuerstellung eines Endpunkts, um dabei Konzepte wie Sitzungskonfigurationen und Rollenfunktionen zu erläutern.

1.  [Einführung](introduction.md)   
Dieses Kapitel bietet eine kurze Übersicht darüber, warum JEA für Sie interessant ist.

2.  [Voraussetzungen](prerequisites.md)  
In diesem Kapitel wird die Einrichtung Ihrer Umgebung erklärt.

3.  [Verwenden von JEA](using-jea.md)  
Dieses Kapitel erleichtert Ihnen den Einstieg, indem die JEA-Benutzererfahrung von Operatoren erläutert wird.

4.  [Neuerstellen der Demo](remake-the-demo-endpoint.md)  
Erstellen Sie eine JEA-Sitzungskonfiguration von Grund auf.

5.  [Rollenfunktionen](role-capabilities.md)  
Erfahren Sie, wie Sie JEA-Funktionen mit JEA-Rollenfunktionsdateien anpassen.

6.  [End-to-End – Active Directory](end-to-end---active-directory.md)  
Erstellen Sie einen völlig neuen Endpunkt zur Verwaltung von Active Directory.

7.  [Bereitstellung und Wartung mehrerer Computer](multi-machine-deployment-and-maintenance.md)  
Erfahren Sie, wie sich die Bereitstellung und die Dokumenterstellung in Abhängigkeit vom Umfang ändern.

8.  [Berichterstellung zu JEA](reporting-on-jea.md)  
Erfahren Sie, wie Sie alle JEA-Aktionen und die gesamte Infrastruktur überprüfen und Berichte dafür erstellen.

9.  Anhänge
  - [Wichtige Konzepte in diesem Leitfaden](key-concepts-used-throughout-this-guide.md)  
  -  [Erstellen eines Domänencontrollers](creating-a-domain-controller.md)  
  -  [Blacklists](on-blacklisting.md)  
  -  [Überlegungen zum Einschränken von Befehlen](considerations-when-limiting-commands.md)  
  -  [Häufige Fehler bei Rollenfunktionen](common-role-capability-pitfalls.md)

## <a name="start-authoring-your-own-jea-endpoints"></a>Ihre ersten eigenen JEA-Endpunkte
Die Erstellung eines JEA-Endpunkts ist ganz einfach – Sie benötigen nur ein JEA-fähiges System und einen Text-Editor (wie z. B. die PowerShell ISE).
Ein guter Tipp für den Einstieg: Erstellen Sie Gerüstdateien mithilfe von [`New-PSRoleCapabilityFile -Path <path>`](https://technet.microsoft.com/library/mt631422.aspx) und [`New-PSSessionConfigurationFile -Path <Path>`](https://technet.microsoft.com/library/mt631422.aspx), ohne weitere Argumente.
Diese Gerüstdateien enthalten alle anwendbaren Konfigurationsfelder sowie nützliche Kommentare, die erklären, wozu welches Feld verwendet werden kann.

Um die Erstellung von JEA-Endpunkten noch einfacher zu gestalten, lesen Sie den Blog [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx). In diesem Blog finden Sie eine GUI, mit deren Hilfe Sie Sitzungskonfigurations- und Rollenfunktionsdateien erstellen können.
Die GUI unterstützt sogar die Erstellung von Rollenfunktionen basierend auf PowerShell-Protokollen, sodass Sie mit den Befehlen beginnen können, die Ihre Benutzer regelmäßig für ihre Arbeit ausführen.

