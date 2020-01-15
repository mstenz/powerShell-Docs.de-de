---
ms.date: 06/12/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: 'Schnellstart: Erstellen einer Website mit DSC'
ms.openlocfilehash: 08ca25604998ce8c913ef8112b5342f2e0216b6e
ms.sourcegitcommit: 1b88c280dd0799f225242608f0cbdab485357633
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/25/2019
ms.locfileid: "75416128"
---
# <a name="quickstart---create-a-website-with-desired-state-configuration-dsc"></a><span data-ttu-id="f2582-103">Schnellstart: Erstellen einer Website mit Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="f2582-103">Quickstart - Create a website with Desired State Configuration (DSC)</span></span>

> <span data-ttu-id="f2582-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f2582-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f2582-105">Diese Übung führt Sie von Anfang bis Ende durch das Erstellen und Anwenden einer Desired State Configuration (DSC)-Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="f2582-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="f2582-106">Das Beispiel, das wir verwenden, stellt sicher, dass ein Server die `Web-Server` (IIS)-Funktion aktiviert hat und der Inhalt für eine einfache „Hello World“-Website ist im Verzeichnis `inetpub\wwwroot` des Servers vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="f2582-106">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `inetpub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="f2582-107">Eine Übersicht über DSC und die Funktionsweise finden Sie unter [Desired State Configuration (DSC): Übersicht für Entscheidungsträger](../overview/decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="f2582-107">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](../overview/decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="f2582-108">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="f2582-108">Requirements</span></span>

<span data-ttu-id="f2582-109">Sie benötigen einen Computer mit Windows Server 2012 oder höher und mit PowerShell 4.0 oder höher, um dieses Beispiel auszuführen.</span><span class="sxs-lookup"><span data-stu-id="f2582-109">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="f2582-110">Schreiben und Platzieren der Datei „Index.htm“</span><span class="sxs-lookup"><span data-stu-id="f2582-110">Write and place the index.htm file</span></span>

<span data-ttu-id="f2582-111">Zunächst erstellen wir die HTML-Datei, die wir als Website-Inhalt verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="f2582-111">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="f2582-112">Erstellen Sie in Ihrem Stammordner einen Ordner namens `test`.</span><span class="sxs-lookup"><span data-stu-id="f2582-112">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="f2582-113">Geben Sie in einem Text-Editor den folgenden Text ein:</span><span class="sxs-lookup"><span data-stu-id="f2582-113">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="f2582-114">Speichern Sie dies als `index.htm` in den Ordner `test`, den Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="f2582-114">Save this as `index.htm` in the `test` folder you created earlier.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="f2582-115">Schreiben der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="f2582-115">Write the configuration</span></span>

