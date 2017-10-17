---
ms.date: 2017-08-23
keywords: powershell,cmdlet
title: Installieren und Verwenden von Windows PowerShell Web Access
ms.openlocfilehash: 63e25fa2b1fc7c0a2b57763e337c25ece17a3296
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2017
---
# <a name="install-and-use-windows-powershell-web-access"></a>Installieren und Verwenden von Windows PowerShell Web Access

Aktualisiert: 5. November 2013 (bearbeitet: 23. August 2017)

Gilt für: Windows Server 2012 R2, Windows Server 2012

## <a name="introduction"></a>Einführung

Windows PowerShell Web Access (eingeführt in Windows Server 2012) fungiert als Windows PowerShell-Gateway, indem eine webbasierte Windows PowerShell-Konsole bereitgestellt wird, die auf einen Remotecomputer ausgerichtet ist. Dadurch können IT-Spezialisten Windows PowerShell-Befehle und -Skripts über eine Windows PowerShell-Konsole in einem Webbrowser ausführen, ohne dass Windows PowerShell, Remoteverwaltungssoftware oder Browser-Plugins auf dem Clientgerät installiert sein müssen. Zur Ausführung der webbasierten Windows PowerShell-Konsole ist lediglich ein ordnungsgemäß konfiguriertes Windows PowerShell Web Access-Gateway und ein Browser auf dem Clientgerät erforderlich, der JavaScript unterstützt und Cookies akzeptiert.

Beispiele für Clientgeräte umfassen Laptops, privat genutzte Personalcomputer, geliehene Computer, Tablet PCs, Webkiosks, Computer, auf denen kein Windows-basiertes Betriebssystem ausgeführt wird, sowie Browser auf Handys. IT-Professionals können über Geräte, die Zugriff auf eine Internetverbindung und einen Webbrowser haben, wichtige Verwaltungsaufgaben auf Windows-basierten Remoteservern ausführen.

Nach der erfolgreichen Einrichtung und Konfiguration des Gateways können Benutzer mithilfe eines Webbrowsers auf eine Windows PowerShell-Konsole zugreifen. Nachdem Benutzer die geschützte Windows PowerShell Web Access-Website geöffnet haben, können sie nach der erfolgreichen Authentifizierung eine webbasierte Windows PowerShell-Konsole ausführen.

Die Einrichtung und Konfiguration von Windows PowerShell Web Access umfasst drei Schritte:

