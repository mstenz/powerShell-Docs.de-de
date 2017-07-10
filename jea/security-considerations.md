---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,security
title: "JEA-Sicherheitsüberlegungen"
ms.openlocfilehash: f85b342625d4dba0890619ef9680eaccbbde5224
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="jea-security-considerations" class="xliff"></a>
# JEA-Sicherheitsüberlegungen

> Gilt für: Windows PowerShell 5.0

JEA unterstützt Sie bei der Verbesserung Ihres Sicherheitsniveaus und reduziert die Anzahl der permanenten Administratoren auf Ihren Computern.
Dies geschieht durch Erstellen eines neuen Einstiegspunkts für Benutzer zum Verwalten des Systems (eine PowerShell-Sitzungskonfiguration), der standardmäßig gesperrt ist, um Missbrauch zu verhindern.
Benutzer, die einen gewissen, aber nicht unbegrenzten Zugriff auf den Computer benötigen, um administrative Aufgaben zu erledigen, können Zugriff auf den JEA-Endpunkt erhalten.
Da JEA das Ausführen von Admin-Befehlen ohne direkten Administratorzugriff ermöglicht, können Sie diese Benutzer aus Sicherheitsgruppen mit weitreichenden Berechtigungen entfernen (und sie zu Standardbenutzern machen).

Dieses Thema enthält eine detaillierte Beschreibung des JEA-Sicherheitsmodells und bewährter Methoden.

<a id="run-as-account" class="xliff"></a>
## Ausführendes Konto

Jeder JEA-Endpunkt verfügt über ein festgelegtes ausführendes Konto, in dem die Aktionen des Benutzers erfolgen, der eine Verbindung herstellt.
Dieses Konto lässt sich in der [Sitzungskonfigurationsdatei](session-configurations.md) konfigurieren und hat einen erheblichen Einfluss auf die Sicherheit Ihres Endpunkts.

Für das Konfigurieren eines ausführenden Kontos werden **virtuelle Konten** empfohlen.
Virtuelle Konten sind einmalige, temporäre lokale Konten, die während der Dauer der JEA-Sitzung für den Benutzer erstellt werden, der die Verbindung herstellt.
Unmittelbar nach Ende der Sitzung wird das virtuelle Konto gelöscht und kann nicht mehr verwendet werden.
Der Benutzer, der die Verbindung herstellt, kennt die Anmeldeinformation des virtuellen Kontos nicht und kann es nicht dazu verwenden, um anderweitig auf das System zuzugreifen, z.B. über Remotedesktop oder einen uneingeschränkten PowerShell-Endpunkt.

Virtuelle Konten gehören standardmäßig zur Gruppe der lokalen Administratoren auf dem Computer.
Dadurch erhalten sie Vollzugriff zum Verwalten aller Elemente auf dem System, aber keine Rechte zum Verwalten von Ressourcen im Netzwerk.
Für die Authentifizierung an anderen Computern wird statt des virtuellen Kontos das lokale Computerkonto als Benutzerkontext verwendet.

Domänencontroller sind ein Sonderfall, da es bei ihnen das Konzept der lokalen Administratorgruppe nicht gibt.
Stattdessen gehören virtuelle Konten zu Domänen-Admins und können die Verzeichnisdienste auf dem Domänencontroller verwalten.
Die Gültigkeit der Domänenidentität ist auf den Domänencontroller beschränkt, auf dem die JEA-Sitzung instanziiert wurde. Bei jedem Netzwerkzugriff wird es stattdessen so aussehen, als erfolge dieser vom Computerobjekt des Domänencontrollers.

In beiden Fällen können Sie auch explizit definieren, zu welchen Sicherheitsgruppen das virtuelle Konto gehören soll.
Dies wird empfohlen, wenn Sie Ihre Aufgabe ohne lokale Administrator- bzw. Domänen-Adminberechtigungen ausführen können.
Wenn Sie bereits eine Sicherheitsgruppe für Ihre Administratoren definiert haben, können Sie das virtuelle Konto einfach zum Mitglied dieser Gruppe machen, damit es über die notwendigen Berechtigungen verfügt.
Die Gruppenmitgliedschaft virtueller Konten beschränkt sich auf lokale Sicherheitsgruppen auf Arbeitsstationen und Mitgliedsservern. Auf einem Domänencontroller können sie nur Mitglieder von Sicherheitsgruppen einer Domäne sein.
Nachdem Sie eine oder mehrere Sicherheitsgruppen für das virtuelle Konto angegeben haben, gehört es nicht mehr zu den Standardgruppen (lokale Administratoren oder Domänen-Admins).

