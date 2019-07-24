---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: JEA-Sitzungskonfigurationen
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726548"
---
# <a name="jea-session-configurations"></a>JEA-Sitzungskonfigurationen

Ein JEA-Endpunkt wird in einem System durch Erstellen und Registrieren einer PowerShell-Sitzungskonfigurationsdatei registriert. Sitzungskonfigurationen definieren, welche Benutzer den JEA-Endpunkt verwenden können und auf welche Rollen sie Zugriff haben. Sie legen außerdem globale Einstellungen fest, die für alle Benutzer der JEA-Sitzung gelten.

## <a name="create-a-session-configuration-file"></a>Erstellen einer Sitzungskonfigurationsdatei

Sie müssen zunächst angeben, wie der JEA-Endpunkt konfiguriert ist, bevor Sie ihn registrieren können. Dafür gibt es zahlreiche Optionen. Folgende Fragen sind dabei entscheidend:

- Wer soll auf den JEA-Endpunkt zugreifen können?
- Welche Rollen sollen den Benutzern zugewiesen werden?
- Welche Identität wird von JEA im Hintergrund verwendet?
- Welchen Namen soll der JEA-Endpunkt erhalten?

Diese Optionen werden in einer PowerShell-Datendatei mit der Erweiterung `.pssc`, auch PowerShell-Sitzungskonfigurationsdatei genannt, definiert. Sie können die Sitzungskonfigurationsdatei mit einem beliebigen Text-Editor bearbeiten.

Führen Sie den folgenden Befehl aus, um eine leere Vorlagenkonfigurationsdatei zu erstellen:

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Standardmäßig enthält die Vorlagendatei nur die häufigsten Konfigurationsoptionen. Verwenden Sie den `-Full`-Switch, um alle anwendbaren Einstellungen in die generierte PSSC-Datei einzuschließen.

Das Feld `-SessionType RestrictedRemoteServer` gibt an, dass die Sitzungskonfiguration von JEA für eine sichere Verwaltung verwendet wird. Sitzungen dieses Typs arbeiten im Modus **NoLanguage** und können nur auf die folgenden Standardbefehle (und Aliase) zugreifen:

- Clear-Host (cls, löschen)
- Exit-PSSession (exsn, beenden)
- Get-Command (gcm)
- Get-FormatData
- "Get-Help "
- Measure-Object (messen)
- Out-Default
- Select-Object (auswählen)

Weder PowerShell-Anbieter noch externe Programme (ausführbare Dateien oder Skripts) stehen zur Verfügung.

Weitere Informationen zu Sprachmodi finden Sie unter [About_Language_Modes (Informationen zu Sprachmodi)](/powershell/module/microsoft.powershell.core/about/about_language_modes).

### <a name="choose-the-jea-identity"></a>Wählen der JEA-Identität

JEA benötigt ein Identitätskonto im Hintergrund, wenn die Befehle eines Benutzers ausgeführt werden, der die Verbindung herstellt.
Sie legen fest, welche Identität von JEA in der Sitzungskonfigurationsdatei verwendet wird.

#### <a name="local-virtual-account"></a>Lokales virtuelles Konto

Die Verwendung eines lokalen virtuellen Kontos ist geeignet für Fälle, in denen alle für diesen JEA-Endpunkt definierten Rollen für die Verwaltung des lokalen Computers eingesetzt werden und ein lokales Administratorkonto ausreicht, um die Befehle erfolgreich auszuführen.
Virtuelle Konten sind temporäre Konten, die für einen bestimmten Benutzer eindeutig sind und nur für die Dauer seiner PowerShell-Sitzung gültig sind. Virtuelle Konten auf einem Mitgliedsserver oder einer Arbeitsstation gehören zur Gruppe der **Administratoren** des lokalen Computers. Auf einem Active Directory-Domänencontroller gehören virtuelle Konten zur Gruppe der **Domänen-Admins** der Domäne.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Wenn die durch die Sitzungskonfiguration definierten Rollen keine vollständigen Administratorrechte benötigen, können Sie die Sicherheitsgruppen angeben, zu denen das virtuelle Konto gehören soll. Auf einem Mitgliedsserver oder einer Arbeitsstation müssen die angegebenen Sicherheitsgruppen lokale Gruppen sein. Es darf sich nicht um Gruppen aus einer Domäne handeln.

