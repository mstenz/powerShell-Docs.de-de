---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,service,setup
title: Schreiben, Kompilieren und Anwenden einer Konfiguration
ms.openlocfilehash: fa4d98fd12202439ba7025fd8af3fa398653ca05
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677840"
---
> <span data-ttu-id="c5941-103">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c5941-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="c5941-104">Schreiben, Kompilieren und Anwenden einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="c5941-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="c5941-105">Diese Übung führt Sie von Anfang bis Ende durch das Erstellen und Anwenden einer Desired State Configuration (DSC)-Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="c5941-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="c5941-106">Im folgenden Beispiel erfahren Sie, wie zum Schreiben und eine sehr einfache Konfiguration anwenden.</span><span class="sxs-lookup"><span data-stu-id="c5941-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="c5941-107">Die Konfiguration wird Stellen Sie sicher, dass eine Datei "HelloWorld.txt" auf dem lokalen Computer vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="c5941-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="c5941-108">Wenn Sie die Datei löschen, werden DSC es das nächste Mal neu erstellt, die, das Sie aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="c5941-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="c5941-109">Eine Übersicht über DSC und wie es funktioniert, finden Sie unter [Desired State Configuration-Übersicht für Entwickler](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="c5941-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="c5941-110">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c5941-110">Requirements</span></span>

<span data-ttu-id="c5941-111">Um dieses Beispiel auszuführen, benötigen Sie einen Computer mit PowerShell 4.0 oder höher.</span><span class="sxs-lookup"><span data-stu-id="c5941-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="c5941-112">Schreiben der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="c5941-112">Write the configuration</span></span>

<span data-ttu-id="c5941-113">Eine DSC-[Konfiguration](configurations.md) ist eine spezielle PowerShell-Funktion, die definiert, wie Sie einen oder mehrere Zielcomputer (Knoten) konfigurieren möchten.</span><span class="sxs-lookup"><span data-stu-id="c5941-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="c5941-114">Geben Sie in der PowerShell ISE oder andere PowerShell-Editor Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="c5941-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

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

<span data-ttu-id="c5941-115">Speichern Sie die Datei als "HelloWorld.ps1".</span><span class="sxs-lookup"><span data-stu-id="c5941-115">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="c5941-116">Definieren eine Konfiguration ist wie eine Funktion definieren.</span><span class="sxs-lookup"><span data-stu-id="c5941-116">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="c5941-117">Der **Node**-Block gibt den zu konfigurierenden Zielknoten an, in diesem Fall `localhost`.</span><span class="sxs-lookup"><span data-stu-id="c5941-117">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="c5941-118">Ruft die Konfiguration einer [Ressourcen](../resources/resources.md), `File` Ressource.</span><span class="sxs-lookup"><span data-stu-id="c5941-118">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="c5941-119">Ressourcen stellen sicher, dass sich der Zielknoten im durch die Konfiguration definierten Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="c5941-119">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="c5941-120">Kompilieren der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="c5941-120">Compile the configuration</span></span>

