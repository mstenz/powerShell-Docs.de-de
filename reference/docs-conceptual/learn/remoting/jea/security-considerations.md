---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: JEA-Sicherheitsüberlegungen
ms.openlocfilehash: befc24fec368c4f6d60477daf63bf17e9431133e
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017771"
---
# <a name="jea-security-considerations"></a>JEA-Sicherheitsüberlegungen

JEA unterstützt Sie bei der Verbesserung Ihres Sicherheitsniveaus und reduziert die Anzahl der permanenten Administratoren auf Ihren Computern. JEA erstellt mithilfe einer PowerShell-Sitzungskonfiguration einen neuen Einstiegspunkt für Benutzer zur Verwaltung des Systems. Benutzer, die für administrative Aufgaben einen erhöhten, aber nicht unbegrenzten Zugriff auf den Computer benötigen, können Zugriff auf den JEA-Endpunkt erhalten. Da JEA den Benutzern das Ausführen von Administratorbefehlen ohne vollständigen Administratorzugriff ermöglicht, können Sie diese Benutzer aus Sicherheitsgruppen mit weitreichenden Berechtigungen entfernen.

## <a name="run-as-account"></a>Ausführendes Konto

Jeder JEA-Endpunkt verfügt über ein designiertes **ausführendes Konto**. Dies ist das Konto, unter dem die Aktionen des Benutzers, der eine Verbindung herstellt, ausgeführt werden. Dieses Konto lässt sich in der [Sitzungskonfigurationsdatei](session-configurations.md) konfigurieren und hat einen erheblichen Einfluss auf die Sicherheit Ihres Endpunkts.

Für das Konfigurieren eines **ausführenden Kontos** werden **virtuelle Konten** empfohlen. Virtuelle Konten sind einmalige, temporäre lokale Konten, die während der Dauer der JEA-Sitzung für den Benutzer erstellt werden, der die Verbindung herstellt. Unmittelbar nach Ende der Sitzung wird das virtuelle Konto gelöscht und kann nicht mehr verwendet werden. Der Benutzer, der eine Verbindung herstellt, kennt die Anmeldeinformationen für das virtuelle Konto nicht. Das virtuelle Konto kann nicht verwendet werden, um über andere Wege wie Remotedesktop oder einen uneingeschränkten PowerShell-Endpunkt auf das System zuzugreifen.

Virtuelle Konten gehören standardmäßig zur lokalen Gruppe **Administratoren** auf dem Computer. Dadurch erhalten sie Vollzugriff zum Verwalten aller Elemente auf dem System, aber keine Rechte zum Verwalten von Ressourcen im Netzwerk.
Für die Authentifizierung auf anderen Computern wird statt des virtuellen Kontos das lokale Computerkonto als Benutzerkontext verwendet.

Domänencontroller sind ein Sonderfall, da sie nicht über eine lokale **Administratorgruppe** verfügen. Stattdessen gehören virtuelle Konten zu **Domänen-Admins** und können die Verzeichnisdienste auf dem Domänencontroller verwalten. Die Domänenidentität ist weiterhin auf die Verwendung auf dem Domänencontroller eingeschränkt, auf dem die JEA-Sitzung instanziiert wurde. Jeder Netzwerkzugriff scheint dann aus dem Domänencontroller-Computerobjekt zu stammen.

In beiden Fällen können Sie auch explizit definieren, zu welchen Sicherheitsgruppen das virtuelle Konto gehört. Dies wird empfohlen, wenn eine Aufgabe ohne lokale Administrator- oder Domänenadministratorberechtigungen ausgeführt werden kann. Wenn Sie bereits eine Sicherheitsgruppe für Ihre Administratoren definiert haben, können Sie das virtuelle Konto zum Mitglied dieser Gruppe machen. Die Gruppenmitgliedschaft virtueller Konten ist auf lokale Sicherheitsgruppen auf Arbeitsstationen und Mitgliedsservern beschränkt. Auf Domänencontrollern müssen virtuelle Konten Mitglieder von Domänensicherheitsgruppen sein.
Sobald das virtuelle Konto einer oder mehreren Sicherheitsgruppen hinzugefügt wurde, gehört es nicht mehr zu den Standardgruppen (lokale oder Domänenadministratoren).

