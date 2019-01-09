---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Veröffentlichen Sie auf einem Pull-Server mithilfe des Konfigurations-ID (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401313"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="31ed8-103">Veröffentlichen Sie auf einem Pull-Server mithilfe des Konfigurations-ID (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="31ed8-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="31ed8-104">In den folgenden Abschnitten wird davon ausgegangen, dass Sie bereits einen Pull-Server eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="31ed8-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="31ed8-105">Wenn Sie Ihre Pull-Server nicht eingerichtet haben, können Sie die folgenden Handbüchern:</span><span class="sxs-lookup"><span data-stu-id="31ed8-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="31ed8-106">Einrichten eines DSC-SMB-Pullservers</span><span class="sxs-lookup"><span data-stu-id="31ed8-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="31ed8-107">Einrichten eines DSC-HTTP-Pullservers</span><span class="sxs-lookup"><span data-stu-id="31ed8-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="31ed8-108">Jeder Zielknoten kann für das Herunterladen von Konfigurationen, Ressourcen und sogar meldet seinen Status konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="31ed8-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="31ed8-109">In diesem Artikel wird zeigen, wie Ressourcen hochladen, damit sie die heruntergeladen werden, und Konfigurieren von Clients zum automatischen Herunterladen von Ressourcen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="31ed8-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="31ed8-110">Zeitpunkt des Knotens eine zugewiesenen Konfiguration und empfängt, über **Pull** oder **Push** (v5), automatisch heruntergeladen von der Konfiguration aus dem Speicherort, die im LCM angegebene erforderlichen Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="31ed8-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="31ed8-111">Kompilieren von Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="31ed8-111">Compile Configurations</span></span>

<span data-ttu-id="31ed8-112">Der erste Schritt zum Speichern von [Konfigurationen](../configurations/configurations.md) auf einem Pull-Server ist in "MOF"-Dateien kompiliert.</span><span class="sxs-lookup"><span data-stu-id="31ed8-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into ".mof" files.</span></span> <span data-ttu-id="31ed8-113">Um eine Konfiguration generisch und gilt für die mehr Clients zu machen, verwenden Sie `localhost` in Ihrer "Node"-Block.</span><span class="sxs-lookup"><span data-stu-id="31ed8-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="31ed8-114">Das folgende Beispiel zeigt eine Konfiguration-Shell, die verwendet `localhost` anstelle eines bestimmten Client-Namens.</span><span class="sxs-lookup"><span data-stu-id="31ed8-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="31ed8-115">Nachdem Sie Ihre Konfiguration des generische kompiliert haben, sollten Sie eine Datei "localhost.mof" haben.</span><span class="sxs-lookup"><span data-stu-id="31ed8-115">Once you have compiled your generic configuration, you should have a "localhost.mof" file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="31ed8-116">Die MOF-Datei umbenennen</span><span class="sxs-lookup"><span data-stu-id="31ed8-116">Renaming the MOF file</span></span>

<span data-ttu-id="31ed8-117">Sie können die Konfiguration "MOF"-Dateien auf einem Pull-Server durch Speichern **ConfigurationName** oder **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="31ed8-117">You can store Configuration ".mof" files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="31ed8-118">Je nachdem, wie Sie Ihre pullclients einrichten möchten können Sie einen Abschnitt unten, um Ihre kompilierten "MOF"-Dateien ordnungsgemäß zu benennen.</span><span class="sxs-lookup"><span data-stu-id="31ed8-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled ".mof" files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="31ed8-119">Konfigurations-ID (GUID)</span><span class="sxs-lookup"><span data-stu-id="31ed8-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="31ed8-120">Sie müssen Ihre "localhost.mof" Datei umbenennen "<GUID>.mof" Datei.</span><span class="sxs-lookup"><span data-stu-id="31ed8-120">You will need to rename your "localhost.mof" file to "<GUID>.mof" file.</span></span> <span data-ttu-id="31ed8-121">Sie können einen zufälligen erstellen **Guid** verwenden Sie das Beispiel unten oder mithilfe der [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="31ed8-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="31ed8-122">Beispielausgabe</span><span class="sxs-lookup"><span data-stu-id="31ed8-122">Sample Output</span></span>

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="31ed8-123">Sie können dann Ihre "MOF"-Datei, die mit einer akzeptablen Methode umbenennen.</span><span class="sxs-lookup"><span data-stu-id="31ed8-123">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="31ed8-124">Im folgenden Beispiel wird die [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="31ed8-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="31ed8-125">Weitere Informationen zur Verwendung von **Guids** in Ihrer Umgebung finden Sie unter [Guids planen](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="31ed8-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="31ed8-126">Konfigurationsnamen</span><span class="sxs-lookup"><span data-stu-id="31ed8-126">Configuration Names</span></span>

<span data-ttu-id="31ed8-127">Sie müssen Ihre "localhost.mof" Datei umbenennen "<Configuration Name>.mof" Datei.</span><span class="sxs-lookup"><span data-stu-id="31ed8-127">You will need to rename your "localhost.mof" file to "<Configuration Name>.mof" file.</span></span> <span data-ttu-id="31ed8-128">Im folgenden Beispiel wird der Konfigurationsname aus dem vorherigen Abschnitt verwendet.</span><span class="sxs-lookup"><span data-stu-id="31ed8-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="31ed8-129">Sie können dann Ihre "MOF"-Datei, die mit einer akzeptablen Methode umbenennen.</span><span class="sxs-lookup"><span data-stu-id="31ed8-129">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="31ed8-130">Im folgenden Beispiel wird die [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="31ed8-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="31ed8-131">Die Prüfsumme zu erstellen</span><span class="sxs-lookup"><span data-stu-id="31ed8-131">Create the CheckSum</span></span>

<span data-ttu-id="31ed8-132">Jedes "MOF"-Datei, die auf einem Pull-Server oder eine SMB-Freigabe muss eine zugeordnete ".checksum"-Datei gespeichert.</span><span class="sxs-lookup"><span data-stu-id="31ed8-132">Each ".mof" file stored on a Pull Server, or SMB share needs to have an associated ".checksum" file.</span></span> <span data-ttu-id="31ed8-133">Diese Datei ermöglicht Clients, die wissen, wann die zugeordnete "MOF"-Datei wurde geändert und erneut heruntergeladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="31ed8-133">This file lets clients know when the associated ".mof" file has changed and should be downloaded again.</span></span>

<span data-ttu-id="31ed8-134">Sie erstellen eine **Prüfsumme** mit der [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="31ed8-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="31ed8-135">Sie können auch ausführen `New-DSCCheckSum` für ein Verzeichnis mit Dateien, die mit der `-Path` Parameter.</span><span class="sxs-lookup"><span data-stu-id="31ed8-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="31ed8-136">Wenn eine Prüfsumme bereits vorhanden ist, können Sie erzwingen, mit neu erstellt werden die `-Force` Parameter.</span><span class="sxs-lookup"><span data-stu-id="31ed8-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="31ed8-137">Im folgenden Beispiel wird ein Verzeichnis mit der Datei "MOF" aus dem vorherigen Abschnitt angegeben und verwendet die `-Force` Parameter.</span><span class="sxs-lookup"><span data-stu-id="31ed8-137">The following example specified a directory containing the ".mof" file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="31ed8-138">Wird keine Ausgabe angezeigt werden, aber jetzt sollte eine "<GUID or Configuration Name>. mof.checksum" Datei.</span><span class="sxs-lookup"><span data-stu-id="31ed8-138">No output will be shown, but you should now see a "<GUID or Configuration Name>.mof.checksum" file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="31ed8-139">Speicherort für MOF-Dateien und Prüfsummen</span><span class="sxs-lookup"><span data-stu-id="31ed8-139">Where to store MOF files and CheckSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="31ed8-140">Auf einem HTTP-Pullserver von DSC</span><span class="sxs-lookup"><span data-stu-id="31ed8-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="31ed8-141">Beim Einrichten Ihrer HTTP-Pullserver, siehe [richten Sie eine DSC-HTTP-Pullserver](pullServer.md), Verzeichnisse für die Angabe der **ModulePath** und **ConfigurationPath** Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="31ed8-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="31ed8-142">Die **ConfigurationPath** Schlüssel gibt an, in dem alle "MOF"-Dateien gespeichert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="31ed8-142">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="31ed8-143">Die **ConfigurationPath** gibt an, in dem alle "MOF" und ".checksum"-Dateien gespeichert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="31ed8-143">The **ConfigurationPath** indicates where any ".mof" files and ".checksum" files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="31ed8-144">Auf einer SMB-Freigabe</span><span class="sxs-lookup"><span data-stu-id="31ed8-144">On an SMB Share</span></span>

<span data-ttu-id="31ed8-145">Wenn Sie einen Pull-Client eingerichtet, eine SMB-Freigabe zu verwenden, geben Sie einen **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="31ed8-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="31ed8-146">Alle "MOF" und ".checksum"-Dateien sollten dann in gespeichert werden die **SourcePath** des Verzeichnisses der **ConfigurationRepositoryShare** Block.</span><span class="sxs-lookup"><span data-stu-id="31ed8-146">All ".mof" files and ".checksum" files should then be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="31ed8-147">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="31ed8-147">Next Steps</span></span>

<span data-ttu-id="31ed8-148">Als Nächstes möchten Sie die Pull-Clients zum Abrufen der angegebenen Konfigurations konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="31ed8-148">Next, you will want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="31ed8-149">Weitere Informationen finden Sie in den folgenden Handbüchern:</span><span class="sxs-lookup"><span data-stu-id="31ed8-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="31ed8-150">Einrichten eines Pull-Clients mithilfe des Konfigurations-ID (v4)</span><span class="sxs-lookup"><span data-stu-id="31ed8-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="31ed8-151">Einrichten eines Pull-Clients mithilfe des Konfigurations-ID (v5)</span><span class="sxs-lookup"><span data-stu-id="31ed8-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="31ed8-152">Einrichten eines Pull-Clients mithilfe von Konfigurationsnamen (v5)</span><span class="sxs-lookup"><span data-stu-id="31ed8-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="31ed8-153">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="31ed8-153">See also</span></span>

- [<span data-ttu-id="31ed8-154">Einrichten eines DSC-SMB-Pullservers</span><span class="sxs-lookup"><span data-stu-id="31ed8-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="31ed8-155">Einrichten eines DSC-HTTP-Pullservers</span><span class="sxs-lookup"><span data-stu-id="31ed8-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="31ed8-156">Paket und Hochladen von Ressourcen mit einem Pullserver</span><span class="sxs-lookup"><span data-stu-id="31ed8-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