<span data-ttu-id="f2582-116">Eine [DSC-Konfiguration](../configurations/configurations.md) ist eine spezielle PowerShell-Funktion, die definiert, wie Sie einen oder mehrere Zielcomputer (Knoten) konfigurieren möchten.</span><span class="sxs-lookup"><span data-stu-id="f2582-116">A [DSC configuration](../configurations/configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="f2582-117">Geben Sie in der PowerShell ISE Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="f2582-117">In the PowerShell ISE, type the following:</span></span>

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

<span data-ttu-id="f2582-118">Speichern Sie die Datei unter dem Namen `WebsiteTest.ps1`.</span><span class="sxs-lookup"><span data-stu-id="f2582-118">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="f2582-119">Sie sehen, dass sie wie eine PowerShell-Funktion aussieht und zusätzlich das Schlüsselworts **Configuration** enthält, welches vor dem Namen der Funktion verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="f2582-119">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="f2582-120">Der **Node**-Block gibt den zu konfigurierenden Zielknoten an.</span><span class="sxs-lookup"><span data-stu-id="f2582-120">The **Node** block specifies the target node to be configured.</span></span> <span data-ttu-id="f2582-121">In diesem Fall `localhost`.</span><span class="sxs-lookup"><span data-stu-id="f2582-121">In this case, `localhost`.</span></span>

<span data-ttu-id="f2582-122">Die Konfiguration ruft zwei [Ressourcen](../resources/resources.md) auf, **WindowsFeature** und **File**.</span><span class="sxs-lookup"><span data-stu-id="f2582-122">The configuration calls two [resources](../resources/resources.md), **WindowsFeature** and **File**.</span></span>
<span data-ttu-id="f2582-123">Ressourcen stellen sicher, dass sich der Zielknoten im durch die Konfiguration definierten Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="f2582-123">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="f2582-124">Kompilieren der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="f2582-124">Compile the configuration</span></span>

<span data-ttu-id="f2582-125">Damit eine DSC-Konfiguration auf einem Knoten angewendet werden kann, muss sie zunächst in eine MOF-Datei kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="f2582-125">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="f2582-126">Hierzu führen Sie die Konfiguration wie eine Funktion aus.</span><span class="sxs-lookup"><span data-stu-id="f2582-126">To do this, you run the configuration like a function.</span></span>
<span data-ttu-id="f2582-127">Wechseln Sie in einer PowerShell-Konsole in den gleichen Ordner, in dem Sie die Konfiguration gespeichert haben, und führen Sie die folgenden Befehle aus, um die Konfiguration in eine MOF-Datei zu kompilieren:</span><span class="sxs-lookup"><span data-stu-id="f2582-127">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="f2582-128">Die folgende Ausgabe wird generiert:</span><span class="sxs-lookup"><span data-stu-id="f2582-128">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="f2582-129">Die erste Zeile macht die Konfigurationsfunktion in der Konsole verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f2582-129">The first line makes the configuration function available in the console.</span></span>
<span data-ttu-id="f2582-130">In der zweiten Zeile wird die Konfiguration ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="f2582-130">The second line runs the configuration.</span></span>
<span data-ttu-id="f2582-131">Dies bedeutet, dass ein neuer Ordner mit dem Namen `WebsiteTest` als Unterordner des aktuellen Ordners erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="f2582-131">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span>
<span data-ttu-id="f2582-132">Der Ordner `WebsiteTest` enthält eine Datei mit dem Namen `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="f2582-132">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span>
<span data-ttu-id="f2582-133">Dies ist die Datei, die anschließend auf den Zielknoten angewendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="f2582-133">This is the file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="f2582-134">Anwenden der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="f2582-134">Apply the configuration</span></span>

<span data-ttu-id="f2582-135">Nun, da Sie die kompilierte MOF-Dateien haben, können Sie die Konfiguration auf den Zielknoten (in diesem Fall der lokale Computer) anwenden, indem Sie das Cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="f2582-135">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="f2582-136">Das `Start-DscConfiguration`-Cmdlet fordert den [lokalen Konfigurations-Manager (Local Configuration Manager – LCM)](../managing-nodes/metaConfig.md), die DSC-Engine, auf, die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="f2582-136">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="f2582-137">Der LCM übernimmt das Aufrufen der DSC-Ressourcen, um die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="f2582-137">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="f2582-138">Damit DSC ausgeführt werden kann, muss Windows für den Empfang von PowerShell-Remotebefehlen konfiguriert werden – selbst dann, wenn Sie eine `localhost`-Konfiguration ausführen.</span><span class="sxs-lookup"><span data-stu-id="f2582-138">To allow DSC to run, Windows needs to be configured to receive PowerShell remote commands, even when you're running a `localhost` configuration.</span></span> <span data-ttu-id="f2582-139">Um Ihre Umgebung auf einfache Weise ordnungsgemäß zu konfigurieren, rufen Sie einfach `Set-WsManQuickConfig -Force` in einem PowerShell-Terminal mit erhöhten Rechten aus.</span><span class="sxs-lookup"><span data-stu-id="f2582-139">To easily configure your environment correctly, just run `Set-WsManQuickConfig -Force` in an elevated PowerShell Terminal.</span></span>

<span data-ttu-id="f2582-140">Wechseln Sie in einer PowerShell-Konsole in den gleichen Ordner, in dem Sie die Konfiguration gespeichert haben, und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="f2582-140">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="f2582-141">Testen der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="f2582-141">Test the configuration</span></span>

<span data-ttu-id="f2582-142">Sie können das Cmdlet [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus), aufrufen, um zu überprüfen, ob die Konfiguration erfolgreich war.</span><span class="sxs-lookup"><span data-stu-id="f2582-142">You can call the [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet to see whether the configuration succeeded.</span></span>

<span data-ttu-id="f2582-143">Sie können die Ergebnisse auch direkt testen, in diesem Fall durch Aufrufen von `http://localhost/` in einem Webbrowser.</span><span class="sxs-lookup"><span data-stu-id="f2582-143">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span>
<span data-ttu-id="f2582-144">Es sollte die „Hello World“-HTML-Seite angezeigt werden, die Sie im ersten Schritt dieses Beispiels erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="f2582-144">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f2582-145">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="f2582-145">Next steps</span></span>

- <span data-ttu-id="f2582-146">Weiteren Informationen zu DSC-Konfigurationen erhalten Sie unter [DSC-Konfigurationen](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="f2582-146">Find out more about DSC configurations at [DSC configurations](../configurations/configurations.md).</span></span>
- <span data-ttu-id="f2582-147">Welche DSC-Ressourcen verfügbar sind und wie Sie benutzerdefinierte DSC-Ressourcen erstellen erfahren Sie unter [DSC-Ressourcen](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="f2582-147">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="f2582-148">DSC-Konfigurationen und -Ressourcen finden Sie unter [PowerShell-Katalog](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="f2582-148">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
