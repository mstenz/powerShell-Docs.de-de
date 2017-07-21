---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Installieren und Verwenden von Windows PowerShell Web Access
ms.openlocfilehash: a860f7c22829da46f0458ea729fa0afd1fe4fb6f
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
#  <a name="install-and-use-windows-powershell-web-access"></a><span data-ttu-id="bbf31-103">Installieren und Verwenden von Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="bbf31-103">Install and Use Windows PowerShell Web Access</span></span>

<span data-ttu-id="bbf31-104">Aktualisiert: 5. November 2013</span><span class="sxs-lookup"><span data-stu-id="bbf31-104">Updated: November 5, 2013</span></span>

<span data-ttu-id="bbf31-105">Gilt für: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="bbf31-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="bbf31-106">Windows PowerShell® Web Access (eingeführt in Windows Server® 2012) fungiert als Windows PowerShell-Gateway, indem eine webbasierte Windows PowerShell-Konsole bereitgestellt wird, die auf einen Remotecomputer ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="bbf31-106">Windows PowerShell® Web Access, first introduced in Windows Server® 2012, acts as a Windows PowerShell gateway, providing a web-based Windows PowerShell console that is targeted at a remote computer.</span></span> <span data-ttu-id="bbf31-107">Dadurch können IT-Spezialisten Windows PowerShell-Befehle und -Skripts über eine Windows PowerShell-Konsole in einem Webbrowser ausführen, ohne dass Windows PowerShell, Remoteverwaltungssoftware oder Browser-Plugins auf dem Clientgerät installiert sein müssen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-107">It enables IT Pros to run Windows PowerShell commands and scripts from a Windows PowerShell console in a web browser, with no Windows PowerShell, remote management software, or browser plug-in installation necessary on the client device.</span></span> <span data-ttu-id="bbf31-108">Zur Ausführung der webbasierten Windows PowerShell-Konsole ist lediglich ein ordnungsgemäß konfiguriertes Windows PowerShell Web Access-Gateway und ein Browser auf dem Clientgerät erforderlich, der JavaScript® unterstützt und Cookies akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="bbf31-108">All that is required to run the web-based Windows PowerShell console is a properly-configured Windows PowerShell Web Access gateway, and a client device browser that supports JavaScript® and accepts cookies.</span></span>

<span data-ttu-id="bbf31-109">Beispiele für Clientgeräte umfassen Laptops, privat genutzte Personalcomputer, geliehene Computer, Tablet PCs, Webkiosks, Computer, auf denen kein Windows-basiertes Betriebssystem ausgeführt wird, sowie Browser auf Handys.</span><span class="sxs-lookup"><span data-stu-id="bbf31-109">Examples of client devices include laptops, non-work personal computers, borrowed computers, tablet computers, web kiosks, computers that are not running a Windows-based operating system, and cell phone browsers.</span></span> <span data-ttu-id="bbf31-110">IT-Professionals können über Geräte, die Zugriff auf eine Internetverbindung und einen Webbrowser haben, wichtige Verwaltungsaufgaben auf Windows-basierten Remoteservern ausführen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-110">IT Pros can perform critical management tasks on remote Windows-based servers from devices that have access to an Internet connection and a web browser.</span></span>

<span data-ttu-id="bbf31-111">Nach der erfolgreichen Einrichtung und Konfiguration des Gateways können Benutzer mithilfe eines Webbrowsers auf eine Windows PowerShell-Konsole zugreifen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-111">After successful gateway setup and configuration, users can access a Windows PowerShell console by using a web browser.</span></span> <span data-ttu-id="bbf31-112">Nachdem Benutzer die geschützte Windows PowerShell Web Access-Website geöffnet haben, können sie nach der erfolgreichen Authentifizierung eine webbasierte Windows PowerShell-Konsole ausführen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-112">When users open the secured Windows PowerShell Web Access website, they can run a web-based Windows PowerShell console after successful authentication.</span></span>

<span data-ttu-id="bbf31-113">Die Einrichtung und Konfiguration von Windows PowerShell Web Access umfasst drei Schritte:</span><span class="sxs-lookup"><span data-stu-id="bbf31-113">Windows PowerShell Web Access setup and configuration is a three-step process:</span></span>

1.  <span data-ttu-id="bbf31-114">Installieren von Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="bbf31-114">Installing Windows PowerShell Web Access</span></span>

2.  <span data-ttu-id="bbf31-115">Konfigurieren des Gateways</span><span class="sxs-lookup"><span data-stu-id="bbf31-115">Configuring the gateway</span></span>

3.  <span data-ttu-id="bbf31-116">Konfigurieren von Autorisierungsregeln, die Benutzern den Zugriff auf die webbasierte Windows PowerShell-Konsole ermöglichen</span><span class="sxs-lookup"><span data-stu-id="bbf31-116">Configuring authorization rules that allow users access to the web-based Windows PowerShell console</span></span>

<span data-ttu-id="bbf31-117">Vor der Installation und Konfiguration von Windows PowerShell Web Access sollten Sie das gesamte Handbuch lesen, das Anweisungen zum Installieren, Sichern und Deinstallieren von Windows PowerShell Web Access enthält.</span><span class="sxs-lookup"><span data-stu-id="bbf31-117">Before you install and configure Windows PowerShell Web Access, we recommend that you read this entire guide, which includes instructions about how to install, secure, and uninstall Windows PowerShell Web Access.</span></span> <span data-ttu-id="bbf31-118">Im Thema [Verwendung der webbasierten Windows PowerShell-Konsole](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx) wird beschrieben, wie Benutzer sich bei der webbasierten Konsole anmelden, und es werden einige Beschränkungen und Unterschiede zwischen der webbasierten Windows PowerShell-Konsole und der **powershell.exe**-Konsole erläutert.</span><span class="sxs-lookup"><span data-stu-id="bbf31-118">The [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx) topic describes how users sign in to the web-based console, and covers limitations and differences between the web-based Windows PowerShell console and the **powershell.exe** console.</span></span> <span data-ttu-id="bbf31-119">Endbenutzer der webbasierten Konsole sollten sich das Thema [Verwendung der webbasierten Windows PowerShell-Konsole](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx) durchlesen, sie müssen den Rest dieses Handbuchs jedoch nicht lesen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-119">End users of the web-based console should read [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx), but do not need to read the rest of this guide.</span></span>

<span data-ttu-id="bbf31-120">Dieses Thema enthält keine ausführliche Anleitung zum Webserverbetrieb (IIS), sondern es werden nur die Schritte beschrieben, die zum Konfigurieren des Windows PowerShell Web Access-Gateways erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="bbf31-120">This topic does not provide in-depth Web Server (IIS) operations guidance; only those steps required to configure the Windows PowerShell Web Access gateway are described in this topic.</span></span> <span data-ttu-id="bbf31-121">Weitere Informationen zum Konfigurieren und Schützen von Websites in IIS finden Sie in den IIS-Dokumentationsressourcen im Abschnitt "Siehe auch".</span><span class="sxs-lookup"><span data-stu-id="bbf31-121">For more information about configuring and securing websites in IIS, see the IIS documentation resources in the See Also section.</span></span>

<span data-ttu-id="bbf31-122">Das folgende Diagramm zeigt die Funktionsweise von Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="bbf31-122">The following diagram shows how Windows PowerShell Web Access works.</span></span>

<span><img src="https://i-technet.sec.s-msft.com/dynimg/IC564303.jpeg" title="Windows PowerShell Web Access diagram" alt="Windows PowerShell Web Access diagram" id="ee15fa8f-ce13-49e5-933d-514f6d60a2b1" /></span>

<span data-ttu-id="bbf31-123">Inhalte dieses Themas:</span><span class="sxs-lookup"><span data-stu-id="bbf31-123">In this topic:</span></span>