In der folgenden Tabelle werden die möglichen Konfigurationsoptionen und die sich daraus ergebenden Berechtigungen für virtuelle Konten zusammengefasst.

Computertyp                | Konfiguration virtueller Kontogruppen | Lokaler Benutzerkontext                                      | Netzwerkbenutzerkontext
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
Domänencontroller            | Standardwert                             | Domänenbenutzer, Mitglied von „*DOMÄNE*\Domänen-Admins“         | Computerkonto
Domänencontroller            | Domänengruppen A und B               | Domänenbenutzer, Mitglied von „*DOMAIN*\A“, „*DOMAIN*\B“       | Computerkonto
Mitgliedsserver oder Arbeitsstation | Standardwert                             | Lokaler Benutzer, Mitglied von „*BUILTIN*\Administrators“        | Computerkonto
Mitgliedsserver oder Arbeitsstation | Lokale Gruppen C und D                | Lokale Gruppen, Mitglied von „*COMPUTER*\C“ und „*COMPUTER*\D“ | Computerkonto

Wenn Sie Sicherheitsüberwachungsereignisse und Anwendungsereignisprotokolle genauer betrachten, erkennen Sie, dass jede JEA-Benutzersitzung über ein eindeutiges virtuelles Konto verfügt.
Dadurch können Sie die Benutzeraktionen in einem JEA-Endpunkt zum ursprünglichen Benutzer zurückverfolgen, der den Befehl ausgeführt hat.
Virtuelle Kontonamen haben folgendes Format: Virtuelle Benutzer\\WinRM\_VA\_*KONTONUMMER*\_*DOMÄNE*\_*sAMKontoName*. Wenn beispielsweise Benutzer „Alice“ in der Domäne „Contoso“ einen Dienst in einem JEA-Endpunkt neu startet, so lautet der Benutzername, der einem beliebigen Ereignis eines Dienststeuerungs-Managers zugeordnet ist, „WinRM\\WinRM\_VA\_1\_Contoso\_alice“.


**Gruppenverwaltete Dienstkonten (gMSAs)** erweisen sich als nützlich, wenn ein Mitgliedsserver in der JEA-Sitzung auf Netzwerkressourcen zugreifen muss.
Ein Anwendungsbeispiel dafür ist ein JEA-Endpunkt, der zur Zugriffssteuerung für eine REST-API genutzt wird, die auf einem anderen Computer gehostet wird.
Für die gewünschten Aufrufe auf der REST-API lassen sich leicht Funktionen schreiben, die Authentifizierung mit der API setzt jedoch eine Netzwerkidentität voraus.
Die Verwendung eines gruppenverwalteten Dienstkontos ermöglicht den „zweiten Hop“, während Sie weiterhin die Kontrolle darüber behalten, welche Computer das Konto verwenden können.
Die effektiven Berechtigungen des gMSA werden durch die Sicherheitsgruppen (lokal oder Domäne) definiert, zu denen das gMSA-Konto gehört.

Wenn ein JEA-Endpunkt für die Verwendung eines gMSA-Kontos konfiguriert ist, sieht es aus, als stammten die Aktionen aller JEA-Benutzer aus demselben gruppenverwalteten Dienstkonto.
Sie können die Aktionen eines bestimmten Benutzers nur dann zurückverfolgen, wenn Sie die ausgeführten Befehle identifizieren können, die in einer PowerShell-Sitzungsaufzeichnung erfasst sind.

