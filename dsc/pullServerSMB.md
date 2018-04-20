---
ms.date: 04/11/2018
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Einrichten eines DSC-SMB-Pullservers
ms.openlocfilehash: e4e313746e95af86c5d17a8de0549451b1399b6c
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="setting-up-a-dsc-smb-pull-server"></a>Einrichten eines DSC-SMB-Pullservers

>Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Der Pull-Server (Windows-Feature *DSC-Dienst*) ist eine von Windows Server unterstützte Komponente, jedoch sollen keine neuen Features oder Funktionen angeboten werden. Es wird empfohlen, verwaltete Clients auf [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) umzustellen (enthält Features zusätzlich zu Pull-Server unter Windows Server) oder auf eine der [hier](pullserver.md#community-solutions-for-pull-service) aufgeführten Communitylösungen.

Ein DSC-[SMB](https://technet.microsoft.com/library/hh831795.aspx)-Pullserver ist ein Computer, der als Host einer SMB-Dateifreigabe fungiert, mit der DSC-Konfigurationsdateien und DSC-Ressourcen für Zielknoten zur Verfügung gestellt werden, wenn sie von diesen Knoten angefordert werden.

Zum Verwenden eines SMB-Pullservers für DSC müssen Sie folgende Schritte ausführen:
- Einrichten einer SMB-Dateifreigabe auf einem Server mit PowerShell 4.0 oder höher
- Konfigurieren eines Clients mit PowerShell 4.0 oder höher zum Abrufen von dieser SMB-Freigabe

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>Verwenden der xSmbShare-Ressource zum Erstellen einer SMB-Dateifreigabe

Es gibt zahlreiche Methoden zum Einrichten einer SMB-Dateifreigabe. Im Folgenden wird die Methode unter Verwendung von DSC beschrieben.

### <a name="install-the-xsmbshare-resource"></a>Installieren der Ressource „xSmbShare“

Rufen Sie das Cmdlet [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) auf, um das Modul **xSmbShare** zu installieren.
>**Hinweis**: **Install-Module** ist im Modul **PowerShellGet** enthalten, das Bestandteil von PowerShell 5.0 ist. Das Modul **PowerShellGet** für PowerShell 3.0 und 4.0 können Sie unter [PowerShell-Module „PackageManagement“ – Vorschau](https://www.microsoft.com/en-us/download/details.aspx?id=49186) herunterladen. **xSmbShare** enthält die DSC-Ressource **xSmbShare**, mit der Sie eine SMB-Dateifreigabe erstellen können.

### <a name="create-the-directory-and-file-share"></a>Erstellen des Verzeichnisses und der Dateifreigabe

Die folgende Konfiguration verwendet die [File](fileResource.md)-Ressource zum Erstellen des Verzeichnisses für die Freigabe und die **xSmbShare**-Ressource zum Einrichten der SMB-Freigabe:

```powershell
Configuration SmbShare {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare

    Node localhost {

        File CreateFolder {

            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'

        }

        xSMBShare CreateShare {

            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'admininstrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'

        }

    }

}
```

Die Konfiguration erstellt das Verzeichnis `C:\DscSmbShare`, wenn es noch nicht vorhanden ist, und verwendet dieses Verzeichnis anschließend als SMB-Dateifreigabe. Jedes Konto, das in die Dateifreigabe schreiben oder Elemente daraus löschen können muss, sollte **FullAccess** erhalten, und allen Clientknoten, die Konfigurationen und/oder DSC-Ressourcen aus dieser Freigabe erhalten, **ReadAccess** gewährt werden (da DSC standardmäßig als Systemkonto ausgeführt wird, daher muss der Computer selbst auf die Freigabe zugreifen können).


### <a name="give-file-system-access-to-the-pull-client"></a>Gewähren von Dateisystemzugriff für den Pullclient

Indem Sie einem Clientknoten **ReadAccess** gewähren, kann dieser Knoten auf die SMB-Freigabe zugreifen, aber nicht auf Dateien oder Ordner innerhalb der Freigabe. Sie müssen Clientknoten explizit Zugriff auf den SMB-Freigabeordner und dessen Unterordner gewähren. In DSC erfolgt dies mithilfe der Ressource **cNtfsPermissionEntry**, die im Modul [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) enthalten ist. Die folgende Konfiguration fügt einen **cNtfsPermissionEntry**-Block hinzu, der dem Pullclient „ReadAndExecute“-Zugriff gewährt:

```powershell
Configuration DSCSMB {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare
Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost {

        File CreateFolder {

            DestinationPath = 'DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'

        }

        xSMBShare CreateShare {

            Name = 'DscSmbShare'
            Path = 'DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'

        }

        cNtfsPermissionEntry PermissionSet1 {

        Ensure = 'Present'
        Path = 'C:\DSCSMB'
        Principal = 'myDomain\Contoso-Server$'
        AccessControlInformation = @(
            cNtfsAccessControlInformation
            {
                AccessControlType = 'Allow'
                FileSystemRights = 'ReadAndExecute'
                Inheritance = 'ThisFolderSubfoldersAndFiles'
                NoPropagateInherit = $false
            }
        )
        DependsOn = '[File]CreateFolder'

        }


    }

}
```

## <a name="placing-configurations-and-resources"></a>Platzieren von Konfigurationen und Ressourcen

Speichern Sie alle MOF-Konfigurationsdateien und/oder DSC-Ressourcen, die von Clientknoten per Pull abgerufen werden sollen, im SMB-Freigabeordner.

Alle MOF-Konfigurationsdateien müssen den Namen _ConfigurationID_.mof haben, wobei _ConfigurationID_ der Wert der **ConfigurationID**-Eigenschaft des LCM des Zielknotens ist. Weitere Informationen zum Einrichten von Pullclients finden Sie unter [Einrichten eines DSC-Pullclients mithilfe einer Konfigurations-ID](pullClientConfigID.md).

>**Hinweis:** Sie müssen Konfigurations-IDs verwenden, wenn Sie einen SMB-Pullserver verwenden. Konfigurationsnamen werden für SMB nicht unterstützt.

Jedes Ressourcenmodul muss komprimiert und entsprechend dem folgenden Muster benannt werden: `{Module Name}_{Module Version}.zip`. Ein Modul namens „xWebAdminstration“ mit einer Modulversion 3.1.2.0 würde beispielsweise „xWebAdministration_3.2.1.0.zip“ heißen. Jede Version eines Moduls muss in einer eigenen ZIP-Datei enthalten sein. Da jede ZIP-Datei nur jeweils eine Version einer Ressource enthält, wird das in WMF 5.0 eingeführte das Modulformat, das mehrere Versionen in einem einzigen Verzeichnis ermöglicht, nicht unterstützt. Das bedeutet, dass Sie vor dem Packen von DSC-Ressourcenmodulen für die Verwendung mit einem Pullserver eine kleine Änderung an der Verzeichnisstruktur vornehmen müssen. Das Standardformat für Module mit DSC-Ressourcen in WMF 5.0 ist: {Modulordner}\{Modulversion}\DscResources\{DSC-Ressourcenordner}\'. Entfernen Sie vor dem Packen für den Pullserver einfach den Ordner **{Modulversion}**, damit der Pfad wie folgt geändert wird: {Modulordner}\DscResources\{DSC-Ressourcenordner}\'. Komprimieren Sie den Ordner nach dieser Änderung wie oben beschrieben, und speichern Sie die ZIP-Dateien im SMB-Freigabeordner.

## <a name="creating-the-mof-checksum"></a>Erstellen der MOF-Prüfsumme
Eine MOF-Konfigurationsdatei muss einer Prüfsummendatei zugeordnet werden, damit ein LCM auf einem Zielknoten die Konfiguration überprüfen kann.
Um eine Prüfsumme zu erstellen, rufen Sie das Cmdlet [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) auf. Das Cmdlet verwendet einen **Path**-Parameter, der den Ordner angibt, in dem sich die MOF-Konfigurationsdatei befindet. Das Cmdlet erstellt eine Prüfsummendatei mit dem Namen `ConfigurationMOFName.mof.checksum`, wobei `ConfigurationMOFName` der Name der MOF-Konfigurationsdatei ist.
Wenn in dem angegebenen Ordner mehrere MOF-Konfigurationsdateien vorhanden sind, wird für jede Konfiguration im Ordner eine Prüfsumme erstellt.

Die Prüfsummendatei muss sich im gleichen Verzeichnis wie die MOF-Konfigurationsdatei befinden (standardmäßig `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration`). Sie muss den gleichen Namen mit der Erweiterung `.checksum` haben.

>**Hinweis**: Wenn Sie die MOF-Konfigurationsdatei in irgendeiner Weise ändern, müssen Sie auch die Prüfsummendatei neu erstellen.

## <a name="setting-up-a-pull-client-for-smb"></a>Einrichten eines Pullclients für SMB

Zum Einrichten eines Clients, der Konfigurationen und/oder der Ressourcen von einer SMB-Freigabe abruft, konfigurieren Sie den lokalen Konfigurations-Manager (Local Configuration Manager, LCM) des Clients mit den Codeblöcken **ConfigurationRepositoryShare** und **ResourceRepositoryShare**, die die Freigabe angeben, aus der Pullkonfigurationen und DSC-Ressourcen abgerufen werden sollen.

Weitere Informationen zum Konfigurieren des LCM finden Sie unter [Einrichten eines DSC-Pullclients mithilfe einer Konfigurations-ID](pullClientConfigID.md).

>**Hinweis:** Der Einfachheit halber wird in diesem Beispiel **PSDscAllowPlainTextPassword** verwendet, um ein Nur-Text-Kennwort an den Parameter **Anmeldeinformationen** zu übergeben. Informationen zur sicheren Weitergabe von Anmeldeinformationen finden Sie unter [Optionen für Anmeldeinformationen in den Konfigurationsdaten](configDataCredentials.md).

>**Hinweis:** Geben Sie eine **Konfigurations-ID** im Codeblock **Einstellungen** einer Metakonfiguration für einen SMB-Pullserver ein, selbst wenn Sie nur Ressourcen abrufen.

```powershell
$secpasswd = ConvertTo-SecureString “Pass1Word” -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential (“TestUser”, $secpasswd)

[DSCLocalConfigurationManager()]
configuration SmbCredTest
{
    Node $AllNodes.NodeName
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
            ConfigurationID    = '16db7357-9083-4806-a80c-ebbaf4acd6c1'
        }

         ConfigurationRepositoryShare SmbConfigShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds
        }

        ResourceRepositoryShare SmbResourceShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds

        }
    }
}

$ConfigurationData = @{

    AllNodes = @(

        @{

            #the "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves

            NodeName="localhost"

            PSDscAllowPlainTextPassword = $true

        })



}
```

## <a name="acknowledgements"></a>Bestätigungen

Besonderer Dank geht an folgende Personen:

- Mike F. Robbins, dessen Beiträge zur Verwendung von SMB für DSC beim Zusammenstellen des Inhalts in diesem Thema geholfen haben. Seinen Blog finden Sie unter [Mike F Robbins](http://mikefrobbins.com/).
- Serge Nikalaichyk, der das Modul **cNtfsAccessControl** erstellt hat. Die Quelle für dieses Modul finden Sie unter https://github.com/SNikalaichyk/cNtfsAccessControl.

## <a name="see-also"></a>Siehe auch
- [Windows PowerShell DSC – Übersicht](overview.md)
- [Inkraftsetzung von Konfigurationen](enactingConfigurations.md)
- [Einrichten eines Pullclients mithilfe einer Konfigurations-ID](pullClientConfigID.md)