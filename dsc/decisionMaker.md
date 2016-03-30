# Desired State Configuration (DSC): Übersicht für Entscheidungsträger #

In diesem Dokument werden die Unternehmensvorteile der Verwendung von PowerShell Desired State Configuration (DSC) beschrieben. Es handelt sich nicht um ein technisches Handbuch.

## Was ist „Desired State Configuration“? ##

Windows PowerShell Desired State Configuration (DSC) ist eine in Windows integrierte Konfigurationsverwaltungsplattform, die auf offenen Standards basiert. DSC ist flexibel genug, in jeder Phase des Bereitstellungslebenszyklus (Entwicklung, Test, Präproduktion, Produktion) sowie bei horizontaler Skalierung zuverlässig und konsistent zu funktionieren. 

DSC basiert auf dem Konzept von <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/powershell/dsc/configurations)">Konfigurationen</ctype="x-NOTFOUND">, wobei es sich um einfach zu lesende Dokumente handelt, die eine aus Computern (Knoten) bestehende Umgebung mit bestimmten Merkmalen beschreiben. Diese Merkmale können so einfach wie das Sicherstellen, dass ein bestimmtes Windows-Feature aktiviert ist, oder so komplex wie das Bereitstellen von SharePoint sein. 

DSC verfügt auch über eine integrierte Überwachung und Berichterstellung. Wenn ein System nicht mehr kompatibel ist, kann DSC eine Warnung auslösen und agieren, um das System zu korrigieren. 

## Vorteile der Verwendung von DSC ##

Konfigurationen sind leicht zu lesen, zu speichern und zu aktualisieren. Konfigurationen definieren lediglich den Zustand, den Zielgeräte haben sollen, anstatt Anweisungen zu schreiben, wie diese in den jeweiligen Zustand versetzt werden können. Dadurch ist der Aufwand wesentlich geringer, eine Konfiguration über DSC zu erlernen, zu übernehmen, zu implementieren und beizubehalten. 

Das Erstellen von Konfigurationen bedeutet, dass komplexe Bereitstellungsschritte als kompakte Lösung an einem zentralen Ort erfasst werden. Dadurch wird die wiederholte Bereitstellung bestimmter Computergruppen wesentlich weniger fehleranfällig. Bereitstellungen werden wiederum schneller und zuverlässiger. Dadurch lassen sich komplexe Bereitstellungen schneller realisieren.

Konfigurationen können auch über den <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://powershellgallery.com)">PowerShell-Katalog</ctype="x-NOTFOUND"> freigegeben werden. Dies bedeutet, dass gängige Szenarien und bewährte Methoden für Aufgaben, die Sie erledigen müssen, ggf. bereits vorhanden sind.


## DSC und DevOps ##

<ctype="x-NOTFOUND" mdpre="[" mdpost="](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx)">DevOps</ctype="x-NOTFOUND"> ist eine Kombination aus Personen, Technologien und Kultur, die eine schnelle Bereitstellung und Iteration zulässt. DSC wurde mit Blick auf DevOps entworfen. Wenn eine Umgebung mittels einer einzelnen Konfiguration definiert wird, können Entwickler ihre Anforderungen in einer Konfiguration codieren und diese Konfiguration in die Quellcodeverwaltung einchecken. Das Betriebsteam kann anschließend Code bereitstellen, ohne fehleranfällige manuelle Prozesse durchlaufen zu müssen. 

Konfigurationen sind auch <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/powershell/dsc/configdata)">datengesteuert</ctype="x-NOTFOUND">, was es dem Betriebsteam erleichtert, Umgebungen ohne Eingriffe von Entwicklern zu bestimmen und zu ändern. 

## DSC – Lokale und externe Bereitstellungen ##

DSC kann zum Verwalten lokaler und externer Bereitstellungen verwendet werden. Für lokale Lösungen bietet DSC einen <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver)">Pullserver</ctype="x-NOTFOUND"> zum Zentralisieren der Verwaltung von Computern und Melden ihres Status. Für Cloudlösungen lässt sich DSC da verwenden, wo Windows verwendet werden kann. Es gibt auch spezielle Angebote in Azure, die auf DSC basieren, wie z. B. <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://azure.microsoft.com/en-us/documentation/services/automation/)">Azure Automation</ctype="x-NOTFOUND"> zum Zentralisieren der Berichterstattung für DSC. 

## DSC und Kompatibilität ##

Obwohl DSC in Windows Server 2012 R2 eingeführt wurde, ist es für ältere Betriebssysteme über das WMF-Paket (WMF) verfügbar. Weitere Informationen zum WMF finden Sie auf der <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/powershell/)">PowerShell-Startseite</ctype="x-NOTFOUND">. 

DSC kann auch zum Verwalten von Linux verwendet werden. Weitere Informationen finden Sie unter <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/powershell/dsc/lnxgettingstarted)">Erste Schritte mit DSC für Linux</ctype="x-NOTFOUND">.<!--HONumber=Mar16_HO1-->
