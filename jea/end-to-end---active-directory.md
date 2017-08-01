---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: End-to-End Active Directory
ms.technology: powershell
ms.openlocfilehash: 3108f5dad96ef54feb3cf559fae38812ed46849c
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="end-to-end---active-directory"></a><span data-ttu-id="2ec83-103">End-to-End – Active Directory</span><span class="sxs-lookup"><span data-stu-id="2ec83-103">End to End - Active Directory</span></span>
<span data-ttu-id="2ec83-104">Angenommen, der Umfang Ihres Programms hat sich erhöht.</span><span class="sxs-lookup"><span data-stu-id="2ec83-104">Imagine the scope of your program has increased.</span></span>
<span data-ttu-id="2ec83-105">Sie sollen jetzt JEA zu Domänencontrollern hinzufügen, damit Active Directory-Aktionen ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="2ec83-105">You are now responsible for adding JEA to Domain Controllers to perform Active Directory actions.</span></span>
<span data-ttu-id="2ec83-106">Die Helpdeskmitarbeiter werden JEA verwenden, um Konten zu entsperren, Kennwörter zurückzusetzen und ähnliche Aktionen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-106">The help desk people are going to use JEA to unlock accounts, reset passwords, and do other similar actions.</span></span>

<span data-ttu-id="2ec83-107">Sie müssen einer anderen Gruppe von Benutzern einen vollkommen neuen Satz an Befehlen verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-107">You need to expose a completely new set of commands to a different group of people.</span></span>
<span data-ttu-id="2ec83-108">Außerdem müssen Sie eine Vielzahl von vorhandenen Active Directory-Skripts verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-108">On top of that, you have a bunch of existing Active Directory scripts you need to expose.</span></span>
<span data-ttu-id="2ec83-109">Dieser Abschnitt leitet Sie durch die Erstellung einer Sitzungskonfiguration sowie einer Rollenfunktion für diese Aufgabe.</span><span class="sxs-lookup"><span data-stu-id="2ec83-109">This section will walk through authoring a Session Configuration and Role Capability for this task.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2ec83-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="2ec83-110">Prerequisites</span></span>
<span data-ttu-id="2ec83-111">Um diesen Abschnitt schrittweise durchzugehen, müssen Sie auf einem Domänencontroller arbeiten.</span><span class="sxs-lookup"><span data-stu-id="2ec83-111">To follow this section step-by-step, you'll need to be operating on a domain controller.</span></span>
<span data-ttu-id="2ec83-112">Machen Sie sich keine Sorgen, wenn Sie keinen Zugriff auf Ihren Domänencontroller haben.</span><span class="sxs-lookup"><span data-stu-id="2ec83-112">If you don't have access to your domain controller, don't worry.</span></span>
<span data-ttu-id="2ec83-113">Folgen Sie den Anweisungen einfach mit einem anderen Szenario oder einer anderen Rolle, mit der Sie vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="2ec83-113">Try to follow along with by working against some other scenario or role with which you are familiar.</span></span>
<span data-ttu-id="2ec83-114">Wenn Sie schnell einen neuen Domänencontroller einrichten möchten, finden Sie die notwendigen Informationen im Anhang unter [Erstellen eines Domänencontrollers](.\creating-a-domain-controller.md).</span><span class="sxs-lookup"><span data-stu-id="2ec83-114">If you want to quickly set up a new domain controller, check out the [Creating a Domain Controller appendix](.\creating-a-domain-controller.md).</span></span>

## <a name="steps-to-make-a-new-role-capability-and-session-configuration"></a><span data-ttu-id="2ec83-115">Schritte zum Erstellen einer neuen Rollenfunktion und Sitzungskonfiguration</span><span class="sxs-lookup"><span data-stu-id="2ec83-115">Steps to Make a new Role Capability and Session Configuration</span></span>

<span data-ttu-id="2ec83-116">Das Erstellen einer neuen Rollenfunktion kann auf den ersten Blick eine große Herausforderung sein. Die Aufgabe lässt sich jedoch in relativ einfache Schritte unterteilen:</span><span class="sxs-lookup"><span data-stu-id="2ec83-116">Making a new role capability can seem daunting at first, but it can be broken into fairly simple steps:</span></span>