Wird mindestens eine Sicherheitsgruppe angegeben, wird das virtuelle Konto nicht der lokalen Gruppe oder der Gruppe der Domänenadministratoren zugewiesen.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> Virtuellen Konten wird die Anmeldung als Dienst direkt in der Sicherheitsrichtlinie für den lokalen Server gewährt. Wenn einer angegebenen Gruppe von virtuellen Konten bereits diese Berechtigung in der Richtlinie gewährt wurde, wird das individuelle virtuelle Konto nicht mehr hinzugefügt, und es wird aus der Richtlinie entfernt. Dies kann sich beispielsweise bei Domänencontrollern als nützlich erweisen, bei denen Änderungen an der Sicherheitsrichtlinie für Domänencontroller genau überwacht werden. Dies ist nur in Windows Server 2016 mit dem Rollup vom November 2018 oder höher und Windows Server 2019 mit dem Rollup vom Januar 2019 verfügbar.

#### <a name="group-managed-service-account"></a>Gruppenverwaltetes Dienstkonto

Für Szenarios, in denen JEA-Benutzer Zugriff auf Netzwerkressourcen wie Dateifreigaben und Webdienste benötigen, eignet sich als Identität ein gruppenverwaltetes Dienstkonto (Group Managed Service Account, gMSA). Ein gMSA-Konto bietet Ihnen eine Domänenidentität zur Authentifizierung bei Ressourcen auf einem beliebigen Computer innerhalb der Domäne. Die mit einem gMSA-Konto einhergehenden Rechte werden durch die Ressourcen bestimmt, auf die Sie zugreifen. Administratorrechte für einen beliebigen Computer oder Dienste besitzen Sie nur dann, wenn der Computer- bzw. Dienstadministrator dem gMSA-Konto diese Rechte explizit erteilt hat.

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

gMSA-Konten sollten nur verwendet werden, wenn es wirklich nötig ist:

- Mit einem gMSA-Konto können Aktionen nur schwer zu einem Benutzer zurückverfolgt werden – jeder Benutzer besitzt dieselbe ausführende Identität. Sie müssen PowerShell-Sitzungsaufzeichnungen und -protokolle überprüfen, um einzelne Benutzer mit ihren Aktionen abzugleichen.

- Ein gMSA-Konto besitzt möglicherweise Zugriff auf zahlreiche Netzwerkressourcen, auf die der Benutzer, der eine Verbindung herstellt, keinen Zugriff benötigt. Versuchen Sie immer, effektive Berechtigungen in einer JEA-Sitzung zu beschränken und damit das Prinzip der geringsten Rechte anzuwenden.

> [!NOTE]
> Gruppenverwaltete Dienstkonten sind nur auf Computern unter PowerShell 5.1 oder höher verfügbar, die einer Domäne angehören.

Weitere Informationen zum Sichern einer JEA-Sitzung finden Sie im Artikel [JEA-Sicherheitsüberlegungen](security-considerations.md).

### <a name="session-transcripts"></a>Sitzungsaufzeichnungen

Es wird empfohlen, einen JEA-Endpunkt zu konfigurieren, um Aufzeichnungen von Benutzersitzungen automatisch zu erfassen. PowerShell-Sitzungsaufzeichnungen enthalten Informationen zu Benutzern, die eine Verbindung herstellen, die ihnen zugewiesene ausführende Identität und die vom Benutzer ausgeführten Befehle. Diese Informationen können für ein Überwachungsteam nützlich sein, um herauszufinden, welcher Benutzer eine bestimmte Änderung in einem System vorgenommen hat.

Geben Sie einen Pfad zu einem Ordner an, in dem die Aufzeichnungen gespeichert werden sollen, um eine automatische Protokollierung in der Sitzungskonfigurationsdatei festzulegen.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

Aufzeichnungen werden durch das **lokale Systemkonto** in den Ordner geschrieben, was Lese- und Schreibzugriff auf das Verzeichnis voraussetzt. Standardbenutzer sollten keinen Zugriff auf diesen Ordner besitzen. Beschränken Sie die Anzahl der Sicherheitsadministratoren, die zur Überwachung auf die Aufzeichnungen zugreifen können.

