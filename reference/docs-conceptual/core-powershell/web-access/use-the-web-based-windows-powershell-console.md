---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Verwendung der webbasierten Windows PowerShell-Konsole
ms.openlocfilehash: 48ed1646c00f909c4e950f197f51a30205060ef0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
#  <a name="use-the-web-based-windows-powershell-console"></a><span data-ttu-id="96f58-103">Verwendung der webbasierten Windows PowerShell-Konsole</span><span class="sxs-lookup"><span data-stu-id="96f58-103">Use the Web-based Windows PowerShell Console</span></span>

<span data-ttu-id="96f58-104">Aktualisiert: 24. Juni 2013</span><span class="sxs-lookup"><span data-stu-id="96f58-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="96f58-105">Gilt für: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="96f58-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="96f58-106">Windows PowerShell® Web Access ermöglicht Windows PowerShell®-Benutzern die Anmeldung bei einer SSL (Secure Sockets Layer )-gesicherten Website zur Verwendung von Windows PowerShell-Sitzungen, Cmdlets und Skripts zur Verwaltung eines Remotecomputers.</span><span class="sxs-lookup"><span data-stu-id="96f58-106">Windows PowerShell® Web Access lets Windows PowerShell® users sign in to a Secure Sockets Layer (SSL)-secured website to use Windows PowerShell sessions, cmdlets, and scripts to manage a remote computer.</span></span> <span data-ttu-id="96f58-107">Da die Windows PowerShell-Konsole in einem Webbrowser ausgeführt wird, kann sie auf verschiedensten Clientgeräten geöffnet werden, etwa auf Handys, Tabletcomputern, öffentlichen Kioskcomputern, Laptopcomputern und gemeinsam genutzten oder ausgeliehenen Computern.</span><span class="sxs-lookup"><span data-stu-id="96f58-107">Because the Windows PowerShell console runs in a web browser, it can be opened from a variety of client devices, including cell phones, tablet computers, public computing kiosks, laptop computers, or shared or borrowed computers.</span></span> <span data-ttu-id="96f58-108">Die webbasierte Windows PowerShell-Konsole steuert einen Remotecomputer, der von Benutzern im Zuge der Anmeldung angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="96f58-108">The web-based Windows PowerShell console is targeted at a remote computer that is specified by users as part of the sign-in process.</span></span> <span data-ttu-id="96f58-109">Dieser Artikel behandelt die Anmeldung für die ersten Schritte mit der webbasierten Windows PowerShell Web Access-Konsole.</span><span class="sxs-lookup"><span data-stu-id="96f58-109">This topic describes how to sign in to and start using the Windows PowerShell Web Access web-based console.</span></span>

<span data-ttu-id="96f58-110">Der Artikel beschreibt nicht die Verwendung von Windows PowerShell oder das Ausführen von Cmdlets und Skripts.</span><span class="sxs-lookup"><span data-stu-id="96f58-110">This topic does not describe how to use Windows PowerShell or run cmdlets or scripts.</span></span> <span data-ttu-id="96f58-111">Informationen zur Verwendung von Windows PowerShell und Skriptressourcen erhalten Sie im Abschnitt „Siehe auch“ am Ende des Artikels.</span><span class="sxs-lookup"><span data-stu-id="96f58-111">For information about how to use Windows PowerShell, and scripting resources, see the See Also section at the end of this topic.</span></span>

<span data-ttu-id="96f58-112">Inhalte dieses Themas:</span><span class="sxs-lookup"><span data-stu-id="96f58-112">In this topic:</span></span>

