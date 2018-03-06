---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Ausführen des zweiten Hops in PowerShell-Remoting"
ms.openlocfilehash: 726b4d1b7a41e9e344347543ecde26da6547bcf3
ms.sourcegitcommit: fff6c0522508eeb408cb055ba4c9337a2759b392
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/23/2018
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>Ausführen des zweiten Hops in PowerShell-Remoting

Das sogenannte „zweite Hop-Problem“ bezieht sich auf folgende Situation:

1. Sie sind bei _ServerA_ angemeldet.
2. Sie starten von _ServerA_ aus eine PowerShell-Remotesitzung, um eine Verbindung mit _ServerB_ herzustellen.
3. Ein auf _ServerB_ über Ihre PowerShell-Remotesitzung ausgeführter Befehl versucht, auf eine Ressource auf _ServerC_ zuzugreifen.
4. Der Zugriff auf die Ressource auf _ServerC_ wird verweigert, da die Anmeldeinformationen, die Sie zum Erstellen der PowerShell-Remotesitzung verwendet haben, nicht von _ServerB_ an _ServerC_ übergeben werden.

Es gibt verschiedene Möglichkeiten, um dieses Problem zu lösen. In diesem Thema werden einige der geläufigsten Lösungen für das zweite Hop-Problem vorgestellt.

## <a name="credssp"></a>CredSSP

Sie können den [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb931352.aspx) für die Authentifizierung verwenden. CredSSP speichert Anmeldeinformationen auf dem Remoteserver  _ServerB_. Der Server wird dadurch der Gefahr von Angriffen zum Diebstahl der Anmeldeinformationen ausgesetzt. Wenn der Remotecomputer kompromittiert ist, hat der Angreifer Zugriff auf die Anmeldeinformationen des Benutzers. CredSSP ist standardmäßig sowohl auf Client- als auch auf Servercomputern deaktiviert. Sie sollten CredSSP nur in absolut vertrauenswürdigen Umgebungen aktivieren. Beispielsweise wenn ein Domänenadministrator eine Verbindung mit einem Domänencontroller herstellt, weil der Domänencontroller hochgradig vertrauenswürdig ist.

Weitere Informationen zu Sicherheitsaspekten bei der Verwendung von CredSSP für PowerShell-Remoting finden Sie unter [Versehentliche Sabotage: Vorsicht vor CredSSP](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).

