---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,security
title: JEA-Rollenfunktionen
ms.openlocfilehash: 10f5f390daccbb012be6ee7272041e777810ee12
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="e6227-103">JEA-Rollenfunktionen</span><span class="sxs-lookup"><span data-stu-id="e6227-103">JEA Role Capabilities</span></span>

> <span data-ttu-id="e6227-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e6227-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="e6227-105">Beim Erstellen eines JEA-Endpunkts müssen Sie eine oder mehrere „Rollenfunktionen“ definieren, die festlegen, *welche Befehle* ein Benutzer in einer JEA-Sitzung ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="e6227-105">When creating a JEA endpoint, you will need to define one or more "role capabilities" which describe *what* someone can do in a JEA session.</span></span>
<span data-ttu-id="e6227-106">Eine Rollenfunktion ist eine PowerShell-Datendatei mit der Erweiterung PSRC. Sie enthält alle Cmdlets, Funktionen, Anbieter und externen Programme für Benutzer, die eine Verbindung herstellen.</span><span class="sxs-lookup"><span data-stu-id="e6227-106">A role capability is a PowerShell data file with the .psrc extension that lists all the cmdlets, functions, providers, and external programs that should be made available to connecting users.</span></span>

<span data-ttu-id="e6227-107">In diesem Thema wird das Erstellen einer PowerShell-Rollenfunktionsdatei für Ihre JEA-Benutzer beschrieben.</span><span class="sxs-lookup"><span data-stu-id="e6227-107">This topic describes how to create a PowerShell role capability file for your JEA users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="e6227-108">Festlegen der zulässigen Befehle</span><span class="sxs-lookup"><span data-stu-id="e6227-108">Determine which commands to allow</span></span>

<span data-ttu-id="e6227-109">Die erste Frage beim Erstellen einer Rollenfunktionsdatei lautet: Welche Zugriffe benötigen Benutzer mit dieser Rolle?</span><span class="sxs-lookup"><span data-stu-id="e6227-109">The first step when creating a role capability file is to consider what the users who are assigned the role will need access to.</span></span>
<span data-ttu-id="e6227-110">Das Sammeln dieser Informationen kann relativ zeitaufwändig sein, aber es ist ein sehr wichtiger Prozess.</span><span class="sxs-lookup"><span data-stu-id="e6227-110">This requirements gathering process can take a while, but it is a very important process.</span></span>
<span data-ttu-id="e6227-111">Benutzer, deren Zugriff auf zu wenige Cmdlets und Funktionen beschränkt ist, können ihre jeweiligen Aufgaben möglicherweise nicht ausführen.</span><span class="sxs-lookup"><span data-stu-id="e6227-111">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span>
<span data-ttu-id="e6227-112">Umgekehrt kann der Zugriff auf zu viele Cmdlets und Funktionen dazu führen, dass Benutzer mithilfe ihrer impliziten Administratorberechtigungen mehr Aktionen ausführen als ursprünglich beabsichtigt und dadurch die Sicherheit beeinträchtigen.</span><span class="sxs-lookup"><span data-stu-id="e6227-112">Allowing access to too many cmdlets and functions can lead to users doing more than you intended with their implicit admin privileges, weakening your security stance.</span></span>

<span data-ttu-id="e6227-113">Der von Ihnen gewählte Prozess ist abhängig von Ihrer Organisation und Ihren Zielen. Die folgenden Tipps sollen Ihnen jedoch auf den richtigen Weg helfen.</span><span class="sxs-lookup"><span data-stu-id="e6227-113">How you go about this process will depend on your organization and goals, however the following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="e6227-114">**Identifizieren** Sie die Befehle, die Benutzer verwenden, um ihre Arbeit zu erledigen.</span><span class="sxs-lookup"><span data-stu-id="e6227-114">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="e6227-115">Dazu müssen Sie möglicherweise IT-Mitarbeiter befragen, Automatisierungsskripts überprüfen oder PowerShell-Sitzungsaufzeichnungen oder -protokolle analysieren.</span><span class="sxs-lookup"><span data-stu-id="e6227-115">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts or logs.</span></span>
2. <span data-ttu-id="e6227-116">**Aktualisieren** Sie, soweit möglich, die Verwendung von Befehlszeilentools auf PowerShell-Entsprechungen, und sorgen Sie dadurch für eine optimale Überwachung und JEA-Anpassungserfahrung.</span><span class="sxs-lookup"><span data-stu-id="e6227-116">**Update** use of command line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="e6227-117">Externe Programme können in JEA nicht so präzise wie native PowerShell-Cmdlets und -Funktionen beschränkt werden.</span><span class="sxs-lookup"><span data-stu-id="e6227-117">External programs cannot be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="e6227-118">**Beschränken** Sie den Gültigkeitsbereich der Cmdlets, falls erforderlich, um nur bestimmte Parameter oder Parameterwerte zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="e6227-118">**Restrict** the scope of the cmdlets if necessary to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="e6227-119">Dies ist besonders wichtig, wenn Benutzer nur Teile eines Systems verwalten sollen.</span><span class="sxs-lookup"><span data-stu-id="e6227-119">This is particularly important if users should only be able to manage part of a system.</span></span>
4. <span data-ttu-id="e6227-120">**Erstellen** Sie benutzerdefinierte Funktionen, um komplexe Befehle zu ersetzen bzw. Befehle, die in JEA nur schwer einzuschränken sind.</span><span class="sxs-lookup"><span data-stu-id="e6227-120">**Create** custom functions to replace complex commands or commands which are difficult to constrain in JEA.</span></span> <span data-ttu-id="e6227-121">Eine einfache Funktion, die einen komplexen Befehl enthält oder zusätzliche Validierungslogik anwendet, bietet Administratoren zusätzliche Kontrolle und sorgt für mehr Benutzerfreundlichkeit bei Endbenutzern.</span><span class="sxs-lookup"><span data-stu-id="e6227-121">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="e6227-122">**Testen** Sie die entsprechende Liste von zulässigen Befehlen mit Ihren Benutzern und/oder Automatisierungsservices, und nehmen Sie bei Bedarf Anpassungen vor.</span><span class="sxs-lookup"><span data-stu-id="e6227-122">**Test** the scoped list of allowable commands with your users and/or automation services and adjust as necessary.</span></span>

