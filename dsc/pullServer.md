# Einrichten eines DSC-Webpullservers

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Ein DSC-Webpullserver ist ein Webdienst in IIS, der eine OData-Schnittstelle verwendet, um DSC-Konfigurationsdateien für Zielknoten zur Verfügung zu stellen, wenn sie von diesen Knoten angefordert werden.

Anforderungen für die Verwendung eines Pullservers:

* Ein Server mit:
  - WMF/PowerShell 4.0 oder höher
  - IIS-Serverrolle
  - DSC-Dienst
* Im Idealfall eine Möglichkeit zum Generieren eines Zertifikats, um die an den lokalen Konfigurations-Manager (LCM) auf Zielknoten übergebenen Anmeldeinformationen abzusichern

Sie können die IIS-Serverrolle und den DSC-Dienst mit dem Assistenten zum Hinzufügen von Rollen und Features in Server Manager oder unter Verwendung von PowerShell hinzufügen. Die in diesem Thema enthaltenen Beispielskripts führen beide Schritte aus.

## Verwenden der xWebService-Ressource
Die einfachste Möglichkeit einen Webpullserver einzurichten, ist die Verwendung der Ressource „xWebService“ im Modul „xPSDesiredStateConfiguration“. Die folgenden Schritte erläutern, wie Sie die Ressource in einer Konfiguration verwenden, die den Webdienst einrichtet.

1. Rufen Sie das Cmdlet [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) auf, um das Modul **xPSDesiredStateConfiguration** zu installieren. **Hinweis**: **Install-Module** ist im Modul **PowerShellGet** enthalten, das Bestandteil von PowerShell 5.0 ist. Das Modul **PowerShellGet** für PowerShell 3.0 und 4.0 können Sie unter [PowerShell-Module „PackageManagement“ – Vorschau](https://www.microsoft.com/en-us/download/details.aspx?id=49186) herunterladen. 
1. Erstellen Sie ein selbstsigniertes Zertifikat mit dem Betreff `"CN=PSDSCPullServerCert"` im `CERT:\LocalMachine\MY\`-Speicher. Hierzu können Sie den Befehl `New-SelfSignedCertificate  -CertStoreLocation 'CERT:\LocalMachine\MY' -DnsName "PSDSCPullServerCert"` verwenden.
1. Starten Sie (F5) in PowerShell ISE das folgende Konfigurationsskript (enthalten im Beispielordner des Moduls **xPSDesiredStateConfiguration** als Sample_xDscWebService.ps1). Dieses Skript richtet den Pullserver und einen Kompatibilitätsserver ein.
  
```powershell
configuration Sample_xDscWebService 
6 { 
7     param  
8     ( 
9         [string[]]$NodeName = 'localhost', 
10 
 
11         [ValidateNotNullOrEmpty()] 
12         [string] $certificateThumbPrint 
13     ) 
14 
 
15     Import-DSCResource -ModuleName xPSDesiredStateConfiguration 
16 
 
17     Node $NodeName 
18     { 
19         WindowsFeature DSCServiceFeature 
20         { 
21             Ensure = "Present" 
22             Name   = "DSC-Service"             
23         } 
24 
 
25         xDscWebService PSDSCPullServer 
26         { 
27             Ensure                  = "Present" 
28             EndpointName            = "PSDSCPullServer" 
29             Port                    = 8080 
30             PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer" 
31             CertificateThumbPrint   = $certificateThumbPrint          
32             ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules" 
33             ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"             
34             State                   = "Started" 
35             DependsOn               = "[WindowsFeature]DSCServiceFeature"                         
36         } 
```

1. Führen Sie die Konfiguration aus, und übergeben Sie den Fingerabdruck des selbstsignierten Zertifikats, das Sie erstellt haben, mit dem Parameter **certificateThumbPrint**:

```powershell
PS:\>$myCert = Get-ChildItem CERT:\LocalMachine\My | Where-Object {$_.Subject -eq 'CN=PSDSCPullServerCert'}
PS:\>Sample_xDSCService -certificateThumbprint $myCert.Thumbprint 
```

## Registrierungsschlüssel
Um zuzulassen, dass Clientknoten sich beim Server registrieren und Konfigurationsnamen anstelle einer Konfigurations-ID verwenden können, muss ein Registrierungsschlüssel (eine GUID, die dem Server- und dem Clientknoten bekannt ist) in eine Datei namens `RegistrationKeys.txt` platziert werden. Standardmäßig erwartet der durch dieses Beispiel erstellte Pullserver die Datei unter `C:\Program Files\WindowsPowerShell\DscService`. Erstellen Sie eine Textdatei mit nur einer Zeile, die den Registrierungsschlüssel enthält, und speichern Sie sie in diesem Ordner.
> **Hinweis**: Registrierungsschlüssel werden in PowerShell 4.0 nicht unterstützt. 

## Platzieren von Konfigurationen und Ressourcen
Nach Abschluss des Setups des Pullservers ist unter `$env:PROGRAMFILES\WindowsPowerShell` ein neuer Ordner mit dem Namen „DscService“ vorhanden. Dieser Ordner enthält zwei Ordner mit den Namen „Module“ und „Konfiguration“. Platzieren Sie im Ordner „Module“ alle Ressourcen, die für Konfigurationen erforderlich sind, die von den Knoten per Pull von diesem Server abgerufen werden. Platzieren Sie im Ordner „Konfiguration“ die MOF-Konfigurationsdateien für alle Konfigurationen, die von Knoten abgerufen werden sollen. Die Namen der MOF-Dateien hängen vom Typ des Pullclients ab. In den folgenden Themen wird das Einrichten von Pullclients im Detail beschrieben:

* [Einrichten eines DSC-Pullclients mithilfe einer Konfigurations-ID](pullClientConfigID.md)
* [Einrichten eines DSC-Pullclients mithilfe von Konfigurationsnamen](pullClientConfigNames.md)
* [Teilkonfigurationen](partialConfigs.md)

## Erstellen der MOF-Prüfsumme
Eine MOF-Konfigurationsdatei muss einer Prüfsummendatei zugeordnet werden, damit ein LCM auf einem Zielknoten die Konfiguration überprüfen kann. Um eine Prüfsumme zu erstellen, rufen Sie das Cmdlet [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) auf. Das Cmdlet verwendet einen **Path**-Parameter, der den Ordner angibt, in dem sich die MOF-Konfigurationsdatei befindet. Das Cmdlet erstellt eine Prüfsummendatei mit dem Namen `ConfigurationMOFName.mof.checksum`, wobei `ConfigurationMOFName` der Name der MOF-Konfigurationsdatei ist. Wenn in dem angegebenen Ordner mehrere MOF-Konfigurationsdateien vorhanden sind, wird für jede Konfiguration im Ordner eine Prüfsumme erstellt.

Die Prüfsummendatei muss sich im gleichen Verzeichnis wie die MOF-Konfigurationsdatei befinden (standardmäßig `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration`). Sie muss den gleichen Namen mit der Erweiterung `.checksum` haben.

>**Hinweis**: Wenn Sie die MOF-Konfigurationsdatei in irgendeiner Weise ändern, müssen Sie auch die Prüfsummendatei neu erstellen.

## Siehe auch
* [Windows PowerShell DSC – Übersicht](overview.md)
* [Inkraftsetzung von Konfigurationen](enactingConfigurations.md)
* [Abrufen von Knoteninformationen vom DSC-Pullserver](retrieveNodeInfo.md)
<!--HONumber=Mar16_HO1-->
