---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Verwenden von JEA
ms.openlocfilehash: 912e7a3c46be40ff5b5dfa37fe92b67bab5f98dc
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995427"
---
# <a name="using-jea"></a><span data-ttu-id="ed2f2-103">Verwenden von JEA</span><span class="sxs-lookup"><span data-stu-id="ed2f2-103">Using JEA</span></span>

<span data-ttu-id="ed2f2-104">In diesem Artikel werden die verschiedenen Möglichkeiten beschrieben, um eine Verbindung mit einem JEA-Endpunkt herzustellen und ihn zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-104">This article describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="ed2f2-105">Interaktives Verwenden von JEA</span><span class="sxs-lookup"><span data-stu-id="ed2f2-105">Using JEA interactively</span></span>

<span data-ttu-id="ed2f2-106">Wenn Sie Ihre JEA-Konfiguration testen oder über einfache Aufgaben für Benutzer verfügen, können Sie JEA wie eine normale PowerShell-Remotingsitzung verwenden.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-106">If you're testing your JEA configuration or have simple tasks for users, you can use JEA the same way you would a regular PowerShell remoting session.</span></span> <span data-ttu-id="ed2f2-107">Für komplexe Remotingaufgaben wird das [implizite Remoting](#using-jea-with-implicit-remoting) empfohlen.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-107">For complex remoting tasks, it's recommended to use [implicit remoting](#using-jea-with-implicit-remoting).</span></span> <span data-ttu-id="ed2f2-108">Damit können Benutzer die Datenobjekte lokal ausführen.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-108">Implicit remoting allows users to operate with the data objects locally.</span></span>

<span data-ttu-id="ed2f2-109">Wenn Sie JEA interaktiv verwenden möchten, benötigen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="ed2f2-109">To use JEA interactively, you need:</span></span>

- <span data-ttu-id="ed2f2-110">Name des Computers, mit dem Sie eine Verbindung herstellen (möglicherweise der lokale Computer)</span><span class="sxs-lookup"><span data-stu-id="ed2f2-110">The name of the computer you're connecting to (can be the local machine)</span></span>
- <span data-ttu-id="ed2f2-111">der Name des auf diesem Computer registrierten JEA-Endpunkts</span><span class="sxs-lookup"><span data-stu-id="ed2f2-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="ed2f2-112">Anmeldeinformationen mit Zugriff auf den JEA-Endpunkt auf diesem Computer</span><span class="sxs-lookup"><span data-stu-id="ed2f2-112">Credentials that have access to the JEA endpoint on that computer</span></span>

<span data-ttu-id="ed2f2-113">Anhand dieser Informationen können Sie eine JEA-Sitzung über die Cmdlets [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) oder [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) starten.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-113">Given that information, you can start a JEA session using the [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="ed2f2-114">Wenn das aktuelle Benutzerkonto Zugriff auf den JEA-Endpunkt besitzt, können Sie den Parameter **Credential** auslassen.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-114">If the current user account has access to the JEA endpoint, you can omit the **Credential** parameter.</span></span>

<span data-ttu-id="ed2f2-115">Wenn sich die PowerShell-Aufforderung in `[localhost]: PS>` ändert, wissen Sie, dass Sie ab jetzt mit der JEA-Remotesitzung interagieren.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-115">When the PowerShell prompt changes to `[localhost]: PS>` you know that you're now interacting with the remote JEA session.</span></span> <span data-ttu-id="ed2f2-116">Sie können `Get-Command` ausführen, um zu überprüfen, welche Befehle verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-116">You can run `Get-Command` to check which commands are available.</span></span> <span data-ttu-id="ed2f2-117">Wenden Sie sich an Ihren Administrator, um zu erfahren, ob für die verfügbaren Parameter oder zulässigen Parameterwerte Einschränkungen gelten.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-117">Consult with your administrator to learn if there are any restrictions on the available parameters or allowed parameter values.</span></span>

