---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Behandeln von Zugriffsproblemen in Windows PowerShell Web Access
ms.openlocfilehash: c10e19b177110ff62d44f28b6a523380b55b79e0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
#  <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="b0da1-103">Behandeln von Zugriffsproblemen in Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="b0da1-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="b0da1-104">Aktualisiert: 24. Juni 2013</span><span class="sxs-lookup"><span data-stu-id="b0da1-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="b0da1-105">Gilt für: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="b0da1-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<a href="" id="BKMK_trouble"></a>

------------------------------------------------------------------------

<span data-ttu-id="b0da1-106">In der folgenden Tabelle sind einige allgemeine Probleme aufgeführt, die möglicherweise auftreten, wenn Benutzer über Windows PowerShell Web Access eine Verbindung mit einem Remotecomputer herstellen möchten. Außerdem enthält die Tabelle Vorschläge zur Behebung der Probleme.</span><span class="sxs-lookup"><span data-stu-id="b0da1-106">The following table identifies some common problems that users might experience when they are attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="b0da1-107">Problem</span><span class="sxs-lookup"><span data-stu-id="b0da1-107">Problem</span></span></p></th>
<th><p><span data-ttu-id="b0da1-108">Mögliche Ursache und Lösung</span><span class="sxs-lookup"><span data-stu-id="b0da1-108">Possible cause and solution</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="b0da1-109">Fehler bei der Anmeldung.</span><span class="sxs-lookup"><span data-stu-id="b0da1-109">Sign-in failure</span></span></p></td>
<td><p><span data-ttu-id="b0da1-110">Ein Fehler kann aufgrund einer der folgenden Bedingungen auftreten.</span><span class="sxs-lookup"><span data-stu-id="b0da1-110">Failure could occur because of any of the following.</span></span></p>
<ul>
<li><p><span data-ttu-id="b0da1-111">Es gibt keine Autorisierungsregel, die dem Benutzer den Zugriff auf den Computer oder eine bestimmte Sitzungskonfiguration auf dem Remotecomputer erlaubt.</span><span class="sxs-lookup"><span data-stu-id="b0da1-111">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span> <span data-ttu-id="b0da1-112">Die Windows PowerShell Web Access-Sicherheit ist restriktiv. Benutzern muss der Zugriff auf Remotecomputer mithilfe von Autorisierungsregeln explizit gewährt werden.</span><span class="sxs-lookup"><span data-stu-id="b0da1-112">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span> <span data-ttu-id="b0da1-113">Weitere Informationen zum Erstellen von Autorisierungsregeln finden Sie unter <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access</a> in diesem Handbuch.</span><span class="sxs-lookup"><span data-stu-id="b0da1-113">For more information about creating authorization rules, see <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a> in this guide.</span></span></p></li>
<li><p><span data-ttu-id="b0da1-114">Der Benutzer hat keinen autorisierten Zugriff auf den Zielcomputer.</span><span class="sxs-lookup"><span data-stu-id="b0da1-114">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="b0da1-115">Dies wird durch Zugriffssteuerungslisten bestimmt.</span><span class="sxs-lookup"><span data-stu-id="b0da1-115">This is determined by access control lists (ACLs).</span></span> <span data-ttu-id="b0da1-116">Weitere Informationen finden Sie unter „Anmelden bei Windows PowerShell Web Access“ in <a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">Verwenden der webbasierten Windows PowerShell-Konsole</a> oder im <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">Windows PowerShell-Teamblog</a>.</span><span class="sxs-lookup"><span data-stu-id="b0da1-116">For more information, see “Signing in to Windows PowerShell Web Access” in <a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">Use the Web-based Windows PowerShell Console</a>, or the <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">Windows PowerShell Team Blog</a>.</span></span></p>
<ul>
<li><p><span data-ttu-id="b0da1-117">Die Windows PowerShell-Remoteverwaltung ist auf dem Zielcomputer möglicherweise nicht aktiviert.</span><span class="sxs-lookup"><span data-stu-id="b0da1-117">Windows PowerShell remote management might not be enabled on the destination computer.</span></span> <span data-ttu-id="b0da1-118">Stellen Sie sicher, dass dieses Feature auf dem Computer aktiviert ist, mit dem der Benutzer eine Verbindung herstellen möchte.</span><span class="sxs-lookup"><span data-stu-id="b0da1-118">Verify that it is enabled on the computer to which the user is trying to connect.</span></span> <span data-ttu-id="b0da1-119">Weitere Informationen finden Sie unter „So konfigurieren Sie den Computer für Remoting“ im Abschnitt <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a> der Windows PowerShell-Hilfethemen.</span><span class="sxs-lookup"><span data-stu-id="b0da1-119">For more information, see “How to Configure Your Computer for Remoting” in <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a> in the Windows PowerShell About Help Topics.</span></span></p></li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b0da1-120">Wenn Benutzer versuchen, sich in einem Internet Explorer-Fenster bei Windows PowerShell Web Access anzumelden, wird die Seite <strong>Interner Serverfehler</strong> angezeigt, oder der Internet Explorer reagiert nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="b0da1-120">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an <strong>Internal Server Error</strong> page, or Internet Explorer stops responding.</span></span> <span data-ttu-id="b0da1-121">Dieses Problem tritt speziell in Internet Explorer auf.</span><span class="sxs-lookup"><span data-stu-id="b0da1-121">This issue is specific to Internet Explorer.</span></span></p></td>
<td><p><span data-ttu-id="b0da1-122">Dies kann bei Benutzern der Fall sein, die sich mit einem Domänennamen angemeldet haben, der chinesische Zeichen enthält, oder wenn der Gatewayservername mindestens ein chinesisches Zeichen aufweist.</span><span class="sxs-lookup"><span data-stu-id="b0da1-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span> <span data-ttu-id="b0da1-123">Benutzer können dieses Problem umgehen, indem sie <a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">Internet Explorer 10 installieren und ausführen</a> und dann die folgenden Schritte ausführen.</span><span class="sxs-lookup"><span data-stu-id="b0da1-123">To work around this issue, the user should <a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">install and run Internet Explorer 10</a>, and then perform the following steps.</span></span></p>
<ol>
<li><p><span data-ttu-id="b0da1-124">Ändern Sie für Internet Explorer die Einstellung <strong>Dokumentmodus</strong> in <strong>IE10-Standards</strong>.</span><span class="sxs-lookup"><span data-stu-id="b0da1-124">Change the Internet Explorer <strong>Document Mode</strong> setting to <strong>IE10 standards</strong>.</span></span></p>
<ol>
<li><p><span data-ttu-id="b0da1-125">Drücken Sie die Taste <strong>F12</strong>, um die Konsole mit den Entwicklertools zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="b0da1-125">Press <strong>F12</strong> to open the Developer Tools console.</span></span></p></li>
<li><p><span data-ttu-id="b0da1-126">Klicken Sie in Internet Explorer 10 auf <strong>Browsermodus</strong>, und wählen Sie die Option <strong>Internet Explorer 10</strong> aus.</span><span class="sxs-lookup"><span data-stu-id="b0da1-126">In Internet Explorer 10, click <strong>Browser Mode</strong>, and then select <strong>Internet Explorer 10</strong>.</span></span></p></li>
<li><p><span data-ttu-id="b0da1-127">Klicken Sie auf <strong>Dokumentmodus</strong> und dann auf <strong>IE10-Standards</strong>.</span><span class="sxs-lookup"><span data-stu-id="b0da1-127">Click <strong>Document Mode</strong>, and then click <strong>IE10 standards</strong>.</span></span></p></li>
<li><p><span data-ttu-id="b0da1-128">Drücken Sie die Taste <strong>F12</strong> erneut, um die Konsole mit den Entwicklertools zu schließen.</span><span class="sxs-lookup"><span data-stu-id="b0da1-128">Press <strong>F12</strong> again to close the Developer Tools console.</span></span></p></li>
</ol></li>
<li><p><span data-ttu-id="b0da1-129">Deaktivieren Sie die automatische Proxykonfiguration.</span><span class="sxs-lookup"><span data-stu-id="b0da1-129">Disable automatic proxy configuration.</span></span></p>
<ol>
<li><p><span data-ttu-id="b0da1-130">Klicken Sie in Internet Explorer 10 auf <strong>Extras</strong> und dann auf <strong>Internetoptionen</strong>.</span><span class="sxs-lookup"><span data-stu-id="b0da1-130">In Internet Explorer 10, click <strong>Tools</strong>, and then click <strong>Internet Options</strong>.</span></span></p></li>
<li><p><span data-ttu-id="b0da1-131">Klicken Sie im Dialogfeld <strong>Internetoptionen</strong> auf der Registerkarte <strong>Verbindungen</strong> auf <strong>LAN-Einstellungen</strong>.</span><span class="sxs-lookup"><span data-stu-id="b0da1-131">In the <strong>Internet Options</strong> dialog box, on the <strong>Connections</strong> tab, click <strong>LAN settings</strong>.</span></span></p></li>
<li><p><span data-ttu-id="b0da1-132">Deaktivieren Sie das Kontrollkästchen <strong>Automatische Suche der Einstellungen</strong>.</span><span class="sxs-lookup"><span data-stu-id="b0da1-132">Clear the <strong>Automatically detect settings</strong> check box.</span></span> <span data-ttu-id="b0da1-133">Klicken Sie auf <strong>OK</strong> und dann erneut auf <strong>OK</strong>, um das Dialogfeld <strong>Internetoptionen</strong> zu schließen.</span><span class="sxs-lookup"><span data-stu-id="b0da1-133">Click <strong>OK</strong>, and then click <strong>OK</strong> again to close the <strong>Internet Options</strong> dialog box.</span></span></p></li>
</ol></li>
</ol></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b0da1-134">Es kann keine Verbindung mit einem Remotecomputer in einer Arbeitsgruppe hergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="b0da1-134">Cannot connect to a remote workgroup computer</span></span></p></td>
<td><p><span data-ttu-id="b0da1-135">Wenn der Zielcomputer Mitglied einer Arbeitsgruppe ist, können Sie die folgende Syntax verwenden, um Ihren Benutzernamen anzugeben und sich am Computer anzumelden: &lt;<em>Name der Arbeitsgruppel</em>&gt;\&lt;<em>Benutzername</em>&gt;</span><span class="sxs-lookup"><span data-stu-id="b0da1-135">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: &lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b0da1-136">Die Verwaltungstools des Webservers (IIS) sind nicht verfügbar, obwohl die Rolle installiert wurde.</span><span class="sxs-lookup"><span data-stu-id="b0da1-136">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span></p></td>
<td><p><span data-ttu-id="b0da1-137">Bei der Installation von Windows PowerShell Web Access mit dem <span class="code">Install-WindowsFeature</span>-Cmdlet werden die Verwaltungstools nur installiert, wenn der <span class="code">IncludeManagementTools</span>-Parameter zum Cmdlet hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="b0da1-137">If you installed Windows PowerShell Web Access by using the <span class="code">Install-WindowsFeature</span> cmdlet, management tools are not installed unless the <span class="code">IncludeManagementTools</span> parameter is added to the cmdlet.</span></span> <span data-ttu-id="b0da1-138">Ein Beispiel finden Sie in diesem Thema unter „So installieren Sie Windows PowerShell Web Access mithilfe von Windows PowerShell-Cmdlets“ in <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Installieren und Verwenden von Windows PowerShell Web Access</a>.</span><span class="sxs-lookup"><span data-stu-id="b0da1-138">For an example, see “To install Windows PowerShell Web Access by using Windows PowerShell cmdlets” in <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Install and Use Windows PowerShell Web Access</a>.</span></span> <span data-ttu-id="b0da1-139">Sie können die IIS-Manager-Konsole und andere benötigte IIS-Verwaltungstools hinzufügen, indem Sie die Tools in einer Sitzung des Assistenten zum Hinzufügen von Rollen und Features auswählen, die auf den Gatewayserver ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="b0da1-139">You can add the IIS Manager console and other IIS management tools that you need by selecting the tools in an Add Roles and Features Wizard session that is targeted at the gateway server.</span></span> <span data-ttu-id="b0da1-140">Der Assistent zum Hinzufügen von Rollen und Features wird über den Server-Manager geöffnet.</span><span class="sxs-lookup"><span data-stu-id="b0da1-140">The Add Roles and Features Wizard is opened from within Server Manager.</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b0da1-141">Auf die Windows PowerShell Web Access-Website kann nicht zugegriffen werden</span><span class="sxs-lookup"><span data-stu-id="b0da1-141">The Windows PowerShell Web Access website is not accessible</span></span></p></td>
<td><p><span data-ttu-id="b0da1-142">Wenn die verstärkte Sicherheitskonfiguration in Internet Explorer (IE ESC) aktiviert ist, können Sie die Windows PowerShell Web Access-Website der Liste der vertrauenswürdigen Websites hinzufügen oder IE ESC deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="b0da1-142">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites, or disable IE ESC.</span></span> <span data-ttu-id="b0da1-143">Sie können IE ESC auf der Kachel <strong>Eigenschaften</strong> der Seite <strong>Lokaler Server</strong> im Server-Manager deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="b0da1-143">You can disable IE ESC in the <strong>Properties</strong> tile on the <strong>Local Server</strong> page in Server Manager.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b0da1-144">Die folgende Fehlermeldung wird beim Versuch angezeigt, eine Verbindung herstellen, wenn der Gatewayserver der Zielcomputer ist und sich auch in einer Arbeitsgruppe befindet: <strong>Fehler bei der Autorisierung. Überprüfen Sie, ob Sie autorisiert sind, eine Verbindung mit dem Zielcomputer herzustellen.</strong></span><span class="sxs-lookup"><span data-stu-id="b0da1-144">The following error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup: <strong>An authorization failure occurred. Verify that you are authorized to connect to the destination computer.</strong></span></span></p></td>
<td><p><span data-ttu-id="b0da1-145">Wenn der Gatewayserver auch der Zielserver ist und sich in einer Arbeitsgruppe befindet, geben Sie den Benutzernamen, den Computernamen und den Benutzergruppennamen wie in der folgenden Tabelle dargestellt an.</span><span class="sxs-lookup"><span data-stu-id="b0da1-145">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name as shown in the following table.</span></span> <span data-ttu-id="b0da1-146">Verwenden Sie nicht nur einen Punkt (.) als Computernamen.</span><span class="sxs-lookup"><span data-stu-id="b0da1-146">Do not use a dot (.) by itself to represent the computer name.</span></span></p>
<div>
<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="b0da1-147">Szenario</span><span class="sxs-lookup"><span data-stu-id="b0da1-147">Scenario</span></span></p></th>
<th><p><span data-ttu-id="b0da1-148">UserName-Parameter</span><span class="sxs-lookup"><span data-stu-id="b0da1-148">UserName Parameter</span></span></p></th>
<th><p><span data-ttu-id="b0da1-149">UserGroup-Parameter</span><span class="sxs-lookup"><span data-stu-id="b0da1-149">UserGroup Parameter</span></span></p></th>
<th><p><span data-ttu-id="b0da1-150">ComputerName-Parameter</span><span class="sxs-lookup"><span data-stu-id="b0da1-150">ComputerName Parameter</span></span></p></th>
<th><p><span data-ttu-id="b0da1-151">ComputerGroup-Parameter</span><span class="sxs-lookup"><span data-stu-id="b0da1-151">ComputerGroup Parameter</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="b0da1-152">Gatewayserver befindet sich in Domäne</span><span class="sxs-lookup"><span data-stu-id="b0da1-152">Gateway server is in a domain</span></span></p></td>
<td><p><span data-ttu-id="b0da1-153"><em>Servername</em>\<em>Benutzername</em>, Localhost\<em>Benutzername</em> oder .\<em>Benutzername</em></span><span class="sxs-lookup"><span data-stu-id="b0da1-153"><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em>, or .\<em>user_name</em></span></span></p></td>
<td><p><span data-ttu-id="b0da1-154"><em>Servername</em>\<em>Benutzergruppe</em>, Localhost\<em>Benutzergruppe</em> oder .\<em>Benutzergruppe</em></span><span class="sxs-lookup"><span data-stu-id="b0da1-154"><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em>, or .\<em>user_group</em></span></span></p></td>
<td><p><span data-ttu-id="b0da1-155">Vollqualifizierter Name des Gatewayservers oder Localhost</span><span class="sxs-lookup"><span data-stu-id="b0da1-155">Fully qualified name of gateway server, or Localhost</span></span></p></td>
<td><p><span data-ttu-id="b0da1-156"><em>Servername</em>\<em>Computergruppe</em>, Localhost\<em>Computergruppe</em> oder .\<em>Computergruppe</em></span><span class="sxs-lookup"><span data-stu-id="b0da1-156"><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em>, or .\<em>computer_group</em></span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b0da1-157">Gatewayserver befindet sich in Arbeitsgruppe</span><span class="sxs-lookup"><span data-stu-id="b0da1-157">Gateway server is in a workgroup</span></span></p></td>
<td><p><span data-ttu-id="b0da1-158"><em>Servername</em>\<em>Benutzername</em>, Localhost\<em>Benutzername</em> oder .\<em>Benutzername</em></span><span class="sxs-lookup"><span data-stu-id="b0da1-158"><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em>, or .\<em>user_name</em></span></span></p></td>
<td><p><span data-ttu-id="b0da1-159"><em>Servername</em>\<em>Benutzergruppe</em>, Localhost\<em>Benutzergruppe</em> oder .\<em>Benutzergruppe</em></span><span class="sxs-lookup"><span data-stu-id="b0da1-159"><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em> or .\<em>user_group</em></span></span></p></td>
<td><p><span data-ttu-id="b0da1-160">Servername</span><span class="sxs-lookup"><span data-stu-id="b0da1-160">Server name</span></span></p></td>
<td><p><span data-ttu-id="b0da1-161"><em>Servername</em>\<em>Computergruppe</em>, Localhost\<em>Computergruppe</em> oder .\<em>Computergruppe</em></span><span class="sxs-lookup"><span data-stu-id="b0da1-161"><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em> or .\<em>computer_group</em></span></span></p></td>
</tr>
</tbody>
</table>
</div>
<p><span data-ttu-id="b0da1-162">Melden Sie sich bei einem Gatewayserver als Zielcomputer an, indem Sie Anmeldeinformationen in einem der folgenden Formate verwenden.</span><span class="sxs-lookup"><span data-stu-id="b0da1-162">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span></p>
<ul>
<li><p><span data-ttu-id="b0da1-163"><em>Servername</em>\<em>Benutzername</em></span><span class="sxs-lookup"><span data-stu-id="b0da1-163"><em>Server_name</em>\<em>user_name</em></span></span></p></li>
<li><p><span data-ttu-id="b0da1-164">Localhost\<em>Benutzername</em></span><span class="sxs-lookup"><span data-stu-id="b0da1-164">Localhost\<em>user_name</em></span></span></p></li>
<li><p><span data-ttu-id="b0da1-165">.\<em>Benutzername</em></span><span class="sxs-lookup"><span data-stu-id="b0da1-165">.\<em>user_name</em></span></span></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b0da1-166">Eine Sicherheits-ID wird in einer Autorisierungsregel anstelle der folgenden Syntax angezeigt: <em>Benutzername</em>/<em>Computername</em> </span><span class="sxs-lookup"><span data-stu-id="b0da1-166">A security identifier (SID) is displayed in an authorization rule instead of the syntax <em>user_name</em>/<em>computer_name</em> </span></span></p></td>
<td><p><span data-ttu-id="b0da1-167">Entweder ist die Regel nicht mehr gültig, oder bei der Active Directory-Domänendienste-Abfrage ist ein Fehler aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="b0da1-167">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span> <span data-ttu-id="b0da1-168">Eine Autorisierungsregel ist normalerweise nicht in Fällen gültig, in denen der Gatewayserver zuerst einer Arbeitsgruppe angehörte, dann jedoch einer Domäne beigetreten ist.</span><span class="sxs-lookup"><span data-stu-id="b0da1-168">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b0da1-169">Anmeldung an einem Zielcomputer, der in Autorisierungsregeln als IPv6-Adresse mit einer Domäne angegeben wurde, nicht möglich</span><span class="sxs-lookup"><span data-stu-id="b0da1-169">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span></p></td>
<td><p><span data-ttu-id="b0da1-170">Autorisierungsregeln unterstützen keine IPv6-Adresse in Form eines Domänennamens.</span><span class="sxs-lookup"><span data-stu-id="b0da1-170">Authorization rules do not support an IPv6 address in form of a domain name.</span></span> <span data-ttu-id="b0da1-171">Verwenden Sie zum Angeben eines Zielcomputers mithilfe einer IPv6-Adresse die ursprüngliche IPv6-Adresse (mit Doppelpunkten) in der Autorisierungsregel.</span><span class="sxs-lookup"><span data-stu-id="b0da1-171">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span> <span data-ttu-id="b0da1-172">Sowohl domänenbezogene als auch numerische IPv6-Adressen (mit Doppelpunkten) werden auf der Anmeldeseite von Windows PowerShell Web Access als Zielcomputername unterstützt. Dies gilt jedoch nicht für Autorisierungsregeln.</span><span class="sxs-lookup"><span data-stu-id="b0da1-172">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span> <span data-ttu-id="b0da1-173">Weitere Informationen zu IPv6-Adressen finden Sie unter <a href="https://technet.microsoft.com/library/cc781672.aspx">Funktionsweise von IPv6</a>.</span><span class="sxs-lookup"><span data-stu-id="b0da1-173">For more information about IPv6 addresses, see <a href="https://technet.microsoft.com/library/cc781672.aspx">How IPv6 Works</a>.</span></span></p></td>
</tr>
</tbody>
</table><span data-ttu-id="b0da1-174">

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Siehe auch</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="b0da1-174">

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="b0da1-175">[Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[Verwendung der webbasierten Windows PowerShell-Konsole](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about_Remote_Requirements](https://technet.microsoft.com/library/dd315349.aspx)</span><span class="sxs-lookup"><span data-stu-id="b0da1-175">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about_Remote_Requirements](https://technet.microsoft.com/library/dd315349.aspx)</span></span>

<span data-ttu-id="b0da1-176"><span>Show:</span> Inherited Protected</span><span class="sxs-lookup"><span data-stu-id="b0da1-176"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="b0da1-177"><span class="stdr-votetitle">War diese Seite hilfreich?</span></span><span class="sxs-lookup"><span data-stu-id="b0da1-177"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="b0da1-178">Ja Nein</span><span class="sxs-lookup"><span data-stu-id="b0da1-178">Yes No</span></span>

<span data-ttu-id="b0da1-179">Zusätzliches Feedback?</span><span class="sxs-lookup"><span data-stu-id="b0da1-179">Additional feedback?</span></span>

<span data-ttu-id="b0da1-180"><span class="stdr-count"><span class="stdr-charcnt">1.500</span> verbleibende Zeichen</span> Senden Diesen Schritt überspringen</span><span class="sxs-lookup"><span data-stu-id="b0da1-180"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="b0da1-181"><span class="stdr-thankyou">Vielen Dank!</span></span><span class="sxs-lookup"><span data-stu-id="b0da1-181"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="b0da1-182"><span class="stdr-appreciate">Wir schätzen Ihr Feedback.</span></span><span class="sxs-lookup"><span data-stu-id="b0da1-182"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="b0da1-183">Profil verwalten</span><span class="sxs-lookup"><span data-stu-id="b0da1-183">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="b0da1-184"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Feedback zur Website</a> Feedback zur Website</span><span class="sxs-lookup"><span data-stu-id="b0da1-184"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="b0da1-185"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="b0da1-185"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="b0da1-186">Teilen Sie uns Ihre Erfahrungen mit.</span><span class="sxs-lookup"><span data-stu-id="b0da1-186">Tell us about your experience...</span></span>

<span data-ttu-id="b0da1-187">Wurde die Seite schnell geladen?</span><span class="sxs-lookup"><span data-stu-id="b0da1-187">Did the page load quickly?</span></span>

<span data-ttu-id="b0da1-188"><span> Ja<span> </span></span> <span> Nein<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="b0da1-188"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="b0da1-189">Gefällt Ihnen das Design der Seite?</span><span class="sxs-lookup"><span data-stu-id="b0da1-189">Do you like the page design?</span></span>

<span data-ttu-id="b0da1-190"><span> Ja<span> </span></span> <span> Nein<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="b0da1-190"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="b0da1-191">Erzählen Sie uns mehr</span><span class="sxs-lookup"><span data-stu-id="b0da1-191">Tell us more</span></span>

-   [<span data-ttu-id="b0da1-192">Flash-Newsletter</span><span class="sxs-lookup"><span data-stu-id="b0da1-192">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="b0da1-193">So erreichen Sie uns</span><span class="sxs-lookup"><span data-stu-id="b0da1-193">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="b0da1-194">Datenschutzbestimmungen</span><span class="sxs-lookup"><span data-stu-id="b0da1-194">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="b0da1-195">Nutzungsbedingungen</span><span class="sxs-lookup"><span data-stu-id="b0da1-195">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="b0da1-196">Marken</span><span class="sxs-lookup"><span data-stu-id="b0da1-196">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="b0da1-197">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="b0da1-197">© 2016 Microsoft</span></span>

<span data-ttu-id="b0da1-198">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="b0da1-198">© 2016 Microsoft</span></span>

<span data-ttu-id="b0da1-199">Die Lizenz für Drittanbieterskripts oder Code, die mit dieser Website verlinkt oder über Verweise verbunden sind, wird Ihnen von den Codeeigentümern erteilt, nicht von Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b0da1-199">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="b0da1-200">Die ASP.NET Ajax CDN-Nutzungsbedingungen finden Sie unter http://www.asp.net/ajaxlibrary/CDN.ashx.</span><span class="sxs-lookup"><span data-stu-id="b0da1-200">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