1.  <span data-ttu-id="2ec83-117">Ermitteln Sie die Aufgaben, die Sie aktivieren müssen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-117">Identify the tasks you need to enable</span></span>
2.  <span data-ttu-id="2ec83-118">Schränken Sie diese Aufgaben nach Bedarf ein.</span><span class="sxs-lookup"><span data-stu-id="2ec83-118">Restrict those tasks as necessary</span></span>
3.  <span data-ttu-id="2ec83-119">Stellen Sie sicher, dass die Aufgaben mit JEA funktionieren.</span><span class="sxs-lookup"><span data-stu-id="2ec83-119">Confirm they work with JEA</span></span>
4.  <span data-ttu-id="2ec83-120">Speichern Sie sie in einer Rollenfunktionsdatei.</span><span class="sxs-lookup"><span data-stu-id="2ec83-120">Put them in a Role Capability file</span></span>
5.  <span data-ttu-id="2ec83-121">Registrieren Sie eine Sitzungskonfiguration, die diese Rollenfunktion verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="2ec83-121">Register a Session Configuration that exposes that Role Capability</span></span>

## <a name="step-1-identify-what-needs-to-be-exposed"></a><span data-ttu-id="2ec83-122">Schritt 1: Ermitteln Sie die Aktionen und Aufgaben, die verfügbar gemacht werden müssen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-122">Step 1: Identify What Needs to Be Exposed</span></span>
<span data-ttu-id="2ec83-123">Bevor Sie eine neue Rollenfunktion oder Sitzungskonfiguration erstellen können, müssen Sie alle Aktionen und Aufgaben identifizieren, die Benutzer über den JEA-Endpunkt ausführen können müssen. Sie müssen ebenfalls ermitteln, wie diese Aktionen und Aufgaben in PowerShell ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="2ec83-123">Before you make a new Role Capability or Session Configuration, you need to identify all of the things users will need to do through the JEA endpoint, as well as how to do them through PowerShell.</span></span>
<span data-ttu-id="2ec83-124">Dieser Schritt erfordert sehr viel Recherche und die Erfassung von Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-124">This will involve a fair amount of requirement gathering and research.</span></span>
<span data-ttu-id="2ec83-125">Die Art und Weise, wie Sie diesen Prozess durchführen, richtet sich nach Ihrer Organisation und Ihren Zielen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-125">How you go about this process will depend on your organization and goals.</span></span>
<span data-ttu-id="2ec83-126">Die Erfassung von Anforderungen und die Recherche sind in der Praxis ein entscheidender Bestandteil des Prozesses.</span><span class="sxs-lookup"><span data-stu-id="2ec83-126">It is important to call out requirement gathering and research as a critical part of the real world process.</span></span>
<span data-ttu-id="2ec83-127">Dies ist möglicherweise der schwierigste Schritt im gesamten Prozess der Einrichtung von JEA.</span><span class="sxs-lookup"><span data-stu-id="2ec83-127">This may be the most difficult step in the process of adopting JEA.</span></span>

### <a name="find-resources"></a><span data-ttu-id="2ec83-128">Suchen nach Ressourcen</span><span class="sxs-lookup"><span data-stu-id="2ec83-128">Find Resources</span></span>
<span data-ttu-id="2ec83-129">Folgende Onlineressourcen bieten nützliche Informationen zum Erstellen eines Active Directory-Verwaltungsendpunkts:</span><span class="sxs-lookup"><span data-stu-id="2ec83-129">Here is a set of online resources that might have come up in your research on creating an Active Directory management endpoint:</span></span>
-   [<span data-ttu-id="2ec83-130">Active Directory PowerShell Overview</span><span class="sxs-lookup"><span data-stu-id="2ec83-130">Active Directory PowerShell Overview</span></span>](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx)
-   [<span data-ttu-id="2ec83-131">CMD to PowerShell Guide for Active Directory</span><span class="sxs-lookup"><span data-stu-id="2ec83-131">CMD to PowerShell Guide for Active Directory</span></span>](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx)

### <a name="make-a-list"></a><span data-ttu-id="2ec83-132">Erstellen einer Liste</span><span class="sxs-lookup"><span data-stu-id="2ec83-132">Make a List</span></span>
<span data-ttu-id="2ec83-133">Mit den zehn folgenden Aktionen werden Sie im Rest dieses Abschnitts arbeiten.</span><span class="sxs-lookup"><span data-stu-id="2ec83-133">Here is a set of ten actions that you will be working from in the remainder of this section.</span></span>
<span data-ttu-id="2ec83-134">Denken Sie daran, dass es sich hier nur um ein Beispiel handelt und Ihre Organisation höchstwahrscheinlich andere Anforderungen stellt:</span><span class="sxs-lookup"><span data-stu-id="2ec83-134">Keep in mind this is simply an example, your organizations requirements may be different:</span></span>

