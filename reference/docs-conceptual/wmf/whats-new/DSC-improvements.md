---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: DSC-Verbesserungen in WMF 5.1
ms.openlocfilehash: d9339ec9f316c4a32c5fa6cb2360c077973ee334
ms.sourcegitcommit: ea7d87a7a56f368e3175219686dfa2870053c644
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2020
ms.locfileid: "76818106"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a>Verbesserungen an DSC (Desired State Configuration) in WMF 5.1

## <a name="dsc-class-resource-improvements"></a>Verbesserungen an DSC-Klassenressourcen

In WMF 5.1 haben wir die folgenden bekannten Probleme behoben:

- „Get-DscConfiguration“ gibt möglicherweise leere Werte (NULL) oder Fehler zurück, wenn von der „Get()“-Funktion einer klassenbasierten DSC-Ressource ein komplexer Typ bzw. ein Hashtabellentyp zurückgegeben wird.
- „Get-DscConfiguration“ gibt einen Fehler zurück, wenn die RunAs-Anmeldeinformationen bei der DSC-Konfiguration verwendet werden.
- Eine klassenbasierte Ressource kann nicht in einer zusammengesetzten Konfiguration verwendet werden.
- „Start-DscConfiguration“ reagiert nicht mehr, wenn die klassenbasierte Ressource eine Eigenschaft des eigenen Typs aufweist.
- Eine klassenbasierte Ressource kann nicht als exklusive Ressource verwendet werden.

## <a name="dsc-resource-debugging-improvements"></a>Verbesserungen beim Debuggen von DSC-Ressourcen

In WMF 5.0 hat der PowerShell-Debugger nicht direkt an der klassenbasierten Ressourcenmethode (Get/Set/Test) angehalten. In WMF 5.1 wird der Debugger bei der klassenbasierten Ressourcenmethode auf die gleiche Weise wie bei MOF-basierten Ressourcenmethoden anhalten.

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a>Der DSC-Pull-Client unterstützt TLS 1.1 und TLS 1.2

Zuvor unterstützte der DSC-Pull-Client nur SSL 3.0 und TLS 1.0 über HTTPS-Verbindungen. Wenn er gezwungen wurde, sicherere Protokolle zu verwenden, funktionierte der Pull-Client nicht mehr. In WMF 5.1 unterstützt der DSC-Pull-Client SSL 3.0 nicht mehr. Stattdessen werden die sichereren TLS 1.1- und TLS 1.2-Protokolle unterstützt.

## <a name="improved-pull-server-registration"></a>Verbesserte Pull-Serverregistrierung

In früheren Versionen von WMF führten gleichzeitige Registrierungen/Berichterstellungsanforderungen an einen DSC-Pullserver während der Verwendung der ESENT-Datenbank zu einem LCM-Registrierungs- und/oder Berichterstellungsfehler. In solchen Fällen enthalten die Ereignisprotokolle auf dem Pull-Server den Fehler „Der Instanzname wird bereits verwendet“. Die Ursache hierfür ist die Verwendung eines falschen Musters für den Zugriff auf die ESENT-Datenbank in einem Multithread-Szenario. In WMF 5.1 wurde dieses Problem behoben. Gleichzeitige Registrierungen oder Berichterstellung (mit ESENT-Datenbank) funktionieren in WMF 5.1 einwandfrei. Dieses Problem gilt nur für die ESENT-Datenbank und nicht für die OLE DB-Datenbank.

## <a name="enable-circular-log-on-esent-database-instance"></a>Aktivieren des Umlaufprotokolls in der ESENT-Datenbankinstanz

In früheren Version von DSC-PullServer füllten die ESENT-Datenbankprotokolldateien den Speicherplatz des Pullservers, weil die Datenbankinstanz ohne Umlaufprotokoll erstellt wurde. In dieser Version können Sie das Umlaufprotokollverhalten der Instanz mit „web.config“ des Pull-Servers steuern. Standardmäßig ist „CircularLogging“ auf TRUE festgelegt.

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a>Wow64-Unterstützung für das Schlüsselwort „Configuration“

Das Schlüsselwort `Configuration` wird nun in WOW64 auf 64-Bit-Computern unterstützt. Dies bedeutet, dass eine DSC-Konfiguration in einem 32-Bit-Prozess, wie z. B. Windows PowerShell ISE (x86) auf einem 64-Bit-Computer, definiert und kompiliert werden kann.

## <a name="pull-partial-configuration-naming-convention"></a>Übertragen einer Namenskonvention für eine partielle Konfiguration mithilfe von Pull

