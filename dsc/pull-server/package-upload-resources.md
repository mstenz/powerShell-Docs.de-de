---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Paket und Hochladen von Ressourcen mit einem Pullserver
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401238"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="bca13-103">Paket und Hochladen von Ressourcen mit einem Pullserver</span><span class="sxs-lookup"><span data-stu-id="bca13-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="bca13-104">In den folgenden Abschnitten wird davon ausgegangen, dass Sie bereits einen Pull-Server eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="bca13-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="bca13-105">Wenn Sie Ihre Pull-Server nicht eingerichtet haben, können Sie die folgenden Handbüchern:</span><span class="sxs-lookup"><span data-stu-id="bca13-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="bca13-106">Einrichten eines DSC-SMB-Pullservers</span><span class="sxs-lookup"><span data-stu-id="bca13-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="bca13-107">Einrichten eines DSC-HTTP-Pullservers</span><span class="sxs-lookup"><span data-stu-id="bca13-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="bca13-108">Jeder Zielknoten kann für das Herunterladen von Konfigurationen, Ressourcen und sogar meldet seinen Status konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="bca13-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="bca13-109">In diesem Artikel wird zeigen, wie Ressourcen hochladen, damit sie die heruntergeladen werden, und Konfigurieren von Clients zum automatischen Herunterladen von Ressourcen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="bca13-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="bca13-110">Zeitpunkt des Knotens eine zugewiesenen Konfiguration und empfängt, über **Pull** oder **Push** (v5), automatisch heruntergeladen von der Konfiguration aus dem Speicherort, die im LCM angegebene erforderlichen Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="bca13-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="bca13-111">Paket-Ressourcenmodulen</span><span class="sxs-lookup"><span data-stu-id="bca13-111">Package Resource Modules</span></span>

<span data-ttu-id="bca13-112">Jede Ressource, die für einen Client zum Herunterladen verfügbar sind, muss in einer Datei ".zip" gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="bca13-112">Each resource available for a client to download must be stored in a ".zip" file.</span></span> <span data-ttu-id="bca13-113">Das folgende Beispiel zeigt die erforderlichen Schritte, die mit der ["xpsdesiredstateconfiguration"](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) Ressource.</span><span class="sxs-lookup"><span data-stu-id="bca13-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="bca13-114">Wenn Sie Clients mithilfe von PowerShell 4.0 verfügen, Sie möchten bei Flaten die Ordnerstruktur für die Ressource und entfernen alle Ordner Version.</span><span class="sxs-lookup"><span data-stu-id="bca13-114">If you have any clients using PowerShell 4.0, you will need to flaten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="bca13-115">Weitere Informationen finden Sie unter [mehrere Versionen der Ressource](../configurations/import-dscresource.md#multiple-resource-versions).</span><span class="sxs-lookup"><span data-stu-id="bca13-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="bca13-116">Sie können das Ressourcenverzeichnis mit jedem Hilfsprogramm, Skript oder -Methode, die Sie bevorzugen, komprimieren.</span><span class="sxs-lookup"><span data-stu-id="bca13-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="bca13-117">In Windows, können Sie *mit der rechten Maustaste* für das Verzeichnis von "xPSDesiredStateConfiguration", und wählen Sie "Senden an", und klicken Sie dann "Komprimierten Ordner".</span><span class="sxs-lookup"><span data-stu-id="bca13-117">In Windows, you can *right-click* on the "xPSDesiredStateConfiguration" directory, and select "Send To", then "Compressed Folder".</span></span>

