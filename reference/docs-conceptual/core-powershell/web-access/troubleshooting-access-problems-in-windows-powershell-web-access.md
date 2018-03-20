---
ms.date: 2017-08-23
keywords: powershell,cmdlet
title: Behandeln von Zugriffsproblemen in Windows PowerShell Web Access
ms.openlocfilehash: 6e51df3f4c6ac196c855ad918a91394d02c7d75e
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="ada46-103">Behandeln von Zugriffsproblemen in Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="ada46-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="ada46-104">Aktualisiert: 24. Juni 2013 (überarbeitet: 23. August 2017)</span><span class="sxs-lookup"><span data-stu-id="ada46-104">Updated: June 24, 2013 (revised August 23, 2017)</span></span>

<span data-ttu-id="ada46-105">Gilt für: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="ada46-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="ada46-106">Im folgenden Abschnitt sind einige allgemeine Probleme aufgeführt, die auftreten können, wenn versucht wird, über Windows PowerShell Web Access eine Verbindung mit einem Remotecomputer herzustellen. Außerdem enthält die Tabelle Vorschläge zur Behebung der Probleme.</span><span class="sxs-lookup"><span data-stu-id="ada46-106">The following sections identify some common problems when attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

## <a name="sign-in-failure"></a><span data-ttu-id="ada46-107">Fehler bei der Anmeldung.</span><span class="sxs-lookup"><span data-stu-id="ada46-107">Sign-in failure</span></span>

<span data-ttu-id="ada46-108">Ein Fehler kann aufgrund einer der folgenden Bedingungen auftreten.</span><span class="sxs-lookup"><span data-stu-id="ada46-108">Failure could occur because of any of the following.</span></span>