|<span data-ttu-id="2ec83-135">Aktion</span><span class="sxs-lookup"><span data-stu-id="2ec83-135">Action</span></span>                                                         |<span data-ttu-id="2ec83-136">PowerShell-Befehl</span><span class="sxs-lookup"><span data-stu-id="2ec83-136">PowerShell Command</span></span>                                             |
|---------------------------------------------------------------|---------------------------------------------------------------|
|<span data-ttu-id="2ec83-137">Konto entsperren</span><span class="sxs-lookup"><span data-stu-id="2ec83-137">Account Unlock</span></span>                                                 |`Unlock-ADAccount`                                             |
|<span data-ttu-id="2ec83-138">Kennwort zurücksetzen</span><span class="sxs-lookup"><span data-stu-id="2ec83-138">Password Reset</span></span>                                                 |<span data-ttu-id="2ec83-139">`Set-ADAccountPassword` und `Set-ADUser -ChangePasswordAtLogon`</span><span class="sxs-lookup"><span data-stu-id="2ec83-139">`Set-ADAccountPassword` and `Set-ADUser -ChangePasswordAtLogon`</span></span>|
|<span data-ttu-id="2ec83-140">Position eines Benutzers ändern</span><span class="sxs-lookup"><span data-stu-id="2ec83-140">Change a User's Title</span></span>                                          |`Set-ADUser -Title`                                            |  
|<span data-ttu-id="2ec83-141">AD-Konten finden, die gesperrt oder deaktiviert wurden oder inaktiv sind usw.</span><span class="sxs-lookup"><span data-stu-id="2ec83-141">Find AD Accounts that are locked out, disabled, inactive, etc.</span></span> |`Search-ADAccount`                                             |
|<span data-ttu-id="2ec83-142">Benutzer zu Gruppe hinzufügen</span><span class="sxs-lookup"><span data-stu-id="2ec83-142">Add User to Group</span></span>                                              |`Add-ADGroupMember -Identity (with whitelist) -Members`        |
|<span data-ttu-id="2ec83-143">Benutzer aus Gruppe entfernen</span><span class="sxs-lookup"><span data-stu-id="2ec83-143">Remove User from Group</span></span>                                         |`Remove-ADGroupMember -Identity (with whitelist) -Members`     |
|<span data-ttu-id="2ec83-144">Benutzerkonto aktivieren</span><span class="sxs-lookup"><span data-stu-id="2ec83-144">Enable a user account</span></span>                                          |`Enable-ADAccount`                                             |
|<span data-ttu-id="2ec83-145">Benutzerkonto deaktivieren</span><span class="sxs-lookup"><span data-stu-id="2ec83-145">Disable a user account</span></span>                                         |`Disable-ADAccount`                                            |

## <a name="step-2-restrict-tasks-as-necessary"></a><span data-ttu-id="2ec83-146">Schritt 2: Schränken Sie die Aufgaben nach Bedarf ein.</span><span class="sxs-lookup"><span data-stu-id="2ec83-146">Step 2: Restrict Tasks as Necessary</span></span>

<span data-ttu-id="2ec83-147">Nachdem Sie jetzt über die Liste der notwendigen Aktionen verfügen, müssen Sie die Funktion jedes einzelnen Befehls gründlich durchdenken.</span><span class="sxs-lookup"><span data-stu-id="2ec83-147">Now that you have your list of actions, you need to think through the capabilities of each command.</span></span>
<span data-ttu-id="2ec83-148">Dafür gibt es zwei wichtige Gründe:</span><span class="sxs-lookup"><span data-stu-id="2ec83-148">There are two important reasons to do this:</span></span>

1.  <span data-ttu-id="2ec83-149">Es kann leicht passieren, dass Sie Benutzern mehr Funktionen bieten als gewollt.</span><span class="sxs-lookup"><span data-stu-id="2ec83-149">It is easy to give users more capabilities than you intend.</span></span>
<span data-ttu-id="2ec83-150">`Set-ADUser` z. B. ist ein unglaublich leistungsfähiger und flexibler Befehl.</span><span class="sxs-lookup"><span data-stu-id="2ec83-150">For example, `Set-ADUser` is an incredibly powerful and flexible command.</span></span>
<span data-ttu-id="2ec83-151">Sie möchten sicher nicht die gesamte Funktionalität dieses Befehls für Helpdeskbenutzer verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-151">You may not want to expose everything it can do to help desk users.</span></span>  

