---
ms.date: 04/11/2018
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: Einrichten eines DSC-SMB-Pullservers
ms.openlocfilehash: be41f7a708f1a129919fae8300fc4307441097f7
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500702"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="799af-103">Einrichten eines DSC-SMB-Pullservers</span><span class="sxs-lookup"><span data-stu-id="799af-103">Setting up a DSC SMB pull server</span></span>

<span data-ttu-id="799af-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="799af-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="799af-105">Der Pull-Server (Windows-Feature *DSC-Dienst*) ist eine von Windows Server unterstützte Komponente, jedoch sollen keine neuen Features oder Funktionen angeboten werden.</span><span class="sxs-lookup"><span data-stu-id="799af-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="799af-106">Es wird empfohlen, verwaltete Clients auf [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) umzustellen (enthält Features zusätzlich zum Pull-Server unter Windows Server) oder auf eine der [hier](pullserver.md#community-solutions-for-pull-service) aufgeführten Communitylösungen.</span><span class="sxs-lookup"><span data-stu-id="799af-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="799af-107">Ein DSC-[SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11))-Pullserver ist ein Computer, der als Host einer SMB-Dateifreigabe fungiert, mit der DSC-Konfigurationsdateien und DSC-Ressourcen für Zielknoten zur Verfügung gestellt werden, wenn sie von diesen Knoten angefordert werden.</span><span class="sxs-lookup"><span data-stu-id="799af-107">A DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="799af-108">Zum Verwenden eines SMB-Pullservers für DSC müssen Sie folgende Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="799af-108">To use an SMB pull server for DSC, you have to:</span></span>

- <span data-ttu-id="799af-109">Einrichten einer SMB-Dateifreigabe auf einem Server mit PowerShell 4.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="799af-109">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="799af-110">Konfigurieren eines Clients mit PowerShell 4.0 oder höher zum Abrufen von dieser SMB-Freigabe</span><span class="sxs-lookup"><span data-stu-id="799af-110">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="799af-111">Verwenden der xSmbShare-Ressource zum Erstellen einer SMB-Dateifreigabe</span><span class="sxs-lookup"><span data-stu-id="799af-111">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="799af-112">Es gibt zahlreiche Methoden zum Einrichten einer SMB-Dateifreigabe. Im Folgenden wird die Methode unter Verwendung von DSC beschrieben.</span><span class="sxs-lookup"><span data-stu-id="799af-112">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="799af-113">Installieren der Ressource „xSmbShare“</span><span class="sxs-lookup"><span data-stu-id="799af-113">Install the xSmbShare resource</span></span>

<span data-ttu-id="799af-114">Rufen Sie das Cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module) auf, um das Modul **xSmbShare** zu installieren.</span><span class="sxs-lookup"><span data-stu-id="799af-114">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xSmbShare** module.</span></span>

> [!NOTE]
> <span data-ttu-id="799af-115">`Install-Module` ist im Modul **PowerShellGet** enthalten, das Bestandteil von PowerShell 5.0 ist.</span><span class="sxs-lookup"><span data-stu-id="799af-115">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span>
> <span data-ttu-id="799af-116">**xSmbShare** enthält die DSC-Ressource **xSmbShare**, mit der Sie eine SMB-Dateifreigabe erstellen können.</span><span class="sxs-lookup"><span data-stu-id="799af-116">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="799af-117">Erstellen des Verzeichnisses und der Dateifreigabe</span><span class="sxs-lookup"><span data-stu-id="799af-117">Create the directory and file share</span></span>

<span data-ttu-id="799af-118">Die folgende Konfiguration verwendet die **File**-Ressource zum Erstellen des Verzeichnisses für die Freigabe und die **xSmbShare**-Ressource zum Einrichten der SMB-Freigabe:</span><span class="sxs-lookup"><span data-stu-id="799af-118">The following configuration uses the **File** resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

