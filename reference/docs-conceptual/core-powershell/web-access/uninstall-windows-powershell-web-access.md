---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Deinstallieren von Windows PowerShell Web Access
ms.openlocfilehash: 7231d5eadceda8e3b28d9a81c2b5dcbe43680ff2
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
#  <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="64cc2-103">Deinstallieren von Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="64cc2-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="64cc2-104">Aktualisiert: 24. Juni 2013</span><span class="sxs-lookup"><span data-stu-id="64cc2-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="64cc2-105">Gilt für: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="64cc2-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="64cc2-106">Führen Sie die Schritte in diesem Thema aus, um die Windows PowerShell Web Access-Website und die Anwendung vom Gatewayserver zu löschen, auf dem entweder Windows Server 2012 R2 oder Windows Server 2012 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="64cc2-106">Follow steps in this topic to delete the Windows PowerShell Web Access website and application from the gateway server that is running either Windows Server 2012 R2 or Windows Server 2012.</span></span> <span data-ttu-id="64cc2-107">Benachrichtigen Sie zuvor die Benutzer der webbasierten Konsole, die Sie von der Website entfernen möchten.</span><span class="sxs-lookup"><span data-stu-id="64cc2-107">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<a href="" id="BKMK_uninstall"></a>

------------------------------------------------------------------------