In der folgenden Tabelle werden die möglichen Konfigurationsoptionen und die sich daraus ergebenden Berechtigungen für virtuelle Konten zusammengefasst:

|        Computertyp         | Konfiguration virtueller Kontogruppen |                   Lokaler Benutzerkontext                    | Netzwerkbenutzerkontext |
| ---------------------------- | ----------------------------------- | ------------------------------------------------------- | -------------------- |
| Domänencontroller            | Standardwert                             | Domänenbenutzer, Mitglied von „*DOMÄNE*\Domänen-Admins“         | Computerkonto     |
| Domänencontroller            | Domänengruppen A und B               | Domänenbenutzer, Mitglied von „*DOMAIN*\A“, „*DOMAIN*\B“       | Computerkonto     |
| Mitgliedsserver oder Arbeitsstation | Standardwert                             | Lokaler Benutzer, Mitglied von „*BUILTIN*\Administrators“        | Computerkonto     |
| Mitgliedsserver oder Arbeitsstation | Lokale Gruppen C und D                | Lokale Gruppen, Mitglied von „*COMPUTER*\C“ und „*COMPUTER*\D“ | Computerkonto     |

Wenn Sie Sicherheitsüberwachungsereignisse und Anwendungsereignisprotokolle genauer betrachten, erkennen Sie, dass jede JEA-Benutzersitzung über ein eindeutiges virtuelles Konto verfügt. Dadurch können Sie die Benutzeraktionen in einem JEA-Endpunkt zum ursprünglichen Benutzer zurückverfolgen, der den Befehl ausgeführt hat. Virtuelle Kontonamen haben folgendes Format: `WinRM Virtual Users\WinRM_VA_<ACCOUNTNUMBER>_<DOMAIN>_<sAMAccountName>`. Wenn beispielsweise der Benutzer **Alice** in der Domäne **Contoso** einen Dienst in einem JEA-Endpunkt neu startet, so lautet der Benutzername, der einem beliebigen Ereignis eines Dienststeuerungs-Managers zugeordnet ist, `WinRM Virtual Users\WinRM_VA_1_contoso_alice`.

**Gruppenverwaltete Dienstkonten (gMSAs)** erweisen sich als nützlich, wenn ein Mitgliedsserver in der JEA-Sitzung auf Netzwerkressourcen zugreifen muss. Dies ist z. B der Fall, wenn ein JEA-Endpunkt zur Zugriffssteuerung für einen REST-API-Dienst genutzt wird, der auf einem anderen Computer gehostet wird. Sie können ganz einfach Funktionen zum Aufrufen der REST-APIs schreiben, Sie benötigen aber eine Netzwerkidentität für die Authentifizierung bei der API. Die Verwendung eines gruppenverwalteten Dienstkontos ermöglicht den „zweiten Hop“, während Sie weiterhin die Kontrolle darüber behalten, welche Computer das Konto verwenden können. Die effektiven Berechtigungen des gMSA werden durch die Sicherheitsgruppen (lokal oder Domäne) definiert, zu denen das gMSA-Konto gehört.

Wenn ein JEA-Endpunkt für die Verwendung von gMSA konfiguriert ist, sieht es aus, als stammten die Aktionen aller JEA-Benutzer aus demselben gMSA. Sie können die Aktionen eines bestimmten Benutzers nur dann zurückverfolgen, wenn Sie die ausgeführten Befehle identifizieren können, die in einer PowerShell-Sitzungsaufzeichnung erfasst sind.

