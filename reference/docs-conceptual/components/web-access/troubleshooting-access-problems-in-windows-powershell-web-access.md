---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: Behandeln von Zugriffsproblemen in Windows PowerShell Web Access
ms.openlocfilehash: 818beffaf7df55ae36a154b7b751f9201c5b4299
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75870182"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="7a45b-103">Behandeln von Zugriffsproblemen in Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="7a45b-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="7a45b-104">Aktualisiert: 24. Juni 2013 (überarbeitet: 23. August 2017)</span><span class="sxs-lookup"><span data-stu-id="7a45b-104">Updated: June 24, 2013 (revised August 23, 2017)</span></span>

<span data-ttu-id="7a45b-105">Gilt für: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="7a45b-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="7a45b-106">Im folgenden Abschnitt sind einige allgemeine Probleme aufgeführt, die auftreten können, wenn versucht wird, über Windows PowerShell Web Access eine Verbindung mit einem Remotecomputer herzustellen. Außerdem enthält die Tabelle Vorschläge zur Behebung der Probleme.</span><span class="sxs-lookup"><span data-stu-id="7a45b-106">The following sections identify some common problems when attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

## <a name="sign-in-failure"></a><span data-ttu-id="7a45b-107">Fehler bei der Anmeldung.</span><span class="sxs-lookup"><span data-stu-id="7a45b-107">Sign-in failure</span></span>

<span data-ttu-id="7a45b-108">Ein Fehler kann aufgrund einer der folgenden Bedingungen auftreten.</span><span class="sxs-lookup"><span data-stu-id="7a45b-108">Failure could occur because of any of the following.</span></span>

