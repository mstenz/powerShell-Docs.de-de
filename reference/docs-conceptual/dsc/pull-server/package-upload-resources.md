---
ms.date: 12/12/2018
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: Verpacken und Hochladen von Ressourcen auf einen Pullserver
ms.openlocfilehash: 8aac343d7495ecda94ed76d1d97079397eecd65f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278499"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="db8a8-103">Verpacken und Hochladen von Ressourcen auf einen Pullserver</span><span class="sxs-lookup"><span data-stu-id="db8a8-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="db8a8-104">Die folgenden Abschnitte gehen davon aus, dass Sie bereits einen Pullserver eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="db8a8-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="db8a8-105">Wenn Sie noch keinen Pullserver eingerichtet haben, können Sie die folgenden Anleitungen verwenden:</span><span class="sxs-lookup"><span data-stu-id="db8a8-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="db8a8-106">Einrichten eines DSC-SMB-Pullservers</span><span class="sxs-lookup"><span data-stu-id="db8a8-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="db8a8-107">Einrichten eines DSC-HTTP-Pullservers</span><span class="sxs-lookup"><span data-stu-id="db8a8-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="db8a8-108">Jeder Zielknoten kann zum Herunterladen von Konfigurationen, Ressourcen und sogar zum Berichten seines Status konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="db8a8-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="db8a8-109">Dieser Artikel zeigt Ihnen, wie Sie Ressourcen hochladen können, damit sie zum Download zur Verfügung stehen, und wie Sie Clients so konfigurieren, dass sie Ressourcen automatisch herunterladen.</span><span class="sxs-lookup"><span data-stu-id="db8a8-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="db8a8-110">Wenn der Knoten eine zugewiesene Konfiguration empfängt (durch **Pull** oder **Push** (v5)), lädt er automatisch alle für die Konfiguration erforderlichen Ressourcen vom in LCM angegebenen Speicherort herunter.</span><span class="sxs-lookup"><span data-stu-id="db8a8-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="db8a8-111">Verpacken von Ressourcenmodulen</span><span class="sxs-lookup"><span data-stu-id="db8a8-111">Package Resource Modules</span></span>

<span data-ttu-id="db8a8-112">Jede Ressource, die für einen Client zum Herunterladen verfügbar ist, muss in einer ZIP-Datei gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="db8a8-112">Each resource available for a client to download must be stored in a ".zip" file.</span></span> <span data-ttu-id="db8a8-113">Das folgende Beispiel zeigt die erforderlichen Schritte unter Verwendung der Ressource [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0).</span><span class="sxs-lookup"><span data-stu-id="db8a8-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="db8a8-114">Wenn ein Client PowerShell 4.0 verwendet, müssen Sie die Ressourcenordnerstruktur vereinfachen und alle Versionsordner entfernen.</span><span class="sxs-lookup"><span data-stu-id="db8a8-114">If you have any clients using PowerShell 4.0, you will need to flaten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="db8a8-115">Weitere Informationen finden Sie unter [Mehrere Ressourcenversionen](../configurations/import-dscresource.md#multiple-resource-versions).</span><span class="sxs-lookup"><span data-stu-id="db8a8-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="db8a8-116">Sie können das Ressourcenverzeichnis mit einem beliebigen Hilfsprogramm, einem Skript oder einer beliebigen Methode komprimieren.</span><span class="sxs-lookup"><span data-stu-id="db8a8-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="db8a8-117">Unter Windows können Sie *mit der rechten Maustaste* auf das Verzeichnis „xPSDesiredStateConfiguration“ klicken und dann „Senden an“ und „Komprimierter Ordner“ auswählen.</span><span class="sxs-lookup"><span data-stu-id="db8a8-117">In Windows, you can *right-click* on the "xPSDesiredStateConfiguration" directory, and select "Send To", then "Compressed Folder".</span></span>

