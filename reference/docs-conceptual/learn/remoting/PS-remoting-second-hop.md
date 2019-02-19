---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Ausführen des zweiten Hops in PowerShell-Remoting
ms.openlocfilehash: 1b6e5ad53346324adc7be2d013e154c8600afa4f
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265585"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="2d43d-103">Ausführen des zweiten Hops in PowerShell-Remoting</span><span class="sxs-lookup"><span data-stu-id="2d43d-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="2d43d-104">Das sogenannte „zweite Hop-Problem“ bezieht sich auf folgende Situation:</span><span class="sxs-lookup"><span data-stu-id="2d43d-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="2d43d-105">Sie sind bei _ServerA_ angemeldet.</span><span class="sxs-lookup"><span data-stu-id="2d43d-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="2d43d-106">Sie starten von _ServerA_ aus eine PowerShell-Remotesitzung, um eine Verbindung mit _ServerB_ herzustellen.</span><span class="sxs-lookup"><span data-stu-id="2d43d-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="2d43d-107">Ein auf _ServerB_ über Ihre PowerShell-Remotesitzung ausgeführter Befehl versucht, auf eine Ressource auf _ServerC_ zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="2d43d-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="2d43d-108">Der Zugriff auf die Ressource auf _ServerC_ wird verweigert, da die Anmeldeinformationen, die Sie zum Erstellen der PowerShell-Remotesitzung verwendet haben, nicht von _ServerB_ an _ServerC_ übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="2d43d-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="2d43d-109">Es gibt verschiedene Möglichkeiten, um dieses Problem zu lösen.</span><span class="sxs-lookup"><span data-stu-id="2d43d-109">There are several ways to address this problem.</span></span> <span data-ttu-id="2d43d-110">In diesem Thema werden einige der geläufigsten Lösungen für das zweite Hop-Problem vorgestellt.</span><span class="sxs-lookup"><span data-stu-id="2d43d-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="2d43d-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="2d43d-111">CredSSP</span></span>

