---
ms.date: 06/27/2017
keywords: powershell,cmdlet
title: Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access
ms.openlocfilehash: c426b8cfb10829241ba244a5d840c91e1de9f66e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "62058419"
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a>Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access

Aktualisiert: 24. Juni 2013

Gilt für: Windows Server 2012 R2, Windows Server 2012

Windows PowerShell Web Access in Windows Server 2012 R2 und in Windows Server 2012 verfügt über ein restriktives Sicherheitsmodell. Benutzern muss explizit der Zugriff gewährt werden, bevor sie sich am Windows PowerShell Web Access-Gateway anmelden und die webbasierte Windows PowerShell-Konsole verwenden können.

## <a name="configuring-authorization-rules-and-site-security"></a>Konfigurieren von Autorisierungsregeln und Websitesicherheit

Nach der Installation von Windows PowerShell Web Access und der Konfiguration des Gateways können Benutzer die Anmeldeseite in einem Browser öffnen. Sie können sich jedoch erst anmelden, nachdem der Windows PowerShell Web Access-Administrator ihnen ausdrücklich Zugriff gewährt hat. Die Windows PowerShell Web Access-Zugriffssteuerung wird mithilfe der Windows PowerShell-Cmdlets verwaltet, die in der folgenden Tabelle beschrieben sind. Eine vergleichbare GUI für das Hinzufügen und Verwalten von Autorisierungsregeln ist nicht verfügbar.
Siehe [Windows PowerShell Web Access-Cmdlets](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Administratoren können `{0-n}`-Authentifizierungsregeln für Windows PowerShell Web Access definieren. Die Standardsicherheit ist nicht %%amp;quot;tolerant%%amp;quot;, sondern restriktiv: Wenn keine Authentifizierungsregel vorhanden ist, darf kein Benutzer auf irgendetwas zugreifen.

Die Cmdlets [Add-PswaAuthorizationRule](/powershell/module/powershellwebaccess/add-pswaauthorizationrule?view=winserver2012r2-ps) und [Test-PswaAuthorizationRule](/powershell/module/powershellwebaccess/test-pswaauthorizationrule?view=winserver2012r2-ps) enthalten nun unter Windows Server 2012 R2 einen „Credential“-Parameter, mit dem Sie Windows PowerShell Web Access-Autorisierungsregeln von einem Remotecomputer aus oder innerhalb einer aktiven Windows PowerShell Web Access-Sitzung hinzufügen und testen können. Wie bei anderen Windows PowerShell-Cmdlets, die über einen „Credential“-Parameter verfügen, können Sie ein „PSCredential“-Objekt als Wert des Parameters angeben. Führen Sie das Cmdlet [Get-Credential](/powershell/module/microsoft.powershell.security/Get-Credential) aus, um ein „PSCredential“-Objekt zu erstellen, das Anmeldeinformationen enthält, die Sie an einen Remotecomputer übergeben möchten.

Windows PowerShell Web Access-Authentifizierungsregeln sind Whitelist-Regeln. Jede Regel ist eine Definition einer zulässigen Verbindung zwischen Benutzern, Zielcomputern und bestimmten Windows PowerShell-[Sitzungskonfigurationen](/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-5.1) (auch als Endpunkte oder _Runspaces_ bezeichnet) auf angegebenen Zielcomputern.
Eine Erläuterung zu **Runspaces** finden Sie unter [Beginning Use of PowerShell Runspaces (Verwenden von PowerShell-Runspaces)](https://blogs.technet.microsoft.com/heyscriptingguy/2015/11/26/beginning-use-of-powershell-runspaces-part-1/)

> [!IMPORTANT]
> Für einen Benutzer muss nur eine Regel zutreffen, damit er Zugriff erhält. Wenn einem Benutzer der Zugriff auf einen Computer mit vollem Sprachzugriff oder ausschließlichem Zugriff auf Windows PowerShell-Remoteverwaltungs-Cmdlets gewährt wird, kann sich der Benutzer über die webbasierte Konsole an anderen Computern anmelden, die mit dem ersten Zielcomputer verbunden sind (bzw. per Hop zu diesen Computern wechseln). Die sicherste Möglichkeit, Windows PowerShell Web Access zu konfigurieren, besteht darin, Benutzern nur den Zugriff auf eingeschränkte Sitzungskonfigurationen zu gewähren, mit denen die Erledigung bestimmter Aufgaben möglich ist, die andernfalls remote ausgeführt werden müssten.

Mit den Cmdlets, auf die in [Windows PowerShell Web Access Cmdlets (Windows PowerShell Web Access-Cmdlets)](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps) verwiesen wird, kann ein Satz von Zugriffsregeln erstellt werden. Diese werden zum Autorisieren eines Benutzers auf dem Windows PowerShell Web Access-Gateway verwendet. Die Regeln unterscheiden sich von Zugriffssteuerungslisten auf dem Zielcomputer und bieten eine zusätzliche Ebene der Sicherheit für den Webzugriff. Weitere Informationen zur Sicherheit finden Sie im folgenden Abschnitt.

Falls ein Benutzer keine der vorherigen Sicherheitsebenen passieren kann, wird im Browserfenster eine allgemeine Meldung des Typs „Zugriff verweigert“ angezeigt. Obwohl die Sicherheitsdetails auf dem Gatewayserver protokolliert werden, erhalten die Benutzern keine Informationen darüber, wie viele Sicherheitsebenen sie passiert haben oder auf welcher Ebene der Anmelde- oder Authentifizierungsfehler aufgetreten ist.

Weitere Informationen zur Konfiguration von Autorisierungsregeln finden Sie unter [Konfigurieren von Autorisierungsregeln](#configuring-authorization-rules-and-site-security) in diesem Thema.

### <a name="security"></a>Sicherheit

Das Windows PowerShell Web Access-Sicherheitsmodell verfügt über vier Ebenen zwischen einem Endbenutzer der webbasierten Konsole und einem Zielcomputer. Windows PowerShell Web Access-Administratoren können Sicherheitsebenen mithilfe zusätzlicher Konfigurationsschritte in der IIS-Manager-Konsole hinzufügen. Weitere Informationen zum Schützen von Websites in der IIS-Manager-Konsole finden Sie unter [Konfigurieren der Webserversicherheit (IIS 7)](https://technet.microsoft.com/library/cc731278).

Weitere Informationen zu den bewährten IIS-Methoden und zur Verhinderung von Denial-of-Service-Angriffen finden Sie unter [Best Practices for Preventing DoS/Denial of Service Attacks](https://technet.microsoft.com/library/cc750213) (Bewährte Methoden zur Verhinderung von Denial-of-Service-Angriffen (DoS)).
Ein Administrator kann außerdem zusätzliche, im Handel verfügbare Authentifizierungssoftware erwerben und installieren.

Die folgende Tabelle enthält eine Beschreibung der vier Sicherheitsebenen zwischen Endbenutzern und Zielcomputern.

|Ebene|Ebene|
|-|-|
|1|[iis web server security features (Sicherheitsfeatures des IIS-Webservers)](#iis-web-server-security-features)|
|2|[windows powershell web access forms-based gateway authentication (Formularbasierte Gatewayauthentifizierung von Windows PowerShell Web Access)](#windows-powershell-web-access-forms-based-gateway-authentication)|
|3|[windows powershell web access authorization rules (Windows PowerShell Web Access-Autorisierungsregeln)](#windows-powershell-web-access-authorization-rules)|
|4|[target authentication and authorization rules (Zielauthentifizierung und Autorisierungsregeln)](#target-authentication-and-authorization-rules)|

Ausführliche Informationen zu jeder Ebene finden Sie unter den folgenden Überschriften:

#### <a name="iis-web-server-security-features"></a>Sicherheitsfeatures des IIS-Webservers

Benutzer von Windows PowerShell Web Access müssen immer einen Benutzernamen und ein Kennwort angeben, um ihre Konten auf dem Gateway zu authentifizieren. Windows PowerShell Web Access-Administratoren können die optionale Authentifizierung per Clientzertifikat jedoch auch aktivieren oder deaktivieren (siehe [install and use windows powershell web access (Installieren und Verwenden von Windows PowerShell Web Access)](install-and-use-windows-powershell-web-access.md)), um ein Testzertifikat zu erstellen und später ein Originalzertifikat zu generieren.

Für die optionale Clientzertifikatauthentifizierung müssen Endbenutzer zusätzlich zu ihren Benutzernamen und Kennwörtern auch über ein gültiges Clientzertifikat verfügen. Das Feature ist Teil der Konfiguration des Webservers (IIS). Wenn die Clientzertifikatebene aktiviert ist, werden Benutzer auf der Windows PowerShell Web Access-Anmeldeseite zum Angeben gültiger Zertifikate aufgefordert, bevor ihre Anmeldeinformationen ausgewertet werden. Die Clientzertifikatauthentifizierung bewirkt, dass automatisch das Vorhandensein des Clientzertifikats überprüft wird. Falls kein gültiges Zertifikat gefunden wird, werden die Benutzer von Windows PowerShell Web Access darüber informiert, damit sie das Zertifikat bereitstellen können. Wenn ein gültiges Clientzertifikat gefunden wird, öffnet Windows PowerShell Web Access die Anmeldeseite, auf der Benutzer ihre Benutzernamen und Kennwörter angeben können.

Dies ist nur ein Beispiel für die zusätzlichen Sicherheitseinstellungen, die vom IIS-Webserver zur Verfügung gestellt werden. Weitere Informationen zu anderen IIS-Sicherheitsfeatures finden Sie unter [Konfigurieren der Webserversicherheit (IIS 7)](https://technet.microsoft.com/library/cc731278).

#### <a name="windows-powershell-web-access-forms-based-gateway-authentication"></a>Formularbasierte Gatewayauthentifizierung von Windows PowerShell Web Access

Die Anmeldeseite von Windows PowerShell Web Access erfordert einen Satz von Anmeldeinformationen (Benutzername und Kennwort) und bietet Benutzern die Möglichkeit, unterschiedliche Anmeldeinformationen für den Zielcomputer anzugeben.
Wenn der Benutzer keine alternativen Anmeldeinformationen angibt, werden die primären Benutzernamen- und Kennwortinformationen, die für die Verbindung zum Gateway verwendet werden, auch genutzt, um eine Verbindung mit dem Zielcomputer herzustellen.

Die erforderlichen Anmeldeinformationen werden auf dem Windows PowerShell Web Access-Gateway authentifiziert. Bei diesen Anmeldeinformationen muss es sich um gültige Benutzerkonten auf entweder dem lokalen Windows PowerShell Web Access-Gatewayserver oder in Active Directory handeln.

#### <a name="windows-powershell-web-access-authorization-rules"></a>Windows PowerShell Web Access-Autorisierungsregeln

Nachdem ein Benutzer am Gateway authentifiziert wurde, werden die Autorisierungsregeln von Windows PowerShell Web Access überprüft, um sicherzustellen, dass der Benutzer zum Zugriff auf den angeforderten Zielcomputer berechtigt ist. Nach der erfolgreichen Autorisierung werden die Anmeldeinformationen des Benutzers an den Zielcomputer übergeben.

Diese Regeln werden erst ausgewertet, nachdem ein Benutzer vom Gateway authentifiziert wurde und bevor ein Benutzer auf einem Zielcomputer authentifiziert werden kann.

#### <a name="target-authentication-and-authorization-rules"></a>Zielauthentifizierung und Autorisierungsregeln

Die letzte Sicherheitsebene für Windows PowerShell Web Access ist die eigene Sicherheitskonfiguration des Zielcomputers. Für Benutzer müssen auf dem Zielcomputer die richtigen Zugriffsrechte konfiguriert sein. Dies gilt auch für die Windows PowerShell Web Access-Autorisierungsregeln zum Ausführen einer webbasierten Windows PowerShell Web Access-Konsole, die für einen Zielcomputer über Windows PowerShell Web Access verwendet wird.

Diese Ebene bietet die gleichen Sicherheitsmechanismen, die auch Verbindungsversuche auswerten würden, falls Benutzer versuchen, eine Windows PowerShell-Remotesitzung zu einem Zielcomputer mithilfe der Cmdlets [Enter-PSSession](/powershell/module/microsoft.powershell.core/Enter-PSSession) oder [New-PSSession](/powershell/module/microsoft.powershell.core/new-pssession) über Windows PowerShell einzurichten.

Standardmäßig verwendet Windows PowerShell Web Access den primären Benutzernamen und das dazugehörige Kennwort für die Authentifizierung auf dem Gateway und dem Zielcomputer. Die webbasierte Anmeldeseite enthält im Abschnitt **Optionale Verbindungseinstellungen** eine Option, bei der Benutzer bei Bedarf andere Anmeldeinformationen für den Zielcomputer angeben können. Wenn der Benutzer keine alternativen Anmeldeinformationen angibt, werden die primären Benutzernamen- und Kennwortinformationen, die für die Verbindung zum Gateway verwendet werden, auch genutzt, um eine Verbindung mit dem Zielcomputer herzustellen.

Mithilfe von Autorisierungsregeln kann Benutzern der Zugriff auf eine bestimmte Sitzungskonfiguration gestattet werden. Sie können _eingeschränkte Runspaces_ oder Sitzungskonfigurationen für Windows PowerShell Web Access erstellen und für bestimmte Benutzer nur die Verbindung mit speziellen Sitzungskonfigurationen zulassen, wenn diese sich bei Windows PowerShell Web Access anmelden. Mithilfe von Zugriffssteuerungslisten können Sie bestimmen, welche Benutzer auf bestimmte Endpunkte zugreifen können, und den Zugriff auf den Endpunkt für eine bestimmte Gruppe von Benutzern anhand von Autorisierungsregeln weiter einschränken, wie in diesem Abschnitt beschrieben. Weitere Informationen zu eingeschränkten Runspaces finden Sie unter [Creating a constrained runspace (Erstellen eines eingeschränkten Runspaces)](https://msdn.microsoft.com/library/dn614668).

### <a name="configuring-authorization-rules"></a>Konfigurieren von Autorisierungsregeln

Administratoren streben für Windows PowerShell Web Access-Benutzer meist die Verwendung derjenigen Autorisierungsregel an, die in ihrer Umgebung bereits für die Windows PowerShell-Remoteverwaltung definiert ist. Im ersten Verfahren dieses Abschnitts wird beschrieben, wie Sie eine sichere Autorisierungsregel hinzufügen können, die es einem einzelnen Benutzer erlaubt, sich für die Verwaltung eines Computers bei Verwendung einer einzigen Sitzungskonfiguration anzumelden. Das zweite Verfahren beschreibt, wie Sie eine Autorisierungsregel entfernen, die nicht mehr benötigt wird.

Wenn Sie die Verwendung von benutzerdefinierten Sitzungskonfigurationen planen, um für bestimmte Benutzer nur die Arbeit in eingeschränkten Runspaces von Windows PowerShell Web Access zuzulassen, erstellen Sie die benutzerdefinierten Sitzungskonfigurationen vor dem Hinzufügen der Autorisierungsregeln, die darauf verweisen. Sie können die Windows PowerShell Web Access-Cmdlets nicht zum Erstellen von benutzerdefinierten Sitzungskonfigurationen verwenden. Weitere Informationen zur Erstellung von benutzerdefinierten Sitzungskonfigurationen finden Sie unter [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

Für Windows PowerShell Web Access-Cmdlets wird ein Platzhalterzeichen unterstützt, und zwar das Sternchen ( \*). Platzhalterzeichen innerhalb von Zeichenfolgen werden nicht unterstützt. Verwenden Sie ein einzelnes Sternchen pro Eigenschaft (Benutzer, Computer oder Sitzungskonfigurationen).

> [!NOTE]
> Weitere Möglichkeiten der Verwendung von Autorisierungsregeln, um Benutzern Zugriff zu gewähren, und Hilfe zum Schutz der Windows PowerShell Web Access-Umgebung finden Sie unter [Weitere Beispiele für Autorisierungsregelszenarios](#other-authorization-rule-scenario-examples) in diesem Thema.

#### <a name="to-add-a-restrictive-authorization-rule"></a>So fügen Sie eine restriktive Autorisierungsregel hinzu

1. Öffnen Sie eine Windows PowerShell-Sitzung mit erhöhten Benutzerrechten, indem Sie einen der folgenden Schritte durchführen.

   - Klicken Sie auf dem Windows-Desktop mit der rechten Maustaste in der Taskleiste auf **Windows PowerShell** und anschließend auf **Als Administrator ausführen**.

   - Klicken Sie auf dem Windows-**Startbildschirm** mit der rechten Maustaste auf **Windows PowerShell**, und klicken Sie anschließend auf **Als Administrator ausführen**.

2. **Optionaler Schritt** zum Einschränken des Benutzerzugriffs mithilfe von Sitzungskonfigurationen:

   Überprüfen Sie, dass die Sitzungskonfigurationen, die Sie verwenden möchten, bereits in Ihren Regeln vorhanden sind.

   Falls diese noch nicht erstellt wurden, verwenden Sie die Anleitung zum Erstellen von Sitzungskonfigurationen unter [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

3. Diese Autorisierungsregel erlaubt es einem bestimmten Benutzer, auf einen Computer im Netzwerk zuzugreifen, auf den er normalerweise zugreifen kann. Der Zugriff ist auf eine bestimmte Sitzungskonfiguration beschränkt, die die üblichen Anforderungen des Benutzers im Hinblick auf die Ausführung von Skripts und Cmdlets abdeckt. Geben Sie Folgendes ein, und drücken Sie anschließend die **EINGABETASTE**.

   ```
   Add-PswaAuthorizationRule -UserName <domain\user | computer\user> `
      -ComputerName <computer_name> -ConfigurationName <session_configuration_name>
   ```

   - Im folgenden Beispiel wird dem Benutzer _JSmith_ in der Domäne _Contoso_ Zugriff auf die Verwaltung des Computers _Contoso_214_ und die Verwendung einer Sitzungskonfiguration mit dem Namen _NewAdminsOnly_ gewährt.

   ```powershell
   Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' `
      -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly
   ```

4. Stellen Sie sicher, dass die Regel erstellt wurde, indem Sie entweder das Cmdlet **Get-PswaAuthorizationRule** oder `Test-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName** <computer_name>` ausführen.
   Beispiel: `Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214`.

#### <a name="to-remove-an-authorization-rule"></a>So entfernen Sie eine Autorisierungsregel

1. Falls noch keine Windows PowerShell-Sitzung geöffnet wurde, finden Sie die entsprechende Vorgehensweise in Schritt 1 unter [So fügen Sie eine restriktive Autorisierungsregel hinzu](#to-add-a-restrictive-authorization-rule) in diesem Abschnitt.

2. Geben Sie Folgendes ein, und drücken Sie anschließend die **EINGABETASTE**, wobei *Regel-ID* für die eindeutige ID-Nummer der Regel steht, die Sie entfernen möchten.

   ```
   Remove-PswaAuthorizationRule -ID <rule ID>
   ```

   Falls Ihnen die ID-Nummer nicht bekannt ist, dafür jedoch der Anzeigename der zu entfernenden Regel, können Sie alternativ dazu den Namen der Regel abrufen und diesen an das Cmdlet `Remove-PswaAuthorizationRule` weiterleiten, um die Regel wie im folgenden Beispiel zu entfernen:

   ```
   Get-PswaAuthorizationRule `
      -RuleName <rule-name> | Remove-PswaAuthorizationRule
   ```

> [!NOTE]
> Sie werden nicht aufgefordert zu bestätigen, dass die angegebene Autorisierungsregel gelöscht werden soll. Die Regel wird gelöscht, wenn Sie die **EINGABETASTE** drücken. Vergewissern Sie sich, ob die Autorisierungsregel wirklich entfernt werden soll, bevor Sie das Cmdlet `Remove-PswaAuthorizationRule` ausführen.

#### <a name="other-authorization-rule-scenario-examples"></a>Weitere Beispiele für Autorisierungsregelszenarios

Bei jeder Windows PowerShell-Sitzung wird eine Sitzungskonfiguration verwendet. Falls für eine Sitzung keine Konfiguration angegeben ist, wird von Windows PowerShell die standardmäßige integrierte Windows PowerShell-Sitzungskonfiguration mit dem Namen „Microsoft.PowerShell“ verwendet. Die Standardsitzungskonfiguration schließt alle auf einem Computer verfügbaren Cmdlets ein. Administratoren können den Zugriff auf alle Computer einschränken, indem sie eine Sitzungskonfiguration mit eingeschränktem Runspace (ein begrenzter Bereich von Cmdlets und Aufgaben, die die Endbenutzer ausführen können) definieren. Ein Benutzer, dem der Zugriff auf einen Computer gestattet wurde (entweder mit vollem Sprachzugriff oder nur mit Zugriff auf die Windows PowerShell-Remoteverwaltungs-Cmdlets), kann Verbindungen mit anderen Computern herstellen, die mit dem ersten Computer verbunden sind. Durch die Definition eines eingeschränkten Runspace kann verhindert werden, dass Benutzer von ihrem zulässigen Windows PowerShell-Runspace aus auf andere Computer zugreifen. Außerdem wird dadurch die Sicherheit der Windows PowerShell Web Access-Umgebung verbessert. Die Sitzungskonfiguration kann (per Gruppenrichtlinie) an alle Computer verteilt werden, für die Administratoren den Zugriff über Windows PowerShell Web Access gewähren möchten. Weitere Informationen zu Sitzungskonfigurationen finden Sie unter [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx). Im Folgenden sind einige Beispiele für die Verwendung von Sitzungskonfigurationen aufgeführt.

- Ein Administrator erstellt einen Endpunkt namens **PswaEndpoint** mit einem eingeschränkten Runspace. Anschließend erstellt der Administrator die Regel `*,*,PswaEndpoint` und verteilt den Endpunkt an andere Computer. Mithilfe der Regel können alle Benutzer auf alle Computer mit dem Endpunkt **PswaEndpoint** zugreifen.
  Falls es sich um die einzige Autorisierungsregel handelt, die in dem Regelsatz definiert ist, ist der Zugriff auf Computer ohne diesen Endpunkt nicht möglich.

- Der Administrator hat einen Endpunkt mit dem eingeschränkten Runspace **PswaEndpoint** erstellt und möchte den Zugriff auf bestimmte Benutzer beschränken. Der Administrator erstellt die Benutzergruppe namens **Level1Support** und definiert die folgende Regel: **Level1Support,\*,PswaEndpoint**. Mit der Regel wird allen Benutzern der Gruppe **Level1Support** Zugriff auf alle Computer mit der Konfiguration **PswaEndpoint** gewährt. Ebenso ist es möglich, den Zugriff auf eine bestimmte Gruppe von Computern zu beschränken.

- Einige Administratoren gewähren bestimmten Benutzern mehr Zugriff als anderen. Beispielsweise erstellt ein Administrator die beiden Benutzergruppen **Admins** und **BasicSupport**. Ferner erstellt der Administrator einen Endpunkt mit dem eingeschränkten Runspace namens **PswaEndpoint** und definiert die folgenden beiden Regeln: **Admins,\*,\*** und **BasicSupport,\*,PswaEndpoint**. Mit der ersten Regel wird allen Benutzern der Gruppe **Admin** Zugriff auf alle Computer gewährt, und mit der zweiten Regel wird allen Benutzern der Gruppe **BasicSupport** nur Zugriff auf Computer mit **PswaEndpoint** gewährt.

- Ein Administrator hat eine private Testumgebung eingerichtet und möchte nun allen autorisierten Netzwerkbenutzern den Zugriff auf alle Computer im Netzwerk ermöglichen, auf die sie normalerweise zugreifen können, und zwar mit Zugriff auf alle Sitzungskonfigurationen, auf die sie normalerweise zugreifen können. Da es sich um eine private Testumgebung handelt, erstellt der Administrator eine Autorisierungsregel, die nicht sicher ist. Der Administrator führt das Cmdlet `Add-PswaAuthorizationRule * * *` aus. Dabei wird das Platzhalterzeichen **\*** verwendet, um alle Benutzer, alle Computer und alle Konfigurationen anzugeben. Diese Regel entspricht Folgendem: `Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *`.

  > [!NOTE]
  > Diese Regel empfiehlt sich nicht für eine sichere Umgebung und umgeht die von Windows PowerShell Web Access bereitgestellte Autorisierungsregel-Sicherheitsebene.

- Ein Administrator muss für Benutzer in einer Umgebung, in der sowohl Arbeitsgruppen als auch Domänen enthalten sind, das Herstellen einer Verbindung mit Zielcomputern zulassen. Dabei werden Arbeitsgruppencomputer gelegentlich verwendet, um eine Verbindung mit Zielcomputern in Domänen herzustellen, und Computer in Domänen werden gelegentlich verwendet, um eine Verbindung mit Zielcomputern in Arbeitsgruppen herzustellen. Der Administrator verfügt über einen Gatewayserver (*PswaServer*) in einer Arbeitsgruppe, und der Zielcomputer *srv1.contoso.com* befindet sich in einer Domäne. Der Benutzer *Chris* ist ein autorisierter lokaler Benutzer auf dem Arbeitsgruppen-Gatewayserver und auf dem Zielcomputer. Sein Benutzername auf dem Arbeitsgruppenserver lautet *chrisLocal*, und sein Benutzername auf dem Zielcomputer lautet *contoso\\chris*. Der Administrator fügt die folgende Regel hinzu, um den Zugriff auf %%amp;quot;srv1.contoso.com%%amp;quot; für Chris zu autorisieren.

```powershell
Add-PswaAuthorizationRule -userName PswaServer\chrisLocal `
   -computerName srv1.contoso.com -configurationName Microsoft.PowerShell
```

Im vorigen Regelbeispiel wird Chris auf dem Gatewayserver authentifiziert und anschließend sein Zugriff auf *srv1* autorisiert. Auf der Anmeldeseite muss Chris unter **Optionale Verbindungseinstellungen** (*contoso\\chris*) einen zweiten Satz Anmeldeinformationen angeben. Der Gatewayserver verwendet den zusätzlichen Satz von Anmeldeinformationen für die Authentifizierung auf dem Zielcomputer *srv1.contoso.com*.

Im obigen Szenario richtet Windows PowerShell Web Access eine Verbindung mit dem Zielcomputer erst ein, nachdem Folgendes erfolgreich durchgeführt und von mindestens einer Autorisierungsregel zugelassen wurde.

1. Authentifizierung des Arbeitsgruppen-Gatewayservers durch Hinzufügen eines Benutzernamens im Format *server_name*\\*user_name* zur Autorisierungsregel

2. Authentifizierung auf dem Zielcomputer mithilfe von alternativen Anmeldeinformationen, die auf der Anmeldeseite unter **Optionale Verbindungseinstellungen** angegeben wurden

   > [!NOTE]
   > Wenn sich Gateway- und Zielcomputer in unterschiedlichen Arbeitsgruppen oder Domänen befinden, muss eine Vertrauensstellung zwischen den beiden Arbeitsgruppencomputern, den beiden Domänen oder der Arbeitsgruppe und der Domäne eingerichtet werden. Diese Vertrauensstellung kann nicht mithilfe von Windows PowerShell Web Access-Autorisierungsregel-Cmdlets konfiguriert werden. Mit den Autorisierungsregeln wird keine Vertrauensstellung zwischen Computern definiert. Damit kann für Benutzer nur die Verbindung mit bestimmten Zielcomputern und Sitzungskonfigurationen konfiguriert werden. Weitere Informationen zur Konfiguration einer Vertrauensstellung zwischen unterschiedlichen Domänen finden Sie unter [Creating Domain and Forest Trusts](https://technet.microsoft.com/library/cc794775.aspx) (Erstellen von Domänen- und Gesamtstruktur-Vertrauensstellungen).
   > Weitere Informationen zum Hinzufügen von Arbeitsgruppencomputern zu einer Liste mit vertrauenswürdigen Hosts finden Sie unter [Remoteverwaltung mit dem Server-Manager](https://technet.microsoft.com/library/dd759202.aspx).

### <a name="using-a-single-set-of-authorization-rules-for-multiple-sites"></a>Verwenden eines einzigen Satzes mit Autorisierungsregeln für mehrere Websites

Autorisierungsregeln werden in einer XML-Datei gespeichert. Standardmäßig lautet der Pfadname der XML-Datei `$env:windir\Web\PowershellWebAccess\data\AuthorizationRules.xml`.

Der Pfad zur XML-Datei mit den Autorisierungsregeln ist in der Datei **powwa.config** gespeichert, die im Ordner `$env:windir\Web\PowershellWebAccess\data` enthalten ist. Der Administrator kann den Verweis auf den Standardpfad in **powwa.config** flexibel ändern, falls Präferenzen oder Anforderungen dies erfordern. Da der Administrator den Speicherort der Datei ändern kann, können mehrere Windows PowerShell Web Access-Gateways dieselben Autorisierungsregeln verwenden, falls eine Konfiguration dieser Art gewünscht wird.

## <a name="session-management"></a>Sitzungsverwaltung

Standardmäßig begrenzt Windows PowerShell Web Access einen Benutzer auf drei zeitgleiche Sitzungen. Sie können die Datei **web.config** der Webanwendung im IIS-Manager bearbeiten, um eine andere Anzahl von Sitzungen pro Benutzer zu unterstützen. Der Pfad zur Datei **web.config** lautet `$env:windir\Web\PowerShellWebAccess\wwwroot\Web.config`.

Standardmäßig ist der IIS-Webserver so konfiguriert, dass der Anwendungspool neu gestartet wird, wenn Einstellungen bearbeitet werden. Beispielsweise wird der Anwendungspool neu gestartet, wenn Änderungen an der Datei **web.config** vorgenommen werden. Da von **Windows PowerShell Web Access** In-Memory-Sitzungszustände verwendet werden, werden Sitzungen von bei **Windows PowerShell Web Access**-Sitzungen angemeldeten Benutzer getrennt, wenn der Anwendungspool neu gestartet wird.

### <a name="setting-default-parameters-on-the-sign-in-page"></a>Festlegen von Standardparametern auf der Anmeldeseite

Wenn Ihr Windows PowerShell Web Access-Gateway unter Windows Server 2012 R2 ausgeführt wird, können Sie die Standardwerte für die Einstellungen konfigurieren, die auf der Windows PowerShell Web Access-Anmeldeseite angezeigt werden. Sie können Werte in der Datei **web.config** konfigurieren, die im vorherigen Abschnitt beschrieben wurde. Standardwerte für die Anmeldeseiteneinstellungen finden Sie im Abschnitt **appSettings** der Datei „web.config“. Es folgt ein Beispiel des Abschnitts **appSettings**. Gültige Werte für viele dieser Einstellungen entsprechen denen der entsprechenden Parameter des Cmdlets [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) in Windows PowerShell.

Der im folgenden Codeblock enthaltene Schlüssel `defaultApplicationName` ist z.B. der Wert der Einstellungsvariablen **$PSSessionApplicationName** auf dem Zielcomputer.

```xml
  <appSettings>
      <add key="maxSessionsAllowedPerUser" value="3"/>
      <add key="defaultPortNumber" value="5985"/>
      <add key="defaultSSLPortNumber" value="5986"/>
      <add key="defaultApplicationName" value="WSMAN"/>
      <add key="defaultUseSslSelection" value="0"/>
      <add key="defaultAuthenticationType" value="0"/>
      <add key="defaultAllowRedirection" value="0"/>
      <add key="defaultConfigurationName" value="Microsoft.PowerShell"/>
  </appSettings>
```

### <a name="time-outs-and-unplanned-disconnections"></a>Timeouts und ungeplante Trennvorgänge

Windows PowerShell Web Access-Sitzungstimeout In Windows PowerShell Web Access unter Windows Server 2012 wird nach 15-minütiger Inaktivität angemeldeten Benutzern eine Timeoutmeldung angezeigt. Wenn der Benutzer nach dem Anzeigen der Timeoutmeldung nicht innerhalb von fünf Minuten reagiert, wird die Sitzung beendet, und der Benutzer wird abgemeldet. Sie können die Zeitspanne für den Sitzungstimeout in den Websiteeinstellungen im IIS-Manager ändern.

In Windows PowerShell Web Access unter Windows Server 2012 R2 wird standardmäßig nach 20-minütiger Inaktivität ein Sitzungstimeout angezeigt. Wenn Benutzer aufgrund von Netzwerkfehlern oder anderen ungeplanten Herunterfahrvorgängen oder Ausfällen von Sitzungen in der webbasierten Konsole getrennt werden, werden die Windows PowerShell Web Access-Sitzungen weiter ausgeführt und bleiben mit den Zielcomputern verbunden, bis die Timeoutperiode auf dem Client überschritten wird. Dies geschieht nicht, wenn Benutzer die Sitzungen selbst beenden. Die Sitzung wird entweder standardmäßig nach 20 Minuten oder nach der vom Gatewayadministrator festgelegten Timeoutperiode getrennt, je nachdem, was kürzer ist.

Wenn der Gatewayserver unter Windows Server 2012 R2 ausgeführt wird, ermöglicht Windows PowerShell Web Access Benutzern das erneute Verbinden mit gespeicherten Sitzungen zu einem späteren Zeitpunkt. Wenn Sitzungen jedoch aufgrund von Netzwerkfehlern, ungeplanten Herunterfahrvorgängen oder Ausfällen getrennt werden, können Benutzer gespeicherte Sitzungen erst sehen bzw. sich wieder mit diesen verbinden, nachdem die vom Gatewayadministrator festgelegte Timeoutperiode abgelaufen ist.

## <a name="see-also"></a>Weitere Informationen

[Install and Use Windows PowerShell Web Access (Installieren und Verwenden von Windows PowerShell Web Access)](https://technet.microsoft.com/library/hh831611(v=ws.11).aspx)

[about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)

[Windows PowerShell Web Access Cmdlets (Windows PowerShell Web Access-Cmdlets)](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps)