-   [<span data-ttu-id="96f58-113">Unterstützte Browser und Clientgeräte</span><span class="sxs-lookup"><span data-stu-id="96f58-113">Supported browsers and client devices</span></span>](#BKMK_browser)

-   [<span data-ttu-id="96f58-114">Anmelden bei Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="96f58-114">Signing in to Windows PowerShell Web Access</span></span>](#BKMK_sign)

-   [<span data-ttu-id="96f58-115">Abmelden und Timeout</span><span class="sxs-lookup"><span data-stu-id="96f58-115">Signing out and timing out</span></span>](#BKMK_timeout)

-   [<span data-ttu-id="96f58-116">Unterschiede bei der webbasierten Windows PowerShell-Konsole</span><span class="sxs-lookup"><span data-stu-id="96f58-116">Differences in the web-based Windows PowerShell console</span></span>](#BKMK_web)

<a href="" id="BKMK_browser"></a>
------------------------------------------------------------------------

<span data-ttu-id="96f58-117">Windows PowerShell Web Access unterstützt die folgenden Internetbrowser.</span><span class="sxs-lookup"><span data-stu-id="96f58-117">Windows PowerShell Web Access supports the following Internet browsers.</span></span> <span data-ttu-id="96f58-118">Obwohl es keine offizielle Unterstützung für mobile Browser gibt, kann die webbasierte Windows PowerShell-Konsole in vielen dieser Browser ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="96f58-118">Although mobile browsers are not officially supported, many may be able to run the web-based Windows PowerShell console.</span></span> <span data-ttu-id="96f58-119">Andere Browser, die Cookies zulassen, JavaScript ausführen und HTTPS-Websites ausführen, sollten ebenfalls funktionieren. Offizielle Tests wurden jedoch nicht durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="96f58-119">Other browsers that accept cookies, run JavaScript, and run HTTPS websites are expected to work, but are not officially tested.</span></span>

###

<span data-ttu-id="96f58-120"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Unterstützte Desktopcomputerbrowser</span></a></span><span class="sxs-lookup"><span data-stu-id="96f58-120"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Supported desktop computer browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="96f58-121">Windows® Internet Explorer® für Microsoft Windows® 8.0, 9.0, 10.0 und 11.0</span><span class="sxs-lookup"><span data-stu-id="96f58-121">Windows® Internet Explorer® for Microsoft Windows® 8.0, 9.0, 10.0, and 11.0</span></span>

-   <span data-ttu-id="96f58-122">Mozilla Firefox® 10.0.2</span><span class="sxs-lookup"><span data-stu-id="96f58-122">Mozilla Firefox® 10.0.2</span></span>

-   <span data-ttu-id="96f58-123">Google Chrome™ 17.0.963.56m für Windows</span><span class="sxs-lookup"><span data-stu-id="96f58-123">Google Chrome™ 17.0.963.56m for Windows</span></span>

-   <span data-ttu-id="96f58-124">Apple Safari® 5.1.2 für Windows</span><span class="sxs-lookup"><span data-stu-id="96f58-124">Apple Safari® 5.1.2 for Windows</span></span>

-   <span data-ttu-id="96f58-125">Apple Safari 5.1.2 für Mac OS®</span><span class="sxs-lookup"><span data-stu-id="96f58-125">Apple Safari 5.1.2 for Mac OS®</span></span>

###

<span data-ttu-id="96f58-126"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Mobile Geräte oder Browser, für die Minimaltests durchgeführt wurden</span></a></span><span class="sxs-lookup"><span data-stu-id="96f58-126"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Minimally-tested mobile devices or browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="96f58-127">Windows Phone 7 und 7.5</span><span class="sxs-lookup"><span data-stu-id="96f58-127">Windows Phone 7 and 7.5</span></span>

-   <span data-ttu-id="96f58-128">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span><span class="sxs-lookup"><span data-stu-id="96f58-128">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span></span>

-   <span data-ttu-id="96f58-129">Apple Safari für iPhone-Betriebssystem 5.0.1</span><span class="sxs-lookup"><span data-stu-id="96f58-129">Apple Safari for iPhone operating system 5.0.1</span></span>

-   <span data-ttu-id="96f58-130">Apple Safari für iPad 2-Betriebssystem 5.0.1</span><span class="sxs-lookup"><span data-stu-id="96f58-130">Apple Safari for iPad 2 operating system 5.0.1</span></span>

###

<span data-ttu-id="96f58-131"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browseranforderungen</span></a></span><span class="sxs-lookup"><span data-stu-id="96f58-131"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser requirements</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="96f58-132">Browser müssen folgende Anforderungen erfüllen, um die webbasierte Windows PowerShell Web Access-Konsole verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="96f58-132">To use the Windows PowerShell Web Access web-based console, browsers must do the following.</span></span>

-   <span data-ttu-id="96f58-133">Zulassen von Cookies von der Website des Windows PowerShell Web Access-Gateways.</span><span class="sxs-lookup"><span data-stu-id="96f58-133">Allow cookies from the Windows PowerShell Web Access gateway website.</span></span>

-   <span data-ttu-id="96f58-134">Öffnen und Lesen von HTTPS-Seiten.</span><span class="sxs-lookup"><span data-stu-id="96f58-134">Be able to open and read HTTPS pages.</span></span>

-   <span data-ttu-id="96f58-135">Öffnen und Ausführen von Websites, die JavaScript verwenden.</span><span class="sxs-lookup"><span data-stu-id="96f58-135">Open and run websites that use JavaScript.</span></span>

<a href="" id="BKMK_sign"></a>

<span data-ttu-id="96f58-136"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Anmelden bei Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="96f58-136"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Signing in to Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="96f58-137">Ihr Windows PowerShell Web Access-Administrator sollten Ihnen eine URL bereitstellen, die die Adresse der Website des Windows PowerShell Web Access-Gateways Ihrer Organisation ist.</span><span class="sxs-lookup"><span data-stu-id="96f58-137">Your Windows PowerShell Web Access administrator should provide you with a URL that is the address of your organization’s Windows PowerShell Web Access gateway website.</span></span> <span data-ttu-id="96f58-138">Standardmäßig ist die Adresse dieser Website „https://&lt;server_name&gt;/pswa“.</span><span class="sxs-lookup"><span data-stu-id="96f58-138">By default, this website address is https://&lt;server_name&gt;/pswa.</span></span> <span data-ttu-id="96f58-139">Bevor Sie sich bei Windows PowerShell Web Access anmelden, sollten Sie sichergehen, dass Sie über den Namen oder die IP-Adresse des zu verwaltenden Remotecomputers verfügen.</span><span class="sxs-lookup"><span data-stu-id="96f58-139">Before you sign in to Windows PowerShell Web Access, be sure that you have the name or IP address of the remote computer that you want to manage.</span></span> <span data-ttu-id="96f58-140">Sie müssen auf dem Remotecomputer ein autorisierter Benutzer sein. Außerdem müssen Sie darauf die Remoteverwaltung zulassen.</span><span class="sxs-lookup"><span data-stu-id="96f58-140">You must be an authorized user on the remote computer, and it must be configured to allow remote management.</span></span> <span data-ttu-id="96f58-141">Weitere Informationen dazu, wie Sie Ihren Computer so konfigurieren, dass eine Remoteverwaltung möglich ist, finden Sie unter [Aktivieren und Verwenden von Remotebefehlen in Windows PowerShell](https://technet.microsoft.com/magazine/ff700227.aspx).</span><span class="sxs-lookup"><span data-stu-id="96f58-141">For more information about configuring your computer to allow remote management, see [Enable and Use Remote Commands in Windows PowerShell](https://technet.microsoft.com/magazine/ff700227.aspx).</span></span> <span data-ttu-id="96f58-142">Die einfachste Möglichkeit, die Remoteverwaltung auf Ihrem Computer zu konfigurieren, besteht in der Ausführung des Cmdlets **Enable-PSRemoting -force** auf dem Computer in einer Windows PowerShell-Sitzung, die mit erhöhten Benutzerrechten (**Als Administrator ausführen**) geöffnet wurde.</span><span class="sxs-lookup"><span data-stu-id="96f58-142">The simplest method of configuring your computer to allow remote management is to run the **Enable-PSRemoting -force** cmdlet on the computer, in a Windows PowerShell session that has been opened with elevated user rights (**Run as Administrator**).</span></span>

### <a name="to-sign-in-to-windows-powershell-web-access"></a><span data-ttu-id="96f58-143">So melden Sie sich bei Windows PowerShell Web Access an</span><span class="sxs-lookup"><span data-stu-id="96f58-143">To sign in to Windows PowerShell Web Access</span></span>

1.  <span data-ttu-id="96f58-144">Öffnen Sie die Windows PowerShell Web Access-Website in einem Fenster oder auf einer Registerkarte des Internetbrowsers.</span><span class="sxs-lookup"><span data-stu-id="96f58-144">Open the Windows PowerShell Web Access website in an Internet browser window or tab.</span></span>

2.  <span data-ttu-id="96f58-145">Geben Sie auf der Windows PowerShell Web Access-Anmeldeseite Ihren Netzwerkbenutzernamen und das dazugehörige Kennwort an, außerdem den Namen des Computers, den Sie verwalten möchten (und auf dem Sie ein autorisierter Benutzer sind).</span><span class="sxs-lookup"><span data-stu-id="96f58-145">On the Windows PowerShell Web Access sign-in page, provide your network user name, password, and the name of the computer that you want to manage (and on which you are an authorized user).</span></span> <span data-ttu-id="96f58-146">Wenn Sie der Windows PowerShell Web Access-Administrator angewiesen hat, einen URI zu einer benutzerdefinierten Website oder einem Proxyserver statt eines Computernamens zu verwenden, wählen Sie **Verbindungs-URI** im Feld **Verbindungstyp** und geben Sie den URI an.</span><span class="sxs-lookup"><span data-stu-id="96f58-146">If the Windows PowerShell Web Access administrator has instructed you to use a URI to a custom site or proxy server instead of a computer name, select **Connection URI** in the **Connection type** field, and then provide the URI.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="96f58-147"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Hinweis </span></span><span class="sxs-lookup"><span data-stu-id="96f58-147"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><ul>
    <li><p><span data-ttu-id="96f58-148">Wenn der Zielcomputer einer Arbeitsgruppe angehört, verwenden Sie die folgende Syntax, um Ihren Benutzernamen anzugeben und sich am Computer anzumelden: &lt;<em>Arbeitsgruppenname</em>&gt;\&lt;<em>Benutzername</em>&gt;.</span><span class="sxs-lookup"><span data-stu-id="96f58-148">If the destination computer is in a workgroup, use the following syntax to provide your user name and sign in to the computer:&lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;.</span></span></p></li>
    <li><p><span data-ttu-id="96f58-149">Wenn es sich beim Zielcomputer um den Gatewayserver handelt, können Sie <strong>localhost</strong> im Feld <strong>Computername</strong> angeben.</span><span class="sxs-lookup"><span data-stu-id="96f58-149">If the destination computer is the gateway server, you can specify <strong>localhost</strong> in the <strong>Computer name</strong> field.</span></span></p></li>
    <li><p><span data-ttu-id="96f58-150">Sollte es sich beim Zielcomputer um den Gatewayserver handeln und dieser sich in einer Arbeitsgruppe befinden, können Sie <strong>localhost</strong> im Feld <strong>Computername</strong> angeben. Verwenden Sie jedoch nicht „localhost\&lt;<em>Benutzername</em>&gt;“ im Feld <strong>Benutzername</strong>.</span><span class="sxs-lookup"><span data-stu-id="96f58-150">If the destination computer is the gateway server, and the gateway server is in a workgroup, you can use <strong>localhost</strong> in the <strong>Computer name</strong> field, but do not use localhost\&lt;<em>user_name</em>&gt; in the <strong>User name</strong> field.</span></span> <span data-ttu-id="96f58-151">Sie müssen &lt;<em>Arbeitsgruppenname</em>&gt;\&lt;<em>Benutzername</em>&gt; verwenden.</span><span class="sxs-lookup"><span data-stu-id="96f58-151">You must use &lt;<em>workgroup name</em>&gt;\&lt;<em>user_name</em>&gt;.</span></span></p></li>
    </ul></td>
    </tr>
    </tbody>
    </table>

3.  <span data-ttu-id="96f58-152">Der Abschnitt **Optionale Verbindungseinstellungen** bezieht sich auf die Autorisierungsanforderungen des zu verwaltenden Remotecomputers.</span><span class="sxs-lookup"><span data-stu-id="96f58-152">The **Optional Connection Settings** section relates to the authorization requirements of the remote computer that you want to manage.</span></span> <span data-ttu-id="96f58-153">Weitere Informationen zu den Parametern, die den optionalen Verbindungseinstellungen entsprechen, finden Sie in der [Hilfe zum Cmdlet „Enter-PSSession“](https://technet.microsoft.com/library/dd315384.aspx).</span><span class="sxs-lookup"><span data-stu-id="96f58-153">For more information about the parameters that are equivalent to optional connection settings, see the [Enter-PSSession cmdlet Help](https://technet.microsoft.com/library/dd315384.aspx).</span></span>

    <span data-ttu-id="96f58-154">In der Regel sind die Anmeldeinformationen zum Passieren des Windows PowerShell Web Access-Gateways dieselben, die vom zu verwaltenden Remotecomputer erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="96f58-154">Typically, the credentials you use to pass through the Windows PowerShell Web Access gateway are the same that are recognized by the remote computer that you want to manage.</span></span> <span data-ttu-id="96f58-155">Wenn Sie jedoch andere Anmeldeinformationen zur Verwaltung des in Schritt 2 angegebenen Remotecomputers verwenden möchten, erweitern Sie den Abschnitt **Optionale Verbindungseinstellungen**, und geben Sie die abweichenden Anmeldeinformationen an.</span><span class="sxs-lookup"><span data-stu-id="96f58-155">However, if you want to use different credentials to manage the remote computer that you specified in step 2, expand the **Optional Connection Settings** section, and provide the alternate credentials.</span></span> <span data-ttu-id="96f58-156">Fahren Sie ansonsten mit Schritt 6 fort.</span><span class="sxs-lookup"><span data-stu-id="96f58-156">Otherwise, skip to step 6.</span></span>

4.  <span data-ttu-id="96f58-157">Wenn der Windows PowerShell Web Access-Administrator eine benutzerdefinierte Konfiguration für Windows PowerShell Web Access-Benutzer erstellt hat, geben Sie den Namen der Sitzungskonfiguration in das Feld **Konfigurationsname** ein.</span><span class="sxs-lookup"><span data-stu-id="96f58-157">If the Windows PowerShell Web Access administrator has created a custom session configuration for Windows PowerShell Web Access users, type the name of the session configuration name in the **Configuration name** field.</span></span> <span data-ttu-id="96f58-158">Weitere Informationen zu Sitzungskonfigurationen finden Sie unter [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx) auf der Microsoft-Website.</span><span class="sxs-lookup"><span data-stu-id="96f58-158">For more information about session configurations, see [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx) on the Microsoft website.</span></span>

5.  <span data-ttu-id="96f58-159">Belassen Sie den **Authentifizierungstyp** als **Standard**, sofern Sie nicht vom Windows PowerShell Web Access-Administrator gegenteilige Anweisungen erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="96f58-159">Keep the **Authentication type** set to **Default** unless you have been instructed to do otherwise by the Windows PowerShell Web Access administrator.</span></span>

6.  <span data-ttu-id="96f58-160">Klicken Sie auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="96f58-160">Click **Sign in**.</span></span>

<a href="" id="BKMK_timeout"></a>

<span data-ttu-id="96f58-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Abmelden und Timeout</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="96f58-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Signing out and timing out</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="96f58-162">Sie werden in den folgenden Situationen von einer webbasierten Windows PowerShell-Sitzung abgemeldet.</span><span class="sxs-lookup"><span data-stu-id="96f58-162">Any of the following signs you out of a web-based Windows PowerShell session.</span></span>

-   <span data-ttu-id="96f58-163">Wenn Sie unten rechts in der Konsole auf **Abmelden** klicken.</span><span class="sxs-lookup"><span data-stu-id="96f58-163">Clicking **Sign out** in the lower right corner of the console.</span></span> <span data-ttu-id="96f58-164">(Nur Windows Server 2012)</span><span class="sxs-lookup"><span data-stu-id="96f58-164">(Windows Server 2012 only)</span></span>

-   <span data-ttu-id="96f58-165">Wenn Sie unten rechts in der Konsole auf **Speichern** oder **Beenden** klicken (nur Windows Server 2012 R2).</span><span class="sxs-lookup"><span data-stu-id="96f58-165">Clicking **Save** or **Exit** in the lower right corner of the console (Windows Server 2012 R2 only).</span></span> <span data-ttu-id="96f58-166">Durch Klicken auf **Speichern** wird Ihre Windows PowerShell Web Access-Sitzung gespeichert und geschlossen. Sie können zu einem späteren Zeitpunkt die Verbindung mit der Sitzung wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="96f58-166">Clicking **Save** saves and closes your Windows PowerShell Web Access session; you can reconnect to the session later.</span></span> <span data-ttu-id="96f58-167">Wenn Sie sich wieder bei Windows PowerShell Web Access anmelden, zeigt Windows PowerShell Web Access eine Liste der gespeicherten Sitzungen an. Sie können entweder eine gespeicherte Sitzung auswählen und die Verbindung erneut herstellen oder eine neue Sitzung starten.</span><span class="sxs-lookup"><span data-stu-id="96f58-167">When you sign in to Windows PowerShell Web Access again, Windows PowerShell Web Access displays a list of your saved sessions; you can either select and reconnect to a saved session, or start a new session.</span></span> <span data-ttu-id="96f58-168">Die maximale Anzahl geöffneter (sowohl gespeicherter als auch aktiver Sitzungen), die für Benutzer zulässig sind, wird vom Gatewayadministrator konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="96f58-168">The maximum number of open sessions that users are allowed, both saved and active, is configured by the gateway administrator.</span></span>

    <span data-ttu-id="96f58-169">Wenn Sie auf **Beenden** klicken, werden Sie von der Windows PowerShell Web Access-Sitzung abgemeldet, ohne dass diese gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="96f58-169">Clicking **Exit** signs you out of the Windows PowerShell Web Access session without saving it.</span></span>

-   <span data-ttu-id="96f58-170">Wenn Sie sich zur Verwaltung eines anderen Remotecomputers in derselben Browsersitzung oder einer neuen Registerkarte desselben Browsers anmelden.</span><span class="sxs-lookup"><span data-stu-id="96f58-170">Attempting to sign in to manage a different remote computer in the same browser session, or in a new tab of the same browser session.</span></span> <span data-ttu-id="96f58-171">(Dies gilt nicht, wenn Windows Server 2012 R2 auf dem Gatewayserver ausgeführt wird. Windows PowerShell Web Access unter Windows Server 2012 R2 lässt mehrere Benutzersitzungen auf neuen Registerkarten in derselben Browsersitzung zu.) Weitere Informationen dazu, wie Sie mehr als eine aktive Sitzung auf demselben Computer starten, finden Sie unter „Aufbauen von Verbindungen zu mehreren Zielcomputern gleichzeitig“ im Abschnitt [Einschränkungen der webbasierten Konsole](#BKMK_limits) dieses Artikels.</span><span class="sxs-lookup"><span data-stu-id="96f58-171">(This does not apply if the gateway server is running Windows Server 2012 R2; Windows PowerShell Web Access running on Windows Server 2012 R2 does allow multiple user sessions in new tabs in the same browser session.) For more information about how to use more than one active session on the same computer, see “Connecting to multiple target computers simultaneously” in the [Limitations of the web-based console](#BKMK_limits) section of this topic.</span></span>

-   <span data-ttu-id="96f58-172">Wenn Sie mehr als 20 Minuten inaktiv sind.</span><span class="sxs-lookup"><span data-stu-id="96f58-172">20 minutes of inactivity in the session.</span></span> <span data-ttu-id="96f58-173">Der Gatewayadministrator kann den Timeoutzeitraum für Inaktivität anpassen. Weitere Informationen finden Sie unter [Sitzungsverwaltung](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx#BKMK_sesmgmt).</span><span class="sxs-lookup"><span data-stu-id="96f58-173">The gateway administrator can customize the inactivity time-out period; for more information, see [Session management](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx#BKMK_sesmgmt).</span></span>

    -   <span data-ttu-id="96f58-174">Wenn Sie aufgrund von Netzwerkfehlern oder anderen ungeplanten Herunterfahrvorgängen oder Ausfällen in der webbasierten Konsole von Sitzungen getrennt werden und nicht weil Sie die Sitzungen selbst geschlossen haben, wird die Windows PowerShell Web Access-Sitzung weiter ausgeführt. Die Verbindung mit dem Zielcomputer bleibt bestehen, bis das Timeout auf dem Client überschritten wird.</span><span class="sxs-lookup"><span data-stu-id="96f58-174">If you are disconnected from a session in the web-based console because of a network error or other unplanned shutdown or failure, and not because you have closed the session yourself, the Windows PowerShell Web Access session continues to run, connected to the target computer, until the time-out period on the client side lapses.</span></span> <span data-ttu-id="96f58-175">In der Standardeinstellung beträgt dieses Zeitlimit 20 Minuten, was vom Gatewayadministrator angepasst werden kann.</span><span class="sxs-lookup"><span data-stu-id="96f58-175">By default, this time-out period is 20 minutes, and is configured by the gateway administrator.</span></span> <span data-ttu-id="96f58-176">Die Sitzung wird entweder standardmäßig nach 20 Minuten oder nach der vom Gatewayadministrator festgelegten Timeoutperiode getrennt, je nachdem, was kürzer ist.</span><span class="sxs-lookup"><span data-stu-id="96f58-176">The session is disconnected after either the default 20 minutes, or after the time-out period specified by the gateway administrator, whichever is shorter.</span></span>

        <span data-ttu-id="96f58-177">Wenn der Gatewayserver unter Windows Server 2012 R2 ausgeführt wird, ermöglicht Windows PowerShell Web Access Benutzern das erneute Verbinden mit gespeicherten Sitzungen zu einem späteren Zeitpunkt. Die Benutzer können jedoch gespeicherte Sitzungen erst anzeigen bzw. die Verbindung erneut herstellen, nachdem das vom Gatewayadministrator festgelegte Timeout abgelaufen ist.</span><span class="sxs-lookup"><span data-stu-id="96f58-177">If the gateway server is running Windows Server 2012 R2, Windows PowerShell Web Access lets users reconnect to saved sessions at a later time, but you cannot see or reconnect to saved sessions until after the time-out period specified by the gateway administrator has lapsed.</span></span>

-   <span data-ttu-id="96f58-178">Wenn Sie das Browserfenster oder die Browserregisterkarte schließen.</span><span class="sxs-lookup"><span data-stu-id="96f58-178">Closing the browser window or tab.</span></span>

-   <span data-ttu-id="96f58-179">Wenn Sie das Clientgerät ausschalten, auf dem der Browser ausgeführt wird, oder es vom Netzwerk trennen.</span><span class="sxs-lookup"><span data-stu-id="96f58-179">Turning off the client device on which the browser is running, or disconnecting it from the network.</span></span>

-   <span data-ttu-id="96f58-180">Wenn Sie den **Beenden**-Befehl in der Webkonsole ausführen.</span><span class="sxs-lookup"><span data-stu-id="96f58-180">Running the **Exit** command in the web console.</span></span> <span data-ttu-id="96f58-181">Der Befehl funktioniert nicht, wenn die Sitzungskonfiguration, mit der Sie verbunden sind, zur Unterstützung des [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx)-Modus konfiguriert ist oder sich in einem eingeschränkten Runspace befindet.</span><span class="sxs-lookup"><span data-stu-id="96f58-181">This command does not work if the session configuration to which you are connected to is configured to support [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) mode, or is in a restricted runspace.</span></span>

<span data-ttu-id="96f58-182">Falls Sie sich wieder anmelden möchten, öffnen Sie die Windows PowerShell Web Access-Website erneut, und melden Sie sich anhand der Schritte in [So melden Sie sich bei Windows PowerShell Web Access an](#BKMK_signin) in diesem Artikel an.</span><span class="sxs-lookup"><span data-stu-id="96f58-182">If you want to sign in again, open the Windows PowerShell Web Access web page again, and sign in by following the steps in [To sign in to Windows PowerShell Web Access](#BKMK_signin) in this topic.</span></span>

<a href="" id="BKMK_web"></a>

<span data-ttu-id="96f58-183"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Unterschiede bei der webbasierten Windows PowerShell-Konsole</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="96f58-183"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Differences in the web-based Windows PowerShell console</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="96f58-184">Nach der Anmeldung bei Windows PowerShell Web Access wird im Fenster oder auf der Registerkarte des Browsers eine webbasierte Windows PowerShell-Konsole geöffnet.</span><span class="sxs-lookup"><span data-stu-id="96f58-184">After signing in to Windows PowerShell Web Access, a web-based Windows PowerShell console opens in your browser window or tab.</span></span> <span data-ttu-id="96f58-185">Die Konsole ist mit dem Remotecomputer verbunden, den Sie während der Anmeldung angegeben haben. Daher können nur die Windows PowerShell-Cmdlets und -Skripts in der Konsole verwendet werden, die auf dem Remotecomputer verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="96f58-185">Because the console is connected to the remote computer that you specified during the sign-in process, only those Windows PowerShell cmdlets or scripts that are available on the remote computer can be used in the console.</span></span> <span data-ttu-id="96f58-186">In diesem Abschnitt werden weitere Einschränkungen von Windows PowerShell Web Access-Konsolen sowie die Unterschiede zwischen Windows PowerShell Web Access-Konsolen und der installierten **PowerShell.exe**-Konsole beschrieben.</span><span class="sxs-lookup"><span data-stu-id="96f58-186">This section describes other limitations of Windows PowerShell Web Access consoles, and differences between Windows PowerShell Web Access consoles and the installed **PowerShell.exe** console.</span></span>

###

<span data-ttu-id="96f58-187"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Funktionale Unterschiede zu „PowerShell.exe“</span></a></span><span class="sxs-lookup"><span data-stu-id="96f58-187"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Functional disparity with PowerShell.exe</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="96f58-188">Die Mehrzahl der Windows PowerShell-Hostfunktionen steht in der webbasierten Windows PowerShell Web Access-Konsole zur Verfügung, einige jedoch nicht.</span><span class="sxs-lookup"><span data-stu-id="96f58-188">The majority of Windows PowerShell host functionality is available in the Windows PowerShell Web Access web-based console, but there are some features that are not available.</span></span>

-   <span data-ttu-id="96f58-189"><span class="label">Verschachtelte Statusanzeigen.</span></span><span class="sxs-lookup"><span data-stu-id="96f58-189"><span class="label">Nested progress displays.</span></span></span>  <span data-ttu-id="96f58-190">Windows PowerShell Web Access zeigt eine Status-GUI für Cmdlets an, die einen Status ausgeben, es werden jedoch nur Informationen der höchsten Statusebene angezeigt.</span><span class="sxs-lookup"><span data-stu-id="96f58-190">Windows PowerShell Web Access displays a progress GUI for cmdlets that report progress, but only top-level progress information is displayed.</span></span>

-   <span data-ttu-id="96f58-191"><span class="label">Änderung der Eingabefarbe.</span></span><span class="sxs-lookup"><span data-stu-id="96f58-191"><span class="label">Input color modification.</span></span></span>  <span data-ttu-id="96f58-192">Die Eingabefarbe (Vordergrund und Hintergrund) kann nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="96f58-192">The input color (both foreground and background) cannot be changed.</span></span> <span data-ttu-id="96f58-193">Der Stil von Ausgabe-, Warn-, ausführlichen und Fehlermeldungen können alle mithilfe eines Skripts geändert werden.</span><span class="sxs-lookup"><span data-stu-id="96f58-193">The style of output, warning, verbose, and error messages can all be changed by running a script.</span></span>

-   <span data-ttu-id="96f58-194"><span class="label">PSHostRawUserInterface.</span></span><span class="sxs-lookup"><span data-stu-id="96f58-194"><span class="label">PSHostRawUserInterface.</span></span></span>  <span data-ttu-id="96f58-195">Windows PowerShell Web Access wird per Windows PowerShell-Remoteverwaltung implementiert und verwendet einen Remoterunspace.</span><span class="sxs-lookup"><span data-stu-id="96f58-195">Windows PowerShell Web Access is implemented over Windows PowerShell remote management, and uses a remote runspace.</span></span> <span data-ttu-id="96f58-196">Windows PowerShell Web Access implementiert einige Methoden dieser Benutzeroberfläche nicht, z. B. Befehle, die in die Windows-Konsole schreiben.</span><span class="sxs-lookup"><span data-stu-id="96f58-196">Windows PowerShell Web Access does not implement some methods in this interface; for example, any command that writes to the Windows console.</span></span> <span data-ttu-id="96f58-197">Befehle wie **PowerTab** funktionieren in Windows PowerShell Web Access nicht.</span><span class="sxs-lookup"><span data-stu-id="96f58-197">Commands such as **PowerTab** do not work in Windows PowerShell Web Access.</span></span>

-   <span data-ttu-id="96f58-198"><span class="label">Funktionstasten.</span></span><span class="sxs-lookup"><span data-stu-id="96f58-198"><span class="label">Function keys.</span></span></span>  <span data-ttu-id="96f58-199">Windows PowerShell Web Access unterstützt einige Funktionstasten nicht. In vielen Fällen liegt dies daran, dass die Befehle vom Browser reserviert sind.</span><span class="sxs-lookup"><span data-stu-id="96f58-199">Windows PowerShell Web Access does not support some function keys, in many cases because the commands are reserved by the browser.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="96f58-200">Nicht unterstützte Funktionstasten</span><span class="sxs-lookup"><span data-stu-id="96f58-200">Unsupported Function Key</span></span></p></th>
<th><p><span data-ttu-id="96f58-201">Aktion</span><span class="sxs-lookup"><span data-stu-id="96f58-201">Action</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="96f58-202">STRG+C</span><span class="sxs-lookup"><span data-stu-id="96f58-202">Ctrl+C</span></span></p></td>
<td><p><span data-ttu-id="96f58-203">In Windows PowerShell Web Access wird <strong>STRG+C</strong> vom Browser verwendet, um Inhalte zu kopieren.</span><span class="sxs-lookup"><span data-stu-id="96f58-203">In Windows PowerShell Web Access, <strong>Ctrl+C</strong> is used by the browser to copy content.</span></span> <span data-ttu-id="96f58-204">Die Konsole stellt eine <strong>Abbrechen</strong>-Schaltfläche bereit, darüber hinaus ist der Befehl <strong>STRG+Q</strong> zum Abbrechen von Befehlen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="96f58-204">The console offers a <strong>Cancel</strong> button, and users can also use <strong>Ctrl+Q</strong> to cancel commands.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="96f58-205">ALT+Leertaste, E, L</span><span class="sxs-lookup"><span data-stu-id="96f58-205">Alt-space, e, l</span></span></p></td>
<td><p><span data-ttu-id="96f58-206">Durch den Bildschirmpuffer scrollen</span><span class="sxs-lookup"><span data-stu-id="96f58-206">Scroll through the screen buffer</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="96f58-207">ALT+Leertaste, E, F</span><span class="sxs-lookup"><span data-stu-id="96f58-207">Alt+Space, e, f</span></span></p></td>
<td><p><span data-ttu-id="96f58-208">Nach Text im Bildschirmpuffer suchen</span><span class="sxs-lookup"><span data-stu-id="96f58-208">Search for text in the screen buffer</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="96f58-209">ALT+Leertaste, E, K</span><span class="sxs-lookup"><span data-stu-id="96f58-209">Alt+Space, e, k</span></span></p></td>
<td><p><span data-ttu-id="96f58-210">Vom Bildschirmpuffer zu kopierenden Text auswählen</span><span class="sxs-lookup"><span data-stu-id="96f58-210">Select text to be copied from the screen buffer</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="96f58-211">ALT+Leertaste, E, P</span><span class="sxs-lookup"><span data-stu-id="96f58-211">Alt+Space, e, p</span></span></p></td>
<td><p><span data-ttu-id="96f58-212">Daten aus der Zwischenablage in die Windows PowerShell-Konsole einfügen</span><span class="sxs-lookup"><span data-stu-id="96f58-212">Paste clipboard contents into the Windows PowerShell console</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="96f58-213">ALT+Leertaste, C</span><span class="sxs-lookup"><span data-stu-id="96f58-213">Alt+Space, c</span></span></p></td>
<td><p><span data-ttu-id="96f58-214">Schließen der Windows PowerShell-Konsole</span><span class="sxs-lookup"><span data-stu-id="96f58-214">Close the Windows PowerShell console</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="96f58-215">STRG+PAUSE</span><span class="sxs-lookup"><span data-stu-id="96f58-215">Ctrl+Break</span></span></p></td>
<td><p><span data-ttu-id="96f58-216">Schließen des Windows PowerShell-Fensters erzwingen</span><span class="sxs-lookup"><span data-stu-id="96f58-216">Force the Windows PowerShell window to close</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="96f58-217">STRG+POS1</span><span class="sxs-lookup"><span data-stu-id="96f58-217">Ctrl+Home</span></span></p></td>
<td><p><span data-ttu-id="96f58-218">Löschvorgang vom Anfang der aktuellen Befehlszeile durchführen</span><span class="sxs-lookup"><span data-stu-id="96f58-218">Deletes from the beginning of the current command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="96f58-219">STRG+ENDE</span><span class="sxs-lookup"><span data-stu-id="96f58-219">Ctrl+End</span></span></p></td>
<td><p><span data-ttu-id="96f58-220">Löschvorgang bis zum Ende der aktuellen Befehlszeile durchführen</span><span class="sxs-lookup"><span data-stu-id="96f58-220">Deletes to end of the command line</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="96f58-221">F1</span><span class="sxs-lookup"><span data-stu-id="96f58-221">F1</span></span></p></td>
<td><p><span data-ttu-id="96f58-222">Cursor in der Befehlszeile ein Zeichen nach rechts verschieben</span><span class="sxs-lookup"><span data-stu-id="96f58-222">Move cursor one character to the right on your command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="96f58-223">F2</span><span class="sxs-lookup"><span data-stu-id="96f58-223">F2</span></span></p></td>
<td><p><span data-ttu-id="96f58-224">Neuen Befehl durch Kopieren des letzten Befehls bis zum getippten Zeichen erstellen</span><span class="sxs-lookup"><span data-stu-id="96f58-224">Creates a new command by copying your last command up to the character that you type</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="96f58-225">F3</span><span class="sxs-lookup"><span data-stu-id="96f58-225">F3</span></span></p></td>
<td><p><span data-ttu-id="96f58-226">Befehlszeile mit Inhalt der letzten Befehlszeile vervollständigen</span><span class="sxs-lookup"><span data-stu-id="96f58-226">Complete the command line with content from your last command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="96f58-227">F4</span><span class="sxs-lookup"><span data-stu-id="96f58-227">F4</span></span></p></td>
<td><p><span data-ttu-id="96f58-228">Zeichen von Cursorposition löschen</span><span class="sxs-lookup"><span data-stu-id="96f58-228">Deletes characters from cursor position</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="96f58-229">F5</span><span class="sxs-lookup"><span data-stu-id="96f58-229">F5</span></span></p></td>
<td><p><span data-ttu-id="96f58-230">Befehlsverlauf rückwärts durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="96f58-230">Scan backward through your command history.</span></span> <span data-ttu-id="96f58-231">Greifen sie auf Befehle im Befehlsverlauf in Windows PowerShell Web Access zu, indem Sie in der webbasierten Konsole auf die <strong>Verlauf</strong>-Bildlaufschaltflächen klicken.</span><span class="sxs-lookup"><span data-stu-id="96f58-231">To access commands in the command history in Windows PowerShell Web Access, click the <strong>History</strong> scroll buttons in the web-based console.</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="96f58-232">F7</span><span class="sxs-lookup"><span data-stu-id="96f58-232">F7</span></span></p></td>
<td><p><span data-ttu-id="96f58-233">Einen Befehl interaktiv aus dem Befehlsverlauf auswählen</span><span class="sxs-lookup"><span data-stu-id="96f58-233">Interactively select a command from your command history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="96f58-234">F8</span><span class="sxs-lookup"><span data-stu-id="96f58-234">F8</span></span></p></td>
<td><p><span data-ttu-id="96f58-235">Verlauf durchsuchen und Befehle aufrufen, die dem aktuellen Text entsprechen</span><span class="sxs-lookup"><span data-stu-id="96f58-235">Scan history displaying commands that match current text</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="96f58-236">F9</span><span class="sxs-lookup"><span data-stu-id="96f58-236">F9</span></span></p></td>
<td><p><span data-ttu-id="96f58-237">Einen bestimmten, nummerierten Befehl aus dem Verlauf ausführen</span><span class="sxs-lookup"><span data-stu-id="96f58-237">Run a specific numbered command from history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="96f58-238">BILD-AUF</span><span class="sxs-lookup"><span data-stu-id="96f58-238">Page Up</span></span></p></td>
<td><p><span data-ttu-id="96f58-239">Den ersten Befehl im Verlauf ausführen</span><span class="sxs-lookup"><span data-stu-id="96f58-239">Run the first command in the history</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="96f58-240">BILD-AB</span><span class="sxs-lookup"><span data-stu-id="96f58-240">Page Down</span></span></p></td>
<td><p><span data-ttu-id="96f58-241">Den letzten Befehl im Verlauf ausführen</span><span class="sxs-lookup"><span data-stu-id="96f58-241">Run the last command in the history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="96f58-242">ALT+F7</span><span class="sxs-lookup"><span data-stu-id="96f58-242">Alt+F7</span></span></p></td>
<td><p><span data-ttu-id="96f58-243">Befehlsverlauf löschen</span><span class="sxs-lookup"><span data-stu-id="96f58-243">Clear the command history list</span></span></p></td>
</tr>
</tbody>
</table><span data-ttu-id="96f58-244">

<a href="" id="BKMK_limits"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Einschränkungen der webbasierten Konsole</span></a></span><span class="sxs-lookup"><span data-stu-id="96f58-244">

<a href="" id="BKMK_limits"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Limitations of the web-based console</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="96f58-245"><span class="label">Double-Hop.</span></span><span class="sxs-lookup"><span data-stu-id="96f58-245"><span class="label">Double-hop.</span></span></span>   <span data-ttu-id="96f58-246">Auf die Doppel-Hop-Einschränkung (oder die Verbindung mit einem zweiten Computer über die erste Verbindung) stoßen Sie, wenn Sie versuchen, eine neue Sitzung zu erstellen oder mit einer neuen Sitzung zu arbeiten, indem Sie Windows PowerShell Web Access verwenden.</span><span class="sxs-lookup"><span data-stu-id="96f58-246">You can encounter the double-hop (or connecting to a second computer from the first connection) limitation if you try to create or work on a new session by using Windows PowerShell Web Access.</span></span> <span data-ttu-id="96f58-247">Windows PowerShell Web Access verwendet einen Remoterunspace, und **PowerShell.exe** unterstützt das Herstellen einer Remoteverbindungen mit einem zweiten Computer von einem Remoterunspace derzeit nicht.</span><span class="sxs-lookup"><span data-stu-id="96f58-247">Windows PowerShell Web Access uses a remote runspace, and currently, **PowerShell.exe** does not support establishing a remote connection to a second computer from a remote runspace.</span></span> <span data-ttu-id="96f58-248">Wenn Sie beispielsweise versuchen, mithilfe des Cmdlets **Enter-PSSession** von einer bestehenden Verbindung aus eine Verbindung mit einem zweiten Remotecomputer herzustellen, können verschiedene Fehler gemeldet werden, z. B. „Netzwerkressourcen nicht verfügbar“.</span><span class="sxs-lookup"><span data-stu-id="96f58-248">If you attempt to connect to a second remote computer from an existing connection by using the **Enter-PSSession** cmdlet, for example, you can get various errors, such as “Cannot get network resources.”</span></span>

    <span data-ttu-id="96f58-249">Derlei Fehler können vermieden werden, indem Ihr Administrator die CredSSP-Authentifizierung in der Netzwerkumgebung Ihrer Organisation einrichtet.</span><span class="sxs-lookup"><span data-stu-id="96f58-249">To avoid double-hop errors, your administrator should configure CredSSP authentication in your organization’s network environment.</span></span> <span data-ttu-id="96f58-250">Weitere Informationen zur Konfiguration der CredSSP-Authentifizierung finden Sie unter [CredSSP für Zweit-Hop-Remoting](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) auf der Microsoft-Website.</span><span class="sxs-lookup"><span data-stu-id="96f58-250">For more information about configuring CredSSP authentication, see [CredSSP for second-hop remoting](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) on the Microsoft website.</span></span> <span data-ttu-id="96f58-251">Sie können auch explizite Anmeldeinformationen zur Verwaltung eines zweiten Remotecomputers angeben, denn mit impliziten Daten ist es unwahrscheinlich, dass der zweite Hop zugelassen wird.</span><span class="sxs-lookup"><span data-stu-id="96f58-251">You can also provide explicit credentials when you want to manage a second remote computer; implicit credentials are unlikely to allow the second hop.</span></span>

-   <span data-ttu-id="96f58-252">Bei Windows PowerShell Web Access gelten dieselben Einschränkungen wie bei Windows PowerShell-Remotesitzungen.</span><span class="sxs-lookup"><span data-stu-id="96f58-252">Windows PowerShell Web Access uses and has the same limitations as a remote Windows PowerShell session.</span></span> <span data-ttu-id="96f58-253">Befehle, die Windows-Konsolen-APIs direkt aufrufen, etwa solche für konsolenbasierte Editoren oder textbasierte Menüprogramme, funktionieren nicht, da die Befehle nicht an die standardmäßigen Eingabe-, Ausgabe- und Fehlerpipes lesen und schreiben.</span><span class="sxs-lookup"><span data-stu-id="96f58-253">Commands that directly call Windows console APIs, such as those for console-based editors or text-based menu programs, do not work because the commands do not read or write to standard input, output, and error pipes.</span></span> <span data-ttu-id="96f58-254">Aus diesem Grund funktionieren Befehle nicht, die ausführbare Dateien wie **notepad.exe** starten oder GUI wie <span class="code">OpenGridView</span> oder <span class="code">ogv</span> anzeigen.</span><span class="sxs-lookup"><span data-stu-id="96f58-254">Therefore, commands that launch an executable file, such as **notepad.exe**, or display a GUI, such as <span class="code">OpenGridView</span> or <span class="code">ogv</span>, do not work.</span></span> <span data-ttu-id="96f58-255">Ihre Erfahrung wird durch dieses Verhalten beeinträchtigt, denn für Sie scheint es so, als würde Windows PowerShell Web Access nicht auf Ihre Befehlseingaben reagieren.</span><span class="sxs-lookup"><span data-stu-id="96f58-255">Your experience is affected by this behavior; to you, it appears that Windows PowerShell Web Access is not responding to your command.</span></span>

-   <span data-ttu-id="96f58-256">Die Registerkartenvervollständigung funktioniert in einer Sitzungskonfiguration mit einem beschränkten Runspace oder einer Sitzungskonfiguration im **NoLanguage**-Modus nicht.</span><span class="sxs-lookup"><span data-stu-id="96f58-256">Tab completion does not work in a session configuration with a restricted runspace or one that is in **NoLanguage** mode.</span></span> <span data-ttu-id="96f58-257">Obwohl Administratoren eine Sitzung so konfigurieren können, dass die Registerkartenvervollständigung unterstützt wird, raten wir aus Sicherheitsgründen davon ab, da sie für nicht autorisierte Benutzer die folgenden Informationen verfügbar machen kann.</span><span class="sxs-lookup"><span data-stu-id="96f58-257">Although administrators can configure a session to support tab completion, it is discouraged for security reasons, because it can expose the following information to unauthorized users.</span></span>

    -   <span data-ttu-id="96f58-258">Interne Pfade des Dateisystems</span><span class="sxs-lookup"><span data-stu-id="96f58-258">Internal file system paths</span></span>

    -   <span data-ttu-id="96f58-259">Freigegebene Ordner und interne Computer</span><span class="sxs-lookup"><span data-stu-id="96f58-259">Shared folders on internal computers</span></span>

    -   <span data-ttu-id="96f58-260">Variable im Runspace</span><span class="sxs-lookup"><span data-stu-id="96f58-260">Variables in the runspace</span></span>

    -   <span data-ttu-id="96f58-261">Geladene Typen oder .NET Framework-Namespaces</span><span class="sxs-lookup"><span data-stu-id="96f58-261">Loaded types or.NET Framework namespaces</span></span>

    -   <span data-ttu-id="96f58-262">Umgebungsvariablen</span><span class="sxs-lookup"><span data-stu-id="96f58-262">Environment variables</span></span>

-   <span data-ttu-id="96f58-263">Benutzer, die bei einer **NoLanguage**-Sitzungskonfiguration oder einem eingeschränkten Runspace in Windows PowerShell Web Access angemeldet sind, können den **Beenden**-Befehl nicht zum Beenden der Sitzung ausführen.</span><span class="sxs-lookup"><span data-stu-id="96f58-263">Users who are signed in to a **NoLanguage** session configuration or a restricted runspace in Windows PowerShell Web Access cannot run the **Exit** command to end the session.</span></span> <span data-ttu-id="96f58-264">Zum Abmelden müssen Benutzer auf der Konsolenseite auf **Abmelden** klicken.</span><span class="sxs-lookup"><span data-stu-id="96f58-264">To sign out, users should click **Sign Out** on the console page.</span></span>

-   <span data-ttu-id="96f58-265"><span class="label">Aufbauen von Verbindungen zu mehreren Zielcomputern gleichzeitig.</span></span><span class="sxs-lookup"><span data-stu-id="96f58-265"><span class="label">Connecting to multiple target computers simultaneously.</span></span></span>   <span data-ttu-id="96f58-266">Wenn Windows Server 2012 auf dem Gatewayserver ausgeführt wird, lässt Windows PowerShell Web Access nur eine Remotecomputerverbindung pro Browsersitzung zu. Die einmalige Anmeldung und anschließende Verbindung mit mehreren Remotecomputern mithilfe verschiedener Browserregisterkarten ist nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="96f58-266">If the gateway server is running Windows Server 2012, Windows PowerShell Web Access allows only one remote computer connection per browser session; it does not allow users to sign in once, and connect to multiple remote computers by using separate browser tabs.</span></span> <span data-ttu-id="96f58-267">Beim Öffnen eines neuen Browserfensters oder einer neuen Browserregisterkarte werden Sie von Windows PowerShell Web Access dazu aufgefordert, Ihre aktuelle Sitzung zu beenden und eine neue Sitzung zu starten, damit Sie eine Verbindung zu einem neuen (oder demselben) Remotecomputer herstellen können.</span><span class="sxs-lookup"><span data-stu-id="96f58-267">When you open a new tab or new browser window, Windows PowerShell Web Access prompts you to disconnect your current session and start a new session, so that you can connect to the new (or the same) remote computer.</span></span> <span data-ttu-id="96f58-268">Falls Sie mehrere separate Sitzungen mit verschiedenen Remotecomputern verwenden möchten, können Sie mithilfe einer Funktion in Internet Explorer eine neue Sitzung erstellen.</span><span class="sxs-lookup"><span data-stu-id="96f58-268">If two or more separate sessions to different remote computers are desired, however, a feature in Internet Explorer lets you create a new session.</span></span> <span data-ttu-id="96f58-269">Starten Sie eine neue Browsersitzung in Internet Explorer, indem Sie **ALT** drücken, das Menü **Datei** öffnen und **Neue Sitzung** auswählen.</span><span class="sxs-lookup"><span data-stu-id="96f58-269">To start a new browser session in Internet Explorer, press **ALT**, open the **File** menu, and then select **New Session**.</span></span> <span data-ttu-id="96f58-270">Öffnen Sie in dieser neuen Sitzung anschließend die Windows PowerShell Web Access-Website, und melden Sie sich an, um auf einen anderen Remotecomputer zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="96f58-270">Then, open the Windows PowerShell Web Access website in the new session, and sign in to access another remote computer.</span></span>

    <span data-ttu-id="96f58-271">Wenn das Windows PowerShell Web Access-Gateway unter Windows Server 2012 R2 ausgeführt wird, können Benutzer mehrere Verbindungen mit Remotecomputern auf verschiedenen Browserregisterkarten öffnen.</span><span class="sxs-lookup"><span data-stu-id="96f58-271">When the Windows PowerShell Web Access gateway is running on Windows Server 2012 R2, users can open multiple connections to remote computers in different browser tabs.</span></span> <span data-ttu-id="96f58-272">Wenn Sie mehr als eine Verbindung mit einem Remotecomputer über die webbasierte Windows PowerShell-Konsole öffnen möchten, erkundigen Sie sich bei Ihrem Windows PowerShell Web Access-Gatewayadministrator, ob dieses Feature vom Gatewayserver unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="96f58-272">If you want to open more than one connection to a remote computer by using the web-based Windows PowerShell console, check with your Windows PowerShell Web Access gateway administrator to see if this feature is supported by the gateway server.</span></span>

-   <span data-ttu-id="96f58-273"><span class="label">Permanente Windows PowerShell-Sitzungen (erneute Verbindung).</span></span><span class="sxs-lookup"><span data-stu-id="96f58-273"><span class="label">Persistent Windows PowerShell sessions (Reconnection).</span></span></span>   <span data-ttu-id="96f58-274">Nachdem die Sitzung mit dem Windows PowerShell Web Access-Gateway abgelaufen ist, wird die Remoteverbindung zwischen dem Gateway und dem Zielcomputer getrennt.</span><span class="sxs-lookup"><span data-stu-id="96f58-274">After you time out of the Windows PowerShell Web Access gateway, the remote connection between the gateway and the target computer is closed.</span></span> <span data-ttu-id="96f58-275">Dabei werden alle Cmdlets und Skripts, die aktuell laufen, beendet.</span><span class="sxs-lookup"><span data-stu-id="96f58-275">This stops any cmdlets or scripts that are currently in process.</span></span> <span data-ttu-id="96f58-276">Es ist empfehlenswert, bei lang andauernden Aufgaben die Windows PowerShell-**-Job**-Infrastruktur zu verwenden, damit Sie Aufträge starten, die Verbindung mit dem Computer trennen und später wieder herstellen können, ohne dass der Auftrag abgebrochen wird.</span><span class="sxs-lookup"><span data-stu-id="96f58-276">You are encouraged to use the Windows PowerShell **-Job** infrastructure when you are performing long-running tasks, so that you can start jobs, disconnect from the computer, reconnect later, and have jobs persist.</span></span> <span data-ttu-id="96f58-277">Ein weiterer Vorteil der Verwendung von **-Job**-Cmdlets ist, dass Sie sie mithilfe von Windows PowerShell Web Access starten, sich abmelden und später wieder anmelden können, indem Sie entweder Windows PowerShell Web Access oder einen anderen Host ausführen (z. B. Windows PowerShell® Integrated Scripting Environment (ISE)).</span><span class="sxs-lookup"><span data-stu-id="96f58-277">Another benefit of using **-Job** cmdlets is that you can start them by using Windows PowerShell Web Access, sign out, and then reconnect later, either by running Windows PowerShell Web Access or another host (such as Windows PowerShell® Integrated Scripting Environment (ISE)).</span></span>

-   <span data-ttu-id="96f58-278"><span class="label">Ändern der Konsolengröße.</span></span><span class="sxs-lookup"><span data-stu-id="96f58-278"><span class="label">Console resizing.</span></span></span>   <span data-ttu-id="96f58-279">Es stehen die folgenden drei Möglichkeiten zur Änderung der Größe des **PowerShell.exe**-Konsolenfensters zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="96f58-279">The **PowerShell.exe** console window can be resized in the following three ways.</span></span>

    -   <span data-ttu-id="96f58-280">Ändern der Konsolenfenstergröße per Ziehen des Mauszeigers</span><span class="sxs-lookup"><span data-stu-id="96f58-280">Drag and adjust the console window size with a mouse</span></span>

    -   <span data-ttu-id="96f58-281">Ändern von Höhe und Breite per GUI für Konsoleneigenschaften</span><span class="sxs-lookup"><span data-stu-id="96f58-281">Change the height and width properties by using a GUI for console properties</span></span>

    -   <span data-ttu-id="96f58-282">Ändern von Höhe und Breite des Konsolenfensters per Cmdlet</span><span class="sxs-lookup"><span data-stu-id="96f58-282">Changing the height and width of console windows with a cmdlet</span></span>

        <span data-ttu-id="96f58-283">Das Konsolenfenster von Windows PowerShell Web Access kann wie folgt mithilfe von Cmdlets konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="96f58-283">The console window for Windows PowerShell Web Access can be configured by using the cmdlets as follows.</span></span> <span data-ttu-id="96f58-284">Im folgenden Beispiel ändert ein Benutzer die Breite der Windows PowerShell Web Access-Konsole auf **20**.</span><span class="sxs-lookup"><span data-stu-id="96f58-284">In the following example, a user changes the width of Windows PowerShell Web Access console to **20**.</span></span>

        [<span data-ttu-id="96f58-285">Copy</span><span class="sxs-lookup"><span data-stu-id="96f58-285">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_778d5e55-9195-4bd7-b313-d1fbca7876e4'); "Copy to clipboard.")

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        <span data-ttu-id="96f58-286">Die Höhe der Konsole lässt sich auf eine ähnliche Weise ändern.</span><span class="sxs-lookup"><span data-stu-id="96f58-286">You can change the height of the console in a similar manner.</span></span>

        <span data-ttu-id="96f58-287">Weitere Beispiele zur Anpassung der Konsolenansicht stehen im [Windows PowerShell-Teamblog](http://blogs.msdn.com/b/powershell/) zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="96f58-287">Additional examples for customizing the console view are available in the [Windows PowerShell Team Blog](http://blogs.msdn.com/b/powershell/).</span></span>

<span data-ttu-id="96f58-288"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Siehe auch</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="96f58-288"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="96f58-289">[Windows PowerShell-Cmdlet-Referenz](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
[Windows PowerShell in Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
[TechNet-Skriptcenterrepository](http://gallery.technet.microsoft.com/scriptcenter)
[Skriptcenter – Hey, Scripting Guy!](https://technet.microsoft.com/scriptcenter)
[Windows PowerShell-Teamblog](http://blogs.msdn.com/b/powershell/)</span><span class="sxs-lookup"><span data-stu-id="96f58-289">[Windows PowerShell Cmdlet Reference](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
[Windows PowerShell on Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
[TechNet Script Center Repository](http://gallery.technet.microsoft.com/scriptcenter)
[Script Center - Hey, Scripting Guy!](https://technet.microsoft.com/scriptcenter)
[Windows PowerShell Team Blog](http://blogs.msdn.com/b/powershell/)</span></span>

<span data-ttu-id="96f58-290"><span>Show:</span> Inherited Protected</span><span class="sxs-lookup"><span data-stu-id="96f58-290"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="96f58-291"><span class="stdr-votetitle">War diese Seite hilfreich?</span></span><span class="sxs-lookup"><span data-stu-id="96f58-291"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="96f58-292">Ja Nein</span><span class="sxs-lookup"><span data-stu-id="96f58-292">Yes No</span></span>

<span data-ttu-id="96f58-293">Zusätzliches Feedback?</span><span class="sxs-lookup"><span data-stu-id="96f58-293">Additional feedback?</span></span>

<span data-ttu-id="96f58-294"><span class="stdr-count"><span class="stdr-charcnt">1.500</span> verbleibende Zeichen</span> Senden Diesen Schritt überspringen</span><span class="sxs-lookup"><span data-stu-id="96f58-294"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="96f58-295"><span class="stdr-thankyou">Vielen Dank!</span></span><span class="sxs-lookup"><span data-stu-id="96f58-295"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="96f58-296"><span class="stdr-appreciate">Wir schätzen Ihr Feedback.</span></span><span class="sxs-lookup"><span data-stu-id="96f58-296"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="96f58-297">Profil verwalten</span><span class="sxs-lookup"><span data-stu-id="96f58-297">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="96f58-298"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Feedback zur Website</a> Feedback zur Website</span><span class="sxs-lookup"><span data-stu-id="96f58-298"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="96f58-299"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="96f58-299"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="96f58-300">Teilen Sie uns Ihre Erfahrungen mit.</span><span class="sxs-lookup"><span data-stu-id="96f58-300">Tell us about your experience...</span></span>

<span data-ttu-id="96f58-301">Wurde die Seite schnell geladen?</span><span class="sxs-lookup"><span data-stu-id="96f58-301">Did the page load quickly?</span></span>

<span data-ttu-id="96f58-302"><span> Ja<span> </span></span> <span> Nein<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="96f58-302"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="96f58-303">Gefällt Ihnen das Design der Seite?</span><span class="sxs-lookup"><span data-stu-id="96f58-303">Do you like the page design?</span></span>

<span data-ttu-id="96f58-304"><span> Ja<span> </span></span> <span> Nein<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="96f58-304"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="96f58-305">Erzählen Sie uns mehr</span><span class="sxs-lookup"><span data-stu-id="96f58-305">Tell us more</span></span>

-   [<span data-ttu-id="96f58-306">Flash-Newsletter</span><span class="sxs-lookup"><span data-stu-id="96f58-306">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="96f58-307">So erreichen Sie uns</span><span class="sxs-lookup"><span data-stu-id="96f58-307">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="96f58-308">Datenschutzbestimmungen</span><span class="sxs-lookup"><span data-stu-id="96f58-308">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="96f58-309">Nutzungsbedingungen</span><span class="sxs-lookup"><span data-stu-id="96f58-309">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="96f58-310">Marken</span><span class="sxs-lookup"><span data-stu-id="96f58-310">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="96f58-311">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="96f58-311">© 2016 Microsoft</span></span>

<span data-ttu-id="96f58-312">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="96f58-312">© 2016 Microsoft</span></span>

<span data-ttu-id="96f58-313">Die Lizenz für Drittanbieterskripts oder Code, die mit dieser Website verlinkt oder über Verweise verbunden sind, wird Ihnen von den Codeeigentümern erteilt, nicht von Microsoft.</span><span class="sxs-lookup"><span data-stu-id="96f58-313">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="96f58-314">Die ASP.NET Ajax CDN-Nutzungsbedingungen finden Sie unter http://www.asp.net/ajaxlibrary/CDN.ashx.</span><span class="sxs-lookup"><span data-stu-id="96f58-314">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

