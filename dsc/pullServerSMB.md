---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Einrichten eines DSC-SMB-Pullservers
ms.openlocfilehash: e9228c050d6f496e30e94404a564ed2e425a5412
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="6228e-103">Einrichten eines DSC-SMB-Pullservers</span><span class="sxs-lookup"><span data-stu-id="6228e-103">Setting up a DSC SMB pull server</span></span>

><span data-ttu-id="6228e-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6228e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="6228e-105">Ein DSC-[SMB](https://technet.microsoft.com/library/hh831795.aspx)-Pullserver ist ein Computer, der als Host einer SMB-Dateifreigabe fungiert, mit der DSC-Konfigurationsdateien und DSC-Ressourcen für Zielknoten zur Verfügung gestellt werden, wenn sie von diesen Knoten angefordert werden.</span><span class="sxs-lookup"><span data-stu-id="6228e-105">A DSC [SMB](https://technet.microsoft.com/library/hh831795.aspx) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="6228e-106">Zum Verwenden eines SMB-Pullservers für DSC müssen Sie folgende Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="6228e-106">To use an SMB pull server for DSC, you have to:</span></span>
- <span data-ttu-id="6228e-107">Einrichten einer SMB-Dateifreigabe auf einem Server mit PowerShell 4.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="6228e-107">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="6228e-108">Konfigurieren eines Clients mit PowerShell 4.0 oder höher zum Abrufen von dieser SMB-Freigabe</span><span class="sxs-lookup"><span data-stu-id="6228e-108">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="6228e-109">Verwenden der xSmbShare-Ressource zum Erstellen einer SMB-Dateifreigabe</span><span class="sxs-lookup"><span data-stu-id="6228e-109">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="6228e-110">Es gibt zahlreiche Methoden zum Einrichten einer SMB-Dateifreigabe. Im Folgenden wird die Methode unter Verwendung von DSC beschrieben.</span><span class="sxs-lookup"><span data-stu-id="6228e-110">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="6228e-111">Installieren der Ressource „xSmbShare“</span><span class="sxs-lookup"><span data-stu-id="6228e-111">Install the xSmbShare resource</span></span>