- <span data-ttu-id="7a45b-109">Es gibt keine Autorisierungsregel, die dem Benutzer den Zugriff auf den Computer oder eine bestimmte Sitzungskonfiguration auf dem Remotecomputer erlaubt.</span><span class="sxs-lookup"><span data-stu-id="7a45b-109">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span>

  <span data-ttu-id="7a45b-110">Die Windows PowerShell Web Access-Sicherheit ist restriktiv. Benutzern muss der Zugriff auf Remotecomputer mithilfe von Autorisierungsregeln explizit gewährt werden.</span><span class="sxs-lookup"><span data-stu-id="7a45b-110">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span>

  <span data-ttu-id="7a45b-111">Weitere Informationen zum Erstellen von Autorisierungsregeln finden Sie unter [Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="7a45b-111">For more information about creating authorization rules, see [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span></span>

- <span data-ttu-id="7a45b-112">Der Benutzer hat keinen autorisierten Zugriff auf den Zielcomputer.</span><span class="sxs-lookup"><span data-stu-id="7a45b-112">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="7a45b-113">Dies wird durch Zugriffssteuerungslisten bestimmt.</span><span class="sxs-lookup"><span data-stu-id="7a45b-113">This is determined by access control lists (ACLs).</span></span>

  <span data-ttu-id="7a45b-114">Weitere Informationen finden Sie unter [Anmelden bei Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access) oder im Windows PowerShell-Teamblog.</span><span class="sxs-lookup"><span data-stu-id="7a45b-114">For more information, see [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), or the Windows PowerShell Team Blog.</span></span>

- <span data-ttu-id="7a45b-115">Die Windows PowerShell-Remoteverwaltung ist auf dem Zielcomputer möglicherweise nicht aktiviert.</span><span class="sxs-lookup"><span data-stu-id="7a45b-115">Windows PowerShell remote management might not be enabled on the destination computer.</span></span>

  <span data-ttu-id="7a45b-116">Stellen Sie sicher, dass die Remoteverwaltung auf dem Computer aktiviert ist, mit dem der Benutzer eine Verbindung herstellen möchte.</span><span class="sxs-lookup"><span data-stu-id="7a45b-116">Verify remote management is enabled on the computer to which the user is trying to connect.</span></span>

  <span data-ttu-id="7a45b-117">Weitere Informationen finden Sie unter [How to Configure Your Computer for Remoting (Vorgehensweise: Konfigurieren Ihres Computers für das Remoting)](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span><span class="sxs-lookup"><span data-stu-id="7a45b-117">For more information, see [How to Configure Your Computer for Remoting](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span></span>

## <a name="internal-server-error"></a><span data-ttu-id="7a45b-118">Interner Serverfehler</span><span class="sxs-lookup"><span data-stu-id="7a45b-118">Internal Server Error</span></span>

<span data-ttu-id="7a45b-119">Wenn Benutzer versuchen, sich in einem Internet Explorer-Fenster bei Windows PowerShell Web Access anzumelden, wird die Seite **Interner Serverfehler** angezeigt, oder der *Internet Explorer* reagiert nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="7a45b-119">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an **Internal Server Error** page, or *Internet Explorer* stops responding.</span></span>

<span data-ttu-id="7a45b-120">Dieses Problem tritt speziell in Internet Explorer auf.</span><span class="sxs-lookup"><span data-stu-id="7a45b-120">This issue is specific to Internet Explorer.</span></span>

### <a name="possible-cause"></a><span data-ttu-id="7a45b-121">Mögliche Ursache</span><span class="sxs-lookup"><span data-stu-id="7a45b-121">Possible cause</span></span>

<span data-ttu-id="7a45b-122">Dies kann bei Benutzern der Fall sein, die sich mit einem Domänennamen angemeldet haben, der chinesische Zeichen enthält, oder wenn der Gatewayservername mindestens ein chinesisches Zeichen aufweist.</span><span class="sxs-lookup"><span data-stu-id="7a45b-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span>

#### <a name="workaround"></a><span data-ttu-id="7a45b-123">Problemumgehung</span><span class="sxs-lookup"><span data-stu-id="7a45b-123">Workaround</span></span>

1. <span data-ttu-id="7a45b-124">Installieren und Ausführen von Internet Explorer 10</span><span class="sxs-lookup"><span data-stu-id="7a45b-124">Install and run Internet Explorer 10</span></span>
1. <span data-ttu-id="7a45b-125">Ändern Sie für Internet Explorer die Einstellung **Dokumentmodus** in *IE10-Standards*.</span><span class="sxs-lookup"><span data-stu-id="7a45b-125">Change Internet Explorer **Document Mode** setting to *IE10* standards.</span></span>
   1. <span data-ttu-id="7a45b-126">Drücken Sie die Taste **F12**, um die Konsole mit den Entwicklertools zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="7a45b-126">Press **F12** to open the Developer Tools console</span></span>
   1. <span data-ttu-id="7a45b-127">Klicken Sie in Internet Explorer 10 auf **Browsermodus**, und wählen Sie die Option *Internet Explorer 10* aus.</span><span class="sxs-lookup"><span data-stu-id="7a45b-127">In Internet Explorer 10, click **Browser Mode**, and then select *Internet Explorer 10*.</span></span>
   1. <span data-ttu-id="7a45b-128">Klicken Sie auf **Dokumentmodus** und dann auf *IE10-Standards*.</span><span class="sxs-lookup"><span data-stu-id="7a45b-128">Click **Document Mode**, and then click *IE10* standards.</span></span>
   1. <span data-ttu-id="7a45b-129">Drücken Sie die Taste **F12** erneut, um die Konsole mit den Entwicklertools zu schließen.</span><span class="sxs-lookup"><span data-stu-id="7a45b-129">Press **F12** again to close the Developer Tools console.</span></span>
1. <span data-ttu-id="7a45b-130">Deaktivieren Sie die automatische Proxykonfiguration in Internet Explorer 10.</span><span class="sxs-lookup"><span data-stu-id="7a45b-130">Disable automatic proxy configuration in Internet Explorer 10.</span></span>
   1. <span data-ttu-id="7a45b-131">Klicken Sie auf **Tools** und dann auf **Internetoptionen**.</span><span class="sxs-lookup"><span data-stu-id="7a45b-131">Click **Tools**, and then click **Internet Options**.</span></span>
   1. <span data-ttu-id="7a45b-132">Klicken Sie im Dialogfeld **Internetoptionen** auf der Registerkarte **Verbindungen** auf **LAN-Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="7a45b-132">In the **Internet Options** dialog box, on the **Connections** tab, click **LAN settings**.</span></span>
   1. <span data-ttu-id="7a45b-133">Deaktivieren Sie das Kontrollkästchen **Automatische Suche der Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="7a45b-133">Clear the **Automatically detect settings** check box.</span></span> <span data-ttu-id="7a45b-134">Klicken Sie auf **OK** und dann erneut auf **OK**, um das Dialogfeld *Internetoptionen* zu schließen.</span><span class="sxs-lookup"><span data-stu-id="7a45b-134">Click **OK**, and then click **OK** again to close the *Internet Options* dialog box.</span></span>

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a><span data-ttu-id="7a45b-135">Es kann keine Verbindung mit einem Remotecomputer in einer Arbeitsgruppe hergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="7a45b-135">Cannot connect to a remote workgroup computer</span></span>

<span data-ttu-id="7a45b-136">Wenn der Zielcomputer Mitglied einer Arbeitsgruppe ist, können Sie die folgende Syntax verwenden, um den Benutzernamen anzugeben und sich am Computer anzumelden: `<workgroup_name>\<user_name>`.</span><span class="sxs-lookup"><span data-stu-id="7a45b-136">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: `<workgroup_name>\<user_name>`</span></span>

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a><span data-ttu-id="7a45b-137">Die Verwaltungstools des Webservers (IIS) sind nicht verfügbar, obwohl die Rolle installiert wurde.</span><span class="sxs-lookup"><span data-stu-id="7a45b-137">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span>

<span data-ttu-id="7a45b-138">Bei der Installation von Windows PowerShell Web Access mit dem `Install-WindowsFeature`-Cmdlet werden die Verwaltungstools nur installiert, wenn der **IncludeManagementTools**-Parameter zum Cmdlet hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="7a45b-138">If you installed Windows PowerShell Web Access by using the `Install-WindowsFeature` cmdlet, management tools are not installed unless the **IncludeManagementTools** parameter is added to the cmdlet.</span></span>

<span data-ttu-id="7a45b-139">Ein Beispiel finden Sie unter [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets (Installieren von Windows PowerShell Web Access mithilfe von Windows PowerShell-Cmdlets)](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="7a45b-139">For an example, see [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span></span>

<span data-ttu-id="7a45b-140">Sie können die IIS-Manager-Konsole und andere benötigte IIS-Verwaltungstools hinzufügen, indem Sie die Tools in einer Sitzung des **Assistenten zum Hinzufügen von Rollen und Features** auswählen, die auf den Gatewayserver ausgerichtet sind.</span><span class="sxs-lookup"><span data-stu-id="7a45b-140">You can add the IIS Manager console, and other IIS management tools that you need, by selecting the tools in an **Add Roles and Features Wizard** session that is targeted at the gateway server.</span></span> <span data-ttu-id="7a45b-141">Der Assistent zum Hinzufügen von Rollen und Features wird über den Server-Manager geöffnet.</span><span class="sxs-lookup"><span data-stu-id="7a45b-141">The Add Roles and Features Wizard is opened from within Server Manager.</span></span>

## <a name="windows-powershell-web-access-website-is-not-accessible"></a><span data-ttu-id="7a45b-142">Auf die Windows PowerShell Web Access-Website kann nicht zugegriffen werden</span><span class="sxs-lookup"><span data-stu-id="7a45b-142">Windows PowerShell Web Access website is not accessible</span></span>

<span data-ttu-id="7a45b-143">Wenn die verstärkte Sicherheitskonfiguration in Internet Explorer (IE ESC) aktiviert ist, können Sie die Windows PowerShell Web Access-Website der Liste der vertrauenswürdigen Websites hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="7a45b-143">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites.</span></span>

<span data-ttu-id="7a45b-144">Ein wenig empfohlener Ansatz ist wegen Sicherheitsrisiken das Deaktivieren von IE ESC.</span><span class="sxs-lookup"><span data-stu-id="7a45b-144">A less recommended approach, due to security risks, is to disable IE ESC.</span></span> <span data-ttu-id="7a45b-145">Sie können IE ESC auf der Kachel „Eigenschaften“ der Seite „Lokaler Server“ im Server-Manager deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="7a45b-145">You can disable IE ESC in the Properties tile on the Local Server page in Server Manager.</span></span>

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a><span data-ttu-id="7a45b-146">Fehler bei der Autorisierung.</span><span class="sxs-lookup"><span data-stu-id="7a45b-146">An authorization failure occurred.</span></span> <span data-ttu-id="7a45b-147">Stellen Sie sicher, dass Sie zum Herstellen einer Verbindung mit dem Zielcomputer autorisiert sind.</span><span class="sxs-lookup"><span data-stu-id="7a45b-147">Verify that you are authorized to connect to the destination computer.</span></span>

<span data-ttu-id="7a45b-148">Die obenstehende Fehlermeldung wird beim Versuch angezeigt, eine Verbindung herzustellen, wenn der Gatewayserver der Zielcomputer ist und sich auch in einer Arbeitsgruppe befindet.</span><span class="sxs-lookup"><span data-stu-id="7a45b-148">The above error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup.</span></span>

<span data-ttu-id="7a45b-149">Wenn der Gatewayserver auch der Zielserver ist und sich in einer Arbeitsgruppe befindet, geben Sie den Benutzernamen, den Computernamen und den Benutzergruppennamen an.</span><span class="sxs-lookup"><span data-stu-id="7a45b-149">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name.</span></span> <span data-ttu-id="7a45b-150">Verwenden Sie nicht nur einen Punkt (.) als Computernamen.</span><span class="sxs-lookup"><span data-stu-id="7a45b-150">Do not use a dot (.) by itself to represent the computer name.</span></span>

### <a name="scenarios-and-proper-values"></a><span data-ttu-id="7a45b-151">Szenarios und richtige Werte</span><span class="sxs-lookup"><span data-stu-id="7a45b-151">Scenarios and proper values</span></span>

#### <a name="all-cases"></a><span data-ttu-id="7a45b-152">Alle Fälle</span><span class="sxs-lookup"><span data-stu-id="7a45b-152">All cases</span></span>

  <span data-ttu-id="7a45b-153">Parameter</span><span class="sxs-lookup"><span data-stu-id="7a45b-153">Parameter</span></span>   |                                        <span data-ttu-id="7a45b-154">value</span><span class="sxs-lookup"><span data-stu-id="7a45b-154">Value</span></span>
------------- | -----------------------------------------------------------------------------------
<span data-ttu-id="7a45b-155">UserName</span><span class="sxs-lookup"><span data-stu-id="7a45b-155">UserName</span></span>      | `Server_name\user_name`<br/>`Localhost\user_name`<br/>`.\user_name`
<span data-ttu-id="7a45b-156">UserGroup</span><span class="sxs-lookup"><span data-stu-id="7a45b-156">UserGroup</span></span>     | `Server_name\user_group`<br/>`Localhost\user_group`<br/>`.\user_group`
<span data-ttu-id="7a45b-157">ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="7a45b-157">ComputerGroup</span></span> | `Server_name\computer_group`<br/>`Localhost\computer_group`<br/>`.\computer_group`

#### <a name="gateway-server-is-in-a-domain"></a><span data-ttu-id="7a45b-158">Gatewayserver befindet sich in Domäne</span><span class="sxs-lookup"><span data-stu-id="7a45b-158">Gateway server is in a domain</span></span>

 <span data-ttu-id="7a45b-159">Parameter</span><span class="sxs-lookup"><span data-stu-id="7a45b-159">Parameter</span></span>   |                        <span data-ttu-id="7a45b-160">value</span><span class="sxs-lookup"><span data-stu-id="7a45b-160">Value</span></span>
------------ | ----------------------------------------------------
<span data-ttu-id="7a45b-161">Computername</span><span class="sxs-lookup"><span data-stu-id="7a45b-161">ComputerName</span></span> | <span data-ttu-id="7a45b-162">Vollqualifizierter Name des Gatewayservers oder Localhost</span><span class="sxs-lookup"><span data-stu-id="7a45b-162">Fully qualified name of gateway server, or Localhost</span></span>

#### <a name="gateway-server-is-in-a-workgroup"></a><span data-ttu-id="7a45b-163">Gatewayserver befindet sich in Arbeitsgruppe</span><span class="sxs-lookup"><span data-stu-id="7a45b-163">Gateway server is in a workgroup</span></span>

 <span data-ttu-id="7a45b-164">Parameter</span><span class="sxs-lookup"><span data-stu-id="7a45b-164">Parameter</span></span>   |    <span data-ttu-id="7a45b-165">value</span><span class="sxs-lookup"><span data-stu-id="7a45b-165">Value</span></span>
------------ | -----------
<span data-ttu-id="7a45b-166">Computername</span><span class="sxs-lookup"><span data-stu-id="7a45b-166">ComputerName</span></span> | <span data-ttu-id="7a45b-167">Servername</span><span class="sxs-lookup"><span data-stu-id="7a45b-167">Server name</span></span>

### <a name="gateway-credentials"></a><span data-ttu-id="7a45b-168">Gateway-Anmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="7a45b-168">Gateway credentials</span></span>

<span data-ttu-id="7a45b-169">Melden Sie sich bei einem Gatewayserver als Zielcomputer an, indem Sie Anmeldeinformationen in einem der folgenden Formate verwenden.</span><span class="sxs-lookup"><span data-stu-id="7a45b-169">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span>

- `Server_name\user_name`
- `Localhost\user_name`
- `.\user_name`

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a><span data-ttu-id="7a45b-170">Eine Sicherheits-ID (SID) wird in einer Autorisierungsregel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7a45b-170">A security identifier (SID) is displayed in an authorization rule</span></span>

<span data-ttu-id="7a45b-171">In einer Autorisierungsregel wird anstelle der Syntax `user_name/computer_name` eine Sicherheits-ID angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7a45b-171">A security identifier (SID) is displayed in an authorization rule instead of the syntax `user_name/computer_name`.</span></span>

<span data-ttu-id="7a45b-172">Entweder ist die Regel nicht mehr gültig, oder bei der Active Directory-Domänendienste-Abfrage ist ein Fehler aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="7a45b-172">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span> <span data-ttu-id="7a45b-173">Eine Autorisierungsregel ist normalerweise nicht in Fällen gültig, in denen der Gatewayserver zuerst einer Arbeitsgruppe angehörte, dann jedoch einer Domäne beigetreten ist.</span><span class="sxs-lookup"><span data-stu-id="7a45b-173">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain</span></span>

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a><span data-ttu-id="7a45b-174">Es ist nicht möglich, sich bei einer Regel mit einer IPv6-Adresse mit einer Domäne anzumelden.</span><span class="sxs-lookup"><span data-stu-id="7a45b-174">Cannot sign in with rule as an IPv6 address with a domain</span></span>

<span data-ttu-id="7a45b-175">Anmeldung an einem Zielcomputer, der in Autorisierungsregeln als IPv6-Adresse mit einer Domäne angegeben wurde, nicht möglich</span><span class="sxs-lookup"><span data-stu-id="7a45b-175">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span>

<span data-ttu-id="7a45b-176">Autorisierungsregeln unterstützen keine IPv6-Adresse in Form eines Domänennamens.</span><span class="sxs-lookup"><span data-stu-id="7a45b-176">Authorization rules do not support an IPv6 address in form of a domain name.</span></span>

<span data-ttu-id="7a45b-177">Verwenden Sie zum Angeben eines Zielcomputers mithilfe einer IPv6-Adresse die ursprüngliche IPv6-Adresse (mit Doppelpunkten) in der Autorisierungsregel.</span><span class="sxs-lookup"><span data-stu-id="7a45b-177">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span> <span data-ttu-id="7a45b-178">Sowohl domänenbezogene als auch numerische IPv6-Adressen (mit Doppelpunkten) werden auf der Anmeldeseite von Windows PowerShell Web Access als Zielcomputername unterstützt. Dies gilt jedoch nicht für Autorisierungsregeln.</span><span class="sxs-lookup"><span data-stu-id="7a45b-178">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span>

<span data-ttu-id="7a45b-179">Weitere Informationen zu IPv6-Adressen finden Sie unter [Funktionsweise von IPv6](/previous-versions/windows/it-pro/windows-server-2003/cc781672(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="7a45b-179">For more information about IPv6 addresses, see [How IPv6 Works](/previous-versions/windows/it-pro/windows-server-2003/cc781672(v=ws.10)).</span></span>

## <a name="see-also"></a><span data-ttu-id="7a45b-180">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7a45b-180">See Also</span></span>

- <span data-ttu-id="7a45b-181">[Authorization Rules and Security Features of Windows PowerShell Web Access (Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access)](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn282394(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="7a45b-181">[Authorization Rules and Security Features of Windows PowerShell Web Access](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn282394(v=ws.11))</span></span>
- <span data-ttu-id="7a45b-182">[Use the Web-based Windows PowerShell Console (Verwenden der webbasierten Windows PowerShell-Konsole)](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="7a45b-182">[Use the Web-based Windows PowerShell Console](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11))</span></span>
- [<span data-ttu-id="7a45b-183">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="7a45b-183">about_Remote_Requirements</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