Weitere Informationen zu Angriffen zum Diebstahl von Anmeldeinformationen finden Sie unter [Abschwächen von Pass-the-Hash-Angriffen (PtH) und anderen Techniken zum Diebstahl von Anmeldeinformationen](https://www.microsoft.com/en-us/download/details.aspx?id=36036).

Ein Beispiel zum Aktivieren und Verwenden von CredSSP für PowerShell-Remoting finden Sie unter [Using CredSSP to solve the second-hop problem (Verwenden von CredSSP zur Lösung des zweiten Hop-Problems)](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).

### <a name="pros"></a>Vorteile

- Die Lösung eignet sich für alle Server mit Windows Server 2008 oder höher.

### <a name="cons"></a>Nachteile

- birgt Sicherheitsrisiken
- erfordert die Konfiguration von Client- und Serverrollen

## <a name="kerberos-delegation-unconstrained"></a>Kerberos-Delegierung (uneingeschränkt)

Sie können auch die uneingeschränkte Kerberos-Delegierung verwenden, um den zweiten Hop ausführen. Diese Methode ermöglicht jedoch keine Kontrolle darüber, wo die delegierten Anmeldeinformationen verwendet werden.

>**Hinweis:** Active Directory-Konten mit dem Eigenschaftensatz **Konto ist vertraulich und kann nicht delegiert werden** können nicht delegiert werden. Weitere Informationen finden Sie unter [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts (Sicherheit im Fokus: Analyse von „Konto ist vertraulich und kann nicht delegiert werden“ für privilegierte Konten)](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) und [Kerberos Authentication Tools and Settings (Kerberos-Authentifizierungstools und -Einstellungen)](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Vorteile

- erfordert keine besondere Codierung

### <a name="cons"></a>Nachteile

- keine Unterstützung für den zweiten Hop für WinRM
- bietet keine Kontrolle darüber, wo Anmeldeinformationen verwendet werden; birgt Sicherheitsrisiken

## <a name="kerberos-constrained-delegation"></a>Eingeschränkte Kerberos-Delegierung

Sie können eingeschränkte Legacydelegierung (nicht ressourcenbasiert) verwenden, um den zweiten Hop auszuführen. 

>**Hinweis:** Active Directory-Konten mit dem Eigenschaftensatz **Konto ist vertraulich und kann nicht delegiert werden** können nicht delegiert werden. Weitere Informationen finden Sie unter [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts (Sicherheit im Fokus: Analyse von „Konto ist vertraulich und kann nicht delegiert werden“ für privilegierte Konten)](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) und [Kerberos Authentication Tools and Settings (Kerberos-Authentifizierungstools und -Einstellungen)](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Vorteile

- erfordert keine besondere Codierung

### <a name="cons"></a>Nachteile

- keine Unterstützung für den zweiten Hop für WinRM
- muss auf dem Active Directory-Objekt des Remoteservers konfiguriert werden (_ServerB_)
- auf einen Server begrenzt; kann Domänen oder Gesamtstrukturen nicht überschreiten
- erfordert Rechte zum Aktualisieren von Objekten und Dienstprinzipalnamen (SPN)

## <a name="resource-based-kerberos-constrained-delegation"></a>Ressourcenbasierte eingeschränkte Kerberos-Delegierung

Mithilfe von ressourcenbasierter eingeschränkter Kerberos-Delegierung (in Windows Server 2012 eingeführt) können Sie die Delegierung der Anmeldeinformationen für das Serverobjekt konfigurieren, in dem sich Ressourcen befinden.
Im zuvor beschriebenen zweiten Hop-Szenario konfigurieren Sie _ServerC_ und geben an, von wo aus Anmeldeinformationen akzeptiert werden.

>**Hinweis:** Active Directory-Konten mit dem Eigenschaftensatz **Konto ist vertraulich und kann nicht delegiert werden** können nicht delegiert werden. Weitere Informationen finden Sie unter [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts (Sicherheit im Fokus: Analyse von „Konto ist vertraulich und kann nicht delegiert werden“ für privilegierte Konten)](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) und [Kerberos Authentication Tools and Settings (Kerberos-Authentifizierungstools und -Einstellungen)](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Vorteile

- kein Speichern von Anmeldeinformationen
- relativ einfach mithilfe von PowerShell-Cmdlets konfigurierbar – keine spezielle Codierung erforderlich
- kein spezieller Domänenzugriff erforderlich
- domänen- und gesamtstrukturübergreifende Funktionsweise
- PowerShell-Code

### <a name="cons"></a>Nachteile

- erfordert Windows Server 2012 oder höher
- keine Unterstützung für den zweiten Hop für WinRM
- erfordert Rechte zum Aktualisieren von Objekten und Dienstprinzipalnamen (SPN) 

### <a name="example"></a>Beispiel

Sehen wir uns ein PowerShell-Beispiel an, bei dem _ServerC_ für eine ressourcenbasierte eingeschränkte Delegierung konfiguriert wird, um delegierte Anmeldeinformationen von einem _ServerB_ zu ermöglichen.
In diesem Beispiel wird davon ausgegangen, dass alle Server Windows Server 2012 oder höher ausführen und dass für jede Domäne jedes eingesetzten Servers mindestens ein Windows Server 2012-Domänencontroller vorhanden ist.

Bevor Sie die eingeschränkte Delegierung konfigurieren können, müssen Sie das `RSAT-AD-PowerShell`-Feature hinzufügen, um das Active Directory-PowerShell-Modul zu installieren und anschließend dieses Modul in die Sitzung zu importieren:

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
Mehrere verfügbare Cmdlets haben jetzt einen **PrincipalsAllowedToDelegateToAccount**-Parameter:

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName     
----------- ----                 ----------     
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

Der Parameter **PrincipalsAllowedToDelegateToAccount** legt das Active Directory-Objektattribut **MsDS-AllowedToActOnBehalfOfOtherIdentity** fest, das eine Zugriffssteuerungsliste (access control list, ACL) enthält. Diese gibt an, welche Konten die Berechtigung zum Delegieren von Anmeldeinformationen für das zugehörige Konto haben (in unserem Beispiel das Computerkonto für _Server_).

Richten Sie nun die Variablen ein, die wir verwenden, um die Server darzustellen:

```powershell
# Set up variables for reuse            
$ServerA = $env:COMPUTERNAME            
$ServerB = Get-ADComputer -Identity ServerB            
$ServerC = Get-ADComputer -Identity ServerC            
```

WinRM (und somit die PowerShell-Remoting) wird standardmäßig als Computerkonto ausgeführt. Dies sehen Sie anhand der **StartName**-Eigenschaft des `winrm`-Diensts:

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

Damit _ServerC_ die Delegierung aus einer PowerShell-Remoting-Sitzung auf _ServerB_ zulässt, vergeben wir Zugriffsrechte, indem wir den Parameter **PrincipalsAllowedToDelegateToAccount** von _ServerC_ auf das Computerobjekt von _ServerB_ festlegen:

```powershell
# Grant resource-based Kerberos constrained delegation            
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB            
            
# Check the value of the attribute directly            
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity            
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access            
            
# Check the value of the attribute indirectly            
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

Das Kerberos-[Schlüsselverteilungscenter (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) speichert verweigerte Zugriffsversuche (negativer Cache) über einen Zeitraum von 15 Minuten. Wenn _ServerB_ zuvor versucht hat, auf _ServerC_ zuzugreifen, müssen Sie zum Löschen des Caches auf _ServerB_ folgenden Befehl aufrufen:

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {            
    klist purge -li 0x3e7            
}
```

Sie können den Computer auch neu starten oder mindestens 15 Minuten warten, bevor Sie den Cache löschen.

Nach dem Löschen des Cache können Sie erfolgreich Code vom _ServerA_ über _ServerB_ auf _ServerC_ ausführen:

```powershell
# Capture a credential            
$cred = Get-Credential Contoso\Alice            
            
# Test kerberos double hop            
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {            
    Test-Path \\$($using:ServerC.Name)\C$            
    Get-Process lsass -ComputerName $($using:ServerC.Name)            
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)            
}
```

In diesem Beispiel wird die `$using`-Variable verwendet, um die `$ServerC`-Variable für _ServerB_ sichtbar zu machen. Weitere Informationen zur `$using`-Variable finden Sie unter [About Remote Variables (Informationen zu Remote-Variablen)](https://technet.microsoft.com/en-us/library/jj149005.aspx).

Damit mehrere Server Anmeldeinformationen an _ServerC_ delegieren können, müssen Sie den Wert des Parameters **PrincipalsAllowedToDelegateToAccount** auf _ServerC_ auf ein Array festlegen:

```powershell
# Set up variables for each server            
$ServerB1 = Get-ADComputer -Identity ServerB1            
$ServerB2 = Get-ADComputer -Identity ServerB2            
$ServerB3 = Get-ADComputer -Identity ServerB3            
$ServerC  = Get-ADComputer -Identity ServerC            
            
# Grant resource-based Kerberos constrained delegation            
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

Wenn Sie den zweiten Hop zwischen Domänen vornehmen möchten, müssen Sie den vollqualifizierten Domänennamen (FQDN) des Domänencontrollers jener Domäne hinzufügen, zu der _ServerB_ gehört:

```powershell
# For ServerC in Contoso domain and ServerB in other domain            
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com            
$ServerC = Get-ADComputer -Identity ServerC            
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

Um die Delegierung von Anmeldeinformationen an ServerC zu löschen, müssen Sie den Wert des Parameters **PrincipalsAllowedToDelegateToAccount** auf _ServerC_ auf `$null` festlegen:

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>Informationen zu ressourcenbasierter eingeschränkter Kerberos-Delegierung

- [Neues bei der Kerberos-Authentifizierung](https://technet.microsoft.com/library/hh831747.aspx)
- [How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1 (Wie Windows Server 2012 bei den Problemen mit der eingeschränkten Kerberos-Delegierung Abhilfe schafft, Teil 1)](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2 (Wie Windows Server 2012 bei den Problemen mit der eingeschränkten Kerberos-Delegierung Abhilfe schafft, Teil 2)](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication (Grundlegendes zur eingeschränkten Kerberos-Delegierung für Azure Active Directory Application Proxy-Bereitstellungen mit integrierter Windows-Authentifizierung)](http://aka.ms/kcdpaper)
- [[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity ([MS-ADA2]: Active Directory-Schemaattribute M2.210 msDS-AllowedToActOnBehalfOfOtherIdentity-Attribut)](https://msdn.microsoft.com/en-us/library/hh554126.aspx)
- [[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy ([MS-SFU]: Kerberos-Protokollerweiterungen: Dienst für Benutzer und eingeschränktes Delegierungsprotokoll 1.3.2 S4U2proxy)](https://msdn.microsoft.com/en-us/library/cc246079.aspx)
- [Resource Based Kerberos Constrained Delegation (Ressourcenbasierte eingeschränkte Kerberos-Delegierung)](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount (Remoteverwaltung ohne eingeschränkte Delegierung mit PrincipalsAllowedToDelegateToAccount)](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a>PSSessionConfiguration mithilfe von RunAs

Sie können eine Sitzungskonfiguration auf _ServerB_ erstellen und ihren **RunAsCredential**-Parameter festlegen.

Weitere Informationen zur Verwendung von PSSessionConfiguration und RunAs, um das zweite Hop-Problem zu lösen, finden Sie unter [Another solution to multi-hop PowerShell remoting (Eine weitere Lösung für Multi-Hop-PowerShell-Remoting)](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).

### <a name="pros"></a>Vorteile

- funktioniert mit jedem Server mit WMF 3.0 oder höher

### <a name="cons"></a>Nachteile

- erfordert die Konfiguration von **PSSessionConfiguration** und **RunAs** auf jedem Zwischenserver (_ServerB_)
- erfordert Kennwortverwaltungsaufgaben bei Verwendung eines Domänen-**RunAs**-Kontos

## <a name="just-enough-administration-jea"></a>Just Enough Administration (JEA)

Mit JEA können Sie einschränken, welche Befehle ein Administrator während einer PowerShell-Sitzung ausführen darf. Das Toolkit kann verwendet werden, um das zweite Hop-Problem zu lösen.

Informationen zu JEA finden Sie unter [Just Enough Administration](https://docs.microsoft.com/en-us/powershell/jea/overview).

### <a name="pros"></a>Vorteile

- keine Kennwortverwaltungsaufgaben bei Verwendung eines virtuellen Kontos

### <a name="cons"></a>Nachteile

- erfordert WMF 5.0 oder höher
- erfordert die Konfiguration auf jedem Zwischenserver (_ServerB_).

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>Übergeben von Anmeldeinformationen innerhalb eines Invoke-Command-Skriptblocks

Anmeldeinformationen können innerhalb des **ScriptBlock**-Parameters für einen Aufruf des [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command)-Cmdlet übergeben werden.

### <a name="pros"></a>Vorteile

- erfordert keine spezielle Serverkonfiguration
- funktioniert auf jedem Server mit WMF 2.0 oder höher

### <a name="cons"></a>Nachteile

- erfordert eine umständliche Codetechnik
- Wenn WMF 2.0 ausgeführt wird, wird eine andere Syntax zum Übergeben von Argumenten an eine Remotesitzung benötigt.

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie Anmeldeinformationen in einem **Invoke-Command**-Skriptblock übergeben werden:

```powershell
# This works without delegation, passing fresh creds            
# Note $Using:Cred in nested request            
$cred = Get-Credential Contoso\Administrator            
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {            
    hostname            
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}            
}
```

## <a name="see-also"></a>Siehe auch

[Sicherheitsaspekte von PowerShell-Remoting](WinRMSecurity.md)








 