Im vorherigen Release besagte die Namenskonvention für eine partielle Konfiguration, dass der MOF-Dateiname im Pull-Server/-Dienst mit dem Namen der partiellen Konfiguration übereinstimmen soll, der in den Einstellungen des lokalen Konfigurations-Managers (Local Configuration Manager; LCM) angegeben wurde. Dieser Name sollte wiederum mit dem in der MOF-Datei eingebetteten Konfigurationsnamen übereinstimmen.

Weitere Informationen finden Sie in den nachfolgenden Abbildungen:

- Lokale Konfigurationseinstellungen, die eine Teilkonfiguration definieren, die von einem Knoten empfangen werden darf.

  ![Beispiel einer Metakonfiguration](../images/DSC-improvements/MetaConfigPartialOne.png)

- Beispieldefinition einer partiellen Konfiguration

  ```powershell
  Configuration PartialOne
  {
      Node('localhost')
      {
          File test
          {
              DestinationPath = "$env:TEMP\partialconfigexample.txt"
              Contents = 'Partial Config Example'
          }
      }
  }
  PartialOne
  ```

- ConfigurationName, eingebettet in der generierten MOF-Datei

  ![Beispiel einer generierten MOF-Datei](../images/DSC-improvements/PartialGeneratedMof.png)

- FileName im Repository der Pull-Konfiguration

  ![FileName im Repository der Konfiguration](../images/DSC-improvements/PartialInConfigRepository.png)

  Basierend auf dem Namen des Azure Automation-Diensts generierte MOF-Dateien nach dem Schema „`<ConfigurationName>.<NodeName>.mof`“. Die nachstehende Konfiguration wird also in „PartialOne.localhost.mof“ kompiliert.

  Aus diesem Grund war es nicht möglich, eine Ihrer Teilkonfigurationen aus dem Azure Automation-Dienst mithilfe von Pull zu übertragen.

  ```powershell
  Configuration PartialOne
  {
      Node('localhost')
      {
          File test
          {
              DestinationPath = "$env:TEMP\partialconfigexample.txt"
              Contents = 'Partial Config Example'
          }
      }
  }
  PartialOne
  ```

  In WMF 5.1 kann die Teilkonfiguration im Pull-Server/Dienst nach dem Schema „`<ConfigurationName>.<NodeName>.mof`“ benannt werden. Darüber hinaus kann die Konfigurationsdatei auf dem Konfigurationsrepository des Pull-Servers einen beliebigen Dateinamen haben, wenn ein Computer eine einzelne Konfiguration von einem Pull-Server/-Dienst mithilfe von Pull überträgt. Diese Benennungsflexibilität erlaubt Ihnen, Ihre Knoten teilweise über den Azure Automation-Dienst zu verwalten, wobei ein Teil der Konfiguration Ihres Knotens von Azure Automation DSC stammt und die andere Teilkonfiguration von Ihnen lokal verwaltet wird.

  Mit der nachstehenden Metakonfiguration wird ein Knoten so eingerichtet, dass er sowohl lokal als auch vom Azure Automation-Dienst verwaltet wird.

  ```powershell
  [DscLocalConfigurationManager()]
  Configuration RegistrationMetaConfig
  {
      Settings
      {
          RefreshFrequencyMins = 30
          RefreshMode = "PULL"
      }

      ConfigurationRepositoryWeb web
      {
          ServerURL =  $endPoint
          RegistrationKey = $registrationKey
          ConfigurationNames = $configurationName
      }

      # Partial configuration managed by Azure Automation service.
      PartialConfiguration PartialConfigurationManagedByAzureAutomation
      {
          ConfigurationSource = "[ConfigurationRepositoryWeb]Web"
      }

      # This partial configuration is managed locally.
      PartialConfiguration OnPremisesConfig
      {
          RefreshMode = "PUSH"
          ExclusiveResources = @("Script")
      }

  }

  RegistrationMetaConfig
  Set-DscLocalConfigurationManager -Path .\RegistrationMetaConfig -Verbose
  ```

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a>Verwenden von PsDscRunAsCredential mit zusammengesetzten DSC-Ressourcen

Ab jetzt können Sie auch[PsDscRunAsCredential](/powershell/scripting/dsc/configurations/runAsUser) mit [zusammengesetzten](/powershell/scripting/dsc/authoringresourcecomposite) DSC-Ressourcen verwenden.

Sie können jetzt für **PsDscRunAsCredential** einen Wert angeben, wenn sie zusammengesetzte Ressourcen innerhalb von Konfigurationen verwenden. Wenn angegeben, werden alle Ressourcen in einer zusammengesetzten Ressource als RunAs-Benutzer ausgeführt. Wenn eine zusammengesetzte Ressource eine andere zusammengesetzte Ressource aufruft, werden deren gesamte Ressourcen ebenfalls als RunAs-Benutzer ausgeführt. RunAs-Anmeldeinformationen werden auf alle Hierarchieebenen der zusammengesetzten Ressource verteilt. Wenn eine Ressource in einer zusammengesetzten Ressource einen eigenen Wert für **PsDscRunAsCredential** angibt, wird während der Kompilierung der Konfiguration ein Fehler beim Zusammenführen zurückgegeben.