![Rechtsklick](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="bca13-119">Benennen das Archiv für die Ressource</span><span class="sxs-lookup"><span data-stu-id="bca13-119">Naming the Resource Archive</span></span>

<span data-ttu-id="bca13-120">Das Archiv für die Ressource muss mit dem folgenden Format benannt wird:</span><span class="sxs-lookup"><span data-stu-id="bca13-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="bca13-121">Im Beispiel oben sollte "xPSDesiredStateConfiguration.zip" umbenannte "xPSDesiredStateConfiguration_8.4.4.0.zip" sein.</span><span class="sxs-lookup"><span data-stu-id="bca13-121">In the example above, "xPSDesiredStateConfiguration.zip" should be renamed "xPSDesiredStateConfiguration_8.4.4.0.zip".</span></span>

### <a name="create-checksums"></a><span data-ttu-id="bca13-122">Erstellen von Prüfsummen</span><span class="sxs-lookup"><span data-stu-id="bca13-122">Create CheckSums</span></span>

<span data-ttu-id="bca13-123">Sobald das Ressourcenmodul komprimiert und umbenannt wurde, müssen Sie erstellen eine **Prüfsumme**.</span><span class="sxs-lookup"><span data-stu-id="bca13-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span>  <span data-ttu-id="bca13-124">Die **Prüfsumme** verwendet wird, durch den LCM auf dem Client, um festzustellen, ob die Ressource geändert wurde und muss erneut heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="bca13-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="bca13-125">Sie erstellen eine **Prüfsumme** mit der [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="bca13-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="bca13-126">Wird keine Ausgabe angezeigt werden, aber ein "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum" sollte nun angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bca13-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="bca13-127">Sie können auch ausführen `New-DSCCheckSum` für ein Verzeichnis mit Dateien, die mit der `-Path` Parameter.</span><span class="sxs-lookup"><span data-stu-id="bca13-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="bca13-128">Wenn eine Prüfsumme bereits vorhanden ist, können Sie erzwingen, mit neu erstellt werden die `-Force` Parameter.</span><span class="sxs-lookup"><span data-stu-id="bca13-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="bca13-129">Speicherort für Archive der Ressource</span><span class="sxs-lookup"><span data-stu-id="bca13-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="bca13-130">Auf einem HTTP-Pullserver von DSC</span><span class="sxs-lookup"><span data-stu-id="bca13-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="bca13-131">Beim Einrichten Ihrer HTTP-Pullserver, siehe [richten Sie eine DSC-HTTP-Pullserver](pullServer.md), Verzeichnisse für die Angabe der **ModulePath** und **ConfigurationPath** Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="bca13-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="bca13-132">Die **ConfigurationPath** Schlüssel gibt an, in dem alle "MOF"-Dateien gespeichert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="bca13-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="bca13-133">Die **ModulePath** gibt an, in dem alle DSC-Ressourcenmodulen gespeichert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="bca13-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="bca13-134">Auf einer SMB-Freigabe</span><span class="sxs-lookup"><span data-stu-id="bca13-134">On an SMB Share</span></span>

<span data-ttu-id="bca13-135">Wenn Sie angegeben haben eine **ResourceRepositoryShare**, wenn das Einrichten Ihrer Pull-Client speichern, Archive und Prüfsummen in der **SourcePath** des Verzeichnisses der **ResourceRepositoryShare** Block.</span><span class="sxs-lookup"><span data-stu-id="bca13-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

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

<span data-ttu-id="bca13-136">Wenn Sie nur angegeben ein **ConfigurationRepositoryShare**, wenn das Einrichten Ihrer Pull-Client speichern, Archive und Prüfsummen in der **SourcePath** des Verzeichnisses der  **ConfigurationRepositoryShare** Block.</span><span class="sxs-lookup"><span data-stu-id="bca13-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="bca13-137">Aktualisieren von Ressourcen</span><span class="sxs-lookup"><span data-stu-id="bca13-137">Updating resources</span></span>

<span data-ttu-id="bca13-138">Sie können erzwingen, dass einen Knoten seine Ressourcen Änderung der Versionsnummer des Archivs Namen aktualisieren, oder indem Sie eine neue Prüfsumme zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="bca13-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="bca13-139">Der Pull-Client überprüft für neuere Versionen der erforderlichen Ressourcen sowie Prüfsummen, aktualisiert, wenn der LCM aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="bca13-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="bca13-140">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="bca13-140">See also</span></span>

- [<span data-ttu-id="bca13-141">Einrichten eines DSC-SMB-Pullservers</span><span class="sxs-lookup"><span data-stu-id="bca13-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="bca13-142">Einrichten eines DSC-HTTP-Pullservers</span><span class="sxs-lookup"><span data-stu-id="bca13-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