**Pass-Through-Anmeldeinformationen** werden verwendet, wenn Sie kein ausführendes Konto angeben und möchten, dass PowerShell für die Ausführung von Befehlen auf dem Remoteserver die Anmeldeinformationen des Benutzers verwendet, der die Verbindung herstellt.
Diese Konfiguration wird für JEA *nicht* empfohlen. Sie setzt voraus, dass Sie dem Benutzer, der eine Verbindung herstellt, direkten Zugriff auf privilegierte Verwaltungsgruppen gewähren.
Benutzer, die eine Verbindung herstellen und über Administratorberechtigungen verfügen, können JEA gänzlich umgehen und das System über andere, uneingeschränkte Möglichkeiten verwalten.
Weitere Informationen dazu, warum [JEA keinen Schutz von Administratoren bietet](#jea-does-not-protect-against-admins), finden Sie im Abschnitt weiter unten.

**Standard-RunAS-Konten** ermöglichen Ihnen, ein beliebiges Benutzerkonto anzugeben, unter dem die gesamte PowerShell-Sitzung ausgeführt wird.
Dies ist ein wichtiger Unterschied, denn eine Sitzungskonfiguration, die die Ausführung eines festen ausführenden Kontos vorsieht (mit dem `-RunAsCredential`-Parameter), ist nicht mit JEA kompatibel.
Das bedeutet, dass Rollendefinitionen nicht mehr wie erwartet funktionieren und dass jedem Benutzer, der für den Zugriff auf den Endpunkt berechtigt ist, die gleiche Rolle zugeordnet wird.

RunAsCredential sollte nicht auf einem JEA-Endpunkt verwendet werden, da Aktionen schwer auf bestimmte Benutzer zurückzuverfolgen sind und die Zuordnung von Benutzern zu Rollen nicht unterstützt wird.

<a id="winrm-endpoint-acl" class="xliff"></a>
## WinRM-Endpunkt-ACL

Wie auch bei regulären PowerShell-Remoting-Endpunkten verfügt jeder JEA-Endpunkt über eine separate Zugriffssteuerungsliste (ACL) in der WinRM-Konfiguration. Sie legt fest, wer für eine Authentifizierung mit dem JEA-Endpunkt berechtigt ist.
Bei einer nicht ordnungsgemäßen Konfiguration können vertrauenswürdige Benutzer möglicherweise nicht auf den JEA-Endpunkt zugreifen und nicht vertrauenswürdige Benutzer Zugriff erhalten.
Die WinRM-ACL wirkt sich allerdings nicht auf die Zuordnung von Benutzern zu JEA-Rollen aus.
Dies wird über das *RoleDefinitions*-Feld in der Sitzungskonfigurationsdatei gesteuert, die auf dem System registriert wurde.

Wenn Sie einen JEA-Endpunkt mithilfe einer Sitzungskonfigurationsdatei und einer oder mehrerer Rollenfunktionen registrieren, wird die WinRM-ACL standardmäßig so konfiguriert, dass alle Benutzer, denen eine oder mehrere Rollen zugeordnet sind, Zugriff auf den Endpunkt haben.
So bietet beispielsweise eine mit den folgenden Befehlen konfigurierte JEA-Sitzung vollen Zugriff auf *CONTOSO\JEA\_Lev1* und *CONTOSO\JEA\_Lev2*.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

Sie können Benutzerberechtigungen über das [Get-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration)-Cmdlet überwachen.

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Sie können den Zugriff der einzelnen Benutzer ändern, indem Sie entweder `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` für eine interaktive Aufforderung oder `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` ausführen, um die Berechtigungen zu aktualisieren.
Benutzer müssen mindestens Rechte zum *Aufrufen* haben, um auf den JEA-Endpunkt zuzugreifen.

Wenn zusätzliche Benutzer Zugriffsrechte für den JEA-Endpunkt erhalten, aber nicht unter eine der in der Sitzungskonfigurationsdatei definierten Rollen fallen, können sie zwar eine JEA-Sitzung starten, sie haben aber nur Zugriff auf die Standard-Cmdlets.
Sie können die Benutzerberechtigungen in einem JEA-Endpunkt überwachen, indem Sie `Get-PSSessionCapability` ausführen.
Weitere Informationen dazu, wie Sie überprüfen können, auf welche Befehle ein Benutzer auf einem JEA-Endpunkt zugreifen kann, finden Sie unter [Überwachung und Berichterstellung zu JEA](audit-and-report.md).

<a id="least-privilege-roles" class="xliff"></a>
## Rollen mit geringsten Rechten

Wenn Sie JEA-Rollen entwickeln, sollten Sie beachten, dass das im Hintergrund ausgeführte virtuelle oder gruppenverwaltete Dienstkonto häufig uneingeschränkten Zugriff auf die Verwaltung des lokalen Computers hat.
Mithilfe von JEA-Rollenfunktionen können Sie die Verwendungsmöglichkeiten dieses Kontos einschränken. Begrenzen Sie dazu die Befehle und Anwendungen, die im Rahmen des privilegierten Kontexts ausgeführt werden können.
Aufgrund nicht ordnungsgemäß entwickelter Rollen lassen sich gefährliche Befehle ausführen: Benutzer können die JEA-Grenzen überschreiten oder sich Zugriff auf vertrauliche Informationen verschaffen.

Betrachten Sie beispielsweise den folgenden Rollenfunktionseintrag:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Über diese Rollenfunktion können Benutzer jedes beliebige PowerShell-Cmdlet mit dem Namen „Process“ aus dem Microsoft.PowerShell.Management-Modul ausführen.
Benutzer benötigen möglicherweise Zugriff auf Cmdlets wie `Get-Process`, um zu erfahren, welche Anwendungen auf dem System ausgeführt werden, oder auf `Stop-Process`, um eine Anwendung zu beenden, die sich aufgehängt hat.
Der Eintrag ermöglicht aber auch den Befehl `Start-Process`, um ein beliebiges Programm mit vollständigen Administratorberechtigungen zu starten.
Das Programm muss nicht zwangsläufig lokal auf dem System installiert werden. Ein Angreifer könnte einfach ein Programm auf einer Dateifreigabe starten, die dem Benutzer, der eine Verbindung herstellt, lokale Administratorrechte gibt und die Ausführung von Malware und vieles mehr ermöglicht.

Eine sicherere Version der gleichen Rollenfunktion würde so aussehen:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Vermeiden Sie Platzhalter in Rollenfunktionen, und gewährleisten Sie, dass effektive Benutzerberechtigungen regelmäßig überwacht werden (siehe [Überwachung und Berichterstellung zu JEA](audit-and-report.md#check-effective-rights-for-a-specific-user)), damit Sie wissen, auf welche Befehle ein Benutzer Zugriff hat.

<a id="jea-does-not-protect-against-admins" class="xliff"></a>
## JEA bietet keinen Schutz vor Administratoren

Eines der wichtigsten Prinzipien von JEA ist, dass auch Nichtadministratoren *gewisse* Administratoraufgaben ausführen können.
JEA bietet keinen Schutz vor Benutzern, die bereits über Administratorberechtigungen verfügen.
Benutzer, die „Domänen-Admins“, „lokalen Administratoren“ oder anderen hoch privilegierten Gruppen in Ihrer Umgebung angehören, können JEA-Schutzmaßnahmen weiterhin umgehen, indem sie sich auf andere Weise beim Computer anmelden.
Sie könnten sich z.B. mit RDP anmelden, Remote-MMC-Konsolen verwenden oder eine Verbindung zu uneingeschränkten PowerShell-Endpunkten herstellen.
Lokale Administratoren auf dem System können JEA-Konfigurationen ebenfalls ändern und zusätzlichen Benutzern Berechtigungen zur Verwaltung des Systems oder zur Änderung von Rollenfunktionen geben, um den Spielraum von Benutzern in ihrer JEA-Sitzung zu erweitern.
Sie sollten daher die erweiterten Berechtigungen Ihrer JEA-Benutzer unbedingt überprüfen, um festzustellen, ob sie sich auf andere Art und Weise einen privilegierten Zugriff auf das System verschaffen könnten.

Üblicherweise wird JEA für regelmäßige tägliche Wartungsaufgaben verwendet. Benutzer können dank dieser privilegierten Just-in-Time-Zugriffsverwaltungslösung in Notfallsituationen vorübergehend zu lokalen Administratoren werden.
Dadurch wird sichergestellt, dass Benutzer nicht zu permanenten Administratoren auf dem System werden. Sie erhalten diese Berechtigung nur dann, wenn sie einen Workflow ausführen, der die Verwendung dieser Berechtigungen dokumentiert.

