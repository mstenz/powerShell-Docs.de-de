---
title: "Überprüfen der Signatur von DSC-Modulen und -Konfigurationen"
author: jaimeo
contributor: berheabra
translationtype: Human Translation
ms.sourcegitcommit: 5c97ca6e93d31aaffc7e2207facc7658ee36dfb4
ms.openlocfilehash: 817fadb79716e41ce8cc8f4245dedc66347ac413

---

##Überprüfen der Signatur von DSC-Modulen und -Konfigurationen
In DSC werden Konfigurationsdokumente und -module vom Pull-Server oder Pull-Servern (im Fall des Pull-Diensts von Azure Automation) an verwaltete Computer verteilt. Wenn der Pull-Server/-Dienst kompromittiert ist, kann ein Angreifer möglicherweise die Konfigurationen und Module auf dem Pull-Server ändern und sie anschließend an alle verwalteten Computer verteilen lassen, wodurch noch mehr Computer des Kunden gefährdet werden. 

 Auf diese Bedrohung wird in WMF 5.1 eingegangen. DSC unterstützt die Überprüfung der digitalen Signaturen in Modulen und Konfigurationsdateien (MOF-Dateien). Diese Funktion verhindert, dass Knoten eine Konfiguration oder Moduldateien ausführen, die nicht von einem vertrauenswürdigen Signaturgeber signiert oder die manipuliert wurden, nachdem der vertrauenswürdige Signaturgeber sie signiert hat. 



###So signieren Sie Konfigurationen und Module 
***
1. Konfigurationsdateien (MOF-Dateien): Das vorhandene PowerShell-Cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) wurde erweitert und unterstützt nun das Signieren von MOF-Dateien.  
2. Module:- Module werden signiert, indem der entsprechende Modulkatalog wie in den nachfolgenden Schritten erläutert signiert wird:- 
    * Erstellen einer Katalogdatei: Eine Katalogdatei enthält eine Sammlung kryptografischer Hashes oder Fingerabdrücke. Jeder Fingerabdruck entspricht einer Datei, die im Modul enthalten ist.  Mit dem neu hinzugefügten Cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) können Benutzer eine Katalogdatei für ihr Modul erstellen. Folgen Sie [diesem Link](catalog-cmdlets.md), wenn Sie mithilfe der Katalog-Cmdlets Katalogdateien erstellen möchten. 
    * Signieren der Katalogdatei: Mit [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) wird die Katalogdatei signiert.
    * Fügen Sie die Katalogdatei in den Modulordner ein.
Gemäß der Konvention sollte die Modulkatalogdatei mit dem gleichen Namen wie das Modul im Modulordner abgelegt werden.

###Einstellungen im lokalen Konfigurations-Manager (Local Configuration Manager; LCM) zur Aktivierung von Signaturüberprüfungen

####PULL
Der lokale Konfigurations-Manager eines Knotens überprüft die Signatur von Modulen und Konfigurationen auf Grundlage der aktuellen Einstellungen. Die Überprüfung der Signatur ist standardmäßig deaktiviert. Die Signaturüberprüfung kann aktiviert werden, indem Sie wie unten dargestellt den Block „SignatureValidation“ der Definition der Metakonfiguration des Knotens hinzufügen:-

```PowerShell
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
        # By default,LCM will use default Windows trusted publisher store to validate the certificate chain. If TrustedStorePath property is specified, LCM will use this custom store for retrieving the trusted publishers to validate the content.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'            
        SignedItemType =  'Configuration','Module'         # Those are list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.       
    }
 
}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose 
 ```

Die Festlegung der oben genannten Metakonfiguration auf einem Knoten aktiviert die Überprüfung der Signatur für heruntergeladene Konfigurationen und Module. Der lokale Konfigurations-Manager führt die folgenden Schritte aus, um die digitalen Signaturen zu überprüfen.
* Überprüfen, ob die Signatur einer Konfigurationsdatei (MOF) gültig ist. Der lokale Konfigurations-Manager verwendet das PowerShell-Cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), das in 5.1 zur Unterstützung der Überprüfung von MOF-Signaturen erweitert wurde.
* Überprüfen der Zertifizierungsstelle, die den Signaturgeber als vertrauenswürdig eingestuft hat.
* Herunterladen der Modul-/Ressourcenabhängigkeiten der Konfiguration in einen temporären Speicherort.
* Überprüfen der Signatur des Katalogs, der im Modul enthalten ist
    * Suchen einer „<moduleName>.cat“-Datei und Überprüfen der Signatur mithilfe des Cmdlets [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx)
    * Überprüfen der Zertifizierungsstelle, die den Signaturgeber als vertrauenswürdig eingestuft hat
    * Sicherstellen, dass der Inhalt der Module nicht mit dem neuen Cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) manipuliert wurde.
* Installieren des Moduls mithilfe des Cmdlets „Install-Module“ im Verzeichnis „$env:ProgramFiles\WindowsPowerShell\Modules\“
* Prozesskonfiguration

Hinweis: - Signaturen von Modulkatalogen und -konfigurationen werden nur bei der ersten Anwendung der Konfiguration auf das System überprüft, oder wenn das Modul heruntergeladen und installiert wird. Der Konsistenzlauf überprüft nicht die Signatur von „current.mof“ oder der Modulabhängigkeiten.
Wenn bei der Überprüfung zu irgendeinem Zeitpunkt ein Fehler auftritt, z.B. wenn die vom Pull-Server mithilfe von Pull übertragene Konfiguration nicht signiert ist, wird bei der Verarbeitung der Konfiguration der nachstehende Fehler ausgegeben, und alle temporären Dateien werden gelöscht.

![Beispielkonfiguration einer Fehlerausgabe](../../images/PullUnsignedConfigFail.PNG)

Entsprechend wird beim Übertragen eines Moduls mithilfe von Pull, dessen Katalog nicht signiert ist, der folgende Fehler ausgegeben:-

![Beispielmodul einer Fehlerausgabe](../../images/PullUnisgnedCatalog.PNG)

####PUSH
Eine Konfiguration, die über Push geliefert wurde, könnte an ihrer Quelle manipuliert worden sein, bevor sie an den Knoten geliefert wurde. Der lokale Konfigurations-Manager wird für mithilfe von Push übertragene oder veröffentlichte Konfigurationen ähnliche Schritte zur Überprüfung der Signatur durchführen.
Nachstehend finden Sie ein vollständiges Beispiel für die Signaturüberprüfung bei einer mithilfe von Push übertragenen Konfiguration.

* Aktivieren Sie die Überprüfung der Signatur auf dem Knoten.

```Powershell
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
* Erstellen Sie eine Beispielkonfigurationsdatei.

```Powershell
# Sample configuration
Configuration Test{

    File foo
    {
        DestinationPath =  "$env:TEMP\signingTest.txt"
        Contents = "ABC"
    }
}
Test
```

* Versuchen Sie, die nicht signierte Konfigurationsdatei mithilfe von Push auf den Knoten zu übertragen. 

```Powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
``` 
![ErrorUnsignedMofPushed](../../images/PushUnsignedMof.PNG)

* Signieren Sie die Konfigurationsdatei mithilfe eines Codesignaturzertifikats.

![SignMofFile](../../images/SignMofFile.PNG)

* Versuchen Sie, die signierte MOF-Datei mithilfe von Push zu übertragen.

![SignMofFile](../../images/PushSignedMof.PNG)




<!--HONumber=Aug16_HO3-->