2.  <span data-ttu-id="2ec83-152">Schlimmer noch: Es kann passieren, dass Sie Befehle verfügbar machen, die es Benutzern ermöglichen, die Beschränkungen von JEA zu umgehen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-152">Even worse, it's possible to expose commands that allow users to escape JEA's restrictions.</span></span>
<span data-ttu-id="2ec83-153">In diesem Fall kann JEA nicht mehr als Sicherheitsmechanismus fungieren.</span><span class="sxs-lookup"><span data-stu-id="2ec83-153">If this happens, JEA ceases to function as a security boundary.</span></span>
<span data-ttu-id="2ec83-154">Gehen Sie daher beim Auswählen von Befehlen mit größter Umsicht vor.</span><span class="sxs-lookup"><span data-stu-id="2ec83-154">Please be careful when selecting commands.</span></span>
<span data-ttu-id="2ec83-155">Invoke-Expression ermöglicht Benutzern beispielsweise die Ausführung von uneingeschränktem Code.</span><span class="sxs-lookup"><span data-stu-id="2ec83-155">For example, Invoke-Expression will allow users to run unrestricted code.</span></span>
<span data-ttu-id="2ec83-156">Weitere Informationen zu diesem Thema finden Sie im Abschnitt „Überlegungen zum Einschränken von Befehlen“.</span><span class="sxs-lookup"><span data-stu-id="2ec83-156">For more discussion on this topic, check out the Considerations When Restricting Commands section.</span></span>

<span data-ttu-id="2ec83-157">Nachdem Sie jeden Befehl sorgfältig geprüft haben, entscheiden Sie sich für folgende Einschränkungen:</span><span class="sxs-lookup"><span data-stu-id="2ec83-157">After reviewing each command, you decide to restrict the following:</span></span>

1.  <span data-ttu-id="2ec83-158">`Set-ADUser` soll nur mit dem Parameter „-Title“ ausgeführt werden dürfen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-158">`Set-ADUser` should only be allowed to run with the -Title parameter</span></span>

2.  <span data-ttu-id="2ec83-159">`Add-ADGroupMember` und `Remove-ADGroupMember` sollen nur für bestimmte Gruppen funktionieren.</span><span class="sxs-lookup"><span data-stu-id="2ec83-159">`Add-ADGroupMember` and `Remove-ADGroupMember` should only work with certain groups</span></span>

### <a name="step-3-confirm-the-tasks-work-with-jea"></a><span data-ttu-id="2ec83-160">Schritt 3: Bestätigen Sie, dass die Aufgaben mit JEA funktionieren.</span><span class="sxs-lookup"><span data-stu-id="2ec83-160">Step 3: Confirm the Tasks Work with JEA</span></span>
<span data-ttu-id="2ec83-161">Die Verwendung dieser Cmdlets ist in der eingeschränkten JEA-Umgebung möglicherweise nicht ganz einfach.</span><span class="sxs-lookup"><span data-stu-id="2ec83-161">Actually using those cmdlets may not be straightforward in the restricted JEA environment.</span></span>
<span data-ttu-id="2ec83-162">JEA wird im Modus *NoLanguage* ausgeführt, der unter anderem verhindert, dass Benutzer Variablen verwenden dürfen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-162">JEA runs in *NoLanguage* mode which, among other things, prevents users from using variables.</span></span>
<span data-ttu-id="2ec83-163">Um die Benutzerfreundlichkeit sicherzustellen, müssen Sie einige Dinge prüfen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-163">In order to ensure that end users have a smooth experience, it's important to check for a few things.</span></span>

<span data-ttu-id="2ec83-164">Sehen Sie sich z. B. `Set-ADAccountPassword` an.</span><span class="sxs-lookup"><span data-stu-id="2ec83-164">As an example, consider `Set-ADAccountPassword`.</span></span>
<span data-ttu-id="2ec83-165">Der Parameter „-NewPassword“ erfordert eine sichere Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="2ec83-165">The -NewPassword parameter requires a secure string.</span></span>
<span data-ttu-id="2ec83-166">Benutzer erstellen häufig eine sichere Zeichenfolge und übergeben sie als Variable, wie hier zu sehen:</span><span class="sxs-lookup"><span data-stu-id="2ec83-166">Often, users create a secure string and pass it in as a variable (as below):</span></span>

```PowerShell
$newPassword = Read-Host -Prompt "Specify a new password" -AsSecureString
Set-ADAccountPassword -Identity mollyd -NewPassword $newPassword -Reset
```

<span data-ttu-id="2ec83-167">Der Modus *NoLanguage* verhindert jedoch die Verwendung von Variablen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-167">However, *NoLanguage* mode prevents the usage of variables.</span></span>
<span data-ttu-id="2ec83-168">Es gibt zwei Möglichkeiten, diese Einschränkung zu umgehen:</span><span class="sxs-lookup"><span data-stu-id="2ec83-168">You can get around this restriction in two ways:</span></span>

