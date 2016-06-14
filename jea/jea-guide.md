# Just Enough Administration (JEA): eine Einführung

## Inhalt
Nach der Lektüre dieses Dokuments werden Sie in der Lage sein, eine JEA-Bereitstellung (Just Enough Administration) zu erstellen, bereitzustellen, zu verwenden, zu verwalten und zu überwachen.
Folgende Themen werden in diesem Einführungsleitfaden behandelt:

1.  [Einführung](#introduction): Kurze Übersicht über die Gründe, aus denen JEA für Sie interessant sein könnte

2.  [Voraussetzungen](#prerequisites): Einrichten der Umgebung

3.  [Verwenden von JEA](#using-jea): Grundlegendes zur Verwendung von JEA durch Operatoren

4.  [Neuerstellen der Demo](#remake-the-demo-endpoint): Erstellen einer JEA-Sitzungskonfiguration von Grund auf

5.  [Rollenfunktionen](#role-capabilities): Informationen zum Anpassen von JEA-Funktionen mit JEA-Rollenfunktionsdateien

6.  [End-to-End – Active Directory](#end-to-end---active-directory): Erstellen eines vollständig neuen Endpunkts zur Verwaltung von Active Directory

7.  [Bereitstellung und Wartung mehrerer Computer](#multi-machine-deployment-and-maintenance): Änderungen bei Erstellung und Bereitstellung in größerem Umfang

8.  [Berichte zu JEA](#reporting-on-jea): Überwachung und Berichterstellung für alle JEA-Aktionen und die gesamte Infrastruktur

9.  [Anhang](#appendix) Wichtige Fähigkeiten und relevante Aspekte

## Einführung

### Beweggründe
Wenn Sie einer Person privilegierten Zugriff auf Ihre Systeme gewähren, erweitern Sie Ihre Vertrauensstellungsgrenze auf diese Person.
Dies birgt Risiken – Administratoren sind eine Angriffsfläche.
Sowohl Angriffe als auch gestohlene Anmeldeinformationen sind reale und nicht seltene Gefahren.

Das ist kein neues Problem.
Sie sind sicher mit der Regel der geringsten Rechte vertraut, und Sie verwenden bestimmt eine Form der rollenbasierten Zugriffssteuerung (Role-Based Access Control, RBAC) bei Anwendungen, die diese bereitstellen.
Effektivität und Verwaltungsfreundlichkeit solcher Lösungen sind jedoch häufig durch ihren Funktionsumfang und ihre Ungenauigkeit begrenzt.
Darüber hinaus weist die rollenbasierte Zugriffssteuerung Lücken auf.
In Windows beispielsweise ist der privilegierte Zugriff im Großen und Ganzen ein binärer Schalter, sodass Sie unnötige Berechtigungen erteilen müssen, wenn Sie Benutzer zur Administratorengruppe hinzufügen.

Just Enough Administration (JEA) bietet eine RBAC-Plattform über PowerShell-Remoting.
*Damit können bestimmte Benutzer bestimmte administrative Aufgaben auf Servern ausführen, ohne dass ihnen Administratorrechte gewährt werden müssen.*
So können Sie die Lücken zwischen Ihren vorhandenen RBAC-Lösungen schließen, und die Verwaltung dieser Einstellungen wird vereinfacht.

## Voraussetzungen

### Anfangszustand
Bevor Sie mit diesem Abschnitt beginnen, stellen Sie Folgendes sicher:

1. JEA ist auf Ihrem System verfügbar. Lesen Sie die [Infodatei](./README.md), um Informationen zu den derzeit unterstützten Betriebssystemen und erforderlichen Downloads zu erhalten.
2. Sie verfügen über Administratorrechte auf dem Computer, auf dem Sie JEA ausprobieren.
3. Der Computer ist in die Domäne eingebunden.
Falls Sie noch nicht über eine Domäne verfügen, finden Sie im Abschnitt [Erstellen eines Domänencontrollers](#creating-a-domain-controller) Informationen zum schnellen Erstellen einer neuen Domäne auf einem Server.

### Aktivieren von PowerShell-Remoting
Die Verwaltung mit JEA erfolgt über PowerShell-Remoting.
Führen Sie Folgendes in einem PowerShell-Administratorfenster aus, um sicherzustellen, dass PowerShell-Remoting aktiviert und ordnungsgemäß konfiguriert ist:

```PowerShell
Enable-PSRemoting 
```

Wenn Sie mit PowerShell-Remoting noch nicht vertraut sind, empfiehlt es sich, `Get-Help about_Remote` auszuführen, um Informationen zu diesem wichtigen und grundlegenden Konzept zu erhalten.

### Identifizieren der Benutzer und Gruppen
Um JEA in Aktion zu erleben, müssen Sie die Benutzer und Gruppen ohne Administratorrechte identifizieren, die Sie in diesem Leitfaden verwenden werden.
  
Wenn Sie eine vorhandene Domäne verwenden, identifizieren oder erstellen Sie einige Benutzer und Gruppen ohne solche Rechte.
Sie werden diesen Benutzern ohne Administratorrechte Zugriff auf JEA gewähren.
Immer, wenn Sie die `$NonAdministrator`-Variable oben in einem Skript sehen, weisen Sie diese Ihren ausgewählten Benutzern oder Gruppen ohne Administratorrechte zu. 

Wenn Sie eine neue Domäne erstellt haben, ist die Aufgabe wesentlich leichter.
Verwenden Sie den Abschnitt [Benutzer und Gruppen einrichten](#set-up-users-and-groups) im Anhang, um Benutzer und Gruppen ohne Administratorrechte zu erstellen.
Die in diesem Abschnitt erstellten Gruppen weisen standardmäßig den Wert `$NonAdministrator` auf.

### Einrichten der Rollenfunktionsdatei für die Wartungsrolle
Führen Sie die folgenden Befehle in PowerShell aus, um die Rollenfunktionsdatei für die Demo zu erstellen, die Sie im nächsten Abschnitt benötigen.
Im späteren Verlauf dieses Leitfadens werden Sie erfahren, wozu diese Datei dient.

```PowerShell
# Fields in the role capability
$MaintenanceRoleCapabilityCreationParams = @{
    Author = 'Contoso Admin'
    CompanyName = 'Contoso'
    VisibleCmdlets = 'Restart-Service'
    FunctionDefinitions = 
            @{ Name = 'Get-UserInfo'; ScriptBlock = { $PSSenderInfo } }
}

# Create the demo module, which will contain the maintenance Role Capability File
New-Item -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module" -ItemType Directory
New-ModuleManifest -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\Demo_Module.psd1"
New-Item -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities" -ItemType Directory 

# Create the Role Capability file
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities\Maintenance.psrc" @MaintenanceRoleCapabilityCreationParams 
```
  
### Erstellen und Registrieren der Sitzungskonfigurationsdatei für die Demo
Führen Sie die folgenden Befehle aus, um die Sitzungskonfigurationsdatei für die Demo zu erstellen und zu registrieren, die Sie im nächsten Abschnitt benötigen.
Im späteren Verlauf dieses Leitfadens werden Sie erfahren, wozu diese Datei dient.

```PowerShell
# Determine domain
$domain = (Get-CimInstance -ClassName Win32_ComputerSystem).Domain

# Replace with your non-admin group name
$NonAdministrator = "$domain\JEA_NonAdmin_Operator"

# Specify the settings for this JEA endpoint
# Note: You will not be able to use a virtual account if you are using WMF 5.0 on Windows 7 or Windows Server 2008 R2
$JEAConfigParams = @{
    SessionType = 'RestrictedRemoteServer'
    RunAsVirtualAccount = $true
    RoleDefinitions = @{
        $NonAdministrator = @{ RoleCapabilities = 'Maintenance' }
    }
    TranscriptDirectory = "$env:ProgramData\JEAConfiguration\Transcripts"
}

# Set up a folder for the Session Configuration files
if (-not (Test-Path "$env:ProgramData\JEAConfiguration"))
{
    New-Item -Path "$env:ProgramData\JEAConfiguration" -ItemType Directory
}

# Specify the name of the JEA endpoint
$sessionName = 'JEA_Demo'

if (Get-PSSessionConfiguration -Name $sessionName -ErrorAction SilentlyContinue)
{
    Unregister-PSSessionConfiguration -Name $sessionName -ErrorAction Stop
}

New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo.pssc" @JEAConfigParams

# Register the session configuration
Register-PSSessionConfiguration -Name $sessionName -Path "$env:ProgramData\JEAConfiguration\JEADemo.pssc"
```
 
### Aktivieren der PowerShell-Modulprotokollierung (optional)
Die folgenden Schritte aktivieren die Protokollierung für alle PowerShell-Aktionen in Ihrem System.
Sie müssen die Protokollierung nicht aktivieren, damit JEA funktioniert, sie ist jedoch sehr nützlich für den Abschnitt [Berichterstellung in JEA](#reporting-on-jea).

1. Öffnen Sie den Editor für lokale Gruppenrichtlinien.
2. Navigieren Sie zu „Computerkonfiguration\Administrative Vorlagen\Windows-Komponenten\Windows-PowerShell“.
3. Doppelklicken Sie auf „Modulprotokollierung aktivieren“.
4. Klicken Sie auf „Aktiviert“.
5. Klicken Sie im Abschnitt „Optionen“ neben den Modulnamen auf „Anzeigen“.
6. Geben Sie „*“ in das Popupfenster ein. Dies bedeutet, dass PowerShell Befehle aus allen Modulen protokolliert.
7. Klicken Sie auf „OK“, und wenden Sie die Richtlinie an.

Hinweis: Sie können über eine Gruppenrichtlinie auch die systemweite PowerShell-Aufzeichnung aktivieren.

**Herzlichen Glückwunsch! Sie haben einen Demoendpunkt für Ihren Computer konfiguriert und sind jetzt bereit für den Einstieg in JEA.**

## Verwenden von JEA
In diesem Abschnitt geht es um das Endbenutzererlebnis beim *Verwenden von JEA*.
Im Abschnitt „Voraussetzungen“ haben Sie einen JEA-Demoendpunkt erstellt.
Wir verwenden diesen Demoendpunkt jetzt, um JEA in Aktion zu zeigen.
In späteren Abschnitten arbeiten wir uns sozusagen rückwärts an das Thema heran und stellen die Aktionen und Dateien vor, die dieses Endbenutzererlebnis ermöglichen.

### Verwenden von JEA als Benutzer ohne Administratorrechte
Um JEA in Aktion zu erleben, müssen Sie PowerShell-Remoting so verwenden, als wären Sie ein Benutzer ohne Administratorrechte.
Führen Sie folgenden Befehl in einem neuen PowerShell-Fenster aus:   

```PowerShell
$NonAdminCred = Get-Credential
```

Wenn Sie dazu aufgefordert werden, geben Sie die Anmeldeinformationen für Ihr Benutzerkonto ohne Administratorrechte ein.
Wenn Sie den Abschnitt [Einrichten von Benutzern und Gruppen](#set-up-users-and-groups) absolviert haben, lauten die Informationen wie folgt:
-   Benutzername = OperatorUser
-   Kennwort = pa$$w0rd

Führen Sie als Nächstes den folgenden Befehl aus, um unter Verwendung der bereitgestellten Anmeldeinformationen eine Verbindung mit dem Demoendpunkt herzustellen:

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred 
```

Sie haben jetzt eine interaktive PowerShell-Remotesitzung auf dem lokalen Computer gestartet. Durch Verwendung des Credential-Parameters haben Sie die Verbindung so hergestellt, *als wären Sie* der Benutzer „OperatorUser“ (bzw. der Benutzer, dessen Kontoinformationen Sie verwendet haben).
Die Eingabeaufforderung ändert sich zu `[localhost]: PS>`, was darauf hinweist, dass Sie in einer Remotesitzung arbeiten.  

Führen Sie folgenden Befehl an der Remoteeingabeaufforderung aus, um die Befehle anzuzeigen, die Ihnen zur Verfügung stehen:

```PowerShell
Get-Command 
```

Wie Sie sehen, steht Ihnen nur eine sehr eingeschränkte Teilmenge der Befehle eines normalen PowerShell-Fensters zur Verfügung (bei denen es sich durchaus um mehrere Tausend handeln kann).
Genau gesagt: Das Fenster zeigt nur die sieben JEA-Standardcmdlets (Clear-Host, Exit-PSSession, Get-Command, Get-FormatData, Get-Help, Measure-Object, Out-Default, Select-Object) sowie die beiden Befehle an, die explizit in der Rollenfunktionsdatei für die Wartungsrolle enthalten sind.

Sehen Sie sich jetzt den Benutzerkontext an, in dem diese Sitzung ausgeführt wird, indem Sie die benutzerdefinierte Funktion aufrufen, die in der Rollenfunktionsdatei für die Wartungsrolle enthalten ist.

```PowerShell
Get-UserInfo
```
 
Die Ausgabe dieser Funktion zeigt „ConnectedUser“ sowie „RunAsUser“.
Der verbundene Benutzer ist das Konto, über das die Verbindung mit der Remotesitzung hergestellt wurde (also z. B. Ihr Konto).
Der verbundene Benutzer benötigt keine Administratorrechte.
Das ausführende Konto ist das Konto, das tatsächlich die Aktionen ausführt, für die Berechtigungen erforderlich sind.
Durch Herstellen einer Verbindung als ein Benutzer und anschließendes Nutzen des Kontos eines anderen Benutzers, der über Administratorrechte verfügt, können Sie nicht privilegierten Benutzern erlauben, bestimmte Verwaltungsaufgaben auszuführen, ohne ihnen Administratorrechte zu erteilen.

Führen Sie den folgenden Befehl aus, um dieses Konzept in Aktion zu erleben:

```PowerShell
Restart-Service -Name Spooler -Verbose
```

Normalerweise sind für die Ausführung von Restart-Service Administratorrechte erforderlich.
Über das virtuelle JEA-Konto können Sie diesen Befehl jedoch auch mit den Anmeldeinformationen eines Benutzers ausführen, der diese Berechtigungen nicht besitzt.

Mit JEA können Sie Ihre Arbeit also mit den Befehlen erledigen, die Sie bereits verwenden.
Was aber ist mit Befehlen, deren Ausführung *nicht* erlaubt sein sollte?
Versuchen Sie, einen anderen Befehl in der JEA-Sitzung auszuführen – z. B. `Restart-Computer` –, und sehen Sie selbst, wie JEA die Ausführung solcher Befehle verhindert.

```PowerShell
[localhost]: PS> Restart-Computer
The term 'Restart-Computer' is not recognized as the name of a cmdlet, function, script file, or
operable program. Check the spelling of the name, or if a path was included, verify that the path
is correct and try again.
    + CategoryInfo          : ObjectNotFound: (Restart-Computer:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException 
```

Um den eingeschränkten JEA-Endpunkt zu verlassen, führen Sie folgenden Befehl aus:

```PowerShell
Exit-PSSession
```

Dadurch wird die Verbindung mit der PowerShell-Remotesitzung getrennt.

## Neuerstellen der Demoendpunkts
In diesem Abschnitt erfahren Sie, wie Sie ein exaktes Replikat des Demoendpunkts erstellen, das Sie im vorherigen Abschnitt verwendet haben.
Hierbei werden wichtige Konzepte vorgestellt, die für ein genaues Verständnis von JEA notwendig sind, einschließlich der PowerShell-Sitzungskonfigurationen und -Rollenfunktionen. 

### PowerShell-Sitzungskonfigurationen
Bei der Verwendung von JEA im vorherigen Abschnitt bestand der erste Schritt darin, den folgenden Befehl auszuführen:

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

Die meisten Parameter sind selbsterklärend, der Parameter *ConfigurationName* kann jedoch auf den ersten Blick verwirrend sein.
Dieser Parameter gab die PowerShell-Sitzungskonfiguration an, mit der Sie eine Verbindung hergestellt haben. 

*PowerShell-Sitzungskonfiguration* ist im Grunde nur eine andere, schickere Bezeichnung für einen PowerShell-Endpunkt.
Es ist im übertragenen Sinn der „Ort“, an dem Benutzer eine Verbindung herstellen und Zugriff auf PowerShell-Funktionen erhalten.
Je nachdem, wie Sie eine Sitzungskonfiguration einrichten, können Sie unterschiedliche Funktionen für die Benutzer bereitstellen, die eine Verbindung herstellen.
Bei JEA werden Sitzungskonfigurationen verwendet, um die in PowerShell verfügbaren Funktionen einzuschränken und eine Ausführung als privilegiertes virtuelles Konto zu ermöglichen.

Sie verfügen bereits über einige registrierte PowerShell-Sitzungskonfigurationen auf Ihrem Computer, die jeweils leicht unterschiedlich eingerichtet sind.
Die meisten Konfigurationen sind im Lieferumfang von Windows enthalten, die Sitzungskonfiguration „JEA_Demo“ wurde jedoch im Abschnitt [Voraussetzungen](#prerequisites) eingerichtet.
Sie können alle registrierten Sitzungskonfigurationen anzeigen, indem Sie folgenden Befehl an einer PowerShell-Administratoreingabeaufforderung ausführen:

```PowerShell
Get-PSSessionConfiguration
```

### PowerShell-Sitzungskonfigurationsdateien
Sie können neuen Sitzungskonfigurationen erstellen, indem Sie neue *PowerShell-Sitzungskonfigurationsdateien* registrieren.
Sitzungskonfigurationsdateien weisen die Dateierweiterung PSSC auf.
Sie können Sitzungskonfigurationsdateien mit dem Cmdlet New-PSSessionConfigurationFile generieren.

Als Nächstes werden Sie eine neue Sitzungskonfiguration für JEA erstellen und registrieren. 

### Generieren und Ändern der PowerShell-Sitzungskonfiguration
Führen Sie folgenden Befehl aus, um eine Gerüstdatei („Skeleton“) für eine PowerShell-Sitzungskonfiguration zu generieren.

```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

> **TIPP**: Standardmäßig sind nur die häufigsten Konfigurationseinstellungen in der Gerüstdatei vorhanden.
> Verwenden Sie den `-Full`-Parameter, um alle anwendbaren Einstellungen in die generierte PSSC-Datei einzuschließen.

Öffnen Sie die Datei in der PowerShell ISE oder einem Text-Editor Ihrer Wahl.

```PowerShell
ise "$env:ProgramData\JEAConfiguration\JEADemo2.pssc" 
```

Aktualisieren Sie die folgenden Felder mit den unten stehenden Werten (denken Sie daran, Ihre eigene Sicherheitsgruppe ohne Administratorrechte einzusetzen): 

```PowerShell
# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: # RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{'CONTOSO\JEA_NonAdmin_Operator' = @{ RoleCapabilities =  'Maintenance' }}
```

Die Einträge haben folgende Bedeutung:

1.  Das Feld *SessionType* definiert vorab eingerichtete Standardeinstellungen, die für diesen Endpunkt verwendet werden sollen.
*RestrictedRemoteServer* definiert die Mindesteinstellungen, die für die Remoteverwaltung erforderlich sind. Standardmäßig macht ein *RestrictedRemoteServer*-Endpunkt die Befehle Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clea-Host, und Out-Default verfügbar.
Die Einstellung *ExecutionPolicy* wird auf *RemoteSigned* und die Einstellung *LanguageMode* auf *NoLanguage* festgelegt.
Das Ergebnis dieser Einstellungen ist ein sicherer und einfacher Startpunkt zum Konfigurieren des Endpunkts.

2.  Das Feld *RoleDefinitions* weist bestimmten Gruppen Rollenfunktionen zu.
Es definiert, welcher Benutzer mit einem privilegierten Konto welche Aufgaben ausführen darf.
Mit diesem Feld können Sie basierend auf der Gruppenmitgliedschaft die Funktionen angeben, die für einen verbundenen Benutzer zur Verfügung stehen.
Dies ist das Kernstück der RBAC-Funktionalität von JEA.
In diesem Beispiel machen Sie die vorab erstellte Rollenfunktion „Demo“ für Mitglieder der Gruppe „Contoso\JEA_NonAdmin_Operator“ verfügbar.

3.  Das Feld *RunAsVirtualAccount* gibt an, dass PowerShell auf diesem Endpunkt mit einem ausführenden virtuellen Konto ausgeführt werden soll.
Standardmäßig ist das virtuelle Konto Mitglied der integrierten Administratorengruppe.
Auf einem Domänencontroller ist es standardmäßig auch Mitglied der Domänenadministratorengruppe.
Im weiteren Verlauf dieses Leitfadens erfahren Sie, wie Sie die Berechtigungen des virtuellen Kontos anpassen.

4.  Das Feld *TranscriptDirectory* definiert, wo mitgeschnittene PowerShell-Aufzeichnungen nach jeder Remotesitzung gespeichert werden.
Diese Aufzeichnungen bieten eine gut lesbare Möglichkeit, die Aktionen zu überprüfen, die in jeder Sitzung ausgeführt wurden.
Weitere Informationen über PowerShell-Aufzeichnungen finden Sie in diesem [Blogbeitrag](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).
Hinweis: Die reguläre Windows-Ereignisverwaltung erfasst ebenfalls Informationen darüber, welche Befehle von den einzelnen Benutzern mit PowerShell ausgeführt wurden.
PowerShell-Aufzeichnungen sind allerdings besser lesbar.

Speichern Sie Ihre Änderungen abschließend in *JEADemo2.pssc*.

### Anwenden der PowerShell-Sitzungskonfiguration 

Um aus einer Sitzungskonfigurationsdatei einen Endpunkt zu erstellen, müssen Sie die Datei registrieren.
Dafür sind einige Informationen erforderlich:

1. Der Pfad zur Sitzungskonfigurationsdatei.
2. Der Name Ihrer registrierten Sitzungskonfiguration. Dies ist der gleiche Name, den Benutzer im ConfigurationName-Parameter angeben, wenn sie mithilfe von `Enter-PSSession` oder `New-PSSession` eine Verbindung mit Ihrem Endpunkt herstellen.

Um die Sitzungskonfiguration auf Ihrem lokalen Computer zu registrieren, führen Sie folgenden Befehl aus:

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

Herzlichen Glückwunsch! Sie haben Ihren JEA-Endpunkt eingerichtet.

### Testen Ihres Endpunkts
Führen Sie die Schritte im Abschnitt [Verwenden von JEA](#using-jea) erneut für Ihren neuen Endpunkt aus, um zu überprüfen, ob er erwartungsgemäß ausgeführt wird.
Stellen Sie sicher, dass Sie einen neuen Endpunktnamen verwenden (JEADemo2), wenn Sie den Konfigurationsnamen in Enter-PSSession bereitstellen.

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

### Wichtige Konzepte
**PowerShell Session-Sitzungskonfiguration**: Wird auch als *PowerShell-Endpunkt* bezeichnet und ist im übertragenen Sinn der „Ort“, an dem Benutzer eine Verbindung herstellen und Zugriff auf PowerShell-Funktionen erhalten.
Sie können die in Ihrem System registrierten Sitzungskonfigurationen durch Ausführen von `Get-PSSessionConfiguration` auflisten.
Wenn eine PowerShell-Sitzungskonfiguration auf bestimmte Weise konfiguriert ist, kann sie auch als *JEA-Endpunkt* bezeichnet werden.

**PowerShell-Sitzungskonfigurationsdatei (PSSC)**: Eine Datei, die nach der Registrierung Einstellungen für eine PowerShell-Sitzungskonfiguration definiert.
Sie enthält Spezifikationen für Benutzerrollen, die eine Verbindung mit dem Endpunkt herstellen können, das ausführende virtuelle Konto sowie weitere Details.     

**RoleDefinitions**: Das Feld in einer Sitzungskonfigurationsdatei, das die Rollenfunktionen definiert, die verbundene Benutzer ausführen können.
Es definiert, *welcher Benutzer* mit einem privilegierten Konto *welche Aufgaben* ausführen darf.
Dies ist das Kernstück der RBAC-Funktionalität von JEA.

**SessionType**: Ein Feld in einer Sitzungskonfigurationsdatei, das Standardeinstellungen für eine Sitzungskonfiguration darstellt.
Bei JEA-Endpunkten muss dieses Feld auf RestrictedRemoteServer festgelegt sein.

**PowerShell-Aufzeichnung**: Eine Datei mit einem Mitschnitt einer PowerShell-Sitzung.
Sie können PowerShell mithilfe des Felds TranscriptDirectory so einrichten, dass Aufzeichnungen von JEA-Sitzungen generiert werden.
Weitere Informationen über Aufzeichnungen finden Sie in diesem [Blogbeitrag](https://technet.microsoft.com/en-us/magazine/ff687007.aspx).

## Rollenfunktionen

### Übersicht
Im vorherigen Abschnitt haben Sie erfahren, dass das Feld RoleDefinitions definiert, welche Gruppen Zugriff auf bestimmte Rollenfunktionen haben.
Möglicherweise haben Sie sich gefragt, was denn Rollenfunktionen sind.
Diese Frage wird im vorliegenden Abschnitt beantwortet.  

## Einführung in PowerShell-Rollenfunktionen
PowerShell-Rollenfunktionen definieren die Aufgaben, die ein Benutzer auf einem JEA-Endpunkt ausführen darf.
Sie stellen eine Whitelist mit sichtbaren Befehlen und Anwendungen sowie weiteren nutzbaren Elementen bereit.
Rollenfunktionen werden durch Dateien mit der Erweiterung PSRC definiert.

## Inhalte von Rollenfunktionen
Zunächst untersuchen und bearbeiten wir die Datei mit den Demorollenfunktionen, die Sie bereits verwendet haben.
Stellen Sie sich folgende Situation vor: Sie haben Ihre Sitzungskonfiguration in der gesamten Umgebung bereitgestellt und erhalten jetzt Feedback, dass Sie die Funktionen ändern müssen, die Benutzern verfügbar gemacht werden.
Operatoren müssen Computer neu starten können und sie möchten auch in der Lage sein, Informationen zu Netzwerkeinstellungen abzurufen.
Darüber hinaus hat das Sicherheitsteam Sie darüber informiert, dass es nicht akzeptabel ist, Benutzern die uneingeschränkte Ausführung von Restart-Service zu ermöglichen.
Sie müssen die Dienste einschränken, die von Operatoren neu gestartet werden dürfen.

Um diese Änderungen durchzuführen, führen Sie die PowerShell ISE als Administrator aus, und öffnen Sie die folgende Datei:

```
C:\Program Files\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities\Maintenance.psrc
```

Suchen Sie die folgenden Zeilen in der Datei, und aktualisieren Sie sie: 

```PowerShell
# OLD: VisibleCmdlets = 'Restart-Service'
VisibleCmdlets = 'Restart-Computer',
                 @{
                     Name = 'Restart-Service'
                     Parameters = @{ Name = 'Name'; ValidateSet = 'Spooler' }
                 },
                 'NetTCPIP\Get-*'

# OLD: VisibleExternalCommands = 'Item1', 'Item2'
VisibleExternalCommands = 'C:\Windows\system32\ipconfig.exe'
```

Dies enthält einige interessante Beispiele:

1.  Sie haben Restart-Service eingeschränkt, sodass Operatoren Restart-Service nur mit dem Parameter „-Name“ verwenden und als Argument für diesen Parameter nur „Spooler“ bereitstellen dürfen.
Wenn gewünscht, können Sie mithilfe eines regulären Ausdrucks unter Verwendung von ValidatePattern anstelle von ValidateSet auch die Argumente einschränken.

2.  Sie haben alle Befehle mit dem Verb „Get“ aus dem NetTCPIP-Modul verfügbar gemacht.
Da Get-Befehle üblicherweise den Systemstatus nicht ändern, ist dies ein relativ sicheres Vorgehen.
Nichtsdestoweniger sollten Sie jeden Befehl, den Sie über JEA verfügbar machen, sehr sorgfältig überprüfen.

3.  Sie haben mithilfe von VisibleExternalCommands eine ausführbare Datei (IPCONFIG) verfügbar gemacht.
Mit diesem Feld können Sie auch vollständige PowerShell-Skripts verfügbar machen.
Es ist wichtig, immer den vollständigen Pfad zu externen Pfaden bereitzustellen, um sicherzustellen, dass nicht versehentlich ein (möglicherweise schädliches) Programm mit ähnlichem Namen ausgeführt wird, das sich im Benutzerpfad befindet.

Speichern Sie die Datei, und stellen Sie dann erneut eine Verbindung mit dem Demoendpunkt her, um zu bestätigen, dass die Änderungen funktioniert haben.

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
Get-Command
```
Da Sie nur die Rollenfunktionsdatei geändert haben, müssen Sie die Sitzungskonfiguration nicht erneut registrieren.
PowerShell findet automatisch die aktualisierten Rollenfunktionen, wenn ein Benutzer eine Verbindung herstellt.
Da Rollenfunktionen beim Start der Sitzung geladen werden, sind vorhandene Sitzungen von Aktualisierungen der Rollenfunktionsdateien nicht betroffen.

Bestätigen Sie jetzt, dass Sie den Computer neu starten können, indem Sie Restart-Computer mit dem Parameter „-WhatIf“ ausführen (es sei denn, Sie möchten den Computer tatsächlich neu starten).

```PowerShell
Restart-Computer -WhatIf 
```

Bestätigen, dass Sie „ipconfig“ ausführen können.

```PowerShell
ipconfig
```

Zum Schluss bestätigen Sie, dass Restart-Service nur für den Spoolerdienst funktioniert.

```PowerShell
Restart-Service Spooler # This should work
Restart-Service WSearch # This should fail 
```

Beenden Sie die Sitzung, wenn Sie fertig sind.

```PowerShell
Exit-PSSession 
```

### Erstellen von Rollenfunktionen
Im nächsten Abschnitt erstellen Sie einen JEA-Endpunkt für AD-Helpdeskbenutzer.
Zur Vorbereitung erstellen Sie zunächst eine leere Rollenfunktionsdatei, die in diesem Abschnitt ausgefüllt werden soll.
Rollenfunktionen müssen in einem gültigen PowerShell-Modul innerhalb eines Ordners namens „RoleCapabilities“ erstellt werden, damit sie beim Start einer Sitzung aufgelöst werden können.

Bei PowerShell-Modulen handelt es sich im Wesentlichen um Pakete mit PowerShell-Funktionalitäten.
Sie können PowerShell-Funktionen, -Cmdlets, -DSC-Ressourcen, -Rollenfunktionen und vieles mehr enthalten.
Sie können Informationen zu Modulen erhalten, indem Sie `Get-Help about_Modules` in einer PowerShell-Konsole ausführen.

Um ein neues PowerShell-Modul mit einer leeren Rollenfunktionsdatei zu erstellen, führen Sie folgende Befehle aus:  

```PowerShell
# Create a new folder for the module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module' -ItemType Directory

# Add a module manifest to contain metadata for this module.
New-ModuleManifest -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psd1' -RootModule Contoso_AD_Module.psm1

# Create a blank script module. You'll use this for custom functions in the next section.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1' -ItemType File 

# Create a RoleCapabilities folder in the AD_Module folder. PowerShell expects Role Capabilities to be located in a "RoleCapabilities" folder within a module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities' -ItemType Directory

# Create a blank Role Capability in your RoleCapabilities folder. Running this command without any additional parameters just creates a blank template.
New-PSRoleCapabilityFile -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc' 
```

Herzlichen Glückwunsch! Sie haben eine leere Rollenfunktionsdatei erstellt.
Diese Datei wird im nächsten Abschnitt verwendet.

### Wichtige Konzepte
**Rollenfunktionen (PSRC)**: Eine Datei, die die Aufgaben definiert, die ein Benutzer auf einem JEA-Endpunkt ausführen darf.
Sie stellt eine Whitelist mit sichtbaren Befehlen und Konsolenanwendungen sowie weiteren nutzbaren Elementen bereit.
Damit PowerShell die Rollenfunktionen erkennen kann, müssen Sie diese in einem gültigen PowerShell-Modul im Ordner „RoleCapabilities“ speichern.

**PowerShell-Modul**: Ein Paket mit PowerShell-Funktionalität.
Es kann PowerShell-Funktionen, -Cmdlets, -DSC-Ressourcen, -Rollenfunktionen und vieles mehr enthalten.
PowerShell-Module müssen in einem Pfad in `$env:PSModulePath` gespeichert werden, damit sie automatisch geladen werden können. 

## End-to-End – Active Directory
Angenommen, der Umfang Ihres Programms hat sich erhöht.
Sie sollen jetzt JEA zu Domänencontrollern hinzufügen, damit Active Directory-Aktionen ausgeführt werden können.
Die Helpdeskmitarbeiter werden JEA verwenden, um Konten zu entsperren, Kennwörter zurückzusetzen und ähnliche Aktionen auszuführen.

Sie müssen einer anderen Gruppe von Benutzern einen vollkommen neuen Satz an Befehlen verfügbar machen.
Außerdem müssen Sie eine Vielzahl von vorhandenen Active Directory-Skripts verfügbar machen.
Dieser Abschnitt leitet Sie durch die Erstellung einer Sitzungskonfiguration sowie einer Rollenfunktion für diese Aufgabe.

### Voraussetzungen
Um diesen Abschnitt schrittweise durchzugehen, müssen Sie auf einem Domänencontroller arbeiten.
Machen Sie sich keine Sorgen, wenn Sie keinen Zugriff auf Ihren Domänencontroller haben.
Folgen Sie den Anweisungen einfach mit einem anderen Szenario oder einer anderen Rolle, mit der Sie vertraut sind.
Wenn Sie schnell einen neuen Domänencontroller einrichten möchten, finden Sie die notwendigen Informationen im Anhang unter [Erstellen eines Domänencontrollers](#creating-a-domain-controller).

### Schritte zum Erstellen einer neuen Rollenfunktion und Sitzungskonfiguration

Das Erstellen einer neuen Rollenfunktion kann auf den ersten Blick eine große Herausforderung sein. Die Aufgabe lässt sich jedoch in relativ einfache Schritte unterteilen:

1.  Ermitteln Sie die Aufgaben, die Sie aktivieren müssen.
2.  Schränken Sie diese Aufgaben nach Bedarf ein.
3.  Stellen Sie sicher, dass die Aufgaben mit JEA funktionieren.
4.  Speichern Sie sie in einer Rollenfunktionsdatei.
5.  Registrieren Sie eine Sitzungskonfiguration, die diese Rollenfunktion verfügbar macht.

### Schritt 1: Ermitteln Sie die Aktionen und Aufgaben, die verfügbar gemacht werden müssen.
Bevor Sie eine neue Rollenfunktion oder Sitzungskonfiguration erstellen können, müssen Sie alle Aktionen und Aufgaben identifizieren, die Benutzer über den JEA-Endpunkt ausführen können müssen. Sie müssen ebenfalls ermitteln, wie diese Aktionen und Aufgaben in PowerShell ausgeführt werden.
Dieser Schritt erfordert sehr viel Recherche und die Erfassung von Anforderungen.
Die Art und Weise, wie Sie diesen Prozess durchführen, richtet sich nach Ihrer Organisation und Ihren Zielen.
Die Erfassung von Anforderungen und die Recherche sind in der Praxis ein entscheidender Bestandteil des Prozesses.
Dies ist möglicherweise der schwierigste Schritt im gesamten Prozess der Einrichtung von JEA.

#### Suchen nach Ressourcen
Folgende Onlineressourcen bieten nützliche Informationen zum Erstellen eines Active Directory-Verwaltungsendpunkts:
-   [Active Directory PowerShell Overview](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx) 
-   [CMD to PowerShell Guide for Active Directory](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx)

#### Erstellen einer Liste
Mit den zehn folgenden Aktionen werden Sie im Rest dieses Abschnitts arbeiten.
Denken Sie daran, dass es sich hier nur um ein Beispiel handelt und Ihre Organisation höchstwahrscheinlich andere Anforderungen stellt:

|Aktion                                                         |PowerShell-Befehl                                             |
|---------------------------------------------------------------|---------------------------------------------------------------|
|Konto entsperren                                                 |`Unlock-ADAccount`                                             |
|Kennwort zurücksetzen                                                 |`Set-ADAccountPassword` und `Set-ADUser -ChangePasswordAtLogon`|
|Position eines Benutzers ändern                                          |`Set-ADUser -Title`                                            |  
|AD-Konten finden, die gesperrt oder deaktiviert wurden oder inaktiv sind usw. |`Search-ADAccount`                                             | 
|Benutzer zu Gruppe hinzufügen                                              |`Add-ADGroupMember -Identity (with whitelist) -Members`        | 
|Benutzer aus Gruppe entfernen                                         |`Remove-ADGroupMember -Identity (with whitelist) -Members`     | 
|Benutzerkonto aktivieren                                          |`Enable-ADAccount`                                             |
|Benutzerkonto deaktivieren                                         |`Disable-ADAccount`                                            |

### Schritt 2: Schränken Sie die Aufgaben nach Bedarf ein.

Nachdem Sie jetzt über die Liste der notwendigen Aktionen verfügen, müssen Sie die Funktion jedes einzelnen Befehls gründlich durchdenken.
Dafür gibt es zwei wichtige Gründe:

1.  Es kann leicht passieren, dass Sie Benutzern mehr Funktionen verfügbar machen als Sie wollten.
`Set-ADUser` z. B. ist ein unglaublich leistungsfähiger und flexibler Befehl.
Sie möchten sicher nicht die gesamte Funktionalität dieses Befehls für Helpdeskbenutzer verfügbar machen.  

2.  Schlimmer noch: Es kann passieren, dass Sie Befehle verfügbar machen, die es Benutzern ermöglichen, die Beschränkungen von JEA zu umgehen.
In diesem Fall kann JEA nicht mehr als Sicherheitsmechanismus fungieren.
Gehen Sie daher beim Auswählen von Befehlen mit größter Umsicht vor.
Invoke-Expression ermöglicht Benutzern beispielsweise die Ausführung von uneingeschränktem Code.
Weitere Informationen zu diesem Thema finden Sie im Abschnitt „Überlegungen zum Einschränken von Befehlen“.

Nachdem Sie jeden Befehl sorgfältig geprüft haben, entscheiden Sie sich für folgende Einschränkungen:

1.  `Set-ADUser` soll nur mit dem Parameter „-Title“ ausgeführt werden dürfen. 

2.  `Add-ADGroupMember` und `Remove-ADGroupMember` sollen nur für bestimmte Gruppen funktionieren

### Schritt 3: Bestätigen Sie, dass die Aufgaben mit JEA funktionieren.
Die Verwendung dieser Cmdlets ist in der eingeschränkten JEA-Umgebung möglicherweise nicht ganz einfach.
JEA wird im Modus *NoLanguage* ausgeführt, der unter anderem verhindert, dass Benutzer Variablen verwenden dürfen.
Um die Benutzerfreundlichkeit sicherzustellen, müssen Sie einige Dinge prüfen.

Sehen Sie sich z. B. `Set-ADAccountPassword` an.
Der Parameter „-NewPassword“ erfordert eine sichere Zeichenfolge.
Benutzer erstellen häufig eine sichere Zeichenfolge und übergeben sie als Variable, wie hier zu sehen:

```PowerShell
$newPassword = (Read-Host -Prompt "Specify a new password" -AsSecureString)
Set-ADAccountPassword -Identity mollyd -NewPassword $newPassword -Reset
```

Der Modus „NoLanguage“ verhindert jedoch die Verwendung von Variablen.
Es gibt zwei Möglichkeiten, diese Einschränkung zu umgehen:

1.  Sie können festlegen, dass Benutzer den Befehl ohne Variablenzuweisung ausführen.
Dies lässt sich einfach konfigurieren, kann jedoch für die Operatoren, die den Endpunkt verwenden, äußerst mühsam sein.
Wer möchte denn beim Zurücksetzen eines Kennworts jedes Mal die sichere Zeichenfolge eingeben?
```PowerShell
Set-ADAccountPassword -Identity mollyd -NewPassword (Read-Host -Prompt "Specify a new password" -AsSecureString) -Reset
```

2.  Sie können die Komplexität in einem Skript oder einer Funktion verpacken, das bzw. die Sie für die Endbenutzer verfügbar machen.
Skripts und Funktionen, die Sie verfügbar machen, werden in einem uneingeschränkten Kontext ausgeführt. Sie können völlig problemlos Funktionen schreiben, die Variablen verwenden und andere Befehle aufrufen.
Diese Vorgehensweise verbessert die Benutzerfreundlichkeit, verhindert Fehler, erfordert weniger PowerShell-Kenntnisse und senkt das Risiko, dass versehentlich zu viel Funktionalität verfügbar gemacht wird.
Der einzige Nachteil ist der Aufwand für die Erstellung und Verwaltung der Funktion.

#### Exkurs: Hinzufügen einer Funktion zu Ihrem Modul
Mithilfe von Vorgehensweise Nr. 2 werden Sie eine PowerShell-Funktion namens `Reset-ContosoUserPassword` schreiben.
Diese Funktion führt alle Aktionen aus, die erforderlich sind, wenn Sie das Kennwort eines Benutzers zurücksetzen.
In Ihrer Organisation gehören dazu möglicherweise hochkomplexe Prozesse.
Da es sich hier nur um ein Beispiel handelt, setzt Ihr Befehl einfach nur das Kennwort zurück und fordert den Benutzer bei der Anmeldung zur Änderung des Kennworts auf.
Wir speichern den Befehl in dem Modul „Contoso_AD_Module“, das Sie im letzten Abschnitt erstellt haben.

1. Öffnen Sie in der PowerShell ISE die Datei „Contoso_AD_Module.psm1“.
```PowerShell
ISE 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1' 
```

2. Drücken Sie STRG+J, um das Menü für Codeausschnitte zu öffnen.

3. Suchen Sie nach „function“, und drücken Sie die EINGABETASTE.
Dadurch erhalten Sie ein simples Grundgerüst einer Funktion.

4. Benennen Sie die Funktion in „Reset-ContosoUserPassword“ um.  

5. Benennen Sie den einen Parameter in „Identity“ um, und löschen Sie den zweiten.

6. Kopieren Sie Folgendes in den Hauptteil der Funktion.
```PowerShell
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
```

7. Speichern Sie die Datei.
Das Resultat sollte in etwa folgendermaßen aussehen:
```PowerShell
function Reset-ContosoUserPassword ($Identity)
{
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
} 
```
Jetzt können Ihre Benutzer einfach `Reset-ContosoUserPassword` aufrufen und müssen sich nicht die Syntax merken, um inline eine sichere Zeichenfolge zu erstellen.

### Schritt 4: Bearbeiten Sie die Rollenfunktionsdatei.
Im Abschnitt [Erstellen einer Rollenfunktion](#role-capability-creation) haben Sie eine leere Rollenfunktionsdatei erstellt.
In diesem Abschnitt werden Sie diese Datei mit Werten füllen.

Öffnen Sie zunächst die Rollenfunktionsdatei in der ISE.
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc' 
```
Aktualisieren Sie die Datei mit folgenden Änderungen:
```PowerShell
# OLD: VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleCmdlets =
    'Unlock-ADAccount',
    'Search-ADAccount',
    'Enable-ADAccount',
    'Disable-ADAccount',
    @{ Name = 'Set-ADUser'; Parameters = @{ Name = 'Title'; ValidateSet = 'Manager', 'Engineer' }},
    @{ Name = 'Add-ADGroupMember'; Parameters = 
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}},
    @{ Name = 'Remove-ADGroupMember'; Parameters = 
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}}
  
# OLD: VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }   
VisibleFunctions = 'Reset-ContosoUserPassword'
```

In obigem Beispiel gilt es einiges zu beachten:
1.  PowerShell versucht, die Module automatisch zu laden, die für Ihre Rollenfunktion benötigt werden.
Möglicherweise müssen Sie Modulnamen explizit im Feld „ModulesToImport“ auflisten, wenn Sie feststellen, dass ein Modul nicht automatisch geladen wird.

2.  Wenn Sie nicht sicher sind, ob es sich bei einem Befehl um ein Cmdlet oder eine Funktion handelt, führen Sie `Get-Command` aus, und sehen Sie sich den Wert für „CommandType“ an.

3.  Das ValidatePattern-Element ermöglicht die Verwendung eines regulären Ausdrucks, um Parameterargumente einzuschränken, falls zulässige Werte nicht einfach zu definieren sind.
Sie können für einen einzigen Parameter nicht sowohl ValidatePattern als auch ValidateSet definieren.

### Schritt 5: Erstellen und registrieren Sie eine neue Sitzungskonfiguration.
Als Nächstes erstellen Sie eine neue Sitzungskonfigurationsdatei, die Ihre Rollenfunktion für Mitglieder der AD-Gruppe „JEA_NonAdmin_HelpDesk“ verfügbar macht. 

Erstellen und öffnen Sie zunächst eine neue leere Sitzungskonfigurationsdatei in der PowerShell ISE.
```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc" 
ise "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
Ändern Sie die folgenden Felder in der PSSC-Datei.
Wenn Sie in Ihrer eigenen Umgebung arbeiten, sollten Sie „CONTOSO\JEA_NonAdmins_Helpdesk“ durch Ihre eigene Gruppe ohne Administratorrechte ersetzen.
```PowerShell
# OLD: Description = ''
Description = 'An endpoint for active directory tasks.' 

# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{ 'CONTOSO\JEA_NonAdmin_HelpDesk' = @{ RoleCapabilities =  'ADHelpDesk' }} 
```
Speichern und registrieren Sie die Sitzungskonfiguration.
```PowerShell
Register-PSSessionConfiguration -Name ADHelpDesk -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc" 
```
### Probieren Sie es aus!
Rufen Sie Ihre Benutzeranmeldeinformationen ohne Administratorrechte ab:
```PowerShell
$HelpDeskCred = Get-Credential
```
Wenn Sie den Abschnitt „Einrichten von Benutzern und Gruppen“ absolviert haben, lauten die Informationen wie folgt:
-   Benutzername = HelpDeskUser
-   Kennwort = pa$$w0rd

Stellen Sie eine Remoteverbindung mit dem AD-Helpdeskendpunkt her, und verwenden Sie dabei diese Anmeldeinformationen ohne Administratorrechte:
```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName ADHelpDesk -Credential $HelpDeskCred 
```
Verwenden Sie Set-ADUser, um die Position eines Benutzers zurückzusetzen.
```PowerShell
Set-ADUser -Identity OperatorUser -Title Engineer 
```
Überprüfen Sie, ob die Position geändert wurde.
```PowerShell
Get-ADUser -Identity OperatorUser -Property Title 
```
Verwenden Sie jetzt Add-ADGroupMember, um einen Benutzer zur Gruppe TestGroup hinzuzufügen.
Hinweis: Stellen Sie sicher, dass Sie die Gruppe TestGroup zuvor erstellt haben.
```PowerShell
Add-ADGroupMember TestGroup -Member OperatorUser -Verbose 
```
Beenden Sie die Sitzung:
```PowerShell
Exit-PSSession
```
### Wichtige Konzepte
**NoLanguage-Modus**: Wenn PowerShell sich im Modus „NoLanguage“ befindet, dürfen Benutzer nur Befehle ausführen und keine Sprachelemente verwenden.
Wenn Sie hierzu weitere Informationen benötigen, führen Sie `Get-Help about_Language_Modes` aus.

**PowerShell-Funktionen**: Bei PowerShell-Funktionen handelt es sich um PowerShell-Codeabschnitte, denen Sie einen Namen zuweisen können.
Wenn Sie hierzu weitere Informationen benötigen, führen Sie `Get-Help about_Functions` aus.

**ValidateSet/ValidatePattern**: Wenn Sie einen Befehl verfügbar machen, können Sie die gültigen Argumente für bestimmte Parameter einschränken.
Ein ValidateSet-Element ist eine spezifische Liste gültiger Befehle.
Ein ValidatePattern-Element ist ein regulärer Ausdruck, mit dem die Argumente für diesen Parameter übereinstimmen müssen.

## Bereitstellung und Wartung mehrerer Computer
Bisher haben Sie JEA mehrmals auf lokalen Systemen bereitgestellt.
Da Ihre Produktionsumgebung aller Wahrscheinlichkeit nach aus mehr als einen Computer besteht, müssen Sie die wichtigen Schritte im Bereitstellungsprozesses kennen, die auf jedem Computer ausgeführt werden müssen.

### Allgemeine Schritte:
1.  Kopieren Sie Ihre Module (mit Rollenfunktionen) auf jeden Knoten.
2.  Kopieren Sie Ihre Sitzungskonfigurationsdateien auf jeden Knoten.
3.  Führen Sie `Register-PSSessionConfiguration` mit Ihrer Sitzungskonfiguration aus.
4.  Speichern Sie eine Kopie Ihrer Sitzungskonfiguration und Toolkits an einem sicheren Ort.
Wenn Sie Änderungen vornehmen, ist es gut, über eine „sichere Informationsquelle“ zu verfügen.

### Beispielskript
Hier sehen Sie ein Beispielskript für die Bereitstellung.
Um dieses Skript in Ihrer Umgebung zu verwenden, müssen Sie die Namen/Pfade echter Dateifreigaben und Module angeben.
```PowerShell
# First, copy the session configuration and modules (containing role capability files) onto a file share you have access to.
Copy-Item -Path 'C:\Demo\Demo.pssc' -Destination '\\FileShare\JEA\Demo.pssc'
Copy-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\SomeModule\' -Recurse -Destination '\\FileShare\JEA\SomeModule'

# Next, author a setup script (C:\JEA\Deploy.ps1) to run on each individual node
    # Contents of C:\JEA\Deploy.ps1
    New-Item -ItemType Directory -Path C:\JEADeploy
    Copy-Item -Path '\\FileShare\JEA\Demo.pssc' -Destination 'C:\JEADeploy\'
    Copy-Item -Path '\\FileShare\JEA\SomeModule' -Recurse -Destination 'C:\Program Files\WindowsPowerShell\Modules' # Remember, Role Capability Files are found in modules
    if (Get-PSSessionConfiguration -Name JEADemo -ErrorAction SilentlyContinue)
    {
        Unregister-PSSessionConfiguration -Name JEADemo -ErrorAction Stop
    }

    Register-PSSessionConfiguration -Name JEADemo -Path 'C:\JEADeploy\Demo.pssc'
    Remove-Item -Path 'C:\JEADeploy' # Don't forget to clean up!

# Now, invoke the script on all of the target machines.
# Note: this requires PowerShell Remoting be enabled on each machine. Enabling PowerShell remoting is a requirement to use JEA as well.
# You may need to provide the "-Credential" parameter if your current user account does not have admin permissions on these machines.
Invoke-Command –ComputerName 'Node1', 'Node2', 'Node3', 'NodeN' -FilePath 'C:\JEA\Deploy.ps1'

# Finally, delete the session configuration and role capability files from the file share.
Remove-Item -Path '\\FileShare\JEA\Demo.pssc'
Remove-Item -Path '\\FileShare\JEA\SomeModule' -Recurse
```
### Ändern von Funktionen
Beim Arbeiten mit vielen Computern ist es wichtig, dass Änderungen auf konsistente Weise eingeführt werden.
Sobald JEA über eine DSC-Ressource verfügt, wird sichergestellt, dass Ihre Umgebung synchronisiert ist.
Bis dahin empfiehlt es sich dringend, eine Masterkopie Ihrer Sitzungskonfigurationen zu speichern und diese nach jeder Änderung erneut bereitzustellen.

### Entfernen von Funktionen:
Um Ihre JEA-Konfiguration von Ihren Systemen zu entfernen, verwenden Sie den folgenden Befehl auf jedem Computer:
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo 
```
## Berichterstellung zu JEA
Da JEA es nicht privilegierten Benutzern erlaubt, in einem privilegierten Kontext zu arbeiten, sind Protokollierung und Überprüfung extrem wichtig.
In diesem Abschnitt geht es um die Tools, die Sie für die Protokollierung und Berichterstellung verwenden können.

### Berichterstellung zu JEA-Aktionen
#### Mitschnitt einer Aufzeichnung
Eine der schnellsten Möglichkeiten, sich einen Überblick über die Aktivitäten in einer PowerShell-Sitzung zu verschaffen, ist es, der Person, die Daten eingibt, über die Schulter zu schauen.
So sehen Sie die eingegebenen Befehle, die Ausgabe dieser Befehle, und alles ist gut.
Vielleicht ist auch nicht alles gut, aber zumindest wissen Sie dann Bescheid.
PowerShell-Aufzeichnungen bieten eine ähnliche Ansicht nach Abschluss der Aktivitäten.

Wenn Sie das Feld „TranscriptDirectory“ in Ihrer Sitzungskonfiguration verwenden, zeichnet PowerShell automatisch alle Aktionen in einer bestimmten Sitzung auf.
Sie finden die Aufzeichnungen Ihrer Sitzungen in diesem Dokument: $env:ProgramData\JEAConfiguration\Transcripts.

Wie Sie sehen, werden Informationen über den verbundenen Benutzer, den ausführenden Benutzer, die in dieser Sitzung ausgeführten Befehle und vieles mehr aufgezeichnet.
Weitere Informationen über PowerShell-Aufzeichnungen finden Sie in diesem [Blogbeitrag](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).

#### PowerShell-Ereignisprotokolle
Wenn die Modulprotokollierung aktiviert ist, werden alle PowerShell-Aktionen auch in regulären Windows-Ereignisprotokollen aufgezeichnet.
Diese sind im Vergleich zu Aufzeichnungen etwas schwieriger zu lesen, aber die Detailgenauigkeit kann sehr hilfreich sein.

Im Betriebsprotokoll „PowerShell“ wird unter der Ereignis-ID 4104 jeder aufgerufene Befehl aufgezeichnet, wenn die Modulprotokollierung aktiviert ist.

#### Weitere Ereignisprotokolle
Im Gegensatz zu PowerShell-Protokollen und -Aufzeichnungen erfassen andere Protokollierungsmechanismen nicht den „verbundenen Benutzer“.
Sie müssen PowerShell-Protokolle und andere Protokolle korrelieren, um durchgeführte Aktionen zu vergleichen.

Im Betriebsprotokoll „Windows Remote Management“ werden unter der Ereignis-ID 193 die SID und der Name des Benutzers aufgezeichnet, der die Verbindung herstellt. Zur Unterstützung der Korrelation wird auch die SID des virtuellen ausführenden Kontos aufgezeichnet.
Sie haben sicherlich auch bemerkt, dass der Name des virtuellen ausführenden Kontos am Ende die Domäne und den Benutzernamen des Benutzers enthält, der die Verbindung herstellt.

### Berichterstellung für die JEA-Konfiguration
#### Get-PSSessionConfiguration
Um einen exakten Bericht über den Status Ihrer Umgebung zu erhalten, müssen Sie wissen, wie viele JEA-Endpunkte Sie auf Ihrem Computer eingerichtet haben.
`Get-PSSessionConfiguration` ruft diese Informationen ab.
 
#### Get-PSSessionCapability
Die manuelle Berichterstellung zu den Funktionen eines bestimmten Benutzers über einen JEA-Endpunkt kann ziemlich komplex sein.
Sie müssen wahrscheinlich mehrere verschiedene Rollenfunktionen überprüfen.
Glücklicherweise macht das Cmdlet „Get-PSSessionCapability“ genau das.

Führen Sie zum Testen den folgenden Befehl von einer PowerShell-Administratoreingabeaufforderung aus:
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```
## Abschluss 
Nach Abschluss dieses Leitfadens verfügen Sie über die notwendigen Tools und das Vokabular, sodass Sie selbst einen JEA-Endpunkt erstellen können. Vielen Dank!

## Anhang

## Wichtige Konzepte in diesem Leitfaden
**PowerShell-Remoting**: Mithilfe von PowerShell-Remoting können Sie PowerShell-Befehle auf Remotecomputern ausführen.
Sie können einen oder mehrere Computer sowie temporäre oder dauerhafte Verbindungen verwenden.
In dieser Demo haben Sie in einer interaktiven Sitzung eine Remoteverbindung mit Ihrem lokalen Computer hergestellt.
JEA schränkt die Funktionalität ein, die über PowerShell-Remoting verfügbar ist.
Um weitere Informationen zu PowerShell zu erhalten, führen Sie `Get-Help about_Remote` aus.

**Ausführender Benutzer (RunAs)**: Bei der Verwendung von JEA führt ein Benutzer ohne Administratorrechte ein privilegiertes virtuelles Konto im Modus „Ausführen als“ aus.
Das virtuelle Konto besteht nur für die Dauer der Remotesitzung.
Das heißt: Das Konto wird erstellt, wenn ein Benutzer eine Verbindung mit dem Endpunkt herstellt, und wieder gelöscht, wenn der Benutzer die Sitzung beendet.
Standardmäßig ist das virtuelle Konto Mitglied der lokalen Administratorengruppe.
Auf einem Domänencontroller ist es Mitglied der Gruppe „Domänen-Admins“.
Virtuelle Konten bestehen nur lokal auf dem Computer, auf dem sie erstellt wurden, und verfügen über keine Berechtigungen außerhalb dieses Computers.
Dies bedeutet, dass sie nicht in Active Directory registriert sind (ihnen ist keine RID zugewiesen).
Außerdem gilt: Wenn ein zulässiger Befehl bzw. ein zulässiges Skript versucht, auf Ressourcen außerhalb des lokalen Computers zuzugreifen, erfolgt der Zugriff auf diese Ressourcen unter der Identität des Computers, nicht der Identität des virtuellen Kontos.

**Verbundener Benutzer (Connected)**: Der Benutzer ohne Administratorrechte, der eine Verbindung mit dem JEA-Endpunkt herstellt und dem Rollen zugewiesen sind.
Alle Befehle, die dieser Benutzer ausführt, werden im Kontext des ausführenden Benutzers oder des virtuellen ausführenden Kontos ausgeführt.


### Erstellen eines Domänencontrollers

Im vorliegenden Dokument wird davon ausgegangen, dass Ihr Computer in eine Domäne eingebunden ist.
Wenn Sie derzeit nicht über eine Domäne verfügen, in die der Computer eingebunden werden kann, hilft Ihnen dieser Abschnitt dabei, mithilfe von DSC schnell einen Domänencontroller einzurichten.

#### Voraussetzungen

1.  Der Computer befindet sich in einem internen Netzwerk.
2.  Der Computer ist nicht in eine vorhandene Domäne eingebunden.
3.  Auf dem Computer wird Windows Server 2016 ausgeführt, oder es ist WMF 5.0 installiert.

#### Installieren von xActiveDirectory
Wenn Ihr Computer über eine aktive Internetverbindung verfügt, führen Sie folgenden Befehl in einem PowerShell-Fenster mit erhöhten Rechten aus:
```PowerShell
Install-Module xActiveDirectory -Force 
```
Wenn Sie nicht über eine Internetverbindung verfügen, installieren Sie xActiveDirectory auf einem anderen Computer, und kopieren Sie den xActiveDirectory-Ordner in das Verzeichnis „C:\Programme\WindowsPowerShell\Modules“ auf Ihrem Computer.

Um zu überprüfen, ob die Installation erfolgreich war, führen Sie folgenden Befehl aus:
```PowerShell
Get-Module xActiveDirectory -ListAvailable
``` 

#### Einrichten einer Domäne mit DSC
Kopieren Sie das folgende Skript in PowerShell, um Ihren Computer als Domänencontroller in einer neuen Domäne einzurichten.
**HINWEIS DES AUTORS: ES GIBT EIN BEKANNTES PROBLEM, DASS DIE BEREITGESTELLTEN ANMELDEINFORMATIONEN NICHT VERWENDET WERDEN.  MERKEN SIE SICH DAHER UNBEDINGT IHR LOKALES ADMINISTRATORKENNWORT.**

```PowerShell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value $env:COMPUTERNAME -Force 

# This "MetaConfiguration" sets the DSC Engine to automatically reboot if required
[DscLocalConfigurationManager()]
Configuration MetaConfiguration
{
    Node $env:Computername
    {
        Settings
        {
            RebootNodeIfNeeded = $true
        }
    }
    
}

MetaConfiguration
# Apply the MetaConfiguration
Set-DscLocalConfigurationManager .\MetaConfiguration

# Configure a domain controller of a new "Contoso" domain
configuration DomainController
{
    param
    (
        $node,
        $cred
    )
    Import-DscResource -ModuleName xActiveDirectory

    Node $node
    {
        WindowsFeature ADDS
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain Contoso
        {
            DomainName = 'contoso.com'
            DomainAdministratorCredential = $cred
            SafemodeAdministratorPassword = $cred
            DependsOn = '[WindowsFeature]ADDS'
        }

        file temp
        {
            DestinationPath = 'C:\temp.txt'
            Contents = 'Domain has been created'
            DependsOn = '[xADDomain]Contoso'
        }
    }
}

$ConfigData = @{
    AllNodes = @(
        @{
            NodeName = $env:Computername
            PSDscAllowPlainTextPassword = $true
        }
    )
}

# Enter your desired password for the domain administrator (note, this will be stored as plain text)
DomainController -cred (Get-Credential -Message "Enter desired credential for domain administrator") -node $env:Computername -configurationData $ConfigData

# Apply the configuration to create the domain controller
Start-DSCConfiguration -path .\DomainController -ComputerName $env:Computername -Wait -Force -Verbose
```
Ihr Computer wird mehrmals neu gestartet.
Sobald Sie eine Datei namens „C:\temp.txt“ mit dem Inhalt „Domain has been created.“ sehen, wissen Sie, dass der Vorgang abgeschlossen ist. 

#### Einrichten von Benutzern und Gruppen
Mit den folgenden Befehlen richten Sie eine Gruppe „Helpdesk“ und eine Gruppe „Operator“ sowie jeweils einen entsprechenden Benutzer ohne Administratorrechte in Ihrer Domäne ein, der Mitglied der jeweiligen Gruppe ist.
```PowerShell
# Make Groups
$NonAdminOperatorGroup = New-ADGroup -Name "JEA_NonAdmin_Operator" -GroupScope DomainLocal -PassThru
$NonAdminHelpDeskGroup = New-ADGroup -Name "JEA_NonAdmin_HelpDesk" -GroupScope DomainLocal -PassThru
$TestGroup = New-ADGroup -Name "Test_Group" -GroupScope DomainLocal -PassThru

# Make Users
$OperatorUser = New-ADUser -Name "OperatorUser" -AccountPassword (ConvertTo-SecureString "pa`$`$w0rd" -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $OperatorUser

$HelpDeskUser = New-ADUser -name "HelpDeskUser" -AccountPassword (ConvertTo-SecureString "pa`$`$w0rd" -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $HelpDeskUser

# Add Users to Groups
Add-ADGroupMember -Identity $NonAdminOperatorGroup -Members $OperatorUser
Add-ADGroupMember -Identity $NonAdminHelpDeskGroup -Members $HelpDeskUser
```

### Blacklists
Nachdem Sie erste Erfahrungen mit JEA gesammelt haben, fragen Sie sich vielleicht, ob es möglich ist, Befehle auf eine „Blacklist“ zu setzen.
Das ist eine verständliche Anforderung, derzeit jedoch aus folgenden Gründen für JEA nicht geplant:

1.  Wir haben JEA dafür konzipiert, Operatoren nur die Aktionen zu erlauben, die sie ausführen müssen.
Eine Blacklist ist das Gegenteil dieses Konzepts.

2.  Die Autoren der PowerShell-Befehle haben diese Befehle nicht mit Blick auf JEA geschrieben.
Bei einer Neuinstallation von Windows Server 2016 sind etwa 1520 Befehle sofort verfügbar.
Bei den Gefahrenmodellen für diese Befehle ist die Möglichkeit, dass ein Benutzer Befehle mit einem Konto mit höheren Berechtigungen ausführt, nicht berücksichtigt.
Einige Befehle lassen per Design Codeeinfügungen zu (z. B. Add-Type und Invoke-Command im PowerShell-Kernmodul).
JEA kann Sie warnen, wenn Sie bestimmte, uns bekannte Befehle verfügbar machen, wir haben jedoch nicht jeden einzelnen Befehl in Windows basierend auf dem neuen Gefahrenmodell neu bewertet.
Sie müssen die Funktionen der Befehle verstehen, die Sie über JEA verfügbar machen.  

3.  Darüber hinaus: Selbst wenn JEA alle Befehle mit möglichen Schwachstellen durch Codeeinfügung blockieren würde, gäbe es keine Garantie, dass ein böswilliger Benutzer nicht in der Lage wäre, eine auf der Blacklist stehende Aktion über einen anderen Befehl auszuführen.
Wenn Sie die Befehle, die Sie verfügbar machen, nicht genau kennen, können Sie nicht garantieren, dass eine bestimmte Aktion nicht möglich ist.
Die Verantwortung dafür, die Befehle zu verstehen, die Sie verfügbar machen, liegt vollständig bei Ihnen – unabhängig davon, ob eine Whitelist oder eine Blacklist verwendet wird.
Die Anzahl von Befehlen, die auf einer Blacklist aufgeführt werden müssten, wäre unüberschaubar. Daher wird JEA stattdessen mit Whitelists implementiert.

### Überlegungen zum Einschränken von Befehlen
Ein wichtiger Hinweis zu diesem Schritt:
Es ist von entscheidender Bedeutung, dass alle über JEA verfügbar gemachten Funktionen sich in Bereichen befinden, auf die nur Administratoren zugreifen können.
Benutzer ohne Administratorrechte dürfen nicht die Möglichkeit haben, die verwendeten Skripts über JEA-Endpunkte zu ändern.

In diesem Zusammenhang ist es ebenso wichtig, dass Sie JEA-Benutzern nicht die Möglichkeit bieten, JEA-Konfigurationen und Skripts auf der Whitelist in ihren JEA-Sitzungen zu überschreiben.
Gehen Sie mit größter Umsicht vor, wenn Sie Befehle wie `Copy-Item` verfügbar machen!

### Häufige Fehler bei Rollenfunktionen
Wenn Sie diesen Prozess alleine absolvieren, könnten Ihnen einige häufig auftretende Fehler unterlaufen.
Hier finden Sie einige wichtige Informationen dazu, wie Sie solche Fehler identifizieren und beheben, wenn Sie einen neuen Endpunkt erstellen oder ändern:

#### Funktionen im Vergleich zu Cmdlets
In PowerShell geschriebene PowerShell-Befehle sind PowerShell-Funktionen.
Als spezielle .NET-Klassen geschriebene PowerShell-Befehle sind PowerShell-Cmdlets.
Sie können den Befehlstyp prüfen, indem Sie `Get-Command` ausführen.

#### VisibleProviders 
Sie müssen alle Anbieter verfügbar machen, die von Ihren Befehlen benötigt werden.
Am häufigsten wird der Dateisystemanbieter verwendet, Sie werden jedoch möglicherweise auch weitere Anbieter verfügbar machen müssen, beispielsweise den Registrierungsanbieter.
Eine Einführung in das Thema Anbieter finden Sie in diesem Blogbeitrag von [Hey, Scripting Guy!](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).
Gehen Sie vorsichtig vor, wenn Sie Anbieter verfügbar machen – häufig ist es besser, selbst eine Funktion zu definieren, die mit den zugrunde liegenden Anbietern arbeitet, als den Anbieter in einer JEA-Sitzung direkt verfügbar zu machen.
Auf diese Weise können Sie Benutzern weiterhin ermöglichen, mit Dateien, Registrierungsschlüsseln usw. zu arbeiten, behalten aber dank einer benutzerdefinierten Validierungslogik die Kontrolle darüber, mit *welchen* Dateien und Registrierungsschlüsseln die Benutzer arbeiten.

<!--HONumber=Jun16_HO1-->


