# Just Enough Administration
Just Enough Administration (JEA) ist eine Sicherheitstechnologie, die eine delegierte Verwaltung für sämtliche Elemente ermöglicht, die in PowerShell verwaltet werden können.
Mit JEA ist Folgendes möglich:
- **Reduzieren Sie die Anzahl von Administratoren auf Ihren Computern**, indem Sie virtuelle Konten nutzen, die privilegierte Aktionen für normale Benutzer ausführen.
- **Beschränken Sie Benutzeraktionen**, indem Sie die Cmdlets, Funktionen und externen Befehle festlegen, die von Benutzern ausgeführt werden dürfen.
- **Verschaffen Sie sich genauere Kenntnis darüber, was Ihre Benutzer tun**, indem Sie Aufzeichnungen mitschneiden, die Ihnen genau zeigen, welche Befehle ein Benutzer während einer Sitzung ausgeführt hat.

Warum ist das so wichtig?
Betrachten Sie das gängige Szenario, bei dem Ihre DNS-Server mit Ihren Active Directory-Domänencontrollern zusammengestellt sind.
Ihre DNS-Administratoren müssen lokale Administratorrechte besitzen, um Probleme mit dem DNS-Server beheben zu können. Zu diesem Zweck müssen Sie sie zu Mitgliedern der Sicherheitsgruppe „Domänen-Admins“ machen, die über weit reichende Berechtigungen verfügt.
Damit erhalten diese Administratoren effektiv Kontrolle über Ihre gesamte Domäne sowie Zugriff auf alle Ressourcen auf diesem Computer.

Mit JEA können Sie eine Rolle für die DNS-Administratoren konfigurieren, die ihnen Zugriff auf alle Befehle gewährt, die sie benötigen – und auf nichts sonst.
Das bedeutet, dass die Administratoren einen beschädigten DNS-Cache reparieren können, ohne gleichzeitig Berechtigungen für den Zugriff auf Active Directory, für das Durchsuchen des Dateisystems oder für das Ausführen potenziell gefährlicher Skripts zu erhalten.
Ein weiterer Vorteil: Wenn die JEA-Sitzung so konfiguriert ist, dass einmalige privilegierte virtuelle Konten verwendet werden, können Ihre DNS-Administratoren eine Verbindung mit dem Server als *nicht privilegierter* Benutzer herstellen und trotzdem Befehle ausführen, für die Berechtigungen erforderlich sind.

## Erste Schritte

### Installation
JEA wird zusammen mit dem bevorstehenden Windows Server 2016-Release entwickelt und steht in älteren Windows-Versionen über Updates des Windows Management Frameworks zur Verfügung.
Das aktuelle JEA-Release ist auf den folgenden Plattformen verfügbar:

**Windows Server**
- Windows Server 2016 Technical Preview 4 und höher
- Windows Server 2012 R2, 2012 und 2008 R2\* mit installiertem [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395)

**Windows-Client**
- Windows 10 mit installiertem November-Update (1511)
- Windows 8.1, 8 und 7\* mit installiertem [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395)

\* Unterstützung für virtuelle JEA-Sitzungen steht in Windows Server 2008 R2 und Windows 7 derzeit nicht zur Verfügung.


### Kernkonzepte
**Was genau ist JEA?**

JEA ist eine Erweiterung von [eingeschränkten PowerShell-Endpunkten](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx), die Rollendefinitionen, virtuelle Konten sowie viele weitere Verbesserungen hinzufügt, mit denen Sie Ihre Verwaltungsendpunkte noch besser sichern können.
Ein JEA-Endpunkt besteht aus einer PowerShell-Sitzungskonfigurationsdatei und mindestens einer Rollenfunktionsdatei.

**Was sind Sitzungskonfigurations- und Rollenfunktionsdateien?**