Dieses Beispiel zeigt die Verwendung in Kombination mit der zusammengesetzten [WindowsFeatureSet](/powershell/scripting/dsc/reference/resources/windows/windowsfeaturesetresource)-Ressource, die im PSDesiredStateConfiguration-Modul enthalten ist.

```powershell
Configuration InstallWindowsFeature
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        WindowsFeatureSet features
        {
            Name = @("Telnet-Client","SNMP-Service")
            Ensure = "Present"
            IncludeAllSubFeature = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost'
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

InstallWindowsFeature -ConfigurationData $configData
```

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>Zulassen identischer doppelter Ressourcen in einer Konfiguration

DSC lässt keine in Konflikt stehenden Ressourcendefinitionen in einer Konfiguration zu bzw. behandeln diese nicht. Anstatt zu versuchen, den Konflikt zu lösen, tritt ein Fehler auf. Sobald die Wiederverwendung von Konfigurationen mittels zusammengesetzter Ressourcen häufiger vorkommt, werden Konflikte häufiger auftreten. Wenn in Konflikt stehende Ressourcendefinitionen identisch sind, sollte DSC diese intelligent zulassen. In dieser Version unterstützen wir mehrere Ressourceninstanzen, die identische Definitionen aufweisen:

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

In früheren Versionen wäre das Ergebnis eine fehlerhafte Kompilierung aufgrund eines Konflikts zwischen der „WindowsFeature FE_IIS“-Instanz und der „WindowsFeature Worker_IIS“-Instanz beim Versuch sicherzustellen, dass die Roll „Web-Server“ installiert ist. Beachten Sie, dass *alle* Eigenschaften, die konfiguriert werden, in diesen beiden Konfigurationen identisch sind. Da *alle* Eigenschaften in diesen beiden Ressourcen identisch sind, führt dies jetzt zu einer erfolgreichen Kompilierung.

Wenn Eigenschaften in beiden Ressourcen unterschiedlich sind, werden sie nicht als identisch eingestuft, weshalb die Kompilierung misslingt.

## <a name="dsc-module-and-configuration-signing-validations"></a>Überprüfen der Signatur von DSC-Modulen und -Konfigurationen

In DSC werden Konfigurationen und Module über den Pull-Server auf die verwalteten Computer verteilt. Wenn ein Pull-Server kompromittiert ist, kann ein Angreifer möglicherweise die Konfigurationen und Module auf dem Pull-Server ändern und sie anschließend an alle verwalteten Knoten verteilen lassen.

In WMF 5.1 unterstützt DSC die Überprüfung der digitalen Signaturen in Katalog- und Konfigurationsdateien (MOF-Dateien). Diese Funktion verhindert, dass Knoten Konfigurationen oder Moduldateien ausführen, die nicht von einem vertrauenswürdigen Signaturgeber signiert oder die manipuliert wurden, nachdem der vertrauenswürdige Signaturgeber sie signiert hat.

### <a name="how-to-sign-configuration-and-module"></a>So signieren Sie Konfigurationen und Module

- Konfigurationsdateien (MOF-Dateien): Das vorhandene PowerShell-Cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) wurde erweitert und unterstützt nun das Signieren von MOF-Dateien.
- Module: Module werden signiert, indem der entsprechende Modulkatalog wie in den nachfolgenden Schritten erläutert signiert wird:
  1. Erstellen einer Katalogdatei: Eine Katalogdatei enthält eine Sammlung kryptografischer Hashes oder Fingerabdrücke. Jeder Fingerabdruck entspricht einer Datei, die im Modul enthalten ist. Mit dem neu hinzugefügten Cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog) können Benutzer eine Katalogdatei für ihr Modul erstellen.
  2. Signieren der Katalogdatei: Mit [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) wird die Katalogdatei signiert.
  3. Fügen Sie die Katalogdatei in den Modulordner ein. Gemäß der Konvention sollte die Modulkatalogdatei mit dem gleichen Namen wie das Modul im Modulordner abgelegt werden.

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a>Einstellungen des lokalen Konfigurations-Managers zur Aktivierung von Signaturüberprüfungen

#### <a name="pull"></a>Pull

