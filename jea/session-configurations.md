---
manager: carmonm
ms.topic: article
author: rpsqrd
ms.author: ryanpu
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2017-03-08
title: JEA-Sitzungskonfigurationen
ms.technology: powershell
ms.openlocfilehash: e98214d1777a1530b5a18ac9df1a6185d6d73979
ms.sourcegitcommit: 910f090edd401870fe137553c3db00d562024a4c
translationtype: HT
---
# <a name="jea-session-configurations"></a>JEA-Sitzungskonfigurationen

> Gilt für: Windows PowerShell 5.0

Ein JEA-Endpunkt wird auf einem System durch Erstellen und Registrieren einer PowerShell-Konfigurationsdatei auf eine bestimmte Art und Weise registriert.
Sitzungskonfigurationen bestimmen, *welche Benutzer* den JEA-Endpunkt verwenden können und auf welche Rollen sie Zugriff haben.
Sie legen außerdem globale Einstellungen fest, die für alle Benutzer einer Rolle in der JEA-Sitzung gelten.

In diesem Thema wird beschrieben, wie Sie eine PowerShell-Konfigurationsdatei erstellen und einen JEA-Endpunkt registrieren.

## <a name="create-a-session-configuration-file"></a>Erstellen einer Sitzungskonfigurationsdatei

Sie müssen zunächst angeben, wie ein JEA-Endpunkt konfiguriert werden soll, bevor Sie ihn registrieren können.
Dabei stehen mehrere Optionen zur Auswahl. Am wichtigsten sind die folgenden: Wer sollte Zugriff auf den JEA-Endpunkt haben? Welche Rollen sollten den Benutzern zugewiesen werden? Welche Identität verwendet JEA unter der Oberfläche und welchen Namen soll der JEA-Endpunkt erhalten?
Alle diese Einstellungen sind in einer PowerShell-Sitzungskonfigurationsdatei definiert. Dabei handelt es sich um eine PowerShell-Datendatei mit der Erweiterung PSSC.

Führen Sie den folgenden Befehl aus, um eine Gerüstdatei der Sitzungskonfigurationsdatei für JEA-Endpunkte zu erstellen:

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Standardmäßig sind nur die häufigsten Konfigurationsoptionen in der Gerüstdatei vorhanden.
> Verwenden Sie den `-Full`-Switch, um alle anwendbaren Einstellungen in die generierte PSSC-Datei einzuschließen.

