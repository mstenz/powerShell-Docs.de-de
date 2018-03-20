---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,security
title: Verwenden von JEA
ms.openlocfilehash: f0c22bf0f823b9fafa203e7f98049a6a6b3b7c05
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="using-jea"></a><span data-ttu-id="77b4a-103">Verwenden von JEA</span><span class="sxs-lookup"><span data-stu-id="77b4a-103">Using JEA</span></span>

> <span data-ttu-id="77b4a-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="77b4a-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="77b4a-105">Dieses Thema beschreibt die verschiedenen Möglichkeiten, um eine Verbindung zu einem JEA-Endpunkt herzustellen und ihn zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="77b4a-105">This topic describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="77b4a-106">Interaktives Verwenden von JEA</span><span class="sxs-lookup"><span data-stu-id="77b4a-106">Using JEA interactively</span></span>

<span data-ttu-id="77b4a-107">Wenn Sie Ihre JEA-Konfiguration testen oder Benutzer einfache Aufgaben ausführen sollen, können Sie JEA wie eine normale PowerShell-Remoting-Sitzung verwenden.</span><span class="sxs-lookup"><span data-stu-id="77b4a-107">If you are testing your JEA configuration or have simple tasks for users to perform, you can use JEA the same way you would a regular PowerShell remoting session.</span></span>
<span data-ttu-id="77b4a-108">Für komplexe Remotingaufgaben empfehlen wir stattdessen [implizites Remoting](#using-jea-with-implicit-remoting), da Ihre Benutzer auf diese Weise lokal mit Datenobjekten arbeiten können, was ihre Aufgabe erleichtert.</span><span class="sxs-lookup"><span data-stu-id="77b4a-108">For complex remoting tasks, it is recommended to use [implicit remoting](#using-jea-with-implicit-remoting) instead to make it easier for your users by allowing users to operate with the data objects locally.</span></span>

<span data-ttu-id="77b4a-109">Wenn Sie JEA interaktiv verwenden möchten, ist Folgendes erforderlich:</span><span class="sxs-lookup"><span data-stu-id="77b4a-109">To use JEA interactively, you will need:</span></span>
- <span data-ttu-id="77b4a-110">der Name des Computers, mit dem Sie eine Verbindung herstellen (möglicherweise der lokale Computer)</span><span class="sxs-lookup"><span data-stu-id="77b4a-110">The name of the computer you are connecting to (can be the local machine)</span></span>
- <span data-ttu-id="77b4a-111">der Name des auf diesem Computer registrierten JEA-Endpunkts</span><span class="sxs-lookup"><span data-stu-id="77b4a-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="77b4a-112">die Anmeldeinformationen für den Computer mit Zugriff auf den JEA-Endpunkt</span><span class="sxs-lookup"><span data-stu-id="77b4a-112">Credentials for the computer that have access to the JEA endpoint</span></span>

<span data-ttu-id="77b4a-113">Anhand dieser Informationen können Sie eine JEA-Sitzung starten und [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) oder [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession) verwenden.</span><span class="sxs-lookup"><span data-stu-id="77b4a-113">With that information in hand, you can start a JEA session using [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="77b4a-114">Wenn das Konto, bei dem Sie zurzeit angemeldet sind, Zugriff auf den JEA-Endpunkt hat, können Sie den Parameter `-Credential` auslassen.</span><span class="sxs-lookup"><span data-stu-id="77b4a-114">If the account you're currently logged in as has access to the JEA endpoint, you can omit the `-Credential` parameter.</span></span>

<span data-ttu-id="77b4a-115">Wenn die PowerShell-Aufforderung sich zu `[localhost]: PS>` ändert, wissen Sie, dass Sie ab jetzt mit der JEA-Remotesitzung interagieren.</span><span class="sxs-lookup"><span data-stu-id="77b4a-115">When the PowerShell prompt changes to `[localhost]: PS>` you will know that you are now interacting with the remote JEA session.</span></span>
<span data-ttu-id="77b4a-116">Sie können `Get-Command` ausführen, um zu überprüfen, welche Befehle verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="77b4a-116">You can run `Get-Command` to check which commands are available.</span></span>
<span data-ttu-id="77b4a-117">Wenden Sie sich an Ihren Administrator, um zu erfahren, ob für die verfügbaren Parameter Einschränkungen gelten oder zulässige Parameterwerte vorliegen.</span><span class="sxs-lookup"><span data-stu-id="77b4a-117">You will need to consult with your administrator to learn if there are any restrictions on the available parameters or allowable parameter values.</span></span>

<span data-ttu-id="77b4a-118">Zur Erinnerung: JEA-Sitzungen werden im NoLanguage-Modus ausgeführt. Daher stehen einige der klassischen Verwendungsmöglichkeiten von PowerShell möglicherweise nicht zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="77b4a-118">As a reminder, JEA sessions operate in NoLanguage mode, so some of the ways you typically use PowerShell may not be available.</span></span>
<span data-ttu-id="77b4a-119">Beispielsweise können Sie keine Variablen zum Speichern von Daten nutzen oder die Eigenschaften der von Cmdlets zurückgegebenen Objekte überprüfen.</span><span class="sxs-lookup"><span data-stu-id="77b4a-119">For instance, you cannot use variables to store data or inspect the properties on objects returned from cmdlets.</span></span>
<span data-ttu-id="77b4a-120">Das unten stehende Beispiel zeigt, wie Sie PowerShell heute verwenden können, und zwei Möglichkeiten, wie Sie den gleichen Befehl im NoLanguage-Modus ausführen.</span><span class="sxs-lookup"><span data-stu-id="77b4a-120">The below example shows an example of how you may be using PowerShell today, and two approaches to get the same command working in NoLanguage mode.</span></span>

```powershell
# Using variables in NoLanguage mode is disallowed, so the following will not work
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# Better yet, use parameter sets that don't require extra data to be passed in when possible
Start-VM -VMName 'SQL01'
```

<span data-ttu-id="77b4a-121">Für eine komplexere Verwendung des Befehls, die diesen Ansatz erschwert, sollten Sie [implizites Remoting](#using-jea-with-implicit-remoting) oder das [Erstellen von benutzerdefinierten Funktionen](role-capabilities.md#creating-custom-functions) in Erwägung ziehen, um die gewünschte Funktionalität nutzen zu können.</span><span class="sxs-lookup"><span data-stu-id="77b4a-121">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you desire.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="77b4a-122">Verwenden von JEA mit implizitem Remoting</span><span class="sxs-lookup"><span data-stu-id="77b4a-122">Using JEA with implicit remoting</span></span>

<span data-ttu-id="77b4a-123">PowerShell bietet ein alternatives Remotingmodell, bei dem Sie Proxy-Cmdlets von einem Remotecomputer auf den lokalen Computer importieren und mit ihnen interagieren können, als wären es lokale Befehle.</span><span class="sxs-lookup"><span data-stu-id="77b4a-123">PowerShell supports an alternative remoting model where you can import proxy cmdlets from a remote machine on your local computer and interact with them as if they were local commands.</span></span>
<span data-ttu-id="77b4a-124">Dies wird als „implizites Remoting“ bezeichnet und wird in folgendem englischsprachigen Blogbeitrag anschaulich erklärt: [*Hey, Scripting Guy!*](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/)</span><span class="sxs-lookup"><span data-stu-id="77b4a-124">This is called implicit remoting, and is explained well in [this *Hey, Scripting Guy!* blog post](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="77b4a-125">Implizites Remoting bietet sich besonders für die Arbeit mit JEA an, da Sie auf diese Weise mit JEA-Cmdlets im FullLangue-Modus arbeiten können.</span><span class="sxs-lookup"><span data-stu-id="77b4a-125">Implicit remoting is particularly useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span>
<span data-ttu-id="77b4a-126">Dies bedeutet, dass Sie die Vervollständigung mittels Tabstopptaste und Variablen nutzen, Objekte bearbeiten und sogar lokale Skripts verwenden können, um eine Automatisierung leichter gegen einen JEA-Endpunkt auszuführen.</span><span class="sxs-lookup"><span data-stu-id="77b4a-126">This means you can use tab completion, variables, manipulate objects, and even use local scripts to more easily automate against a JEA endpoint.</span></span>
<span data-ttu-id="77b4a-127">Jedes Mal, wenn Sie einen Proxybefehl aufrufen, werden die Daten an den JEA-Endpunkt auf dem Remotecomputer gesendet und dort ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="77b4a-127">Anytime you invoke a proxy command, the data will be sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="77b4a-128">Mithilfe von implizitem Remoting können Sie Cmdlets aus einer vorhandenen PowerShell-Sitzung importieren.</span><span class="sxs-lookup"><span data-stu-id="77b4a-128">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span>
<span data-ttu-id="77b4a-129">Sie können optional den Namen der einzelnen Proxy-Cmdlets eine Zeichenfolge Ihrer Wahl vorausstellen, um besser hervorzuheben, welche Befehle zum Remotesystem gehören.</span><span class="sxs-lookup"><span data-stu-id="77b4a-129">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing to distinguish which commands are for the remote system.</span></span>
<span data-ttu-id="77b4a-130">Ein temporäres Skriptmodul mit allen Proxybefehlen wird erstellt und kann für die Dauer Ihrer lokalen PowerShell-Sitzung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="77b4a-130">A temporary script module containing all of the proxy commands will be created and can be used for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="77b4a-131">Einige Systeme können möglicherweise aufgrund von Einschränkungen in den Standard-JEA-Cmdlets keine vollständige JEA-Sitzung importieren.</span><span class="sxs-lookup"><span data-stu-id="77b4a-131">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span>
> <span data-ttu-id="77b4a-132">Dies können Sie umgehen, indem Sie nur die von Ihnen benötigten Befehle aus der JEA-Sitzung importieren und ihre Namen explizit für den `-CommandName` Parameter angeben.</span><span class="sxs-lookup"><span data-stu-id="77b4a-132">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span>
> <span data-ttu-id="77b4a-133">Ein zukünftiges Update wird dieses Problem berücksichtigen und die vollständigen JEA-Sitzungen auf den betroffenen Systemen importieren.</span><span class="sxs-lookup"><span data-stu-id="77b4a-133">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="77b4a-134">Wenn Sie aufgrund von Einschränkungen auf den JEA-Standardparametern keine JEA-Sitzung importieren können, führen Sie die nachfolgenden Schritte aus, um die Standardbefehle aus dem importierten Satz herauszufiltern.</span><span class="sxs-lookup"><span data-stu-id="77b4a-134">If you are unable to import a JEA session due to constraints on the default JEA parameters, you can follow the steps below to filter out the default commands from the imported set.</span></span>
<span data-ttu-id="77b4a-135">Sie können weiterhin Befehle wie `Select-Object` ausführen. Sie verwenden dabei allerdings nur die auf Ihrem Computer installierte lokale Version und nicht die Remoteversion in der JEA-Sitzung.</span><span class="sxs-lookup"><span data-stu-id="77b4a-135">You will still be able to use commands like `Select-Object` -- you'll just use the local version installed on your computer instead of the remote one in the JEA session.</span></span>

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

<span data-ttu-id="77b4a-136">Sie können die Proxy-Cmdlets aus dem impliziten Remotingvorgang auch mithilfe von [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession) beibehalten.</span><span class="sxs-lookup"><span data-stu-id="77b4a-136">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="77b4a-137">Weitere Informationen zum impliziten Remoting finden Sie in der Hilfedokumentation zu [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) und [Import-Module](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="77b4a-137">For more information about implicit remoting, check out the help documentation for [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) and [Import-Module](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programatically"></a><span data-ttu-id="77b4a-138">Programmgesteuertes Verwenden von JEA</span><span class="sxs-lookup"><span data-stu-id="77b4a-138">Using JEA programatically</span></span>

<span data-ttu-id="77b4a-139">JEA kann auch in Automatisierungssystemen und Benutzeranwendungen wie z.B. internen Helpdesk-Apps und Websites verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="77b4a-139">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and web sites.</span></span>
<span data-ttu-id="77b4a-140">Dabei wird genauso vorgegangen wie beim Erstellen von Apps, die mit uneingeschränkten PowerShell-Endpunkten kommunizieren. Das Programm muss jedoch unterstützen, dass JEA die Befehle beschränkt, die in der Remotesitzung ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="77b4a-140">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints, with the caveat that the program should be aware that JEA is limiting the commands that can be run in the remote session.</span></span>

<span data-ttu-id="77b4a-141">Für einfache, einmalige Vorgänge können Sie [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) zum Ausführen einer Reihe von Befehlen mit JEA verwenden.</span><span class="sxs-lookup"><span data-stu-id="77b4a-141">For simple, one-off tasks, you can use [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) to run a set of commands using JEA.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="77b4a-142">Um festzustellen, welche Befehle zur Verfügung stehen, wenn Sie eine Verbindung mit einer JEA-Sitzung herstellen, führen Sie `Get-Command` aus, und durchlaufen Sie die Ergebnisse , um die zulässigen Parameter zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="77b4a-142">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="77b4a-143">Wenn Sie eine C#-App erstellen, können Sie einen PowerShell-Runspace erstellen, der eine Verbindung mit einer JEA-Sitzung herstellt. Dazu müssen Sie den Namen der Konfiguration in einem [WSManConnectionInfo](https://msdn.microsoft.com/en-us/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx)-Objekt angeben.</span><span class="sxs-lookup"><span data-stu-id="77b4a-143">If you are building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](https://msdn.microsoft.com/en-us/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) object.</span></span>

```csharp

// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/en-us/library/system.management.automation.pscredential(v=vs.85).aspx)

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
                    false,                 // Use SSL
                    computerName,          // Computer name
                    5985,                  // WSMan Port
                    "/wsman",              // WSMan Path
                    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),  // Connection URI with config name
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

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="77b4a-144">Verwenden von JEA mit PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="77b4a-144">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="77b4a-145">Hyper-V in Windows 10 und Windows Server 2016 bieten [PowerShell Direct](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/vmsession). Mit dieser Funktion können Hyper-V-Administratoren virtuelle Computer mit PowerShell verwalten, und zwar unabhängig von der Netzwerkkonfiguration oder den Einstellungen für die Remoteverwaltung auf dem virtuellen Computer.</span><span class="sxs-lookup"><span data-stu-id="77b4a-145">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/vmsession), a feature which allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="77b4a-146">Sie können PowerShell direkt mit JEA verwenden und einem Hyper-V-Administrator beschränkten Zugriff auf Ihren virtuellen Computer geben. Dies kann sinnvoll sein, wenn Sie die Netzwerkkonnektivität zur Ihrer VM verlieren und ein Datencenter-Administrator die Einstellungen des Netzwerks beheben muss.</span><span class="sxs-lookup"><span data-stu-id="77b4a-146">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM, which can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="77b4a-147">Für die Verwendung von JEA über PowerShell Direct ist keine weitere Konfiguration erforderlich. Das auf dem virtuellen Computer ausgeführte Betriebssystem muss jedoch Windows 10 oder Windows Server 2016 sein.</span><span class="sxs-lookup"><span data-stu-id="77b4a-147">No additional configuration is required to use JEA over PowerShell Direct, however the operating system running inside the virtual machine must be Windows 10 or Windows Server 2016.</span></span>
<span data-ttu-id="77b4a-148">Der Hyper-V-Administrator kann eine Verbindung mit dem JEA-Endpunkt herstellen und den `-VMName` oder den `-VMId`-Parameter auf PSRemoting-Cmdlets verwenden:</span><span class="sxs-lookup"><span data-stu-id="77b4a-148">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="77b4a-149">Es wird dringend empfohlen, einen dedizierten lokalen Benutzer zu erstellen, der über keine weiteren Berechtigungen zum Verwalten des Systems verfügt, das Ihre Hyper-V-Administratoren verwenden.</span><span class="sxs-lookup"><span data-stu-id="77b4a-149">It is strongly recommended that you create a dedicated local user with no other rights to manage the system for your Hyper-V administrators to use.</span></span>
<span data-ttu-id="77b4a-150">Berücksichtigen Sie, dass sich selbst Benutzer ohne Rechte standardmäßig weiterhin an einem Windows-Computer anmelden und PowerShell uneingeschränkt verwenden können.</span><span class="sxs-lookup"><span data-stu-id="77b4a-150">Remember that even an unprivileged user can still log into a Windows machine by default, including using unconstrained PowerShell.</span></span>
<span data-ttu-id="77b4a-151">Auf diese Weise können sie das Dateisystem (teilweise) durchsuchen und mehr über Ihre OS-Umgebung erfahren.</span><span class="sxs-lookup"><span data-stu-id="77b4a-151">That will allow them to browse (some of) the file system and learn more about your OS environment.</span></span>
<span data-ttu-id="77b4a-152">Wenn ein Hyper-V-Administrator nur über PowerShell Direct mit JEA auf eine VM zugreifen soll, müssen Sie die lokalen Anmelderechte für das JEA-Konto des Hyper-V-Administrators verweigern.</span><span class="sxs-lookup"><span data-stu-id="77b4a-152">To lock down a Hyper-V administrator to only access a VM using PowerShell Direct with JEA, you will need to deny local logon rights to the Hyper-V admin's JEA account.</span></span>