```powershell
Configuration SmbShare
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

<span data-ttu-id="799af-119">Mit der Konfiguration wird das Verzeichnis `C:\DscSmbShare` erstellt, wenn es noch nicht vorhanden ist. Das Verzeichnis wird dann als SMB-Dateifreigabe verwendet.</span><span class="sxs-lookup"><span data-stu-id="799af-119">The configuration creates the directory `C:\DscSmbShare`, if it doesn't already exist, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="799af-120">Die Berechtigung **FullAccess** sollte jedem Konto gewährt werden, das in die Dateifreigabe schreiben oder aus dieser löschen muss.</span><span class="sxs-lookup"><span data-stu-id="799af-120">**FullAccess** should be given to any account that needs to write to or delete from the file share.</span></span> <span data-ttu-id="799af-121">Die Berechtigung **ReadAccess** muss allen Clientknoten gewährt werden, die Konfigurationen und bzw. oder DSC-Ressourcen von der Freigabe abrufen.</span><span class="sxs-lookup"><span data-stu-id="799af-121">**ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share.</span></span>

> [!NOTE]
> <span data-ttu-id="799af-122">DSC wird standardmäßig als das Systemkonto ausgeführt, der Computer selbst muss also über Zugriff auf die Freigabe verfügen.</span><span class="sxs-lookup"><span data-stu-id="799af-122">DSC runs as the system account by default, so the computer itself must have access to the share.</span></span>

### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="799af-123">Gewähren von Dateisystemzugriff für den Pullclient</span><span class="sxs-lookup"><span data-stu-id="799af-123">Give file system access to the pull client</span></span>

<span data-ttu-id="799af-124">Indem Sie einem Clientknoten **ReadAccess** gewähren, kann dieser Knoten auf die SMB-Freigabe zugreifen, aber nicht auf Dateien oder Ordner innerhalb der Freigabe.</span><span class="sxs-lookup"><span data-stu-id="799af-124">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="799af-125">Sie müssen Clientknoten explizit Zugriff auf den SMB-Freigabeordner und dessen Unterordner gewähren.</span><span class="sxs-lookup"><span data-stu-id="799af-125">You have to explicitly grant client nodes access to the SMB share folder and subfolders.</span></span> <span data-ttu-id="799af-126">In DSC erfolgt dies mithilfe der Ressource **cNtfsPermissionEntry**, die im Modul [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="799af-126">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span>
<span data-ttu-id="799af-127">Die folgende Konfiguration fügt einen **cNtfsPermissionEntry**-Block hinzu, der dem Pullclient „ReadAndExecute“-Zugriff gewährt:</span><span class="sxs-lookup"><span data-stu-id="799af-127">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

```powershell
Configuration DSCSMB
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare
    Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }

        cNtfsPermissionEntry PermissionSet1
        {
            Ensure = 'Present'
            Path = 'C:\DscSmbShare'
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

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="799af-128">Platzieren von Konfigurationen und Ressourcen</span><span class="sxs-lookup"><span data-stu-id="799af-128">Placing configurations and resources</span></span>

<span data-ttu-id="799af-129">Speichern Sie alle MOF-Konfigurationsdateien und/oder DSC-Ressourcen, die von Clientknoten per Pull abgerufen werden sollen, im SMB-Freigabeordner.</span><span class="sxs-lookup"><span data-stu-id="799af-129">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="799af-130">Alle MOF-Konfigurationsdateien müssen den Namen *ConfigurationID*.mof haben, wobei *ConfigurationID* der Wert der **ConfigurationID**-Eigenschaft des LCM des Zielknotens ist.</span><span class="sxs-lookup"><span data-stu-id="799af-130">Any configuration MOF file must be named *ConfigurationID*.mof, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="799af-131">Weitere Informationen zum Einrichten von Pullclients finden Sie unter [Einrichten eines DSC-Pullclients mithilfe einer Konfigurations-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="799af-131">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="799af-132">Sie müssen Konfigurations-IDs verwenden, wenn Sie einen SMB-Pullserver verwenden.</span><span class="sxs-lookup"><span data-stu-id="799af-132">You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="799af-133">Konfigurationsnamen werden für SMB nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="799af-133">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="799af-134">Jedes Ressourcenmodul muss komprimiert und entsprechend dem folgenden Muster benannt werden: `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="799af-134">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="799af-135">Ein Modul namens „xWebAdminstration“ mit einer Modulversion 3.1.2.0 würde beispielsweise „xWebAdministration_3.2.1.0.zip“ heißen.</span><span class="sxs-lookup"><span data-stu-id="799af-135">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="799af-136">Jede Version eines Moduls muss in einer eigenen ZIP-Datei enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="799af-136">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="799af-137">Separate Versionen eines Moduls in einer ZIP-Datei werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="799af-137">Separate versions of a module in a zip file are not supported.</span></span>
<span data-ttu-id="799af-138">Bevor Sie die DSC-Ressourcenmodule für die Verwendung mit einem Pullserver verpacken, müssen Sie eine kleine Änderung an der Verzeichnisstruktur vornehmen.</span><span class="sxs-lookup"><span data-stu-id="799af-138">Before packaging up DSC resource modules for use with pull server, you need to make a small change to the directory structure.</span></span>

<span data-ttu-id="799af-139">Das Standardformat für Module mit DSC-Ressourcen in WMF 5.0 ist `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="799af-139">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>

<span data-ttu-id="799af-140">Entfernen Sie vor dem Packvorgang für den Pullserver einfach den Ordner `{Module version}`, damit der Pfad zu `{Module Folder}\DscResources\{DSC Resource Folder}\` wird.</span><span class="sxs-lookup"><span data-stu-id="799af-140">Before packaging up for the pull server simply remove the `{Module version}` folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="799af-141">Komprimieren Sie den Ordner nach dieser Änderung wie oben beschrieben, und speichern Sie die ZIP-Dateien im SMB-Freigabeordner.</span><span class="sxs-lookup"><span data-stu-id="799af-141">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="799af-142">Erstellen der MOF-Prüfsumme</span><span class="sxs-lookup"><span data-stu-id="799af-142">Creating the MOF checksum</span></span>

<span data-ttu-id="799af-143">Eine MOF-Konfigurationsdatei muss einer Prüfsummendatei zugeordnet werden, damit ein LCM auf einem Zielknoten die Konfiguration überprüfen kann.</span><span class="sxs-lookup"><span data-stu-id="799af-143">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span> <span data-ttu-id="799af-144">Um eine Prüfsumme zu erstellen, rufen Sie das Cmdlet [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) auf.</span><span class="sxs-lookup"><span data-stu-id="799af-144">To create a checksum, call the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span></span> <span data-ttu-id="799af-145">Das Cmdlet verwendet einen `Path`-Parameter, der den Ordner angibt, in dem sich die MOF-Konfigurationsdatei befindet.</span><span class="sxs-lookup"><span data-stu-id="799af-145">The cmdlet takes a `Path` parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="799af-146">Das Cmdlet erstellt eine Prüfsummendatei mit dem Namen `ConfigurationMOFName.mof.checksum`, wobei `ConfigurationMOFName` der Name der MOF-Konfigurationsdatei ist.</span><span class="sxs-lookup"><span data-stu-id="799af-146">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span> <span data-ttu-id="799af-147">Wenn in dem angegebenen Ordner mehrere MOF-Konfigurationsdateien vorhanden sind, wird für jede Konfiguration im Ordner eine Prüfsumme erstellt.</span><span class="sxs-lookup"><span data-stu-id="799af-147">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="799af-148">Die Prüfsummendatei muss sich im gleichen Verzeichnis wie die MOF-Konfigurationsdatei befinden (standardmäßig `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration`). Sie muss den gleichen Namen mit der Erweiterung `.checksum` haben.</span><span class="sxs-lookup"><span data-stu-id="799af-148">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

> [!NOTE]
> <span data-ttu-id="799af-149">Wenn Sie die MOF-Konfigurationsdatei in irgendeiner Weise ändern, müssen Sie auch die Prüfsummendatei neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="799af-149">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="799af-150">Einrichten eines Pullclients für SMB</span><span class="sxs-lookup"><span data-stu-id="799af-150">Setting up a pull client for SMB</span></span>

<span data-ttu-id="799af-151">Zum Einrichten eines Clients, der Konfigurationen und/oder der Ressourcen von einer SMB-Freigabe abruft, konfigurieren Sie den lokalen Konfigurations-Manager (Local Configuration Manager, LCM) des Clients mit den Codeblöcken **ConfigurationRepositoryShare** und **ResourceRepositoryShare**, die die Freigabe angeben, aus der Pullkonfigurationen und DSC-Ressourcen abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="799af-151">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="799af-152">Weitere Informationen zum Konfigurieren des LCM finden Sie unter [Einrichten eines DSC-Pullclients mithilfe einer Konfigurations-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="799af-152">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="799af-153">Der Einfachheit halber wird in diesem Beispiel **PSDscAllowPlainTextPassword** verwendet, um die Übergabe eines Nur-Text-Kennworts an den Parameter **Credential** zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="799af-153">For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="799af-154">Informationen zur sicheren Weitergabe von Anmeldeinformationen finden Sie unter [Optionen für Anmeldeinformationen in den Konfigurationsdaten](../configurations/configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="799af-154">For information about passing credentials more securely, see [Credentials Options in Configuration Data](../configurations/configDataCredentials.md).</span></span> <span data-ttu-id="799af-155">Sie **MÜSSEN** eine **ConfigurationID** im Codeblock **Settings** einer Metakonfiguration für einen SMB-Pullserver eingeben, selbst wenn Sie nur Ressourcen abrufen.</span><span class="sxs-lookup"><span data-stu-id="799af-155">You **MUST** specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

```powershell
$secpasswd = ConvertTo-SecureString "Pass1Word" -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential ("TestUser", $secpasswd)

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

## <a name="acknowledgements"></a><span data-ttu-id="799af-156">Danksagung</span><span class="sxs-lookup"><span data-stu-id="799af-156">Acknowledgements</span></span>

<span data-ttu-id="799af-157">Besonderer Dank gilt den folgenden Personen:</span><span class="sxs-lookup"><span data-stu-id="799af-157">Special thanks to the following individuals:</span></span>

- <span data-ttu-id="799af-158">Mike F. Robbins, dessen Beiträge zur Verwendung von SMB für DSC beim Zusammenstellen des Inhalts in diesem Thema geholfen haben.</span><span class="sxs-lookup"><span data-stu-id="799af-158">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="799af-159">Seinen Blog finden Sie unter [Mike F Robbins](http://mikefrobbins.com/).</span><span class="sxs-lookup"><span data-stu-id="799af-159">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="799af-160">Serge Nikalaichyk, der das Modul **cNtfsAccessControl** erstellt hat.</span><span class="sxs-lookup"><span data-stu-id="799af-160">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="799af-161">Die Quelle für dieses Modul finden Sie unter [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span><span class="sxs-lookup"><span data-stu-id="799af-161">The source for this module is at [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span></span>

## <a name="see-also"></a><span data-ttu-id="799af-162">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="799af-162">See also</span></span>

[<span data-ttu-id="799af-163">Windows PowerShell DSC – Übersicht</span><span class="sxs-lookup"><span data-stu-id="799af-163">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)

[<span data-ttu-id="799af-164">Inkraftsetzung von Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="799af-164">Enacting configurations</span></span>](enactingConfigurations.md)

[<span data-ttu-id="799af-165">Einrichten eines Pullclients mithilfe einer Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="799af-165">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)
