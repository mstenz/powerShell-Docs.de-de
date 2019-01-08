---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Erstellen erweiterter DSC-Ressourcen für Komposition und Zusammenarbeit
ms.openlocfilehash: 3e40ba94de0a53c1c9663553c4ec443b5e0df3fd
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401799"
---
# <a name="advanced-dsc-authoring-for-composition-and-collaboration"></a>Erstellen erweiterter DSC-Ressourcen für Komposition und Zusammenarbeit

In diesem Artikel werden die verschiedenen Ansätze beschrieben, die für das Kombinieren von Konfigurationen und Ressourcen verfügbar sind.
Die einzelnen Szenarios haben alle das gleiche Ziel: Reduzieren der Komplexität, wenn zum Erreichen des Endstatus einer Serverbereitstellung mehrere Konfigurationen bevorzugt werden.
Ein Beispiel hierfür wären mehrere Teams, die zum Ergebnis einer Serverbereitstellung beitragen, wie z.B. ein Anwendungsbesitzer, der den Anwendungszustand beibehält, und ein zentrales Team, das die Änderungen in Sicherheitsbaselines veröffentlicht.
Die Einzelheiten der einzelnen Ansätze, einschließlich der Vorteile und Risiken, werden hier näher erläutert.

![Pipeline](../images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a>Techniken zur kollaborativen Dokumenterstellung

Im lokalen Konfigurations-Manager sind zwei Lösungen integriert, die dieses Konzept ermöglichen:

| Konzept | Detaillierte Informationen
|-|-
| Teilkonfigurationen | [Dokumentation](../pull-server/partialConfigs.md)
| Zusammengesetzte Ressourcen | [Dokumentation](../resources/authoringResourceComposite.md)

## <a name="understanding-the-impact-of-each-approach"></a>Grundlegendes zu den Auswirkungen der einzelnen Ansätze

Beide Lösungen können für die Verwaltung des Ergebnisses einer Serverbereitstellung verwendet werden.
Die Auswirkungen bei der Verwendung der einzelnen Ansätze unterscheiden sich jedoch erheblich voneinander.

## <a name="partial-configurations"></a>Teilkonfigurationen

Wenn Sie Teilkonfigurationen verwenden, wird der lokale Konfigurations-Manager so konfiguriert, dass mehrere Konfigurationen unabhängig voneinander verwaltet werden.
Konfigurationen werden unabhängig voneinander kompiliert und anschließend dem Knoten zugewiesen.
Dies macht erforderlich, dass der lokale Konfigurations-Manager im Vorhinein mit dem Namen der jeweiligen Konfiguration konfiguriert wird.

![PartialConfiguration](../images/PartialConfiguration.jpg)

Durch Teilkonfigurationen haben mindestens zwei Teams die vollständige Kontrolle über die Konfiguration eines Servers, häufig ist die Kommunikation oder die Zusammenarbeit dabei nicht von Nutzen.

Kunden haben zurückgemeldet, dass dies zu Ressourcenkonflikten, unbeabsichtigten Außerkraftsetzungen und letztlich zu einem Verlust der Kontrolle über die Konfiguration des Objekts führen kann.

Ferner haben Kunden geäußert, dass es unwahrscheinlich ist, dass bei Verwendung dieses Modells die Konfigurationsänderungen der einzelnen Steuerungsteams vollständig über eine Releasepipeline getestet werden können. Dies wiederum führe zu unerwarteten Ergebnissen in der Produktion.

**Es ist wichtig, dass für die Auswertung sämtlicher auf dem Server freigegebenen Änderungen eine einzelne Pipeline verwendet wird.**

In der nachfolgenden Abbildung gibt Team B seine Teilkonfiguration für Team A frei. Anschließend führt Team A Tests auf dem Server aus, bei denen beide Konfigurationen angewendet werden.
In diesem Modell verfügt nur eine Stelle über die Berechtigung zur Vornahme von Änderungen in der Produktion.

![PartialSinglePipeline](../images/PartialSinglePipeline.jpg)

Wenn Team B Änderungen vornehmen muss, sollte das Team einen Pull Request an die Umgebung für die Quellcodeverwaltung von Team A übermitteln.
Anschließend überprüft Team A die Änderungen mithilfe der Testautomatisierung und gibt diese für die Produktion frei, wenn davon auszugehen ist, dass die Änderungen in den Anwendungen oder den vom Server gehosteten Diensten keine Fehler verursachen.

## <a name="composite-resources"></a>Zusammengesetzte Ressourcen

Eine zusammengesetzte Ressource ist eine DSC-Konfiguration, die als Ressource verpackt ist.
Bei der Konfiguration des LCM (lokaler Konfigurations-Manager) zum Akzeptieren zusammengesetzter Ressourcen müssen keine besonderen Anforderungen berücksichtigt werden.
Die Ressourcen werden in einer neuen Konfiguration verwendet, und eine einzige Kompilierung ergibt eine MOF-Datei.

![CompositeResource](../images/CompositeResource.jpg)

Für zusammengesetzte Ressourcen gibt es zwei gängige Szenarios.
Das erste Szenario beinhaltet die Verringerung der Komplexität und das Abstrahieren eindeutiger Konzepte.
Im zweiten Szenario wird zugelassen, dass Baselines nach dem Bestehen sämtlicher Tests für ein Anwendungsteam verpackt werden, damit diese über die zugehörige Releasepipeline sicher für die Produktion bereitgestellt werden.

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

Zusammengesetzte Ressourcen stufen die Komposition und die Zusammenarbeit über eine Pipeline hoch, während Betriebsbereitschaft geschaffen wird

Möglicherweise verwenden Sie bereits zusammengesetzte Ressourcen, ohne es zu bemerken.
Ein Beispiel hierfür ist **ServiceSet**.
Diese Ressource verwaltet den Status mehrerer Windows-Dienste, ohne diese einzeln aufzuführen.
Die Eigenschaft „Name“ akzeptiert ein Array von Zeichenfolgen für die Angabe der Namen der einzelnen Dienste.
Wenn die Konfiguration kompiliert wird, enthält die MOF-Datei für jeden der an ServiceSet übergebenen Namen einen eindeutigen Abschnitt („Dienst“).

Organisationen verfügen möglicherweise über „Agents“ oder „Middleware“, die auf allen Servern installiert werden sollten.
Eine zusammengesetzte Ressource ist die optimale Lösung für die Verwaltung von Abhängigkeiten sowie die Einrichtung und Konfiguration dieser Tools und Dienstprogramme.

Die Person bzw. das Team, die/das für serverübergreifende Lösungen verantwortlich ist, erstellt eine Konfiguration mit den entsprechenden Anforderungen.
In einem nächsten Schritt wird die Konfiguration mithilfe von Anweisungen aus der Dokumentation zu zusammengesetzten Ressourcen als zusammengesetzte Ressource verpackt.
Abschließend wird die zusammengesetzte Ressource an einem bestimmten Speicherort veröffentlicht (z.B. in einer Dateifreigabe oder einem NuGet-Feed), an dem die Anwendungsteams die Ressource in ihren Konfigurationen verwenden können.

Jedes Mal, wenn das Team eine neue Version freigibt, wird die Versionsnummer im Modulmanifest für die zugehörige zusammengesetzte Ressource schrittweise erhöht.
Die Anwendungsteams schließen die zusammengesetzte Ressource in die Konfiguration ein, die sie für die Verwaltung von Anwendungsabhängigkeiten erstellen.
Wenn die Betriebs-/Sicherheitsteams eine neue Version ihrer Ressource freigeben, benachrichtigen sie die Anwendungsteams über die neue Änderung.

Die Anwendungsteams lösen möglicherweise eine Freigabe für die Produktion aus, die nur eine Änderung an den Baselines beinhaltet.
Dies bietet jedoch eine Möglichkeit zum Auswerten der Auswirkungen auf Anwendungen vor dem Risiko eines Dienstausfalls.

Hinweis: Das Feedback in Bezug auf die Verwendung zusammengesetzter Ressourcen beinhaltete die Kritik, dass zum Vornehmen von Änderungen eine neue MOF-Datei kompiliert und freigegeben werden muss.
Dies ist entwurfsbedingt.
Jedes neue Konfigurationsrelease sollte einen statischen Verweis auf eine bestimmte Version der einzelnen Ressourcen enthalten. Zudem sollte es durch Tests validiert werden, bevor der Serverknoten für die Produktion erreicht wird.
Der Prozess des Testens und Freigebens von Änderungen aus der Quellcodeverwaltung schafft eine sichere Umgebung für die Freigabe von Änderungen in kleinen, aber häufigen Batches.

Weitere Informationen zur Verwendung von Releasepipelines für die Verwaltung der Kerninfrastruktur finden Sie in folgendem Whitepaper: [Das Releasepipeline-Modell](../further-reading/whitepapers.md).
