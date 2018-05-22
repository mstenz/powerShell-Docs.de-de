---
ms.date: 04/11/2018
keywords: dsc,powershell,configuration,setup
title: DSC-Pulldienst
ms.openlocfilehash: 057da50843e79ae31eef4fea1fa58e882a9d1ace
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
---
# <a name="desired-state-configuration-pull-service"></a>Desired State Configuration – Pulldienst

> Gilt für: Windows PowerShell 5.0

> [!IMPORTANT]
> Der Pull-Server (Windows-Feature *DSC-Dienst*) ist eine von Windows Server unterstützte Komponente, jedoch sollen keine neuen Features oder Funktionen angeboten werden. Es wird empfohlen, verwaltete Clients auf [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) umzustellen (enthält Features zusätzlich zum Pull-Server unter Windows Server) oder auf eine der [hier](pullserver.md#community-solutions-for-pull-service) aufgeführten Communitylösungen.

Der lokale Konfigurations-Manager kann zentral mithilfe einer Pulldienstlösung verwaltet werden.
Bei diesem Ansatz wird der verwaltete Knoten bei einem Dienst registriert und in den LCM-Einstellungen einer Konfiguration zugeordnet.
Die Konfiguration und alle DSC-Ressourcen, die als Abhängigkeiten für die Konfiguration erforderlich sind, werden auf den Computer heruntergeladen und von LCM zum Verwalten der Konfiguration verwendet.
Informationen über den Status des verwalteten Computers werden zur Berichterstellung auf den Dienst hochgeladen.
Dieses Konzept wird als „Pulldienst“ bezeichnet.

Folgende Optionen sind zurzeit für den Pulldienst verfügbar:

- Azure Automation DSC-Dienst (Desired State Configuration)
- Ein Pulldienst bei der Ausführung unter Windows Server
- Von der Community verwaltete Open-Source-Lösungen
- Eine SMB-Freigabe

**Die empfohlene Lösung** und die Option mit den meisten verfügbaren Features ist [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).

Der Azure-Dienst kann Knoten lokal in privaten Rechenzentren oder in öffentlichen Clouds wie Azure und AWS verwalten.
Für private Umgebungen, in denen Server keine direkte Verbindung mit dem Internet herstellen können, sollten Sie die Begrenzung des ausgehenden Datenverkehrs auf den veröffentlichten Azure-IP-Adressbereich in Betracht ziehen. Informationen hierzu finden Sie unter [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653) (IP-Adressbereiche für Azure-Rechenzentren).

Features des Onlinediensts, die im Pulldienst unter Windows Server zurzeit nicht verfügbar sind:
- Verschlüsselung aller Daten während der Übertragung und im Ruhezustand
- Automatische Erstellung und Verwaltung von Clientzertifikaten
- Speicherung von Geheimnissen zur zentralen Verwaltung von [Kennwörtern/Anmeldeinformationen](/azure/automation/automation-credentials) oder [Variablen](/azure/automation/automation-variables) wie z.B. Servernamen oder Verbindungszeichenfolgen
- Zentrale Verwaltung der [LCM-Konfiguration](metaConfig.md#basic-settings) für Knoten
- Zentrale Zuweisung von Konfigurationen zu Clientknoten
- Freigabe von Konfigurationsänderungen für Canarygruppen zum Durchführen von Tests vor Einführung in die Produktion
- Grafische Berichterstellung
  - Statusdetails auf der Granularitätsstufe von DSC-Ressourcen
  - Ausführliche Fehlermeldungen von Clientcomputern für die Problembehandlung
- [Integration in Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) für Warnungen, automatisierte Tasks, Android-/iOS-App für Berichte und Warnungen

## <a name="dsc-pull-service-in-windows-server"></a>DSC-Pulldienst in Windows Server

Es ist möglich, einen Pulldienst für die Ausführung unter Windows Server zu konfigurieren.
Beachten Sie, dass die in Windows Server enthaltene Pulldienstlösung nur die Funktionen zum Speichern von Konfigurationen/Modulen für den Download und das Erfassen von Berichtsdaten in einer Datenbank umfasst.
Sie umfasst viele der Funktionen nicht, die vom Dienst in Azure bereitgestellt werden, und stellt daher kein gutes Tool dar, um den Einsatz des Diensts zu bewerten.

Der in Windows Server angebotene Pulldienst ist ein Webdienst in IIS, der DSC-Konfigurationsdateien mithilfe einer OData-Schnittstelle für Zielknoten verfügbar macht, wenn die Zielknoten diese anfordern.

Anforderungen für die Verwendung eines Pullservers:

- Ein Server mit:
  - WMF/PowerShell 5.0 oder höher
  - IIS-Serverrolle
  - DSC-Dienst
- Im Idealfall eine Möglichkeit zum Generieren eines Zertifikats, um die an den lokalen Konfigurations-Manager (LCM) auf Zielknoten übergebenen Anmeldeinformationen abzusichern

Die beste Möglichkeit, Windows Server zum Hosten eines Pulldiensts zu konfigurieren, ist die Verwendung einer DSC-Konfiguration.
Ein Beispielskript finden Sie unten.

### <a name="supported-database-systems"></a>Unterstützte Datenbanksysteme

|WMF 4.0   |WMF 5.0  |WMF 5.1 |WMF 5.1 (Windows Server Insider Preview 17090)|
|---------|---------|---------|---------|
|MDB     |ESENT (Standard), MDB |ESENT (Standard), MDB|ESENT (Standard), SQL Server, MDB

Ab dem Release 17090 von [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver) ist SQL Server eine unterstützte Option für den Pulldienst (Windows-Feature *DSC-Dienst*).  Dadurch wird eine neue Option für die Skalierung großer DSC-Umgebungen bereitgestellt, die nicht zu [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) migriert wurden.

> **Hinweis**: Die Unterstützung für SQL Server wird vorherigen Versionen von WMF 5.1 (oder früher) nicht hinzugefügt und ist nur für Windows Server-Versionen ab 17090 verfügbar.

Um den Pull-Server so zu konfigurieren, dass er SQL Server verwendet, legen Sie **SqlProvider** auf `$true` und **SqlConnectionString** auf eine gültige SQL Server-Verbindungszeichenfolge fest.  Weitere Informationen finden Sie unter [SqlClient-Verbindungszeichenfolgen](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).
Ein Beispiel einer SQL Server-Konfiguration mit **xDscWebService** finden Sie zunächst unter [Verwenden der xDSCWebService-Ressource](#using-the-xdscwebservice-resource), lesen Sie anschließend die GitHub-Seite zu [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).

### <a name="using-the-xdscwebservice-resource"></a>Verwenden der xDscWebService-Ressource

Die einfachste Möglichkeit einen Web-Pull-Server einzurichten, ist die Verwendung der Ressource **xDscWebService** im Modul **xPSDesiredStateConfiguration**.
Die folgenden Schritte erläutern, wie Sie die Ressource in einer Konfiguration verwenden, die den Webdienst einrichtet.

1. Rufen Sie das Cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module) auf, um das Modul **xPSDesiredStateConfiguration** zu installieren. **Hinweis**: **Install-Module** ist im Modul **PowerShellGet** enthalten, das Bestandteil von PowerShell 5.0 ist. Das Modul **PowerShellGet** für PowerShell 3.0 und 4.0 können Sie unter [PowerShell-Module „PackageManagement“ – Vorschau](https://www.microsoft.com/en-us/download/details.aspx?id=49186) herunterladen.
1. Rufen Sie ein SSL-Zertifikat für den DSC-Pullserver von einer vertrauenswürdigen Zertifizierungsstelle innerhalb Ihrer Organisation oder von einer öffentlichen Zertifizierungsstelle ab. Das von der Zertifizierungsstelle empfangene Zertifikat weist normalerweise das PFX-Format auf. Installieren Sie auf dem Knoten, der als DSC-Pull-Server fungieren soll, das Zertifikat am Standardspeicherort, also normalerweise unter „CERT:\LocalMachine\My“. Notieren Sie sich den Zertifikatfingerabdruck.
1. Wählen Sie eine GUID als der Registrierungsschlüssel aus. Um einen mithilfe von PowerShell zu generieren, geben Sie ``` [guid]::newGuid()``` oder ```New-Guid``` an der PS-Eingabeaufforderung ein, und drücken Sie anschließend die EINGABETASTE. Dieser Schlüssel wird von Clientknoten bei der Registrierung als gemeinsamer Schlüssel zum Authentifizieren verwendet. Weitere Informationen finden Sie weiter unten im Abschnitt „Registrierungsschlüssel“.
1. Starten Sie (F5) in PowerShell ISE das folgende Konfigurationsskript (enthalten im Beispielordner des Moduls **xPSDesiredStateConfiguration** als „Sample_xDscWebServiceRegistration.ps1“). Dieses Skript richtet den Pullserver ein.

```powershell
configuration Sample_xDscWebServiceRegistration
{
    param
    (
        [string[]]$NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $certificateThumbPrint,

        [Parameter(HelpMessage='This should be a string with enough entropy (randomness) to protect the registration of clients to the pull server.  We will use new GUID by default.')]
        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey   # A guid that clients use to initiate conversation with pull server
    )

    Import-DSCResource -ModuleName xPSDesiredStateConfiguration

    Node $NodeName
    {
        WindowsFeature DSCServiceFeature
        {
            Ensure = "Present"
            Name   = "DSC-Service"
        }

        xDscWebService PSDSCPullServer
        {
            Ensure                  = "Present"
            EndpointName            = "PSDSCPullServer"
            Port                    = 8080
            PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer"
            CertificateThumbPrint   = $certificateThumbPrint
            ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
            ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
            State                   = "Started"
            DependsOn               = "[WindowsFeature]DSCServiceFeature"
            RegistrationKeyPath     = "$env:PROGRAMFILES\WindowsPowerShell\DscService"
            AcceptSelfSignedCertificates = $true
            Enable32BitAppOnWin64   = $false
        }

        File RegistrationKeyFile
        {
            Ensure          = 'Present'
            Type            = 'File'
            DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
            Contents        = $RegistrationKey
        }
    }
}
```

1. Führen Sie die Konfiguration aus, und übergeben Sie als Parameter **certificateThumbPrint** den Fingerabdruck des SSL-Zertifikats und als Parameter **RegistrationKey** einen GUID-Registrierungschlüssel:

```powershell
# To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
# and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
dir Cert:\LocalMachine\my

# Then include this thumbprint when running the configuration
Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

# Run the compiled configuration to make the target node a DSC Pull Server
Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
```

#### <a name="registration-key"></a>Registrierungsschlüssel

Um zuzulassen, dass Clientknoten sich beim Server registrieren und Konfigurationsnamen anstelle einer Konfigurations-ID verwenden können, wird ein von der oben beschriebenen Konfiguration erstellter Registrierungsschlüssel in einer Datei namens `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService` gespeichert. Der Registrierungsschlüssel fungiert als ein gemeinsamer geheimer Schlüssel, der vom Client während der anfänglichen Registrierung beim Pullserver verwendet wird. Der Client generiert ein selbstsigniertes Zertifikat, das nach der erfolgreich abgeschlossenen Registrierung zur eindeutigen Authentifizierung beim Pull-Server verwendet wird. Der Fingerabdruck dieses Zertifikats wird lokal gespeichert und der URL des Pullservers zugeordnet.
> **Hinweis**: Registrierungsschlüssel werden in PowerShell 4.0 nicht unterstützt.

Zum Konfigurieren eines Knotens zur Authentifizierung beim Pull-Server muss der Registrierungsschlüssel in der Metakonfiguration für alle Zielknoten enthalten sein, die sich bei diesem Pull-Server registrieren. Beachten Sie, dass **RegistrationKey** aus der unten stehenden Metakonfiguration entfernt wird, nachdem der Zielcomputer erfolgreich registriert wurde, und dass der Wert „140a952b-b9d6-406b-b416-e0f759c9c0e4“ dem in der Datei „RegistrationKeys.txt“ auf dem Pullserver gespeicherten Wert entsprechen muss. Behandeln Sie den Registrierungsschlüsselwert immer vertraulich, da sich jeder beliebige Zielcomputer mit diesem Schlüssel beim Pullserver registrieren könnte.

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to setup pull server in previous configuration

        [ValidateNotNullOrEmpty()]
        [string] $ServerName = 'localhost' #node name of the pull server, same as $NodeName used in previous configuration
    )

    Node $NodeName
    {
        Settings
        {
            RefreshMode        = 'Pull'
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey    = $RegistrationKey
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey = $RegistrationKey
        }
    }
}

Sample_MetaConfigurationToRegisterWithLessSecurePullServer -RegistrationKey $RegistrationKey -OutputPath c:\Configs\TargetNodes
```

> **Hinweis**: Der Abschnitt **ReportServerWeb** ermöglicht das Senden von Berichtsdaten an den Pullserver.

Das Fehlen der Eigenschaft **ConfigurationID** in der Metakonfigurationsdatei bedeutet implizit, dass der Pullserver die V2-Version des Pullserverprotokolls unterstützt und somit eine Registrierung erforderlich ist.
Umgekehrt bedeutet das Vorhandensein einer **ConfigurationID**, dass die V1-Version des Pullserverprotokolls verwendet wird und keine Registrierungsverarbeitung erfolgt.

>**Hinweis**: In einem PUSH-Szenario tritt im aktuellen Release ein Fehler auf, aufgrund dessen es erforderlich ist, in der Metakonfigurationsdatei für Knoten, die noch nie bei einem Pull-Server registriert wurden, die Eigenschaft „ConfigurationID“ zu definieren. Dies erzwingt die Verwendung des V1-Pullserver-Protokolls verhindert Registrierungsfehlermeldungen.

## <a name="placing-configurations-and-resources"></a>Platzieren von Konfigurationen und Ressourcen

Nach Abschluss des Pullserversetups befinden sich die von den Eigenschaften **ConfigurationPath** und **ModulePath** in der Pullserverkonfiguration definierten Ordner an dem Ort, an dem Module und Konfigurationen abgelegt werden, die für Zielknoten zum Abrufen verfügbar sein sollen.
Diese Dateien müssen in einem bestimmten Format vorliegen, damit sie von den Pullservern ordnungsgemäß verarbeiten werden können.

### <a name="dsc-resource-module-package-format"></a>Format des DSC-Ressourcenmodulpakets

Jedes Ressourcenmodul muss komprimiert und entsprechend dem folgenden Muster benannt werden: `{Module Name}_{Module Version}.zip`.
Ein Modul namens „xWebAdminstration“ mit einer Modulversion 3.1.2.0 würde beispielsweise „xWebAdministration_3.2.1.0.zip“ heißen.
Jede Version eines Moduls muss in einer eigenen ZIP-Datei enthalten sein.
Da jede ZIP-Datei nur jeweils eine Version einer Ressource enthält, wird das in WMF 5.0 eingeführte das Modulformat, das mehrere Versionen in einem einzigen Verzeichnis ermöglicht, nicht unterstützt.
Das bedeutet, dass Sie vor dem Packen von DSC-Ressourcenmodulen für die Verwendung mit einem Pullserver eine kleine Änderung an der Verzeichnisstruktur vornehmen müssen.
Das Standardformat für Module mit DSC-Ressourcen in WMF 5.0 ist: {Modulordner}\{Modulversion}\DscResources\{DSC-Ressourcenordner}\'.
Entfernen Sie vor dem Packen für den Pull-Server den Ordner **{Modulversion}**, damit der Pfad wie folgt geändert wird: {Modulordner}\DscResources\{DSC-Ressourcenordner}\'.
Komprimieren Sie den Odner nach dieser Änderung wie oben beschrieben, und speichern Sie die ZIP-Dateien im Ordner **ModulePath**.

Verwenden Sie `New-DscChecksum {module zip file}` zum Erstellen einer Prüfsummendatei für das neu hinzugefügte Modul.

### <a name="configuration-mof-format"></a>MOF-Konfigurationsformat

Eine MOF-Konfigurationsdatei muss einer Prüfsummendatei zugeordnet werden, damit ein LCM auf einem Zielknoten die Konfiguration überprüfen kann.
Um eine Prüfsumme zu erstellen, rufen Sie das Cmdlet [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) auf.
Das Cmdlet verwendet einen **Path**-Parameter, der den Ordner angibt, in dem sich die MOF-Konfigurationsdatei befindet.
Das Cmdlet erstellt eine Prüfsummendatei mit dem Namen `ConfigurationMOFName.mof.checksum`, wobei `ConfigurationMOFName` der Name der MOF-Konfigurationsdatei ist.
Wenn in dem angegebenen Ordner mehrere MOF-Konfigurationsdateien vorhanden sind, wird für jede Konfiguration im Ordner eine Prüfsumme erstellt.
Platzieren Sie die MOF-Dateien und die zugeordneten Prüfsummendateien im Ordner **ConfigurationPath**.

>**Hinweis**: Wenn Sie die MOF-Konfigurationsdatei in irgendeiner Weise ändern, müssen Sie auch die Prüfsummendatei neu erstellen.

### <a name="tooling"></a>Tools

Um das Einrichten, Überprüfen und Verwalten des Pullservers zu vereinfachen, enthält die neueste Version des Moduls „xPSDesiredStateConfiguration“ folgende Tools als Beispiele:

1. Ein Modul, das beim Packen von DSC-Ressourcenmodulen und Konfigurationsdateien zur Verwendung auf dem Pullserver hilft. [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1). Beispiele unten:

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Ein Skript, das den Pullserver überprüft, wurde ordnungsgemäß konfiguriert. [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).

## <a name="community-solutions-for-pull-service"></a>Community-Lösungen für Pulldienste

Die DSC-Community hat mehrere Lösungen zum Implementieren des Pulldienstprotokolls erstellt.
Für lokale Umgebungen bieten diese Pulldienstfunktionen und die Möglichkeit, der Community mit inkrementellen Verbesserungen etwas zurückzugeben.

- [Tug](https://github.com/powershellorg/tug)
- [DSC-TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>Pullclientkonfiguration

In den folgenden Themen wird das Einrichten von Pullclients im Detail beschrieben:

- [Einrichten eines DSC-Pullclients mithilfe einer Konfigurations-ID](pullClientConfigID.md)
- [Einrichten eines DSC-Pullclients mithilfe von Konfigurationsnamen](pullClientConfigNames.md)
- [Teilkonfigurationen](partialConfigs.md)

## <a name="see-also"></a>Siehe auch

- [Windows PowerShell DSC – Übersicht](overview.md)
- [Inkraftsetzung von Konfigurationen](enactingConfigurations.md)
- [Verwenden eines DSC-Berichtsservers](reportServer.md)
- [[MS-DSCPM]: Desired State Configuration Pull Model Protocol ([MS-DSCPM]: DSC-Pullmodell-Protokoll)](https://msdn.microsoft.com/library/dn393548.aspx)
- [[MS-DSCPM]: Desired State Configuration Pull Model Protocol ([MS-DSCPM]: DSC-Pullmodell-Protokoll Errata)](https://msdn.microsoft.com/library/mt612824.aspx)