<span data-ttu-id="2d43d-112">Sie können den [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) für die Authentifizierung verwenden.</span><span class="sxs-lookup"><span data-stu-id="2d43d-112">You can use the [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) for authentication.</span></span> <span data-ttu-id="2d43d-113">CredSSP speichert Anmeldeinformationen auf dem Remoteserver  _ServerB_. Der Server wird dadurch der Gefahr von Angriffen zum Diebstahl der Anmeldeinformationen ausgesetzt.</span><span class="sxs-lookup"><span data-stu-id="2d43d-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="2d43d-114">Wenn der Remotecomputer kompromittiert ist, hat der Angreifer Zugriff auf die Anmeldeinformationen des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="2d43d-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="2d43d-115">CredSSP ist standardmäßig sowohl auf Client- als auch auf Servercomputern deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="2d43d-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="2d43d-116">Sie sollten CredSSP nur in absolut vertrauenswürdigen Umgebungen aktivieren.</span><span class="sxs-lookup"><span data-stu-id="2d43d-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="2d43d-117">Beispielsweise wenn ein Domänenadministrator eine Verbindung mit einem Domänencontroller herstellt, weil der Domänencontroller hochgradig vertrauenswürdig ist.</span><span class="sxs-lookup"><span data-stu-id="2d43d-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="2d43d-118">Weitere Informationen zu Sicherheitsaspekten bei der Verwendung von CredSSP für PowerShell-Remoting finden Sie unter [Versehentliche Sabotage: Vorsicht vor CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span><span class="sxs-lookup"><span data-stu-id="2d43d-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="2d43d-119">Weitere Informationen zu Angriffen zum Diebstahl von Anmeldeinformationen finden Sie unter [Abschwächen von Pass-the-Hash-Angriffen (PtH) und anderen Techniken zum Diebstahl von Anmeldeinformationen](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span><span class="sxs-lookup"><span data-stu-id="2d43d-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="2d43d-120">Ein Beispiel zum Aktivieren und Verwenden von CredSSP für PowerShell-Remoting finden Sie unter [Using CredSSP to solve the second-hop problem (Verwenden von CredSSP zur Lösung des zweiten Hop-Problems)](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span><span class="sxs-lookup"><span data-stu-id="2d43d-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="2d43d-121">Vorteile</span><span class="sxs-lookup"><span data-stu-id="2d43d-121">Pros</span></span>

- <span data-ttu-id="2d43d-122">Die Lösung eignet sich für alle Server mit Windows Server 2008 oder höher.</span><span class="sxs-lookup"><span data-stu-id="2d43d-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="2d43d-123">Nachteile</span><span class="sxs-lookup"><span data-stu-id="2d43d-123">Cons</span></span>

- <span data-ttu-id="2d43d-124">birgt Sicherheitsrisiken</span><span class="sxs-lookup"><span data-stu-id="2d43d-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="2d43d-125">erfordert die Konfiguration von Client- und Serverrollen</span><span class="sxs-lookup"><span data-stu-id="2d43d-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="2d43d-126">Kerberos-Delegierung (uneingeschränkt)</span><span class="sxs-lookup"><span data-stu-id="2d43d-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="2d43d-127">Sie können auch die uneingeschränkte Kerberos-Delegierung verwenden, um den zweiten Hop ausführen.</span><span class="sxs-lookup"><span data-stu-id="2d43d-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="2d43d-128">Diese Methode ermöglicht jedoch keine Kontrolle darüber, wo die delegierten Anmeldeinformationen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2d43d-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="2d43d-129">**Hinweis:** Active Directory-Konten mit dem Eigenschaftensatz **Konto ist vertraulich und kann nicht delegiert werden** können nicht delegiert werden.</span><span class="sxs-lookup"><span data-stu-id="2d43d-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="2d43d-130">Weitere Informationen finden Sie unter [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts (Sicherheit im Fokus: Analyse von „Konto ist vertraulich und kann nicht delegiert werden“ für privilegierte Konten)](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) und [Kerberos Authentication Tools and Settings (Kerberos-Authentifizierungstools und -Einstellungen)](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="2d43d-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="2d43d-131">Vorteile</span><span class="sxs-lookup"><span data-stu-id="2d43d-131">Pros</span></span>

- <span data-ttu-id="2d43d-132">erfordert keine besondere Codierung</span><span class="sxs-lookup"><span data-stu-id="2d43d-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="2d43d-133">Nachteile</span><span class="sxs-lookup"><span data-stu-id="2d43d-133">Cons</span></span>

- <span data-ttu-id="2d43d-134">keine Unterstützung für den zweiten Hop für WinRM</span><span class="sxs-lookup"><span data-stu-id="2d43d-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="2d43d-135">bietet keine Kontrolle darüber, wo Anmeldeinformationen verwendet werden; birgt Sicherheitsrisiken</span><span class="sxs-lookup"><span data-stu-id="2d43d-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="2d43d-136">Eingeschränkte Kerberos-Delegierung</span><span class="sxs-lookup"><span data-stu-id="2d43d-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="2d43d-137">Sie können eingeschränkte Legacydelegierung (nicht ressourcenbasiert) verwenden, um den zweiten Hop auszuführen.</span><span class="sxs-lookup"><span data-stu-id="2d43d-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="2d43d-138">Konfigurieren Sie die eingeschränkte Kerberos-Delegierung mit der Option "Beliebiges Authentifizierungsprotokoll verwenden" auf den Protokollübergang zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="2d43d-138">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

> [!NOTE]
> <span data-ttu-id="2d43d-139">Active Directory-Konten mit dem Eigenschaftensatz **Konto ist vertraulich und kann nicht delegiert werden** können nicht delegiert werden.</span><span class="sxs-lookup"><span data-stu-id="2d43d-139">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="2d43d-140">Weitere Informationen finden Sie unter [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts (Sicherheit im Fokus: Analyse von „Konto ist vertraulich und kann nicht delegiert werden“ für privilegierte Konten)](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) und [Kerberos Authentication Tools and Settings (Kerberos-Authentifizierungstools und -Einstellungen)](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="2d43d-140">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="2d43d-141">Vorteile</span><span class="sxs-lookup"><span data-stu-id="2d43d-141">Pros</span></span>

- <span data-ttu-id="2d43d-142">erfordert keine besondere Codierung</span><span class="sxs-lookup"><span data-stu-id="2d43d-142">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="2d43d-143">Nachteile</span><span class="sxs-lookup"><span data-stu-id="2d43d-143">Cons</span></span>

- <span data-ttu-id="2d43d-144">keine Unterstützung für den zweiten Hop für WinRM</span><span class="sxs-lookup"><span data-stu-id="2d43d-144">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="2d43d-145">muss auf dem Active Directory-Objekt des Remoteservers konfiguriert werden (_ServerB_)</span><span class="sxs-lookup"><span data-stu-id="2d43d-145">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="2d43d-146">auf einen Server begrenzt;</span><span class="sxs-lookup"><span data-stu-id="2d43d-146">Limited to one domain.</span></span> <span data-ttu-id="2d43d-147">kann Domänen oder Gesamtstrukturen nicht überschreiten</span><span class="sxs-lookup"><span data-stu-id="2d43d-147">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="2d43d-148">erfordert Rechte zum Aktualisieren von Objekten und Dienstprinzipalnamen (SPN)</span><span class="sxs-lookup"><span data-stu-id="2d43d-148">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="2d43d-149">Ressourcenbasierte eingeschränkte Kerberos-Delegierung</span><span class="sxs-lookup"><span data-stu-id="2d43d-149">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="2d43d-150">Mithilfe von ressourcenbasierter eingeschränkter Kerberos-Delegierung (in Windows Server 2012 eingeführt) können Sie die Delegierung der Anmeldeinformationen für das Serverobjekt konfigurieren, in dem sich Ressourcen befinden.</span><span class="sxs-lookup"><span data-stu-id="2d43d-150">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="2d43d-151">Im zuvor beschriebenen zweiten Hop-Szenario konfigurieren Sie _ServerC_ und geben an, von wo aus Anmeldeinformationen akzeptiert werden.</span><span class="sxs-lookup"><span data-stu-id="2d43d-151">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="2d43d-152">**Hinweis:** Active Directory-Konten mit dem Eigenschaftensatz **Konto ist vertraulich und kann nicht delegiert werden** können nicht delegiert werden.</span><span class="sxs-lookup"><span data-stu-id="2d43d-152">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="2d43d-153">Weitere Informationen finden Sie unter [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts (Sicherheit im Fokus: Analyse von „Konto ist vertraulich und kann nicht delegiert werden“ für privilegierte Konten)](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) und [Kerberos Authentication Tools and Settings (Kerberos-Authentifizierungstools und -Einstellungen)](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="2d43d-153">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="2d43d-154">Vorteile</span><span class="sxs-lookup"><span data-stu-id="2d43d-154">Pros</span></span>

- <span data-ttu-id="2d43d-155">kein Speichern von Anmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="2d43d-155">Credentials are not stored.</span></span>
- <span data-ttu-id="2d43d-156">relativ einfach mithilfe von PowerShell-Cmdlets konfigurierbar – keine spezielle Codierung erforderlich</span><span class="sxs-lookup"><span data-stu-id="2d43d-156">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="2d43d-157">kein spezieller Domänenzugriff erforderlich</span><span class="sxs-lookup"><span data-stu-id="2d43d-157">No special domain access is required.</span></span>
- <span data-ttu-id="2d43d-158">domänen- und gesamtstrukturübergreifende Funktionsweise</span><span class="sxs-lookup"><span data-stu-id="2d43d-158">Works across domains and forests.</span></span>
- <span data-ttu-id="2d43d-159">PowerShell-Code</span><span class="sxs-lookup"><span data-stu-id="2d43d-159">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="2d43d-160">Nachteile</span><span class="sxs-lookup"><span data-stu-id="2d43d-160">Cons</span></span>

- <span data-ttu-id="2d43d-161">erfordert Windows Server 2012 oder höher</span><span class="sxs-lookup"><span data-stu-id="2d43d-161">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="2d43d-162">keine Unterstützung für den zweiten Hop für WinRM</span><span class="sxs-lookup"><span data-stu-id="2d43d-162">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="2d43d-163">erfordert Rechte zum Aktualisieren von Objekten und Dienstprinzipalnamen (SPN)</span><span class="sxs-lookup"><span data-stu-id="2d43d-163">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

### <a name="example"></a><span data-ttu-id="2d43d-164">Beispiel</span><span class="sxs-lookup"><span data-stu-id="2d43d-164">Example</span></span>

<span data-ttu-id="2d43d-165">Sehen wir uns ein PowerShell-Beispiel an, bei dem _ServerC_ für eine ressourcenbasierte eingeschränkte Delegierung konfiguriert wird, um delegierte Anmeldeinformationen von einem _ServerB_ zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="2d43d-165">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="2d43d-166">In diesem Beispiel wird davon ausgegangen, dass alle Server Windows Server 2012 oder höher ausführen und dass für jede Domäne jedes eingesetzten Servers mindestens ein Windows Server 2012-Domänencontroller vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="2d43d-166">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="2d43d-167">Bevor Sie die eingeschränkte Delegierung konfigurieren können, müssen Sie das `RSAT-AD-PowerShell`-Feature hinzufügen, um das Active Directory-PowerShell-Modul zu installieren und anschließend dieses Modul in die Sitzung zu importieren:</span><span class="sxs-lookup"><span data-stu-id="2d43d-167">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
<span data-ttu-id="2d43d-168">Mehrere verfügbare Cmdlets haben jetzt einen **PrincipalsAllowedToDelegateToAccount**-Parameter:</span><span class="sxs-lookup"><span data-stu-id="2d43d-168">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

<span data-ttu-id="2d43d-169">Der Parameter **PrincipalsAllowedToDelegateToAccount** legt das Active Directory-Objektattribut **MsDS-AllowedToActOnBehalfOfOtherIdentity** fest, das eine Zugriffssteuerungsliste (access control list, ACL) enthält. Diese gibt an, welche Konten die Berechtigung zum Delegieren von Anmeldeinformationen für das zugehörige Konto haben (in unserem Beispiel das Computerkonto für _Server_).</span><span class="sxs-lookup"><span data-stu-id="2d43d-169">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="2d43d-170">Richten Sie nun die Variablen ein, die wir verwenden, um die Server darzustellen:</span><span class="sxs-lookup"><span data-stu-id="2d43d-170">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="2d43d-171">WinRM (und somit die PowerShell-Remoting) wird standardmäßig als Computerkonto ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="2d43d-171">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="2d43d-172">Dies sehen Sie anhand der **StartName**-Eigenschaft des `winrm`-Diensts:</span><span class="sxs-lookup"><span data-stu-id="2d43d-172">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="2d43d-173">Damit _ServerC_ die Delegierung aus einer PowerShell-Remoting-Sitzung auf _ServerB_ zulässt, vergeben wir Zugriffsrechte, indem wir den Parameter **PrincipalsAllowedToDelegateToAccount** von _ServerC_ auf das Computerobjekt von _ServerB_ festlegen:</span><span class="sxs-lookup"><span data-stu-id="2d43d-173">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="2d43d-174">Das Kerberos-[Schlüsselverteilungscenter (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) speichert verweigerte Zugriffsversuche (negativer Cache) über einen Zeitraum von 15 Minuten.</span><span class="sxs-lookup"><span data-stu-id="2d43d-174">The Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="2d43d-175">Wenn _ServerB_ zuvor versucht hat, auf _ServerC_ zuzugreifen, müssen Sie zum Löschen des Caches auf _ServerB_ folgenden Befehl aufrufen:</span><span class="sxs-lookup"><span data-stu-id="2d43d-175">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="2d43d-176">Sie können den Computer auch neu starten oder mindestens 15 Minuten warten, bevor Sie den Cache löschen.</span><span class="sxs-lookup"><span data-stu-id="2d43d-176">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="2d43d-177">Nach dem Löschen des Cache können Sie erfolgreich Code vom _ServerA_ über _ServerB_ auf _ServerC_ ausführen:</span><span class="sxs-lookup"><span data-stu-id="2d43d-177">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

<span data-ttu-id="2d43d-178">In diesem Beispiel wird die `$using`-Variable verwendet, um die `$ServerC`-Variable für _ServerB_ sichtbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="2d43d-178">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="2d43d-179">Weitere Informationen zur `$using`-Variable finden Sie unter [About Remote Variables (Informationen zu Remote-Variablen)](https://technet.microsoft.com/library/jj149005.aspx).</span><span class="sxs-lookup"><span data-stu-id="2d43d-179">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span></span>

<span data-ttu-id="2d43d-180">Damit mehrere Server Anmeldeinformationen an _ServerC_ delegieren können, müssen Sie den Wert des Parameters **PrincipalsAllowedToDelegateToAccount** auf _ServerC_ auf ein Array festlegen:</span><span class="sxs-lookup"><span data-stu-id="2d43d-180">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

<span data-ttu-id="2d43d-181">Wenn Sie den zweiten Hop zwischen Domänen vornehmen möchten, müssen Sie den vollqualifizierten Domänennamen (FQDN) des Domänencontrollers jener Domäne hinzufügen, zu der _ServerB_ gehört:</span><span class="sxs-lookup"><span data-stu-id="2d43d-181">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="2d43d-182">Um die Delegierung von Anmeldeinformationen an ServerC zu löschen, müssen Sie den Wert des Parameters **PrincipalsAllowedToDelegateToAccount** auf _ServerC_ auf `$null` festlegen:</span><span class="sxs-lookup"><span data-stu-id="2d43d-182">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="2d43d-183">Informationen zu ressourcenbasierter eingeschränkter Kerberos-Delegierung</span><span class="sxs-lookup"><span data-stu-id="2d43d-183">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="2d43d-184">Neues bei der Kerberos-Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="2d43d-184">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- [<span data-ttu-id="2d43d-185">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1 (Wie Windows Server 2012 bei den Problemen mit der eingeschränkten Kerberos-Delegierung Abhilfe schafft, Teil 1)</span><span class="sxs-lookup"><span data-stu-id="2d43d-185">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1</span></span>](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [<span data-ttu-id="2d43d-186">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2 (Wie Windows Server 2012 bei den Problemen mit der eingeschränkten Kerberos-Delegierung Abhilfe schafft, Teil 2)</span><span class="sxs-lookup"><span data-stu-id="2d43d-186">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2</span></span>](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [<span data-ttu-id="2d43d-187">Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication (Grundlegendes zur eingeschränkten Kerberos-Delegierung für Azure Active Directory Application Proxy-Bereitstellungen mit integrierter Windows-Authentifizierung)</span><span class="sxs-lookup"><span data-stu-id="2d43d-187">Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication</span></span>](https://aka.ms/kcdpaper)
- <span data-ttu-id="2d43d-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity ([MS-ADA2]: Active Directory-Schemaattribute M2.210 msDS-AllowedToActOnBehalfOfOtherIdentity-Attribut)](https://msdn.microsoft.com/library/hh554126.aspx)</span><span class="sxs-lookup"><span data-stu-id="2d43d-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span></span>
- <span data-ttu-id="2d43d-189">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy ([MS-SFU]: Kerberos-Protokollerweiterungen: Dienst für Benutzer und eingeschränktes Delegierungsprotokoll 1.3.2 S4U2proxy)](https://msdn.microsoft.com/library/cc246079.aspx)</span><span class="sxs-lookup"><span data-stu-id="2d43d-189">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span></span>
- [<span data-ttu-id="2d43d-190">Resource Based Kerberos Constrained Delegation (Ressourcenbasierte eingeschränkte Kerberos-Delegierung)</span><span class="sxs-lookup"><span data-stu-id="2d43d-190">Resource Based Kerberos Constrained Delegation</span></span>](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [<span data-ttu-id="2d43d-191">Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount (Remoteverwaltung ohne eingeschränkte Delegierung mit PrincipalsAllowedToDelegateToAccount)</span><span class="sxs-lookup"><span data-stu-id="2d43d-191">Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount</span></span>](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="2d43d-192">PSSessionConfiguration mithilfe von RunAs</span><span class="sxs-lookup"><span data-stu-id="2d43d-192">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="2d43d-193">Sie können eine Sitzungskonfiguration auf _ServerB_ erstellen und ihren **RunAsCredential**-Parameter festlegen.</span><span class="sxs-lookup"><span data-stu-id="2d43d-193">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="2d43d-194">Weitere Informationen zur Verwendung von PSSessionConfiguration und RunAs, um das zweite Hop-Problem zu lösen, finden Sie unter [Another solution to multi-hop PowerShell remoting (Eine weitere Lösung für Multi-Hop-PowerShell-Remoting)](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span><span class="sxs-lookup"><span data-stu-id="2d43d-194">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="2d43d-195">Vorteile</span><span class="sxs-lookup"><span data-stu-id="2d43d-195">Pros</span></span>

- <span data-ttu-id="2d43d-196">funktioniert mit jedem Server mit WMF 3.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="2d43d-196">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="2d43d-197">Nachteile</span><span class="sxs-lookup"><span data-stu-id="2d43d-197">Cons</span></span>

- <span data-ttu-id="2d43d-198">erfordert die Konfiguration von **PSSessionConfiguration** und **RunAs** auf jedem Zwischenserver (_ServerB_)</span><span class="sxs-lookup"><span data-stu-id="2d43d-198">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="2d43d-199">erfordert Kennwortverwaltungsaufgaben bei Verwendung eines Domänen-**RunAs**-Kontos</span><span class="sxs-lookup"><span data-stu-id="2d43d-199">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="2d43d-200">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="2d43d-200">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="2d43d-201">Mit JEA können Sie einschränken, welche Befehle ein Administrator während einer PowerShell-Sitzung ausführen darf.</span><span class="sxs-lookup"><span data-stu-id="2d43d-201">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="2d43d-202">Das Toolkit kann verwendet werden, um das zweite Hop-Problem zu lösen.</span><span class="sxs-lookup"><span data-stu-id="2d43d-202">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="2d43d-203">Informationen zu JEA finden Sie unter [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="2d43d-203">For information about JEA, see [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="2d43d-204">Vorteile</span><span class="sxs-lookup"><span data-stu-id="2d43d-204">Pros</span></span>

- <span data-ttu-id="2d43d-205">keine Kennwortverwaltungsaufgaben bei Verwendung eines virtuellen Kontos</span><span class="sxs-lookup"><span data-stu-id="2d43d-205">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="2d43d-206">Nachteile</span><span class="sxs-lookup"><span data-stu-id="2d43d-206">Cons</span></span>

- <span data-ttu-id="2d43d-207">erfordert WMF 5.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="2d43d-207">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="2d43d-208">erfordert die Konfiguration auf jedem Zwischenserver (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="2d43d-208">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="2d43d-209">Übergeben von Anmeldeinformationen innerhalb eines Invoke-Command-Skriptblocks</span><span class="sxs-lookup"><span data-stu-id="2d43d-209">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="2d43d-210">Anmeldeinformationen können innerhalb des **ScriptBlock**-Parameters für einen Aufruf des [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command)-Cmdlet übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="2d43d-210">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="2d43d-211">Vorteile</span><span class="sxs-lookup"><span data-stu-id="2d43d-211">Pros</span></span>

- <span data-ttu-id="2d43d-212">erfordert keine spezielle Serverkonfiguration</span><span class="sxs-lookup"><span data-stu-id="2d43d-212">Does not require special server configuration.</span></span>
- <span data-ttu-id="2d43d-213">funktioniert auf jedem Server mit WMF 2.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="2d43d-213">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="2d43d-214">Nachteile</span><span class="sxs-lookup"><span data-stu-id="2d43d-214">Cons</span></span>

- <span data-ttu-id="2d43d-215">erfordert eine umständliche Codetechnik</span><span class="sxs-lookup"><span data-stu-id="2d43d-215">Requires an awkward code technique.</span></span>
- <span data-ttu-id="2d43d-216">Wenn WMF 2.0 ausgeführt wird, wird eine andere Syntax zum Übergeben von Argumenten an eine Remotesitzung benötigt.</span><span class="sxs-lookup"><span data-stu-id="2d43d-216">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="2d43d-217">Beispiel</span><span class="sxs-lookup"><span data-stu-id="2d43d-217">Example</span></span>

<span data-ttu-id="2d43d-218">Das folgende Beispiel zeigt, wie Anmeldeinformationen in einem **Invoke-Command**-Skriptblock übergeben werden:</span><span class="sxs-lookup"><span data-stu-id="2d43d-218">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="2d43d-219">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2d43d-219">See also</span></span>

[<span data-ttu-id="2d43d-220">Sicherheitsaspekte von PowerShell-Remoting</span><span class="sxs-lookup"><span data-stu-id="2d43d-220">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)