### <a name="user-drive"></a>Benutzerlaufwerk

Wenn Benutzer, die eine Verbindung herstellen, Dateien von einem oder auf einen JEA-Endpunkt kopieren müssen, können Sie das Benutzerlaufwerk in der Sitzungskonfigurationsdatei aktivieren. Das Benutzerlaufwerk ist ein **PSDrive**, das einem eindeutigen Ordner für jeden Benutzer zugeordnet ist, der eine Verbindung herstellt. Benutzer können über diesen Ordner Dateien vom System oder auf das System kopieren, ohne dass sie Zugriff auf das gesamte Dateisystem benötigen bzw. ohne dass der FileSystem-Anbieter verfügbar gemacht wird. Der Inhalt der Benutzerlaufwerke steht durchgehend und sitzungsübergreifend zur Verfügung, um in Situationen Abhilfe zu schaffen, in denen die Netzwerkkonnektivität unterbrochen ist.

```powershell
MountUserDrive = $true
```

Auf dem Benutzerlaufwerk können standardmäßig maximal 50 MB Daten pro Benutzer gespeichert werden. Sie können die Datenmenge, die ein Benutzer nutzen kann, mithilfe des Felds *UserDriveMaximumSize* einschränken.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Wenn die Daten auf dem Laufwerk nicht permanent zur Verfügung stehen sollen, können Sie eine geplante Aufgabe im System konfigurieren, damit der Ordner jede Nacht automatisch bereinigt wird.

> [!NOTE]
> Das Benutzerlaufwerk ist nur in PowerShell 5.1 oder höher verfügbar.

Weitere Informationen zu PSDrives finden Sie unter [Verwalten von Windows PowerShell-Laufwerken](/powershell/scripting/samples/managing-windows-powershell-drives).

### <a name="role-definitions"></a>Rollendefinitionen

Über Rollendefinitionen in einer Sitzungskonfigurationsdatei legen Sie fest, welche **Benutzer** welchen **Rollen** zugeordnet sind. Jeder Benutzer bzw. jede Gruppe in diesem Feld erhält die Berechtigung für den JEA-Endpunkt, sobald er registriert ist.
Jeder Benutzer und jede Gruppe kann jeweils nur einmal als Schlüssel in der Hashtabelle eingefügt werden, darf jedoch über mehrere Rollen verfügen. Der Name der Rollenfunktion sollte dem Namen der Rollenfunktionsdatei ohne die Erweiterung `.psrc` entsprechen.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Wenn ein Benutzer zu mehr als einer Gruppe in der Rollendefinition gehört, erhält er Zugriff auf die Rollen jeder einzelnen Gruppe. Wenn zwei Rollen Zugriff auf die gleichen Cmdlets erteilen, erhält der Benutzer den Parametersatz mit den höchsten Berechtigungen.

Wenn Sie im Rollendefinitionsfeld lokale Benutzer bzw. Gruppen angeben, verwenden Sie den Computernamen, und nicht **localhost** oder Platzhalter. Überprüfen Sie den Computernamen durch Untersuchen der Variablen `$env:COMPUTERNAME`.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Suchreihenfolge für Rollenfunktionen

Auf die Rollenfunktionen wird, wie im vorherigen Beispiel gezeigt, durch den Basisnamen der Rollenfunktionsdatei verwiesen. Der Basisname einer Datei entspricht dem Dateinamen ohne Erweiterung. Sind im System mehrere Rollenfunktionen mit demselben Namen verfügbar, verwendet PowerShell die implizite Suchreihenfolge, um die gültige Rollenfunktionsdatei auszuwählen. JEA erteilt **keinen** Zugriff auf alle Rollenfunktionsdateien mit demselben Namen.

JEA verwendet die Umgebungsvariable `$env:PSModulePath`, um zu bestimmen, welche Pfaden nach Rollenfunktionsdateien gescannt werden sollen. JEA sucht innerhalb dieser Pfade nach gültigen PowerShell-Modulen, die einen Unterordner namens „RoleCapabilities“ enthalten. Wie beim Importieren von Modulen zieht JEA Rollenfunktionen, die mit Windows ausgeliefert wurden, benutzerdefinierten Rollenfunktionen gleichen Namens vor.

