---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Bewährte Methoden für Pullserver
ms.openlocfilehash: a3c4ca039b1e061a9246848bef6aeecebcd89011
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953527"
---
# <a name="pull-server-best-practices"></a>Bewährte Methoden für Pullserver

Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Der Pull-Server (Windows-Feature *DSC-Dienst*) ist eine von Windows Server unterstützte Komponente, jedoch sollen keine neuen Features oder Funktionen angeboten werden. Es wird empfohlen, verwaltete Clients auf [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) umzustellen (enthält Features zusätzlich zum Pull-Server unter Windows Server) oder auf eine der [hier](/powershell/dsc/pull-server/pullserver#community-solutions-for-pull-service) aufgeführten Communitylösungen.

Zusammenfassung: Dieser Artikel enthält Prozesse und Erweiterungen, die Techniker beim Vorbereiten von Lösungen helfen sollen. Details sollten bewährte Methoden bereitstellen, die von Kunden ermittelt und dann vom Produktteam bestätigt wurden, um sicherzustellen, dass die Empfehlungen in die Zukunft gerichtet sind und als stabil angesehen werden.

| |Dokumentinformation|
|:---|:---|
Autor | Michael Greene
Prüfer | Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic
Veröffentlicht | April 2015

## <a name="abstract"></a>Zusammenfassung

Dieses Dokument soll als offizieller Leitfaden für alle dienen, die die Implementierung eines Windows PowerShell DSC-Pullservers planen. Ein Pullserver ist ein einfacher Dienst, der in wenigen Minuten bereitgestellt sein sollte. Obwohl dieses Dokument technische Hilfe und Anleitungen zur Verfügung stellen soll, die in einer Bereitstellung genutzt werden können, stellt dieses eine Referenz für bewährte Methoden und die zu beachtenden Punkte vor der Bereitstellung dar.
Leser sollten über grundlegende DSC-Kenntnisse verfügen und die Bestimmungen kennen, mit denen die Komponenten beschrieben werden, die in einer DSC-Bereitstellung enthalten sind. Weitere Informationen finden Sie im Thema [Windows PowerShell DSC – Übersicht](/powershell/dsc/overview).
Da sich DSC im gleichen Maße weiterentwickeln sollte, wie sich die Cloudinfrastruktur weiterentwickelt, wird die zugrunde liegende Technologie einschließlich des Pullservers sich ebenfalls weiterentwickeln und neue Funktionen einführen. Dieses Dokument enthält eine Versionstabelle im Anhang, die Referenzen zu vorherigen Versionen und in die Zukunft gerichteten Lösungen bereitstellt, um in die Zukunft gerichtete Entwürfe zu fördern.

Die zwei Hauptabschnitte dieses Dokuments:

- Konfigurationsplanung
- Installationsanweisungen

### <a name="versions-of-the-windows-management-framework"></a>Windows Management Framework-Versionen

Die Informationen in diesem Dokument sollen auf Windows Management Framework 5.0 angewendet werden. Obwohl WMF 5.0 nicht für die Bereitstellung und Ausführung eines Pullservers erforderlich ist, konzentriert sich dieses Dokument auf die Version 5.0.

### <a name="windows-powershell-desired-state-configuration"></a>Windows PowerShell zum Konfigurieren des gewünschten Zustands

Desired State Configuration (DSC) ist eine Managementplattform, die das Bereitstellen und Verwalten von Konfigurationsdaten mithilfe einer Branchensyntax namens „Managed Object Format“ (MOF) aktiviert, um „Common Information Models“ (CIM) zu beschreiben. Das Open Source-Projekt „Open Management Infrastructure“ (OMI) ist vorhanden, um die Entwicklung dieser Standards plattformübergreifend zu unterstützen, einschließlich Linux und Betriebssysteme für die Netzwerkhardware. Weitere Informationen finden Sie unter der [DMTF page linking to MOF specifications (DMTF-Seite mit Link zu den MOF-Spezifikationen)](https://www.dmtf.org/standards/cim) und [OMI Documents and Source (OMI-Dokumente und Quelle)](https://collaboration.opengroup.org/omi/documents.php).

Windows PowerShell bietet eine Reihe an Spracherweiterungen für Desired State Configuration, die Sie zur Erstellung und Verwaltung deklarativer Konfigurationen verwenden können.

### <a name="pull-server-role"></a>Pullserverrolle

Ein Pullserver bietet einen zentralisierten Dienst zum Speichern von Konfigurationen, die für Zielknoten zugänglich sein werden.

Die Pullserverrolle kann als Webserverinstanz oder SMB-Dateifreigabe bereitgestellt werden. Die Webserverfunktion enthält eine OData-Schnittstelle und kann optional Funktionen für die Zielknoten enthalten, die die Bestätigung des Erfolgs oder Misserfolgs der angewendeten Konfigurationen übermitteln. Diese Funktion ist nützlich in Umgebungen, in denen eine große Anzahl von Knoten besteht.
Nach dem Konfigurieren eines Zielknotens (auch als Client bezeichnet), der auf den Pullserver verweist, werden die aktuellen Konfigurationsdaten und alle erforderlichen Skripts heruntergeladen und angewendet. Dies kann eine einmalige Bereitstellung oder eine wiederkehrende Aufgabe sein und macht den Pullserver zu einer wichtigen Ressource zur Verwaltung von Skalierungsänderungen. Weitere Informationen finden Sie unter [Desired State Configuration – Pulldienst](/powershell/dsc/pullServer/pullserver) und

[Desired State Configuration – Pulldienst](/powershell/dsc/pullServer/pullserver).

## <a name="configuration-planning"></a>Konfigurationsplanung

Für jede Bereitstellung einer Unternehmenssoftware können im Voraus Informationen gesammelt werden, um die Planung der korrekten Architektur zu unterstützen und um auf die erforderlichen Schritte zum Abschließen der Bereitstellung vorbereitet zu sein. Die folgenden Abschnitte stellen Informationen zur Vorbereitung und Unternehmensverbindungen bereit, die wahrscheinlich im Voraus erfolgen müssen.

### <a name="software-requirements"></a>Softwareanforderungen

Das Bereitstellen eines Pullservers erfordert das DSC-Servicefeature von Windows Server. Dieses Feature wurde in Windows Server 2012 eingeführt und durch fortlaufende Versionen von Windows Management Framework (WMF) aktualisiert.

### <a name="software-downloads"></a>Softwaredownloads

Neben der Installation der neuesten Inhalte von Windows Update werden zwei Downloads als bewährte Methoden für die Bereitstellung eines DSC-Pullservers empfohlen: Die neueste Version von Windows Management Framework und ein DSC-Modul zum Automatisieren der Bereitstellung von Pullservern.

### <a name="wmf"></a>WMF

Windows Server 2012 R2 umfasst ein Feature namens DSC-Dienst. Das DSC-Dienstfeature bietet die Pullserverfunktionalität, einschließlich der Binärdateien, die den OData-Endpunkt unterstützen.
WMF ist in Windows Server enthalten und wird in einem agilen Rhythmus zwischen den Windows Server-Versionen aktualisiert. [Neue WMF 5.0-Versionen](https://www.microsoft.com/en-us/download/details.aspx?id=54616) können Updates des DSC-Dienstfeatures enthalten. Aus diesem Grund ist es eine bewährte Methode, die neueste WMF-Version herunterzuladen und die Versionshinweise zu überprüfen, um festzustellen, ob die Version ein Update für das DSC-Dienstfeature enthält. Sie sollten auch den Abschnitt über die Versionshinweise überprüfen, die angeben, ob der Status des Entwurfs für ein Update oder Szenario als stabil oder experimentell aufgeführt wird.
Damit ein agiler Veröffentlichungszyklus möglich ist, können einzelne Features als stabil erklärt werden. Dies gibt an, dass das Feature zur Nutzung in einer Produktionsumgebung bereit ist, auch wenn WMF als Vorschau zur Verfügung gestellt wird.
Andere Features, die in der Vergangenheit durch WMF-Versionen aktualisiert wurden (weitere Informationen in den WMF-Versionshinweisen):

- Windows PowerShell Windows PowerShell Integrated Scripting
- Environment (ISE) Windows PowerShell Web Services (Management OData
- IIS-Erweiterung)  Windows PowerShell Desired State Configuration (DSC)
- Windows-Remoteverwaltung (WinRM) Windows-Verwaltungsinstrumentation (WMI)

### <a name="dsc-resource"></a>DSC-Ressource

Eine Pullserverbereitstellung kann durch die Bereitstellung des Dienstes mithilfe eines DSC-Konfigurationsskripts vereinfacht werden. Dieses Dokument enthält Konfigurationsskripts, die verwendet werden können, um einen Serverknoten bereitzustellen, der für die Produktion geeignet ist. Für die Verwendung der Konfigurationsskripts ist ein DSC-Modul erforderlich, das nicht in Windows Server enthalten ist. Der erforderliche Modulname lautet **xPSDesiredStateConfiguration** und enthält die DSC-Ressource **xDscWebService**. Das Modul xPSDesiredStateConfiguration kann [hier](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d) heruntergeladen werden.

Verwenden Sie das Cmdlet `Install-Module` aus dem Modul **PowerShellGet**.

```powershell
Install-Module xPSDesiredStateConfiguration
```

Das Modul **PowerShellGet** wird das Modul hier speichern:

`C:\Program Files\Windows PowerShell\Modules`

Planungsaufgabe|
---|
Haben Sie Zugriff auf die Installationsdateien für Windows Server 2012 R2?|
Wird die Bereitstellungsumgebung Internetzugang haben, damit WMF und das Modul aus dem Onlinekatalog heruntergeladen werden können?|
Wie werden Sie nach der Installation des Betriebssystems die neuesten Sicherheitsupdates installieren?|
Wird die Umgebung Internetzugang haben, um Updates zu erhalten oder wird sie über einen lokalen Windows Server Update Services-Server (WSUS) verfügen?|
Haben Sie Zugang zu den Installationsdateien von Windows Server, die durch eine Einführung offline bereits Updates enthalten?|

### <a name="hardware-requirements"></a>Hardwareanforderungen

Pullserverbereitstellungen werden auf physischen und virtuellen Servern unterstützt. Die Größenanforderungen für Pullserver decken sich mit den Anforderungen für Windows Server 2012 R2.

CPU: 1,4-GHz-64-Bit-Prozessor, Arbeitsspeicher: 512 MB, Festplattenspeicher: 32 GB, Netzwerk: Gigabit-Ethernet-Adapter.

Planungsaufgabe|
---|
Werden Sie auf einer physischen Hardware oder einer Virtualisierungsplattform bereitstellen?|
Wie sieht der Prozess zum Anfordern eines neuen Servers für Ihre Zielumgebung aus?|
Was ist die durchschnittliche Verarbeitungszeit, bis ein Server verfügbar wird?|
Welche Servergröße werden Sie anfordern?|

### <a name="accounts"></a>Konten

Es gibt keine Anforderungen an das Dienstkonto zur Bereitstellung einer Pullserverinstanz.
Es gibt jedoch Szenarios, in denen die Website im Kontext des lokalen Benutzerkontos ausgeführt werden könnte.
Zum Beispiel, wenn Zugang zur Speicherfreigabe für Websiteinhalte benötigt wird und der Windows Server oder das Gerät, das die Datenfreigabe hostet, nicht in eine Domäne eingebunden sind.

### <a name="dns-records"></a>DNS-Datensätze

Sie benötigen einen Servernamen für die Konfiguration von Clients, damit diese mit einer Pullserverumgebung arbeiten.
In Testumgebungen wird in der Regel der Serverhostname verwendet oder die IP-Adresse für den Server, wenn die DNS-Namensauflösung nicht verfügbar ist.
In Produktionsumgebungen oder in einer Laborumgebung, die eine Produktionsbereitstellung darstellen soll, wird empfohlen, einen DNS CNAME-Datensatz zu erstellen.

Mit einem DNS-CNAME können Sie ein Alias erstellen, um auf Ihren Hosteintrag (A) zu verweisen.
Die Absicht des zusätzlichen Namenseintrags ist eine verbesserte Flexibilität für den Fall, dass eine Änderung in der Zukunft erforderlich sein sollte.
Ein CNAME kann bei der Isolierung der Clientkonfiguration behilflich sein, damit Änderungen der Serverumgebung keine entsprechenden Änderungen der Clientkonfiguration erfordern. Diese Änderungen umfassen das Ersetzen eines Pullservers oder Hinzufügen zusätzlicher Pullserver.

Bedenken Sie die Lösungsarchitektur, wenn Sie einen Namen für den DNS-Datensatz auswählen.
Bei der Nutzung des Lastenausgleichs muss das Zertifikat zur Sicherung von Datenverkehr über HTTPS über denselben Namen verfügen wie der DNS-Datensatz.

Szenario |Bewährte Methode
:---|:---
Testumgebung |Reproduzieren Sie nach Möglichkeit die geplante Produktionsumgebung. Ein Serverhostname eignet sich für einfache Konfigurationen. Wenn DNS nicht verfügbar ist, kann eine IP-Adresse anstatt eines Hostnamen verwendet werden.|
Einzelknotenbereitstellung |Erstellen Sie einen DNS CNAME-Datensatz, der auf den Serverhostnamen verweist.|

Weitere Informationen finden Sie unter [Configuring DNS Round Robin in Windows Server (Konfigurieren des DNS-Roundrobin in Windows Server)](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).

Planungsaufgabe|
---|
Wissen Sie, an wen Sie sich zur Erstellung und Änderung der DNS-Datensätze wenden müssen?|
Was ist die durchschnittliche Verarbeitungszeit für eine Anforderung eines DNS-Datensatzes?|
Müssen Sie statische Hostnamendatensätze (A) für Server anfordern?|
Was werden Sie als CNAME anfordern?|
Wenn nötig, welche Art von Lastenausgleichslösung werden Sie verwenden? (siehe Abschnitt „Lastenausgleich“ für weitere Informationen)|

### <a name="public-key-infrastructure"></a>Public Key-Infrastruktur

In den meisten Unternehmen muss Netzwerkdatenverkehr, insbesondere Datenverkehr, der vertrauliche Daten wie die Serverkonfiguration enthält, heutzutage bei der Übertragung bestätigt und/oder verschlüsselt werden.
Es ist zwar möglich, einen Pullserver mithilfe von HTTP bereitzustellen, was Clientanforderungen im Klartext vereinfacht, aber die bewährte Methode ist ein mit HTTPS gesicherter Datenverkehr. Der Dienst kann mithilfe einer Reihe von Parametern in der DSC-Ressource **xPSDesiredStateConfiguration** zur Verwendung von HTTPS konfiguriert werden.

Die Zertifikatanforderungen zur Sicherung von HTTPS-Datenverkehr für Pullserver unterscheiden sich nicht von der Sicherung anderer HTTPS-Websites. Die **Webserver**-Vorlage in einem Windows Server Certificate Service erfüllt die erforderlichen Funktionen.

Planungsaufgabe|
---|
Wenn Zertifikatanforderungen nicht automatisiert sind, wen müssen Sie kontaktieren, um ein Zertifikat anzufordern?|
Was ist die durchschnittliche Verarbeitungszeit für die Anforderung?|
Wie wird Ihnen diese Zertifikatdatei übertragen?|
Wie wird Ihnen der private Schlüssel des Zertifikats übertragen?|
Wie lange dauert die Standardablaufzeit?|
Haben Sie einen DNS-Namen für die Pullserverumgebung ausgewählt, die Sie für den Zertifikatnamen verwenden können?|

### <a name="choosing-an-architecture"></a>Auswählen einer Architektur

Ein Pullserver kann mithilfe eines auf IIS gehosteten Webdiensts oder einer SMB-Datenfreigabe bereitgestellt werden. In den meisten Fällen bietet die Webdienstoption mehr Flexibilität. Es ist nicht ungewöhnlich, dass HTTPS-Datenverkehr die Netzwerkgrenzen durchläuft. Im Gegensatz dazu wird SMB-Datenverkehr häufig zwischen Netzwerken gefiltert oder blockiert. Der Webdienst bietet außerdem die Option zum Einschließen eines Conformance Server oder Web Reporting Manager (beide Themen werden in einer künftigen Version dieses Dokuments behandelt), die einen Mechanismus für Clients bereitstellen, mit dem der Status an einen Server weitergeleitet werden kann, um somit für zentrale Sichtbarkeit zu sorgen.
SMB bietet eine Option für Umgebungen, bei der eine Richtlinie bestimmt, dass ein Webserver nicht verwendet werden sollte und für andere Umgebungsanforderungen, die eine Webserverrolle unerwünscht erscheinen lassen.
Sie müssen in beiden Fällen die Anforderungen für die Signierung und Verschlüsselung des Datenverkehrs bewerten. HTTPS, SMB-Signaturen und IPSEC-Richtlinien sind Optionen, die in Betracht gezogen werden sollten.

#### <a name="load-balancing"></a>Lastenausgleich

Clients, die mit dem Webdienst interagieren, fordern Informationen an, die in einer einzelnen Antwort zurückgegeben werden. Es sind keine sequenziellen Anforderungen erforderlich. Deshalb muss die Lastenausgleichsplattform nicht sicherstellen, dass Sitzungen zu jedem Zeitpunkt auf einem einzelnen Server beibehalten werden.

Planungsaufgabe|
---|
Welche Lösung wird für den serverübergreifenden Lastenausgleich für Datenverkehr verwendet werden?|
Wenn Sie einen Hardwarelastenausgleich verwenden, wer wird eine Anforderung annehmen, um eine neue Konfiguration zum Gerät hinzuzufügen?|
Was ist die durchschnittliche Verarbeitungszeit für eine Anforderung zur Konfiguration eines neuen, per Lastenausgleich verarbeiteten, Webdiensts?|
Welche Information ist für die Anforderung erforderlich?|
Müssen Sie eine zusätzliche IP-Adresse anfordern oder wird das für den Lastenausgleich verantwortliche Team sich darum kümmern?|
Verfügen Sie über die benötigten DNS-Datensätze, und werden diese vom Team benötigt, das für die Konfiguration der Lastenausgleichslösung verantwortlich ist?|
Erfordert die Lastenausgleichslösung, dass PKI vom Gerät verarbeitet wird, oder kann es den HTTPS-Datenverkehr per Lastenausgleich verarbeiten, so lange keine Sitzungserforderungen bestehen?|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a>Bereitstellen von Konfigurationen und Modulen auf dem Pullserver

Als Teil der Konfigurationsplanung müssen Sie darüber nachdenken, welche DSC-Module und Konfigurationen von Pullservern gehostet werden. Für die Konfigurationsplanung ist es wichtig, grundlegende Kenntnisse zum Vorbereiten und Bereitstellen von Inhalten auf einem Pullserver zu haben.

Dieser Abschnitt wird in Zukunft erweitert und in einem Betriebshandbuch für DSC-Pullserver enthalten sein.  Im Handbuch wird das tägliche Verfahren zum Verwalten von Modulen und Konfigurationen im Laufe der Zeit mithilfe der Automatisierung erläutert.

#### <a name="dsc-modules"></a>DSC-Module

Clients, die eine Konfiguration anfordern, benötigen die erforderlichen DSC-Module. Die automatische Verteilung von DSC-Modulen an Clients bei Bedarf ist eine Funktion des Pullservers. Wenn Sie einen Pullserver zum ersten Mal vielleicht als Labor oder Machbarkeitsstudie bereitstellen, werden Sie wahrscheinlich von DSC-Modulen abhängig sein, die auf öffentlichen Repositorys verfügbar sind, wie z.B. dem PowerShell-Katalog oder den PowerShell.org GitHub-Repositorys für DSC-Module.

Beachten Sie, dass auch bei vertrauenswürdigen Onlinequellen wie dem PowerShell-Katalog jedes Modul, das aus einem öffentlichen Repository heruntergeladen wird, vor seiner Verwendung in der Produktion von jemandem kontrolliert werden sollte, der Erfahrung mit PowerShell hat und über Kenntnisse der Umgebung verfügt, in der die Module verwendet werden. Das Ausführen dieser Aufgabe ist ein guter Zeitpunkt, das Modul auf eine beliebige zusätzliche Nutzlast zu überprüfen, die entfernt werden kann, wie z.B. Dokumentation und Beispielskripts. Dies verringert die Netzwerkbandbreite pro Client bei ihrer ersten Anforderung, wenn Module über das Netzwerk vom Server zum Client heruntergeladen werden.

Jedes Modul muss in einem bestimmten Format, einer ZIP-Datei mit dem Namen ModuleName_Version.zip, verpackt sein, die die Modulnutzlast enthält. Nachdem die Datei auf den Server kopiert wurde, muss eine Prüfsummendatei erstellt werden. Wenn Clients eine Verbindung mit dem Server herstellen, wird die Prüfsumme verwendet, um zu überprüfen, ob der Inhalt des DSC-Moduls seit der Veröffentlichung nicht geändert wurde.

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

Planungsaufgabe|
---|
Welche Szenarios sind wichtig zur Überprüfung, wenn Sie eine Test- oder Laborumgebung planen?|
Gibt es öffentlich verfügbare Module, die Ressourcen enthalten, die alles abdecken, das Sie benötigen, oder müssen Sie Ihre eigenen Ressourcen erstellen?|
Wird Ihre Umgebung Internetzugang haben, um öffentliche Module abrufen zu können?|
Wer wird für die Prüfung von DSC-Modulen zuständig sein?|
Was verwenden Sie als lokales Repository zum Speichern von DSC-Modulen, wenn Sie eine Produktionsumgebung planen?|
Wird ein zentrales Team DSC-Module von Anwendungsteams akzeptieren? Wie wird das Verfahren aussehen?|
Werden Sie das Verpacken, Kopieren und Erstellen einer Prüfsumme für produktionsbereite DSC-Module für den Server aus Ihrem Quell-Repository automatisieren?|
Wird Ihr Team auch für das Verwalten der Automatisierungsplattform verantwortlich sein?|

#### <a name="dsc-configurations"></a>DSC-Konfigurationen

Ein Pullserver dient zur Bereitstellung eines zentralisierten Mechanismus für die Verteilung von DSC-Konfigurationen auf Clientknoten. Die Konfigurationen werden als MOF-Dokumente auf dem Server gespeichert.
Jedes Dokument wird mit einer eindeutigen **GUID** benannt. Wenn Clients für die Verbindung mit einem Pullserver konfiguriert sind, wird ihnen auch die **GUID** für die Konfiguration zugewiesen, die sie anfordern sollten. Dieses System des Verweisens auf Konfigurationen mit **GUID** garantiert globale Eindeutigkeit und ist flexibel, sodass eine Konfiguration mit Genauigkeit pro Knoten angewendet werden kann oder als eine Rollenkonfiguration, die viele Server umfasst, die identische Konfigurationen aufweisen sollten.

#### <a name="guids"></a>GUIDs

Das Planen der Konfigurations-**GUIDs** lohnt sich besonders, wenn Sie eine Pullserverbereitstellung planen. Es bestehen keine besonderen Anforderungen für die Behandlung von **GUIDs**, und der Prozess wird wahrscheinlich für jede Umgebung einzigartig sein. Der Prozess kann einfach bis komplex sein: eine zentral gespeicherte CSV-Datei, eine einfache SQL-Tabelle, eine CMDB oder eine komplexe Lösung, die eine Integration mit einem anderen Tool oder einer Softwarelösung erfordert. Es gibt zwei allgemeine Vorgehensweisen:

- **Zuweisen von GUIDs pro Server** – Hiermit kann sichergestellt werden, dass jede Serverkonfiguration einzeln gesteuert wird. Dies bietet einen Grad an Genauigkeit um Updates und kann auch in Umgebungen mit wenigen Servern ausgeführt werden.
- **Zuweisen von GUIDs pro Serverrolle** – Alle Server, die die gleiche Funktion erfüllen, z.B. Webserver, verwenden dieselbe GUID, um auf die erforderlichen Konfigurationsdaten zu verweisen.  Beachten Sie, dass wenn viele Server dieselbe GUID verwenden, alle gleichzeitig aktualisiert werden würden, wenn die Konfiguration geändert wird.

  Die GUID sollte als vertraulich behandelt werden, da sie von jemanden mit böswilligen Absichten genutzt werden könnte, um Informationen über die Bereitstellung und Konfiguration von Servern in Ihrer Umgebung zu erlangen. Weitere Informationen finden Sie unter [Securely allocating GUIDs in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/) (Sicheres Zuweisen von GUIDs in PowerShell Desired State Configuration Pullmodus).

Planungsaufgabe|
---|
Wer wird für das Kopieren der Konfigurationen in den Pullserverordner verantwortlich sein, sobald sie bereit sind?|
Wie wird der Weiterleitungsprozess aussehen, wenn Konfigurationen von einem Anwendungsteam erstellt werden?|
Werden Sie ein Repository zum Speichern von Konfigurationen nutzen, wenn sie über Teams hinweg verfasst werden?|
Werden Sie das Kopieren von Konfigurationen auf den Server und das Erstellen einer Prüfsumme automatisieren, wenn sie bereit sind?|
Wie werden Sie GUIDS den Servern oder Rollen zuordnen, und wo werden diese gespeichert?|
Welchen Prozess werden Sie zum Konfigurieren der Clientcomputer verwenden, und wie wird er sich in Ihren Prozess zum Erstellen und Speichern von Konfigurations-GUIDs integrieren?|

## <a name="installation-guide"></a>Installationsanweisungen

*Die in diesem Dokument angegebenen Skripts sind stabile Beispiele. Überprüfen Sie Skripts immer sorgfältig, bevor diese in einer Produktionsumgebung ausgeführt werden.*

### <a name="prerequisites"></a>Voraussetzungen

Verwenden Sie den folgenden Befehl, um die PowerShell-Version auf Ihrem Server zu überprüfen.

```powershell
$PSVersionTable.PSVersion
```

Installieren Sie nach Möglichkeit die neueste Version von Windows Management Framework.
Laden Sie als nächstes das `xPsDesiredStateConfiguration`-Modul mit dem folgenden Befehl herunter.

```powershell
Install-Module xPSDesiredStateConfiguration
```

Der Befehl wird Sie nach Ihrer Genehmigung fragen, bevor Sie das Modul herunterladen.

### <a name="installation-and-configuration-scripts"></a>Installations- und Konfigurationsskripts

Die beste Methode zur Bereitstellung eines DSC-Pullservers ist die Verwendung eines DSC-Konfigurationsskripts. Dieses Dokument präsentiert Skripts, einschließlich beide grundlegenden Einstellungen, die nur den DSC-Webdienst konfigurieren und erweiterte Einstellungen, die einen durchgängigen Windows Server, einschließlich DSC-Webdienst konfigurieren.

Hinweis:  Das `xPSDesiredStateConfiguration`-DSC-Modul erfordert derzeit das Gebietsschema EN-US für den Server.

### <a name="basic-configuration-for-windows-server-2012"></a>Grundlegende Konfiguration für Windows Server 2012

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a>Fortgeschrittene Konfiguration für Windows Server 2012 R2

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a>Überprüfen der Funktionalität des Pullservers

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a>Konfigurieren von Clients

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a>Weitere Referenzen, Ausschnitte und Beispiele

Dieses Beispiel zeigt die manuelle Initiierung einer Clientverbindung (WMF5 erforderlich) zum Testen.

```powershell
Update-DscConfiguration –Wait -Verbose
```

Das Cmdlet [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) wird verwendet, um einen CNAME-Datensatz zu einer DNS-Zone hinzuzufügen.

Die PowerShell-Funktion [Create a Checksum and Publish DSC MOF to SMB Pull Server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) (Erstellen einer Prüfsumme und Veröffentlichen von DSC MOF auf einem SMB-Pullserver) generiert automatisch die erforderlichen Prüfsumme, und kopiert dann die MOF-Konfiguration und die Prüfsummendateien auf den SMB-Pullserver.

## <a name="appendix---understanding-odata-service-data-file-types"></a>Anhang ‒ Verstehen der ODATA-Dienstdateitypen

Eine Datendatei wird gespeichert, um während der Bereitstellung eines Pullservers Informationen zu erstellen, die den OData-Webdienst enthalten. Wie unten beschrieben, hängt der Dateityp vom Betriebssystem ab.

- **Windows Server 2012** Der Dateityp ist immer MDB.
- **Windows Server 2012 R2** Der Dateityp wird standardmäßig auf EDB festgelegt, es sei denn, in der Konfiguration wird eine MDB-Datei angegeben.

Im [erweiterte Beispielskript](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) für die Installation eines Pullservers finden Sie außerdem ein Beispiel für die automatische Steuerung der web.config-Dateieinstellungen, um mögliche Fehler durch den Dateityp zu verhindern.
