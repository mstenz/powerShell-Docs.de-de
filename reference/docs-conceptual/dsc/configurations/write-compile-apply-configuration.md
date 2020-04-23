---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,service,setup
title: Schreiben, Kompilieren und Anwenden einer Konfiguration
ms.openlocfilehash: eb61e518762b9f13e617ecd4711bfef7a86814ec
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "76818157"
---
> <span data-ttu-id="14517-103">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="14517-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="14517-104">Schreiben, Kompilieren und Anwenden einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="14517-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="14517-105">Diese Übung führt Sie von Anfang bis Ende durch das Erstellen und Anwenden einer Desired State Configuration (DSC)-Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="14517-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="14517-106">Anhand des folgenden Beispiels erfahren Sie, wie Sie eine einfache Konfiguration schreiben und anwenden.</span><span class="sxs-lookup"><span data-stu-id="14517-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="14517-107">Mit der Konfiguration wird sichergestellt, dass eine „HelloWorld.txt“-Datei auf Ihrem lokalen Computer vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="14517-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="14517-108">Wenn Sie die Datei löschen, erstellt DSC sie beim nächsten Update neu.</span><span class="sxs-lookup"><span data-stu-id="14517-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="14517-109">Eine Übersicht über DSC und die Funktionsweise finden Sie unter [Desired State Configuration Overview for Developers (Desired State Configuration (DSC): Übersicht für Entwickler)](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="14517-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="14517-110">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="14517-110">Requirements</span></span>

<span data-ttu-id="14517-111">Sie benötigen einen Computer mit PowerShell 4.0 oder höher, um dieses Beispiel auszuführen.</span><span class="sxs-lookup"><span data-stu-id="14517-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="14517-112">Schreiben der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="14517-112">Write the configuration</span></span>

<span data-ttu-id="14517-113">Eine DSC-[Konfiguration](configurations.md) ist eine spezielle PowerShell-Funktion, die definiert, wie Sie einen oder mehrere Zielcomputer (Knoten) konfigurieren möchten.</span><span class="sxs-lookup"><span data-stu-id="14517-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="14517-114">Geben Sie Folgendes in die PowerShell ISE oder einen anderen PowerShell-Editor ein:</span><span class="sxs-lookup"><span data-stu-id="14517-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

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

> <span data-ttu-id="14517-115">!Wichtig: In komplexeren Szenarien, in denen mehrere Module importiert werden müssen, damit Sie mit vielen DSC-Ressourcen in der gleichen Konfiguration arbeiten können, geben Sie jedes Modul mit `Import-DscResource` in einer separaten Zeile an.</span><span class="sxs-lookup"><span data-stu-id="14517-115">!Important In more advanced scenarios where multiple modules need to be imported so you can work with many DSC Resources in the same configuration, make sure to put each module in a separate line using `Import-DscResource`.</span></span>
> <span data-ttu-id="14517-116">Dies lässt sich in der Quellcodeverwaltung leichter nachverfolgen und ist erforderlich, wenn Sie in Azure State Configuration mit DSC arbeiten.</span><span class="sxs-lookup"><span data-stu-id="14517-116">This is easier to maintain in source control and required when working with DSC in Azure State Configuration.</span></span>
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

<span data-ttu-id="14517-117">Speichern Sie die Datei als „HelloWorld.ps1“.</span><span class="sxs-lookup"><span data-stu-id="14517-117">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="14517-118">Das Definieren einer Konfiguration entspricht dem Definieren einer Funktion.</span><span class="sxs-lookup"><span data-stu-id="14517-118">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="14517-119">Der **Node**-Block gibt den zu konfigurierenden Zielknoten an, in diesem Fall `localhost`.</span><span class="sxs-lookup"><span data-stu-id="14517-119">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="14517-120">Die Konfiguration ruft eine [Ressource](../resources/resources.md) auf, die `File`-Ressource.</span><span class="sxs-lookup"><span data-stu-id="14517-120">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="14517-121">Ressourcen stellen sicher, dass sich der Zielknoten im durch die Konfiguration definierten Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="14517-121">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="14517-122">Kompilieren der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="14517-122">Compile the configuration</span></span>

<span data-ttu-id="14517-123">Damit eine DSC-Konfiguration auf einem Knoten angewendet werden kann, muss sie zunächst in eine MOF-Datei kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="14517-123">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="14517-124">Durch Ausführen der Konfiguration wie eine Funktion wird eine MOF-Datei für jeden Knoten vom `Node`-Block definiert.</span><span class="sxs-lookup"><span data-stu-id="14517-124">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="14517-125">Sie müssen das Skript „HelloWorld.ps1“ per *dot source* im aktuellen Bereich aufrufen, um die Konfiguration auszuführen.</span><span class="sxs-lookup"><span data-stu-id="14517-125">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="14517-126">Weitere Informationen hierzu finden Sie unter [about_Scripts (Informationen zu Skripts)](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="14517-126">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="14517-127">Das Skript „HelloWorld.ps1“ rufen Sie per *Dot source* auf, indem Sie den Pfad zum Speicherort nach dem `. ` (Punkt gefolgt von einem Leerzeichen) eingeben.</span><span class="sxs-lookup"><span data-stu-id="14517-127">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="14517-128">Anschließend können Sie Ihre Konfiguration ausführen, indem Sie sie wie eine Funktion aufrufen.</span><span class="sxs-lookup"><span data-stu-id="14517-128">You may then, run your configuration by calling it like a Function.</span></span>
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

<span data-ttu-id="14517-129">Die folgende Ausgabe wird generiert:</span><span class="sxs-lookup"><span data-stu-id="14517-129">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="14517-130">Anwenden der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="14517-130">Apply the configuration</span></span>

<span data-ttu-id="14517-131">Nun, da Sie die kompilierte MOF-Dateien haben, können Sie die Konfiguration auf den Zielknoten (in diesem Fall der lokale Computer) anwenden, indem Sie das Cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="14517-131">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="14517-132">Das Cmdlet `Start-DscConfiguration` fordert den [lokalen Konfigurations-Manager](../managing-nodes/metaConfig.md) (die DSC-Engine) dazu auf, die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="14517-132">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="14517-133">Der LCM übernimmt das Aufrufen der DSC-Ressourcen, um die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="14517-133">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="14517-134">Verwenden Sie den folgenden Code, um das Cmdlet `Start-DSCConfiguration` auszuführen.</span><span class="sxs-lookup"><span data-stu-id="14517-134">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="14517-135">Geben Sie für den `-Path`-Parameter den Verzeichnispfad an, unter dem „localhost.mof“ gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="14517-135">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="14517-136">Das Cmdlet `Start-DSCConfiguration` durchsucht das angegebene Verzeichnis auf Dateien namens „\<Computername\>.mof“.</span><span class="sxs-lookup"><span data-stu-id="14517-136">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="14517-137">Das Cmdlet `Start-DSCConfiguration` versucht alle gefundenen MOF-Dateien auf den vom Dateinamen angegeben Computernamen („localhost“, „server01“, „dc-02“ usw.).</span><span class="sxs-lookup"><span data-stu-id="14517-137">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="14517-138">Wenn der Parameter `-Wait` nicht festgelegt wird, erstellt `Start-DSCConfiguration` einen Hintergrundauftrag zum Ausführen des Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="14517-138">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="14517-139">Durch Festlegen des `-Verbose`-Parameters können Sie die **ausführliche** Ausgabe des Vorgangs anzeigen.</span><span class="sxs-lookup"><span data-stu-id="14517-139">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="14517-140">`-Wait` und `-Verbose` sind optionale Parameter.</span><span class="sxs-lookup"><span data-stu-id="14517-140">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="14517-141">Testen der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="14517-141">Test the configuration</span></span>

<span data-ttu-id="14517-142">Sobald das Cmdlet `Start-DSCConfiguration` abgeschlossen ist, sollte Ihnen eine „HelloWorld.txt“-Datei am von Ihnen festgelegten Speicherort angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="14517-142">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="14517-143">Sie können die Inhalte mit dem Cmdlet [Get-Content](/powershell/module/microsoft.powershell.management/get-content) überprüfen.</span><span class="sxs-lookup"><span data-stu-id="14517-143">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="14517-144">Sie können den aktuellen Status auch mit *Test-DSCConfiguration*[testen](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="14517-144">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="14517-145">Die Ausgabe sollte „TRUE“ zurückgeben, wenn der Knoten derzeit der angewendeten Konfiguration entspricht.</span><span class="sxs-lookup"><span data-stu-id="14517-145">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

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

## <a name="re-applying-the-configuration"></a><span data-ttu-id="14517-146">Erneutes Anwenden der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="14517-146">Re-applying the configuration</span></span>

<span data-ttu-id="14517-147">Sie können die Textdatei entfernen, die von Ihrer Konfiguration erstellt wurde, um die erneute Anwendung Ihrer Konfiguration anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="14517-147">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="14517-148">Verwenden Sie dann das Cmdlet `Start-DSCConfiguration` mit dem Parameter `-UseExisting`.</span><span class="sxs-lookup"><span data-stu-id="14517-148">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="14517-149">Der Parameter `-UseExisting` weist `Start-DSCConfiguration` an, die Datei „current.mof“ erneut anzuwenden, die die letzte erfolgreich angewendete Konfiguration darstellt.</span><span class="sxs-lookup"><span data-stu-id="14517-149">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="14517-150">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="14517-150">Next steps</span></span>

- <span data-ttu-id="14517-151">Weiteren Informationen zu DSC-Konfigurationen erhalten Sie unter [DSC-Konfigurationen](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="14517-151">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="14517-152">Welche DSC-Ressourcen verfügbar sind und wie Sie benutzerdefinierte DSC-Ressourcen erstellen erfahren Sie unter [DSC-Ressourcen](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="14517-152">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="14517-153">DSC-Konfigurationen und -Ressourcen finden Sie unter [PowerShell-Katalog](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="14517-153">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