<span data-ttu-id="e6227-123">Beachten Sie, dass Befehle in einer JEA-Sitzung häufig mit Administratorberechtigungen (oder anderweitig erhöhten Berechtigungen) ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="e6227-123">It is important to remember that commands in a JEA session are often run with admin (or otherwise elevated) privileges.</span></span>
<span data-ttu-id="e6227-124">Die verfügbaren Befehle sollten sorgfältig ausgewählt werden, um sicherzustellen, dass der JEA-Endpunkt dem Benutzer, der eine Verbindung herstellt, keine Möglichkeit gibt, seine Berechtigungen zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="e6227-124">Careful selection of available commands is important to ensure the JEA endpoint does not allow the connecting user to elevate their permissions.</span></span>
<span data-ttu-id="e6227-125">Im Folgenden finden Sie Beispiele für Befehle, die böswillig verwendet werden können, wenn sie uneingeschränkt zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="e6227-125">Below are some examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span>
<span data-ttu-id="e6227-126">Beachten Sie, dass dies keine vollständige Liste und lediglich als einleitende Vorsichtsmaßnahme gedacht ist.</span><span class="sxs-lookup"><span data-stu-id="e6227-126">Note that this is not an exhaustive list and should only be used as a cautionary starting point.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="e6227-127">Beispiele für potenziell gefährliche Befehle</span><span class="sxs-lookup"><span data-stu-id="e6227-127">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="e6227-128">Risiko</span><span class="sxs-lookup"><span data-stu-id="e6227-128">Risk</span></span> | <span data-ttu-id="e6227-129">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e6227-129">Example</span></span> | <span data-ttu-id="e6227-130">Verwandte Befehle</span><span class="sxs-lookup"><span data-stu-id="e6227-130">Related commands</span></span>
-----|---------|-----------------
<span data-ttu-id="e6227-131">Gewähren von Administratorberechtigungen für Benutzer, die eine Verbindung aufbauen, um JEA zu umgehen</span><span class="sxs-lookup"><span data-stu-id="e6227-131">Granting the connecting user admin privileges to bypass JEA</span></span> | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="e6227-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="e6227-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>
<span data-ttu-id="e6227-133">Ausführen von beliebigem Code, z.B. Malware, Exploits oder benutzerdefinierten Skripts, um Schutzmechanismen zu umgehen</span><span class="sxs-lookup"><span data-stu-id="e6227-133">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'` | <span data-ttu-id="e6227-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="e6227-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span>

## <a name="create-a-role-capability-file"></a><span data-ttu-id="e6227-135">Erstellen einer Rollenfunktionsdatei</span><span class="sxs-lookup"><span data-stu-id="e6227-135">Create a role capability file</span></span>