PowerShell-Sitzungskonfigurationsdateien (PSSC) definieren, *wer* eine Verbindung zu einem PowerShell-Endpunkt herstellen darf und *wie* diese Sitzung konfiguriert wird.
In diesen Dateien ordnen Sie Benutzer und Sicherheitsgruppen zu bestimmten Verwaltungsrollen zu und konfigurieren globale Einstellungen wie virtuelle Konten und Aufzeichnungsrichtlinien.
Sitzungskonfigurationsdateien sind computerspezifisch, sodass Sie den Zugriff bei Bedarf für jeden Computer einzeln steuern können.

PowerShell-Rollenfunktionsdateien (PSRC) definieren, *was* Benutzer, die dieser Rolle angehören, auf dem System tun können.
Hier können Sie festlegen, welche Cmdlets, Funktionen, Anbieter und externen Programme ein Benutzer während einer JEA-Sitzung verwenden darf.
Rollenfunktionsdateien gelten häufig allgemein für die jeweilige Rolle (DNS-Administrator, Level-1-Helpdesk, schreibgeschützte Bestandsüberwachung usw.) und gehören zu PowerShell-Modulen, sodass sie problemlos in Ihrer Umgebung und für andere Benutzer freigegeben werden können.

**Wie nutzt JEA virtuelle Konten?**

In der PowerShell-Sitzungskonfigurationsdatei können Sie JEA-Sitzungen so konfigurieren, dass sie virtuelle ausführende Konten verwenden.
Virtuelle Konten sind einmalige privilegierte Konten. Sie werden nur für genau den Benutzer angelegt, der in genau der Sitzung eine Verbindung herstellt, in deren Kontext die Befehle des Benutzers ausgeführt werden.
Virtuelle Konten gehören standardmäßig zur Sicherheitsgruppe „Administratoren“, können optional jedoch so konfiguriert werden, dass sie nur den von Ihnen angegebenen Sicherheitsgruppen angehören.

### Einführungsleitfaden zu JEA
Sind Sie bereit, Ihren ersten JEA-Endpunkt zu erstellen?
Sehen Sie sich den [Einführungsleitfaden zu JEA](jea-uide.md) an, um zu erfahren, wie Sie selbst einen JEA-Endpunkt erstellen, bereitstellen und verwenden.
Dieser Leitfaden ist ein idealer Startpunkt für den schnellen Einstieg: Anhand eines vorgefertigten JEA-Endpunkts erhalten Sie eine Vorstellung davon, welche Möglichkeiten JEA dem Endbenutzer bietet. Anschließend führt der Leitfaden Sie durch den Prozess der Erstellung eines Endpunkts von Grund auf und erläutert dabei die Konzepte von Sitzungskonfigurationen und Rollenfunktionen.

### Ihre ersten eigenen JEA-Endpunkte
Die Erstellung eines JEA-Endpunkts ist ganz einfach – Sie benötigen nur ein JEA-fähiges System und einen Text-Editor (wie z. B. die PowerShell ISE).
Ein guter Tipp für den Einstieg: Erstellen Sie Gerüstdateien mithilfe von `New-PSRoleCapabilityFile -Path <path>` und `New-PSSessionCapabilityFile -Path <Path>`, ohne weitere Argumente.
Diese Gerüstdateien enthalten alle anwendbaren Konfigurationsfelder sowie nützliche Kommentare, die erklären, wozu welches Feld verwendet werden kann.

Um die Erstellung von JEA-Endpunkten noch einfacher zu gestalten, lesen Sie den Blog [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx). In diesem Blog finden Sie eine GUI, mit deren Hilfe Sie Sitzungskonfigurations- und Rollenfunktionsdateien erstellen können.
Die GUI unterstützt sogar die Erstellung von Rollenfunktionen basierend auf PowerShell-Protokollen, sodass Sie mit den Befehlen beginnen können, die Ihre Benutzer regelmäßig für ihre Arbeit ausführen.


<!--HONumber=Jun16_HO3-->


