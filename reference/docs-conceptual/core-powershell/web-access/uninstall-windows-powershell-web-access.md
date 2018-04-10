---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: Deinstallieren von Windows PowerShell Web Access
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="81e37-103">Deinstallieren von Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="81e37-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="81e37-104">Aktualisiert: 24. Juni 2013</span><span class="sxs-lookup"><span data-stu-id="81e37-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="81e37-105">Gilt für: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="81e37-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="81e37-106">Mit den Schritten in diesem Thema entfernen Sie die Windows PowerShell Web Access-Website und die zugehörige Anwendung von dem Gatewayserver, auf dem diese installiert sind.</span><span class="sxs-lookup"><span data-stu-id="81e37-106">The steps in this topic remove the Windows PowerShell Web Access website and corresponding application from the gateway server where it is installed.</span></span>

## <a name="notify-users"></a><span data-ttu-id="81e37-107">Benachrichtigen von Benutzern</span><span class="sxs-lookup"><span data-stu-id="81e37-107">Notify users</span></span>

<span data-ttu-id="81e37-108">Benachrichtigen Sie zuvor die Benutzer der webbasierten Konsole, die Sie von der Website entfernen möchten.</span><span class="sxs-lookup"><span data-stu-id="81e37-108">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<span data-ttu-id="81e37-109">Bei der Deinstallation von Windows PowerShell Web Access werden IIS oder andere Features, die automatisch installiert wurden, nicht deinstalliert, weil diese von Windows PowerShell Web Access zur Ausführung benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="81e37-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span>
<span data-ttu-id="81e37-110">Beim Deinstallationsvorgang bleiben die Features unangetastet, mit denen für Windows PowerShell Web Access eine Abhängigkeit besteht. Sie können diese Features bei Bedarf separat deinstallieren.</span><span class="sxs-lookup"><span data-stu-id="81e37-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

## <a name="recommended-quick-uninstallation"></a><span data-ttu-id="81e37-111">Empfohlene (schnelle) Deinstallation</span><span class="sxs-lookup"><span data-stu-id="81e37-111">Recommended (quick) uninstallation</span></span>

<span data-ttu-id="81e37-112">Mit den in diesem Abschnitt beschriebenen Verfahren können Sie Folgendes deinstallieren:</span><span class="sxs-lookup"><span data-stu-id="81e37-112">Procedures in this section help you uninstall both:</span></span>

- <span data-ttu-id="81e37-113">Die Windows PowerShell Web Access-Anwendung und</span><span class="sxs-lookup"><span data-stu-id="81e37-113">the Windows PowerShell Web Access web application, and</span></span>
- <span data-ttu-id="81e37-114">das Windows PowerShell Web Access-Feature</span><span class="sxs-lookup"><span data-stu-id="81e37-114">the Windows PowerShell Web Access feature</span></span>

<span data-ttu-id="81e37-115">, indem Sie Windows PowerShell-Cmdlets verwenden.</span><span class="sxs-lookup"><span data-stu-id="81e37-115">by using Windows PowerShell cmdlets.</span></span>

### <a name="step-1-delete-the-web-application-using-cmdlets"></a><span data-ttu-id="81e37-116">Schritt 1: Löschen der Webanwendung mithilfe von Cmdlets</span><span class="sxs-lookup"><span data-stu-id="81e37-116">Step 1: Delete the web application using cmdlets</span></span>