<span data-ttu-id="6228e-112">Rufen Sie das Cmdlet [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) auf, um das Modul **xSmbShare** zu installieren.</span><span class="sxs-lookup"><span data-stu-id="6228e-112">Call the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to install the **xSmbShare** module.</span></span>
><span data-ttu-id="6228e-113">**Hinweis**: **Install-Module** ist im Modul **PowerShellGet** enthalten, das Bestandteil von PowerShell 5.0 ist.</span><span class="sxs-lookup"><span data-stu-id="6228e-113">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="6228e-114">Das Modul **PowerShellGet** für PowerShell 3.0 und 4.0 können Sie unter [PowerShell-Module „PackageManagement“ – Vorschau](https://www.microsoft.com/en-us/download/details.aspx?id=49186) herunterladen.</span><span class="sxs-lookup"><span data-stu-id="6228e-114">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> <span data-ttu-id="6228e-115">**xSmbShare** enthält die DSC-Ressource **xSmbShare**, mit der Sie eine SMB-Dateifreigabe erstellen können.</span><span class="sxs-lookup"><span data-stu-id="6228e-115">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="6228e-116">Erstellen des Verzeichnisses und der Dateifreigabe</span><span class="sxs-lookup"><span data-stu-id="6228e-116">Create the directory and file share</span></span>

<span data-ttu-id="6228e-117">Die folgende Konfiguration verwendet die [File](fileResource.md)-Ressource zum Erstellen des Verzeichnisses für die Freigabe und die **xSmbShare**-Ressource zum Einrichten der SMB-Freigabe:</span><span class="sxs-lookup"><span data-stu-id="6228e-117">The following configuration uses the [File](fileResource.md) resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

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

<span data-ttu-id="6228e-118">Die Konfiguration erstellt das Verzeichnis `C:\DscSmbShare`, wenn es noch nicht vorhanden ist, und verwendet dieses Verzeichnis anschließend als SMB-Dateifreigabe.</span><span class="sxs-lookup"><span data-stu-id="6228e-118">The configuration creates the directory `C:\DscSmbShare` if it doesn't already exists, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="6228e-119">Jedes Konto, das in die Dateifreigabe schreiben oder Elemente daraus löschen können muss, sollte **FullAccess** erhalten, und allen Clientknoten, die Konfigurationen und/oder DSC-Ressourcen aus dieser Freigabe erhalten, **ReadAccess** gewährt werden (da DSC standardmäßig als Systemkonto ausgeführt wird, daher muss der Computer selbst auf die Freigabe zugreifen können).</span><span class="sxs-lookup"><span data-stu-id="6228e-119">**FullAccess** should be given to any account that needs to write to or delete from the file share, and **ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share ( this is because DSC runs as the system account by default, so the computer itself has to have access to the share).</span></span>


### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="6228e-120">Gewähren von Dateisystemzugriff für den Pullclient</span><span class="sxs-lookup"><span data-stu-id="6228e-120">Give file system access to the pull client</span></span>

<span data-ttu-id="6228e-121">Indem Sie einem Clientknoten **ReadAccess** gewähren, kann dieser Knoten auf die SMB-Freigabe zugreifen, aber nicht auf Dateien oder Ordner innerhalb der Freigabe.</span><span class="sxs-lookup"><span data-stu-id="6228e-121">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="6228e-122">Sie müssen Clientknoten explizit Zugriff auf den SMB-Freigabeordner und dessen Unterordner gewähren.</span><span class="sxs-lookup"><span data-stu-id="6228e-122">You have to explicitly grant client nodes access to the SMB share folder and sub-folders.</span></span> <span data-ttu-id="6228e-123">In DSC erfolgt dies mithilfe der Ressource **cNtfsPermissionEntry**, die im Modul [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="6228e-123">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="6228e-124">Die folgende Konfiguration fügt einen **cNtfsPermissionEntry**-Block hinzu, der dem Pullclient „ReadAndExecute“-Zugriff gewährt:</span><span class="sxs-lookup"><span data-stu-id="6228e-124">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

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

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="6228e-125">Platzieren von Konfigurationen und Ressourcen</span><span class="sxs-lookup"><span data-stu-id="6228e-125">Placing configurations and resources</span></span>

<span data-ttu-id="6228e-126">Speichern Sie alle MOF-Konfigurationsdateien und/oder DSC-Ressourcen, die von Clientknoten per Pull abgerufen werden sollen, im SMB-Freigabeordner.</span><span class="sxs-lookup"><span data-stu-id="6228e-126">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="6228e-127">Alle MOF-Konfigurationsdateien müssen den Namen _ConfigurationID_.mof haben, wobei _ConfigurationID_ der Wert der **ConfigurationID**-Eigenschaft des LCM des Zielknotens ist.</span><span class="sxs-lookup"><span data-stu-id="6228e-127">Any configuration MOF file must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="6228e-128">Weitere Informationen zum Einrichten von Pullclients finden Sie unter [Einrichten eines DSC-Pullclients mithilfe einer Konfigurations-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="6228e-128">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

><span data-ttu-id="6228e-129">**Hinweis:** Sie müssen Konfigurations-IDs verwenden, wenn Sie einen SMB-Pullserver verwenden.</span><span class="sxs-lookup"><span data-stu-id="6228e-129">**Note:** You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="6228e-130">Konfigurationsnamen werden für SMB nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6228e-130">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="6228e-131">Jedes Ressourcenmodul muss komprimiert und entsprechend dem folgenden Muster benannt werden: `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="6228e-131">Each resource module needs to be zipped and named according the the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="6228e-132">Ein Modul namens „xWebAdminstration“ mit einer Modulversion 3.1.2.0 würde beispielsweise „xWebAdministration_3.2.1.0.zip“ heißen.</span><span class="sxs-lookup"><span data-stu-id="6228e-132">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="6228e-133">Jede Version eines Moduls muss in einer eigenen ZIP-Datei enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="6228e-133">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="6228e-134">Da jede ZIP-Datei nur jeweils eine Version einer Ressource enthält, wird das in WMF 5.0 eingeführte das Modulformat, das mehrere Versionen in einem einzigen Verzeichnis ermöglicht, nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6228e-134">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="6228e-135">Das bedeutet, dass Sie vor dem Packen von DSC-Ressourcenmodulen für die Verwendung mit einem Pullserver eine kleine Änderung an der Verzeichnisstruktur vornehmen müssen.</span><span class="sxs-lookup"><span data-stu-id="6228e-135">This means that before packaging up DSC resource modules for use with pull server you need to make a small change to the directory structure.</span></span> <span data-ttu-id="6228e-136">Das Standardformat für Module mit DSC-Ressourcen in WMF 5.0 ist: {Modulordner}\{Modulversion}\DscResources\{DSC-Ressourcenordner}\'.</span><span class="sxs-lookup"><span data-stu-id="6228e-136">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="6228e-137">Entfernen Sie vor dem Packen für den Pullserver einfach den Ordner **{Modulversion}**, damit der Pfad wie folgt geändert wird: {Modulordner}\DscResources\{DSC-Ressourcenordner}\'.</span><span class="sxs-lookup"><span data-stu-id="6228e-137">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="6228e-138">Komprimieren Sie den Ordner nach dieser Änderung wie oben beschrieben, und speichern Sie die ZIP-Dateien im SMB-Freigabeordner.</span><span class="sxs-lookup"><span data-stu-id="6228e-138">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="6228e-139">Erstellen der MOF-Prüfsumme</span><span class="sxs-lookup"><span data-stu-id="6228e-139">Creating the MOF checksum</span></span>
<span data-ttu-id="6228e-140">Eine MOF-Konfigurationsdatei muss einer Prüfsummendatei zugeordnet werden, damit ein LCM auf einem Zielknoten die Konfiguration überprüfen kann.</span><span class="sxs-lookup"><span data-stu-id="6228e-140">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="6228e-141">Um eine Prüfsumme zu erstellen, rufen Sie das Cmdlet [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) auf.</span><span class="sxs-lookup"><span data-stu-id="6228e-141">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span> <span data-ttu-id="6228e-142">Das Cmdlet verwendet einen **Path**-Parameter, der den Ordner angibt, in dem sich die MOF-Konfigurationsdatei befindet.</span><span class="sxs-lookup"><span data-stu-id="6228e-142">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="6228e-143">Das Cmdlet erstellt eine Prüfsummendatei mit dem Namen `ConfigurationMOFName.mof.checksum`, wobei `ConfigurationMOFName` der Name der MOF-Konfigurationsdatei ist.</span><span class="sxs-lookup"><span data-stu-id="6228e-143">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="6228e-144">Wenn in dem angegebenen Ordner mehrere MOF-Konfigurationsdateien vorhanden sind, wird für jede Konfiguration im Ordner eine Prüfsumme erstellt.</span><span class="sxs-lookup"><span data-stu-id="6228e-144">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="6228e-145">Die Prüfsummendatei muss sich im gleichen Verzeichnis wie die MOF-Konfigurationsdatei befinden (standardmäßig `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration`). Sie muss den gleichen Namen mit der Erweiterung `.checksum` haben.</span><span class="sxs-lookup"><span data-stu-id="6228e-145">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

><span data-ttu-id="6228e-146">**Hinweis**: Wenn Sie die MOF-Konfigurationsdatei in irgendeiner Weise ändern, müssen Sie auch die Prüfsummendatei neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="6228e-146">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="6228e-147">Einrichten eines Pullclients für SMB</span><span class="sxs-lookup"><span data-stu-id="6228e-147">Setting up a pull client for SMB</span></span>

<span data-ttu-id="6228e-148">Zum Einrichten eines Clients, der Konfigurationen und/oder der Ressourcen von einer SMB-Freigabe abruft, konfigurieren Sie den lokalen Konfigurations-Manager (Local Configuration Manager, LCM) des Clients mit den Codeblöcken **ConfigurationRepositoryShare** und **ResourceRepositoryShare**, die die Freigabe angeben, aus der Pullkonfigurationen und DSC-Ressourcen abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="6228e-148">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="6228e-149">Weitere Informationen zum Konfigurieren des LCM finden Sie unter [Einrichten eines DSC-Pullclients mithilfe einer Konfigurations-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="6228e-149">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

><span data-ttu-id="6228e-150">**Hinweis:** Der Einfachheit halber wird in diesem Beispiel **PSDscAllowPlainTextPassword** verwendet, um ein Nur-Text-Kennwort an den Parameter **Anmeldeinformationen** zu übergeben.</span><span class="sxs-lookup"><span data-stu-id="6228e-150">**Note:** For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="6228e-151">Informationen zur sicheren Weitergabe von Anmeldeinformationen finden Sie unter [Optionen für Anmeldeinformationen in den Konfigurationsdaten](configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="6228e-151">For information about passing credentials more securely, see [Credentials Options in Configuration Data](configDataCredentials.md).</span></span>

><span data-ttu-id="6228e-152">**Hinweis:** Geben Sie eine **Konfigurations-ID** im Codeblock **Einstellungen** einer Metakonfiguration für einen SMB-Pullserver ein, selbst wenn Sie nur Ressourcen abrufen.</span><span class="sxs-lookup"><span data-stu-id="6228e-152">**Note:** You must specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

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

## <a name="acknowledgements"></a><span data-ttu-id="6228e-153">Bestätigungen</span><span class="sxs-lookup"><span data-stu-id="6228e-153">Acknowledgements</span></span>

<span data-ttu-id="6228e-154">Besonderer Dank geht an folgende Personen:</span><span class="sxs-lookup"><span data-stu-id="6228e-154">Special thanks to the following:</span></span>

- <span data-ttu-id="6228e-155">Mike F. Robbins, dessen Beiträge zur Verwendung von SMB für DSC beim Zusammenstellen des Inhalts in diesem Thema geholfen haben.</span><span class="sxs-lookup"><span data-stu-id="6228e-155">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="6228e-156">Seinen Blog finden Sie unter [Mike F Robbins](http://mikefrobbins.com/).</span><span class="sxs-lookup"><span data-stu-id="6228e-156">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="6228e-157">Serge Nikalaichyk, der das Modul **cNtfsAccessControl** erstellt hat.</span><span class="sxs-lookup"><span data-stu-id="6228e-157">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="6228e-158">Die Quelle für dieses Modul finden Sie unter https://github.com/SNikalaichyk/cNtfsAccessControl.</span><span class="sxs-lookup"><span data-stu-id="6228e-158">The source for this module is at https://github.com/SNikalaichyk/cNtfsAccessControl.</span></span>

## <a name="see-also"></a><span data-ttu-id="6228e-159">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="6228e-159">See also</span></span>
- [<span data-ttu-id="6228e-160">Windows PowerShell DSC – Übersicht</span><span class="sxs-lookup"><span data-stu-id="6228e-160">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="6228e-161">Inkraftsetzung von Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="6228e-161">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="6228e-162">Einrichten eines Pullclients mithilfe einer Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="6228e-162">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)