-   [<span data-ttu-id="bbf31-124">Anforderungen für die Ausführung von Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="bbf31-124">Requirements for running Windows PowerShell Web Access</span></span>](#BKMK_reqs)

-   [<span data-ttu-id="bbf31-125">Unterstützung für Browser und Clientgeräte</span><span class="sxs-lookup"><span data-stu-id="bbf31-125">Browser and client device support</span></span>](#BKMK_browser)

-   [<span data-ttu-id="bbf31-126">Empfohlene (schnelle) Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="bbf31-126">Recommended (quick) deployment</span></span>](#BKMK_recm)

-   [<span data-ttu-id="bbf31-127">Benutzerdefinierte Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="bbf31-127">Custom deployment</span></span>](#BKMK_custom)

-   [<span data-ttu-id="bbf31-128">Konfigurieren eines Originalzertifikats</span><span class="sxs-lookup"><span data-stu-id="bbf31-128">Configure a genuine certificate</span></span>](#BKMK_configcert)

<a href="" id="BKMK_reqs"></a>

<span data-ttu-id="bbf31-129"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Anforderungen für die Ausführung von Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_0" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="bbf31-129"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Requirements for running Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_0" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="bbf31-130">Windows PowerShell Web Access erfordert die Ausführung von Webserver (IIS), .NET Framework 4.5 und Windows PowerShell 3.0 oder Windows PowerShell 4.0 auf dem Server, auf dem Sie das Gateway ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="bbf31-130">Windows PowerShell Web Access requires Web Server (IIS), .NET Framework 4.5, and Windows PowerShell 3.0 or Windows PowerShell 4.0 to be running on the server on which you want to run the gateway.</span></span> <span data-ttu-id="bbf31-131">Sie können Windows PowerShell Web Access auf einem Server mit Windows Server 2012 R2 oder Windows Server 2012 installieren, indem Sie entweder den Assistenten zum Hinzufügen von Rollen und Features im Server-Manager oder Windows PowerShell-Bereitstellungs-Cmdlets für den Server-Manager verwenden.</span><span class="sxs-lookup"><span data-stu-id="bbf31-131">You can install Windows PowerShell Web Access on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using either the Add Roles and Features Wizard in Server Manager, or Windows PowerShell deployment cmdlets for Server Manager.</span></span> <span data-ttu-id="bbf31-132">Wenn Sie Windows PowerShell Web Access mithilfe des Server-Managers oder seiner Bereitstellungs-Cmdlets installieren, werden die erforderlichen Rollen und Features im Rahmen des Installationsvorgangs automatisch hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="bbf31-132">When you install Windows PowerShell Web Access by using Server Manager or its deployment cmdlets, required roles and features are automatically added as part of the installation process.</span></span>

<span data-ttu-id="bbf31-133">Mithilfe von Windows PowerShell Web Access können Remotebenutzer auf Computer der Organisation über Windows PowerShell in einem Webbrowser zugreifen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-133">Windows PowerShell Web Access allows remote users to access computers in your organization by using Windows PowerShell in a web browser.</span></span> <span data-ttu-id="bbf31-134">Obwohl Windows PowerShell Web Access ein benutzerfreundliches und leistungsfähiges Verwaltungstool ist, ist der webbasierte Zugriff mit Sicherheitsrisiken verbunden. Daher sollte eine möglichst sichere Konfiguration gewählt werden.</span><span class="sxs-lookup"><span data-stu-id="bbf31-134">Although Windows PowerShell Web Access is a convenient and powerful management tool, the web-based access poses security risks, and should be configured as securely as possible.</span></span> <span data-ttu-id="bbf31-135">Administratoren, die das Windows PowerShell Web Access-Gateway konfigurieren, wird die Verwendung der verfügbaren Sicherheitsebenen empfohlen. Damit sind die auf Cmdlets basierenden Autorisierungsregeln von Windows PowerShell Web Access sowie die Sicherheitsebenen gemeint, die im Webserver (IIS) und in Drittanbieteranwendungen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="bbf31-135">We recommend that administrators who configure the Windows PowerShell Web Access gateway use available security layers, both the cmdlet-based authorization rules included with Windows PowerShell Web Access, and security layers that are available in Web Server (IIS) and third-party applications.</span></span> <span data-ttu-id="bbf31-136">In dieser Dokumentation wird sowohl auf nicht sichere Konfigurationen, die nur für Testumgebungen empfohlen werden, als auch auf Konfigurationen eingegangen, die für sichere Bereitstellungen empfohlen werden.</span><span class="sxs-lookup"><span data-stu-id="bbf31-136">This documentation includes both unsecure examples that are only recommended for test environments, as well as examples that are recommended for secure deployments.</span></span>

<a href="" id="BKMK_browser"></a>

<span data-ttu-id="bbf31-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Unterstützung für Browser und Clientgeräte</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="bbf31-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser and client device support</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="bbf31-138">Windows PowerShell Web Access unterstützt die folgenden Internetbrowser.</span><span class="sxs-lookup"><span data-stu-id="bbf31-138">Windows PowerShell Web Access supports the following Internet browsers.</span></span> <span data-ttu-id="bbf31-139">Obwohl es keine offizielle Unterstützung für mobile Browser gibt, kann die webbasierte Windows PowerShell-Konsole in vielen dieser Browser ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="bbf31-139">Although mobile browsers are not officially supported, many may be able to run the web-based Windows PowerShell console.</span></span> <span data-ttu-id="bbf31-140">Andere Browser, die Cookies zulassen, JavaScript ausführen und HTTPS-Websites ausführen, sollten ebenfalls funktionieren. Offizielle Tests wurden jedoch nicht durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="bbf31-140">Other browsers that accept cookies, run JavaScript, and run HTTPS websites are expected to work, but are not officially tested.</span></span>

###

<span data-ttu-id="bbf31-141"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Unterstützte Desktopcomputerbrowser</span></a></span><span class="sxs-lookup"><span data-stu-id="bbf31-141"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Supported desktop computer browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="bbf31-142">Windows® Internet Explorer® für Microsoft Windows® 8.0, 9.0, 10.0 und 11.0</span><span class="sxs-lookup"><span data-stu-id="bbf31-142">Windows® Internet Explorer® for Microsoft Windows® 8.0, 9.0, 10.0, and 11.0</span></span>

-   <span data-ttu-id="bbf31-143">Mozilla Firefox® 10.0.2</span><span class="sxs-lookup"><span data-stu-id="bbf31-143">Mozilla Firefox® 10.0.2</span></span>

-   <span data-ttu-id="bbf31-144">Google Chrome™ 17.0.963.56m für Windows</span><span class="sxs-lookup"><span data-stu-id="bbf31-144">Google Chrome™ 17.0.963.56m for Windows</span></span>

-   <span data-ttu-id="bbf31-145">Apple Safari® 5.1.2 für Windows</span><span class="sxs-lookup"><span data-stu-id="bbf31-145">Apple Safari® 5.1.2 for Windows</span></span>

-   <span data-ttu-id="bbf31-146">Apple Safari 5.1.2 für Mac OS®</span><span class="sxs-lookup"><span data-stu-id="bbf31-146">Apple Safari 5.1.2 for Mac OS®</span></span>

###

<span data-ttu-id="bbf31-147"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Mobile Geräte oder Browser, für die Minimaltests durchgeführt wurden</span></a></span><span class="sxs-lookup"><span data-stu-id="bbf31-147"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Minimally-tested mobile devices or browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="bbf31-148">Windows Phone 7 und 7.5</span><span class="sxs-lookup"><span data-stu-id="bbf31-148">Windows Phone 7 and 7.5</span></span>

-   <span data-ttu-id="bbf31-149">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span><span class="sxs-lookup"><span data-stu-id="bbf31-149">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span></span>

-   <span data-ttu-id="bbf31-150">Apple Safari für iPhone-Betriebssystem 5.0.1</span><span class="sxs-lookup"><span data-stu-id="bbf31-150">Apple Safari for iPhone operating system 5.0.1</span></span>

-   <span data-ttu-id="bbf31-151">Apple Safari für iPad 2-Betriebssystem 5.0.1</span><span class="sxs-lookup"><span data-stu-id="bbf31-151">Apple Safari for iPad 2 operating system 5.0.1</span></span>

###

<span data-ttu-id="bbf31-152"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browseranforderungen</span></a></span><span class="sxs-lookup"><span data-stu-id="bbf31-152"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser requirements</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="bbf31-153">Browser müssen folgende Anforderungen erfüllen, um die webbasierte Windows PowerShell Web Access-Konsole verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="bbf31-153">To use the Windows PowerShell Web Access web-based console, browsers must do the following.</span></span>

-   <span data-ttu-id="bbf31-154">Zulassen von Cookies von der Website des Windows PowerShell Web Access-Gateways.</span><span class="sxs-lookup"><span data-stu-id="bbf31-154">Allow cookies from the Windows PowerShell Web Access gateway website.</span></span>

-   <span data-ttu-id="bbf31-155">Öffnen und Lesen von HTTPS-Seiten.</span><span class="sxs-lookup"><span data-stu-id="bbf31-155">Be able to open and read HTTPS pages.</span></span>

-   <span data-ttu-id="bbf31-156">Öffnen und Ausführen von Websites, die JavaScript verwenden.</span><span class="sxs-lookup"><span data-stu-id="bbf31-156">Open and run websites that use JavaScript.</span></span>

<a href="" id="BKMK_recm"></a>

<span data-ttu-id="bbf31-157"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Empfohlene (schnelle) Bereitstellung</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="bbf31-157"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Recommended (quick) deployment</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="bbf31-158">Sie können das Windows PowerShell Web Access-Gateway auf einem Server mit Windows Server 2012 R2 oder Windows Server 2012 installieren, indem Sie entweder Windows PowerShell-Cmdlets oder den Assistenten zum Hinzufügen von Rollen und Features im Server-Manager verwenden.</span><span class="sxs-lookup"><span data-stu-id="bbf31-158">You can install the Windows PowerShell Web Access gateway on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using either Windows PowerShell cmdlets, or by using the Add Roles and Features Wizard that is opened from within Server Manager.</span></span> <span data-ttu-id="bbf31-159">Verwenden Sie für schnelle Installation und Konfiguration Windows PowerShell-Cmdlets, wie in diesem Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="bbf31-159">For quick installation and configuration, use Windows PowerShell cmdlets, as described in this section.</span></span>

-   [<span data-ttu-id="bbf31-160">Schritt 1: Installieren von Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="bbf31-160">Step 1: Install Windows PowerShell Web Access</span></span>](#BKMK_step1)

-   [<span data-ttu-id="bbf31-161">Schritt 2: Konfigurieren des Gateways</span><span class="sxs-lookup"><span data-stu-id="bbf31-161">Step 2: Configure the gateway</span></span>](#BKMK_step2)

-   [<span data-ttu-id="bbf31-162">Schritt 3: Konfigurieren einer restriktiven Autorisierungsregel</span><span class="sxs-lookup"><span data-stu-id="bbf31-162">Step 3: Configure a restrictive authorization rule</span></span>](#BKMK_step3)

<a href="" id="BKMK_step1"></a>
###

<span data-ttu-id="bbf31-163"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Schritt 1: Installieren von Windows PowerShell Web Access</span></a></span><span class="sxs-lookup"><span data-stu-id="bbf31-163"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Install Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a><span data-ttu-id="bbf31-164">So installieren Sie Windows PowerShell Web Access mithilfe von Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="bbf31-164">To install Windows PowerShell Web Access by using Windows PowerShell cmdlets</span></span>

1.  <span data-ttu-id="bbf31-165">Öffnen Sie eine Windows PowerShell-Sitzung mit erhöhten Benutzerrechten, indem Sie einen der folgenden Schritte durchführen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-165">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="bbf31-166">Klicken Sie auf dem Windows-Desktop mit der rechten Maustaste in der Taskleiste auf **Windows PowerShell** und anschließend auf **Als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-166">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="bbf31-167">Klicken Sie auf dem Windows-**Startbildschirm** mit der rechten Maustaste auf **Windows PowerShell**, und klicken Sie anschließend auf **Als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-167">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="bbf31-168"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Hinweis </span></span><span class="sxs-lookup"><span data-stu-id="bbf31-168"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="bbf31-169">In Windows PowerShell 3.0 und 4.0 muss das Server-Manager-Cmdlet-Modul vor der Ausführung von Cmdlets, die zum Modul gehören, nicht in die Windows PowerShell-Sitzung importiert werden.</span><span class="sxs-lookup"><span data-stu-id="bbf31-169">In Windows PowerShell 3.0 and 4.0, there is no need to import the Server Manager cmdlet module into the Windows PowerShell session before running cmdlets that are part of the module.</span></span> <span data-ttu-id="bbf31-170">Module werden automatisch importiert, wenn Sie ein zum Modul gehörendes Cmdlet zum ersten Mal ausführen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-170">A module is automatically imported the first time you run a cmdlet that is part of the module.</span></span> <span data-ttu-id="bbf31-171">Außerdem wird die Groß- und Kleinschreibung bei Windows PowerShell-Cmdlets nicht berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="bbf31-171">Also, Windows PowerShell cmdlets are not case-sensitive.</span></span></p></td>
    </tr>
    </tbody>
    </table>

2.  <span data-ttu-id="bbf31-172">Geben Sie Folgendes ein, und drücken Sie dann die **EINGABETASTE**, wobei *Computername* für den Remotecomputer steht, auf dem Sie Windows PowerShell Web Access ggf. installieren möchten.</span><span class="sxs-lookup"><span data-stu-id="bbf31-172">Type the following, and then press **Enter**, where *computer_name* represents a remote computer on which you want to install Windows PowerShell Web Access, if applicable.</span></span> <span data-ttu-id="bbf31-173">Mit dem <span class="code">Restart</span>-Parameter werden Zielserver bei Bedarf automatisch neu gestartet.</span><span class="sxs-lookup"><span data-stu-id="bbf31-173">The <span class="code">Restart</span> parameter automatically restarts destination servers if required.</span></span>

    [<span data-ttu-id="bbf31-174">Kopieren</span><span class="sxs-lookup"><span data-stu-id="bbf31-174">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_374a9c21-4f6e-471e-b957-bb190a594533'); "In Zwischenablage kopieren.")

        Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="bbf31-175"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Hinweis </span></span><span class="sxs-lookup"><span data-stu-id="bbf31-175"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="bbf31-176">Bei der Installation von Windows PowerShell Web Access mithilfe von Windows PowerShell-Cmdlets werden Webserver (IIS)-Verwaltungstools nicht standardmäßig hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="bbf31-176">Installing Windows PowerShell Web Access by using Windows PowerShell cmdlets does not add Web Server (IIS) management tools by default.</span></span> <span data-ttu-id="bbf31-177">Wenn Sie die Verwaltungstools auf demselben Server wie das Windows PowerShell Web Access-Gateway installieren möchten, fügen Sie dem Installationsbefehl den <span class="code">IncludeManagementTools</span>-Parameter hinzu (wie in diesem Schritt angegeben).</span><span class="sxs-lookup"><span data-stu-id="bbf31-177">If you want to install the management tools on the same server as the Windows PowerShell Web Access gateway, add the <span class="code">IncludeManagementTools</span> parameter to the installation command (as provided in this step).</span></span> <span data-ttu-id="bbf31-178">Wenn Sie die Windows PowerShell Web Access-Website über einen Remotecomputer verwalten, installieren Sie das IIS-Manager-Snap-In, indem Sie die <a href="http://go.microsoft.com/fwlink/?LinkID=304145">Remoteserver-Verwaltungstools für Windows 8.1</a> oder die <a href="http://go.microsoft.com/fwlink/p/?LinkID=238560">Remoteserver-Verwaltungstools für Windows 8</a> auf dem Computer installieren, von dem aus Sie das Gateway verwalten möchten.</span><span class="sxs-lookup"><span data-stu-id="bbf31-178">If you are managing the Windows PowerShell Web Access website from a remote computer, install the IIS Manager snap-in by installing <a href="http://go.microsoft.com/fwlink/?LinkID=304145">Remote Server Administration Tools for Windows 8.1</a> or <a href="http://go.microsoft.com/fwlink/p/?LinkID=238560">Remote Server Administration Tools for Windows 8</a> on the computer from which you want to manage the gateway.</span></span></p></td>
    </tr>
    </tbody>
    </table>

    <span data-ttu-id="bbf31-179">Zum Installieren von Rollen oder Features auf einer Offline-VHD müssen Sie sowohl den <span class="code">ComputerName</span>- als auch den <span class="code">VHD</span>-Parameter hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-179">To install roles and features on an offline VHD, you must add both the <span class="code">ComputerName</span> parameter and the <span class="code">VHD</span> parameter.</span></span> <span data-ttu-id="bbf31-180">Der <span class="code">ComputerName</span>-Parameter enthält den Namen des Servers, auf dem die VHD eingebunden werden soll. Der <span class="code">VHD</span>-Parameter enthält den Pfad zur VHD-Datei auf dem angegebenen Server.</span><span class="sxs-lookup"><span data-stu-id="bbf31-180">The <span class="code">ComputerName</span> parameter contains the name of the server on which to mount the VHD, and the <span class="code">VHD</span> parameter contains the path to the VHD file on the specified server.</span></span>

    [<span data-ttu-id="bbf31-181">Kopieren</span><span class="sxs-lookup"><span data-stu-id="bbf31-181">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_d841d509-347e-49d0-bf54-8d1f306bece6'); "In Zwischenablage kopieren.")

        Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart

3.  <span data-ttu-id="bbf31-182">Stellen Sie nach Abschluss der Installation sicher, dass Windows PowerShell Web Access auf den Zielservern installiert wurde. Führen Sie dazu das Cmdlet **Get-WindowsFeature** auf einem Zielserver in einer Windows PowerShell-Konsole aus, die mit erhöhten Benutzerrechten geöffnet wurde.</span><span class="sxs-lookup"><span data-stu-id="bbf31-182">When installation is complete, verify that Windows PowerShell Web Access was installed on destination servers by running the **Get-WindowsFeature** cmdlet on a destination server, in a Windows PowerShell console that has been opened with elevated user rights.</span></span> <span data-ttu-id="bbf31-183">Sie können die Installation von Windows PowerShell Web Access auch in der Server-Manager-Konsole überprüfen, indem Sie auf der Seite **Alle Server** einen Zielserver auswählen und anschließend die Kachel **Rollen und Features** für den ausgewählten Server anzeigen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-183">You can also verify that Windows PowerShell Web Access was installed in the Server Manager console, by selecting a destination server on the **All Servers** page, and then viewing the **Roles and Features** tile for the selected server.</span></span> <span data-ttu-id="bbf31-184">Sie können auch die Infodatei für Windows PowerShell Web Access anzeigen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-184">You can also view the readme file for Windows PowerShell Web Access.</span></span>

4.  <span data-ttu-id="bbf31-185">Nachdem Windows PowerShell Web Access installiert wurde, werden Sie aufgefordert, die Infodatei zu lesen, in der grundlegende, erforderliche Setupanweisungen für das Gateway enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="bbf31-185">After Windows PowerShell Web Access is installed, you are prompted to review the readme file, which contains basic, required setup instructions for the gateway.</span></span> <span data-ttu-id="bbf31-186">Diese Setupanweisungen finden Sie auch im nächsten Abschnitt [Schritt 2: Konfigurieren des Gateways](#BKMK_step2).</span><span class="sxs-lookup"><span data-stu-id="bbf31-186">These setup instructions are also in the following section, [Step 2: Configure the gateway](#BKMK_step2).</span></span> <span data-ttu-id="bbf31-187">Die Infodatei befindet sich unter <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt.</span></span><span class="sxs-lookup"><span data-stu-id="bbf31-187">The path to the readme file is <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span></span>

<a href="" id="BKMK_step2"></a>
###

<span data-ttu-id="bbf31-188"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Schritt 2: Konfigurieren des Gateways</span></a></span><span class="sxs-lookup"><span data-stu-id="bbf31-188"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Configure the gateway</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="bbf31-189">Das Cmdlet **Install-PswaWebApplication** stellt eine schnelle Möglichkeit zum Konfigurieren von Windows PowerShell Web Access dar.</span><span class="sxs-lookup"><span data-stu-id="bbf31-189">The **Install-PswaWebApplication** cmdlet is a quick way to get Windows PowerShell Web Access configured.</span></span> <span data-ttu-id="bbf31-190">Sie können den <span class="code">UseTestCertificate</span>-Parameter zwar dem Cmdlet <span class="code">Install-PswaWebApplication</span> hinzufügen, um zu Testzwecken ein selbstsigniertes SSL-Zertifikat zu installieren, aber dies ist kein sicheres Verfahren. Verwenden Sie für eine sichere Produktionsumgebung immer ein gültiges SSL-Zertifikat, das von einer Zertifizierungsstelle signiert wurde.</span><span class="sxs-lookup"><span data-stu-id="bbf31-190">Although you can add the <span class="code">UseTestCertificate</span> parameter to the <span class="code">Install-PswaWebApplication</span> cmdlet to install a self-signed SSL certificate for test purposes, this is not secure; for a secure production environment, always use a valid SSL certificate that has been signed by a certification authority (CA).</span></span> <span data-ttu-id="bbf31-191">Mithilfe der IIS-Manager-Konsole können Administratoren das Testzertifikat durch ein signiertes Zertifikat ihrer Wahl ersetzen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-191">Administrators can replace the test certificate with a signed certificate of their choice by using the IIS Manager console.</span></span>

<span data-ttu-id="bbf31-192">Sie können die Konfiguration der Windows PowerShell Web Access-Webanwendung durchführen, indem Sie entweder das Cmdlet <span class="code">Install-PswaWebApplication</span> ausführen oder im IIS-Manager GUI-basierte Konfigurationsschritte ausführen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-192">You can complete Windows PowerShell Web Access web application configuration either by running the <span class="code">Install-PswaWebApplication</span> cmdlet or by performing GUI-based configuration steps in IIS Manager.</span></span> <span data-ttu-id="bbf31-193">Standardmäßig wird die Webanwendung **pswa** (und der dazugehörige Anwendungspool **pswa_pool**) durch das Cmdlet im Container **Standardwebsite** installiert, wie im IIS-Manager gezeigt. Bei Bedarf können Sie das Cmdlet anweisen, den Container „Standardwebsite“ der Webanwendung zu ändern.</span><span class="sxs-lookup"><span data-stu-id="bbf31-193">By default, the cmdlet installs the web application, **pswa** (and an application pool for it, **pswa_pool**), in the **Default Web Site** container, as shown in IIS Manager; if desired, you can instruct the cmdlet to change the default site container of the web application.</span></span> <span data-ttu-id="bbf31-194">Der IIS-Manager bietet Konfigurationsoptionen, die für Webanwendungen verfügbar sind, beispielsweise das Ändern der Portnummer oder des SSL-Zertifikats (Secure Sockets Layer).</span><span class="sxs-lookup"><span data-stu-id="bbf31-194">IIS Manager offers configuration options that are available for web applications, such as changing the port number or the Secure Sockets Layer (SSL) certificate.</span></span>

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="bbf31-195"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle">Sicherheitshinweis </span></span><span class="sxs-lookup"><span data-stu-id="bbf31-195"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="bbf31-196">Es wird nachdrücklich empfohlen, dass Administratoren das Gateway so konfigurieren, dass ein gültiges, von einer Zertifizierungsstelle signiertes Zertifikat verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bbf31-196">We strongly recommend that administrators configure the gateway to use a valid certificate that has been signed by a CA.</span></span></p></td>
</tr>
</tbody>
</table>

-   [<span data-ttu-id="bbf31-197">So verwenden Sie Install-PswaWebApplication, um das Windows PowerShell Web Access-Gateway mit einem Testzertifikat zu konfigurieren</span><span class="sxs-lookup"><span data-stu-id="bbf31-197">To configure the Windows PowerShell Web Access gateway with a test certificate by using Install-PswaWebApplication</span></span>](#BKMK_testcert)

-   [<span data-ttu-id="bbf31-198">So verwenden Sie Install-PswaWebApplication und IIS-Manager, um das Windows PowerShell Web Access-Gateway mit einem Originalzertifikat zu konfigurieren</span><span class="sxs-lookup"><span data-stu-id="bbf31-198">To configure the Windows PowerShell Web Access gateway with a genuine certificate by using Install-PswaWebApplication and IIS Manager</span></span>](#BKMK_gencert)

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a><span data-ttu-id="bbf31-199">So verwenden Sie das Install-PswaWebApplication-Cmdlet, um das Windows PowerShell Web Access-Gateway mit einem Testzertifikat zu konfigurieren</span><span class="sxs-lookup"><span data-stu-id="bbf31-199">To configure the Windows PowerShell Web Access gateway with a test certificate by using Install-PswaWebApplication</span></span>

1.  <span data-ttu-id="bbf31-200">Öffnen Sie eine Windows PowerShell-Sitzung, indem Sie einen der folgenden Schritte durchführen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-200">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="bbf31-201">Klicken Sie auf dem Windows-Desktop mit der rechten Maustaste auf der Taskleiste auf **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-201">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="bbf31-202">Klicken Sie auf der Windows-Startseite**** auf **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-202">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="bbf31-203">Geben Sie Folgendes ein, und drücken Sie anschließend die **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-203">Type the following, and then press **Enter**.</span></span>

    <span data-ttu-id="bbf31-204">**Install-PswaWebApplication -UseTestCertificate**</span><span class="sxs-lookup"><span data-stu-id="bbf31-204">**Install-PswaWebApplication -UseTestCertificate**</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="bbf31-205"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle">Sicherheitshinweis </span></span><span class="sxs-lookup"><span data-stu-id="bbf31-205"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="bbf31-206">Der <span class="code">UseTestCertificate</span>-Parameter sollte nur in einer privaten Testumgebung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bbf31-206">The <span class="code">UseTestCertificate</span> parameter should only be used in a private test environment.</span></span> <span data-ttu-id="bbf31-207">Für sichere Produktionsumgebungen empfiehlt sich die Verwendung eines gültigen Zertifikats, das von einer Zertifizierungsstelle signiert wurde.</span><span class="sxs-lookup"><span data-stu-id="bbf31-207">For a secure production environment, we recommend using a valid certificate that has been signed by a CA.</span></span></p></td>
    </tr>
    </tbody>
    </table>

    <span data-ttu-id="bbf31-208">Beim Ausführen des Cmdlets wird die Windows PowerShell Web Access-Webanwendung im Container „Standardwebsite“ von IIS installiert.</span><span class="sxs-lookup"><span data-stu-id="bbf31-208">Running the cmdlet installs the Windows PowerShell Web Access web application within the IIS Default Web Site container.</span></span> <span data-ttu-id="bbf31-209">Das Cmdlet erstellt die erforderliche Infrastruktur zum Ausführen von Windows PowerShell Web Access auf der Standardwebsite „https://&lt;Servername&gt;/pswa“.</span><span class="sxs-lookup"><span data-stu-id="bbf31-209">The cmdlet creates the infrastructure required to run Windows PowerShell Web Access on the default website, https://&lt;server_name&gt;/pswa.</span></span> <span data-ttu-id="bbf31-210">Geben Sie zum Installieren der Webanwendung auf einer anderen Website den Websitenamen an, indem Sie den <span class="code">WebSiteName</span>-Parameter hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-210">To install the web application in a different website, provide the website name by adding the <span class="code">WebSiteName</span> parameter.</span></span> <span data-ttu-id="bbf31-211">Fügen Sie den <span class="code">WebApplicationName</span>-Parameter hinzu, um den Namen der Webanwendung zu ändern (der Standardname lautet <span class="code">pswa</span>).</span><span class="sxs-lookup"><span data-stu-id="bbf31-211">To change the name of the web application (the default is <span class="code">pswa</span>), add the <span class="code">WebApplicationName</span> parameter.</span></span>

    <span data-ttu-id="bbf31-212">Die folgenden Einstellungen werden durch die Ausführung des Cmdlets konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="bbf31-212">The following settings are configured by running the cmdlet.</span></span> <span data-ttu-id="bbf31-213">Falls gewünscht, können Sie diese in der IIS-Manager-Konsole manuell ändern.</span><span class="sxs-lookup"><span data-stu-id="bbf31-213">You can change these manually in the IIS Manager console, if desired.</span></span>

    -   <span data-ttu-id="bbf31-214">Pfad: /pswa</span><span class="sxs-lookup"><span data-stu-id="bbf31-214">Path: /pswa</span></span>

    -   <span data-ttu-id="bbf31-215">Anwendungspool: pswa_pool</span><span class="sxs-lookup"><span data-stu-id="bbf31-215">ApplicationPool: pswa_pool</span></span>

    -   <span data-ttu-id="bbf31-216">Aktivierte Protokolle: http</span><span class="sxs-lookup"><span data-stu-id="bbf31-216">EnabledProtocols: http</span></span>

    -   <span data-ttu-id="bbf31-217">Physischer Pfad: %*windir*%/Web/PowerShellWebAccess/wwwroot</span><span class="sxs-lookup"><span data-stu-id="bbf31-217">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span></span>

    <span data-ttu-id="bbf31-218"><span class="label">Beispiel:</span> <span class="code"> Install-PswaWebApplication –webApplicationName myWebApp –useTestCertificate</span></span><span class="sxs-lookup"><span data-stu-id="bbf31-218"><span class="label">Example:</span> <span class="code">Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate</span></span></span>

    <span data-ttu-id="bbf31-219">In diesem Beispiel ergibt sich als Website für Windows PowerShell Web Access „https://&lt;*Servername*&gt;/myWebApp“.</span><span class="sxs-lookup"><span data-stu-id="bbf31-219">In this example, the resulting website for Windows PowerShell Web Access is https://&lt; *server_name*&gt;/myWebApp.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="bbf31-220"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Hinweis </span></span><span class="sxs-lookup"><span data-stu-id="bbf31-220"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="bbf31-221">Eine Anmeldung ist erst möglich, nachdem den Benutzern durch Hinzufügen von Autorisierungsregeln der Zugriff auf die Website gestattet wurde.</span><span class="sxs-lookup"><span data-stu-id="bbf31-221">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span> <span data-ttu-id="bbf31-222">Weitere Informationen finden Sie unter <a href="#BKMK_step3">Schritt 3: Konfigurieren einer restriktiven Autorisierungsregel</a> und <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access</a>.</span><span class="sxs-lookup"><span data-stu-id="bbf31-222">For more information, see <a href="#BKMK_step3">Step 3: Configure a restrictive authorization rule</a> and <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table>

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a><span data-ttu-id="bbf31-223">So verwenden Sie Install-PswaWebApplication und IIS-Manager, um das Windows PowerShell Web Access-Gateway mit einem Originalzertifikat zu konfigurieren</span><span class="sxs-lookup"><span data-stu-id="bbf31-223">To configure the Windows PowerShell Web Access gateway with a genuine certificate by using Install-PswaWebApplication and IIS Manager</span></span>

1.  <span data-ttu-id="bbf31-224">Öffnen Sie eine Windows PowerShell-Sitzung, indem Sie einen der folgenden Schritte durchführen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-224">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="bbf31-225">Klicken Sie auf dem Windows-Desktop mit der rechten Maustaste auf der Taskleiste auf **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-225">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="bbf31-226">Klicken Sie auf der Windows-Startseite**** auf **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-226">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="bbf31-227">Geben Sie Folgendes ein, und drücken Sie anschließend die **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-227">Type the following, and then press **Enter**.</span></span>

    <span data-ttu-id="bbf31-228">**Install-PswaWebApplication**</span><span class="sxs-lookup"><span data-stu-id="bbf31-228">**Install-PswaWebApplication**</span></span>

    <span data-ttu-id="bbf31-229">Die folgenden Gatewayeinstellungen werden durch die Ausführung des Cmdlets konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="bbf31-229">The following gateway settings are configured by running the cmdlet.</span></span> <span data-ttu-id="bbf31-230">Falls gewünscht, können Sie diese in der IIS-Manager-Konsole manuell ändern.</span><span class="sxs-lookup"><span data-stu-id="bbf31-230">You can change these manually in the IIS Manager console, if desired.</span></span> <span data-ttu-id="bbf31-231">Sie können auch Werte für die Parameter <span class="code">WebsiteName</span> und <span class="code">WebApplicationName</span> des Cmdlets <span class="code">Install-PswaWebApplication</span> angeben.</span><span class="sxs-lookup"><span data-stu-id="bbf31-231">You can also specify values for the <span class="code">WebsiteName</span> and <span class="code">WebApplicationName</span> parameters of the <span class="code">Install-PswaWebApplication</span> cmdlet.</span></span>

    -   <span data-ttu-id="bbf31-232">Pfad: /pswa</span><span class="sxs-lookup"><span data-stu-id="bbf31-232">Path: /pswa</span></span>

    -   <span data-ttu-id="bbf31-233">Anwendungspool: pswa_pool</span><span class="sxs-lookup"><span data-stu-id="bbf31-233">ApplicationPool: pswa_pool</span></span>

    -   <span data-ttu-id="bbf31-234">Aktivierte Protokolle: http</span><span class="sxs-lookup"><span data-stu-id="bbf31-234">EnabledProtocols: http</span></span>

    -   <span data-ttu-id="bbf31-235">Physischer Pfad: %*windir*%/Web/PowerShellWebAccess/wwwroot</span><span class="sxs-lookup"><span data-stu-id="bbf31-235">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span></span>

3.  <span data-ttu-id="bbf31-236">Öffnen Sie die IIS-Manager-Konsole, indem Sie eine der folgenden Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="bbf31-236">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="bbf31-237">Starten Sie auf dem Windows-Desktop den Server-Manager, indem Sie in der Windows-Taskleiste auf **Server-Manager** klicken.</span><span class="sxs-lookup"><span data-stu-id="bbf31-237">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="bbf31-238">Klicken Sie im Menü **Tools** im Server-Manager auf **Internetinformationsdienste-Manager (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-238">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="bbf31-239">Klicken Sie auf der Windows-Startseite**** auf **Server-Manager**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-239">On the Windows **Start** screen, click **Server Manager**.</span></span>

4.  <span data-ttu-id="bbf31-240">Erweitern Sie im IIS-Manager-Strukturbereich den Knoten für den Server, auf dem Windows PowerShell Web Access installiert ist, bis der Ordner **Sites** sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="bbf31-240">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="bbf31-241">Erweitern Sie den Ordner **Sites**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-241">Expand the **Sites** folder.</span></span>

5.  <span data-ttu-id="bbf31-242">Wählen Sie die Website aus, auf der Sie die Windows PowerShell Web Access-Webanwendung installiert haben.</span><span class="sxs-lookup"><span data-stu-id="bbf31-242">Select the website in which you have installed the Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="bbf31-243">Klicken Sie im Bereich **Aktionen** auf **Bindungen**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-243">In the **Actions** pane, click **Bindings**.</span></span>

6.  <span data-ttu-id="bbf31-244">Klicken Sie im Dialogfeld **Websitebindung** auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-244">In the **Site Binding** dialog box, click **Add**.</span></span>

7.  <span data-ttu-id="bbf31-245">Wählen Sie im Dialogfeld **Websitebindung hinzufügen** im Feld **Typ** die Option **https** aus.</span><span class="sxs-lookup"><span data-stu-id="bbf31-245">In the **Add Site Binding** dialog box, in the **Type** field, select **https**.</span></span>

8.  <span data-ttu-id="bbf31-246">Wählen Sie das signierte Zertifikat im Dropdownmenü des Felds **SSL-Zertifikat** aus.</span><span class="sxs-lookup"><span data-stu-id="bbf31-246">In the **SSL certificate** field, select your signed certificate from the drop-down menu.</span></span> <span data-ttu-id="bbf31-247">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-247">Click **OK**.</span></span> <span data-ttu-id="bbf31-248">Weitere Informationen zum Anfordern eines Zertifikats finden Sie in diesem Thema unter [So konfigurieren Sie ein SSL-Zertifikat im IIS-Manager](#BKMK_cert).</span><span class="sxs-lookup"><span data-stu-id="bbf31-248">See [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic for more information about how to obtain a certificate.</span></span>

    <span data-ttu-id="bbf31-249">Die Windows PowerShell Web Access-Webanwendung ist jetzt für die Verwendung des signierten SSL-Zertifikats konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="bbf31-249">The Windows PowerShell Web Access web application is now configured to use your signed SSL certificate.</span></span> <span data-ttu-id="bbf31-250">Sie können auf Windows PowerShell Web Access zugreifen, indem Sie „https://&lt;Servername&gt;/pswa“ in einem Browserfenster öffnen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-250">You can access Windows PowerShell Web Access by opening https://&lt;server_name&gt;/pswa in a browser window.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="bbf31-251"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Hinweis </span></span><span class="sxs-lookup"><span data-stu-id="bbf31-251"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="bbf31-252">Eine Anmeldung ist erst möglich, nachdem den Benutzern durch Hinzufügen von Autorisierungsregeln der Zugriff auf die Website gestattet wurde.</span><span class="sxs-lookup"><span data-stu-id="bbf31-252">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span> <span data-ttu-id="bbf31-253">Weitere Informationen finden Sie unter <a href="#BKMK_step3">Schritt 3: Konfigurieren einer restriktiven Autorisierungsregel</a> und <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access</a>.</span><span class="sxs-lookup"><span data-stu-id="bbf31-253">For more information, see <a href="#BKMK_step3">Step 3: Configure a restrictive authorization rule</a> and <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table><span data-ttu-id="bbf31-254">

<a href="" id="BKMK_step3"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Schritt 3: Konfigurieren einer restriktiven Autorisierungsregel</span></a></span><span class="sxs-lookup"><span data-stu-id="bbf31-254">

<a href="" id="BKMK_step3"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 3: Configure a restrictive authorization rule</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="bbf31-255">Nach der Installation von Windows PowerShell Web Access und der Konfiguration des Gateways können Benutzer die Anmeldeseite in einem Browser öffnen. Sie können sich jedoch erst anmelden, nachdem der Windows PowerShell Web Access-Administrator ihnen ausdrücklich Zugriff gewährt hat.</span><span class="sxs-lookup"><span data-stu-id="bbf31-255">After Windows PowerShell Web Access is installed and the gateway is configured, users can open the sign-in page in a browser, but they cannot sign in until the Windows PowerShell Web Access administrator grants users access explicitly.</span></span> <span data-ttu-id="bbf31-256">Die Windows PowerShell Web Access-Zugriffssteuerung wird mithilfe der Windows PowerShell-Cmdlets verwaltet, die in der folgenden Tabelle beschrieben sind.</span><span class="sxs-lookup"><span data-stu-id="bbf31-256">Windows PowerShell Web Access access control is managed by using the set of Windows PowerShell cmdlets described in the following table.</span></span> <span data-ttu-id="bbf31-257">Eine vergleichbare GUI für das Hinzufügen und Verwalten von Autorisierungsregeln ist nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bbf31-257">There is no comparable GUI for adding or managing authorization rules.</span></span> <span data-ttu-id="bbf31-258">Ausführlichere Informationen zu Windows PowerShell Web Access-Cmdlets finden Sie in den Cmdlet-Referenzthemen unter [Windows PowerShell Web Access-Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span><span class="sxs-lookup"><span data-stu-id="bbf31-258">For more detailed information about Windows PowerShell Web Access cmdlets, see the cmdlet reference topics, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span></span>

<span data-ttu-id="bbf31-259">Weitere Informationen zu Windows PowerShell Web Access-Autorisierungsregeln und -Sicherheit finden Sie unter [Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span><span class="sxs-lookup"><span data-stu-id="bbf31-259">For more detail about Windows PowerShell Web Access authorization rules and security, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span></span>

#### <a name="to-add-a-restrictive-authorization-rule"></a><span data-ttu-id="bbf31-260">So fügen Sie eine restriktive Autorisierungsregel hinzu</span><span class="sxs-lookup"><span data-stu-id="bbf31-260">To add a restrictive authorization rule</span></span>

1.  <span data-ttu-id="bbf31-261">Öffnen Sie eine Windows PowerShell-Sitzung mit erhöhten Benutzerrechten, indem Sie einen der folgenden Schritte durchführen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-261">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="bbf31-262">Klicken Sie auf dem Windows-Desktop mit der rechten Maustaste in der Taskleiste auf **Windows PowerShell** und anschließend auf **Als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-262">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="bbf31-263">Klicken Sie auf dem Windows-**Startbildschirm** mit der rechten Maustaste auf **Windows PowerShell**, und klicken Sie anschließend auf **Als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-263">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="bbf31-264"><span class="label">Optionaler Schritt zur Einschränkung des Benutzerzugriffs mithilfe von Sitzungskonfigurationen:</span> Überprüfen Sie, ob Sitzungskonfigurationen, die Sie in Ihren Regeln verwenden möchten, bereits vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="bbf31-264"><span class="label">Optional step for restricting user access by using session configurations:</span> Verify that session configurations that you want to use in your rules already exist.</span></span> <span data-ttu-id="bbf31-265">Falls diese noch nicht erstellt wurden, verwenden Sie die Anleitung zum Erstellen von Sitzungskonfigurationen in MSDN unter [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx).</span><span class="sxs-lookup"><span data-stu-id="bbf31-265">If they have not yet been created, use instructions for creating session configurations in [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

3.  <span data-ttu-id="bbf31-266">Geben Sie Folgendes ein, und drücken Sie anschließend die **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-266">Type the following, and then press **Enter**.</span></span>

    [<span data-ttu-id="bbf31-267">Kopieren</span><span class="sxs-lookup"><span data-stu-id="bbf31-267">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_f9e7959b-75d0-4d63-8f8e-02334a8dd09d'); "In Zwischenablage kopieren.")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    <span data-ttu-id="bbf31-268">Diese Autorisierungsregel erlaubt es einem bestimmten Benutzer, auf einen Computer im Netzwerk zuzugreifen, auf den er normalerweise zugreifen kann. Der Zugriff ist auf eine bestimmte Sitzungskonfiguration beschränkt, die die üblichen Anforderungen des Benutzers im Hinblick auf die Ausführung von Skripts und Cmdlets abdeckt.</span><span class="sxs-lookup"><span data-stu-id="bbf31-268">This authorization rule allows a specific user access to one computer on the network to which they typically have access, with access to a specific session configuration that is scoped to the user’s typical scripting and cmdlet needs.</span></span> <span data-ttu-id="bbf31-269">Im folgenden Beispiel wird dem Benutzer <span class="code">JSmith</span> in der Domäne <span class="code">Contoso</span> Zugriff auf die Verwaltung des Computers <span class="code">Contoso_214</span> und die Verwendung einer Sitzungskonfiguration mit dem Namen <span class="code">NewAdminsOnly</span> gewährt.</span><span class="sxs-lookup"><span data-stu-id="bbf31-269">In the following example, a user named <span class="code">JSmith</span> in the <span class="code">Contoso</span> domain is granted access to manage the computer <span class="code">Contoso_214</span>, and use a session configuration named <span class="code">NewAdminsOnly</span>.</span></span>

    [<span data-ttu-id="bbf31-270">Kopieren</span><span class="sxs-lookup"><span data-stu-id="bbf31-270">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ebd5bc5e-ec5d-4955-a86a-63843e480e37'); "In Zwischenablage kopieren.")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  <span data-ttu-id="bbf31-271">Stellen Sie sicher, dass die Regel erstellt wurde, indem Sie entweder das Cmdlet **Get-PswaAuthorizationRule** oder **Test-PswaAuthorizationRule -UserName &lt;Domäne\\Benutzer | Computer\\Benutzer&gt; -ComputerName** &lt;Computername&gt; ausführen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-271">Verify that the rule has been created by running either the **Get-PswaAuthorizationRule** cmdlet, or **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span></span> <span data-ttu-id="bbf31-272">Beispiel: **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-272">For example, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span></span>

<span data-ttu-id="bbf31-273">Nachdem Sie eine Autorisierungsregel konfiguriert haben, können sich autorisierte Benutzer bei der webbasierten Konsole anmelden und mit der Nutzung von Windows PowerShell Web Access beginnen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-273">After you have configured an authorization rule, you are ready for authorized users to sign in to the web-based console and begin using Windows PowerShell Web Access.</span></span>

<a href="" id="BKMK_custom"></a>

<span data-ttu-id="bbf31-274"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Benutzerdefinierte Bereitstellung</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="bbf31-274"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Custom deployment</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="bbf31-275">Sie können das Windows PowerShell Web Access-Gateway auf einem Server mit Windows Server 2012 R2 oder Windows Server 2012 installieren, indem Sie den Assistenten zum Hinzufügen von Rollen und Features im Server-Manager verwenden.</span><span class="sxs-lookup"><span data-stu-id="bbf31-275">You can install the Windows PowerShell Web Access gateway on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using the Add Roles and Features Wizard in Server Manager.</span></span> <span data-ttu-id="bbf31-276">Nach der Installation von Windows PowerShell Web Access können Sie die Konfiguration des Gateways im IIS-Manager anpassen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-276">After Windows PowerShell Web Access is installed, you can customize the configuration of the gateway in IIS Manager.</span></span>

<a href="" id="BKMK_custom1"></a>
###

<span data-ttu-id="bbf31-277"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Schritt 1: Installieren von Windows PowerShell Web Access</span></a></span><span class="sxs-lookup"><span data-stu-id="bbf31-277"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Install Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-install-windows-powershell-web-access-by-using-the-add-roles-and-features-wizard"></a><span data-ttu-id="bbf31-278">So installieren Sie Windows PowerShell Web Access mithilfe des Assistenten zum Hinzufügen von Rollen und Features</span><span class="sxs-lookup"><span data-stu-id="bbf31-278">To install Windows PowerShell Web Access by using the Add Roles and Features Wizard</span></span>

1.  <span data-ttu-id="bbf31-279">Wenn der Server-Manager bereits geöffnet ist, fahren Sie mit dem nächsten Schritt fort.</span><span class="sxs-lookup"><span data-stu-id="bbf31-279">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="bbf31-280">Ist der Server-Manager noch nicht geöffnet, öffnen Sie ihn mit einer der folgenden Aktionen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-280">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="bbf31-281">Starten Sie auf dem Windows-Desktop den Server-Manager, indem Sie in der Windows-Taskleiste auf **Server-Manager** klicken.</span><span class="sxs-lookup"><span data-stu-id="bbf31-281">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="bbf31-282">Klicken Sie auf der Windows-Startseite**** auf **Server-Manager**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-282">On the Windows **Start** screen, click **Server Manager**.</span></span>

2.  <span data-ttu-id="bbf31-283">Klicken Sie im Menü **Verwalten** auf **Rollen und Funktionen hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-283">On the **Manage** menu, click **Add Roles and Features**.</span></span>

3.  <span data-ttu-id="bbf31-284">Wählen Sie auf der Seite **Installationstyp auswählen** die Option **Rollenbasierte oder featurebasierte Installation** aus.</span><span class="sxs-lookup"><span data-stu-id="bbf31-284">On the **Select installation type** page, select **Role-based or feature-based installation**.</span></span> <span data-ttu-id="bbf31-285">Klicken Sie auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-285">Click **Next**.</span></span>

4.  <span data-ttu-id="bbf31-286">Wählen Sie auf der Seite **Zielserver auswählen** einen Server aus dem Serverpool aus, oder wählen Sie eine Offline-VHD aus.</span><span class="sxs-lookup"><span data-stu-id="bbf31-286">On the **Select destination server** page, select a server from the server pool, or select an offline VHD.</span></span> <span data-ttu-id="bbf31-287">Um eine Offline-VHD als Zielserver auszuwählen, müssen Sie zuerst den Server auswählen, auf dem die VHD eingebunden werden soll. Wählen Sie anschließend die VHD-Datei aus.</span><span class="sxs-lookup"><span data-stu-id="bbf31-287">To select an offline VHD as your destination server, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="bbf31-288">Informationen zum Hinzufügen von Servern zu Ihrem Serverpool finden Sie in der Server-Manager-Hilfe.</span><span class="sxs-lookup"><span data-stu-id="bbf31-288">For information about how to add servers to your server pool, see the Server Manager Help.</span></span> <span data-ttu-id="bbf31-289">Klicken Sie nach dem Auswählen des Zielservers auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-289">After you have selected the destination server, click **Next**.</span></span>

5.  <span data-ttu-id="bbf31-290">Erweitern Sie im Assistenten auf der Seite **Features auswählen** die Option **Windows PowerShell**, und wählen Sie anschließend **Windows PowerShell Web Access** aus.</span><span class="sxs-lookup"><span data-stu-id="bbf31-290">On the **Select features** page of the wizard, expand **Windows PowerShell**, and then select **Windows PowerShell Web Access**.</span></span>

6.  <span data-ttu-id="bbf31-291">Sie werden aufgefordert, erforderliche Features, wie beispielsweise .NET Framework 4.5, und Rollendienste des Webservers (IIS) hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-291">Note that you are prompted to add required features, such as .NET Framework 4.5, and role services of Web Server (IIS).</span></span> <span data-ttu-id="bbf31-292">Fügen Sie die erforderlichen Features hinzu, und setzen Sie den Vorgang fort.</span><span class="sxs-lookup"><span data-stu-id="bbf31-292">Add required features and continue.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="bbf31-293"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Hinweis </span></span><span class="sxs-lookup"><span data-stu-id="bbf31-293"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="bbf31-294">Bei der Installation von Windows PowerShell Web Access mithilfe des Assistenten zum Hinzufügen von Rollen und Features wird auch Webserver (IIS) einschließlich IIS-Manager-Snap-In installiert.</span><span class="sxs-lookup"><span data-stu-id="bbf31-294">Installing Windows PowerShell Web Access by using the Add Roles and Features Wizard also installs Web Server (IIS), including the IIS Manager snap-in.</span></span> <span data-ttu-id="bbf31-295">Das Snap-In und andere IIS-Verwaltungstools werden standardmäßig installiert, wenn Sie den Assistenten zum Hinzufügen von Rollen und Features verwenden.</span><span class="sxs-lookup"><span data-stu-id="bbf31-295">The snap-in and other IIS management tools are installed by default if you use Add Roles and Features Wizard.</span></span> <span data-ttu-id="bbf31-296">Wenn Sie Windows PowerShell Web Access mithilfe von Windows PowerShell-Cmdlets wie im folgenden Verfahren beschrieben installieren, werden Verwaltungstools nicht standardmäßig hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="bbf31-296">If you install Windows PowerShell Web Access by using Windows PowerShell cmdlets as described in the following procedure, management tools are not added by default.</span></span></p></td>
    </tr>
    </tbody>
    </table>

7.  <span data-ttu-id="bbf31-297">Falls die Featuredateien für Windows PowerShell Web Access nicht auf dem in Schritt 4 ausgewählten Zielserver gespeichert sind, klicken Sie auf der Seite **Installationsauswahl bestätigen** auf **Alternativen Quellpfad angeben**, und geben Sie den Pfad zu den Featuredateien an.</span><span class="sxs-lookup"><span data-stu-id="bbf31-297">On the **Confirm installation selections** page, if the feature files for Windows PowerShell Web Access are not stored on the destination server that you selected in step 4, click **Specify an alternate source path**, and provide the path to the feature files.</span></span> <span data-ttu-id="bbf31-298">Klicken Sie andernfalls auf **Installieren**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-298">Otherwise, click **Install**.</span></span>

8.  <span data-ttu-id="bbf31-299">Nachdem Sie auf **Installieren** geklickt haben, werden auf der Seite **Installationsstatus** der Installationsstatus, Ergebnisse und Meldungen wie Warnungen, Fehler oder nach der Installation auszuführende Konfigurationsschritten angezeigt, die für Windows PowerShell Web Access erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="bbf31-299">After you click **Install**, the **Installation progress** page displays installation progress, results, and messages such as warnings, failures, or post-installation configuration steps that are required for Windows PowerShell Web Access.</span></span> <span data-ttu-id="bbf31-300">Nachdem Windows PowerShell Web Access installiert wurde, werden Sie aufgefordert, die Infodatei zu lesen, in der grundlegende, erforderliche Setupanweisungen für das Gateway enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="bbf31-300">After Windows PowerShell Web Access is installed, you are prompted to review the readme file, which contains basic, required setup instructions for the gateway.</span></span> <span data-ttu-id="bbf31-301">Diese Anweisungen sind auch in diesem Thema enthalten.</span><span class="sxs-lookup"><span data-stu-id="bbf31-301">These instructions are also included in this topic.</span></span> <span data-ttu-id="bbf31-302">Die Infodatei befindet sich unter <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt.</span></span><span class="sxs-lookup"><span data-stu-id="bbf31-302">The path to the readme file is <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span></span>

###

<span data-ttu-id="bbf31-303"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Schritt 2: Konfigurieren des Gateways</span></a></span><span class="sxs-lookup"><span data-stu-id="bbf31-303"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Configure the gateway</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="bbf31-304">Die Anweisungen in diesem Abschnitt gelten für die Installation der Windows PowerShell Web Access-Webanwendung in einem Unterverzeichnis der Website, und nicht im Stammverzeichnis.</span><span class="sxs-lookup"><span data-stu-id="bbf31-304">Instructions in this section are for installing the Windows PowerShell Web Access web application in a subdirectory—and not in the root directory—of your website.</span></span> <span data-ttu-id="bbf31-305">Dieses GUI-basierte Verfahren entspricht den Aktionen, die vom Cmdlet <span class="code">Install-PswaWebApplication</span> durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="bbf31-305">This procedure is the GUI-based equivalent of the actions performed by the <span class="code">Install-PswaWebApplication</span> cmdlet.</span></span> <span data-ttu-id="bbf31-306">Dieser Abschnitt enthält auch Anweisungen zur Verwendung des IIS-Managers zum Konfigurieren des Windows PowerShell Web Access-Gateways als Stammwebsite.</span><span class="sxs-lookup"><span data-stu-id="bbf31-306">This section also includes instructions for how to use IIS Manager to configure the Windows PowerShell Web Access gateway as a root website.</span></span>

-   [<span data-ttu-id="bbf31-307">So verwenden Sie den IIS-Manager, um das Gateway auf einer vorhandenen Website zu konfigurieren</span><span class="sxs-lookup"><span data-stu-id="bbf31-307">To use IIS Manager to configure the gateway in an existing website</span></span>](#BKMK_configman)

-   [<span data-ttu-id="bbf31-308">So verwenden Sie den IIS-Manager, um das Gateway als Stammwebsite mit einem Testzertifikat zu konfigurieren</span><span class="sxs-lookup"><span data-stu-id="bbf31-308">To use IIS Manager to configure the gateway as a root website with a test certificate</span></span>](#BKMK_configroot)

-   

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a><span data-ttu-id="bbf31-309">So verwenden Sie den IIS-Manager, um das Gateway auf einer vorhandenen Website zu konfigurieren</span><span class="sxs-lookup"><span data-stu-id="bbf31-309">To use IIS Manager to configure the gateway in an existing website</span></span>

1.  <span data-ttu-id="bbf31-310">Öffnen Sie die IIS-Manager-Konsole, indem Sie eine der folgenden Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="bbf31-310">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="bbf31-311">Starten Sie auf dem Windows-Desktop den Server-Manager, indem Sie in der Windows-Taskleiste auf **Server-Manager** klicken.</span><span class="sxs-lookup"><span data-stu-id="bbf31-311">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="bbf31-312">Klicken Sie im Menü **Tools** im Server-Manager auf **Internetinformationsdienste-Manager (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-312">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="bbf31-313">Geben Sie auf dem Windows-**Startbildschirm** einen beliebigen Teil des Namens **Internetinformationsdienste-Manager (IIS)** ein.</span><span class="sxs-lookup"><span data-stu-id="bbf31-313">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="bbf31-314">Klicken Sie auf die Verknüpfung, wenn diese in den **Apps**-Ergebnissen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bbf31-314">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="bbf31-315">Erstellen Sie einen neuen Anwendungspool für Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="bbf31-315">Create a new application pool for Windows PowerShell Web Access.</span></span> <span data-ttu-id="bbf31-316">Erweitern Sie den Knoten des Gatewayservers im IIS-Manager-Strukturbereich, wählen Sie die **Anwendungspools** aus, und klicken Sie im Bereich **Aktionen** auf **Anwendungspool hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-316">Expand the node of the gateway server in the IIS Manager tree pane, select **Application Pools**, and click **Add Application Pool** in the **Actions** pane.</span></span>

3.  <span data-ttu-id="bbf31-317">Fügen Sie einen neuen Anwendungspool mit dem Namen **pswa_pool** hinzu, oder geben Sie einen anderen Namen an.</span><span class="sxs-lookup"><span data-stu-id="bbf31-317">Add a new application pool with the name **pswa_pool**, or provide another name.</span></span> <span data-ttu-id="bbf31-318">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-318">Click **OK**.</span></span>

4.  <span data-ttu-id="bbf31-319">Erweitern Sie im IIS-Manager-Strukturbereich den Knoten für den Server, auf dem Windows PowerShell Web Access installiert ist, bis der Ordner **Sites** sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="bbf31-319">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="bbf31-320">Wählen Sie den Ordner **Sites** aus.</span><span class="sxs-lookup"><span data-stu-id="bbf31-320">Select the **Sites** folder.</span></span>

5.  <span data-ttu-id="bbf31-321">Klicken Sie mit der rechten Maustaste auf die Website (z.B. **Standardwebsite**), der Sie die Windows PowerShell Web Access-Website hinzufügen möchten, und klicken Sie anschließend auf **Anwendung hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-321">Right-click the website (for example, **Default Web Site**) to which you would like to add the Windows PowerShell Web Access website, and then click **Add Application**.</span></span>

6.  <span data-ttu-id="bbf31-322">Geben Sie im Feld **Alias** „pswa“ ein, oder geben Sie einen anderen Alias an.</span><span class="sxs-lookup"><span data-stu-id="bbf31-322">In the **Alias** field, type pswa, or provide another alias.</span></span> <span data-ttu-id="bbf31-323">Der Alias wird zum Namen des virtuellen Verzeichnisses.</span><span class="sxs-lookup"><span data-stu-id="bbf31-323">The alias becomes the virtual directory name.</span></span> <span data-ttu-id="bbf31-324">In der folgenden URL steht **pswa** z.B. für den Alias, der in diesem Schritt angegeben wurde: „https://&lt;Servername&gt;/pswa“.</span><span class="sxs-lookup"><span data-stu-id="bbf31-324">For example, **pswa** in the following URL represents the alias specified in this step: https://&lt;server_name&gt;/pswa.</span></span>

7.  <span data-ttu-id="bbf31-325">Wählen Sie im Feld **Anwendungspool** den Anwendungspool aus, den Sie in Schritt 3 erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="bbf31-325">In the **Application pool** field, select the application pool that you created in step 3.</span></span>

8.  <span data-ttu-id="bbf31-326">Suchen Sie im Feld **Physischer Pfad** nach dem Speicherort der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="bbf31-326">In the **Physical path** field, browse for the location of the application.</span></span> <span data-ttu-id="bbf31-327">Sie können den Standardspeicherort %%amp;quot;%windir%/Web/PowerShellWebAccess/wwwroot%%amp;quot;% verwenden.</span><span class="sxs-lookup"><span data-stu-id="bbf31-327">You can use the default location, %windir%/Web/PowerShellWebAccess/wwwroot.</span></span> <span data-ttu-id="bbf31-328">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-328">Click **OK**.</span></span>

9.  <span data-ttu-id="bbf31-329">Führen Sie die Schritte im Verfahren [So konfigurieren Sie ein SSL-Zertifikat im IIS-Manager](#BKMK_cert) in diesem Thema aus.</span><span class="sxs-lookup"><span data-stu-id="bbf31-329">Follow the steps in the procedure [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic.</span></span>

10. <span data-ttu-id="bbf31-330"><span class="label">Optionaler Sicherheitsschritt:</span> Doppelklicken Sie im Inhaltsbereich auf **SSL-Einstellungen**, während die Website im Strukturbereich ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="bbf31-330"><span class="label">Optional security step:</span> With the website selected in the tree pane, double-click **SSL Settings** in the content pane.</span></span> <span data-ttu-id="bbf31-331">Wählen Sie die Option **SSL erforderlich** aus, und klicken Sie anschließend im Bereich **Aktionen** auf **Übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-331">Select **Require SSL**, and then in the **Actions** pane, click **Apply**.</span></span> <span data-ttu-id="bbf31-332">Optional können Sie es im Bereich **SSL-Einstellungen** obligatorisch machen, dass Benutzer, die eine Verbindung mit der Windows PowerShell Web Access-Website herstellen, über Clientzertifikate verfügen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-332">Optionally, in the **SSL Settings** pane, you can require that users connecting to the Windows PowerShell Web Access website have client certificates.</span></span> <span data-ttu-id="bbf31-333">Clientzertifikate dienen dazu, die Identität des Benutzers eines Clientgeräts zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-333">Client certificates help to verify the identity of a client device user.</span></span> <span data-ttu-id="bbf31-334">Weitere Informationen dazu, wie das Anfordern von Clientzertifikaten die Sicherheit von Windows PowerShell Web Access erhöhen kann, finden Sie unter [Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx) in diesem Handbuch.</span><span class="sxs-lookup"><span data-stu-id="bbf31-334">For more information about how requiring client certificates can increase the security of Windows PowerShell Web Access, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx) in this guide.</span></span>

11. <span data-ttu-id="bbf31-335">Öffnen Sie eine Browsersitzung auf einem Clientgerät.</span><span class="sxs-lookup"><span data-stu-id="bbf31-335">Open a browser session on a client device.</span></span> <span data-ttu-id="bbf31-336">Weitere Informationen zu unterstützten Browsern und Geräten finden Sie in diesem Thema unter [Unterstützung für Browser und Clientgeräte](#BKMK_browser).</span><span class="sxs-lookup"><span data-stu-id="bbf31-336">For more information about supported browsers and devices, see [Browser and client device support](#BKMK_browser) in this topic.</span></span>

12. <span data-ttu-id="bbf31-337">Öffnen Sie die neue Windows PowerShell Web Access-Website https://&lt;*Gatewayservername*&gt;/pswa.</span><span class="sxs-lookup"><span data-stu-id="bbf31-337">Open the new Windows PowerShell Web Access website, https://&lt; *gateway_server_name*&gt;/pswa.</span></span>

    <span data-ttu-id="bbf31-338">Der Browser sollte die Anmeldeseite der Windows PowerShell Web Access-Konsole anzeigen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-338">The browser should display the Windows PowerShell Web Access console sign-in page.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="bbf31-339"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Hinweis </span></span><span class="sxs-lookup"><span data-stu-id="bbf31-339"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="bbf31-340">Eine Anmeldung ist erst möglich, nachdem den Benutzern durch Hinzufügen von Autorisierungsregeln der Zugriff auf die Website gestattet wurde.</span><span class="sxs-lookup"><span data-stu-id="bbf31-340">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span></p></td>
    </tr>
    </tbody>
    </table>

13. <span data-ttu-id="bbf31-341">Führen Sie in einer mit erhöhten Benutzerrechten (Als Administrator ausführen) geöffneten Windows PowerShell-Sitzung das folgende Skript aus (hierbei entspricht *Anwendungspoolname* dem Namen des in Schritt 3 erstellten Anwendungspools), um dem Anwendungspool Zugriffsrechte für die Autorisierungsdatei zu erteilen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-341">In a Windows PowerShell session that has been opened with elevated user rights (Run as Administrator), run the following script, in which *application_pool_name* represents the name of the application pool that you created in step 3, to give the application pool access rights to the authorization file.</span></span>

    [<span data-ttu-id="bbf31-342">Kopieren</span><span class="sxs-lookup"><span data-stu-id="bbf31-342">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_c1a80a93-8fcf-4beb-a025-5f81bfb8bdae'); "In Zwischenablage kopieren.")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    <span data-ttu-id="bbf31-343">Führen Sie den folgenden Befehl aus, um die vorhandenen Zugriffsrechte für die Autorisierungsdatei anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="bbf31-343">To view existing access rights on the authorization file, run the following command:</span></span>

    [<span data-ttu-id="bbf31-344">Kopieren</span><span class="sxs-lookup"><span data-stu-id="bbf31-344">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ac2179c2-9548-4a17-8663-267fdd105380'); "In Zwischenablage kopieren.")

        c:\windows\system32\icacls.exe $authorizationFile

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a><span data-ttu-id="bbf31-345">So verwenden Sie den IIS-Manager, um das Gateway als Stammwebsite mit einem Testzertifikat zu konfigurieren</span><span class="sxs-lookup"><span data-stu-id="bbf31-345">To use IIS Manager to configure the gateway as a root website with a test certificate</span></span>

1.  <span data-ttu-id="bbf31-346">Öffnen Sie die IIS-Manager-Konsole, indem Sie eine der folgenden Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="bbf31-346">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="bbf31-347">Starten Sie auf dem Windows-Desktop den Server-Manager, indem Sie in der Windows-Taskleiste auf **Server-Manager** klicken.</span><span class="sxs-lookup"><span data-stu-id="bbf31-347">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="bbf31-348">Klicken Sie im Menü **Tools** im Server-Manager auf **Internetinformationsdienste-Manager (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-348">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="bbf31-349">Geben Sie auf dem Windows-**Startbildschirm** einen beliebigen Teil des Namens **Internetinformationsdienste-Manager (IIS)** ein.</span><span class="sxs-lookup"><span data-stu-id="bbf31-349">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="bbf31-350">Klicken Sie auf die Verknüpfung, wenn diese in den **Apps**-Ergebnissen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bbf31-350">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="bbf31-351">Erweitern Sie im IIS-Manager-Strukturbereich den Knoten für den Server, auf dem Windows PowerShell Web Access installiert ist, bis der Ordner **Sites** sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="bbf31-351">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="bbf31-352">Wählen Sie den Ordner **Sites** aus.</span><span class="sxs-lookup"><span data-stu-id="bbf31-352">Select the **Sites** folder.</span></span>

3.  <span data-ttu-id="bbf31-353">Klicken Sie im Bereich **Aktionen** auf **Website hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-353">In the **Actions** pane, click **Add Website**.</span></span>

4.  <span data-ttu-id="bbf31-354">Geben Sie einen Namen für die Website ein, z.B. **Windows PowerShell Web Access**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-354">Type a name for the website, such as **Windows PowerShell Web Access**.</span></span>

5.  <span data-ttu-id="bbf31-355">Für die neue Website wird automatisch ein Anwendungspool erstellt.</span><span class="sxs-lookup"><span data-stu-id="bbf31-355">An application pool is automatically created for the new website.</span></span> <span data-ttu-id="bbf31-356">Wenn Sie einen anderen Anwendungspool verwenden möchten, klicken Sie auf **Auswählen**, um einen Anwendungspool zum Zuordnen zur neuen Website auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-356">To use a different application pool, click **Select** to select an application pool to associate with the new website.</span></span> <span data-ttu-id="bbf31-357">Wählen Sie den alternativen Anwendungspool im Dialogfeld **Anwendungspool auswählen** aus, und klicken Sie anschließend auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-357">Select the alternate application pool in the **Select Application Pool** dialog box, and then click **OK**.</span></span>

6.  <span data-ttu-id="bbf31-358">Navigieren Sie im Textfeld **Physischer Pfad** zu %*windir*%/Web/PowerShellWebAccess/wwwroot.</span><span class="sxs-lookup"><span data-stu-id="bbf31-358">In the **Physical path** text box, navigate to %*windir*%/Web/PowerShellWebAccess/wwwroot.</span></span>

7.  <span data-ttu-id="bbf31-359">Wählen Sie unter **Bindung** im Feld **Typ** die Option **https** aus.</span><span class="sxs-lookup"><span data-stu-id="bbf31-359">In the **Type** field of the **Binding** area, select **https**.</span></span>

8.  <span data-ttu-id="bbf31-360">Weisen Sie der Website eine Portnummer zu, die noch nicht von einer anderen Website oder -anwendung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bbf31-360">Assign a port number to the website that is not already in use by another site or application.</span></span> <span data-ttu-id="bbf31-361">Sie können den **netstat**-Befehl in einem Eingabeaufforderungsfenster ausführen, um nach offenen Ports zu suchen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-361">To locate open ports, you can run the **netstat** command in a Command Prompt window.</span></span> <span data-ttu-id="bbf31-362">Die Standardportnummer ist 443.</span><span class="sxs-lookup"><span data-stu-id="bbf31-362">The default port number is 443.</span></span>

    <span data-ttu-id="bbf31-363">Ändern Sie den Standardport, falls Port 443 bereits von einer anderen Website verwendet wird oder wenn das Ändern der Portnummer aus anderen Sicherheitsgründen notwendig ist.</span><span class="sxs-lookup"><span data-stu-id="bbf31-363">Change the default port if another website is already using 443, or if you have other security reasons for changing the port number.</span></span> <span data-ttu-id="bbf31-364">Falls eine andere Website, die auf dem Gatewayserver ausgeführt wird, den ausgewählten Port verwendet, wird eine Warnung angezeigt, wenn Sie im Dialogfeld **Website hinzufügen** auf **OK** klicken.</span><span class="sxs-lookup"><span data-stu-id="bbf31-364">If another website that is running on your gateway server is using your selected port, a warning is displayed when you click **OK** in the **Add Website** dialog box.</span></span> <span data-ttu-id="bbf31-365">Sie müssen einen nicht verwendeten Port zum Ausführen von Windows PowerShell Web Access verwenden.</span><span class="sxs-lookup"><span data-stu-id="bbf31-365">You must use an unused port to run Windows PowerShell Web Access.</span></span>

9.  <span data-ttu-id="bbf31-366">Falls dies für Ihre Organisation erforderlich ist, können Sie optional einen Hostnamen angeben, der für die Organisation und Benutzer sinnvoll ist, z.B. **www.contoso.com**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-366">Optionally, if needed for your organization, specify a host name that makes sense to your organization and users, such as **www.contoso.com**.</span></span> <span data-ttu-id="bbf31-367">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-367">Click **OK**.</span></span>

10. <span data-ttu-id="bbf31-368">Zur Erhöhung der Sicherheit von Produktionsumgebungen wird dringend dazu geraten, ein gültiges Zertifikat bereitzustellen, das von einer Zertifizierungsstelle signiert wurde.</span><span class="sxs-lookup"><span data-stu-id="bbf31-368">For a more secure production environment, we strongly recommend providing a valid certificate that has been signed by a CA.</span></span> <span data-ttu-id="bbf31-369">Sie müssen ein SSL-Zertifikat bereitstellen, weil Benutzer die Verbindung mit Windows PowerShell Web Access nur über eine HTTPS-Website herstellen können.</span><span class="sxs-lookup"><span data-stu-id="bbf31-369">You must provide an SSL certificate, because users can only connect to Windows PowerShell Web Access through an HTTPS website.</span></span> <span data-ttu-id="bbf31-370">Weitere Informationen zum Anfordern eines Zertifikats finden Sie in diesem Thema unter [So konfigurieren Sie ein SSL-Zertifikat im IIS-Manager](#BKMK_cert).</span><span class="sxs-lookup"><span data-stu-id="bbf31-370">See [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic for more information about how to obtain a certificate.</span></span>

11. <span data-ttu-id="bbf31-371">Klicken Sie auf **OK**, um das Dialogfeld **Website hinzufügen** zu schließen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-371">Click **OK** to close the **Add Website** dialog box.</span></span>

12. <span data-ttu-id="bbf31-372">Führen Sie in einer mit erhöhten Benutzerrechten (Als Administrator ausführen) geöffneten Windows PowerShell-Sitzung das folgende Skript aus (hierbei entspricht *Anwendungspoolname* dem Namen des in Schritt 4 erstellten Anwendungspools), um dem Anwendungspool Zugriffsrechte für die Autorisierungsdatei zu erteilen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-372">In a Windows PowerShell session that has been opened with elevated user rights (Run as Administrator), run the following script, in which *application_pool_name* represents the name of the application pool that you created in step 4, to give the application pool access rights to the authorization file.</span></span>

    [<span data-ttu-id="bbf31-373">Kopieren</span><span class="sxs-lookup"><span data-stu-id="bbf31-373">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_35ae9944-ca44-4af7-9c96-616083b3e3db'); "In Zwischenablage kopieren.")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    <span data-ttu-id="bbf31-374">Führen Sie den folgenden Befehl aus, um die vorhandenen Zugriffsrechte für die Autorisierungsdatei anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="bbf31-374">To view existing access rights on the authorization file, run the following command:</span></span>

    [<span data-ttu-id="bbf31-375">Kopieren</span><span class="sxs-lookup"><span data-stu-id="bbf31-375">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_0eb6d70a-2807-498b-b088-fa5233ed68d5'); "In Zwischenablage kopieren.")

        c:\windows\system32\icacls.exe $authorizationFile

13. <span data-ttu-id="bbf31-376">Klicken Sie, während die neue Website im IIS-Manager-Strukturbereich ausgewählt ist, im Bereich **Aktionen** auf **Start**, um die Website zu starten.</span><span class="sxs-lookup"><span data-stu-id="bbf31-376">With the new website selected in the IIS Manager tree pane, click **Start** in the **Actions** pane to start the website.</span></span>

14. <span data-ttu-id="bbf31-377">Öffnen Sie eine Browsersitzung auf einem Clientgerät.</span><span class="sxs-lookup"><span data-stu-id="bbf31-377">Open a browser session on a client device.</span></span> <span data-ttu-id="bbf31-378">Weitere Informationen zu unterstützten Browsern und Geräten finden Sie in diesem Dokument unter [Unterstützung für Browser und Clientgeräte](#BKMK_browser).</span><span class="sxs-lookup"><span data-stu-id="bbf31-378">For more information about supported browsers and devices, see [Browser and client device support](#BKMK_browser) in this document.</span></span>

15. <span data-ttu-id="bbf31-379">Öffnen Sie die neue Windows PowerShell Web Access-Website.</span><span class="sxs-lookup"><span data-stu-id="bbf31-379">Open the new Windows PowerShell Web Access website.</span></span>

    <span data-ttu-id="bbf31-380">Da die Stammwebsite auf den Windows PowerShell Web Access-Ordner verweist, sollte im Browser die Anmeldeseite von Windows PowerShell Web Access angezeigt werden, wenn Sie „https://&lt; *Gatewayservername*&gt;“ öffnen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-380">Because the root website points to the Windows PowerShell Web Access folder, the browser should display the Windows PowerShell Web Access sign-in page when you open https://&lt; *gateway_server_name*&gt;.</span></span> <span data-ttu-id="bbf31-381">Es sollte nicht erforderlich sein, der URL **/pswa** hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-381">You should not need to add **/pswa** to the URL.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="bbf31-382"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Hinweis </span></span><span class="sxs-lookup"><span data-stu-id="bbf31-382"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="bbf31-383">Eine Anmeldung ist erst möglich, nachdem den Benutzern durch Hinzufügen von Autorisierungsregeln der Zugriff auf die Website gestattet wurde.</span><span class="sxs-lookup"><span data-stu-id="bbf31-383">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span></p></td>
    </tr>
    </tbody>
    </table>

###

<span data-ttu-id="bbf31-384"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Schritt 3: Konfigurieren einer restriktiven Autorisierungsregel</span></a></span><span class="sxs-lookup"><span data-stu-id="bbf31-384"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 3: Configure a restrictive authorization rule</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="bbf31-385">Nach der Installation von Windows PowerShell Web Access und der Konfiguration des Gateways können Benutzer die Anmeldeseite in einem Browser öffnen. Sie können sich jedoch erst anmelden, nachdem der Windows PowerShell Web Access-Administrator ihnen ausdrücklich Zugriff gewährt hat.</span><span class="sxs-lookup"><span data-stu-id="bbf31-385">After Windows PowerShell Web Access is installed and the gateway is configured, users can open the sign-in page in a browser, but they cannot sign in until the Windows PowerShell Web Access administrator grants users access explicitly.</span></span> <span data-ttu-id="bbf31-386">Die Windows PowerShell Web Access-Zugriffssteuerung wird mithilfe der Windows PowerShell-Cmdlets verwaltet, die in der folgenden Tabelle beschrieben sind.</span><span class="sxs-lookup"><span data-stu-id="bbf31-386">Windows PowerShell Web Access access control is managed by using the set of Windows PowerShell cmdlets described in the following table.</span></span> <span data-ttu-id="bbf31-387">Eine vergleichbare GUI für das Hinzufügen und Verwalten von Autorisierungsregeln ist nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bbf31-387">There is no comparable GUI for adding or managing authorization rules.</span></span> <span data-ttu-id="bbf31-388">Ausführlichere Informationen zu Windows PowerShell Web Access-Cmdlets finden Sie in den Cmdlet-Referenzthemen unter [Windows PowerShell Web Access-Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span><span class="sxs-lookup"><span data-stu-id="bbf31-388">For more detailed information about Windows PowerShell Web Access cmdlets, see the cmdlet reference topics, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span></span>

<span data-ttu-id="bbf31-389">Weitere Informationen zu Windows PowerShell Web Access-Autorisierungsregeln und -Sicherheit finden Sie unter [Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span><span class="sxs-lookup"><span data-stu-id="bbf31-389">For more detail about Windows PowerShell Web Access authorization rules and security, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span></span>

#### <a name="to-add-a-restrictive-authorization-rule"></a><span data-ttu-id="bbf31-390">So fügen Sie eine restriktive Autorisierungsregel hinzu</span><span class="sxs-lookup"><span data-stu-id="bbf31-390">To add a restrictive authorization rule</span></span>

1.  <span data-ttu-id="bbf31-391">Öffnen Sie eine Windows PowerShell-Sitzung mit erhöhten Benutzerrechten, indem Sie einen der folgenden Schritte durchführen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-391">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="bbf31-392">Klicken Sie auf dem Windows-Desktop mit der rechten Maustaste in der Taskleiste auf **Windows PowerShell** und anschließend auf **Als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-392">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="bbf31-393">Klicken Sie auf dem Windows-**Startbildschirm** mit der rechten Maustaste auf **Windows PowerShell**, und klicken Sie anschließend auf **Als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-393">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="bbf31-394"><span class="label">Optionaler Schritt zur Einschränkung des Benutzerzugriffs mithilfe von Sitzungskonfigurationen:</span> Überprüfen Sie, ob Sitzungskonfigurationen, die Sie in Ihren Regeln verwenden möchten, bereits vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="bbf31-394"><span class="label">Optional step for restricting user access by using session configurations:</span> Verify that session configurations that you want to use in your rules already exist.</span></span> <span data-ttu-id="bbf31-395">Falls diese noch nicht erstellt wurden, verwenden Sie die Anleitung zum Erstellen von Sitzungskonfigurationen in MSDN unter [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx).</span><span class="sxs-lookup"><span data-stu-id="bbf31-395">If they have not yet been created, use instructions for creating session configurations in [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

3.  <span data-ttu-id="bbf31-396">Geben Sie Folgendes ein, und drücken Sie anschließend die **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-396">Type the following, and then press **Enter**.</span></span>

    [<span data-ttu-id="bbf31-397">Kopieren</span><span class="sxs-lookup"><span data-stu-id="bbf31-397">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_4df22c91-f56f-4bb5-91e7-99f9b365ed5d'); "In Zwischenablage kopieren.")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    <span data-ttu-id="bbf31-398">Diese Autorisierungsregel erlaubt es einem bestimmten Benutzer, auf einen Computer im Netzwerk zuzugreifen, auf den er normalerweise zugreifen kann. Der Zugriff ist auf eine bestimmte Sitzungskonfiguration beschränkt, die die üblichen Anforderungen des Benutzers im Hinblick auf die Ausführung von Skripts und Cmdlets abdeckt.</span><span class="sxs-lookup"><span data-stu-id="bbf31-398">This authorization rule allows a specific user access to one computer on the network to which they typically have access, with access to a specific session configuration that is scoped to the user’s typical scripting and cmdlet needs.</span></span> <span data-ttu-id="bbf31-399">Im folgenden Beispiel wird dem Benutzer <span class="code">JSmith</span> in der Domäne <span class="code">Contoso</span> Zugriff auf die Verwaltung des Computers <span class="code">Contoso_214</span> und die Verwendung einer Sitzungskonfiguration mit dem Namen <span class="code">NewAdminsOnly</span> gewährt.</span><span class="sxs-lookup"><span data-stu-id="bbf31-399">In the following example, a user named <span class="code">JSmith</span> in the <span class="code">Contoso</span> domain is granted access to manage the computer <span class="code">Contoso_214</span>, and use a session configuration named <span class="code">NewAdminsOnly</span>.</span></span>

    [<span data-ttu-id="bbf31-400">Kopieren</span><span class="sxs-lookup"><span data-stu-id="bbf31-400">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_efc3999a-2905-453f-86cd-014b41658ffc'); "In Zwischenablage kopieren.")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  <span data-ttu-id="bbf31-401">Stellen Sie sicher, dass die Regel erstellt wurde, indem Sie entweder das Cmdlet **Get-PswaAuthorizationRule** oder **Test-PswaAuthorizationRule -UserName &lt;Domäne\\Benutzer | Computer\\Benutzer&gt; -ComputerName** &lt;Computername&gt; ausführen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-401">Verify that the rule has been created by running either the **Get-PswaAuthorizationRule** cmdlet, or **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span></span> <span data-ttu-id="bbf31-402">Beispiel: **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-402">For example, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span></span>

<span data-ttu-id="bbf31-403">Nachdem Sie eine Autorisierungsregel konfiguriert haben, können sich autorisierte Benutzer bei der webbasierten Konsole anmelden und mit der Nutzung von Windows PowerShell Web Access beginnen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-403">After you have configured an authorization rule, you are ready for authorized users to sign in to the web-based console and begin using Windows PowerShell Web Access.</span></span>

<a href="" id="BKMK_configcert"></a>

<span data-ttu-id="bbf31-404"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Konfigurieren eines Originalzertifikats</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="bbf31-404"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configure a genuine certificate</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="bbf31-405">Für sichere Produktionsumgebungen sollten Sie stets ein gültiges, von einer Zertifizierungsstelle (ZS) signiertes SSL-Zertifikat verwenden.</span><span class="sxs-lookup"><span data-stu-id="bbf31-405">For a secure production environment, always use a valid SSL certificate that has been signed by a certification authority (CA).</span></span> <span data-ttu-id="bbf31-406">In diesem Abschnitt wird das Verfahren beschrieben, mit dem Sie ein gültiges SSL-Zertifikat von einer Zertifizierungsstelle beziehen und anwenden.</span><span class="sxs-lookup"><span data-stu-id="bbf31-406">The procedure in this section describes how to obtain and apply a valid SSL certificate from a CA.</span></span>

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a><span data-ttu-id="bbf31-407">So konfigurieren Sie ein SSL-Zertifikat im IIS-Manager</span><span class="sxs-lookup"><span data-stu-id="bbf31-407">To configure an SSL certificate in IIS Manager</span></span>

1.  <span data-ttu-id="bbf31-408">Wählen Sie im IIS-Manager-Strukturbereich den Server aus, auf dem Windows PowerShell Web Access installiert ist.</span><span class="sxs-lookup"><span data-stu-id="bbf31-408">In the IIS Manager tree pane, select the server on which Windows PowerShell Web Access is installed.</span></span>

2.  <span data-ttu-id="bbf31-409">Doppelklicken Sie im Inhaltsbereich auf **Serverzertifikate**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-409">In the content pane, double click **Server Certificates**.</span></span>

3.  <span data-ttu-id="bbf31-410">Führen Sie im Bereich **Aktionen** eine der folgenden Aktionen aus.</span><span class="sxs-lookup"><span data-stu-id="bbf31-410">In the **Actions** pane, do one of the following.</span></span> <span data-ttu-id="bbf31-411">Weitere Informationen zur Konfiguration von Serverzertifikaten in IIS finden Sie unter [Konfigurieren von Serverzertifikaten in IIS 7](https://technet.microsoft.com/library/cc732230.aspx).</span><span class="sxs-lookup"><span data-stu-id="bbf31-411">For more information about configuring server certificates in IIS, see [Configuring Server Certificates in IIS 7](https://technet.microsoft.com/library/cc732230.aspx).</span></span>

    -   <span data-ttu-id="bbf31-412">Klicken Sie auf **Importieren**, um ein vorhandenes gültiges Zertifikat von einem Speicherort im Netzwerk zu importieren.</span><span class="sxs-lookup"><span data-stu-id="bbf31-412">Click **Import** to import an existing, valid certificate from a location on your network.</span></span>

    -   <span data-ttu-id="bbf31-413">Klicken Sie auf **Zertifikatanforderung erstellen**, um ein Zertifikat von einer Zertifizierungsstelle wie VeriSign™, Thawte oder GeoTrust® anzufordern.</span><span class="sxs-lookup"><span data-stu-id="bbf31-413">Click **Create Certificate Request** to request a certificate from a CA such as VeriSign™, Thawte, or GeoTrust®.</span></span> <span data-ttu-id="bbf31-414">Der allgemeine Name des Zertifikats muss dem Hostheader in der Anforderung entsprechen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-414">The certificate's common name must match the host header in the request.</span></span> <span data-ttu-id="bbf31-415">Wenn der Clientbrowser beispielsweise http://www.contoso.com/ anfordert, muss der allgemeine Name ebenfalls http://www.contoso.com/ lauten.</span><span class="sxs-lookup"><span data-stu-id="bbf31-415">For example, if the client browser requests http://www.contoso.com/, then the common name must also be http://www.contoso.com/.</span></span> <span data-ttu-id="bbf31-416">Dies ist die sicherste und empfohlene Option, um das Windows PowerShell Web Access-Gateway mit einem Zertifikat zu versehen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-416">This is the most secure and recommended option for providing the Windows PowerShell Web Access gateway with a certificate.</span></span>

    -   <span data-ttu-id="bbf31-417">Klicken Sie auf **Selbstsigniertes Zertifikat erstellen**, um ein Zertifikat zu erstellen, das Sie sofort verwenden und später bei Bedarf von einer Zertifizierungsstelle signieren lassen können.</span><span class="sxs-lookup"><span data-stu-id="bbf31-417">Click **Create a Self-Signed Certificate** to create a certificate that you can use immediately, and have signed later by a CA if desired.</span></span> <span data-ttu-id="bbf31-418">Geben Sie einen Anzeigenamen für das selbstsignierte Zertifikat an, z.B. **Windows PowerShell Web Access**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-418">Specify a friendly name for the self-signed certificate, such as **Windows PowerShell Web Access**.</span></span> <span data-ttu-id="bbf31-419">Diese Vorgehensweise ist als nicht sicher anzusehen und wird nur für eine private Testumgebung empfohlen.</span><span class="sxs-lookup"><span data-stu-id="bbf31-419">This option is not considered secure, and is recommended only for a private test environment.</span></span>

4.  <span data-ttu-id="bbf31-420">Wählen Sie nach der Erstellung bzw. Beschaffung eines Zertifikats die Website, auf die das Zertifikat angewendet werden soll (z.B. **Standardwebsite**), im IIS-Manager-Strukturbereich aus. Klicken Sie anschließend im Bereich **Aktionen** auf **Bindungen**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-420">After creating or obtaining a certificate, select the website to which the certificate is applied (for example, **Default Web Site**) in the IIS Manager tree pane, and then click **Bindings** in the **Actions** pane.</span></span>

5.  <span data-ttu-id="bbf31-421">Fügen Sie im Dialogfeld **Websitebindung hinzufügen** eine Bindung vom Typ **https** für die Website hinzu, falls noch keine Bindung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bbf31-421">In the **Add Site Binding** dialog box, add an **https** binding for the site, if one is not already displayed.</span></span> <span data-ttu-id="bbf31-422">Wenn Sie kein selbstsigniertes Zertifikat verwenden, geben Sie den Hostnamen aus Schritt 3 dieses Verfahrens an.</span><span class="sxs-lookup"><span data-stu-id="bbf31-422">If you are not using a self-signed certificate, specify the host name from step 3 of this procedure.</span></span> <span data-ttu-id="bbf31-423">Wenn Sie ein selbstsigniertes Zertifikat verwenden, ist dieser Schritt nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="bbf31-423">If you are using a self-signed certificate, this step is not required.</span></span>

6.  <span data-ttu-id="bbf31-424">Wählen Sie das Zertifikat aus, das Sie in Schritt 3 dieses Verfahrens abgerufen oder erstellt haben, und klicken Sie anschließend auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="bbf31-424">Select the certificate that you obtained or created in step 3 of this procedure, and then click **OK**.</span></span>

<a href="" id="BKMK_using"></a>

<span data-ttu-id="bbf31-425"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Verwenden der webbasierten Windows PowerShell-Konsole</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_5" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="bbf31-425"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Using the web-based Windows PowerShell console</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_5" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="bbf31-426">Nachdem Windows PowerShell Web Access installiert und die Gatewaykonfiguration wie in diesem Thema beschrieben abgeschlossen wurde, ist die webbasierte Windows PowerShell-Konsole für die Verwendung bereit.</span><span class="sxs-lookup"><span data-stu-id="bbf31-426">After Windows PowerShell Web Access is installed and the gateway configuration is finished as described in this topic, the Windows PowerShell web-based console is ready to use.</span></span> <span data-ttu-id="bbf31-427">Weitere Informationen zu den ersten Schritten mit der webbasierten Konsole finden Sie unter [Verwendung der webbasierten Windows PowerShell-Konsole](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx).</span><span class="sxs-lookup"><span data-stu-id="bbf31-427">For more information about getting started in the web-based console, see [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx).</span></span>

<span data-ttu-id="bbf31-428"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Siehe auch</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_6" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="bbf31-428"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_6" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="bbf31-429">[Dokumentation zu Internetinformationsdienste (IIS) 7.0](https://technet.microsoft.com/library/cc753433.aspx)
[Hilfe zum IIS-Manager 7.0](https://technet.microsoft.com/library/cc732664.aspx)
[Konfigurieren der Webserversicherheit (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
[Ressourcen zur IPsec-Bereitstellung](https://technet.microsoft.com/network/bb531150)</span><span class="sxs-lookup"><span data-stu-id="bbf31-429">[Internet Information Services (IIS) 7.0 Documentation](https://technet.microsoft.com/library/cc753433.aspx)
[IIS Manager 7.0 Help](https://technet.microsoft.com/library/cc732664.aspx)
[Configure Web Server Security (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
[IPsec Deployment Resources](https://technet.microsoft.com/network/bb531150)</span></span>

<span data-ttu-id="bbf31-430"><span>Show:</span> Inherited Protected</span><span class="sxs-lookup"><span data-stu-id="bbf31-430"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="bbf31-431"><span class="stdr-votetitle">War diese Seite hilfreich?</span></span><span class="sxs-lookup"><span data-stu-id="bbf31-431"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="bbf31-432">Ja Nein</span><span class="sxs-lookup"><span data-stu-id="bbf31-432">Yes No</span></span>

<span data-ttu-id="bbf31-433">Zusätzliches Feedback?</span><span class="sxs-lookup"><span data-stu-id="bbf31-433">Additional feedback?</span></span>

<span data-ttu-id="bbf31-434"><span class="stdr-count"><span class="stdr-charcnt">1.500</span> verbleibende Zeichen</span> Senden Diesen Schritt überspringen</span><span class="sxs-lookup"><span data-stu-id="bbf31-434"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="bbf31-435"><span class="stdr-thankyou">Vielen Dank!</span></span><span class="sxs-lookup"><span data-stu-id="bbf31-435"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="bbf31-436"><span class="stdr-appreciate">Wir schätzen Ihr Feedback.</span></span><span class="sxs-lookup"><span data-stu-id="bbf31-436"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="bbf31-437">Profil verwalten</span><span class="sxs-lookup"><span data-stu-id="bbf31-437">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="bbf31-438"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Feedback zur Website</a> Feedback zur Website</span><span class="sxs-lookup"><span data-stu-id="bbf31-438"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="bbf31-439"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="bbf31-439"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="bbf31-440">Teilen Sie uns Ihre Erfahrungen mit.</span><span class="sxs-lookup"><span data-stu-id="bbf31-440">Tell us about your experience...</span></span>

<span data-ttu-id="bbf31-441">Wurde die Seite schnell geladen?</span><span class="sxs-lookup"><span data-stu-id="bbf31-441">Did the page load quickly?</span></span>

<span data-ttu-id="bbf31-442"><span> Ja<span> </span></span> <span> Nein<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="bbf31-442"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="bbf31-443">Gefällt Ihnen das Design der Seite?</span><span class="sxs-lookup"><span data-stu-id="bbf31-443">Do you like the page design?</span></span>

<span data-ttu-id="bbf31-444"><span> Ja<span> </span></span> <span> Nein<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="bbf31-444"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="bbf31-445">Erzählen Sie uns mehr</span><span class="sxs-lookup"><span data-stu-id="bbf31-445">Tell us more</span></span>

-   [<span data-ttu-id="bbf31-446">Flash-Newsletter</span><span class="sxs-lookup"><span data-stu-id="bbf31-446">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="bbf31-447">So erreichen Sie uns</span><span class="sxs-lookup"><span data-stu-id="bbf31-447">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="bbf31-448">Datenschutzbestimmungen</span><span class="sxs-lookup"><span data-stu-id="bbf31-448">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="bbf31-449">Nutzungsbedingungen</span><span class="sxs-lookup"><span data-stu-id="bbf31-449">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="bbf31-450">Marken</span><span class="sxs-lookup"><span data-stu-id="bbf31-450">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="bbf31-451">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="bbf31-451">© 2016 Microsoft</span></span>

<span data-ttu-id="bbf31-452">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="bbf31-452">© 2016 Microsoft</span></span>

<span data-ttu-id="bbf31-453">Die Lizenz für Drittanbieterskripts oder Code, die mit dieser Website verlinkt oder über Verweise verbunden sind, wird Ihnen von den Codeeigentümern erteilt, nicht von Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bbf31-453">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="bbf31-454">Die ASP.NET Ajax CDN-Nutzungsbedingungen finden Sie unter http://www.asp.net/ajaxlibrary/CDN.ashx.</span><span class="sxs-lookup"><span data-stu-id="bbf31-454">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