Bei allen anderen Namenskonflikten wird die Rangfolge durch die Reihenfolge bestimmt, in der Windows die Dateien im Verzeichnis aufzählt. Diese Reihenfolge muss nicht unbedingt alphabetisch sein. Die erste gefundene Rollenfunktionsdatei, die mit dem angegebenen Namen übereinstimmt, wird für den Benutzer verwendet, der eine Verbindung herstellt. Da die Suchreihenfolge für die Rollenfunktionen nicht deterministisch ist, wird **dringend empfohlen**, Rollenfunktionen eindeutige Dateinamen zu geben.

### <a name="conditional-access-rules"></a>Regeln für bedingten Zugriff

Alle Benutzer und Gruppen im Feld **RoleDefinitions** erhalten automatisch Zugriff auf JEA-Endpunkte. Sie können diesen Zugriff über Regeln für bedingten Zugriff optimieren und festlegen, dass Benutzer zusätzlichen Sicherheitsgruppen angehören müssen, die keinen Einfluss auf die ihnen zugewiesenen Rollen haben. Dies ist hilfreich, wenn Sie eine Just-in-Time-Lösung für Privileged Access Management, eine Smartcard-Authentifizierung oder eine andere mehrstufige Authentifizierungslösung in JEA integrieren möchten.

Bedingte Zugriffsregeln werden im Feld „RequiredGroups“ in einer Sitzungskonfigurationsdatei definiert.
Geben Sie dazu eine (optional geschachtelte) Hashtabelle an, die zum Erstellen Ihrer Regeln die Schlüssel „And“ und „Or“ verwendet. Nachfolgend finden Sie einige Beispiele für die Verwendung dieses Felds:

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
> Regeln für bedingten Zugriff sind nur in PowerShell 5.1 oder höher verfügbar.

### <a name="other-properties"></a>Weitere Eigenschaften

Sitzungskonfigurationsdateien verfügen über die gleichen Möglichkeiten wie eine Rollenfunktionsdatei, ohne jedoch Benutzern, die eine Verbindung herstellen, Zugriff auf unterschiedliche Befehle zu geben. Wenn Sie allen Benutzern den Zugriff auf bestimmte Cmdlets, Funktionen oder Anbieter ermöglichen möchten, können Sie dies direkt in der Sitzungskonfigurationsdatei tun.
Eine vollständige Liste der unterstützten Eigenschaften in der Sitzungskonfigurationsdatei erhalten Sie, wenn Sie `Get-Help New-PSSessionConfigurationFile -Full` ausführen.

## <a name="testing-a-session-configuration-file"></a>Testen einer Sitzungskonfigurationsdatei

Sie können eine Sitzungskonfigurationsdatei über das [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile)-Cmdlet testen. Es wird empfohlen, die Sitzungskonfigurationsdatei zu testen, wenn Sie die Datei `.pssc` manuell bearbeitet haben. Dadurch wird sichergestellt, dass die Syntax korrekt ist. Besteht eine Sitzungskonfigurationsdatei diesen Test nicht, kann sie im System auch nicht registriert werden.

## <a name="sample-session-configuration-file"></a>Beispiel für eine Sitzungskonfigurationsdatei

Im folgenden Beispiel wird eine Sitzungskonfiguration für JEA erstellt und überprüft. Zur Vereinfachung und aus Gründen der Lesbarkeit werden die Rollendefinitionen in der `$roles`-Variable erstellt und gespeichert. Dies ist jedoch nicht unbedingt erforderlich.

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

Wenn Sie die Eigenschaften einer JEA-Sitzungskonfiguration einschließlich der Zuordnung von Benutzern zu Rollen ändern möchten, müssen Sie zunächst die [Registrierung aufheben](register-jea.md#unregistering-jea-configurations). Führen Sie anschließend für die JEA-Sitzungskonfiguration mit einer aktualisierten Sitzungskonfigurationsdatei eine [erneute Registrierung](register-jea.md) durch.

## <a name="next-steps"></a>Nächste Schritte

- [Registrieren einer JEA-Konfiguration](register-jea.md)
- [Erstellen von JEA-Rollen](role-capabilities.md)
