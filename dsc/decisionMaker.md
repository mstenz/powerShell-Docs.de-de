---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 'Desired State Configuration (DSC): Übersicht für Entscheidungsträger'
ms.openlocfilehash: 7c36aa5fadeab8bcb381f316288d102b5ce402e2
ms.sourcegitcommit: ac20e0faaa37142e9c6e4507a21df2f4a3fdbece
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339836"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Desired State Configuration (DSC): Übersicht für Entscheidungsträger

In diesem Dokument werden die Unternehmensvorteile der Verwendung von Windows PowerShell Desired State Configuration (DSC) beschrieben. Es handelt sich nicht um ein technisches Handbuch.

## <a name="what-is-desired-state-configuration"></a>Was ist „Desired State Configuration“?

PowerShell Desired State Configuration ist eine in Windows integrierte Konfigurationsverwaltungsplattform, die auf offenen Standards basiert. DSC ist flexibel genug, in jeder Phase des Bereitstellungslebenszyklus (Entwicklung, Test, Präproduktion, Produktion) sowie bei horizontaler Skalierung zuverlässig und konsistent zu funktionieren.

Eine Hauptfunktion von DSC sind [Konfigurationen](configurations.md).
Eine Konfiguration ist ein einfach zu lesendes Dokument, das eine aus Computern („Knoten“) bestehende Umgebung mit bestimmten Merkmalen beschreibt.
Diese Merkmale können so einfach wie das Sicherstellen, dass ein bestimmtes Windows-Feature aktiviert ist, oder so komplex wie das Bereitstellen von SharePoint sein.

DSC verfügt auch über eine integrierte Überwachung und Berichterstellung.
Wenn ein System nicht mehr kompatibel ist, kann DSC eine Warnung auslösen und agieren, um das System zu korrigieren.

## <a name="benefits-of-using-desired-state-configuration"></a>Vorteile der Verwendung von DSC

Konfigurationen sind leicht zu lesen, zu speichern und zu aktualisieren.
Konfigurationen definieren den Zustand, den Zielgeräte haben sollen, anstatt Anweisungen zu schreiben, wie diese in den jeweiligen Zustand versetzt werden können.
Dadurch ist der Aufwand wesentlich geringer, eine Konfiguration über DSC zu erlernen, zu übernehmen, zu implementieren und beizubehalten.

Das Erstellen von Konfigurationen bedeutet, dass komplexe Bereitstellungsschritte als kompakte Lösung an einem zentralen Ort erfasst werden.
Dadurch wird die wiederholte Bereitstellung bestimmter Computergruppen wesentlich weniger fehleranfällig.
Auf der anderen Seite werden Bereitstellungen schneller und zuverlässiger, sodass sich komplexe Bereitstellungen schneller realisieren lassen.

Konfigurationen können auch über den [PowerShell-Katalog](https://powershellgallery.com) freigegeben werden. Möglicherweise sind für die Arbeiten, die erledigt werden müssen, bereits gängige Szenarios und bewährte Methoden vorhanden.


## <a name="desired-state-configuration-and-devops"></a>DSC und DevOps

DSC wurde mit [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) im Hinterkopf entwickelt. Dieser Ansatz vereint Benutzer, Prozesse und Tools, sodass eine schnelle Bereitstellung und Iteration möglich ist, um sowohl internen als auch externen Endbenutzern einen Mehrwert zu bieten.
Wenn eine Umgebung mittels einer einzelnen Konfiguration definiert wird, können Entwickler ihre Anforderungen in einer Konfiguration codieren und diese Konfiguration in die Quellcodeverwaltung einchecken. Das Betriebsteam kann anschließend Code bereitstellen, ohne fehleranfällige manuelle Prozesse durchlaufen zu müssen.

Konfigurationen sind auch [datengesteuert](configData.md), was es dem Betriebsteam erleichtert, Umgebungen ohne Eingriffe von Entwicklern zu erkennen und zu ändern.

## <a name="desired-state-configuration-on--and-off-premises"></a>DSC – lokale und externe Bereitstellungen

DSC kann zum Verwalten lokaler und externer Bereitstellungen verwendet werden.
Für lokale Lösungen bietet DSC einen [Pullserver](pullServer.md) zum Zentralisieren der Verwaltung von Computern und Melden ihres Status.
Für Cloudlösungen lässt sich DSC da verwenden, wo Windows verwendet werden kann.
Es gibt auch spezielle Angebote in Azure, die auf DSC basieren, wie z.B. [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/) zum Zentralisieren der Berichterstattung für DSC.

## <a name="dsc-and-compatibility"></a>DSC und Kompatibilität

DSC wurde zwar in Windows Server 2012 R2 eingeführt, ist aber auch für ältere Betriebssysteme über das WMF-Paket (WMF) verfügbar.
Weitere Informationen zum WMF finden Sie auf der [PowerShell-Startseite](/powershell/).

DSC kann auch zum Verwalten von Linux verwendet werden. Weitere Informationen finden Sie unter [Erste Schritte mit DSC für Linux](lnxGettingStarted.md).