<span data-ttu-id="ed2f2-118">Bedenken Sie, dass JEA-Sitzungen im Modus „NoLanguage“ ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-118">Remember, JEA sessions operate in NoLanguage mode.</span></span> <span data-ttu-id="ed2f2-119">Einige ihrer üblichen Verwendungsmöglichkeiten in PowerShell sind möglicherweise nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-119">Some of the ways you typically use PowerShell may not be available.</span></span> <span data-ttu-id="ed2f2-120">Beispielsweise können Sie keine Variablen zum Speichern von Daten nutzen oder die Eigenschaften der von Cmdlets zurückgegebenen Objekte überprüfen.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-120">For instance, you can't use variables to store data or inspect the properties on objects returned from cmdlets.</span></span> <span data-ttu-id="ed2f2-121">Das folgende Beispiel enthält zwei Ansätze für die Ausführung derselben Befehle im Modus „NoLanguage“:</span><span class="sxs-lookup"><span data-stu-id="ed2f2-121">The following example shows two approaches to get the same commands to work in NoLanguage mode.</span></span>

```powershell
# Using variables is prohibited in NoLanguage mode. The following will not work:
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# You can also use parameter sets that don't require extra data to be passed in
Start-VM -VMName 'SQL01'
```

<span data-ttu-id="ed2f2-122">Für komplexere Befehlsaufrufe, die mit diesem Ansatz nur schwer möglich sind, sollten Sie [implizites Remoting](#using-jea-with-implicit-remoting) oder das [Erstellen von benutzerdefinierten Funktionen](role-capabilities.md#creating-custom-functions) in Erwägung ziehen, um die benötigten Funktionen nutzen zu können.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-122">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you require.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="ed2f2-123">Verwenden von JEA mit implizitem Remoting</span><span class="sxs-lookup"><span data-stu-id="ed2f2-123">Using JEA with implicit remoting</span></span>

<span data-ttu-id="ed2f2-124">PowerShell bietet ein implizites Remotingmodell, bei dem Sie Proxy-Cmdlets von einem Remotecomputer importieren und damit interagieren können, als wären es lokale Befehle.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-124">PowerShell has an implicit remoting model that lets you import proxy cmdlets from a remote machine and interact with them as if they were local commands.</span></span> <span data-ttu-id="ed2f2-125">Weitere Informationen zum impliziten Remoting finden Sie in diesem **Blogbeitrag** von</span><span class="sxs-lookup"><span data-stu-id="ed2f2-125">Implicit remoting is explained in this **Hey, Scripting Guy!**</span></span> <span data-ttu-id="ed2f2-126">[Hey, Scripting Guy!](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="ed2f2-126">[blog post](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="ed2f2-127">Implizites Remoting ist für die Arbeit mit JEA geeignet, da Sie auf diese Weise mit JEA-Cmdlets im Modus „FullLanguage“ arbeiten können.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-127">Implicit remoting is useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span> <span data-ttu-id="ed2f2-128">Dabei können Sie die Vervollständigung mit der TAB-TASTE und Variablen nutzen, Objekte bearbeiten und sogar lokale Skripts verwenden, um Aufgaben für einen JEA-Endpunkt zu automatisieren.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-128">You can use tab completion, variables, manipulate objects, and even use local scripts to automate tasks against a JEA endpoint.</span></span> <span data-ttu-id="ed2f2-129">Jedes Mal, wenn Sie einen Proxybefehl aufrufen, werden die Daten an den JEA-Endpunkt auf dem Remotecomputer gesendet und dort ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-129">Anytime you invoke a proxy command, the data is sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="ed2f2-130">Mithilfe von implizitem Remoting können Sie Cmdlets aus einer vorhandenen PowerShell-Sitzung importieren.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-130">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span> <span data-ttu-id="ed2f2-131">Sie können optional den Namen der einzelnen Proxy-Cmdlets eine Zeichenfolge Ihrer Wahl vorausstellen.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-131">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing.</span></span> <span data-ttu-id="ed2f2-132">Mit diesem Präfix können Sie die Befehle hervorheben, die zum Remotesystem gehören.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-132">The prefix allows you to distinguish the commands that are for the remote system.</span></span> <span data-ttu-id="ed2f2-133">Ein temporäres Skriptmodul mit allen Proxybefehlen wird erstellt und für die Dauer Ihrer lokalen PowerShell-Sitzung importiert.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-133">A temporary script module containing all the proxy commands is created and imported for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="ed2f2-134">Einige Systeme können möglicherweise aufgrund von Einschränkungen in den Standard-JEA-Cmdlets keine vollständige JEA-Sitzung importieren.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-134">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span> <span data-ttu-id="ed2f2-135">Dies können Sie umgehen, indem Sie nur die von Ihnen benötigten Befehle aus der JEA-Sitzung importieren und ihre Namen explizit für den `-CommandName` Parameter angeben.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-135">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span> <span data-ttu-id="ed2f2-136">Ein zukünftiges Update wird dieses Problem berücksichtigen und die vollständigen JEA-Sitzungen auf den betroffenen Systemen importieren.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-136">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="ed2f2-137">Wenn Sie aufgrund von JEA-Einschränkungen für die Standardparameter keine JEA-Sitzung importieren können, führen Sie die nachfolgenden Schritte aus, um die Standardbefehle aus dem importierten Satz herauszufiltern.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-137">If you're unable to import a JEA session because of JEA constraints on the default parameters, follow the steps below to filter out the default commands from the imported set.</span></span> <span data-ttu-id="ed2f2-138">Sie können weiterhin Befehle wie `Select-Object` ausführen, verwenden dabei aber nur die auf Ihrem Computer installierte lokale Version anstelle der importierten Version der JEA-Remotesitzung.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-138">You can continue use commands like `Select-Object`, but you'll just use the local version installed on your computer instead of the one imported from the remote JEA session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Get a list of all the commands on the JEA endpoint
$commands = Invoke-Command -Session $jeasession -ScriptBlock { Get-Command }

# Filter out the default cmdlets
$jeaDefaultCmdlets = 'Clear-Host', 'Exit-PSSession', 'Get-Command', 'Get-FormatData', 'Get-Help', 'Measure-Object', 'Out-Default', 'Select-Object'
$filteredCommands = $commands.Name | Where-Object { $jeaDefaultCmdlets -notcontains $_ }

# Import only commands explicitly added in role capabilities and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA' -CommandName $filteredCommands
```

<span data-ttu-id="ed2f2-139">Sie können die Proxy-Cmdlets aus dem impliziten Remotingvorgang auch mithilfe von [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession) beibehalten.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-139">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="ed2f2-140">Weitere Informationen zum impliziten Remoting finden Sie in der Dokumentation zu [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) und [Import-Module](/powershell/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="ed2f2-140">For more information about implicit remoting, see the documentation for [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) and [Import-Module](/powershell/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="ed2f2-141">Programmgesteuertes Verwenden von JEA</span><span class="sxs-lookup"><span data-stu-id="ed2f2-141">Using JEA programmatically</span></span>

<span data-ttu-id="ed2f2-142">JEA kann auch in Automatisierungssystemen und Benutzeranwendungen wie z. B. internen Helpdesk-Apps und Websites verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-142">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and websites.</span></span> <span data-ttu-id="ed2f2-143">Dabei ist der Ansatz derselbe wie beim Erstellen von Apps, die mit uneingeschränkten PowerShell-Endpunkten kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-143">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints.</span></span> <span data-ttu-id="ed2f2-144">Vergewissern Sie sich, dass das Programm für die Verwendung mit JEA-Einschränkungen konzipiert wurde.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-144">Ensure the program is designed to work with limitation imposed by JEA.</span></span>

<span data-ttu-id="ed2f2-145">Für einfache, einmalige Vorgänge können Sie [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) zum Ausführen von Befehlen in einer JEA-Sitzung verwenden.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-145">For simple, one-off tasks, you can use [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) to run commands in a JEA session.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="ed2f2-146">Um festzustellen, welche Befehle zur Verfügung stehen, wenn Sie eine Verbindung mit einer JEA-Sitzung herstellen, führen Sie `Get-Command` aus, und durchlaufen Sie die Ergebnisse , um die zulässigen Parameter zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-146">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="ed2f2-147">Wenn Sie eine C#-App erstellen, können Sie einen PowerShell-Runspace erstellen, der eine Verbindung mit einer JEA-Sitzung herstellt. Dazu müssen Sie den Namen der Konfiguration in einem [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo)-Objekt angeben.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-147">If you're building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) object.</span></span>

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
// See https://docs.microsoft.com/dotnet/api/system.management.automation.pscredential
var creds        = // create a PSCredential object here

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
    false,                 // Use SSL
    computerName,          // Computer name
    5985,                  // WSMan Port
    "/wsman",              // WSMan Path
                           // Connection URI with config name
    string.Format(CultureInfo.InvariantCulture, "https://schemas.microsoft.com/powershell/{0}", configName),
    creds);                // Credentials

// Now, use the connection info to create a runspace where you can run the commands
using (Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo))
{
    // Open the runspace
    runspace.Open();

    using (PowerShell ps = PowerShell.Create())
    {
        // Set the PowerShell object to use the JEA runspace
        ps.Runspace = runspace;

        // Now you can add and invoke commands
        ps.AddCommand("Get-Command");
        foreach (var result in ps.Invoke())
        {
            Console.WriteLine(result);
        }
    }

    // Close the runspace
    runspace.Close();
}
```

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="ed2f2-148">Verwenden von JEA mit PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="ed2f2-148">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="ed2f2-149">Hyper-V in Windows 10 und Windows Server 2016 beinhaltet [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct). Mit dieser Funktion können Hyper-V-Administratoren virtuelle Computer mit PowerShell verwalten, und zwar unabhängig von der Netzwerkkonfiguration oder den Einstellungen für die Remoteverwaltung auf dem virtuellen Computer.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-149">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), a feature that allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="ed2f2-150">Durch die Verwendung von PowerShell Direct mit JEA können Sie einem Hyper-V-Administrator eingeschränkten Zugriff auf Ihren virtuellen Computer gewähren.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-150">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM.</span></span>
<span data-ttu-id="ed2f2-151">Dies kann hilfreich sein, wenn Sie die Netzwerkverbindung zu Ihrer VM verlieren und zur Reparatur der Netzwerkeinstellungen einen Datacenter-Administrator benötigen.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-151">This can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="ed2f2-152">Für die Verwendung von JEA über PowerShell Direct ist keine weitere Konfiguration erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-152">No additional configuration is required to use JEA over PowerShell Direct.</span></span> <span data-ttu-id="ed2f2-153">Allerdings muss das Gastbetriebssystem des virtuellen Computers Windows 10, Windows Server 2016 oder höher sein.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-153">However, the guest operating system running inside the virtual machine must be Windows 10, Windows Server 2016, or higher.</span></span> <span data-ttu-id="ed2f2-154">Der Hyper-V-Administrator kann eine Verbindung mit dem JEA-Endpunkt herstellen und den `-VMName` oder den `-VMId`-Parameter auf PSRemoting-Cmdlets verwenden:</span><span class="sxs-lookup"><span data-stu-id="ed2f2-154">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="ed2f2-155">Das Erstellen eines dedizierten Benutzerkontos mit minimalen Berechtigungen wird empfohlen, um das System für die Verwendung durch einen Hyper-V-Administrator zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-155">It's recommended you create a dedicated user account with the minimum rights needed to manage the system for use by a Hyper-V administrator.</span></span> <span data-ttu-id="ed2f2-156">Bedenken Sie, dass sich selbst Benutzer ohne Berechtigungen standardmäßig bei einem Windows-Computer anmelden und PowerShell uneingeschränkt verwenden können.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-156">Remember, even an unprivileged user can sign into a Windows machine by default, including using unconstrained PowerShell.</span></span> <span data-ttu-id="ed2f2-157">Auf diese Weise können sie das Dateisystem durchsuchen und Informationen über Ihr Betriebssystem sammeln.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-157">That allows them to browse the file system and learn more about your OS environment.</span></span> <span data-ttu-id="ed2f2-158">Wenn ein Hyper-V-Administrator gesperrt werden und dessen Zugriff auf eine VM nur über PowerShell Direct mit JEA möglich sein soll, müssen Sie die lokalen Anmelderechte für das JEA-Konto des Hyper-V-Administrators verweigern.</span><span class="sxs-lookup"><span data-stu-id="ed2f2-158">To lock down a Hyper-V administrator and limit them to only access a VM using PowerShell Direct with JEA, you must deny local logon rights to the Hyper-V admin's JEA account.</span></span>
