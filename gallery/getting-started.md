---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Erste Schritte mit dem PowerShell-Katalog
ms.openlocfilehash: 85b0a754aba25d850dc918024419318554f92b33
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225674"
---
# <a name="getting-started-with-the-powershell-gallery"></a><span data-ttu-id="cc3a5-103">Erste Schritte mit dem PowerShell-Katalog</span><span class="sxs-lookup"><span data-stu-id="cc3a5-103">Getting Started with the PowerShell Gallery</span></span>

<span data-ttu-id="cc3a5-104">Die richtige Vorgehensweise zum Installieren von Paketen aus dem PowerShell-Katalog ist die Verwendung der Cmdlets im Modul [PowerShellGet](/powershell/module/powershellget).</span><span class="sxs-lookup"><span data-stu-id="cc3a5-104">The proper way to install packages from the PowerShell Gallery is to use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="cc3a5-105">Um diese Elemente aus dem PowerShell-Katalog herunterzuladen, müssen Sie sich nicht anmelden.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-105">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="cc3a5-106">Zwar ist es möglich, ein Paket direkt aus dem PowerShell-Katalog herunterzuladen, diese Vorgehensweise wird aber nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-106">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span>
> <span data-ttu-id="cc3a5-107">Weitere Informationen finden Sie unter [Manual Package Download (Paket manuell herunterladen)](/powershell/gallery/how-to/working-with-packages/manual-download).</span><span class="sxs-lookup"><span data-stu-id="cc3a5-107">For more details, see [Manual Package Download](/powershell/gallery/how-to/working-with-packages/manual-download).</span></span>

## <a name="discovering-packages-from-the-powershell-gallery"></a><span data-ttu-id="cc3a5-108">Ermitteln von Paketen im PowerShell-Katalog</span><span class="sxs-lookup"><span data-stu-id="cc3a5-108">Discovering packages from the PowerShell Gallery</span></span>

<span data-ttu-id="cc3a5-109">Sie können Pakete im PowerShell-Katalog mithilfe des Steuerelements **Suchen** auf dieser Website suchen. Alternativ dazu können Sie die Seiten zu Modulen und Skripts durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-109">You can find packages in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="cc3a5-110">Sie können auch nach Paketen im PowerShell-Katalog suchen, indem Sie je nach Pakettyp die Cmdlets [Find-Module][] und [Find-Script][] mit `-Repository PSGallery` ausführen.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-110">You can also find packages from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="cc3a5-111">Das Filtern von Ergebnissen im Katalog kann über die folgenden Parameter erfolgen:</span><span class="sxs-lookup"><span data-stu-id="cc3a5-111">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="cc3a5-112">Name</span><span class="sxs-lookup"><span data-stu-id="cc3a5-112">Name</span></span>
- <span data-ttu-id="cc3a5-113">AllVersions</span><span class="sxs-lookup"><span data-stu-id="cc3a5-113">AllVersions</span></span>
- <span data-ttu-id="cc3a5-114">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="cc3a5-114">MinimumVersion</span></span>
- <span data-ttu-id="cc3a5-115">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="cc3a5-115">RequiredVersion</span></span>
- <span data-ttu-id="cc3a5-116">Tag</span><span class="sxs-lookup"><span data-stu-id="cc3a5-116">Tag</span></span>
- <span data-ttu-id="cc3a5-117">Includes</span><span class="sxs-lookup"><span data-stu-id="cc3a5-117">Includes</span></span>
- <span data-ttu-id="cc3a5-118">DscResource</span><span class="sxs-lookup"><span data-stu-id="cc3a5-118">DscResource</span></span>
- <span data-ttu-id="cc3a5-119">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="cc3a5-119">RoleCapability</span></span>
- <span data-ttu-id="cc3a5-120">Befehl</span><span class="sxs-lookup"><span data-stu-id="cc3a5-120">Command</span></span>
- <span data-ttu-id="cc3a5-121">Filter</span><span class="sxs-lookup"><span data-stu-id="cc3a5-121">Filter</span></span>

<span data-ttu-id="cc3a5-122">Wenn Sie nur spezifische DSC-Ressourcen im Katalog suchen, können Sie das Cmdlet [Find-DscResource] ausführen.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-122">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="cc3a5-123">„Find-DscResource“ gibt Daten zu DSC-Ressourcen zurück, die im Katalog enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-123">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="cc3a5-124">Da DSC-Ressourcen immer als Teil eines Moduls geliefert werden, müssen Sie [Install-Module][] ausführen, um diese DSC-Ressourcen zu installieren.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-124">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-packages-in-the-powershell-gallery"></a><span data-ttu-id="cc3a5-125">Informationen Paketen im PowerShell-Katalog</span><span class="sxs-lookup"><span data-stu-id="cc3a5-125">Learning about packages in the PowerShell Gallery</span></span>