<span data-ttu-id="e6227-136">Sie können eine neue PowerShell-Rollenfunktionsdatei mit dem [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile)-Cmdlet erstellen.</span><span class="sxs-lookup"><span data-stu-id="e6227-136">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="e6227-137">Die resultierende Rollenfunktionsdatei kann in einem Text-Editor geöffnet und geändert werden, um die gewünschten Befehle für die Rolle zuzulassen.</span><span class="sxs-lookup"><span data-stu-id="e6227-137">The resulting role capability file can be opened in a text editor and modified to allow the desired commands for the role.</span></span>
<span data-ttu-id="e6227-138">Die PowerShell-Hilfedokumentation enthält mehrere Beispiele dafür, wie Sie die Datei konfigurieren können.</span><span class="sxs-lookup"><span data-stu-id="e6227-138">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="e6227-139">Zulassen von PowerShell-Cmdlets und -Funktionen</span><span class="sxs-lookup"><span data-stu-id="e6227-139">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="e6227-140">Fügen Sie den Feldern „VisbibleCmdlets“ oder „VisibleFunctionsCmdlet“ den Cmdlet- oder Funktionsnamen hinzu, um Benutzern das Ausführen von PowerShell-Cmdlets oder -Funktionen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="e6227-140">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisbibleCmdlets or VisibleFunctions fields.</span></span>
<span data-ttu-id="e6227-141">Wenn Sie nicht sicher sind, ob es sich um einen Befehl für ein Cmdlet oder eine Funktion handelt, können Sie `Get-Command <name>` ausführen und die Eigenschaft „CommandType“ in der Ausgabe überprüfen.</span><span class="sxs-lookup"><span data-stu-id="e6227-141">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the "CommandType" property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="e6227-142">Manchmal ist der Gültigkeitsbereich eines bestimmten Cmdlets oder einer Funktion für die Anforderungen Ihrer Benutzer zu weit gefasst.</span><span class="sxs-lookup"><span data-stu-id="e6227-142">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span>
<span data-ttu-id="e6227-143">Ein DNS-Administrator z.B. muss wahrscheinlich nur über Zugriff verfügen, um den DNS-Dienst neu zu starten.</span><span class="sxs-lookup"><span data-stu-id="e6227-143">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span>
<span data-ttu-id="e6227-144">In einer Umgebung mit mehreren Mandanten, die Zugriff auf Self-Service-Managementtools haben, sollte die Verwaltung durch diese Mandanten auf deren eigene Ressourcen beschränkt sein.</span><span class="sxs-lookup"><span data-stu-id="e6227-144">In a multi-tenant environment where tenants are granted access to self-service management tools, tenants should be limited to managing with their own resources.</span></span>
<span data-ttu-id="e6227-145">In einem solchen Fall können Sie festlegen, welche Parameter vom Cmdlet oder der Funktion verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="e6227-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