Der lokale Konfigurations-Manager eines Knotens überprüft die Signatur von Modulen und Konfigurationen auf Grundlage der aktuellen Einstellungen. Die Überprüfung der Signatur ist standardmäßig deaktiviert. Die Signaturüberprüfung kann aktiviert werden, indem Sie wie nachfolgend gezeigt den Block „SignatureValidation“ der Metakonfigurationsdefinition des Knotens hinzufügen:

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'
    }

    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # If the TrustedStorePath property is provided then LCM will use the custom path. Otherwise, the LCM will use default trusted store path (Cert:\LocalMachine\DSCStore) to find the signing certificate.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

Die Festlegung der oben genannten Metakonfiguration auf einem Knoten aktiviert die Überprüfung der Signatur für heruntergeladene Konfigurationen und Module. Der lokale Konfigurations-Manager führt die folgenden Schritte aus, um die digitalen Signaturen zu überprüfen.

1. Überprüfen, ob die Signatur einer Konfigurationsdatei (MOF) gültig ist, mithilfe des Cmdlets `Get-AuthenticodeSignature`.
2. Überprüfen der Zertifizierungsstelle, die den Signaturgeber als vertrauenswürdig eingestuft hat.
3. Herunterladen der Modul-/Ressourcenabhängigkeiten der Konfiguration in einen temporären Speicherort.
4. Überprüfen der Signatur des Katalogs, der im Modul enthalten ist.
   - Suchen einer `<moduleName>.cat`-Datei und Überprüfen ihrer Signatur mithilfe von `Get-AuthenticodeSignature`.
   - Überprüfen der Zertifizierungsstelle, die den Signaturgeber als vertrauenswürdig eingestuft hat
   - Sicherstellen, dass der Inhalt der Module nicht manipuliert wurde, mithilfe des neuen Cmdlets `Test-FileCatalog`.
5. `Install-Module` in `$env:ProgramFiles\WindowsPowerShell\Modules\`
6. Prozesskonfiguration

> [!NOTE]
> Signaturen von Modulkatalogen und -konfigurationen werden nur bei der ersten Anwendung der Konfiguration auf das System überprüft, oder wenn das Modul heruntergeladen und installiert wird.
> Konsistenzläufe überprüfen nicht die Signatur von „current.mof“-Dateien oder deren Modulabhängigkeiten. Wenn bei der Überprüfung zu irgendeinem Zeitpunkt ein Fehler auftritt, z. B. wenn die vom Pull-Server mithilfe von Pull übertragene Konfiguration nicht signiert ist, wird bei der Verarbeitung der Konfiguration der nachstehende Fehler ausgegeben, und alle temporären Dateien werden gelöscht.

![Beispielkonfiguration einer Fehlerausgabe](../images/DSC-improvements/PullUnsignedConfigFail.png)

Entsprechend wird beim Übertragen eines Moduls mithilfe von Pull, dessen Katalog nicht signiert ist, der folgende Fehler ausgegeben:

![Beispielmodul einer Fehlerausgabe](../images/DSC-improvements/PullUnisgnedCatalog.png)

#### <a name="push"></a>Push

Eine Konfiguration, die über Push bereitgestellt wurde, könnte an ihrer Quelle manipuliert worden sein, bevor sie an den Knoten übermittelt wurde. Der lokale Konfigurations-Manager führt für mithilfe von Push übertragene oder veröffentlichte Konfigurationen ähnliche Schritte zur Überprüfung der Signatur durch. Nachstehend finden Sie ein vollständiges Beispiel für die Signaturüberprüfung bei einer mithilfe von Push übertragenen Konfiguration.

- Aktivieren Sie die Überprüfung der Signatur auf dem Knoten.

  ```powershell
  [DSCLocalConfigurationManager()]
  Configuration EnableSignatureValidation
  {
      Settings
      {
          RefreshMode = 'PUSH'
      }
      SignatureValidation validations{
          TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
          SignedItemType =  'Configuration','Module'
      }

  }
  EnableSignatureValidation
  Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
  ```

- Erstellen Sie eine Beispielkonfigurationsdatei.

  ```powershell
  # Sample configuration
  Configuration Test
  {

      File foo
      {
          DestinationPath =  "$env:TEMP\signingTest.txt"
          Contents = "ABC"
      }
  }
  Test
  ```

- Versuchen Sie, die nicht signierte Konfigurationsdatei mithilfe von Push auf den Knoten zu übertragen.

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](../images/DSC-improvements/PushUnsignedMof.png)

- Signieren Sie die Konfigurationsdatei mithilfe eines Codesignaturzertifikats.

  ![SignMofFile](../images/DSC-improvements/SignMofFile.png)

- Versuchen Sie, die signierte MOF-Datei mithilfe von Push zu übertragen.

  ![PushSignedMofFile](../images/DSC-improvements/PushSignedMof.png)