<span data-ttu-id="cc3a5-126">Wenn Sie ein Paket ermittelt haben, an dem Sie interessiert sind, möchten Sie möglicherweise weitere Informationen dazu erhalten.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-126">Once you've identified a package that you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="cc3a5-127">Sehen Sie sich zu diesem Zweck die Katalogseite dieses bestimmten Pakets an.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-127">You can do this by examining that package's specific page on the Gallery.</span></span> <span data-ttu-id="cc3a5-128">Dort finden Sie alle Metadaten, die mit dem Paket hochgeladen wurden.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-128">On that page, you'll be able to see all of the metadata uploaded with the package.</span></span> <span data-ttu-id="cc3a5-129">Diese Metadaten werden vom Autor des Pakets bereitgestellt und nicht von Microsoft überprüft.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-129">This metadata is provided by the package's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="cc3a5-130">Der Besitzer des Pakets ist eng an das Katalog-Konto gebunden, das für die Veröffentlichung des Pakets verwendet wurde, und ist vertrauenswürdiger als das Feld „Autor“.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-130">The Owner of the package is strongly tied to the Gallery account used to publish the package, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="cc3a5-131">Wenn Sie ein Paket entdecken, das Ihrer Meinung nach nicht mit guten Absichten veröffentlicht wurde, klicken Sie auf der Seite dieses Pakets auf **Missbrauch melden**.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-131">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

<span data-ttu-id="cc3a5-132">Wenn Sie [Find-Module][] oder [Find-Script][] ausführen, können Sie diese Daten im zurückgegebenen PSGetModuleInfo-Objekt anzeigen.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-132">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="cc3a5-133">Die Ausführung von `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` gibt beispielsweise</span><span class="sxs-lookup"><span data-stu-id="cc3a5-133">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="cc3a5-134">Daten für das PSReadLine-Modul im Katalog zurück.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-134">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-packages-from-the-powershell-gallery"></a><span data-ttu-id="cc3a5-135">Herunterladen von Paketen aus dem PowerShell-Katalog</span><span class="sxs-lookup"><span data-stu-id="cc3a5-135">Downloading packages from the PowerShell Gallery</span></span>

<span data-ttu-id="cc3a5-136">Wir empfehlen den folgenden Prozess für das Herunterladen von Paketen aus dem PowerShell-Katalog:</span><span class="sxs-lookup"><span data-stu-id="cc3a5-136">We encourage the following process when downloading packages from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="cc3a5-137">Überprüfen</span><span class="sxs-lookup"><span data-stu-id="cc3a5-137">Inspect</span></span>

<span data-ttu-id="cc3a5-138">Um ein Paket zur Überprüfung aus dem Katalog herunterzuladen, führen Sie je nach Pakettyp entweder das Cmdlet [Save-Module][] oder das Cmdlet [Save-Script][] aus.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-138">To download a package from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the package type.</span></span> <span data-ttu-id="cc3a5-139">Dadurch können Sie das Paket lokal speichern, ohne es zu installieren, und den Paketinhalt überprüfen.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-139">This lets you save the package locally without installing it, and inspect the package contents.</span></span> <span data-ttu-id="cc3a5-140">Denken Sie daran, das gespeicherte Paket später manuell zu löschen.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-140">Remember to delete the saved package manually.</span></span>

<span data-ttu-id="cc3a5-141">Einige dieser Pakete wurden von Microsoft erstellt, andere stammen aus der PowerShell-Community.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-141">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="cc3a5-142">Microsoft empfiehlt, dass Sie den Inhalt und den Code der Pakete in diesem Katalog vor der Installation überprüfen.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-142">Microsoft recommends that you review the contents and code of packages on this gallery prior to installation.</span></span>

<span data-ttu-id="cc3a5-143">Wenn Sie ein Paket entdecken, das Ihrer Meinung nach nicht mit guten Absichten veröffentlicht wurde, klicken Sie auf der Seite dieses Pakets auf **Missbrauch melden**.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-143">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

### <a name="install"></a><span data-ttu-id="cc3a5-144">Installation</span><span class="sxs-lookup"><span data-stu-id="cc3a5-144">Install</span></span>

<span data-ttu-id="cc3a5-145">Um ein Paket aus dem Katalog für die Verwendung zu installieren, führen Sie je nach Pakettyp das Cmdlet [Install-Module][] oder das Cmdlet [Install-Script][] aus.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-145">To install a package from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the package type.</span></span>

