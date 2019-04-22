---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,service,setup
title: Schreiben, Kompilieren und Anwenden einer Konfiguration
ms.openlocfilehash: 947308efa165543571801c88a922daf44fa88be0
ms.sourcegitcommit: 3f6002e7109373eda31cc65fc84d2600447cb7e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59506817"
---
> <span data-ttu-id="e45c3-103">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e45c3-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="e45c3-104">Schreiben, Kompilieren und Anwenden einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="e45c3-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="e45c3-105">Diese Übung führt Sie von Anfang bis Ende durch das Erstellen und Anwenden einer Desired State Configuration (DSC)-Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="e45c3-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="e45c3-106">Anhand des folgenden Beispiels erfahren Sie, wie Sie eine einfache Konfiguration schreiben und anwenden.</span><span class="sxs-lookup"><span data-stu-id="e45c3-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="e45c3-107">Mit der Konfiguration wird sichergestellt, dass eine „HelloWorld.txt“-Datei auf Ihrem lokalen Computer vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="e45c3-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="e45c3-108">Wenn Sie die Datei löschen, erstellt DSC sie beim nächsten Update neu.</span><span class="sxs-lookup"><span data-stu-id="e45c3-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="e45c3-109">Eine Übersicht über DSC und die Funktionsweise finden Sie unter [Desired State Configuration Overview for Developers (Desired State Configuration (DSC): Übersicht für Entwickler)](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="e45c3-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="e45c3-110">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="e45c3-110">Requirements</span></span>

<span data-ttu-id="e45c3-111">Sie benötigen einen Computer mit PowerShell 4.0 oder höher, um dieses Beispiel auszuführen.</span><span class="sxs-lookup"><span data-stu-id="e45c3-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="e45c3-112">Schreiben der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="e45c3-112">Write the configuration</span></span>

<span data-ttu-id="e45c3-113">Eine DSC-[Konfiguration](configurations.md) ist eine spezielle PowerShell-Funktion, die definiert, wie Sie einen oder mehrere Zielcomputer (Knoten) konfigurieren möchten.</span><span class="sxs-lookup"><span data-stu-id="e45c3-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="e45c3-114">Geben Sie Folgendes in die PowerShell ISE oder einen anderen PowerShell-Editor ein:</span><span class="sxs-lookup"><span data-stu-id="e45c3-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

<span data-ttu-id="e45c3-115">Speichern Sie die Datei als „HelloWorld.ps1“.</span><span class="sxs-lookup"><span data-stu-id="e45c3-115">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="e45c3-116">Das Definieren einer Konfiguration entspricht dem Definieren einer Funktion.</span><span class="sxs-lookup"><span data-stu-id="e45c3-116">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="e45c3-117">Der **Node**-Block gibt den zu konfigurierenden Zielknoten an, in diesem Fall `localhost`.</span><span class="sxs-lookup"><span data-stu-id="e45c3-117">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="e45c3-118">Die Konfiguration ruft eine [Ressource](../resources/resources.md) auf, die `File`-Ressource.</span><span class="sxs-lookup"><span data-stu-id="e45c3-118">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="e45c3-119">Ressourcen stellen sicher, dass sich der Zielknoten im durch die Konfiguration definierten Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="e45c3-119">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="e45c3-120">Kompilieren der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="e45c3-120">Compile the configuration</span></span>

