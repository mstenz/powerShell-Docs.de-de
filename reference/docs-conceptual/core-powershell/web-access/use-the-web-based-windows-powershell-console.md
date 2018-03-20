---
ms.date: 2017-08-23
keywords: powershell,cmdlet
title: Verwendung der webbasierten Windows PowerShell-Konsole
ms.openlocfilehash: a6c9812253309ba1225141cfd48d0f1c8b8785b5
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="use-the-web-based-windows-powershell-console"></a>Use the Web-based Windows PowerShell Console

Aktualisiert: 24. Juni 2013

Gilt für: Windows Server 2012 R2, Windows Server 2012

Windows PowerShell Web Access ermöglicht Benutzern die Anmeldung gesicherten Website zur Verwendung von Windows PowerShell-Sitzungen, Cmdlets und Skripts zur Verwaltung eines Remotecomputers.

Da die Windows PowerShell-Konsole in einem Webbrowser ausgeführt wird, kann sie von einer Vielzahl von Clientgeräten aus geöffnet werden. Dazu zählen fast alle Geräte, die einen Webbrowser verwenden können.

Die webbasierte Windows PowerShell-Konsole steuert einen Remotecomputer, der von Benutzern im Zuge der Anmeldung angegeben wird. 

Dieser Artikel behandelt die Anmeldung für die ersten Schritte mit der webbasierten Windows PowerShell Web Access-Konsole.

