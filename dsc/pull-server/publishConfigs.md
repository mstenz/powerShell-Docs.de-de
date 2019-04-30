---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Veröffentlichen auf einem Pullserver mithilfe von Konfigurations-IDs (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079505"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="d6b08-103">Veröffentlichen auf einem Pullserver mithilfe von Konfigurations-IDs (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="d6b08-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="d6b08-104">Die folgenden Abschnitte gehen davon aus, dass Sie bereits einen Pullserver eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="d6b08-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="d6b08-105">Wenn Sie noch keinen Pullserver eingerichtet haben, können Sie die folgenden Anleitungen verwenden:</span><span class="sxs-lookup"><span data-stu-id="d6b08-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="d6b08-106">Einrichten eines DSC-SMB-Pullservers</span><span class="sxs-lookup"><span data-stu-id="d6b08-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="d6b08-107">Einrichten eines DSC-HTTP-Pullservers</span><span class="sxs-lookup"><span data-stu-id="d6b08-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="d6b08-108">Jeder Zielknoten kann zum Herunterladen von Konfigurationen, Ressourcen und sogar zum Berichten seines Status konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="d6b08-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="d6b08-109">Dieser Artikel zeigt Ihnen, wie Sie Ressourcen hochladen können, damit sie zum Download zur Verfügung stehen, und wie Sie Clients so konfigurieren, dass sie Ressourcen automatisch herunterladen.</span><span class="sxs-lookup"><span data-stu-id="d6b08-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="d6b08-110">Wenn der Knoten eine zugewiesene Konfiguration empfängt (durch **Pull** oder **Push** (v5)), lädt er automatisch alle für die Konfiguration erforderlichen Ressourcen vom in LCM angegebenen Speicherort herunter.</span><span class="sxs-lookup"><span data-stu-id="d6b08-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="d6b08-111">Kompilieren von Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="d6b08-111">Compile Configurations</span></span>

<span data-ttu-id="d6b08-112">Der erste Schritt beim Speichern von [Konfigurationen](../configurations/configurations.md) auf einem Pullserver besteht im Kompilieren der Dateien in MOF-Dateien.</span><span class="sxs-lookup"><span data-stu-id="d6b08-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into ".mof" files.</span></span> <span data-ttu-id="d6b08-113">Damit eine Konfiguration generisch und auf mehrere Clients anwendbar wird, verwenden Sie `localhost` in Ihrem Node-Block.</span><span class="sxs-lookup"><span data-stu-id="d6b08-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="d6b08-114">Das folgende Beispiel zeigt eine Konfigurationsshell, die `localhost` anstelle eines bestimmten Clientnamens verwendet.</span><span class="sxs-lookup"><span data-stu-id="d6b08-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="d6b08-115">Sobald Sie Ihre generische Konfiguration erstellt haben, sollten Sie über eine Datei „localhost.mof“ verfügen.</span><span class="sxs-lookup"><span data-stu-id="d6b08-115">Once you have compiled your generic configuration, you should have a "localhost.mof" file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="d6b08-116">Umbenennen der MOF-Datei</span><span class="sxs-lookup"><span data-stu-id="d6b08-116">Renaming the MOF file</span></span>

<span data-ttu-id="d6b08-117">Sie können MOF-Konfigurationsdateien auf einem Pullserver mithilfe von **ConfigurationName** oder **ConfigurationID** speichern.</span><span class="sxs-lookup"><span data-stu-id="d6b08-117">You can store Configuration ".mof" files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="d6b08-118">Je nachdem, wie Sie die Einrichtung Ihrer Pullclients planen, können Sie einen der folgenden Abschnitte auswählen, um Ihre kompilierten MOF-Dateien ordnungsgemäß umzubenennen.</span><span class="sxs-lookup"><span data-stu-id="d6b08-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled ".mof" files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="d6b08-119">Konfigurations-IDs (GUIDs)</span><span class="sxs-lookup"><span data-stu-id="d6b08-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="d6b08-120">Sie müssen Ihre Datei „localhost.mof“ in „<GUID>.mof“ umbenennen.</span><span class="sxs-lookup"><span data-stu-id="d6b08-120">You will need to rename your "localhost.mof" file to "<GUID>.mof" file.</span></span> <span data-ttu-id="d6b08-121">Sie können eine zufällige **GUID** mithilfe des folgenden Beispiels oder des Cmdlets [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) erstellen.</span><span class="sxs-lookup"><span data-stu-id="d6b08-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="d6b08-122">Beispielausgabe</span><span class="sxs-lookup"><span data-stu-id="d6b08-122">Sample Output</span></span>

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="d6b08-123">Sie können Ihre MOF-Datei dann mit jeder zulässigen Methode umbenennen.</span><span class="sxs-lookup"><span data-stu-id="d6b08-123">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="d6b08-124">Im folgenden Beispiel wird das Cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) verwendet.</span><span class="sxs-lookup"><span data-stu-id="d6b08-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="d6b08-125">Weitere Informationen zur Verwendung von **GUIDs** in Ihrer Umgebung finden Sie unter [Plan for Guids (Planen von GUIDs)](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="d6b08-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="d6b08-126">Konfigurationsnamen</span><span class="sxs-lookup"><span data-stu-id="d6b08-126">Configuration Names</span></span>