<span data-ttu-id="cc3a5-146">[Install-Module][] installiert das Modul standardmäßig in `$env:ProgramFiles\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-146">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="cc3a5-147">Dafür ist ein Administratorkonto erforderlich.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-147">This requires an administrator account.</span></span> <span data-ttu-id="cc3a5-148">Wenn Sie den Parameter `-Scope CurrentUser` hinzufügen, wird das Modul in `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` installiert.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-148">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="cc3a5-149">[Install-Script][] installiert das Skript standardmäßig in `$env:ProgramFiles\WindowsPowerShell\Scripts`.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-149">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="cc3a5-150">Dafür ist ein Administratorkonto erforderlich.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-150">This requires an administrator account.</span></span> <span data-ttu-id="cc3a5-151">Wenn Sie den Parameter `-Scope CurrentUser` hinzufügen, wird das Skript in `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` installiert.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-151">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="cc3a5-152">[Install-Module][] und [Install-Script][] installieren standardmäßig die neueste Version eines Pakets.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-152">By default, [Install-Module][] and [Install-Script][] installs the most current version of a package.</span></span>
<span data-ttu-id="cc3a5-153">Um eine ältere Version des Pakets zu installieren, fügen Sie den Parameter `-RequiredVersion` hinzu.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-153">To install an older version of the package, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="cc3a5-154">Bereitstellen</span><span class="sxs-lookup"><span data-stu-id="cc3a5-154">Deploy</span></span>

<span data-ttu-id="cc3a5-155">Klicken Sie auf der Detailseite des Pakets auf **In Azure Automation bereitstellen**, um ein Paket aus dem PowerShell-Katalog in Azure Automation bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-155">To deploy a package from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the package details page.</span></span> <span data-ttu-id="cc3a5-156">Sie werden zum Azure-Verwaltungsportal umgeleitet, wo Sie sich mit den Anmeldeinformationen Ihres Azure-Kontos anmelden.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-156">You will be redirected to the Azure Management Portal where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="cc3a5-157">Beachten Sie, dass das Bereitstellen von Paketen mit Abhängigkeiten alle Abhängigkeiten in Azure Automation bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-157">Note that deploying packages with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="cc3a5-158">Sie können die Schaltfläche „In Azure Automation bereitstellen“ deaktivieren, indem Sie den Paketmetadaten das Tag **AzureAutomationNotSupported** hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-158">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your package metadata.</span></span>

<span data-ttu-id="cc3a5-159">Weitere Informationen zu Azure Automation finden Sie in der [Azure Automation](/azure/automation)-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-159">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-packages-from-the-powershell-gallery"></a><span data-ttu-id="cc3a5-160">Aktualisieren von Paketen aus dem PowerShell-Katalog</span><span class="sxs-lookup"><span data-stu-id="cc3a5-160">Updating packages from the PowerShell Gallery</span></span>

<span data-ttu-id="cc3a5-161">Führen Sie zum Aktualisieren der aus dem PowerShell-Katalog installierten Pakete das Cmdlet [Update-Module][] oder das Cmdlet [Update-Script][] aus.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-161">To update packages installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="cc3a5-162">[Update-Module][] versucht, jedes mithilfe von [Install-Module][] installierte Modul zu aktualisieren, wenn es ohne zusätzliche Parameter ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-162">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="cc3a5-163">Um Module einzeln zu aktualisieren, fügen Sie den Parameter `-Name` hinzu.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-163">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="cc3a5-164">Ähnlich versucht [Update-Script][], jedes durch Ausführung von [Install-Script][] installierte Skript zu aktualisieren, wenn es ohne zusätzliche Parameter ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-164">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="cc3a5-165">Um Skripts einzeln zu aktualisieren, fügen Sie den Parameter `-Name` hinzu.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-165">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="cc3a5-166">Auflisten von aus dem PowerShell-Katalog installierten Paketen</span><span class="sxs-lookup"><span data-stu-id="cc3a5-166">List packages that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="cc3a5-167">Führen Sie das Cmdlet [Get-InstalledModule][] aus, um herauszufinden, welche Module Sie aus dem PowerShell-Katalog installiert haben.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-167">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="cc3a5-168">Dieser Befehl listet alle Module auf, die direkt aus dem PowerShell-Katalog auf Ihrem System installiert wurden.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-168">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="cc3a5-169">Um herauszufinden, welche Skripts Sie aus dem PowerShell-Katalog installiert haben, führen Sie das Cmdlet [Get-InstalledScript][] aus.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-169">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="cc3a5-170">Dieser Befehl listet alle Skripts auf, die direkt aus dem PowerShell-Katalog auf Ihrem System installiert wurden.</span><span class="sxs-lookup"><span data-stu-id="cc3a5-170">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script