<span data-ttu-id="e6227-146">In komplexeren Szenarios müssen Sie möglicherweise auch beschränken, welche Werte ein Benutzer für diese Parameter angibt.</span><span class="sxs-lookup"><span data-stu-id="e6227-146">In more advanced scenarios, you may also need to restrict which values someone can supply to these parameters.</span></span>
<span data-ttu-id="e6227-147">Anhand von Rollenfunktionen können Sie einen Satz zulässiger Werte oder das Muster eines regulären Ausdrucks definieren, der bzw. das ausgewertet wird, um festzustellen, ob eine gegebene Eingabe zulässig ist.</span><span class="sxs-lookup"><span data-stu-id="e6227-147">Role capabilities let you define a set of allowed values or a regular expression pattern that is evaluated to determine if a given input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="e6227-148">Die [allgemeinen PowerShell-Parameter](https://technet.microsoft.com/en-us/library/hh847884.aspx) sind immer zulässig, selbst wenn Sie die verfügbaren Parameter beschränken.</span><span class="sxs-lookup"><span data-stu-id="e6227-148">The [common PowerShell parameters](https://technet.microsoft.com/en-us/library/hh847884.aspx) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="e6227-149">Sie brauchen sie nicht explizit im Parameter-Feld aufzuführen.</span><span class="sxs-lookup"><span data-stu-id="e6227-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="e6227-150">Die folgende Tabelle beschreibt die verschiedenen Methoden, mit denen Sie ein sichtbares Cmdlet bzw. eine sichtbare Funktion anpassen können.</span><span class="sxs-lookup"><span data-stu-id="e6227-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="e6227-151">Sie können alle unten aufgeführten Cmdlets und Funktionen im VisibleCmdlets-Feld frei miteinander kombinieren.</span><span class="sxs-lookup"><span data-stu-id="e6227-151">You can mix and match any of the below in the VisibleCmdlets field.</span></span>

<span data-ttu-id="e6227-152">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e6227-152">Example</span></span>                                                                                      | <span data-ttu-id="e6227-153">Anwendungsfall</span><span class="sxs-lookup"><span data-stu-id="e6227-153">Use case</span></span>
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="e6227-154">`'My-Func'` oder `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="e6227-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                       | <span data-ttu-id="e6227-155">Ermöglicht dem Benutzer das Ausführen von `My-Func` ohne jegliche Einschränkungen bei den Parametern</span><span class="sxs-lookup"><span data-stu-id="e6227-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>
`'MyModule\My-Func'`                                                                         | <span data-ttu-id="e6227-156">Ermöglicht dem Benutzer das Ausführen von `My-Func` vom Modul `MyModule` ohne jegliche Einschränkungen bei den Parametern</span><span class="sxs-lookup"><span data-stu-id="e6227-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>
`'My-*'`                                                                                     | <span data-ttu-id="e6227-157">Ermöglicht dem Benutzer das Ausführen eines beliebigen Cmdlets oder einer beliebigen Funktion mit dem Verb `My`</span><span class="sxs-lookup"><span data-stu-id="e6227-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>
`'*-Func'`                                                                                   | <span data-ttu-id="e6227-158">Ermöglicht dem Benutzer das Ausführen eines beliebigen Cmdlets oder einer beliebigen Funktion mit dem Namen `Func`</span><span class="sxs-lookup"><span data-stu-id="e6227-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | <span data-ttu-id="e6227-159">Ermöglicht dem Benutzer das Ausführen von `My-Func` mit den Parametern `Param1` und/oder `Param2`</span><span class="sxs-lookup"><span data-stu-id="e6227-159">Allows the user to run `My-Func` with the `Param1` and/or `Param2` parameters.</span></span> <span data-ttu-id="e6227-160">Für die Parameter kann ein beliebiger Wert angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="e6227-160">Any value can be supplied to the parameters.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | <span data-ttu-id="e6227-161">Ermöglicht dem Benutzer das Ausführen von `My-Func` mit dem Parameter `Param1`.</span><span class="sxs-lookup"><span data-stu-id="e6227-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="e6227-162">Für den Parameter kann nur „Value1“ und „Value2“ angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="e6227-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | <span data-ttu-id="e6227-163">Ermöglicht dem Benutzer das Ausführen von `My-Func` mit dem Parameter `Param1`.</span><span class="sxs-lookup"><span data-stu-id="e6227-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="e6227-164">Für den Parameter kann ein beliebiger Wert, beginnend mit „Contoso“, angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="e6227-164">Any value starting with "contoso" can be supplied to the parameter.</span></span>


> [!WARNING]
> <span data-ttu-id="e6227-165">Bewährten Sicherheitsmaßnahmen zufolge wird bei der Definition sichtbarer Cmdlets und Funktionen empfohlen, keine Platzhalter zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e6227-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span>
> <span data-ttu-id="e6227-166">Stattdessen sollten Sie jeden vertrauenswürdigen Befehl einzeln aufführen, um sicherzustellen, dass Befehle, die dem gleichen Namensschema folgen, nicht unbeabsichtigt autorisiert werden.</span><span class="sxs-lookup"><span data-stu-id="e6227-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="e6227-167">Sie können nicht gleichzeitig ein ValidatePattern- und ein ValidateSet-Attribut auf das gleiche Cmdlet oder die gleiche Funktion anwenden.</span><span class="sxs-lookup"><span data-stu-id="e6227-167">You cannot apply both a ValidatePattern and ValidateSet to the same cmdlet or function.</span></span>

<span data-ttu-id="e6227-168">Andernfalls wird das ValidateSet-Attribut vom ValidatePattern-Attribut überschrieben.</span><span class="sxs-lookup"><span data-stu-id="e6227-168">If you do, the ValidatePattern will override the ValidateSet.</span></span>

<span data-ttu-id="e6227-169">Weitere Informationen zum ValidatePattern-Attribut finden Sie unter [dem englischsprachigen Blogbeitrag *Hey, Scripting Guy!*](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) und dem Referenzmaterial [PowerShell Regular Expressions (Reguläre Ausdrücke in PowerShell)](https://technet.microsoft.com/en-us/library/hh847880.aspx).</span><span class="sxs-lookup"><span data-stu-id="e6227-169">For more information about ValidatePattern, check out [this *Hey, Scripting Guy!* post](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](https://technet.microsoft.com/en-us/library/hh847880.aspx) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="e6227-170">Zulassen von externen Befehlen und PowerShell-Skripts</span><span class="sxs-lookup"><span data-stu-id="e6227-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="e6227-171">Um Benutzern das Ausführen von ausführbaren Dateien und PowerShell-Skripts (.ps1) in einer JEA-Sitzung zu ermöglichen, müssen Sie den vollständigen Pfad zu jedem einzelnen Programm im Feld „VisibleExternalCommands“ hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e6227-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the VisibleExternalCommands field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="e6227-172">Es wird empfohlen, möglichst mit den PowerShell-Cmdlet- bzw. -Funktionsentsprechungen der von Ihnen autorisierten, ausführbaren Dateien zu arbeiten, da Sie bestimmen können, welche Parameter für PowerShell-Cmdlets bzw. -Funktionen zulässig sind.</span><span class="sxs-lookup"><span data-stu-id="e6227-172">It is advised, where possible, to use PowerShell cmdlet/function equivalents of any external executables you authorize since you have control over which parameters are allowed with PowerShell cmdlets/functions.</span></span>

<span data-ttu-id="e6227-173">Mithilfe vieler ausführbarer Dateien können Sie den aktuellen Status lesen und ändern, indem Sie einfach unterschiedliche Parameter angeben.</span><span class="sxs-lookup"><span data-stu-id="e6227-173">Many executables allow you to both read the current state and then change it just by providing different parameters.</span></span>

<span data-ttu-id="e6227-174">Betrachten Sie z.B. die Rolle eines Dateiserveradministrators, der überprüfen möchte, welche Netzwerkfreigaben auf dem lokalen Computer gehostet werden.</span><span class="sxs-lookup"><span data-stu-id="e6227-174">For example, consider the role of a file server admin who wants to check which network shares are hosted by the local machine.</span></span>
<span data-ttu-id="e6227-175">Eine Möglichkeit der Überprüfung besteht in der Verwendung von `net share`.</span><span class="sxs-lookup"><span data-stu-id="e6227-175">One way to check is to use `net share`.</span></span>
<span data-ttu-id="e6227-176">Die Verwendung von „net.exe“ ist allerdings mit Gefahren verbunden, denn der Administrator könnte den Befehl auch problemlos nutzen, um sich mithilfe von `net group Administrators unprivilegedjeauser /add` Administratorberechtigungen zu verschaffen.</span><span class="sxs-lookup"><span data-stu-id="e6227-176">However, allowing net.exe is very dangerous becuase the admin could just as easily use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span>
<span data-ttu-id="e6227-177">Eine bessere Lösung ist die Verwendung von [Get-SmbShare](https://technet.microsoft.com/en-us/library/jj635704.aspx). Dieses Cmdlet sorgt für das gleiche Ergebnis, verfügt jedoch über einen weitaus eingeschränkteren Geltungsbereich.</span><span class="sxs-lookup"><span data-stu-id="e6227-177">A better approach is to allow [Get-SmbShare](https://technet.microsoft.com/en-us/library/jj635704.aspx) which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="e6227-178">Wenn Sie Benutzern in einer JEA-Sitzung externe Befehle zur Verfügung stellen, geben Sie immer den vollständigen Pfad zur ausführbaren Datei an, um sicherzustellen, dass kein (potenziell bösartiges) Programm mit ähnlichem Namen an anderer Stelle im System ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e6227-178">When making external commands available to users in a JEA session, always specify the complete path to the executable to ensure a similarly named (and potentially malicous) program placed elsewhere on the system does not get executed instead.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="e6227-179">Zulassen von Zugriffssteuerung für PowerShell-Anbieter</span><span class="sxs-lookup"><span data-stu-id="e6227-179">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="e6227-180">Standardmäßig sind in JEA-Sitzungen keine PowerShell-Anbieter verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e6227-180">By default, no PowerShell providers are available in JEA sessions.</span></span>

<span data-ttu-id="e6227-181">Dies geschieht in erster Linie, um zu verhindern, dass vertrauliche Informationen und Konfigurationseinstellungen an Benutzer weitergegeben werden, die eine Verbindung herstellen.</span><span class="sxs-lookup"><span data-stu-id="e6227-181">This is primarily to reduce the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="e6227-182">Bei Bedarf können Sie den Zugriff auf die PowerShell-Anbieter über den Befehl `VisibleProviders` ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="e6227-182">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span>
<span data-ttu-id="e6227-183">Sie erhalten eine vollständige Liste aller Anbieter, indem Sie `Get-PSProvider` ausführen.</span><span class="sxs-lookup"><span data-stu-id="e6227-183">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="e6227-184">Für einfache Aufgaben, die Zugriff auf das Dateisystem, die Registrierung, den Zertifikatspeicher oder andere vertrauliche Anbieter voraussetzen, können Sie auch eine benutzerdefinierte Funktion in Erwägung ziehen, die einen Zugriff auf den Anbieter im Auftrag des Benutzers ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="e6227-184">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, you can also consider writing a custom function that works with the provider on the user's behalf.</span></span>
<span data-ttu-id="e6227-185">Funktionen, Cmdlets und externe Programme, die in einer JEA-Sitzung verfügbar sind, unterliegen nicht den gleichen Einschränkungen wie JEA – sie können standardmäßig auf alle Anbieter zugreifen.</span><span class="sxs-lookup"><span data-stu-id="e6227-185">Functions, cmdlets, and external programs that are available in a JEA session are not subject to the same constraints as JEA -- they can access any provider by default.</span></span>
<span data-ttu-id="e6227-186">Sie können auch das [Benutzerlaufwerk](session-configurations.md#user-drive) verwenden, wenn Sie Dateien auf einen bzw. von einem JEA-Endpunkt kopieren müssen.</span><span class="sxs-lookup"><span data-stu-id="e6227-186">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to/from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="e6227-187">Erstellen von benutzerdefinierten Funktionen</span><span class="sxs-lookup"><span data-stu-id="e6227-187">Creating custom functions</span></span>

<span data-ttu-id="e6227-188">Sie können benutzerdefinierte Funktionen in einer Rollenfunktionsdatei erstellen, um komplexe Aufgaben für Ihre Endbenutzer zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="e6227-188">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span>
<span data-ttu-id="e6227-189">Benutzerdefinierte Funktionen erweisen sich als nützlich, wenn für Cmdlet-Parameterwerte eine erweiterte Validierungslogik erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="e6227-189">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span>
<span data-ttu-id="e6227-190">Sie können einfache Funktionen in das Feld **FunctionDefinitions** schreiben:</span><span class="sxs-lookup"><span data-stu-id="e6227-190">You can write simple functions in the **FunctionDefinitions** field:</span></span>

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="e6227-191">Vergessen Sie nicht, den Namen der benutzerdefinierten Funktionen im Feld **VisibleFunctions** hinzuzufügen, damit sie von den JEA-Benutzern ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="e6227-191">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>


<span data-ttu-id="e6227-192">Textkörper (Skriptblöcke) von benutzerdefinierten Funktionen werden im Standardsprachmodus für das System ausgeführt und unterliegen nicht den JEA-Spracheinschränkungen.</span><span class="sxs-lookup"><span data-stu-id="e6227-192">The body (script block) of custom functions runs in the default language mode for the system and is not subject to JEA's language constraints.</span></span>
<span data-ttu-id="e6227-193">Dies bedeutet, dass Funktionen Zugriff auf das Dateisystem und die Registrierung haben und Befehle ausführen können, die in der Rollenfunktionsdatei nicht sichtbar gemacht wurden.</span><span class="sxs-lookup"><span data-stu-id="e6227-193">This means that functions can access the file system and registry, and run commands that were not made visible in the role capability file.</span></span>
<span data-ttu-id="e6227-194">Achten Sie darauf, dass kein beliebiger Code ausgeführt wird, wenn Sie Parameter verwenden. Vermeiden Sie außerdem das direkte Weiterreichen von Benutzereingaben in Cmdlets wie `Invoke-Expression`.</span><span class="sxs-lookup"><span data-stu-id="e6227-194">Take care to avoid allowing arbitrary code to be run when using parameters and avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="e6227-195">Im obigen Beispiel sehen Sie, dass der vollqualifizierte Modulname (FQMN) `Microsoft.PowerShell.Utility\Select-Object` verwendet wurde anstelle der Kurzschreibweise `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="e6227-195">In the above example, you will notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="e6227-196">Funktionen, die in Rollenfunktionsdateien definiert werden, unterliegen weiterhin dem Gültigkeitsbereich von JEA-Sitzungen. Darunter fallen auch die Proxyfunktionen, die JEA erstellt, um vorhandene Befehle einzuschränken.</span><span class="sxs-lookup"><span data-stu-id="e6227-196">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="e6227-197">„Select-Object“ ist ein standardmäßiges, eingeschränktes Cmdlet in allen JEA-Sitzungen, das eine Auswahl beliebiger Eigenschaften auf Objekten nicht zulässt.</span><span class="sxs-lookup"><span data-stu-id="e6227-197">Select-Object is a default, constrained cmdlet in all JEA sessions that doesn't allow you to select arbitrary properties on objects.</span></span>
<span data-ttu-id="e6227-198">Um das uneingeschränkte Select-Object-Cmdlet in Funktionen verwenden zu können, müssen Sie die vollständige Implementierung explizit durch Angabe der FQMN anfordern.</span><span class="sxs-lookup"><span data-stu-id="e6227-198">To use the unconstrained Select-Object in functions, you must explicitly request the full implementation by specifying the FQMN.</span></span>
<span data-ttu-id="e6227-199">Alle eingeschränkten Cmdlets in einer JEA-Sitzung weisen das gleiche Verhalten auf, wenn sie über eine Funktion aufgerufen werden. Dabei folgen sie der PowerShell-[Rangfolge von Befehlen](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span><span class="sxs-lookup"><span data-stu-id="e6227-199">Any constrained cmdlet in a JEA session will exhibit the same behavior when invoked from a function, in line with PowerShell's [command precedence](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="e6227-200">Wenn Sie viele benutzerdefinierte Funktionen schreiben, ist es möglicherweise einfacher, diese in einem [PowerShell-Skriptmodul](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx) zu speichern.</span><span class="sxs-lookup"><span data-stu-id="e6227-200">If you are writing a lot of custom functions, it may be easier to put them in a [PowerShell Script Module](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).</span></span>
<span data-ttu-id="e6227-201">Sie können diese Funktionen anschließend in der JEA-Sitzung mithilfe des VisibleFunctions-Felds genauso sichtbar machen wie integrierte und Drittanbietermodule.</span><span class="sxs-lookup"><span data-stu-id="e6227-201">You can then make those functions visible in the JEA session using the VisibleFunctions field like you would with built-in and third party modules.</span></span>

## <a name="place-role-capabilities-in-a-module"></a><span data-ttu-id="e6227-202">Platzieren von Rollenfunktionen in einem Modul</span><span class="sxs-lookup"><span data-stu-id="e6227-202">Place role capabilities in a module</span></span>

<span data-ttu-id="e6227-203">Damit PowerShell eine Rollenfunktionsdatei erkennen kann, müssen Sie diese in einem Ordner „RoleCapabilities“ in einem PowerShell-Modul speichern.</span><span class="sxs-lookup"><span data-stu-id="e6227-203">In order for PowerShell to find a role capability file, it must be stored in a "RoleCapabilities" folder in a PowerShell module.</span></span>
<span data-ttu-id="e6227-204">Das Modul kann in einem beliebigen Ordner gespeichert werden, der in der Umgebungsvariable `$env:PSModulePath` enthalten ist. Sie sollten das Modul jedoch nicht unter dem Ordner „System32“ (reserviert für integrierte Module) oder in einen Ordner einfügen, dessen Dateien von nicht vertrauenswürdigen Benutzern geändert werden können, die eine Verbindung herstellen.</span><span class="sxs-lookup"><span data-stu-id="e6227-204">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you should not place it in System32 (reserved for built-in modules) or a folder where the untrusted, connecting users could modify the files.</span></span>
<span data-ttu-id="e6227-205">Im Folgenden finden Sie ein Beispiel für das Erstellen eines grundlegenden PowerShell-Skripts mit dem Namen *ContosoJEA* im Pfad „Programme“.</span><span class="sxs-lookup"><span data-stu-id="e6227-205">Below is an example of creating a basic PowerShell script module called *ContosoJEA* in the "Program Files" path.</span></span>

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

<span data-ttu-id="e6227-206">Weitere Informationen zu PowerShell-Modulen, Modulmanifeste und die Umgebungsvariable „PSModulePath“ finden Sie unter [Understanding a PowerShell Module (Grundlegendes zu PowerShell-Modulen)](https://msdn.microsoft.com/en-us/library/dd878324.aspx).</span><span class="sxs-lookup"><span data-stu-id="e6227-206">See [Understanding a PowerShell Module](https://msdn.microsoft.com/en-us/library/dd878324.aspx) for more information about PowerShell modules, module manifests, and the PSModulePath environment variable.</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="e6227-207">Aktualisieren von Rollenfunktionen</span><span class="sxs-lookup"><span data-stu-id="e6227-207">Updating role capabilities</span></span>


<span data-ttu-id="e6227-208">Sie können eine Rollenfunktionsdatei jederzeit aktualisieren, indem Sie einfach Änderungen an der Rollenfunktionsdatei speichern.</span><span class="sxs-lookup"><span data-stu-id="e6227-208">You can update a role capability file at any time by simply saving changes to the role capability file.</span></span>
<span data-ttu-id="e6227-209">Jede neue JEA-Sitzung, die nach dem Aktualisieren der Rollenfunktion gestartet wird, enthält die überarbeiteten Funktionen.</span><span class="sxs-lookup"><span data-stu-id="e6227-209">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="e6227-210">Aus diesem Grund ist es so wichtig, den Zugriff auf den Rollenfunktionsordner genau zu steuern.</span><span class="sxs-lookup"><span data-stu-id="e6227-210">This is why controlling access to the role capabilities folder is so important.</span></span>
<span data-ttu-id="e6227-211">Nur sehr vertrauenswürdige Administratoren sollten Rollenfunktionsdateien ändern können.</span><span class="sxs-lookup"><span data-stu-id="e6227-211">Only highly trusted administrators should be able to change role capability files.</span></span>
<span data-ttu-id="e6227-212">Wenn nicht vertrauenswürdige Benutzer berechtigt sind, Rollenfunktionsdateien zu ändern, können sie sich leicht selbst Zugriff auf Cmdlets verschaffen und damit ihre eigenen Berechtigungen erhöhen.</span><span class="sxs-lookup"><span data-stu-id="e6227-212">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets which allow them to elevate their privileges.</span></span>


<span data-ttu-id="e6227-213">Administratoren, die den Zugriff auf die Rollenfunktionen einschränken möchten, müssen sicherstellen, dass das lokale System über Lesezugriff auf die Rollenfunktionsdateien und die darin enthaltenen Module verfügt.</span><span class="sxs-lookup"><span data-stu-id="e6227-213">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="e6227-214">Zusammenführung von Rollenfunktionen</span><span class="sxs-lookup"><span data-stu-id="e6227-214">How role capabilities are merged</span></span>

<span data-ttu-id="e6227-215">Benutzer können Zugriff auf mehrere Rollenfunktionen erhalten, wenn sie eine JEA-Sitzung beginnen, abhängig von den Rollenzuordnungen in der [Sitzungskonfigurationsdatei](session-configurations.md).</span><span class="sxs-lookup"><span data-stu-id="e6227-215">Users can be granted access to multiple role capabilities when they enter a JEA session depending on the role mappings in the [session configuration file](session-configurations.md).</span></span>
<span data-ttu-id="e6227-216">In diesem Fall versucht JEA, den Benutzern den Satz von Befehlen mit den *höchsten Berechtigungen* zur Verfügung zu stellen, die für die Rollen zulässig sind.</span><span class="sxs-lookup"><span data-stu-id="e6227-216">When this happens, JEA tries to give the user the *most permissive* set of commands allowed by any of the roles.</span></span>

<span data-ttu-id="e6227-217">**VisibleCmdlets und VisibleFunctions**</span><span class="sxs-lookup"><span data-stu-id="e6227-217">**VisibleCmdlets and VisibleFunctions**</span></span>

<span data-ttu-id="e6227-218">Die komplexe Zusammenführungslogik wirkt sich auf Cmdlets und Funktionen aus, deren Parameter und Parameterwerte in JEA eingeschränkt sein können.</span><span class="sxs-lookup"><span data-stu-id="e6227-218">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="e6227-219">Die folgenden Regeln gelten:</span><span class="sxs-lookup"><span data-stu-id="e6227-219">The rules are as follows:</span></span>

1. <span data-ttu-id="e6227-220">Wenn ein Cmdlet nur in einer Rolle sichtbar gemacht wird, ist es für Benutzer mit beliebigen Parametereinschränkungen sichtbar.</span><span class="sxs-lookup"><span data-stu-id="e6227-220">If a cmdlet is only made visible in one role, it will be visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="e6227-221">Wenn ein Cmdlet in mehr als einer Rolle sichtbar gemacht wird und jede Rolle über dieselben Einschränkungen für das Cmdlet verfügt, ist das Cmdlet für Benutzer mit diesen Einschränkungen sichtbar.</span><span class="sxs-lookup"><span data-stu-id="e6227-221">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet will be visible to the user with those constraints.</span></span>
3. <span data-ttu-id="e6227-222">Wenn ein Cmdlet in mehr als einer Rolle sichtbar gemacht wird und jede Rolle einen anderen Satz von Parametern zulässt, sind das Cmdlet und alle für jede Rolle definierten Parameter für die Benutzer sichtbar.</span><span class="sxs-lookup"><span data-stu-id="e6227-222">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all of the parameters defined across every role will be visible to the user.</span></span> <span data-ttu-id="e6227-223">Wenn für eine Rolle keine Einschränkungen für die Parameter gelten, sind alle Parameter zulässig.</span><span class="sxs-lookup"><span data-stu-id="e6227-223">If one role doesn't have constraints on the parameters, all parameters will be allowed.</span></span>
4. <span data-ttu-id="e6227-224">Wenn eine Rolle ein ValidateSet- oder ein ValidatePattern-Attribut für einen Cmdlet-Parameter definiert und die andere Rolle den Parameter zwar zulässt, aber die Parameterwerte nicht einschränkt, werden das ValidateSet- bzw. das ValidatePattern-Attribut ignoriert.</span><span class="sxs-lookup"><span data-stu-id="e6227-224">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern will be ignored.</span></span>
5. <span data-ttu-id="e6227-225">Wenn für den gleichen Cmdlet-Parameter in mehr als einer Rolle ein ValidateSet-Attribut definiert ist, sind alle Werte aller ValidateSet-Attribute zulässig.</span><span class="sxs-lookup"><span data-stu-id="e6227-225">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets will be allowed.</span></span>
6. <span data-ttu-id="e6227-226">Wenn für den gleichen Cmdlet-Parameter in mehr als einer Rolle ein ValidatePattern-Attribut definiert ist, sind alle Werte, die einem beliebigen ValidatePattern-Attribut entsprechen, zulässig.</span><span class="sxs-lookup"><span data-stu-id="e6227-226">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns will be allowed.</span></span>
7. <span data-ttu-id="e6227-227">Wenn ein ValidateSet-Attribut in einer oder mehreren Rollen definiert ist und ein ValidatePattern-Attribut in einer anderen Rolle für den gleichen Cmdlet-Parameter definiert ist,wird das ValidateSet-Attribut ignoriert und für die übrigen ValidatePattern-Attribute gilt Regel 6.</span><span class="sxs-lookup"><span data-stu-id="e6227-227">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="e6227-228">Das nachstehende Beispiel zeigt, wie Rollen gemäß geltenden Regeln zusammengeführt werden:</span><span class="sxs-lookup"><span data-stu-id="e6227-228">Below is an example of how roles are merged according to these rules:</span></span>

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permisisons for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored becuase of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```



<span data-ttu-id="e6227-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span><span class="sxs-lookup"><span data-stu-id="e6227-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span></span>

<span data-ttu-id="e6227-230">Alle anderen Felder in der Rollenfunktionsdatei werden einfach einem kumulativen Satz von zulässigen externen Befehlen, Aliasen, Anbietern und Startskripts hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e6227-230">All other fields in the role capability file are simply added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span>
<span data-ttu-id="e6227-231">Alle in einer Rollenfunktion verfügbaren Befehle, Aliase, Anbieter oder Skripts sind für JEA-Benutzer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e6227-231">Any command, alias, provider, or script available in one role capability will be available to the JEA user.</span></span>

<span data-ttu-id="e6227-232">Achten Sie darauf, dass die kombinierte Gruppe der Anbieter einer Rollenfunktion und der Anbieter von Cmdlets/Funktionen/Befehlen einer anderen Rollenfunktion den Benutzern, die eine Verbindung herstellen, keinen unbeabsichtigten Zugriff auf Systemressourcen gibt.</span><span class="sxs-lookup"><span data-stu-id="e6227-232">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another do not allow connecting users unintentional access to system resources.</span></span>
<span data-ttu-id="e6227-233">Wenn eine Rolle z.B. das `Remove-Item`-Cmdlet zulässt und eine andere den `FileSystem`-Anbieter, besteht die Gefahr, dass ein JEA-Benutzer beliebige Dateien auf Ihrem Computer löscht.</span><span class="sxs-lookup"><span data-stu-id="e6227-233">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span>
<span data-ttu-id="e6227-234">Weitere Informationen dazu, wie die geltenden Berechtigungen von Benutzern ermittelt werden können, finden Sie im Thema [Auditing and Reporting on JEA (Überprüfen und Erstellen von Berichten mit JEA)](audit-and-report.md).</span><span class="sxs-lookup"><span data-stu-id="e6227-234">Additional information about identifying users' effective permissions can be found in the [auditing JEA topic](audit-and-report.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e6227-235">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="e6227-235">Next steps</span></span>

- [<span data-ttu-id="e6227-236">Create a session configuration file (Erstellen einer Sitzungskonfigurationsdatei)</span><span class="sxs-lookup"><span data-stu-id="e6227-236">Create a session configuration file</span></span>](session-configurations.md)