<span data-ttu-id="64cc2-108">Führen Sie vor dem Deinstallieren von Windows PowerShell Web Access vom Gatewayserver entweder das Cmdlet <span class="code">Uninstall-PswaWebApplication</span> aus, um die Website und die Windows PowerShell Web Access-Webanwendungen zu entfernen, oder verwenden Sie das IIS-Manager-Verfahren unter [So löschen Sie die Windows PowerShell Web Access-Website und -Webanwendungen mit IIS Manager](#BKMK_delsite).</span><span class="sxs-lookup"><span data-stu-id="64cc2-108">Before you uninstall Windows PowerShell Web Access from the gateway server, either run the <span class="code">Uninstall-PswaWebApplication</span> cmdlet to remove the website and Windows PowerShell Web Access web applications, or use the IIS Manager procedure, [To delete the Windows PowerShell Web Access website and web applications by using IIS Manager](#BKMK_delsite).</span></span>

<span data-ttu-id="64cc2-109">Bei der Deinstallation von Windows PowerShell Web Access werden IIS oder andere Features, die automatisch installiert wurden, nicht deinstalliert, weil diese von Windows PowerShell Web Access zur Ausführung benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="64cc2-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span> <span data-ttu-id="64cc2-110">Beim Deinstallationsvorgang bleiben die Features unangetastet, mit denen für Windows PowerShell Web Access eine Abhängigkeit besteht. Sie können diese Features bei Bedarf separat deinstallieren.</span><span class="sxs-lookup"><span data-stu-id="64cc2-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

<span data-ttu-id="64cc2-111"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Empfohlene (schnelle) Deinstallation</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="64cc2-111"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Recommended (quick) uninstallation</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="64cc2-112">Mit den in diesem Abschnitt beschriebenen Verfahren können Sie die Windows PowerShell Web Access-Webanwendung und die Windows PowerShell Web Access-Funktion mit Windows PowerShell-Cmdlets deinstallieren.</span><span class="sxs-lookup"><span data-stu-id="64cc2-112">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using Windows PowerShell cmdlets.</span></span>

###

<span data-ttu-id="64cc2-113"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Schritt 1: Löschen der Webanwendung</span></a></span><span class="sxs-lookup"><span data-stu-id="64cc2-113"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Delete the web application</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="64cc2-114">Wenn Sie Ihre eigenen, benutzerdefinierten Websitenamen angegeben haben, fügen Sie dem Befehl den <span class="code">WebsiteName</span>-Parameter hinzu, und geben Sie den Namen der Website an.</span><span class="sxs-lookup"><span data-stu-id="64cc2-114">If you have specified your own, custom website name, add the <span class="code">WebsiteName</span> parameter to your command, and specify the website name.</span></span> <span data-ttu-id="64cc2-115">Wenn Sie eine benutzerdefinierte Webanwendung (und nicht die Standardanwendung **pswa**) verwendet haben, fügen Sie dem Befehl den <span class="code">WebApplicationName</span>-Parameter hinzu, und geben Sie den Namen der Webanwendung an.</span><span class="sxs-lookup"><span data-stu-id="64cc2-115">If you have used a custom web application (not the default application, **pswa**, add the <span class="code">WebApplicationName</span> parameter to your command, and specify the name of the web application.</span></span>

#### <a name="to-delete-the-website-and-web-applications-by-using-the-uninstall-pswawebapplication-cmdlet"></a><span data-ttu-id="64cc2-116">So löschen Sie die Website und Webanwendungen mithilfe des Uninstall-PswaWebApplication-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="64cc2-116">To delete the website and web applications by using the Uninstall-PswaWebApplication cmdlet</span></span>

1.  <span data-ttu-id="64cc2-117">Öffnen Sie eine Windows PowerShell-Sitzung, indem Sie einen der folgenden Schritte durchführen.</span><span class="sxs-lookup"><span data-stu-id="64cc2-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="64cc2-118">Klicken Sie auf dem Windows-Desktop mit der rechten Maustaste auf der Taskleiste auf **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="64cc2-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="64cc2-119">Klicken Sie auf der Windows-Startseite**** auf **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="64cc2-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="64cc2-120">Geben Sie **Uninstall-PswaWebApplication** ein, und drücken Sie dann die **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="64cc2-120">Type **Uninstall-PswaWebApplication**, and then press **Enter**.</span></span>

3.  <span data-ttu-id="64cc2-121">Fügen Sie dem Cmdlet den <span class="code">DeleteTestCertificate</span>-Parameter hinzu, falls Sie ein Testzertifikat verwenden. Dies ist im folgenden Beispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="64cc2-121">If you are using a test certificate, add the <span class="code">DeleteTestCertificate</span> parameter to the cmdlet, as shown in the following example.</span></span>

    [<span data-ttu-id="64cc2-122">Copy</span><span class="sxs-lookup"><span data-stu-id="64cc2-122">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_28147344-ab2f-49e7-b1c2-6dbe649d4366'); "Copy to clipboard.")

        Uninstall-PswaWebApplication -DeleteTestCertificate

###

<span data-ttu-id="64cc2-123"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Schritt 2: Deinstallieren von Windows PowerShell Web Access</span></a></span><span class="sxs-lookup"><span data-stu-id="64cc2-123"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Uninstall Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-uninstall-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a><span data-ttu-id="64cc2-124">So deinstallieren Sie Windows PowerShell Web Access mithilfe von Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="64cc2-124">To uninstall Windows PowerShell Web Access by using Windows PowerShell cmdlets</span></span>

1.  <span data-ttu-id="64cc2-125">Öffnen Sie eine Windows PowerShell-Sitzung mit erhöhten Benutzerrechten, indem Sie einen der folgenden Schritte durchführen.</span><span class="sxs-lookup"><span data-stu-id="64cc2-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="64cc2-126">Wenn bereits eine Sitzung geöffnet ist, fahren Sie mit dem nächsten Schritt fort.</span><span class="sxs-lookup"><span data-stu-id="64cc2-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="64cc2-127">Klicken Sie auf dem Windows-Desktop mit der rechten Maustaste in der Taskleiste auf **Windows PowerShell** und anschließend auf **Als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="64cc2-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="64cc2-128">Klicken Sie auf dem Windows-**Startbildschirm** mit der rechten Maustaste auf **Windows PowerShell**, und klicken Sie anschließend auf **Als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="64cc2-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="64cc2-129">Geben Sie Folgendes ein, und drücken Sie dann die **EINGABETASTE**, wobei *computer_name* für einen Remoteserver steht, von dem Sie Windows PowerShell Web Access entfernen möchten.</span><span class="sxs-lookup"><span data-stu-id="64cc2-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="64cc2-130">Mit dem Parameter <span class="code">-Restart</span> werden Zielserver automatisch neu gestartet, falls dies für die Entfernung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="64cc2-130">The <span class="code">-Restart</span> parameter automatically restarts destination servers if required by the removal.</span></span>

    [<span data-ttu-id="64cc2-131">Copy</span><span class="sxs-lookup"><span data-stu-id="64cc2-131">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7b534520-f292-471f-89e3-a1079c03e369'); "Copy to clipboard.")

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="64cc2-132">Zum Entfernen von Rollen oder Features von einer Offline-VHD müssen Sie sowohl den <span class="code">ComputerName</span>-Parameter als auch den <span class="code">VHD</span>-Parameter hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="64cc2-132">To remove roles and features from an offline VHD, you must add both the <span class="code">-ComputerName</span> parameter and the <span class="code">-VHD</span> parameter.</span></span> <span data-ttu-id="64cc2-133">Der <span class="code">ComputerName</span>-Parameter enthält den Namen des Servers, auf dem die VHD eingebunden werden soll. Der <span class="code">VHD</span>-Parameter enthält den Pfad zur VHD-Datei auf dem angegebenen Server.</span><span class="sxs-lookup"><span data-stu-id="64cc2-133">The <span class="code">-ComputerName</span> parameter contains the name of the server on which to mount the VHD, and the <span class="code">-VHD</span> parameter contains the path to the VHD file on the specified server.</span></span>

    [<span data-ttu-id="64cc2-134">Copy</span><span class="sxs-lookup"><span data-stu-id="64cc2-134">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_5d8f91ee-b91a-4653-b7df-e745187fd72d'); "Copy to clipboard.")

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

3.  <span data-ttu-id="64cc2-135">Vergewissern Sie sich nach Abschluss der Entfernung, ob Windows PowerShell Web Access wirklich entfernt wurde. Öffnen Sie dazu im Server-Manager die Seite **Alle Server**, wählen Sie einen Server aus, von dem Sie das Feature entfernt haben, und zeigen Sie auf der Seite für den ausgewählten Server die Kachel **Rollen und Features** an.</span><span class="sxs-lookup"><span data-stu-id="64cc2-135">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span> <span data-ttu-id="64cc2-136">Sie können auch das Cmdlet <span class="code">Get-WindowsFeature</span> für den ausgewählten Server (Get-WindowsFeature -ComputerName &lt;*Computername*&gt;) ausführen, um eine Liste der Rollen und Features anzuzeigen, die auf dem Server installiert sind.</span><span class="sxs-lookup"><span data-stu-id="64cc2-136">You can also run the <span class="code">Get-WindowsFeature</span> cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

<span data-ttu-id="64cc2-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Benutzerdefinierte Deinstallation</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="64cc2-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Custom uninstallation</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="64cc2-138">Mit den in diesem Abschnitt beschriebenen Verfahren können Sie die Windows PowerShell Web Access-Webanwendung und die Windows PowerShell Web Access-Funktion mit dem Assistenten zum Entfernen von Rollen und Features im Server-Manager und der IIS Manager-Konsole deinstallieren.</span><span class="sxs-lookup"><span data-stu-id="64cc2-138">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

###

<span data-ttu-id="64cc2-139"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Schritt 1: Löschen der Webanwendung</span></a></span><span class="sxs-lookup"><span data-stu-id="64cc2-139"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Delete the web application</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-delete-the-windows-powershell-web-access-website-and-web-applications-by-using-iis-manager"></a><span data-ttu-id="64cc2-140">So löschen Sie die Windows PowerShell Web Access-Website und -Webanwendungen mithilfe des IIS-Managers</span><span class="sxs-lookup"><span data-stu-id="64cc2-140">To delete the Windows PowerShell Web Access website and web applications by using IIS Manager</span></span>

1.  <span data-ttu-id="64cc2-141">Öffnen Sie die IIS-Manager-Konsole, indem Sie eine der folgenden Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="64cc2-141">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="64cc2-142">Wenn die Konsole bereits geöffnet ist, fahren Sie mit dem nächsten Schritt fort.</span><span class="sxs-lookup"><span data-stu-id="64cc2-142">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="64cc2-143">Starten Sie auf dem Windows-Desktop den Server-Manager, indem Sie in der Windows-Taskleiste auf **Server-Manager** klicken.</span><span class="sxs-lookup"><span data-stu-id="64cc2-143">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="64cc2-144">Klicken Sie im Menü **Tools** im Server-Manager auf **Internetinformationsdienste-Manager (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="64cc2-144">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="64cc2-145">Geben Sie auf dem Windows-**Startbildschirm** einen beliebigen Teil des Namens **Internetinformationsdienste-Manager (IIS)** ein.</span><span class="sxs-lookup"><span data-stu-id="64cc2-145">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="64cc2-146">Klicken Sie auf die Verknüpfung, wenn diese in den Ergebnissen unter **Apps** angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="64cc2-146">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="64cc2-147">Wählen Sie im IIS-Manager-Strukturbereich die Website aus, auf der die Windows PowerShell Web Access-Webanwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="64cc2-147">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

3.  <span data-ttu-id="64cc2-148">Klicken Sie im **Aktionsbereich** unter **Website verwalten** auf **Beenden**.</span><span class="sxs-lookup"><span data-stu-id="64cc2-148">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

4.  <span data-ttu-id="64cc2-149">Klicken Sie im Strukturbereich mit der rechten Maustaste auf die Webanwendung der Website, von der die Windows PowerShell Web Access-Webanwendung ausgeführt wird, und klicken Sie dann auf **Entfernen**.</span><span class="sxs-lookup"><span data-stu-id="64cc2-149">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

5.  <span data-ttu-id="64cc2-150">Wählen Sie im Strukturbereich die Option **Anwendungspools** und dann den Windows PowerShell Web Access-Anwendungsordner aus, klicken Sie im **Aktionsbereich** auf **Beenden**, und klicken Sie im Inhaltsbereich dann auf **Entfernen**.</span><span class="sxs-lookup"><span data-stu-id="64cc2-150">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

6.  <span data-ttu-id="64cc2-151">Schließen Sie den IIS-Manager.</span><span class="sxs-lookup"><span data-stu-id="64cc2-151">Close IIS Manager.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="64cc2-152"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Hinweis </span></span><span class="sxs-lookup"><span data-stu-id="64cc2-152"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="64cc2-153">Das Zertifikat wird während der Deinstallation nicht gelöscht.</span><span class="sxs-lookup"><span data-stu-id="64cc2-153">The certificate is not deleted during uninstallation.</span></span> <span data-ttu-id="64cc2-154">Wenn Sie ein selbstsigniertes Zertifikat erstellt oder ein Testzertifikat verwendet haben und dieses Zertifikat nun entfernen möchten, müssen Sie es im IIS-Manager löschen.</span><span class="sxs-lookup"><span data-stu-id="64cc2-154">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span></p></td>
    </tr>
    </tbody>
    </table>

###

<span data-ttu-id="64cc2-155"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Schritt 2: Deinstallieren von Windows PowerShell Web Access</span></a></span><span class="sxs-lookup"><span data-stu-id="64cc2-155"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Uninstall Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-uninstall-windows-powershell-web-access-by-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="64cc2-156">So deinstallieren Sie Windows PowerShell Web Access mithilfe des Assistenten zum Entfernen von Rollen und Features</span><span class="sxs-lookup"><span data-stu-id="64cc2-156">To uninstall Windows PowerShell Web Access by using the Remove Roles and Features Wizard</span></span>

1.  <span data-ttu-id="64cc2-157">Wenn der Server-Manager bereits geöffnet ist, fahren Sie mit dem nächsten Schritt fort.</span><span class="sxs-lookup"><span data-stu-id="64cc2-157">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="64cc2-158">Ist der Server-Manager noch nicht geöffnet, öffnen Sie ihn mit einer der folgenden Aktionen.</span><span class="sxs-lookup"><span data-stu-id="64cc2-158">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="64cc2-159">Starten Sie auf dem Windows-Desktop den Server-Manager, indem Sie in der Windows-Taskleiste auf **Server-Manager** klicken.</span><span class="sxs-lookup"><span data-stu-id="64cc2-159">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="64cc2-160">Klicken Sie auf der Windows-Startseite**** auf **Server-Manager**.</span><span class="sxs-lookup"><span data-stu-id="64cc2-160">On the Windows **Start** screen, click **Server Manager**.</span></span>

2.  <span data-ttu-id="64cc2-161">Klicken Sie im Menü **Verwalten** auf **Rollen und Funktionen entfernen**.</span><span class="sxs-lookup"><span data-stu-id="64cc2-161">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

3.  <span data-ttu-id="64cc2-162">Wählen Sie auf der Seite **Zielserver auswählen** den Server oder die Offline-VHD aus, von dem bzw. der Sie das Feature entfernen möchten.</span><span class="sxs-lookup"><span data-stu-id="64cc2-162">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="64cc2-163">Um eine Offline-VHD auszuwählen, müssen Sie zuerst den Server auswählen, auf dem die VHD eingebunden werden soll. Wählen Sie anschließend die VHD-Datei aus.</span><span class="sxs-lookup"><span data-stu-id="64cc2-163">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="64cc2-164">Klicken Sie nach dem Auswählen des Zielservers auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64cc2-164">After you have selected the destination server, click **Next**.</span></span>

4.  <span data-ttu-id="64cc2-165">Klicken Sie erneut auf **Weiter**, um auf die Seite **Features entfernen** zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="64cc2-165">Click **Next** again to skip to the **Remove features** page.</span></span>

5.  <span data-ttu-id="64cc2-166">Deaktivieren Sie das Kontrollkästchen unter **Windows PowerShell Web Access**, und klicken Sie auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64cc2-166">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

6.  <span data-ttu-id="64cc2-167">Klicken Sie auf der Seite **Entfernungsauswahl bestätigen** auf **Entfernen**.</span><span class="sxs-lookup"><span data-stu-id="64cc2-167">On the **Confirm removal selections** page, click **Remove**.</span></span>

<span data-ttu-id="64cc2-168"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Siehe auch</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="64cc2-168"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="64cc2-169">[Installieren und Verwenden von Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[Hilfe zum IIS-Manager 7.0](https://technet.microsoft.com/library/cc732664.aspx)</span><span class="sxs-lookup"><span data-stu-id="64cc2-169">[Install and Use Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[IIS Manager 7.0 Help](https://technet.microsoft.com/library/cc732664.aspx)</span></span>

<span data-ttu-id="64cc2-170"><span>Show:</span> Inherited Protected</span><span class="sxs-lookup"><span data-stu-id="64cc2-170"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="64cc2-171"><span class="stdr-votetitle">War diese Seite hilfreich?</span></span><span class="sxs-lookup"><span data-stu-id="64cc2-171"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="64cc2-172">Ja Nein</span><span class="sxs-lookup"><span data-stu-id="64cc2-172">Yes No</span></span>

<span data-ttu-id="64cc2-173">Zusätzliches Feedback?</span><span class="sxs-lookup"><span data-stu-id="64cc2-173">Additional feedback?</span></span>

<span data-ttu-id="64cc2-174"><span class="stdr-count"><span class="stdr-charcnt">1.500</span> verbleibende Zeichen</span> Senden Diesen Schritt überspringen</span><span class="sxs-lookup"><span data-stu-id="64cc2-174"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="64cc2-175"><span class="stdr-thankyou">Vielen Dank!</span></span><span class="sxs-lookup"><span data-stu-id="64cc2-175"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="64cc2-176"><span class="stdr-appreciate">Wir schätzen Ihr Feedback.</span></span><span class="sxs-lookup"><span data-stu-id="64cc2-176"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="64cc2-177">Profil verwalten</span><span class="sxs-lookup"><span data-stu-id="64cc2-177">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="64cc2-178"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Feedback zur Website</a> Feedback zur Website</span><span class="sxs-lookup"><span data-stu-id="64cc2-178"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="64cc2-179"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="64cc2-179"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="64cc2-180">Teilen Sie uns Ihre Erfahrungen mit.</span><span class="sxs-lookup"><span data-stu-id="64cc2-180">Tell us about your experience...</span></span>

<span data-ttu-id="64cc2-181">Wurde die Seite schnell geladen?</span><span class="sxs-lookup"><span data-stu-id="64cc2-181">Did the page load quickly?</span></span>

<span data-ttu-id="64cc2-182"><span> Ja<span> </span></span> <span> Nein<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="64cc2-182"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="64cc2-183">Gefällt Ihnen das Design der Seite?</span><span class="sxs-lookup"><span data-stu-id="64cc2-183">Do you like the page design?</span></span>

<span data-ttu-id="64cc2-184"><span> Ja<span> </span></span> <span> Nein<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="64cc2-184"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="64cc2-185">Erzählen Sie uns mehr</span><span class="sxs-lookup"><span data-stu-id="64cc2-185">Tell us more</span></span>

-   [<span data-ttu-id="64cc2-186">Flash-Newsletter</span><span class="sxs-lookup"><span data-stu-id="64cc2-186">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="64cc2-187">So erreichen Sie uns</span><span class="sxs-lookup"><span data-stu-id="64cc2-187">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="64cc2-188">Datenschutzbestimmungen</span><span class="sxs-lookup"><span data-stu-id="64cc2-188">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="64cc2-189">Nutzungsbedingungen</span><span class="sxs-lookup"><span data-stu-id="64cc2-189">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="64cc2-190">Marken</span><span class="sxs-lookup"><span data-stu-id="64cc2-190">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="64cc2-191">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="64cc2-191">© 2016 Microsoft</span></span>

<span data-ttu-id="64cc2-192">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="64cc2-192">© 2016 Microsoft</span></span>

<span data-ttu-id="64cc2-193">Die Lizenz für Drittanbieterskripts oder Code, die mit dieser Website verlinkt oder über Verweise verbunden sind, wird Ihnen von den Codeeigentümern erteilt, nicht von Microsoft.</span><span class="sxs-lookup"><span data-stu-id="64cc2-193">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="64cc2-194">Die ASP.NET Ajax CDN-Nutzungsbedingungen finden Sie unter http://www.asp.net/ajaxlibrary/CDN.ashx.</span><span class="sxs-lookup"><span data-stu-id="64cc2-194">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