<span data-ttu-id="d6b08-127">Sie müssen Ihre Datei „localhost.mof“ in „<Configuration Name>.mof“ umbenennen.</span><span class="sxs-lookup"><span data-stu-id="d6b08-127">You will need to rename your "localhost.mof" file to "<Configuration Name>.mof" file.</span></span> <span data-ttu-id="d6b08-128">Im folgenden Beispiel wird der Konfigurationsname aus dem vorherigen Abschnitt verwendet.</span><span class="sxs-lookup"><span data-stu-id="d6b08-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="d6b08-129">Sie können Ihre MOF-Datei dann mit jeder zulässigen Methode umbenennen.</span><span class="sxs-lookup"><span data-stu-id="d6b08-129">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="d6b08-130">Im folgenden Beispiel wird das Cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) verwendet.</span><span class="sxs-lookup"><span data-stu-id="d6b08-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="d6b08-131">Erstellen der Prüfsumme</span><span class="sxs-lookup"><span data-stu-id="d6b08-131">Create the CheckSum</span></span>

<span data-ttu-id="d6b08-132">Jede MOF-Datei, die auf einem Pullserver oder in einer SMB-Freigabe gespeichert ist, muss über eine zugehörige CHECKSUM-Datei verfügen.</span><span class="sxs-lookup"><span data-stu-id="d6b08-132">Each ".mof" file stored on a Pull Server, or SMB share needs to have an associated ".checksum" file.</span></span> <span data-ttu-id="d6b08-133">Diese Datei informiert Clients darüber, wenn sich die zugehörige MOF-Datei geändert hat und erneut heruntergeladen werden sollte.</span><span class="sxs-lookup"><span data-stu-id="d6b08-133">This file lets clients know when the associated ".mof" file has changed and should be downloaded again.</span></span>

<span data-ttu-id="d6b08-134">Sie können mit dem Cmdlet [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) eine **CheckSum** erstellen.</span><span class="sxs-lookup"><span data-stu-id="d6b08-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="d6b08-135">Sie können auch `New-DSCCheckSum` für ein Verzeichnis mit Dateien mit dem Parameter `-Path` ausführen.</span><span class="sxs-lookup"><span data-stu-id="d6b08-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="d6b08-136">Wenn bereits eine Prüfsumme vorhanden ist, können Sie mit dem Parameter `-Force` erzwingen, dass sie neu erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="d6b08-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="d6b08-137">Das folgende Beispiel gibt ein Verzeichnis mit der MOF-Datei aus dem vorherigen Abschnitt an und verwendet den Parameter `-Force`.</span><span class="sxs-lookup"><span data-stu-id="d6b08-137">The following example specified a directory containing the ".mof" file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="d6b08-138">Es wird keine Ausgabe angezeigt, aber es sollte nun eine Datei „<GUID or Configuration Name>.mof.checksum“ vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="d6b08-138">No output will be shown, but you should now see a "<GUID or Configuration Name>.mof.checksum" file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="d6b08-139">Speicherort für MOF-Dateien und Prüfsummen</span><span class="sxs-lookup"><span data-stu-id="d6b08-139">Where to store MOF files and CheckSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="d6b08-140">Auf einem DSC-HTTP-Pullserver</span><span class="sxs-lookup"><span data-stu-id="d6b08-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="d6b08-141">Wenn Sie Ihren HTTP-Pullserver einrichten (wie unter [Einrichten eines DSC-HTTP-Pullservers](pullServer.md) beschrieben), geben Sie Verzeichnisse für die Schlüssel **ModulePath** und **ConfigurationPath** an.</span><span class="sxs-lookup"><span data-stu-id="d6b08-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="d6b08-142">Der Schlüssel **ConfigurationPath** gibt an, wo MOF-Dateien gespeichert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="d6b08-142">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="d6b08-143">**ConfigurationPath** gibt an, wo MOF- und CHECKSUM-Dateien gespeichert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="d6b08-143">The **ConfigurationPath** indicates where any ".mof" files and ".checksum" files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="d6b08-144">Auf einer SMB-Freigabe</span><span class="sxs-lookup"><span data-stu-id="d6b08-144">On an SMB Share</span></span>

<span data-ttu-id="d6b08-145">Wenn Sie einen Pullclient für die Verwendung einer SMB-Freigabe einrichten, geben Sie eine **ConfigurationRepositoryShare** an.</span><span class="sxs-lookup"><span data-stu-id="d6b08-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="d6b08-146">Alle MOF- und CHECKSUM-Dateien sollten dann im Verzeichnis **SourcePath** aus dem **ConfigurationRepositoryShare**-Block gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="d6b08-146">All ".mof" files and ".checksum" files should then be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="d6b08-147">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="d6b08-147">Next Steps</span></span>

<span data-ttu-id="d6b08-148">Im nächsten Schritt müssen Sie die Pullclients so konfigurieren, dass sie die angegebene Konfiguration pullen.</span><span class="sxs-lookup"><span data-stu-id="d6b08-148">Next, you will want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="d6b08-149">Weitere Informationen finden Sie in einem der folgenden Leitfäden:</span><span class="sxs-lookup"><span data-stu-id="d6b08-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="d6b08-150">Einrichten eines Pullclients mithilfe von Konfigurations-IDs (v4)</span><span class="sxs-lookup"><span data-stu-id="d6b08-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="d6b08-151">Einrichten eines Pullclients mithilfe von Konfigurations-IDs (v5)</span><span class="sxs-lookup"><span data-stu-id="d6b08-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="d6b08-152">Einrichten eines Pullclients mithilfe von Konfigurationsnamen (v5)</span><span class="sxs-lookup"><span data-stu-id="d6b08-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="d6b08-153">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d6b08-153">See also</span></span>

- [<span data-ttu-id="d6b08-154">Einrichten eines DSC-SMB-Pullservers</span><span class="sxs-lookup"><span data-stu-id="d6b08-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="d6b08-155">Einrichten eines DSC-HTTP-Pullservers</span><span class="sxs-lookup"><span data-stu-id="d6b08-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="d6b08-156">Verpacken und Hochladen von Ressourcen auf einen Pullserver</span><span class="sxs-lookup"><span data-stu-id="d6b08-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