<span data-ttu-id="c5941-121">Damit eine DSC-Konfiguration auf einem Knoten angewendet werden kann, muss sie zunächst in eine MOF-Datei kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="c5941-121">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="c5941-122">Ausführen der Konfiguration, wie eine Funktion kann für jeden Knoten, die definiert, die von einem "MOF"-Datei kompiliert die `Node` Block.</span><span class="sxs-lookup"><span data-stu-id="c5941-122">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="c5941-123">Um die Konfiguration ausgeführt werden, müssen Sie *Punkt als Stammelement* Ihr Skript "HelloWorld.ps1" in den aktuellen Bereich.</span><span class="sxs-lookup"><span data-stu-id="c5941-123">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="c5941-124">Weitere Informationen finden Sie unter [About_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="c5941-124">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<span data-ttu-id="c5941-125">*Punkt als Stammelement* Ihr Skript "HelloWorld.ps1" Geben Sie in den Pfad, in dem Sie, nachdem gespeichert, die `. ` (Punkt, Speicherplatz).</span><span class="sxs-lookup"><span data-stu-id="c5941-125">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="c5941-126">Anschließend können Sie Ihre Konfiguration ausführen, indem Sie es wie eine Funktion aufrufen.</span><span class="sxs-lookup"><span data-stu-id="c5941-126">You may then, run your configuration by calling it like a Function.</span></span>

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
```

<span data-ttu-id="c5941-127">Die folgende Ausgabe wird generiert:</span><span class="sxs-lookup"><span data-stu-id="c5941-127">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="c5941-128">Anwenden der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="c5941-128">Apply the configuration</span></span>

<span data-ttu-id="c5941-129">Nun, da Sie die kompilierte MOF-Dateien haben, können Sie die Konfiguration auf den Zielknoten (in diesem Fall der lokale Computer) anwenden, indem Sie das Cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="c5941-129">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="c5941-130">Die `Start-DscConfiguration` Cmdlet fordert den [lokalen Konfigurations-Manager (LCM)](../managing-nodes/metaConfig.md), der Engine für DSC, um die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="c5941-130">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="c5941-131">Der LCM übernimmt das Aufrufen der DSC-Ressourcen, um die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="c5941-131">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="c5941-132">Verwenden Sie den folgenden Code zum Ausführen der `Start-DSCConfiguration` Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c5941-132">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="c5941-133">Geben Sie den Directory-Pfad, in Ihrer "localhost.mof", um gespeichert ist, die `-Path` Parameter.</span><span class="sxs-lookup"><span data-stu-id="c5941-133">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="c5941-134">Die `Start-DSCConfiguration` Cmdlet durchsucht den für eine angegebene Verzeichnis "\<Computername\>.mof" Dateien.</span><span class="sxs-lookup"><span data-stu-id="c5941-134">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="c5941-135">Die `Start-DSCConfiguration` Cmdlet versucht, jede "MOF"-Datei gefundenen auf den Computernamen, angegeben durch den Dateinamen ("Localhost", "server01", "dc-02" usw.) anwenden.</span><span class="sxs-lookup"><span data-stu-id="c5941-135">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="c5941-136">Wenn die `-Wait` Parameter nicht angegeben ist, `Start-DSCConfiguration` erstellt einen Hintergrundauftrag, um den Vorgang auszuführen.</span><span class="sxs-lookup"><span data-stu-id="c5941-136">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="c5941-137">Angeben der `-Verbose` Parameter können Sie sehen Sie sich die **ausführlich** Ausgabe des Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="c5941-137">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="c5941-138">`-Wait`, und `-Verbose` sind beide optionale Parameter.</span><span class="sxs-lookup"><span data-stu-id="c5941-138">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="c5941-139">Testen der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="c5941-139">Test the configuration</span></span>

<span data-ttu-id="c5941-140">Sobald die `Start-DSCConfiguration` Cmdlet abgeschlossen ist, sollte eine "HelloWorld.txt"-Datei im angegebenen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="c5941-140">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="c5941-141">Sie können überprüfen, ob die Inhalte mit der [Get-Content](/powershell/module/microsoft.powershell.management/get-content) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c5941-141">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="c5941-142">Sie können auch *testen* den aktuellen Status mit [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="c5941-142">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="c5941-143">Die Ausgabe sollte "True" sein, wenn der Knoten derzeit mit den angewendeten Konfiguration kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="c5941-143">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

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

## <a name="re-applying-the-configuration"></a><span data-ttu-id="c5941-144">Erneutes Anwenden der Konfigurations</span><span class="sxs-lookup"><span data-stu-id="c5941-144">Re-applying the configuration</span></span>

<span data-ttu-id="c5941-145">Zum Anzeigen Ihrer Konfiguration erneut angewendet werden, können Sie die Textdatei wird von Ihrer Konfiguration entfernen.</span><span class="sxs-lookup"><span data-stu-id="c5941-145">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="c5941-146">Die Verwendung der `Start-DSCConfiguration` Cmdlet mit dem `-UseExisting` Parameter.</span><span class="sxs-lookup"><span data-stu-id="c5941-146">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="c5941-147">Die `-UseExisting` -Parameter weist `Start-DSCConfiguration` um die Datei "current.mof" erneut anzuwenden, die zuletzt erfolgreich steht Konfiguration angewendet.</span><span class="sxs-lookup"><span data-stu-id="c5941-147">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="c5941-148">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="c5941-148">Next steps</span></span>

- <span data-ttu-id="c5941-149">Weiteren Informationen zu DSC-Konfigurationen erhalten Sie unter [DSC-Konfigurationen](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="c5941-149">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="c5941-150">Welche DSC-Ressourcen verfügbar sind und wie Sie benutzerdefinierte DSC-Ressourcen erstellen erfahren Sie unter [DSC-Ressourcen](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="c5941-150">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="c5941-151">DSC-Konfigurationen und -Ressourcen finden Sie unter [PowerShell-Katalog](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="c5941-151">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