1. <span data-ttu-id="81e37-117">Öffnen Sie eine Windows PowerShell-Sitzung, indem Sie einen der folgenden Schritte durchführen.</span><span class="sxs-lookup"><span data-stu-id="81e37-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="81e37-118">Klicken Sie auf dem Windows-Desktop mit der rechten Maustaste auf der Taskleiste auf **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="81e37-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="81e37-119">Klicken Sie auf der Windows-**Startseite** auf **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="81e37-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2. <span data-ttu-id="81e37-120">Geben Sie `Uninstall-PswaWebApplication` ein, und drücken Sie dann die **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="81e37-120">Type `Uninstall-PswaWebApplication`, and then press **Enter**.</span></span>
   1. <span data-ttu-id="81e37-121">Wenn Sie Ihre eigenen, benutzerdefinierten Websitenamen angegeben haben, fügen Sie dem Befehl den `-WebsiteName`-Parameter hinzu, und geben Sie den Namen der Website an.</span><span class="sxs-lookup"><span data-stu-id="81e37-121">If you have specified your own, custom website name, add the `-WebsiteName` parameter to your command, and specify the website name.</span></span>

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. <span data-ttu-id="81e37-122">Wenn Sie eine benutzerdefinierte Webanwendung (und nicht die Standardanwendung **pswa**) verwendet haben, fügen Sie dem Befehl den `-WebApplicationName`-Parameter hinzu, und geben Sie den Namen der Webanwendung an.</span><span class="sxs-lookup"><span data-stu-id="81e37-122">If you have used a custom web application (not the default application, **pswa**, add the `-WebApplicationName` parameter to your command, and specify the name of the web application.</span></span>

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. <span data-ttu-id="81e37-123">Fügen Sie dem Cmdlet den Parameter `DeleteTestCertificate` hinzu, falls Sie ein Testzertifikat verwenden. Dies ist im folgenden Beispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="81e37-123">If you are using a test certificate, add the `DeleteTestCertificate` parameter to the cmdlet, as shown in the following example.</span></span>

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a><span data-ttu-id="81e37-124">Schritt 2: Deinstallieren von Windows PowerShell Web Access mithilfe von Cmdlets</span><span class="sxs-lookup"><span data-stu-id="81e37-124">Step 2: Uninstall Windows PowerShell Web Access using cmdlets</span></span>

1. <span data-ttu-id="81e37-125">Öffnen Sie eine Windows PowerShell-Sitzung mit erhöhten Benutzerrechten, indem Sie einen der folgenden Schritte durchführen.</span><span class="sxs-lookup"><span data-stu-id="81e37-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="81e37-126">Wenn bereits eine Sitzung geöffnet ist, fahren Sie mit dem nächsten Schritt fort.</span><span class="sxs-lookup"><span data-stu-id="81e37-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="81e37-127">Klicken Sie auf dem Windows-Desktop mit der rechten Maustaste in der Taskleiste auf **Windows PowerShell** und anschließend auf **Als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="81e37-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="81e37-128">Klicken Sie auf dem Windows-**Startbildschirm** mit der rechten Maustaste auf **Windows PowerShell**, und klicken Sie anschließend auf **Als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="81e37-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

1. <span data-ttu-id="81e37-129">Geben Sie Folgendes ein, und drücken Sie dann die **EINGABETASTE**, wobei *computer_name* für einen Remoteserver steht, von dem Sie Windows PowerShell Web Access entfernen möchten.</span><span class="sxs-lookup"><span data-stu-id="81e37-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="81e37-130">Mit dem Parameter `-Restart` werden Zielserver automatisch neu gestartet, falls dies für die Entfernung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="81e37-130">The `-Restart` parameter automatically restarts destination servers if required by the removal.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="81e37-131">Zum Entfernen von Rollen oder Features von einer Offline-VHD müssen Sie die Parameter `-ComputerName` und `-VHD` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="81e37-131">To remove roles and features from an offline VHD, you must add both the `-ComputerName` parameter and the `-VHD` parameter.</span></span> <span data-ttu-id="81e37-132">Der Parameter `-ComputerName` enthält den Namen des Servers, auf dem die VHD eingebunden werden soll, und der Parameter `-VHD` enthält den Pfad zur VHD-Datei auf dem angegebenen Server.</span><span class="sxs-lookup"><span data-stu-id="81e37-132">The `-ComputerName` parameter contains the name of the server on which to mount the VHD, and the `-VHD` parameter contains the path to the VHD file on the specified server.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. <span data-ttu-id="81e37-133">Vergewissern Sie sich nach Abschluss der Entfernung, ob Windows PowerShell Web Access wirklich entfernt wurde. Öffnen Sie dazu im Server-Manager die Seite **Alle Server**, wählen Sie einen Server aus, von dem Sie das Feature entfernt haben, und zeigen Sie auf der Seite für den ausgewählten Server die Kachel **Rollen und Features** an.</span><span class="sxs-lookup"><span data-stu-id="81e37-133">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span>

    <span data-ttu-id="81e37-134">Sie können auch das `Get-WindowsFeature`-Cmdlet für den ausgewählten Server auswählen (Get-WindowsFeature -ComputerName &lt;*Computername*&gt;), um eine Liste der auf dem Server installierten Rollen und Features anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="81e37-134">You can also run the `Get-WindowsFeature` cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

## <a name="custom-uninstallation"></a><span data-ttu-id="81e37-135">Benutzerdefinierte Deinstallation</span><span class="sxs-lookup"><span data-stu-id="81e37-135">Custom uninstallation</span></span>

<span data-ttu-id="81e37-136">Mit den in diesem Abschnitt beschriebenen Verfahren können Sie die Windows PowerShell Web Access-Webanwendung und die Windows PowerShell Web Access-Funktion mit dem Assistenten zum Entfernen von Rollen und Features im Server-Manager und der IIS Manager-Konsole deinstallieren.</span><span class="sxs-lookup"><span data-stu-id="81e37-136">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

### <a name="step-1-delete-the-web-application-using-iis-manager"></a><span data-ttu-id="81e37-137">Schritt 1: Löschen der Webanwendung mithilfe des IIS-Managers</span><span class="sxs-lookup"><span data-stu-id="81e37-137">Step 1: Delete the web application using IIS Manager</span></span>


1. <span data-ttu-id="81e37-138">Öffnen Sie die IIS-Manager-Konsole, indem Sie eine der folgenden Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="81e37-138">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="81e37-139">Wenn die Konsole bereits geöffnet ist, fahren Sie mit dem nächsten Schritt fort.</span><span class="sxs-lookup"><span data-stu-id="81e37-139">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="81e37-140">Starten Sie auf dem Windows-Desktop den Server-Manager, indem Sie in der Windows-Taskleiste auf **Server-Manager** klicken.</span><span class="sxs-lookup"><span data-stu-id="81e37-140">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="81e37-141">Klicken Sie im Menü **Tools** im Server-Manager auf **Internetinformationsdienste-Manager (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="81e37-141">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="81e37-142">Geben Sie auf dem Windows-**Startbildschirm** einen beliebigen Teil des Namens **Internetinformationsdienste-Manager (IIS)** ein.</span><span class="sxs-lookup"><span data-stu-id="81e37-142">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="81e37-143">Klicken Sie auf die Verknüpfung, wenn diese in den Ergebnissen unter **Apps** angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="81e37-143">Click the shortcut when it is displayed in the **Apps** results.</span></span>

1. <span data-ttu-id="81e37-144">Wählen Sie im IIS-Manager-Strukturbereich die Website aus, auf der die Windows PowerShell Web Access-Webanwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="81e37-144">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

1. <span data-ttu-id="81e37-145">Klicken Sie im **Aktionsbereich** unter **Website verwalten** auf **Beenden**.</span><span class="sxs-lookup"><span data-stu-id="81e37-145">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

1. <span data-ttu-id="81e37-146">Klicken Sie im Strukturbereich mit der rechten Maustaste auf die Webanwendung der Website, von der die Windows PowerShell Web Access-Webanwendung ausgeführt wird, und klicken Sie dann auf **Entfernen**.</span><span class="sxs-lookup"><span data-stu-id="81e37-146">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

1. <span data-ttu-id="81e37-147">Wählen Sie im Strukturbereich die Option **Anwendungspools** und dann den Windows PowerShell Web Access-Anwendungsordner aus, klicken Sie im **Aktionsbereich** auf **Beenden**, und klicken Sie im Inhaltsbereich dann auf **Entfernen**.</span><span class="sxs-lookup"><span data-stu-id="81e37-147">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

1. <span data-ttu-id="81e37-148">Schließen Sie den IIS-Manager.</span><span class="sxs-lookup"><span data-stu-id="81e37-148">Close IIS Manager.</span></span>

> <span data-ttu-id="81e37-149">![Warnhinweis](images/SecurityNote.jpeg)**Hinweis**:</span><span class="sxs-lookup"><span data-stu-id="81e37-149">![Warning note](images/SecurityNote.jpeg)**Note**:</span></span>
>
> <span data-ttu-id="81e37-150">Das Zertifikat wird während der Deinstallation nicht gelöscht.</span><span class="sxs-lookup"><span data-stu-id="81e37-150">The certificate is not deleted during uninstallation.</span></span>
>
> <span data-ttu-id="81e37-151">Wenn Sie ein selbstsigniertes Zertifikat erstellt oder ein Testzertifikat verwendet haben und dieses Zertifikat nun entfernen möchten, müssen Sie es im IIS-Manager löschen.</span><span class="sxs-lookup"><span data-stu-id="81e37-151">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span>

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="81e37-152">Schritt 2: Deinstallieren von Windows PowerShell Web Access mithilfe des Assistenten zum Entfernen von Rollen und Features</span><span class="sxs-lookup"><span data-stu-id="81e37-152">Step 2: Uninstall Windows PowerShell Web Access using the Remove Roles and Features Wizard</span></span>

1. <span data-ttu-id="81e37-153">Wenn der Server-Manager bereits geöffnet ist, fahren Sie mit dem nächsten Schritt fort.</span><span class="sxs-lookup"><span data-stu-id="81e37-153">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="81e37-154">Ist der Server-Manager noch nicht geöffnet, öffnen Sie ihn mit einer der folgenden Aktionen.</span><span class="sxs-lookup"><span data-stu-id="81e37-154">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="81e37-155">Starten Sie auf dem Windows-Desktop den Server-Manager, indem Sie in der Windows-Taskleiste auf **Server-Manager** klicken.</span><span class="sxs-lookup"><span data-stu-id="81e37-155">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="81e37-156">Klicken Sie auf der Windows-**Startseite** auf **Server-Manager**.</span><span class="sxs-lookup"><span data-stu-id="81e37-156">On the Windows **Start** screen, click **Server Manager**.</span></span>

1. <span data-ttu-id="81e37-157">Klicken Sie im Menü **Verwalten** auf **Rollen und Funktionen entfernen**.</span><span class="sxs-lookup"><span data-stu-id="81e37-157">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

1. <span data-ttu-id="81e37-158">Wählen Sie auf der Seite **Zielserver auswählen** den Server oder die Offline-VHD aus, von dem bzw. der Sie das Feature entfernen möchten.</span><span class="sxs-lookup"><span data-stu-id="81e37-158">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="81e37-159">Um eine Offline-VHD auszuwählen, müssen Sie zuerst den Server auswählen, auf dem die VHD eingebunden werden soll. Wählen Sie anschließend die VHD-Datei aus.</span><span class="sxs-lookup"><span data-stu-id="81e37-159">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="81e37-160">Klicken Sie nach dem Auswählen des Zielservers auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="81e37-160">After you have selected the destination server, click **Next**.</span></span>

1. <span data-ttu-id="81e37-161">Klicken Sie erneut auf **Weiter**, um auf die Seite **Features entfernen** zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="81e37-161">Click **Next** again to skip to the **Remove features** page.</span></span>

1. <span data-ttu-id="81e37-162">Deaktivieren Sie das Kontrollkästchen unter **Windows PowerShell Web Access**, und klicken Sie auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="81e37-162">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

1. <span data-ttu-id="81e37-163">Klicken Sie auf der Seite **Entfernungsauswahl bestätigen** auf **Entfernen**.</span><span class="sxs-lookup"><span data-stu-id="81e37-163">On the **Confirm removal selections** page, click **Remove**.</span></span>

## <a name="see-also"></a><span data-ttu-id="81e37-164">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="81e37-164">See Also</span></span>

- [<span data-ttu-id="81e37-165">Install and Use Windows PowerShell Web Access (Installieren und Verwenden von Windows PowerShell Web Access)</span><span class="sxs-lookup"><span data-stu-id="81e37-165">Install and Use Windows PowerShell Web Access</span></span>](install-and-use-windows-powershell-web-access.md)
- [<span data-ttu-id="81e37-166">IIS Manager 7.0 Help (Hilfe zum IIS-Manager 7.0)</span><span class="sxs-lookup"><span data-stu-id="81e37-166">IIS Manager 7.0 Help</span></span>](https://technet.microsoft.com/library/cc732664.aspx)