1.  <span data-ttu-id="2ec83-169">Sie können festlegen, dass Benutzer den Befehl ohne Variablenzuweisung ausführen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-169">You can require users run the command without assigning variables.</span></span>
<span data-ttu-id="2ec83-170">Dies lässt sich einfach konfigurieren, kann jedoch für die Operatoren, die den Endpunkt verwenden, äußerst mühsam sein.</span><span class="sxs-lookup"><span data-stu-id="2ec83-170">This is easy to configure, but can be painful for the operators using the endpoint.</span></span>
<span data-ttu-id="2ec83-171">Wer möchte denn beim Zurücksetzen eines Kennworts jedes Mal die sichere Zeichenfolge eingeben?</span><span class="sxs-lookup"><span data-stu-id="2ec83-171">Who wants to type this out every time you reset a password?</span></span>
```PowerShell
Set-ADAccountPassword -Identity mollyd -NewPassword (Read-Host -Prompt "Specify a new password" -AsSecureString) -Reset
```

2.  <span data-ttu-id="2ec83-172">Sie können die Komplexität in einem Skript oder einer Funktion verpacken, das bzw. die Sie für die Endbenutzer verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-172">You can wrap the complexity in a script or a function that you expose to end users.</span></span>
<span data-ttu-id="2ec83-173">Skripts und Funktionen, die Sie verfügbar machen, werden in einem uneingeschränkten Kontext ausgeführt. Sie können völlig problemlos Funktionen schreiben, die Variablen verwenden und andere Befehle aufrufen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-173">Scripts and functions that you expose run in an unrestricted context; you can write functions that use variables and call other commands without any issue.</span></span>
<span data-ttu-id="2ec83-174">Diese Vorgehensweise verbessert die Benutzerfreundlichkeit, verhindert Fehler, erfordert weniger PowerShell-Kenntnisse und senkt das Risiko, dass versehentlich zu viel Funktionalität verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="2ec83-174">This approach simplifies the end user experience, prevents errors, reduces required PowerShell knowledge, and reduces unintentionally exposing excess functionality.</span></span>
<span data-ttu-id="2ec83-175">Der einzige Nachteil ist der Aufwand für die Erstellung und Verwaltung der Funktion.</span><span class="sxs-lookup"><span data-stu-id="2ec83-175">The only downside is the cost of authoring and maintaining the function.</span></span>

### <a name="aside-adding-a-function-to-your-module"></a><span data-ttu-id="2ec83-176">Exkurs: Hinzufügen einer Funktion zu Ihrem Modul</span><span class="sxs-lookup"><span data-stu-id="2ec83-176">Aside: Adding a Function to your Module</span></span>
<span data-ttu-id="2ec83-177">Mithilfe von Vorgehensweise Nr. 2 werden Sie eine PowerShell-Funktion namens `Reset-ContosoUserPassword` schreiben.</span><span class="sxs-lookup"><span data-stu-id="2ec83-177">Taking approach #2, you are going to write a PowerShell function called `Reset-ContosoUserPassword`.</span></span>
<span data-ttu-id="2ec83-178">Diese Funktion führt alle Aktionen aus, die erforderlich sind, wenn Sie das Kennwort eines Benutzers zurücksetzen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-178">This function is going to do everything that needs to happen when you reset a user's password.</span></span>
<span data-ttu-id="2ec83-179">In Ihrer Organisation gehören dazu möglicherweise hochkomplexe Prozesse.</span><span class="sxs-lookup"><span data-stu-id="2ec83-179">In your organization, this may involve doing fancy and complicated things.</span></span>
<span data-ttu-id="2ec83-180">Da es sich hier nur um ein Beispiel handelt, setzt Ihr Befehl einfach nur das Kennwort zurück und fordert den Benutzer bei der Anmeldung zur Änderung des Kennworts auf.</span><span class="sxs-lookup"><span data-stu-id="2ec83-180">Because this is just an example, your command will just reset the password and require the user change the password at logon.</span></span>
<span data-ttu-id="2ec83-181">Wir speichern den Befehl in dem Modul „Contoso_AD_Module“, das Sie im letzten Abschnitt erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="2ec83-181">We will put it in the Contoso_AD_Module module you made in the last section.</span></span>