<span data-ttu-id="e45c3-121">Damit eine DSC-Konfiguration auf einem Knoten angewendet werden kann, muss sie zunächst in eine MOF-Datei kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="e45c3-121">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="e45c3-122">Durch Ausführen der Konfiguration wie eine Funktion wird eine MOF-Datei für jeden Knoten vom `Node`-Block definiert.</span><span class="sxs-lookup"><span data-stu-id="e45c3-122">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="e45c3-123">Sie müssen das Skript „HelloWorld.ps1“ per *dot source* im aktuellen Bereich aufrufen, um die Konfiguration auszuführen.</span><span class="sxs-lookup"><span data-stu-id="e45c3-123">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="e45c3-124">Weitere Informationen hierzu finden Sie unter [about_Scripts (Informationen zu Skripts)](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="e45c3-124">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="e45c3-125">Das Skript „HelloWorld.ps1“ rufen Sie per *Dot source* auf, indem Sie den Pfad zum Speicherort nach dem `. ` (Punkt gefolgt von einem Leerzeichen) eingeben.</span><span class="sxs-lookup"><span data-stu-id="e45c3-125">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="e45c3-126">Anschließend können Sie Ihre Konfiguration ausführen, indem Sie sie wie eine Funktion aufrufen.</span><span class="sxs-lookup"><span data-stu-id="e45c3-126">You may then, run your configuration by calling it like a Function.</span></span>
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

<span data-ttu-id="e45c3-127">Die folgende Ausgabe wird generiert:</span><span class="sxs-lookup"><span data-stu-id="e45c3-127">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="e45c3-128">Anwenden der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="e45c3-128">Apply the configuration</span></span>

<span data-ttu-id="e45c3-129">Nun, da Sie die kompilierte MOF-Dateien haben, können Sie die Konfiguration auf den Zielknoten (in diesem Fall der lokale Computer) anwenden, indem Sie das Cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="e45c3-129">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="e45c3-130">Das Cmdlet `Start-DscConfiguration` fordert den [lokalen Konfigurations-Manager](../managing-nodes/metaConfig.md) (die DSC-Engine) dazu auf, die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="e45c3-130">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="e45c3-131">Der LCM übernimmt das Aufrufen der DSC-Ressourcen, um die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="e45c3-131">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="e45c3-132">Verwenden Sie den folgenden Code, um das Cmdlet `Start-DSCConfiguration` auszuführen.</span><span class="sxs-lookup"><span data-stu-id="e45c3-132">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="e45c3-133">Geben Sie für den `-Path`-Parameter den Verzeichnispfad an, unter dem „localhost.mof“ gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="e45c3-133">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="e45c3-134">Das Cmdlet `Start-DSCConfiguration` durchsucht das angegebene Verzeichnis auf Dateien namens „\<Computername\>.mof“.</span><span class="sxs-lookup"><span data-stu-id="e45c3-134">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="e45c3-135">Das Cmdlet `Start-DSCConfiguration` versucht alle gefundenen MOF-Dateien auf den vom Dateinamen angegeben Computernamen („localhost“, „server01“, „dc-02“ usw.).</span><span class="sxs-lookup"><span data-stu-id="e45c3-135">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="e45c3-136">Wenn der Parameter `-Wait` nicht festgelegt wird, erstellt `Start-DSCConfiguration` einen Hintergrundauftrag zum Ausführen des Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="e45c3-136">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="e45c3-137">Durch Festlegen des `-Verbose`-Parameters können Sie die **ausführliche** Ausgabe des Vorgangs anzeigen.</span><span class="sxs-lookup"><span data-stu-id="e45c3-137">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> `-Wait`<span data-ttu-id="e45c3-138">und `-Verbose` sind optionale Parameter.</span><span class="sxs-lookup"><span data-stu-id="e45c3-138">, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="e45c3-139">Testen der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="e45c3-139">Test the configuration</span></span>

<span data-ttu-id="e45c3-140">Sobald das Cmdlet `Start-DSCConfiguration` abgeschlossen ist, sollte Ihnen eine „HelloWorld.txt“-Datei am von Ihnen festgelegten Speicherort angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e45c3-140">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="e45c3-141">Sie können die Inhalte mit dem Cmdlet [Get-Content](/powershell/module/microsoft.powershell.management/get-content) überprüfen.</span><span class="sxs-lookup"><span data-stu-id="e45c3-141">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="e45c3-142">Sie können den aktuellen Status auch mit [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) *testen*.</span><span class="sxs-lookup"><span data-stu-id="e45c3-142">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="e45c3-143">Die Ausgabe sollte „TRUE“ zurückgeben, wenn der Knoten derzeit der angewendeten Konfiguration entspricht.</span><span class="sxs-lookup"><span data-stu-id="e45c3-143">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a><span data-ttu-id="e45c3-144">Erneutes Anwenden der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="e45c3-144">Re-applying the configuration</span></span>

<span data-ttu-id="e45c3-145">Sie können die Textdatei entfernen, die von Ihrer Konfiguration erstellt wurde, um die erneute Anwendung Ihrer Konfiguration anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e45c3-145">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="e45c3-146">Verwenden Sie dann das Cmdlet `Start-DSCConfiguration` mit dem Parameter `-UseExisting`.</span><span class="sxs-lookup"><span data-stu-id="e45c3-146">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="e45c3-147">Der Parameter `-UseExisting` weist `Start-DSCConfiguration` an, die Datei „current.mof“ erneut anzuwenden, die die letzte erfolgreich angewendete Konfiguration darstellt.</span><span class="sxs-lookup"><span data-stu-id="e45c3-147">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="e45c3-148">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="e45c3-148">Next steps</span></span>

- <span data-ttu-id="e45c3-149">Weiteren Informationen zu DSC-Konfigurationen erhalten Sie unter [DSC-Konfigurationen](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="e45c3-149">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="e45c3-150">Welche DSC-Ressourcen verfügbar sind und wie Sie benutzerdefinierte DSC-Ressourcen erstellen erfahren Sie unter [DSC-Ressourcen](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="e45c3-150">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="e45c3-151">DSC-Konfigurationen und -Ressourcen finden Sie unter [PowerShell-Katalog](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="e45c3-151">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
