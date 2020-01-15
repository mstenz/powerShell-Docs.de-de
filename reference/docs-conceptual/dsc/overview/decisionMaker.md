---
ms.date: 10/11/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: 'Desired State Configuration (DSC): Übersicht für Entscheidungsträger'
ms.openlocfilehash: bb73ee8fe636272f99989aa45712fe34fedad617
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870794"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Desired State Configuration (DSC): Übersicht für Entscheidungsträger

Dieses Dokument ist keine technische Anleitung, sondern beschreibt die geschäftlichen Vorteile von PowerShell Desired State Configuration (DSC).

## <a name="what-is-dsc"></a>Was ist DSC?

PowerShell DSC ist eine in Windows integrierte Konfigurationsverwaltungsplattform, die auf offenen Standards basiert. DSC ist flexibel genug, in jeder Phase des Bereitstellungslebenszyklus (Entwicklung, Test, Vorproduktion, Produktion) sowie bei horizontaler Skalierung zuverlässig und konsistent zu funktionieren.

Eine Hauptfunktion von DSC sind [Konfigurationen](../configurations/configurations.md). Eine Konfiguration ist ein PowerShell-Skript, das eine aus Computern (Knoten) bestehende Umgebung mit bestimmten Merkmalen beschreibt. Diese Merkmale können so einfach wie das Sicherstellen, dass ein bestimmtes Windows-Feature aktiviert ist, oder so komplex wie das Bereitstellen von SharePoint sein.

DSC verfügt über integrierte Überwachungs- und Berichterstellungsfunktionen. Wenn ein System nicht mehr kompatibel ist, kann DSC eine Warnung auslösen und agieren, um das System zu korrigieren.

## <a name="benefits-of-using-dsc"></a>Die Vorteile von DSC

Das Design vereinfacht das Lesen, Speichern und Aktualisieren von Konfigurationen. Konfigurationen definieren den Zustand von Zielgeräten, anstatt Anweisungen zu schreiben, wie diese in den jeweiligen Zustand versetzt werden können. Dank dieser Faktoren ist der Aufwand wesentlich geringer, eine Konfiguration über DSC zu erlernen, zu übernehmen, zu implementieren und zu warten.

Eine Konfiguration zu erstellen bedeutet, komplexe Bereitstellungsschritte als **kompakte Lösung** an einem zentralen Ort zu erfassen. Durch Konfigurationen wird die wiederholte Bereitstellung bestimmter Computergruppen wesentlich weniger fehleranfällig. Zudem sind Bereitstellungen schneller und zuverlässiger, sodass sich komplexe Bereitstellungen schneller realisieren lassen.

Konfigurationen können über den [PowerShell-Katalog](https://powershellgallery.com) freigegeben werden. Es ist möglich, dass bereits gängige Szenarien und bewährte Methoden für die Aufgaben vorhanden sind, die Sie ausführen müssen.

## <a name="dsc-and-devops"></a>DSC und DevOps

DSC wurde mit Fokus auf [DevOps](/archive/blogs/ashleymcglone/devops-for-n00bs-ie-windows-people-like-me) entworfen. DevOps ist eine Kombination aus Benutzern, Prozessen und Tools, die eine schnelle Bereitstellung und Iteration ermöglicht, um sowohl internen als auch externen Endbenutzern einen Mehrwert zu bieten. Wenn eine Umgebung durch eine einzige Konfiguration definiert wird, können Entwickler ihre Anforderungen in die Konfiguration programmieren und diese in die Quellcodeverwaltung einchecken. Betriebsteams können den Code dann bereitstellen, ohne fehleranfällige manuelle Prozesse durchlaufen zu müssen.

Konfigurationen sind [datengesteuert](../configurations/configData.md). Durch definierte Daten ist es für Betriebsteams leichter, Umgebungen ohne Eingriffe von Entwicklern zu erkennen und zu ändern.

## <a name="dsc-on-premises-and-off-premises"></a>DSC lokal und extern

DSC kann zum Verwalten lokaler und externer Bereitstellungen verwendet werden. Für lokale Lösungen bietet DSC einen [Pullserver](../pull-server/pullServer.md) zum Zentralisieren der Verwaltung von Computern und zum Melden ihres Status. Für externe Cloudlösungen kann DSC überall dort eingesetzt werden wo auch Windows verwendet werden kann.
Es gibt bestimmte Angebote von Azure, die auf DSC basieren, wie z. B. [Azure Automation ](/azure/automation), mit dem die DSC-Berichterstellung zentralisiert wird.

## <a name="dsc-and-compatibility"></a>DSC und Kompatibilität

DSC wurde in Windows Server 2012 R2 eingeführt, ist aber über das Windows Management Framework (WMF) auch für ältere Betriebssysteme verfügbar. Weitere Informationen zu WMF finden Sie unter [Windows Management Framework](/powershell/scripting/wmf/overview).

DSC kann zum Verwalten von Linux verwendet werden. Weitere Informationen finden Sie unter [Erste Schritte mit DSC für Linux](../getting-started/lnxGettingStarted.md).