Der Artikel beschreibt nicht die Verwendung von Windows PowerShell oder das Ausführen von Cmdlets und Skripts. Informationen zur Verwendung von Windows PowerShell und Skriptressourcen erhalten Sie im Abschnitt [Siehe auch](#see-also) am Ende des Artikels.

## <a name="supported-browsers-and-client-devices"></a>Unterstützte Browser und Clientgeräte

Windows PowerShell Web Access unterstützt die folgenden Internetbrowser. Obwohl es keine offizielle Unterstützung für mobile Browser gibt, kann die webbasierte Windows PowerShell-Konsole in vielen dieser Browser ausgeführt werden. Andere Browser, die Cookies zulassen, JavaScript ausführen und HTTPS-Websites ausführen, sollten ebenfalls funktionieren. Offizielle Tests wurden jedoch nicht durchgeführt.

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

## <a name="signing-in-to-windows-powershell-web-access"></a>Anmelden bei Windows PowerShell Web Access

Ihr Windows PowerShell Web Access-Administrator sollte Ihnen eine URL bereitstellen, die die Adresse der Website des Windows PowerShell Web Access-Gateways Ihrer Organisation ist.
Standardmäßig ist die Adresse dieser Website *https://\<Servername\>/pswa*.

Bevor Sie sich bei Windows PowerShell Web Access anmelden, sollten Sie sichergehen, dass Sie über den Namen oder die IP-Adresse des zu verwaltenden Remotecomputers verfügen.
Sie müssen auf dem Remotecomputer ein autorisierter Benutzer sein. Außerdem müssen Sie darauf die Remoteverwaltung zulassen.
Weitere Informationen dazu, wie Sie Ihren Computer so konfigurieren, dass eine Remoteverwaltung möglich ist, finden Sie unter [Aktivieren und Verwenden von Remotebefehlen in Windows PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting).

Die einfachste Möglichkeit, die Remoteverwaltung auf Ihrem Computer zu konfigurieren, besteht in der Ausführung des Cmdlets **Enable-PSRemoting -force** auf dem Computer in einer Windows PowerShell-Sitzung, die mit erhöhten Benutzerrechten (**Als Administrator ausführen**) geöffnet wurde.

### <a name="to-sign-in-to-windows-powershell-web-access"></a>So melden Sie sich bei Windows PowerShell Web Access an

1. Öffnen Sie die Windows PowerShell Web Access-Website in einem Fenster oder auf einer Registerkarte des Internetbrowsers.

1. Geben Sie auf der Windows PowerShell Web Access-Anmeldeseite Ihren Netzwerkbenutzernamen und das dazugehörige Kennwort an, außerdem den Namen des Computers, den Sie verwalten möchten (und auf dem Sie ein autorisierter Benutzer sind). Wenn Sie der Windows PowerShell Web Access-Administrator angewiesen hat, einen URI zu einer benutzerdefinierten Website oder einem Proxyserver statt eines Computernamens zu verwenden, wählen Sie **Verbindungs-URI** im Feld **Verbindungstyp** und geben Sie den URI an.

    > ![Hinweis](images/Note.jpeg) **Note**:
    >
    > - Wenn der Zielcomputer einer Arbeitsgruppe angehört, müssen Sie die folgende Syntax verwenden, um den Benutzernamen anzugeben und sich am Computer anzumelden: `<workgroup_name>\<user_name>`.
    > - Wenn es sich beim Zielcomputer um einen Gatewayserver handelt, können Sie `localhost` im Feld „Computername“ angeben.
    > - Sollte es sich beim Zielcomputer um einen Gatewayserver handeln und sich der Gatewayserver in einer Arbeitsgruppe befinden, müssen Sie `<workgroup name>\<user_name>` im Feld „Benutzername“ verwenden. Sie können `localhost` im Feld „Computername“ verwenden.

1. Der Abschnitt **Optionale Verbindungseinstellungen** bezieht sich auf Autorisierungsanforderungen des zu verwaltenden Remotecomputers. Weitere Informationen zu den Parametern, die den optionalen Verbindungseinstellungen entsprechen, finden Sie in der Hilfe zum Cmdlet [Enter-PSSession](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession).

    In der Regel sind die Anmeldeinformationen zum Passieren des Windows PowerShell Web Access-Gateways dieselben, die vom zu verwaltenden Remotecomputer erkannt werden. Wenn Sie jedoch andere Anmeldeinformationen zur Verwaltung des in Schritt 2 angegebenen Remotecomputers verwenden möchten, erweitern Sie den Abschnitt **Optionale Verbindungseinstellungen**, und geben Sie die abweichenden Anmeldeinformationen an. Fahren Sie ansonsten mit Schritt 6 fort.

1. Wenn der Windows PowerShell Web Access-Administrator eine benutzerdefinierte Konfiguration für Windows PowerShell Web Access-Benutzer erstellt hat, geben Sie den Namen der Sitzungskonfiguration in das Feld **Konfigurationsname** ein. Weitere Informationen zu Sitzungskonfigurationen finden Sie unter [about_Session_Configurations](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Belassen Sie den **Authentifizierungstyp** als **Standard**, sofern Sie nicht vom Windows PowerShell Web Access-Administrator gegenteilige Anweisungen erhalten haben.

1. Klicken Sie auf **Anmelden**.

## <a name="signing-out-and-timing-out"></a>Abmelden und Timeout

Sie werden in den folgenden Situationen von einer webbasierten Windows PowerShell-Sitzung abgemeldet.

- Wenn Sie unten rechts in der Konsole auf **Abmelden** klicken. (Nur Windows Server 2012)

- Wenn Sie unten rechts in der Konsole auf **Speichern** oder **Beenden** klicken (nur Windows Server 2012 R2). Durch Klicken auf **Speichern** wird Ihre Windows PowerShell Web Access-Sitzung gespeichert und geschlossen. Sie können zu einem späteren Zeitpunkt die Verbindung mit der Sitzung wiederherstellen. Wenn Sie sich wieder bei Windows PowerShell Web Access anmelden, zeigt Windows PowerShell Web Access eine Liste der gespeicherten Sitzungen an. Sie können entweder eine gespeicherte Sitzung auswählen und die Verbindung erneut herstellen oder eine neue Sitzung starten. Die maximale Anzahl geöffneter (sowohl gespeicherter als auch aktiver Sitzungen), die für Benutzer zulässig sind, wird vom Gatewayadministrator konfiguriert.

    Wenn Sie auf **Beenden** klicken, werden Sie von der Windows PowerShell Web Access-Sitzung abgemeldet, ohne dass diese gespeichert wird.

- Wenn Sie sich zur Verwaltung eines anderen Remotecomputers in derselben Browsersitzung oder einer neuen Registerkarte desselben Browsers anmelden. (Dies gilt nicht, wenn Windows Server 2012 R2 auf dem Gatewayserver ausgeführt wird. Windows PowerShell Web Access unter Windows Server 2012 R2 lässt mehrere Benutzersitzungen auf neuen Registerkarten in derselben Browsersitzung zu.) Weitere Informationen dazu, wie Sie mehr als eine aktive Sitzung auf demselben Computer starten, finden Sie unter „Aufbauen von Verbindungen zu mehreren Zielcomputern gleichzeitig“ im Abschnitt [Einschränkungen der webbasierten Konsole](#limitations-of-the-web-based-console) dieses Artikels.

- Wenn Sie mehr als 20 Minuten inaktiv sind. Der Gatewayadministrator kann den Timeoutzeitraum für Inaktivität anpassen. Weitere Informationen finden Sie unter [Sitzungsverwaltung](authorization-rules-and-security-features-of-windows-powershell-web-access.md#session-management).

    - Wenn Sie aufgrund von Netzwerkfehlern oder anderen ungeplanten Herunterfahrvorgängen oder Ausfällen in der webbasierten Konsole von Sitzungen getrennt werden und nicht weil Sie die Sitzungen selbst geschlossen haben, wird die Windows PowerShell Web Access-Sitzung weiter ausgeführt. Die Verbindung mit dem Zielcomputer bleibt bestehen, bis das Timeout auf dem Client überschritten wird. In der Standardeinstellung beträgt dieses Zeitlimit 20 Minuten, was vom Gatewayadministrator angepasst werden kann. Die Sitzung wird entweder standardmäßig nach 20 Minuten oder nach der vom Gatewayadministrator festgelegten Timeoutperiode getrennt, je nachdem, was kürzer ist.

        Wenn der Gatewayserver unter Windows Server 2012 R2 ausgeführt wird, ermöglicht Windows PowerShell Web Access Benutzern das erneute Verbinden mit gespeicherten Sitzungen zu einem späteren Zeitpunkt. Die Benutzer können jedoch gespeicherte Sitzungen erst anzeigen bzw. die Verbindung erneut herstellen, nachdem das vom Gatewayadministrator festgelegte Timeout abgelaufen ist.

- Wenn Sie das Browserfenster oder die Browserregisterkarte schließen.

- Wenn Sie das Clientgerät ausschalten, auf dem der Browser ausgeführt wird, oder es vom Netzwerk trennen.

- Wenn Sie den **Beenden** -Befehl in der Webkonsole ausführen. Der Befehl funktioniert nicht, wenn die Sitzungskonfiguration, mit der Sie verbunden sind, zur Unterstützung des [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx)-Modus konfiguriert ist oder sich in einem eingeschränkten Runspace befindet.

Falls Sie sich wieder anmelden möchten, öffnen Sie die Windows PowerShell Web Access-Website erneut, und melden Sie sich anhand der Schritte in [Anmelden bei Windows PowerShell Web Access](#signing-in-to-windows-powershell-web-access) in diesem Artikel an.

## <a name="differences-in-the-web-based-windows-powershell-console"></a>Unterschiede bei der webbasierten Windows PowerShell-Konsole

Nach der Anmeldung bei Windows PowerShell Web Access wird im Fenster oder auf der Registerkarte des Browsers eine webbasierte Windows PowerShell-Konsole geöffnet. Die Konsole ist mit dem Remotecomputer verbunden, den Sie während der Anmeldung angegeben haben. Daher können nur die Windows PowerShell-Cmdlets und -Skripts in der Konsole verwendet werden, die auf dem Remotecomputer verfügbar sind. In diesem Abschnitt werden weitere Einschränkungen von Windows PowerShell Web Access-Konsolen sowie die Unterschiede zwischen Windows PowerShell Web Access-Konsolen und der installierten **PowerShell.exe**-Konsole beschrieben.

### <a name="functional-disparity-with-powershellexe"></a>Funktionelle Unterschiede von "PowerShell.exe"

Die Mehrzahl der Windows PowerShell-Hostfunktionen steht in der webbasierten Windows PowerShell Web Access-Konsole zur Verfügung, einige jedoch nicht.

- Verschachtelte Statusanzeigen.

  Windows PowerShell Web Access zeigt eine Status-GUI für Cmdlets an, die einen Status ausgeben, es werden jedoch nur Informationen der höchsten Statusebene angezeigt.

- Änderung der Eingabefarbe.

  Die Eingabefarbe (Vordergrund und Hintergrund) kann nicht geändert werden. Der Stil von Ausgabe-, Warn-, ausführlichen und Fehlermeldungen können alle mithilfe eines Skripts geändert werden.

- PSHostRawUserInterface.

  Windows PowerShell Web Access wird per Windows PowerShell-Remoteverwaltung implementiert und verwendet einen Remoterunspace. Windows PowerShell Web Access implementiert einige Methoden dieser Benutzeroberfläche nicht, z. B. Befehle, die in die Windows-Konsole schreiben. Befehle wie **PowerTab** funktionieren in Windows PowerShell Web Access nicht.

- Funktionstasten.

  Windows PowerShell Web Access unterstützt einige Funktionstasten nicht. In vielen Fällen liegt dies daran, dass die Befehle vom Browser reserviert sind.

### <a name="unsupported-shortcut-keys"></a>Nicht unterstützte Tastenkombinationen

Funktionstasten | Action
-- | --
STRG+C | In Windows PowerShell Web Access wird **STRG+C** vom Browser verwendet, um Inhalte zu kopieren. Die Konsole stellt eine **Abbrechen**-Schaltfläche bereit, darüber hinaus ist der Befehl **STRG+Q** zum Abbrechen von Befehlen verfügbar.
ALT+Leertaste, E, L | Durch den Bildschirmpuffer scrollen
ALT+Leertaste, E, F | Nach Text im Bildschirmpuffer suchen
ALT+Leertaste, E, K | Vom Bildschirmpuffer zu kopierenden Text auswählen
ALT+Leertaste, E, P | Daten aus der Zwischenablage in die Windows PowerShell-Konsole einfügen
ALT+Leertaste, C | Schließen der Windows PowerShell-Konsole
STRG+PAUSE | Schließen des Windows PowerShell-Fensters erzwingen
STRG+POS1 | Löschvorgang vom Anfang der aktuellen Befehlszeile durchführen
STRG+ENDE | Löschvorgang bis zum Ende der aktuellen Befehlszeile durchführen
F1 | Cursor in der Befehlszeile ein Zeichen nach rechts verschieben
F2 | Neuen Befehl durch Kopieren des letzten Befehls bis zum getippten Zeichen erstellen
F3 | Befehlszeile mit Inhalt der letzten Befehlszeile vervollständigen
F4 | Zeichen von Cursorposition löschen
F5 | Befehlsverlauf rückwärts durchsuchen. Greifen sie auf Befehle im Befehlsverlauf in Windows PowerShell Web Access zu, indem Sie in der webbasierten Konsole auf die **Verlauf**-Bildlaufschaltflächen klicken.
F7 | Einen Befehl interaktiv aus dem Befehlsverlauf auswählen
F8 | Verlauf durchsuchen und Befehle aufrufen, die dem aktuellen Text entsprechen
F9 | Einen bestimmten, nummerierten Befehl aus dem Verlauf ausführen
BILD-AUF | Den ersten Befehl im Verlauf ausführen
BILD-AB | Den letzten Befehl im Verlauf ausführen
ALT+F7 | Befehlsverlauf löschen

### <a name="limitations-of-the-web-based-console"></a>Einschränkungen der webbasierten Konsole

- Doppel-Hop

    Auf die Doppel-Hop-Einschränkung (oder die Verbindung mit einem zweiten Computer über die erste Verbindung) stoßen Sie, wenn Sie versuchen, eine neue Sitzung zu erstellen oder mit einer neuen Sitzung zu arbeiten, indem Sie Windows PowerShell Web Access verwenden. Windows PowerShell Web Access verwendet einen Remoterunspace, und **PowerShell.exe** unterstützt das Herstellen einer Remoteverbindungen mit einem zweiten Computer von einem Remoterunspace derzeit nicht. Wenn Sie beispielsweise versuchen, mithilfe des Cmdlets **Enter-PSSession** von einer bestehenden Verbindung aus eine Verbindung mit einem zweiten Remotecomputer herzustellen, können verschiedene Fehler gemeldet werden, z.B. „Netzwerkressourcen nicht verfügbar“.

    Derlei Fehler können vermieden werden, indem Ihr Administrator die CredSSP-Authentifizierung in der Netzwerkumgebung Ihrer Organisation einrichtet. Weitere Informationen zur Einrichtung der CredSSP-Authentifizierung finden Sie unter [CredSSP für Zweit-Hop-Remoting](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) auf der Microsoft-Website. Sie können auch explizite Anmeldeinformationen zur Verwaltung eines zweiten Remotecomputers angeben, denn mit impliziten Daten ist es unwahrscheinlich, dass der zweite Hop zugelassen wird.

- Remoting

    Bei Windows PowerShell Web Access gelten dieselben Einschränkungen wie bei Windows PowerShell-Remotesitzungen. Befehle, die Windows-Konsolen-APIs direkt aufrufen, etwa solche für konsolenbasierte Editoren oder textbasierte Menüprogramme, funktionieren nicht, da die Befehle nicht an die standardmäßigen Eingabe-, Ausgabe- und Fehlerpipes lesen und schreiben. Aus diesem Grund funktionieren Befehle nicht, die ausführbare Dateien wie **notepad.exe** starten oder GUI wie `OpenGridView` oder `ogv` anzeigen. Ihre Erfahrung wird durch dieses Verhalten beeinträchtigt, denn für Sie scheint es so, als würde Windows PowerShell Web Access nicht auf Ihre Befehlseingaben reagieren.

- Registerkartenvervollständigung

    Die Registerkartenvervollständigung funktioniert in einer Sitzungskonfiguration mit einem beschränkten Runspace oder einer solchen im **NoLanguage** -Modus nicht. Obwohl Administratoren eine Sitzung so konfigurieren können, dass die Registerkartenvervollständigung unterstützt wird, raten wir aus Sicherheitsgründen davon ab, da sie für nicht autorisierte Benutzer die folgenden Informationen verfügbar machen kann.

    - Interne Pfade des Dateisystems

    - Freigegebene Ordner und interne Computer

    - Variable im Runspace

    - Geladene Typen oder .NET Framework-Namespaces

    - Umgebungsvariablen

- **NoLanguage**-Sitzung oder eingeschränkter Runspace

    Benutzer, die bei einer **NoLanguage**-Sitzungskonfiguration oder einem eingeschränkten Runspace in Windows PowerShell Web Access angemeldet sind, können den **Beenden**-Befehl nicht zum Beenden der Sitzung ausführen. Zum Abmelden müssen Benutzer auf der Konsolenseite auf **Abmelden** klicken.

- Aufbauen von Verbindungen zu mehreren Zielcomputern gleichzeitig.

    Wenn Windows Server 2012 auf dem Gatewayserver ausgeführt wird, lässt Windows PowerShell Web Access nur eine Remotecomputerverbindung pro Browsersitzung zu. Die einmalige Anmeldung und anschließende Verbindung mit mehreren Remotecomputern mithilfe verschiedener Browserregisterkarten ist nicht zulässig. Beim Öffnen eines neuen Browserfensters oder einer neuen Browserregisterkarte werden Sie von Windows PowerShell Web Access dazu aufgefordert, Ihre aktuelle Sitzung zu beenden und eine neue Sitzung zu starten, damit Sie eine Verbindung zu einem neuen (oder demselben) Remotecomputer herstellen können. Falls Sie mehrere separate Sitzungen mit verschiedenen Remotecomputern verwenden möchten, können Sie mithilfe einer Funktion in Internet Explorer eine neue Sitzung erstellen. Starten Sie eine neue Browsersitzung in Internet Explorer, indem Sie **ALT** drücken, das Menü **Datei** öffnen und **Neue Sitzung** auswählen. Öffnen Sie in dieser neuen Sitzung anschließend die Windows PowerShell Web Access-Website, und melden Sie sich an, um auf einen anderen Remotecomputer zuzugreifen.

    Wenn das Windows PowerShell Web Access-Gateway unter Windows Server 2012 R2 ausgeführt wird, können Benutzer mehrere Verbindungen mit Remotecomputern auf verschiedenen Browserregisterkarten öffnen. Wenn Sie mehr als eine Verbindung mit einem Remotecomputer über die webbasierte Windows PowerShell-Konsole öffnen möchten, erkundigen Sie sich bei Ihrem Windows PowerShell Web Access-Gatewayadministrator, ob dieses Feature vom Gatewayserver unterstützt wird.

- Permanente Windows PowerShell-Sitzungen (erneute Verbindung).

    Nachdem die Sitzung mit dem Windows PowerShell Web Access-Gateway abgelaufen ist, wird die Remoteverbindung zwischen dem Gateway und dem Zielcomputer getrennt. Dabei werden alle Cmdlets und Skripts, die aktuell laufen, beendet. Es ist empfehlenswert, bei lang andauernden Aufgaben die Windows PowerShell-**-Job**-Infrastruktur zu verwenden, damit Sie Aufträge starten, die Verbindung mit dem Computer trennen und später wieder herstellen können, ohne dass der Auftrag abgebrochen wird. Ein weiterer Vorteil der Verwendung von **-Job**-Cmdlets ist, dass Sie sie mithilfe von Windows PowerShell Web Access starten, sich abmelden und später wieder anmelden können, indem Sie entweder Windows PowerShell Web Access oder einen anderen Host ausführen (z.B. Windows PowerShell Integrated Scripting Environment (ISE)).

- Ändern der Konsolengröße.

    Der Abschnitt **PowerShell.exe** -Konsolenfensters zur Verfügung.

    - Ändern der Konsolenfenstergröße per Ziehen des Mauszeigers

    - Ändern von Höhe und Breite per GUI für Konsoleneigenschaften

    - Ändern von Höhe und Breite des Konsolenfensters per Cmdlet

        Das Konsolenfenster von Windows PowerShell Web Access kann wie folgt mithilfe von Cmdlets konfiguriert werden. Im folgenden Beispiel ändert ein Benutzer die Breite der Windows PowerShell Web Access-Konsole auf **20**.

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        Die Höhe der Konsole lässt sich auf eine ähnliche Weise ändern.

        Weitere Beispiele zur Anpassung der Konsolenansicht stehen im [Windows PowerShell-Teamblog](http://blogs.msdn.com/b/powershell/) zur Verfügung.

## <a name="see-also"></a>Weitere Informationen

- [Windows PowerShell Cmdlet Reference (Windows PowerShell-Cmdlet-Verweis)](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
- [Windows PowerShell on Microsoft TechNet (Windows PowerShell in Microsoft TechNet)](https://technet.microsoft.com/library/bb978526.aspx)
- [TechNet Script Center Repository (TechNet-Skriptcenterrepository)](http://gallery.technet.microsoft.com/scriptcenter)
- [Script Center - Hey, Scripting Guy! (Skriptcenter – Hey, Scripting Guy!)](https://technet.microsoft.com/scriptcenter)
- [Windows PowerShell Team Blog (Windows PowerShell-Teamblog)](http://blogs.msdn.com/b/powershell/)