1. <span data-ttu-id="2ec83-182">Öffnen Sie in der PowerShell ISE die Datei „Contoso_AD_Module.psm1“.</span><span class="sxs-lookup"><span data-stu-id="2ec83-182">In PowerShell ISE, open "Contoso_AD_Module.psm1"</span></span>
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1'
```

2. <span data-ttu-id="2ec83-183">Drücken Sie STRG+J, um das Menü für Codeausschnitte zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-183">Press Crtl+J to open the snippets menu.</span></span>

3. <span data-ttu-id="2ec83-184">Suchen Sie nach „function“, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="2ec83-184">Key down until you find "function" and press enter.</span></span>
<span data-ttu-id="2ec83-185">Dadurch erhalten Sie ein simples Grundgerüst einer Funktion.</span><span class="sxs-lookup"><span data-stu-id="2ec83-185">This puts up a super basic skeleton of a function.</span></span>

4. <span data-ttu-id="2ec83-186">Benennen Sie die Funktion in „Reset-ContosoUserPassword“ um.</span><span class="sxs-lookup"><span data-stu-id="2ec83-186">Rename the function "Reset-ContosoUserPassword".</span></span>  

5. <span data-ttu-id="2ec83-187">Benennen Sie den einen Parameter in „Identity“ um, und löschen Sie den zweiten.</span><span class="sxs-lookup"><span data-stu-id="2ec83-187">Rename one of the parameters "Identity" and delete the second.</span></span>

6. <span data-ttu-id="2ec83-188">Kopieren Sie Folgendes in den Hauptteil der Funktion.</span><span class="sxs-lookup"><span data-stu-id="2ec83-188">Copy the following into the body of the function.</span></span>
```PowerShell
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
```

7. <span data-ttu-id="2ec83-189">Speichern Sie die Datei.</span><span class="sxs-lookup"><span data-stu-id="2ec83-189">Save the file.</span></span>
<span data-ttu-id="2ec83-190">Das Resultat sollte in etwa folgendermaßen aussehen:</span><span class="sxs-lookup"><span data-stu-id="2ec83-190">You should end up with something that looks like this:</span></span>
```PowerShell
function Reset-ContosoUserPassword ($Identity)
{
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
}
```
<span data-ttu-id="2ec83-191">Jetzt können Ihre Benutzer einfach `Reset-ContosoUserPassword` aufrufen und müssen sich nicht die Syntax merken, um inline eine sichere Zeichenfolge zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-191">Now, your users can simply call `Reset-ContosoUserPassword` and not have to remember the syntax to create a secure string inline.</span></span>

## <a name="step-4-edit-the-role-capability-file"></a><span data-ttu-id="2ec83-192">Schritt 4: Bearbeiten Sie die Rollenfunktionsdatei.</span><span class="sxs-lookup"><span data-stu-id="2ec83-192">Step 4: Edit the Role Capability File</span></span>
<span data-ttu-id="2ec83-193">Im Abschnitt [Erstellen von Rollenfunktionen](./role-capabilities.md#role-capability-creation) haben Sie eine leere Rollenfunktionsdatei erstellt.</span><span class="sxs-lookup"><span data-stu-id="2ec83-193">In the [Role Capability Creation](./role-capabilities.md#role-capability-creation) section, you created a blank Role Capability file.</span></span>
<span data-ttu-id="2ec83-194">In diesem Abschnitt werden Sie diese Datei mit Werten füllen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-194">In this section, you will fill in the values in that file.</span></span>

<span data-ttu-id="2ec83-195">Öffnen Sie zunächst die Rollenfunktionsdatei in der PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="2ec83-195">Start by opening the role capability file in PowerShell ISE.</span></span>
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc'
```
<span data-ttu-id="2ec83-196">Aktualisieren Sie die Datei mit folgenden Änderungen:</span><span class="sxs-lookup"><span data-stu-id="2ec83-196">Update the file with the following changes:</span></span>
```PowerShell
# OLD: VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleCmdlets =
    'Unlock-ADAccount',
    'Search-ADAccount',
    'Enable-ADAccount',
    'Disable-ADAccount',
    @{ Name = 'Set-ADUser'; Parameters = @{ Name = 'Title'; ValidateSet = 'Manager', 'Engineer' }},
    @{ Name = 'Add-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}},
    @{ Name = 'Remove-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}}

# OLD: VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleFunctions = 'Reset-ContosoUserPassword'
```

<span data-ttu-id="2ec83-197">In obigem Beispiel gilt es einiges zu beachten:</span><span class="sxs-lookup"><span data-stu-id="2ec83-197">There are a few things to note about the above:</span></span>
1.  <span data-ttu-id="2ec83-198">PowerShell versucht, die Module automatisch zu laden, die für Ihre Rollenfunktion benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="2ec83-198">PowerShell will attempt to auto-load the modules needed for your Role Capability.</span></span>
<span data-ttu-id="2ec83-199">Möglicherweise müssen Sie Modulnamen explizit im Feld „ModulesToImport“ auflisten, wenn Sie feststellen, dass ein Modul nicht automatisch geladen wird.</span><span class="sxs-lookup"><span data-stu-id="2ec83-199">You may need to explicitly list module names in the "ModulesToImport" field if you notice problems with a module not being autoloaded.</span></span>