1. [Install Windows PowerShell Web Access (Installieren von Windows PowerShell Web Access)](#install-windows-powershell-web-access)
1. [Configure the Gateway (Konfigurieren des Gateways)](#configure-the-gateway)
1. [Configure a restrictive authorization rule (Konfigurieren einer restriktiven Autorisierungsregel)](#configure-a-restrictive-authorization-rule)

Vor der Installation und Konfiguration von Windows PowerShell Web Access sollten Sie das gesamte Handbuch lesen, das Anweisungen zum Installieren, Sichern und Deinstallieren von Windows PowerShell Web Access enthält.
Im Thema [Verwendung der webbasierten Windows PowerShell-Konsole](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx) wird beschrieben, wie Benutzer sich bei der webbasierten Konsole anmelden, und es werden einige Beschränkungen und Unterschiede zwischen der webbasierten Windows PowerShell-Konsole und der **powershell.exe**-Konsole erläutert. Endbenutzer der webbasierten Konsole sollten sich das Thema [Verwendung der webbasierten Windows PowerShell-Konsole](use-the-web-based-windows-powershell-console.md) durchlesen, sie müssen den Rest dieses Handbuchs jedoch nicht lesen.

Dieses Thema enthält keine ausführliche Anleitung zum IIS-Webserverbetrieb, sondern es werden nur die Schritte beschrieben, die zum Konfigurieren des Windows PowerShell Web Access-Gateways erforderlich sind. Weitere Informationen zum Konfigurieren und Schützen von Websites in IIS finden Sie in den IIS-Dokumentationsressourcen im Abschnitt "Siehe auch".

Das folgende Diagramm zeigt die Funktionsweise von Windows PowerShell Web Access.

![Windows PowerShell Web Access-Diagramm](images/Windows-PowerShell-Web-Access-diagram.jpg)

## <a name="requirements-for-running-windows-powershell-web-access"></a>Anforderungen für die Ausführung von Windows PowerShell Web Access

Windows PowerShell Web Access erfordert die Ausführung von Webserver (IIS), .NET Framework 4.5 und Windows PowerShell 3.0 oder Windows PowerShell 4.0 auf dem Server, auf dem Sie das Gateway ausführen möchten. Sie können Windows PowerShell Web Access auf einem Server mit Windows Server 2012 R2 oder Windows Server 2012 installieren, indem Sie entweder den Assistenten zum Hinzufügen von Rollen und Features im Server-Manager oder Windows PowerShell-Bereitstellungs-Cmdlets für den Server-Manager verwenden. Wenn Sie Windows PowerShell Web Access mithilfe des Server-Managers oder seiner Bereitstellungs-Cmdlets installieren, werden die erforderlichen Rollen und Features im Rahmen des Installationsvorgangs automatisch hinzugefügt.

Mithilfe von Windows PowerShell Web Access können Remotebenutzer auf Computer der Organisation über Windows PowerShell in einem Webbrowser zugreifen. Obwohl Windows PowerShell Web Access ein benutzerfreundliches und leistungsfähiges Verwaltungstool ist, ist der webbasierte Zugriff mit Sicherheitsrisiken verbunden. Daher sollte eine möglichst sichere Konfiguration gewählt werden. Administratoren, die das Windows PowerShell Web Access-Gateway konfigurieren, wird die Verwendung der verfügbaren Sicherheitsebenen empfohlen. Damit sind die auf Cmdlets basierenden Autorisierungsregeln von Windows PowerShell Web Access sowie die Sicherheitsebenen gemeint, die im Webserver (IIS) und in Drittanbieteranwendungen verfügbar sind. In dieser Dokumentation wird sowohl auf nicht sichere Konfigurationen, die nur für Testumgebungen empfohlen werden, als auch auf Konfigurationen eingegangen, die für sichere Bereitstellungen empfohlen werden.

## <a name="browser-and-client-device-support"></a>Unterstützung für Browser und Clientgeräte

Windows PowerShell Web Access unterstützt die folgenden Internetbrowser.
Obwohl es keine offizielle Unterstützung für mobile Browser gibt, kann die webbasierte Windows PowerShell-Konsole in vielen dieser Browser ausgeführt werden. Andere Browser, die Cookies zulassen, JavaScript ausführen und HTTPS-Websites ausführen, sollten ebenfalls funktionieren. Offizielle Tests wurden jedoch nicht durchgeführt.

### <a name="supported-desktop-computer-browsers"></a>Unterstützte Desktopcomputerbrowser

- Windows Internet Explorer für Microsoft Windows 8.0, 9.0, 10.0 und 11.0
- Mozilla Firefox 10.0.2
- Google Chrome 17.0.963.56m für Windows
- Apple Safari 5.1.2 für Windows
- Apple Safari 5.1.2 für Mac OS

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Mobile Geräte oder Browser, für die Minimaltests durchgeführt wurden

- Windows Phone 7 und 7.5
- Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)
- Apple Safari für iPhone-Betriebssystem 5.0.1
- Apple Safari für iPad 2-Betriebssystem 5.0.1

### <a name="browser-requirements"></a>Browseranforderungen

Browser müssen folgende Anforderungen erfüllen, um die webbasierte Windows PowerShell Web Access-Konsole verwenden zu können.

- Zulassen von Cookies von der Website des Windows PowerShell Web Access-Gateways.
- Öffnen und Lesen von HTTPS-Seiten.
- Öffnen und Ausführen von Websites, die JavaScript verwenden.

## <a name="recommended-quick-deployment"></a>Empfohlene schnelle Bereitstellung

Sie können das Windows PowerShell Web Access-Gateway auf einem Server mit Windows Server 2012 R2 oder Windows Server 2012 installieren, indem Sie entweder Windows PowerShell-Cmdlets oder den Assistenten zum Hinzufügen von Rollen und Features im Server-Manager verwenden. Verwenden Sie für schnelle Installation und Konfiguration Windows PowerShell-Cmdlets, wie in diesem Abschnitt beschrieben.

1. [Install Windows PowerShell Web Access (Installieren von Windows PowerShell Web Access)](#install-Windows-powershell-web-access)
1. [Configure the Gateway (Konfigurieren des Gateways)](#configure-the-gateway)
1. [Configure a restrictive authorization rule (Konfigurieren einer restriktiven Autorisierungsregel)](#configure-a-restrictive-authorization-rule)

### <a name="install-windows-powershell-web-access"></a>Installieren von Windows PowerShell Web Access

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a>So installieren Sie Windows PowerShell Web Access mithilfe von Windows PowerShell-Cmdlets

1. Öffnen Sie eine Windows PowerShell-Sitzung mit erhöhten Benutzerrechten, indem Sie einen der folgenden Schritte durchführen.
    - Klicken Sie auf dem Windows-Desktop mit der rechten Maustaste in der Taskleiste auf **Windows PowerShell** und anschließend auf **Als Administrator ausführen**.
    - Klicken Sie auf dem Windows-**Startbildschirm** mit der rechten Maustaste auf **Windows PowerShell**, und klicken Sie anschließend auf **Als Administrator ausführen**.

    >**![Hinweis](images/note.jpeg) Note** In Windows PowerShell 3.0 und 4.0 muss das Server-Manager-Cmdlet-Modul vor der Ausführung von Cmdlets, die zum Modul gehören, nicht in die Windows PowerShell-Sitzung importiert werden. Module werden automatisch importiert, wenn Sie ein zum Modul gehörendes Cmdlet zum ersten Mal ausführen. Außerdem wird die Groß- und Kleinschreibung bei Windows PowerShell-Cmdlets nicht berücksichtigt.

1. Geben Sie Folgendes ein, und drücken Sie dann die **EINGABETASTE**, wobei *Computername* für den Remotecomputer steht, auf dem Sie Windows PowerShell Web Access ggf. installieren möchten. Mit dem Parameter `-Restart` werden die Zielserver bei Bedarf automatisch neu gestartet.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart`

   >**![Hinweis](images/note.jpeg) Note**
   >
   >Bei der Installation von Windows PowerShell Web Access mithilfe von Windows PowerShell-Cmdlets werden Webserver (IIS)-Verwaltungstools nicht standardmäßig hinzugefügt. Wenn Sie die Verwaltungstools auf demselben Server wie das Windows PowerShell Web Access-Gateway installieren möchten, fügen Sie dem Installationsbefehl wie in diesem Schritt angegeben den `-IncludeManagementTools`-Parameter hinzu. Wenn Sie die Windows PowerShell Web Access-Website über einen Remotecomputer verwalten, installieren Sie das IIS-Manager-Snap-In, indem Sie die [Remoteserver-Verwaltungstools für Windows 8.1](http://go.microsoft.com/fwlink/?LinkID=304145) oder die [Remoteserver-Verwaltungstools für Windows 8](http://go.microsoft.com/fwlink/p/?LinkID=238560) auf dem Computer installieren, von dem aus Sie das Gateway verwalten möchten.
   
   Zum Installieren von Rollen oder Features auf einer Offline-VHD müssen Sie die Parameter `-ComputerName` und `-VHD` hinzufügen. Der Parameter `-ComputerName` enthält den Namen des Servers, auf dem die VHD eingebunden werden soll, und der Parameter `-VHD` enthält den Pfad zur VHD-Datei auf dem angegebenen Server.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart`

1. Stellen Sie nach Abschluss der Installation sicher, dass Windows PowerShell Web Access auf den Zielservern installiert wurde. Führen Sie dazu das Cmdlet **Get-WindowsFeature** auf einem Zielserver in einer Windows PowerShell-Konsole aus, die mit erhöhten Benutzerrechten geöffnet wurde. Sie können die Installation von Windows PowerShell Web Access auch in der Server-Manager-Konsole überprüfen, indem Sie auf der Seite **Alle Server** einen Zielserver auswählen und anschließend die Kachel **Rollen und Features** für den ausgewählten Server anzeigen. Sie können auch die Infodatei für Windows PowerShell Web Access anzeigen.

1. Nachdem Windows PowerShell Web Access installiert wurde, werden Sie aufgefordert, die Infodatei zu lesen, in der grundlegende, erforderliche Setupanweisungen für das Gateway enthalten sind. Diese Setupanweisungen finden Sie auch im nächsten Abschnitt [Konfigurieren des Gateways](#configure-the-gateway). Die Infodatei befindet sich unter **C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt.**

### <a name="configure-the-gateway"></a>Konfigurieren des Gateways

Das Cmdlet **Install-PswaWebApplication** stellt eine schnelle Möglichkeit zum Konfigurieren von Windows PowerShell Web Access dar. Sie können den Parameter `UseTestCertificate` zwar dem Cmdlet `Install-PswaWebApplication` hinzufügen können, um zu Testzwecken ein selbstsigniertes SSL-Zertifikat zu installieren, aber dies ist kein sicheres Verfahren. Verwenden Sie für eine sichere Produktionsumgebung immer ein gültiges SSL-Zertifikat, das von einer Zertifizierungsstelle signiert wurde.
Mithilfe der IIS-Manager-Konsole können Administratoren das Testzertifikat durch ein signiertes Zertifikat ihrer Wahl ersetzen.

Sie können die Konfiguration der Windows PowerShell Web Access-Webanwendung durchführen, indem Sie entweder das Cmdlet `Install-PswaWebApplication` ausführen oder im IIS-Manager GUI-basierte Konfigurationsschritte ausführen. Standardmäßig wird die Webanwendung **pswa** (und der dazugehörige Anwendungspool **pswa_pool**) durch das Cmdlet im Container **Standardwebsite** installiert, wie im IIS-Manager gezeigt. Bei Bedarf können Sie das Cmdlet anweisen, den Container „Standardwebsite“ der Webanwendung zu ändern. Der IIS-Manager bietet Konfigurationsoptionen, die für Webanwendungen verfügbar sind, beispielsweise das Ändern der Portnummer oder des SSL-Zertifikats (Secure Sockets Layer).

>**![Sicherheitshinweis](images/securitynote.jpeg) Security Note**
> 
>Es wird nachdrücklich empfohlen, dass Administratoren das Gateway so konfigurieren, dass ein gültiges, von einer Zertifizierungsstelle signiertes Zertifikat verwendet wird. 

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a>So verwenden Sie das Install-PswaWebApplication-Cmdlet, um das Windows PowerShell Web Access-Gateway mit einem Testzertifikat zu konfigurieren

1. Öffnen Sie eine Windows PowerShell-Sitzung, indem Sie einen der folgenden Schritte durchführen.

    - Klicken Sie auf dem Windows-Desktop mit der rechten Maustaste auf der Taskleiste auf **Windows PowerShell**.

    - Klicken Sie auf der Windows-Startseite**** auf **Windows PowerShell**.

2. Geben Sie Folgendes ein, und drücken Sie anschließend die **EINGABETASTE**.

    **Install-PswaWebApplication -UseTestCertificate**

  >**![Sicherheitshinweis](images/securitynote.jpeg) Security Note**
  >
  >Der Parameter `UseTestCertificate` sollte nur in einer privaten Testumgebung verwendet werden. Für sichere Produktionsumgebungen empfiehlt sich die Verwendung eines gültigen Zertifikats, das von einer Zertifizierungsstelle signiert wurde.

Beim Ausführen des Cmdlets wird die Windows PowerShell Web Access-Webanwendung im Container „Standardwebsite“ von IIS installiert. Das Cmdlet erstellt die erforderliche Infrastruktur zum Ausführen von Windows PowerShell Web Access auf der Standardwebsite `https://<server_name>/pswa`. Geben Sie zum Installieren der Webanwendung auf einer anderen Website den Websitenamen an, indem Sie den Parameter `WebSiteName` hinzufügen. Fügen Sie den Parameter `pswa`hinzu, um den Namen der Webanwendung zu ändern (der Standardname lautet `WebApplicationName` ).

Die folgenden Einstellungen werden durch die Ausführung des Cmdlets konfiguriert. Falls gewünscht, können Sie diese in der IIS-Manager-Konsole manuell ändern.

- Pfad: /pswa
- Anwendungspool: pswa_pool
- Aktivierte Protokolle: http
- Physischer Pfad: %*windir*%/Web/PowerShellWebAccess/wwwroot

**Beispiel**: `Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate`

In diesem Beispiel ergibt sich als Website für Windows PowerShell Web Access „https://\<*Servername*\>/myWebApp“.

>**![Hinweis](images/note.jpeg) Note** 
> 
>Eine Anmeldung ist erst möglich, nachdem den Benutzern durch Hinzufügen von Autorisierungsregeln der Zugriff auf die Website gestattet wurde. Weitere Informationen finden Sie unter [Konfigurieren einer restriktiven Autorisierungsregel](#configure-a-restrictive-authorization-rule) und [Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a>So verwenden Sie Install-PswaWebApplication und IIS-Manager, um das Windows PowerShell Web Access-Gateway mit einem Originalzertifikat zu konfigurieren

1. Öffnen Sie eine Windows PowerShell-Sitzung, indem Sie einen der folgenden Schritte durchführen.

    - Klicken Sie auf dem Windows-Desktop mit der rechten Maustaste auf der Taskleiste auf **Windows PowerShell**.

    - Klicken Sie auf der Windows-Startseite**** auf **Windows PowerShell**.

2. Geben Sie Folgendes ein, und drücken Sie anschließend die **EINGABETASTE**.

    **Install-PswaWebApplication**

    Die folgenden Gatewayeinstellungen werden durch die Ausführung des Cmdlets konfiguriert.
    Falls gewünscht, können Sie diese in der IIS-Manager-Konsole manuell ändern.
    Sie können auch Werte für die Parameter `WebsiteName` und `WebApplicationName` des Cmdlets `Install-PswaWebApplication` angeben.

    - Pfad: /pswa

    - Anwendungspool: pswa_pool

    - Aktivierte Protokolle: http

    - Physischer Pfad: %*windir*%/Web/PowerShellWebAccess/wwwroot

3. Öffnen Sie die IIS-Manager-Konsole, indem Sie eine der folgenden Aktionen ausführen:

    - Starten Sie auf dem Windows-Desktop den Server-Manager, indem Sie in der Windows-Taskleiste auf **Server-Manager** klicken. Klicken Sie im Menü **Tools** im Server-Manager auf **Internetinformationsdienste-Manager (IIS)**.

    - Klicken Sie auf der Windows-Startseite**** auf **Server-Manager**.

4. Erweitern Sie im IIS-Manager-Strukturbereich den Knoten für den Server, auf dem Windows PowerShell Web Access installiert ist, bis der Ordner **Sites** sichtbar ist. Erweitern Sie den Ordner **Sites**.

5. Wählen Sie die Website aus, auf der Sie die Windows PowerShell Web Access-Webanwendung installiert haben. Klicken Sie im Bereich **Aktionen** auf **Bindungen**.

6. Klicken Sie im Dialogfeld **Websitebindung** auf **Hinzufügen**.

7. Wählen Sie im Dialogfeld **Websitebindung hinzufügen** im Feld **Typ** die Option **https** aus.

8. Wählen Sie das signierte Zertifikat im Dropdownmenü des Felds **SSL-Zertifikat** aus. Klicken Sie auf **OK**. Weitere Informationen zum Anfordern eines Zertifikats finden Sie in diesem Thema unter [So konfigurieren Sie ein SSL-Zertifikat im IIS-Manager](#to-configure-an-ssl-certificate-in-iis-Manager).

    Die Windows PowerShell Web Access-Webanwendung ist jetzt für die Verwendung des signierten SSL-Zertifikats konfiguriert.

    Sie können auf Windows PowerShell Web Access zugreifen, indem Sie **https://\<Servername\>/pswa** in einem Browserfenster öffnen.

>**![Hinweis](images/note.jpeg) Note** 
> 
>Eine Anmeldung ist erst möglich, nachdem den Benutzern durch Hinzufügen von Autorisierungsregeln der Zugriff auf die Website gestattet wurde. 
>Weitere Informationen finden Sie in den Themen [Konfigurieren einer restriktiven Autorisierungsregel](#configure-a-restrictive-authorization-rule) und [Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>Konfigurieren einer restriktiven Autorisierungsregel

Nach der Installation von Windows PowerShell Web Access und der Konfiguration des Gateways können Benutzer die Anmeldeseite in einem Browser öffnen. Sie können sich jedoch erst anmelden, nachdem der Windows PowerShell Web Access-Administrator ihnen ausdrücklich Zugriff gewährt hat. Die Windows PowerShell Web Access-Zugriffssteuerung wird mithilfe der Windows PowerShell-Cmdlets verwaltet, die in der folgenden Tabelle beschrieben sind. Eine vergleichbare GUI für das Hinzufügen und Verwalten von Autorisierungsregeln ist nicht verfügbar. Ausführlichere Informationen zu Windows PowerShell Web Access-Cmdlets finden Sie in den Cmdlet-Referenzthemen unter [Windows PowerShell Web Access-Cmdlets](cmdlets/web-access-cmdlets.md).

Weitere Informationen zu Windows PowerShell Web Access-Autorisierungsregeln und -Sicherheit finden Sie unter [Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>So fügen Sie eine restriktive Autorisierungsregel hinzu

1. Öffnen Sie eine Windows PowerShell-Sitzung mit erhöhten Benutzerrechten, indem Sie einen der folgenden Schritte durchführen.

    - Klicken Sie auf dem Windows-Desktop mit der rechten Maustaste in der Taskleiste auf **Windows PowerShell** und anschließend auf **Als Administrator ausführen**.

    - Klicken Sie auf dem Windows-**Startbildschirm** mit der rechten Maustaste auf **Windows PowerShell**, und klicken Sie anschließend auf **Als Administrator ausführen**.

2. Optionaler Schritt zur Einschränkung des Benutzerzugriffs mithilfe von Sitzungskonfigurationen: Überprüfen Sie, ob Sitzungskonfigurationen, die Sie in Ihren Regeln verwenden möchten, bereits vorhanden sind. Falls diese noch nicht erstellt wurden, verwenden Sie die Anleitung zum Erstellen von Sitzungskonfigurationen unter [about_Session_Configuration_Files](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Geben Sie Folgendes ein, und drücken Sie anschließend die **EINGABETASTE**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Diese Autorisierungsregel erlaubt es einem bestimmten Benutzer, auf einen Computer im Netzwerk zuzugreifen, auf den er normalerweise zugreifen kann. Der Zugriff ist auf eine bestimmte Sitzungskonfiguration beschränkt, die die üblichen Anforderungen des Benutzers im Hinblick auf die Ausführung von Skripts und Cmdlets abdeckt.
   
   Im folgenden Beispiel wird dem Benutzer `JSmith` in der Domäne `Contoso` Zugriff auf die Verwaltung des Computers `Contoso_214` gewährt und eine Sitzungskonfiguration mit dem Namen `NewAdminsOnly` verwendet.

   `Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

4. Stellen Sie sicher, dass die Regel erstellt wurde, indem Sie das Cmdlet `Get-PswaAuthorizationRule` oder `Test-PswaAuthorizationRule -UserName <domain\user> -ComputerName <computer-name>` ausführen.

5. Beispiel: `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

Nachdem Sie eine Autorisierungsregel konfiguriert haben, können sich autorisierte Benutzer bei der webbasierten Konsole anmelden und mit der Nutzung von Windows PowerShell Web Access beginnen.

## <a name="custom-deployment"></a>Benutzerdefinierte Bereitstellung

Sie können das Windows PowerShell Web Access-Gateway auf einem Server mit Windows Server 2012 R2 oder Windows Server 2012 installieren, indem Sie den Assistenten zum Hinzufügen von Rollen und Features im Server-Manager verwenden. Nach der Installation von Windows PowerShell Web Access können Sie die Konfiguration des Gateways im IIS-Manager anpassen.

### <a name="install-windows-powershell-web-access"></a>Installieren von Windows PowerShell Web Access

#### <a name="to-install-windows-powershell-web-access-by-using-the-add-roles-and-features-wizard"></a>So installieren Sie Windows PowerShell Web Access mithilfe des Assistenten zum Hinzufügen von Rollen und Features

1. Wenn der Server-Manager bereits geöffnet ist, fahren Sie mit dem nächsten Schritt fort. Ist der Server-Manager noch nicht geöffnet, öffnen Sie ihn mit einer der folgenden Aktionen.

    - Starten Sie auf dem Windows-Desktop den Server-Manager, indem Sie in der Windows-Taskleiste auf **Server-Manager** klicken.

    - Klicken Sie auf der Windows-Startseite**** auf **Server-Manager**.

2. Klicken Sie im Menü **Verwalten** auf **Rollen und Funktionen hinzufügen**.

3. Wählen Sie auf der Seite **Installationstyp auswählen** die Option **Rollenbasierte oder featurebasierte Installation** aus. Klicken Sie auf **Weiter**.

4. Wählen Sie auf der Seite **Zielserver auswählen** einen Server aus dem Serverpool aus, oder wählen Sie eine Offline-VHD aus. Um eine Offline-VHD als Zielserver auszuwählen, müssen Sie zuerst den Server auswählen, auf dem die VHD eingebunden werden soll. Wählen Sie anschließend die VHD-Datei aus. Informationen zum Hinzufügen von Servern zu Ihrem Serverpool finden Sie in der Server-Manager-Hilfe. Klicken Sie nach dem Auswählen des Zielservers auf **Weiter**.

5. Erweitern Sie im Assistenten auf der Seite **Features auswählen** die Option **Windows PowerShell**, und wählen Sie anschließend **Windows PowerShell Web Access** aus.

6. Sie werden aufgefordert, erforderliche Features, wie beispielsweise .NET Framework 4.5, und Rollendienste des Webservers (IIS) hinzuzufügen. Fügen Sie die erforderlichen Features hinzu, und setzen Sie den Vorgang fort.

    >**![Hinweis](images/note.jpeg) Note** 
    >
    >Bei der Installation von Windows PowerShell Web Access mithilfe des Assistenten zum Hinzufügen von Rollen und Features wird auch Webserver (IIS) einschließlich IIS-Manager-Snap-In installiert. Das Snap-In und andere IIS-Verwaltungstools werden standardmäßig installiert, wenn Sie den Assistenten zum Hinzufügen von Rollen und Features verwenden. Wenn Sie Windows PowerShell Web Access mithilfe von Windows PowerShell-Cmdlets wie im folgenden Verfahren beschrieben installieren, werden Verwaltungstools nicht standardmäßig hinzugefügt.

7. Falls die Featuredateien für Windows PowerShell Web Access nicht auf dem in Schritt 4 ausgewählten Zielserver gespeichert sind, klicken Sie auf der Seite **Installationsauswahl bestätigen** auf **Alternativen Quellpfad angeben**, und geben Sie den Pfad zu den Featuredateien an. Klicken Sie andernfalls auf **Installieren**.

8. Nachdem Sie auf **Installieren** geklickt haben, werden auf der Seite **Installationsstatus** der Installationsstatus, Ergebnisse und Meldungen wie Warnungen, Fehler oder nach der Installation auszuführende Konfigurationsschritten angezeigt, die für Windows PowerShell Web Access erforderlich sind. Nachdem Windows PowerShell Web Access installiert wurde, werden Sie aufgefordert, die Infodatei zu lesen, in der grundlegende, erforderliche Setupanweisungen für das Gateway enthalten sind. Diese Anweisungen sind auch in diesem Thema enthalten. Der Pfad zu der Readme-Datei ist `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>Konfigurieren des Gateways

Die Anweisungen in diesem Abschnitt gelten für die Installation der Windows PowerShell Web Access-Webanwendung in einem Unterverzeichnis der Website, und nicht im Stammverzeichnis. Dieses GUI-basierte Verfahren entspricht den Aktionen, die vom Cmdlet `Install-PswaWebApplication` durchgeführt werden. Dieser Abschnitt enthält auch Anweisungen zur Verwendung des IIS-Managers zum Konfigurieren des Windows PowerShell Web Access-Gateways als Stammwebsite.

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a>So verwenden Sie den IIS-Manager, um das Gateway auf einer vorhandenen Website zu konfigurieren

1. Öffnen Sie die IIS-Manager-Konsole, indem Sie eine der folgenden Aktionen ausführen:

    - Starten Sie auf dem Windows-Desktop den Server-Manager, indem Sie in der Windows-Taskleiste auf **Server-Manager** klicken. Klicken Sie im Menü **Tools** im Server-Manager auf **Internetinformationsdienste-Manager (IIS)**.

    - Geben Sie auf dem Windows-**Startbildschirm** einen beliebigen Teil des Namens **Internetinformationsdienste-Manager (IIS)** ein. Klicken Sie auf die Verknüpfung, wenn diese in den **Apps**-Ergebnissen angezeigt wird.

2. Erstellen Sie einen neuen Anwendungspool für Windows PowerShell Web Access. Erweitern Sie den Knoten des Gatewayservers im IIS-Manager-Strukturbereich, wählen Sie die **Anwendungspools** aus, und klicken Sie im Bereich **Aktionen** auf **Anwendungspool hinzufügen**.

3. Fügen Sie einen neuen Anwendungspool mit dem Namen **pswa_pool** hinzu, oder geben Sie einen anderen Namen an. Klicken Sie auf **OK**.

4. Erweitern Sie im IIS-Manager-Strukturbereich den Knoten für den Server, auf dem Windows PowerShell Web Access installiert ist, bis der Ordner **Sites** sichtbar ist. Wählen Sie den Ordner **Sites** aus.

5. Klicken Sie mit der rechten Maustaste auf die Website (z.B. **Standardwebsite**), der Sie die Windows PowerShell Web Access-Website hinzufügen möchten, und klicken Sie anschließend auf **Anwendung hinzufügen**.

6. Geben Sie im Feld **Alias** „pswa“ ein, oder geben Sie einen anderen Alias an. Der Alias wird zum Namen des virtuellen Verzeichnisses. In der folgenden URL steht **pswa** z.B. für den Alias, der in diesem Schritt angegeben wurde:**https://\<Servername\>/pswa**.

7. Wählen Sie im Feld **Anwendungspool** den Anwendungspool aus, den Sie in Schritt 3 erstellt haben.

8. Suchen Sie im Feld **Physischer Pfad** nach dem Speicherort der Anwendung. Sie können den Standardspeicherort %%amp;quot;%windir%/Web/PowerShellWebAccess/wwwroot%%amp;quot;% verwenden. Klicken Sie auf **OK**.

9. Führen Sie die Schritte im Verfahren „So konfigurieren Sie ein SSL-Zertifikat im IIS-Manager“ in diesem Thema aus.

10. ![](images/SecurityNote.jpeg) Optionaler Sicherheitsschritt:

    Doppelklicken Sie im Inhaltsbereich auf **SSL-Einstellungen**, während die Website im Strukturbereich ausgewählt ist. Wählen Sie die Option **SSL erforderlich** aus, und klicken Sie anschließend im Bereich **Aktionen** auf **Übernehmen**. Optional können Sie es im Bereich **SSL-Einstellungen** obligatorisch machen, dass Benutzer, die eine Verbindung mit der Windows PowerShell Web Access-Website herstellen, über Clientzertifikate verfügen. Clientzertifikate dienen dazu, die Identität des Benutzers eines Clientgeräts zu überprüfen. Weitere Informationen dazu, wie das Anfordern von Clientzertifikaten die Sicherheit von Windows PowerShell Web Access erhöhen kann, finden Sie unter [Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md) in diesem Handbuch.

11. Öffnen Sie eine Browsersitzung auf einem Clientgerät. Weitere Informationen zu unterstützten Browsern und Geräten finden Sie in diesem Thema unter [Unterstützung für Browser und Clientgeräte](#browser-and-client-device-support).

12. Öffnen Sie die neue Windows PowerShell Web Access-Website **https://\<*Gatewayservername*\>/pswa**.

    Der Browser sollte die Anmeldeseite der Windows PowerShell Web Access-Konsole anzeigen.

    >**![Hinweis](images/note.jpeg) Note** 
    > 
    >Eine Anmeldung ist erst möglich, nachdem den Benutzern durch Hinzufügen von Autorisierungsregeln der Zugriff auf die Website gestattet wurde. 
    >Weitere Informationen finden Sie in den Themen [Konfigurieren einer restriktiven Autorisierungsregel](#configure-a-restrictive-authorization-rule) und [Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

13. Führen Sie in einer mit erhöhten Benutzerrechten (Als Administrator ausführen) geöffneten Windows PowerShell-Sitzung das folgende Skript aus (hierbei entspricht *Anwendungspoolname* dem Namen des in Schritt 3 erstellten Anwendungspools), um dem Anwendungspool Zugriffsrechte für die Autorisierungsdatei zu erteilen.

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    Führen Sie den folgenden Befehl aus, um die vorhandenen Zugriffsrechte für die Autorisierungsdatei anzuzeigen:

        c:\windows\system32\icacls.exe $authorizationFile

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a>So verwenden Sie den IIS-Manager, um das Gateway als Stammwebsite mit einem Testzertifikat zu konfigurieren

1. Öffnen Sie die IIS-Manager-Konsole, indem Sie eine der folgenden Aktionen ausführen:

    - Starten Sie auf dem Windows-Desktop den Server-Manager, indem Sie in der Windows-Taskleiste auf **Server-Manager** klicken. Klicken Sie im Menü **Tools** im Server-Manager auf **Internetinformationsdienste-Manager (IIS)**.

    - Geben Sie auf dem Windows-**Startbildschirm** einen beliebigen Teil des Namens **Internetinformationsdienste-Manager (IIS)** ein. Klicken Sie auf die Verknüpfung, wenn diese in den **Apps**-Ergebnissen angezeigt wird.

2. Erweitern Sie im IIS-Manager-Strukturbereich den Knoten für den Server, auf dem Windows PowerShell Web Access installiert ist, bis der Ordner **Sites** sichtbar ist. Wählen Sie den Ordner **Sites** aus.

3. Klicken Sie im Bereich **Aktionen** auf **Website hinzufügen**.

4. Geben Sie einen Namen für die Website ein, z.B. **Windows PowerShell Web Access**.

5. Für die neue Website wird automatisch ein Anwendungspool erstellt. Wenn Sie einen anderen Anwendungspool verwenden möchten, klicken Sie auf **Auswählen**, um einen Anwendungspool zum Zuordnen zur neuen Website auszuwählen. Wählen Sie den alternativen Anwendungspool im Dialogfeld **Anwendungspool auswählen** aus, und klicken Sie anschließend auf **OK**.

6. Navigieren Sie im Textfeld **Physischer Pfad** zu %*windir*%/Web/PowerShellWebAccess/wwwroot.

7. Wählen Sie unter **Bindung** im Feld **Typ** die Option **https** aus.

8. Weisen Sie der Website eine Portnummer zu, die noch nicht von einer anderen Website oder -anwendung verwendet wird. Sie können den **netstat**-Befehl in einem Eingabeaufforderungsfenster ausführen, um nach offenen Ports zu suchen. Die Standardportnummer ist 443.

    Ändern Sie den Standardport, falls Port 443 bereits von einer anderen Website verwendet wird oder wenn das Ändern der Portnummer aus anderen Sicherheitsgründen notwendig ist. Falls eine andere Website, die auf dem Gatewayserver ausgeführt wird, den ausgewählten Port verwendet, wird eine Warnung angezeigt, wenn Sie im Dialogfeld **Website hinzufügen** auf **OK** klicken. Sie müssen einen nicht verwendeten Port zum Ausführen von Windows PowerShell Web Access verwenden.

9. Falls dies für Ihre Organisation erforderlich ist, können Sie optional einen Hostnamen angeben, der für die Organisation und Benutzer sinnvoll ist, z.B. **www.contoso.com**. Klicken Sie auf **OK**.

10. Zur Erhöhung der Sicherheit von Produktionsumgebungen wird dringend dazu geraten, ein gültiges Zertifikat bereitzustellen, das von einer Zertifizierungsstelle signiert wurde. Sie müssen ein SSL-Zertifikat bereitstellen, weil Benutzer die Verbindung mit Windows PowerShell Web Access nur über eine HTTPS-Website herstellen können. Weitere Informationen zum Anfordern eines Zertifikats finden Sie in diesem Thema unter [So konfigurieren Sie ein SSL-Zertifikat im IIS-Manager](#to-configure-an-ssl-certificate-in-iis-Manager).

11. Klicken Sie auf **OK**, um das Dialogfeld **Website hinzufügen** zu schließen.

12. Führen Sie in einer mit erhöhten Benutzerrechten (Als Administrator ausführen) geöffneten Windows PowerShell-Sitzung das folgende Skript aus (hierbei entspricht *Anwendungspoolname* dem Namen des in Schritt 4 erstellten Anwendungspools), um dem Anwendungspool Zugriffsrechte für die Autorisierungsdatei zu erteilen.

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    Führen Sie den folgenden Befehl aus, um die vorhandenen Zugriffsrechte für die Autorisierungsdatei anzuzeigen:

        c:\windows\system32\icacls.exe $authorizationFile

13. Klicken Sie, während die neue Website im IIS-Manager-Strukturbereich ausgewählt ist, im Aktionsbereich **** auf **Start** , um die Website zu starten.

14. Öffnen Sie eine Browsersitzung auf einem Clientgerät. Weitere Informationen zu unterstützten Browsern und Geräten finden Sie in diesem Dokument unter [Unterstützung für Browser und Clientgeräte](#browser-and-client-device-support).

15. Öffnen Sie die neue Windows PowerShell Web Access-Website.

    Da die Stammwebsite auf den Windows PowerShell Web Access-Ordner verweist, sollte im Browser die Anmeldeseite von Windows PowerShell Web Access angezeigt werden, wenn Sie **https://\<*Gatewayservername*\> öffnen. Es sollte nicht erforderlich sein, der URL **/pswa** hinzuzufügen.

    >**![Hinweis](images/note.jpeg) Note** 
    > 
    >Eine Anmeldung ist erst möglich, nachdem den Benutzern durch Hinzufügen von Autorisierungsregeln der Zugriff auf die Website gestattet wurde. 
    >Weitere Informationen finden Sie in den Themen [Konfigurieren einer restriktiven Autorisierungsregel](#configure-a-restrictive-authorization-rule) und [Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>Konfigurieren einer restriktiven Autorisierungsregel

Nach der Installation von Windows PowerShell Web Access und der Konfiguration des Gateways können Benutzer die Anmeldeseite in einem Browser öffnen. Sie können sich jedoch erst anmelden, nachdem der Windows PowerShell Web Access-Administrator ihnen ausdrücklich Zugriff gewährt hat. Die Windows PowerShell Web Access-Zugriffssteuerung wird mithilfe der Windows PowerShell-Cmdlets verwaltet, die in der folgenden Tabelle beschrieben sind. Eine vergleichbare GUI für das Hinzufügen und Verwalten von Autorisierungsregeln ist nicht verfügbar. Ausführlichere Informationen zu Windows PowerShell Web Access-Cmdlets finden Sie in den Cmdlet-Referenzthemen unter [Windows PowerShell Web Access-Cmdlets](cmdlets/web-access-cmdlets.md).

Weitere Informationen zu Windows PowerShell Web Access-Autorisierungsregeln und -Sicherheit finden Sie unter [Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>So fügen Sie eine restriktive Autorisierungsregel hinzu

1. Öffnen Sie eine Windows PowerShell-Sitzung mit erhöhten Benutzerrechten, indem Sie einen der folgenden Schritte durchführen.

    - Klicken Sie auf dem Windows-Desktop mit der rechten Maustaste in der Taskleiste auf **Windows PowerShell** und anschließend auf **Als Administrator ausführen**.

    - Klicken Sie auf dem Windows-**Startbildschirm** mit der rechten Maustaste auf **Windows PowerShell**, und klicken Sie anschließend auf **Als Administrator ausführen**.

2. ![Sicherheitshinweis](images/SecurityNote.jpeg) Optionaler Schritt zum Einschränken des Benutzerzugriffs mithilfe von Sitzungskonfigurationen:

    Überprüfen Sie, dass die Sitzungskonfigurationen, die Sie in Ihren Regeln verwenden möchten, bereits vorhanden sind. Falls diese noch nicht erstellt wurden, verwenden Sie die Anleitung zum Erstellen von Sitzungskonfigurationen unter [about_Session_Configuration_Files](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Geben Sie Folgendes ein, und drücken Sie anschließend die **EINGABETASTE**.

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    Diese Autorisierungsregel erlaubt es einem bestimmten Benutzer, auf einen Computer im Netzwerk zuzugreifen, auf den er normalerweise zugreifen kann. Der Zugriff ist auf eine bestimmte Sitzungskonfiguration beschränkt, die die üblichen Anforderungen des Benutzers im Hinblick auf die Ausführung von Skripts und Cmdlets abdeckt. 
    
    Im folgenden Beispiel wird dem Benutzer `JSmith` in der Domäne `Contoso` Zugriff auf die Verwaltung des Computers `Contoso_214` gewährt und eine Sitzungskonfiguration mit dem Namen `NewAdminsOnly` verwendet.

        Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4. Stellen Sie sicher, dass die Regel erstellt wurde, indem Sie das Cmdlet `Get-PswaAuthorizationRule` oder `Test-PswaAuthorizationRule -UserName '<domain\user>' -ComputerName <computer-name>` ausführen. 

    Beispiel: `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

Nachdem Sie eine Autorisierungsregel konfiguriert haben, können sich autorisierte Benutzer bei der webbasierten Konsole anmelden und mit der Nutzung von Windows PowerShell Web Access beginnen.

## <a name="configure-a-genuine-certificate"></a>Konfigurieren eines Originalzertifikats

Für sichere Produktionsumgebungen sollten Sie stets ein gültiges, von einer Zertifizierungsstelle (ZS) signiertes SSL-Zertifikat verwenden. In diesem Abschnitt wird das Verfahren beschrieben, mit dem Sie ein gültiges SSL-Zertifikat von einer Zertifizierungsstelle beziehen und anwenden.

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a>So konfigurieren Sie ein SSL-Zertifikat im IIS-Manager

1. Wählen Sie im IIS-Manager-Strukturbereich den Server aus, auf dem Windows PowerShell Web Access installiert ist.

2. Doppelklicken Sie im Inhaltsbereich auf **Serverzertifikate**.

3. Führen Sie im Bereich **Aktionen** eine der folgenden Aktionen aus. Weitere Informationen zur Konfiguration von Serverzertifikaten in IIS finden Sie unter [Konfigurieren von Serverzertifikaten in IIS 7](https://technet.microsoft.com/library/cc732230.aspx).

    - Klicken Sie auf **Importieren**, um ein vorhandenes gültiges Zertifikat von einem Speicherort im Netzwerk zu importieren.

    - Klicken Sie auf **Zertifikatanforderung erstellen**, um ein Zertifikat von einer Zertifizierungsstelle wie [VeriSign](http://www.verisign.com/), [Thawte](https://www.thawte.com/) oder [GeoTrust](https://www.geotrust.com/) anzufordern. Der allgemeine Name des Zertifikats muss dem Hostheader in der Anforderung entsprechen.

      Wenn der Clientbrowser beispielsweise http://www.contoso.com/ anfordert, muss der allgemeine Name ebenfalls http://www.contoso.com/ lauten. Dies ist die sicherste und empfohlene Option, um das Windows PowerShell Web Access-Gateway mit einem Zertifikat zu versehen.

    - Klicken Sie auf **Selbstsigniertes Zertifikat erstellen**, um ein Zertifikat zu erstellen, das Sie sofort verwenden und später bei Bedarf von einer Zertifizierungsstelle signieren lassen können. Geben Sie einen Anzeigenamen für das selbstsignierte Zertifikat an, z.B. **Windows PowerShell Web Access**. Diese Vorgehensweise ist als nicht sicher anzusehen und wird nur für eine private Testumgebung empfohlen.

4. Wählen Sie nach der Erstellung bzw. Beschaffung eines Zertifikats die Website, auf die das Zertifikat angewendet werden soll (z.B. **Standardwebsite**), im IIS-Manager-Strukturbereich aus. Klicken Sie anschließend im Bereich **Aktionen** auf **Bindungen**.

5. Fügen Sie im Dialogfeld **Websitebindung hinzufügen** eine Bindung vom Typ **https** für die Website hinzu, falls noch keine Bindung angezeigt wird. Wenn Sie kein selbstsigniertes Zertifikat verwenden, geben Sie den Hostnamen aus Schritt 3 dieses Verfahrens an. Wenn Sie ein selbstsigniertes Zertifikat verwenden, ist dieser Schritt nicht erforderlich.

6. Wählen Sie das Zertifikat aus, das Sie in Schritt 3 dieses Verfahrens abgerufen oder erstellt haben, und klicken Sie anschließend auf **OK**.

## <a name="using-the-web-based-windows-powershell-console"></a>Verwenden der webbasierten Windows PowerShell-Konsole

Nachdem Windows PowerShell Web Access installiert und die Gatewaykonfiguration wie in diesem Thema beschrieben abgeschlossen wurde, ist die webbasierte Windows PowerShell-Konsole für die Verwendung bereit. Weitere Informationen zu den ersten Schritten mit der webbasierten Konsole finden Sie unter [Verwendung der webbasierten Windows PowerShell-Konsole](use-the-web-based-windows-powershell-console.md).

## <a name="see-also"></a>Weitere Informationen

- [Internet Information Services (IIS) 7.0 Documentation (Dokumentation zu Internetinformationsdienste (IIS) 7.0)](https://technet.microsoft.com/library/cc753433.aspx)
- [IIS Manager 7.0 Help (Hilfe zum IIS-Manager 7.0)](https://technet.microsoft.com/library/cc732664.aspx)
- [Configure Web Server Security (IIS 7) (Konfigurieren der Webserversicherheit (IIS 7))](https://technet.microsoft.com/library/cc731278.aspx)
- [IPsec Deployment Resources (Ressourcen zur IPsec-Bereitstellung)](https://technet.microsoft.com/network/bb531150)