Sie können die Sitzungskonfigurationsdatei in einem beliebigen Texteditor öffnen.
Das `-SessionType RestrictedRemoteServer`-Feld gibt an, dass die Sitzungskonfiguration von JEA für eine sichere Verwaltung verwendet wird.
Auf diese Weise konfigurierte Sitzungen arbeiten im [NoLanguage-Modus](https://technet.microsoft.com/en-us/library/dn433292.aspx) und verfügen nur über die folgenden acht Standard-Cmdlets (und Aliase):

- Clear-Host (cls, löschen)
- Exit-PSSession (exsn, beenden)
- Get-Command (gcm)
- Get-FormatData
- "Get-Help "
- Measure-Object (messen)
- Out-Default
- Select-Object (auswählen)

Weder PowerShell-Anbieter noch externe Programme (ausführbare Dateien, Skripts usw.) stehen zur Verfügung.

Es gibt mehrere andere Felder, die Sie für die JEA-Sitzung konfigurieren sollten.
Sie werden in den folgenden Abschnitten beschrieben.

### <a name="choose-the-jea-identity"></a>Wählen der JEA-Identität

JEA benötigt ein Identitätskonto im Hintergrund, wenn die Befehle eines Benutzers ausgeführt werden, der die Verbindung herstellt.
Sie entscheiden, welche Identität JEA in der Sitzungskonfigurationsdatei verwendet.

#### <a name="local-virtual-account"></a>Lokales virtuelles Konto

Wenn alle von diesem JEA-Endpunkt unterstützten Rollen für die Verwaltung des lokalen Computers eingesetzt werden und ein lokales Administratorkonto ausreicht, um die Befehle erfolgreich auszuführen, sollten Sie JEA für die Verwendung eines lokalen virtuellen Kontos konfigurieren.
Virtuelle Konten sind temporäre Konten, die für einen bestimmten Benutzer eindeutig sind und nur für die Dauer seiner PowerShell-Sitzung gültig sind.
Virtuelle Konten auf einem Mitgliedsserver oder einer Arbeitsstation gehören zur Gruppe der **Administratoren** des lokalen Computers und haben Zugriff auf die meisten Systemressourcen.
Auf einem Active Directory-Domänencontroller gehören virtuelle Konten zur Gruppe der **Domänen-Admins** der Domäne.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Wenn die Rollen, die von der Sitzungskonfiguration unterstützt werden, keine derart umfassenden Berechtigungen benötigen, können Sie optional die Sicherheitsgruppen angeben, zu denen das virtuelle Konto gehören wird.
Auf einem Mitgliedsserver oder einer Arbeitsstation müssen die angegebenen Sicherheitsgruppen lokale Gruppen sein. Es darf sich nicht um Gruppen aus einer Domäne handeln.

Wenn eine oder mehrere Sicherheitsgruppen angegeben wurden, gehört das virtuelle Konto nicht mehr zur lokalen Gruppe oder der Administratorengruppe der Domäne.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a>Gruppenverwaltetes Dienstkonto


Für Szenarios, in denen der JEA-Benutzer Zugriff auf Netzwerkressourcen wie einen anderen Computer oder andere Webdienste benötigt, empfiehlt sich ein gruppenverwaltetes Dienstkonto (Group Managed Service Account, gMSA) als bessere Identität.
gMSA-Konten bieten Ihnen eine Domänenidentität, die eine Authentifizierung von Ressourcen auf einem beliebigen Computer innerhalb der Domäne ermöglicht.
Die Rechte eines gMSA-Kontos werden durch die Ressourcen bestimmt, auf die Sie zugreifen.
Administratorrechte auf einem beliebigen Computer oder auf Dienste werden automatisch zugewiesen, wenn Ihnen der Computer-/Dienstadministrator explizit Administratorberechtigungen für das gMSA-Konto erteilt hat.

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'MyJEAgMSA'
```

gMSA-Konten sollten nur dann verwendet werden, wenn ein Zugriff auf Netzwerkressourcen erforderlich ist, und das aus folgenden Gründen:

- Es ist schwieriger, Aktionen zu einem Benutzer zurückzuverfolgen, wenn ein gMSA-Konto verwendet wird, da jeder Benutzer die gleiche ausführende Identität aufweist. Sie müssen PowerShell-Sitzungsaufzeichnungen und -protokolle überprüfen, um Benutzer mit ihren Aktionen zu korrelieren.

- Das gMSA-Konto hat möglicherweise Zugriff auf zahlreiche Netzwerkressourcen, auf die der Benutzer, der eine Verbindung herstellt, keinen Zugriff benötigt. Versuchen Sie immer, effektive Berechtigungen in einer JEA-Sitzung zu beschränken und damit das Prinzip der geringsten Rechte anzuwenden.

> [!NOTE]
> Gruppenverwaltete Dienstkonten sind nur unter Windows PowerShell 5.1 oder höher verfügbar sowie auf den einer Domäne angehörigen Computern.


#### <a name="more-information-about-run-as-users"></a>Weitere Informationen zum Ausführen als Benutzer

Weitere Informationen zum Ausführen als Identitäten und wie sie zur Sicherheit einer JEA-Sitzung beitragen finden Sie im Artikel zum Thema [Security Considerations (Sicherheitsaspekte)](security-considerations.md).

### <a name="session-transcripts"></a>Sitzungsaufzeichnungen

Es wird empfohlen, dass Sie eine JEA-Sitzungskonfigurationsdatei konfigurieren, um Protokolle von Benutzersitzungen automatisch aufzuzeichnen.
PowerShell-Sitzungsaufzeichnungen enthalten Informationen zu Benutzern, die eine Verbindung herstellen, die ihnen zugewiesene ausführende Identität und die vom Benutzer ausgeführten Befehle.
Diese Informationen können für ein Überwachungsteam nützlich sein, das wissen muss, wer an einem System eine Änderung vorgenommen hat.

Geben Sie einen Pfad zu einem Ordner an, in dem die Aufzeichnungen gespeichert werden sollen, um eine automatische Protokollierung in der Sitzungskonfigurationsdatei festzulegen.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

Der angegebene Ordner sollte so konfiguriert sein, dass Benutzer ihn weder ändern noch darin enthaltene Daten löschen können.
Aufzeichnungen werden durch das lokale Systemkonto in den Ordner geschrieben, was Lese- und Schreibzugriff auf das Verzeichnis voraussetzt.
Standardbenutzer sollten keinen Zugriff auf den Ordner haben. Außerdem sollte nur eine begrenzte Anzahl von Sicherheitsadministratoren über Rechte für die Überwachung der Aufzeichnungen verfügen.

### <a name="user-drive"></a>Benutzerlaufwerk

Wenn Benutzer, die eine Verbindung herstellen, Dateien von einem bzw. auf einen JEA-Endpunkt kopieren müssen, um einen Befehl auszuführen, können Sie das Benutzerlaufwerk in der Sitzungskonfigurationsdatei aktivieren.
Das Benutzerlaufwerk ist ein [PSDrive](https://msdn.microsoft.com/en-us/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives), das einem eindeutigen Ordner für jeden Benutzer zugeordnet ist, der eine Verbindung herstellt.
Dieser Ordner dient als Speicherplatz, um Dateien vom und auf das System zu kopieren, ohne dass die Benutzer Zugriff auf das gesamte Dateisystem benötigen bzw. ohne den FileSystem-Anbieter verfügbar zu machen.
Der Inhalt der Benutzerlaufwerke steht durchgehend und sitzungsübergreifend zur Verfügung, um in Situationen Abhilfe zu schaffen, in denen die Netzwerkkonnektivität unterbrochen ist.

```powershell
MountUserDrive = $true
```

Auf dem Benutzerlaufwerk können standardmäßig maximal 50 MB Daten pro Benutzer gespeichert werden.
Sie können die Datenmenge, die ein Benutzer nutzen kann, mithilfe des Felds *UserDriveMaxmimumSize* einschränken.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Wenn die Daten auf dem Laufwerk nicht permanent zur Verfügung stehen sollen, können Sie eine geplante Aufgabe auf dem System konfigurieren, damit der Ordner jede Nacht automatisch bereinigt wird.

> [!NOTE]
> Das Benutzerlaufwerk ist nur in Windows PowerShell 5.1 oder höher verfügbar.

### <a name="role-definitions"></a>Rollendefinitionen

Über Rollendefinitionen in einer Sitzungskonfigurationsdatei legen Sie fest, welche *Benutzer* welchen *Rollen* zugeordnet sind.
Jeder Benutzer bzw. jede Gruppe in diesem Feld erhält automatisch Berechtigungen für den JEA-Endpunkt, sobald er registriert ist.
Jeder Benutzer und jede Gruppe kann jeweils nur einmal als Schlüssel in der Hashtabelle eingefügt werden, darf jedoch über mehrere Rollen verfügen.
Der Name der Rollenfunktion sollte dem Namen der Rollenfunktionsdatei ohne die Erweiterung PSRC entsprechen.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Wenn ein Benutzer zu mehr als einer Gruppe in der Rollendefinition gehört, erhält er Zugriff auf die Rollen jeder einzelnen Gruppe.
Wenn zwei Rollen Zugriff auf die gleichen Cmdlets vergeben, erhält der Benutzer den Parameter mit den höchsten Berechtigungen.

### <a name="role-capability-search-order"></a>Suchreihenfolge für Rollenfunktionen
Wie im obigen Beispiel gezeigt, wird auf die Rollenfunktionen durch den flachen Namen (Dateiname ohne Erweiterung) verwiesen.
Wenn mehrere Rollenfunktionen mit dem gleichen flachen Namen im System verfügbar sind, verwendet PowerShell die implizite Suchreihenfolge, um die zutreffende Rollenfunktionsdatei auszuwählen.
Sie erhalten **keinen** Zugriff auf alle Rollenfunktionsdateien mit dem gleichen Namen.

JEA verwendet die Umgebungsvariable `$env:PSModulePath`, um zu bestimmen, welche Pfaden nach Rollenfunktionsdateien gescannt werden sollen.
JEA sucht innerhalb dieser Pfade nach gültigen PowerShell-Modulen, die einen Unterordner namens „RoleCapabilities“ enthalten.
Wie beim Importieren von Modulen zieht JEA Rollenfunktionen, die mit Windows ausgeliefert wurden, benutzerdefinierten Rollenfunktionen gleichen Namens vor.
Bei allen anderen Namenskonflikten wird die Rangfolge durch die Reihenfolge bestimmt, in der Windows die Dateien im Verzeichnis aufzählt (nicht unbedingt alphabetisch).
Die erste gefundene Rollenfunktionsdatei, die den gewünschten Namen hat, wird für den verbindenden Benutzer verwendet.

Da die Suchreihenfolge der Rollenfunktion nicht deterministisch ist, wenn zwei oder mehr Funktionen der Rolle den gleichen Namen aufweisen, wird **dringend empfohlen**, sicherzustellen, dass Rollenfunktionen auf Ihrem Computer über eindeutige Namen verfügen.

### <a name="conditional-access-rules"></a>Regeln für bedingten Zugriff

Alle Benutzer und Gruppen im Feld „RoleDefinitions“ haben automatisch Zugriff auf JEA-Endpunkte.
Anhand von bedingten Zugriffsregeln können Sie diesen Zugriff optimieren und zur Bedingung machen, dass Benutzer zusätzlichen Sicherheitsgruppen angehören, die keinen Einfluss auf die ihnen zugewiesenen Rollen haben.
Dies kann hilfreich sein, wenn Sie eine Just-in-Time-Privileged Access Management-Lösung, eine Smartcard-Authentifizierung oder eine andere Multifaktor-Authentifizierungslösung mit JEA integrieren möchten.

Bedingte Zugriffsregeln werden im Feld „RequiredGroups“ in einer Sitzungskonfigurationsdatei definiert.
Geben Sie dazu eine (optional geschachtelte) Hashtabelle an, die zum Erstellen Ihrer Regeln die Schlüssel „And“ und „Or“ verwendet.
Nachfolgend finden Sie einige Beispiele für die Verwendung dieses Felds:

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> Bedingte Zugriffsregeln sind nur in Windows PowerShell 5.1 oder höher verfügbar.

### <a name="other-properties"></a>Weitere Eigenschaften
Sitzungskonfigurationsdateien verfügen über die gleichen Möglichkeiten wie eine Rollenfunktionsdatei, ohne jedoch Benutzern, die eine Verbindung herstellen, Zugriff auf unterschiedliche Befehle zu geben.
Wenn Sie allen Benutzern den Zugriff auf bestimmte Cmdlets, Funktionen oder Anbieter ermöglichen möchten, können Sie dies direkt in der Sitzungskonfigurationsdatei tun.
Eine vollständige Liste der unterstützten Eigenschaften in der Sitzungskonfigurationsdatei erhalten Sie, wenn Sie `Get-Help New-PSSessionConfigurationFile -Full` ausführen.

## <a name="testing-a-session-configuration-file"></a>Testen einer Sitzungskonfigurationsdatei

Sie können eine Sitzungskonfigurationsdatei über das [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile)-Cmdlet testen.
Es wird dringend empfohlen, die Sitzungskonfigurationsdatei zu testen, wenn Sie die PSSC-Datei manuell mithilfe eines Text-Editors bearbeitet haben, um eine korrekte Syntax zu gewährleisten.
Wenn eine Sitzungskonfigurationsdatei den Test nicht bestanden hat, kann sie nicht erfolgreich auf dem System registriert werden.

## <a name="sample-session-configuration-file"></a>Beispiel für eine Sitzungskonfigurationsdatei

Nachstehend finden Sie ein vollständiges Beispiel zum Erstellen und Überprüfen einer Sitzungskonfiguration für JEA.
Beachten Sie, dass die Rollendefinitionen zur Vereinfachung und aus Gründen der Lesbarkeit in der `$roles`-Variablen erstellt und gespeichert werden.
Dies ist jedoch nicht Voraussetzung.

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a>Aktualisieren von Sitzungskonfigurationsdateien

Wenn Sie die Eigenschaften einer JEA-Sitzungskonfiguration einschließlich der Zuordnung von Benutzern zu Rollen ändern möchten, müssen Sie für diese JEA-Sitzungskonfiguration zunächst die [Registrierung aufheben](register-jea.md#unregistering-jea-configurations) und sie dann [erneut registrieren](register-jea.md).
Wenn Sie die JEA-Sitzungskonfiguration erneut registrieren, verwenden Sie eine aktualisierte PowerShell-Sitzungskonfigurationsdatei, die die gewünschten Änderungen enthält.

## <a name="next-steps"></a>Nächste Schritte

- [Register a JEA configuration (Registrieren einer JEA-Konfiguration)](register-jea.md)
- [Author JEA roles (Erstellen von JEA-Rollen)](role-capabilities.md)