2.  <span data-ttu-id="2ec83-200">Wenn Sie nicht sicher sind, ob es sich bei einem Befehl um ein Cmdlet oder eine Funktion handelt, führen Sie `Get-Command` aus, und sehen Sie sich den Wert der „CommandType“-Eigenschaft an.</span><span class="sxs-lookup"><span data-stu-id="2ec83-200">If you aren't sure if a command is a cmdlet or a function, run `Get-Command` and look at the "CommandType" property</span></span>

3.  <span data-ttu-id="2ec83-201">Das ValidatePattern-Element ermöglicht die Verwendung eines regulären Ausdrucks, um Parameterargumente einzuschränken, falls zulässige Werte nicht einfach zu definieren sind.</span><span class="sxs-lookup"><span data-stu-id="2ec83-201">The ValidatePattern allows you to use a regular expression to restrict parameter arguments if it is not easy to define a set of allowable values.</span></span>
<span data-ttu-id="2ec83-202">Sie können für einen einzigen Parameter nicht sowohl ValidatePattern als auch ValidateSet definieren.</span><span class="sxs-lookup"><span data-stu-id="2ec83-202">You cannot define both a ValidatePattern and ValidateSet for a single parameter.</span></span>

## <a name="step-5-register-a-new-session-configuration"></a><span data-ttu-id="2ec83-203">Schritt 5: Erstellen und registrieren Sie eine neue Sitzungskonfiguration.</span><span class="sxs-lookup"><span data-stu-id="2ec83-203">Step 5: Register a new Session Configuration</span></span>
<span data-ttu-id="2ec83-204">Als Nächstes erstellen Sie eine neue Sitzungskonfigurationsdatei, die Ihre Rollenfunktion für Mitglieder der AD-Gruppe „JEA_NonAdmin_HelpDesk“ verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="2ec83-204">Next, you will create a new session configuration file that will expose your Role Capability to members of the "JEA_NonAdmin_HelpDesk" AD group.</span></span>

<span data-ttu-id="2ec83-205">Erstellen und öffnen Sie zunächst eine neue leere Sitzungskonfigurationsdatei in der PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="2ec83-205">Start by creating and opening a new blank Session Configuration file in PowerShell ISE.</span></span>
```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
ise "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
<span data-ttu-id="2ec83-206">Ändern Sie die folgenden Felder in der PSSC-Datei.</span><span class="sxs-lookup"><span data-stu-id="2ec83-206">Modify the following fields in the PSSC file.</span></span>
<span data-ttu-id="2ec83-207">Wenn Sie in Ihrer eigenen Umgebung arbeiten, sollten Sie „CONTOSO\JEA_NonAdmins_Helpdesk“ durch Ihre eigene Gruppe ohne Administratorrechte ersetzen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-207">If you are working in your own environment, you should replace "CONTOSO\JEA_NonAdmins_Helpdesk" with your own non-administrator user or group.</span></span>
```PowerShell
# OLD: Description = ''
Description = 'An endpoint for Active Directory tasks.'

# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{ 'CONTOSO\JEA_NonAdmin_HelpDesk' = @{ RoleCapabilities =  'ADHelpDesk' }}
```
<span data-ttu-id="2ec83-208">Speichern und registrieren Sie die Sitzungskonfiguration.</span><span class="sxs-lookup"><span data-stu-id="2ec83-208">Save and register the Session Configuration</span></span>
```PowerShell
Register-PSSessionConfiguration -Name ADHelpDesk -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
## <a name="test-it-out"></a><span data-ttu-id="2ec83-209">Probieren Sie es aus!</span><span class="sxs-lookup"><span data-stu-id="2ec83-209">Test It Out!</span></span>
<span data-ttu-id="2ec83-210">Rufen Sie Ihre Benutzeranmeldeinformationen ohne Administratorrechte ab:</span><span class="sxs-lookup"><span data-stu-id="2ec83-210">Get your non-administrator user credentials:</span></span>
```PowerShell
$HelpDeskCred = Get-Credential
```
<span data-ttu-id="2ec83-211">Wenn Sie den Abschnitt [Set Up Users and Groups](creating-a-domain-controller.md#set-up-users-and-groups) (Einrichten von Benutzern und Gruppen) absolviert haben, lauten die Informationen wie folgt:</span><span class="sxs-lookup"><span data-stu-id="2ec83-211">If you followed the [Set Up Users and Groups](creating-a-domain-controller.md#set-up-users-and-groups) section, the credentials will be:</span></span>
-   <span data-ttu-id="2ec83-212">Benutzername = HelpDeskUser</span><span class="sxs-lookup"><span data-stu-id="2ec83-212">Username = "HelpDeskUser"</span></span>
-   <span data-ttu-id="2ec83-213">Kennwort = pa$$w0rd</span><span class="sxs-lookup"><span data-stu-id="2ec83-213">Password = "pa$$w0rd"</span></span>

<span data-ttu-id="2ec83-214">Stellen Sie eine Remoteverbindung mit dem „ADHelpdesk“ -Endpunkt her, und verwenden Sie dabei diese Anmeldeinformationen ohne Administratorrechte:</span><span class="sxs-lookup"><span data-stu-id="2ec83-214">Remote into the ADHelpdesk endpoint using the non-admin credential:</span></span>
```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName ADHelpDesk -Credential $HelpDeskCred
```
<span data-ttu-id="2ec83-215">Verwenden Sie Set-ADUser, um die Position eines Benutzers zurückzusetzen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-215">Use Set-ADUser to reset a user's title.</span></span>
```PowerShell
Set-ADUser -Identity OperatorUser -Title Engineer
```
<span data-ttu-id="2ec83-216">Überprüfen Sie, ob die Position geändert wurde.</span><span class="sxs-lookup"><span data-stu-id="2ec83-216">Verify that the title has changed.</span></span>
```PowerShell
Get-ADUser -Identity OperatorUser -Property Title
```
<span data-ttu-id="2ec83-217">Verwenden Sie jetzt Add-ADGroupMember, um einen Benutzer zur Gruppe TestGroup hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-217">Now, use Add-ADGroupMember to add a user to the TestGroup.</span></span>
<span data-ttu-id="2ec83-218">Hinweis: Stellen Sie sicher, dass Sie die Gruppe TestGroup zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="2ec83-218">Note: make sure you've created the TestGroup beforehand.</span></span>
```PowerShell
Add-ADGroupMember TestGroup -Member OperatorUser -Verbose
```
<span data-ttu-id="2ec83-219">Beenden Sie die Sitzung:</span><span class="sxs-lookup"><span data-stu-id="2ec83-219">Exit the session:</span></span>
```PowerShell
Exit-PSSession
```
## <a name="key-concepts"></a><span data-ttu-id="2ec83-220">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="2ec83-220">Key Concepts</span></span>
<span data-ttu-id="2ec83-221">**NoLanguage-Modus**: Wenn PowerShell sich im Modus „NoLanguage“ befindet, dürfen Benutzer nur Befehle ausführen und keine Sprachelemente verwenden.</span><span class="sxs-lookup"><span data-stu-id="2ec83-221">**NoLanguage Mode**: When PowerShell is in "NoLanguage" mode, users may only run commands; they cannot use any language elements.</span></span>
<span data-ttu-id="2ec83-222">Wenn Sie hierzu weitere Informationen benötigen, führen Sie `Get-Help about_Language_Modes` aus.</span><span class="sxs-lookup"><span data-stu-id="2ec83-222">For more information, run `Get-Help about_Language_Modes`.</span></span>

<span data-ttu-id="2ec83-223">**PowerShell-Funktionen**: Bei PowerShell-Funktionen handelt es sich um PowerShell-Codeabschnitte, denen Sie einen Namen zuweisen können.</span><span class="sxs-lookup"><span data-stu-id="2ec83-223">**PowerShell Functions**: PowerShell functions are bits of PowerShell code that you can call by name.</span></span>
<span data-ttu-id="2ec83-224">Wenn Sie hierzu weitere Informationen benötigen, führen Sie `Get-Help about_Functions` aus.</span><span class="sxs-lookup"><span data-stu-id="2ec83-224">For more information, run `Get-Help about_Functions`.</span></span>

<span data-ttu-id="2ec83-225">**ValidateSet/ValidatePattern**: Wenn Sie einen Befehl verfügbar machen, können Sie die gültigen Argumente für bestimmte Parameter einschränken.</span><span class="sxs-lookup"><span data-stu-id="2ec83-225">**ValidateSet/ValidatePattern**: When exposing a command, you can restrict valid arguments for specific parameters.</span></span>
<span data-ttu-id="2ec83-226">Ein „ValidateSet“-Element ist eine spezifische Liste gültiger Argumente.</span><span class="sxs-lookup"><span data-stu-id="2ec83-226">A ValidateSet is a specific list of valid arguments.</span></span>
<span data-ttu-id="2ec83-227">Ein ValidatePattern-Element ist ein regulärer Ausdruck, mit dem die Argumente für diesen Parameter übereinstimmen müssen.</span><span class="sxs-lookup"><span data-stu-id="2ec83-227">A ValidatePattern is a regular expression that the arguments for that parameter must match.</span></span>