**Pass-Through-Anmeldeinformationen** werden verwendet, wenn Sie kein **ausführendes Konto** angeben. PowerShell verwendet dann die Anmeldeinformationen des Benutzers, der die Verbindung herstellt, um Befehle auf dem Remoteserver ausführen. Dazu müssen Sie dem Benutzer, der die Verbindung herstellt, direkten Zugriff auf privilegierte Verwaltungsgruppen gewähren. Diese Konfiguration wird für JEA **nicht** empfohlen. Benutzer, die eine Verbindung herstellen und über Administratorberechtigungen verfügen, können JEA umgehen und das System über andere, uneingeschränkte Möglichkeiten verwalten. Weitere Informationen dazu, warum [JEA keinen Schutz von Administratoren bietet](#jea-doesnt-protect-against-admins), finden Sie im Abschnitt weiter unten.

**Standard-Ausführungskonten** ermöglichen Ihnen, ein beliebiges Benutzerkonto anzugeben, unter dem die gesamte PowerShell-Sitzung ausgeführt wird. Sitzungskonfigurationen mit festgelegten **ausführenden Konten** (mit dem `-RunAsCredential`-Parameter) sind nicht mit JEA kompatibel. Rollendefinitionen funktionieren nicht mehr wie erwartet. Jedem Benutzer, der zum Zugriff auf den Endpunkt berechtigt ist, wird die gleiche Rolle zugewiesen.

**RunAsCredential** sollte nicht auf einem JEA-Endpunkt verwendet werden, da Aktionen schwer zu bestimmten Benutzern zurückzuverfolgen sind und die Zuordnung von Benutzern zu Rollen nicht unterstützt wird.

## <a name="winrm-endpoint-acl"></a>WinRM-Endpunkt-ACL

Wie reguläre PowerShell-Remoting-Endpunkte verfügt jeder JEA-Endpunkt über eine separate Zugriffssteuerungsliste (ACL), die festlegt, wer für eine Authentifizierung mit dem JEA-Endpunkt berechtigt ist. Bei einer nicht ordnungsgemäßen Konfiguration können vertrauenswürdige Benutzer möglicherweise nicht auf den JEA-Endpunkt zugreifen und nicht vertrauenswürdige Benutzer Zugriff erhalten. Die WinRM-ACL wirkt sich nicht auf die Zuordnung von Benutzern zu JEA-Rollen aus. Dies wird über das **RoleDefinitions**-Feld in der Sitzungskonfigurationsdatei gesteuert, mit der der Endpunkt registriert wurde.

Wenn ein JEA-Endpunkt über mehrere Rollenfunktionen verfügt, wird die WinRM-ACL standardmäßig dafür konfiguriert, den Zugriff für alle zugeordneten Benutzer zu ermöglichen. So bietet beispielsweise eine mit den folgenden Befehlen konfigurierte JEA-Sitzung vollen Zugriff auf `CONTOSO\JEA_Lev1` und `CONTOSO\JEA_Lev2`.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

Sie können Benutzerberechtigungen über das [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration)-Cmdlet überwachen.

```powershell
Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission
```

```Output
Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Sie können den Zugriff der einzelnen Benutzer ändern, indem Sie entweder `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` für eine interaktive Aufforderung oder `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` ausführen, um die Berechtigungen zu aktualisieren. Benutzer müssen mindestens Rechte zum *Aufrufen* haben, um auf den JEA-Endpunkt zuzugreifen.

Es ist möglich, einen JEA-Endpunkt zu erstellen, der nicht jedem Benutzer mit Zugriff eine definierte Rolle zuordnet. Diese Benutzer können eine JEA-Sitzung starten, haben aber nur Zugriff auf die Standard-Cmdlets. Sie können die Benutzerberechtigungen in einem JEA-Endpunkt überwachen, indem Sie `Get-PSSessionCapability` ausführen. Weitere Informationen finden Sie unter [Überwachung und Berichterstellung zu JEA](audit-and-report.md).

## <a name="least-privilege-roles"></a>Rollen mit geringsten Rechten

Wenn Sie JEA-Rollen entwickeln, sollten Sie beachten, dass im Hintergrund ausgeführte virtuelle und gruppenverwaltete Dienstkonten uneingeschränkten Zugriff auf den lokalen Computer haben können. Mit JEA-Rollenfunktionen können Sie einschränken, welche Befehle und Anwendungen in diesem privilegierten Kontext ausgeführt werden können.
Aufgrund nicht ordnungsgemäß entwickelter Rollen lassen sich gefährliche Befehle ausführen: Benutzer können die JEA-Grenzen überschreiten oder sich Zugriff auf vertrauliche Informationen verschaffen.

Betrachten Sie beispielsweise den folgenden Rollenfunktionseintrag:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Über diese Rollenfunktion können Benutzer jedes beliebige PowerShell-Cmdlet mit dem Namen **Process** aus dem **Microsoft.PowerShell.Management**-Modul ausführen. Benutzer benötigen möglicherweise Zugriff auf Cmdlets wie `Get-Process`, um zu erfahren, welche Anwendungen auf dem System ausgeführt werden, oder auf `Stop-Process`, um Anwendungen zu beenden, die nicht mehr reagieren. Der Eintrag ermöglicht aber auch den Befehl `Start-Process`, um ein beliebiges Programm mit vollständigen Administratorberechtigungen zu starten. Das Programm muss nicht lokal im System installiert sein. Ein verbundener Benutzer kann aus einer Dateifreigabe ein Programm starten, das ihm lokale Administratorrechte gewährt, Schadsoftware ausführt o. ä.

Eine sicherere Version der gleichen Rollenfunktion würde so aussehen:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Verwenden Sie möglichst keine Platzhalter in Rollenfunktionen. [Überprüfen Sie regelmäßig die geltenden Benutzerberechtigungen](audit-and-report.md#check-effective-rights-for-a-specific-user), um zu sehen, welche Befehle für einen Benutzer zugänglich sind.

## <a name="jea-doesnt-protect-against-admins"></a>JEA bietet keinen Schutz vor Administratoren

Eines der wichtigsten Prinzipien von JEA ist, dass auch Nichtadministratoren gewisse Administratoraufgaben ausführen können. JEA bietet keinen Schutz vor Benutzern, die bereits über Administratorberechtigungen verfügen. Benutzer, die zur Gruppe **Domänen-Admins**, zur lokalen Gruppe **Administratoren** oder anderen Gruppen mit vielen Berechtigungen gehören, können die JEA-Schutzmaßnahmen auf andere Weise umgehen. Sie könnten sich z. B. mit RDP anmelden, Remote-MMC-Konsolen verwenden oder eine Verbindung mit uneingeschränkten PowerShell-Endpunkten herstellen. Lokale Administratoren im System können JEA-Konfigurationen ändern und zusätzlichen Benutzern Berechtigungen gewähren oder Rollenfunktionen ändern, um den Spielraum von Benutzern in ihrer JEA-Sitzung zu erweitern. Sie sollten daher die erweiterten Berechtigungen Ihrer JEA-Benutzer unbedingt überprüfen, um festzustellen, ob sie sich auf andere Art und Weise einen privilegierten Zugriff auf das System verschaffen könnten.

Üblicherweise wird JEA für regelmäßige tägliche Wartungsaufgaben verwendet. Benutzer können dank dieser privilegierten Just-in-Time-Zugriffsverwaltungslösung in Notfallsituationen vorübergehend zu lokalen Administratoren werden. Dadurch wird sichergestellt, dass Benutzer nicht zu permanenten Administratoren im System werden. Sie erhalten diese Berechtigung nur dann, wenn sie einen Workflow ausführen, der die Verwendung dieser Berechtigungen dokumentiert.