![Rechtsklick](media/package-upload-resources/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="db8a8-119">Benennen des Ressourcenarchivs</span><span class="sxs-lookup"><span data-stu-id="db8a8-119">Naming the Resource Archive</span></span>

<span data-ttu-id="db8a8-120">Das Ressourcenarchiv muss im folgenden Format benannt werden:</span><span class="sxs-lookup"><span data-stu-id="db8a8-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="db8a8-121">Im Beispiel oben sollte „xPSDesiredStateConfiguration.zip“ in „xPSDesiredStateConfiguration_8.4.4.0.zip“ umbenannt werden.</span><span class="sxs-lookup"><span data-stu-id="db8a8-121">In the example above, "xPSDesiredStateConfiguration.zip" should be renamed "xPSDesiredStateConfiguration_8.4.4.0.zip".</span></span>

### <a name="create-checksums"></a><span data-ttu-id="db8a8-122">Erstellen von Prüfsummen</span><span class="sxs-lookup"><span data-stu-id="db8a8-122">Create CheckSums</span></span>

<span data-ttu-id="db8a8-123">Sobald das Ressourcenmodul komprimiert und umbenannt wurde, müssen Sie eine **Prüfsumme** erstellen.</span><span class="sxs-lookup"><span data-stu-id="db8a8-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span>  <span data-ttu-id="db8a8-124">Die **CheckSum** wird von LCM auf dem Client verwendet, um festzustellen, ob die Ressource geändert wurde und erneut heruntergeladen werden muss.</span><span class="sxs-lookup"><span data-stu-id="db8a8-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="db8a8-125">Sie können mit dem Cmdlet **New-DSCCheckSum** eine [CheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) erstellen, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="db8a8-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="db8a8-126">Es wird keine Ausgabe angezeigt, aber Sie sollten nun eine „xPSDesiredStateConfiguration_8.4.4.4.4.0.zip.zip.checksum“ vorfinden.</span><span class="sxs-lookup"><span data-stu-id="db8a8-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="db8a8-127">Sie können auch `New-DSCCheckSum` für ein Verzeichnis mit Dateien mit dem Parameter `-Path` ausführen.</span><span class="sxs-lookup"><span data-stu-id="db8a8-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="db8a8-128">Wenn bereits eine Prüfsumme vorhanden ist, können Sie mit dem Parameter `-Force` erzwingen, dass sie neu erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="db8a8-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="db8a8-129">Speicherort für Ressourcenarchive</span><span class="sxs-lookup"><span data-stu-id="db8a8-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="db8a8-130">Auf einem DSC-HTTP-Pullserver</span><span class="sxs-lookup"><span data-stu-id="db8a8-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="db8a8-131">Wenn Sie Ihren HTTP-Pullserver einrichten (wie unter [Einrichten eines DSC-HTTP-Pullservers](pullServer.md) beschrieben), geben Sie Verzeichnisse für die Schlüssel **ModulePath** und **ConfigurationPath** an.</span><span class="sxs-lookup"><span data-stu-id="db8a8-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="db8a8-132">Der Schlüssel **ConfigurationPath** gibt an, wo MOF-Dateien gespeichert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="db8a8-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="db8a8-133">**ModulePath** gibt an, wo DSC-Ressourcenmodule gespeichert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="db8a8-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="db8a8-134">Auf einer SMB-Freigabe</span><span class="sxs-lookup"><span data-stu-id="db8a8-134">On an SMB Share</span></span>

<span data-ttu-id="db8a8-135">Wenn Sie eine **ResourceRepositoryShare** angegeben haben, speichern Sie beim Einrichten Ihres Pullclients Archive und Prüfsummen im Verzeichnis **SourcePath** aus dem Block **ResourceRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="db8a8-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

<span data-ttu-id="db8a8-136">Wenn Sie nur eine **ConfigurationRepositoryShare** angegeben haben, speichern Sie beim Einrichten Ihres Pullclients Archive und Prüfsummen im Verzeichnis **SourcePath** aus dem Block **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="db8a8-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="db8a8-137">Aktualisieren von Ressourcen</span><span class="sxs-lookup"><span data-stu-id="db8a8-137">Updating resources</span></span>

<span data-ttu-id="db8a8-138">Sie können einen Knoten zwingen, seine Ressourcen zu aktualisieren, indem Sie die Versionsnummer im Namen des Archivs ändern oder eine neue Prüfsumme erstellen.</span><span class="sxs-lookup"><span data-stu-id="db8a8-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="db8a8-139">Der Pullclient sucht nach neueren Versionen der erforderlichen Ressourcen sowie nach aktualisierten Prüfsummen, wenn sein LCM aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="db8a8-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="db8a8-140">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="db8a8-140">See also</span></span>

- [<span data-ttu-id="db8a8-141">Einrichten eines DSC-SMB-Pullservers</span><span class="sxs-lookup"><span data-stu-id="db8a8-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="db8a8-142">Einrichten eines DSC-HTTP-Pullservers</span><span class="sxs-lookup"><span data-stu-id="db8a8-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