- <span data-ttu-id="ada46-109">Es gibt keine Autorisierungsregel, die dem Benutzer den Zugriff auf den Computer oder eine bestimmte Sitzungskonfiguration auf dem Remotecomputer erlaubt.</span><span class="sxs-lookup"><span data-stu-id="ada46-109">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span>

  <span data-ttu-id="ada46-110">Die Windows PowerShell Web Access-Sicherheit ist restriktiv. Benutzern muss der Zugriff auf Remotecomputer mithilfe von Autorisierungsregeln explizit gewährt werden.</span><span class="sxs-lookup"><span data-stu-id="ada46-110">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span>

  <span data-ttu-id="ada46-111">Weitere Informationen zum Erstellen von Autorisierungsregeln finden Sie unter [Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="ada46-111">For more information about creating authorization rules, see [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span></span>

- <span data-ttu-id="ada46-112">Der Benutzer hat keinen autorisierten Zugriff auf den Zielcomputer.</span><span class="sxs-lookup"><span data-stu-id="ada46-112">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="ada46-113">Dies wird durch Zugriffssteuerungslisten bestimmt.</span><span class="sxs-lookup"><span data-stu-id="ada46-113">This is determined by access control lists (ACLs).</span></span>

  <span data-ttu-id="ada46-114">Weitere Informationen finden Sie unter [Anmelden bei Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access) oder im Windows PowerShell-Teamblog.</span><span class="sxs-lookup"><span data-stu-id="ada46-114">For more information, see [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), or the Windows PowerShell Team Blog.</span></span>

- <span data-ttu-id="ada46-115">Die Windows PowerShell-Remoteverwaltung ist auf dem Zielcomputer möglicherweise nicht aktiviert.</span><span class="sxs-lookup"><span data-stu-id="ada46-115">Windows PowerShell remote management might not be enabled on the destination computer.</span></span>

  <span data-ttu-id="ada46-116">Stellen Sie sicher, dass die Remoteverwaltung auf dem Computer aktiviert ist, mit dem der Benutzer eine Verbindung herstellen möchte.</span><span class="sxs-lookup"><span data-stu-id="ada46-116">Verify remote management is enabled on the computer to which the user is trying to connect.</span></span>

  <span data-ttu-id="ada46-117">Weitere Informationen finden Sie unter [How to Configure Your Computer for Remoting (Vorgehensweise: Konfigurieren Ihres Computers für das Remoting)](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span><span class="sxs-lookup"><span data-stu-id="ada46-117">For more information, see [How to Configure Your Computer for Remoting](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span></span>

## <a name="internal-server-error"></a><span data-ttu-id="ada46-118">Interner Serverfehler.</span><span class="sxs-lookup"><span data-stu-id="ada46-118">Internal Server Error</span></span>

<span data-ttu-id="ada46-119">Wenn Benutzer versuchen, sich in einem Internet Explorer-Fenster bei Windows PowerShell Web Access anzumelden, wird die Seite **Interner Serverfehler** angezeigt, oder der *Internet Explorer* reagiert nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="ada46-119">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an **Internal Server Error** page, or *Internet Explorer* stops responding.</span></span>

<span data-ttu-id="ada46-120">Dieses Problem tritt speziell in Internet Explorer auf.</span><span class="sxs-lookup"><span data-stu-id="ada46-120">This issue is specific to Internet Explorer.</span></span>

### <a name="possible-cause"></a><span data-ttu-id="ada46-121">Mögliche Ursache</span><span class="sxs-lookup"><span data-stu-id="ada46-121">Possible cause</span></span>

<span data-ttu-id="ada46-122">Dies kann bei Benutzern der Fall sein, die sich mit einem Domänennamen angemeldet haben, der chinesische Zeichen enthält, oder wenn der Gatewayservername mindestens ein chinesisches Zeichen aufweist.</span><span class="sxs-lookup"><span data-stu-id="ada46-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span>

#### <a name="workaround"></a><span data-ttu-id="ada46-123">Problemumgehung</span><span class="sxs-lookup"><span data-stu-id="ada46-123">Workaround</span></span>

1. [<span data-ttu-id="ada46-124">Install and run Internet Explorer 10 (Installieren und Ausführen von Internet Explorer 10)</span><span class="sxs-lookup"><span data-stu-id="ada46-124">Install and run Internet Explorer 10</span></span>](http://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. <span data-ttu-id="ada46-125">Ändern Sie für Internet Explorer die Einstellung **Dokumentmodus** in *IE10-Standards*.</span><span class="sxs-lookup"><span data-stu-id="ada46-125">Change Internet Explorer **Document Mode** setting to *IE10* standards.</span></span>
   1. <span data-ttu-id="ada46-126">Drücken Sie die Taste **F12**, um die Konsole mit den Entwicklertools zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="ada46-126">Press **F12** to open the Developer Tools console</span></span>
   1. <span data-ttu-id="ada46-127">Klicken Sie in Internet Explorer 10 auf **Browsermodus**, und wählen Sie die Option *Internet Explorer 10* aus.</span><span class="sxs-lookup"><span data-stu-id="ada46-127">In Internet Explorer 10, click **Browser Mode**, and then select *Internet Explorer 10*.</span></span>
   1. <span data-ttu-id="ada46-128">Klicken Sie auf **Dokumentmodus** und dann auf *IE10-Standards*.</span><span class="sxs-lookup"><span data-stu-id="ada46-128">Click **Document Mode**, and then click *IE10* standards.</span></span>
   1. <span data-ttu-id="ada46-129">Drücken Sie die Taste **F12** erneut, um die Konsole mit den Entwicklertools zu schließen.</span><span class="sxs-lookup"><span data-stu-id="ada46-129">Press **F12** again to close the Developer Tools console.</span></span>
1. <span data-ttu-id="ada46-130">Deaktivieren Sie die automatische Proxykonfiguration in Internet Explorer 10.</span><span class="sxs-lookup"><span data-stu-id="ada46-130">Disable automatic proxy configuration in Internet Explorer 10.</span></span>
   1. <span data-ttu-id="ada46-131">Klicken Sie auf **Tools**und dann auf **Internetoptionen**.</span><span class="sxs-lookup"><span data-stu-id="ada46-131">Click **Tools**, and then click **Internet Options**.</span></span>
   1. <span data-ttu-id="ada46-132">Klicken Sie im Dialogfeld **Internetoptionen** auf der Registerkarte **Verbindungen** auf **LAN-Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="ada46-132">In the **Internet Options** dialog box, on the **Connections** tab, click **LAN settings**.</span></span>
   1. <span data-ttu-id="ada46-133">Deaktivieren Sie das Kontrollkästchen **Automatische Suche der Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="ada46-133">Clear the **Automatically detect settings** check box.</span></span> <span data-ttu-id="ada46-134">Klicken Sie auf **OK** und dann erneut auf **OK**, um das Dialogfeld *Internetoptionen* zu schließen.</span><span class="sxs-lookup"><span data-stu-id="ada46-134">Click **OK**, and then click **OK** again to close the *Internet Options* dialog box.</span></span>

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a><span data-ttu-id="ada46-135">Es kann keine Verbindung mit einem Remotecomputer in einer Arbeitsgruppe hergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="ada46-135">Cannot connect to a remote workgroup computer</span></span>

<span data-ttu-id="ada46-136">Wenn der Zielcomputer Mitglied einer Arbeitsgruppe ist, können Sie die folgende Syntax verwenden, um den Benutzernamen anzugeben und sich am Computer anzumelden: `<workgroup_name>\<user_name>`.</span><span class="sxs-lookup"><span data-stu-id="ada46-136">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: `<workgroup_name>\<user_name>`</span></span>

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a><span data-ttu-id="ada46-137">Die Verwaltungstools des Webservers (IIS) sind nicht verfügbar, obwohl die Rolle installiert wurde.</span><span class="sxs-lookup"><span data-stu-id="ada46-137">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span>

<span data-ttu-id="ada46-138">Wenn Sie Windows PowerShell Web Access mit dem Cmdlet `Install-WindowsFeature` installiert haben, werden die Verwaltungstools nur installiert, wenn dem Cmdlet der Parameter `-IncludeManagementTools` hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="ada46-138">If you installed Windows PowerShell Web Access by using the `Install-WindowsFeature` cmdlet, management tools are not installed unless the `-IncludeManagementTools` parameter is added to the cmdlet.</span></span>

<span data-ttu-id="ada46-139">Ein Beispiel finden Sie unter [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets (Installieren von Windows PowerShell Web Access mithilfe von Windows PowerShell-Cmdlets)](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="ada46-139">For an example, see [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span></span>

<span data-ttu-id="ada46-140">Sie können die IIS-Manager-Konsole und andere benötigte IIS-Verwaltungstools hinzufügen, indem Sie die Tools in einer Sitzung des **Assistenten zum Hinzufügen von Rollen und Features** auswählen, die auf den Gatewayserver ausgerichtet sind.</span><span class="sxs-lookup"><span data-stu-id="ada46-140">You can add the IIS Manager console, and other IIS management tools that you need, by selecting the tools in an **Add Roles and Features Wizard** session that is targeted at the gateway server.</span></span>
<span data-ttu-id="ada46-141">Der Assistent zum Hinzufügen von Rollen und Features wird über den Server-Manager geöffnet.</span><span class="sxs-lookup"><span data-stu-id="ada46-141">The Add Roles and Features Wizard is opened from within Server Manager.</span></span>

## <a name="windows-powershell-web-access-website-is-not-accessible"></a><span data-ttu-id="ada46-142">Auf die Windows PowerShell Web Access-Website kann nicht zugegriffen werden</span><span class="sxs-lookup"><span data-stu-id="ada46-142">Windows PowerShell Web Access website is not accessible</span></span>

<span data-ttu-id="ada46-143">Wenn die verstärkte Sicherheitskonfiguration in Internet Explorer (IE ESC) aktiviert ist, können Sie die Windows PowerShell Web Access-Website der Liste der vertrauenswürdigen Websites hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ada46-143">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites.</span></span>

<span data-ttu-id="ada46-144">Ein wenig empfohlener Ansatz ist wegen Sicherheitsrisiken das Deaktivieren von IE ESC.</span><span class="sxs-lookup"><span data-stu-id="ada46-144">A less recommended approach, due to security risks, is to disable IE ESC.</span></span>
<span data-ttu-id="ada46-145">Sie können IE ESC auf der Kachel „Eigenschaften“ der Seite „Lokaler Server“ im Server-Manager deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="ada46-145">You can disable IE ESC in the Properties tile on the Local Server page in Server Manager.</span></span>

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a><span data-ttu-id="ada46-146">Fehler bei der Autorisierung.</span><span class="sxs-lookup"><span data-stu-id="ada46-146">An authorization failure occurred.</span></span> <span data-ttu-id="ada46-147">Stellen Sie sicher, dass Sie zum Herstellen einer Verbindung mit dem Zielcomputer autorisiert sind.</span><span class="sxs-lookup"><span data-stu-id="ada46-147">Verify that you are authorized to connect to the destination computer.</span></span>

<span data-ttu-id="ada46-148">Die obenstehende Fehlermeldung wird beim Versuch angezeigt, eine Verbindung herzustellen, wenn der Gatewayserver der Zielcomputer ist und sich auch in einer Arbeitsgruppe befindet.</span><span class="sxs-lookup"><span data-stu-id="ada46-148">The above error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup.</span></span>

<span data-ttu-id="ada46-149">Wenn der Gatewayserver auch der Zielserver ist und sich in einer Arbeitsgruppe befindet, geben Sie den Benutzernamen, den Computernamen und den Benutzergruppennamen an.</span><span class="sxs-lookup"><span data-stu-id="ada46-149">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name.</span></span>
<span data-ttu-id="ada46-150">Verwenden Sie nicht nur einen Punkt (.) als Computernamen.</span><span class="sxs-lookup"><span data-stu-id="ada46-150">Do not use a dot (.) by itself to represent the computer name.</span></span>

### <a name="scenarios-and-proper-values"></a><span data-ttu-id="ada46-151">Szenarios und richtige Werte</span><span class="sxs-lookup"><span data-stu-id="ada46-151">Scenarios and proper values</span></span>

#### <a name="all-cases"></a><span data-ttu-id="ada46-152">Alle Fälle</span><span class="sxs-lookup"><span data-stu-id="ada46-152">All cases</span></span>

<span data-ttu-id="ada46-153">Parameter</span><span class="sxs-lookup"><span data-stu-id="ada46-153">Parameter</span></span> | <span data-ttu-id="ada46-154">Value</span><span class="sxs-lookup"><span data-stu-id="ada46-154">Value</span></span>
-- | --
<span data-ttu-id="ada46-155">UserName</span><span class="sxs-lookup"><span data-stu-id="ada46-155">UserName</span></span> | <span data-ttu-id="ada46-156">Server\_name\\user\_name</span><span class="sxs-lookup"><span data-stu-id="ada46-156">Server\_name\\user\_name</span></span><br/><span data-ttu-id="ada46-157">Localhost\\user\_name</span><span class="sxs-lookup"><span data-stu-id="ada46-157">Localhost\\user\_name</span></span><br/><span data-ttu-id="ada46-158">.\\user\_name</span><span class="sxs-lookup"><span data-stu-id="ada46-158">.\\user\_name</span></span>
<span data-ttu-id="ada46-159">UserGroup</span><span class="sxs-lookup"><span data-stu-id="ada46-159">UserGroup</span></span> | <span data-ttu-id="ada46-160">Server\_name\\user\_group</span><span class="sxs-lookup"><span data-stu-id="ada46-160">Server\_name\\user\_group</span></span><br/><span data-ttu-id="ada46-161">Localhost\\user\_group</span><span class="sxs-lookup"><span data-stu-id="ada46-161">Localhost\\user\_group</span></span><br/><span data-ttu-id="ada46-162">.\\user\_group</span><span class="sxs-lookup"><span data-stu-id="ada46-162">.\\user\_group</span></span>
<span data-ttu-id="ada46-163">ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="ada46-163">ComputerGroup</span></span> | <span data-ttu-id="ada46-164">Server\_name\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="ada46-164">Server\_name\\computer\_group</span></span><br/><span data-ttu-id="ada46-165">Localhost\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="ada46-165">Localhost\\computer\_group</span></span><br/><span data-ttu-id="ada46-166">.\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="ada46-166">.\\computer\_group</span></span>

#### <a name="gateway-server-is-in-a-domain"></a><span data-ttu-id="ada46-167">Gatewayserver befindet sich in Domäne</span><span class="sxs-lookup"><span data-stu-id="ada46-167">Gateway server is in a domain</span></span>

<span data-ttu-id="ada46-168">Parameter</span><span class="sxs-lookup"><span data-stu-id="ada46-168">Parameter</span></span> | <span data-ttu-id="ada46-169">Value</span><span class="sxs-lookup"><span data-stu-id="ada46-169">Value</span></span>
-- | --
<span data-ttu-id="ada46-170">ComputerName</span><span class="sxs-lookup"><span data-stu-id="ada46-170">ComputerName</span></span> | <span data-ttu-id="ada46-171">Vollqualifizierter Name des Gatewayservers oder Localhost</span><span class="sxs-lookup"><span data-stu-id="ada46-171">Fully qualified name of gateway server, or Localhost</span></span>

#### <a name="gateway-server-is-in-a-workgroup"></a><span data-ttu-id="ada46-172">Gatewayserver befindet sich in Arbeitsgruppe</span><span class="sxs-lookup"><span data-stu-id="ada46-172">Gateway server is in a workgroup</span></span>

<span data-ttu-id="ada46-173">Parameter</span><span class="sxs-lookup"><span data-stu-id="ada46-173">Parameter</span></span> | <span data-ttu-id="ada46-174">Value</span><span class="sxs-lookup"><span data-stu-id="ada46-174">Value</span></span>
-- | --
<span data-ttu-id="ada46-175">ComputerName</span><span class="sxs-lookup"><span data-stu-id="ada46-175">ComputerName</span></span> | <span data-ttu-id="ada46-176">Servername</span><span class="sxs-lookup"><span data-stu-id="ada46-176">Server name</span></span>

### <a name="gateway-credentials"></a><span data-ttu-id="ada46-177">Gateway-Anmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="ada46-177">Gateway credentials</span></span>

<span data-ttu-id="ada46-178">Melden Sie sich bei einem Gatewayserver als Zielcomputer an, indem Sie Anmeldeinformationen in einem der folgenden Formate verwenden.</span><span class="sxs-lookup"><span data-stu-id="ada46-178">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span>

- <span data-ttu-id="ada46-179">Server\_name\\user\_name</span><span class="sxs-lookup"><span data-stu-id="ada46-179">Server\_name\\user\_name</span></span>
- <span data-ttu-id="ada46-180">Localhost\\user\_name</span><span class="sxs-lookup"><span data-stu-id="ada46-180">Localhost\\user\_name</span></span>
- <span data-ttu-id="ada46-181">.\\user\_name</span><span class="sxs-lookup"><span data-stu-id="ada46-181">.\\user\_name</span></span>

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a><span data-ttu-id="ada46-182">Eine Sicherheits-ID (SID) wird in einer Autorisierungsregel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ada46-182">A security identifier (SID) is displayed in an authorization rule</span></span>

<span data-ttu-id="ada46-183">Eine Sicherheits-ID wird in einer Autorisierungsregel anstelle der Syntax user\_name/computer\_name angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ada46-183">A security identifier (SID) is displayed in an authorization rule instead of the syntax user\_name/computer\_name.</span></span>

<span data-ttu-id="ada46-184">Entweder ist die Regel nicht mehr gültig, oder bei der Active Directory-Domänendienste-Abfrage ist ein Fehler aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="ada46-184">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span>
<span data-ttu-id="ada46-185">Eine Autorisierungsregel ist normalerweise nicht in Fällen gültig, in denen der Gatewayserver zuerst einer Arbeitsgruppe angehörte, dann jedoch einer Domäne beigetreten ist.</span><span class="sxs-lookup"><span data-stu-id="ada46-185">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain</span></span>

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a><span data-ttu-id="ada46-186">Es ist nicht möglich, sich bei einer Regel mit einer IPv6-Adresse mit einer Domäne anzumelden.</span><span class="sxs-lookup"><span data-stu-id="ada46-186">Cannot sign in with rule as an IPv6 address with a domain</span></span>

<span data-ttu-id="ada46-187">Anmeldung an einem Zielcomputer, der in Autorisierungsregeln als IPv6-Adresse mit einer Domäne angegeben wurde, nicht möglich</span><span class="sxs-lookup"><span data-stu-id="ada46-187">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span>

<span data-ttu-id="ada46-188">Autorisierungsregeln unterstützen keine IPv6-Adresse in Form eines Domänennamens.</span><span class="sxs-lookup"><span data-stu-id="ada46-188">Authorization rules do not support an IPv6 address in form of a domain name.</span></span>

<span data-ttu-id="ada46-189">Verwenden Sie zum Angeben eines Zielcomputers mithilfe einer IPv6-Adresse die ursprüngliche IPv6-Adresse (mit Doppelpunkten) in der Autorisierungsregel.</span><span class="sxs-lookup"><span data-stu-id="ada46-189">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span>
<span data-ttu-id="ada46-190">Sowohl domänenbezogene als auch numerische IPv6-Adressen (mit Doppelpunkten) werden auf der Anmeldeseite von Windows PowerShell Web Access als Zielcomputername unterstützt. Dies gilt jedoch nicht für Autorisierungsregeln.</span><span class="sxs-lookup"><span data-stu-id="ada46-190">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span> 

<span data-ttu-id="ada46-191">Weitere Informationen zu IPv6-Adressen finden Sie unter [Funktionsweise von IPv6](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="ada46-191">For more information about IPv6 addresses, see [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="ada46-192">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ada46-192">See Also</span></span>

- <span data-ttu-id="ada46-193">[Authorization Rules and Security Features of Windows PowerShell Web Access (Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access)](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="ada46-193">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span></span>
- <span data-ttu-id="ada46-194">[Use the Web-based Windows PowerShell Console (Verwenden der webbasierten Windows PowerShell-Konsole)](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="ada46-194">[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span></span>
- [<span data-ttu-id="ada46-195">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="ada46-195">about_Remote_Requirements</span></span>](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
