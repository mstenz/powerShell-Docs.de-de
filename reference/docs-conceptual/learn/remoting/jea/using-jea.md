---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Verwenden von JEA
ms.openlocfilehash: 1c424eb4a476dd0db3cc69c0e6f14c89a3c523ba
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500515"
---
# <a name="using-jea"></a>Verwenden von JEA

In diesem Artikel werden die verschiedenen Möglichkeiten beschrieben, um eine Verbindung mit einem JEA-Endpunkt herzustellen und ihn zu verwenden.

## <a name="using-jea-interactively"></a>Interaktives Verwenden von JEA

Wenn Sie Ihre JEA-Konfiguration testen oder über einfache Aufgaben für Benutzer verfügen, können Sie JEA wie eine normale PowerShell-Remotingsitzung verwenden. Für komplexe Remotingaufgaben wird das [implizite Remoting](#using-jea-with-implicit-remoting) empfohlen. Damit können Benutzer die Datenobjekte lokal ausführen.

Wenn Sie JEA interaktiv verwenden möchten, benötigen Sie Folgendes:

- Name des Computers, mit dem Sie eine Verbindung herstellen (möglicherweise der lokale Computer)
- der Name des auf diesem Computer registrierten JEA-Endpunkts
- Anmeldeinformationen mit Zugriff auf den JEA-Endpunkt auf diesem Computer

Anhand dieser Informationen können Sie eine JEA-Sitzung über die Cmdlets [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) oder [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) starten.

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Wenn das aktuelle Benutzerkonto Zugriff auf den JEA-Endpunkt besitzt, können Sie den Parameter **Credential** auslassen.

Wenn sich die PowerShell-Aufforderung in `[localhost]: PS>` ändert, wissen Sie, dass Sie ab jetzt mit der JEA-Remotesitzung interagieren. Sie können `Get-Command` ausführen, um zu überprüfen, welche Befehle verfügbar sind. Wenden Sie sich an Ihren Administrator, um zu erfahren, ob für die verfügbaren Parameter oder zulässigen Parameterwerte Einschränkungen gelten.

Bedenken Sie, dass JEA-Sitzungen im Modus „NoLanguage“ ausgeführt werden. Einige ihrer üblichen Verwendungsmöglichkeiten in PowerShell sind möglicherweise nicht verfügbar. Beispielsweise können Sie keine Variablen zum Speichern von Daten nutzen oder die Eigenschaften der von Cmdlets zurückgegebenen Objekte überprüfen. Das folgende Beispiel enthält zwei Ansätze für die Ausführung derselben Befehle im Modus „NoLanguage“:

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

Für komplexere Befehlsaufrufe, die mit diesem Ansatz nur schwer möglich sind, sollten Sie [implizites Remoting](#using-jea-with-implicit-remoting) oder das [Erstellen von benutzerdefinierten Funktionen](role-capabilities.md#creating-custom-functions) in Erwägung ziehen, um die benötigten Funktionen nutzen zu können.

## <a name="using-jea-with-implicit-remoting"></a>Verwenden von JEA mit implizitem Remoting

PowerShell bietet ein implizites Remotingmodell, bei dem Sie Proxy-Cmdlets von einem Remotecomputer importieren und damit interagieren können, als wären es lokale Befehle. Weitere Informationen zum impliziten Remoting finden Sie in diesem **Blogbeitrag** von [Hey, Scripting Guy!](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).
Implizites Remoting ist für die Arbeit mit JEA geeignet, da Sie auf diese Weise mit JEA-Cmdlets im Modus „FullLanguage“ arbeiten können. Dabei können Sie die Vervollständigung mit der TAB-TASTE und Variablen nutzen, Objekte bearbeiten und sogar lokale Skripts verwenden, um Aufgaben für einen JEA-Endpunkt zu automatisieren. Jedes Mal, wenn Sie einen Proxybefehl aufrufen, werden die Daten an den JEA-Endpunkt auf dem Remotecomputer gesendet und dort ausgeführt.

Mithilfe von implizitem Remoting können Sie Cmdlets aus einer vorhandenen PowerShell-Sitzung importieren. Sie können optional den Namen der einzelnen Proxy-Cmdlets eine Zeichenfolge Ihrer Wahl vorausstellen. Mit diesem Präfix können Sie die Befehle hervorheben, die zum Remotesystem gehören. Ein temporäres Skriptmodul mit allen Proxybefehlen wird erstellt und für die Dauer Ihrer lokalen PowerShell-Sitzung importiert.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Einige Systeme können möglicherweise aufgrund von Einschränkungen in den Standard-JEA-Cmdlets keine vollständige JEA-Sitzung importieren. Dies können Sie umgehen, indem Sie nur die von Ihnen benötigten Befehle aus der JEA-Sitzung importieren und ihre Namen explizit für den `-CommandName` Parameter angeben. Ein zukünftiges Update wird dieses Problem berücksichtigen und die vollständigen JEA-Sitzungen auf den betroffenen Systemen importieren.

Wenn Sie aufgrund von JEA-Einschränkungen für die Standardparameter keine JEA-Sitzung importieren können, führen Sie die nachfolgenden Schritte aus, um die Standardbefehle aus dem importierten Satz herauszufiltern. Sie können weiterhin Befehle wie `Select-Object` ausführen, verwenden dabei aber nur die auf Ihrem Computer installierte lokale Version anstelle der importierten Version der JEA-Remotesitzung.

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

Sie können die Proxy-Cmdlets aus dem impliziten Remotingvorgang auch mithilfe von [Export-PSSession](/powershell/module/microsoft.powershell.utility/Export-PSSession) beibehalten.
Weitere Informationen zum impliziten Remoting finden Sie in der Dokumentation zu [Import-PSSession](/powershell/module/microsoft.powershell.utility/import-pssession) und [Import-Module](/powershell/module/microsoft.powershell.core/import-module).

## <a name="using-jea-programmatically"></a>Programmgesteuertes Verwenden von JEA

JEA kann auch in Automatisierungssystemen und Benutzeranwendungen wie z. B. internen Helpdesk-Apps und Websites verwendet werden. Dabei ist der Ansatz derselbe wie beim Erstellen von Apps, die mit uneingeschränkten PowerShell-Endpunkten kommunizieren. Vergewissern Sie sich, dass das Programm für die Verwendung mit JEA-Einschränkungen konzipiert wurde.

Für einfache, einmalige Vorgänge können Sie [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) zum Ausführen von Befehlen in einer JEA-Sitzung verwenden.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Um festzustellen, welche Befehle zur Verfügung stehen, wenn Sie eine Verbindung mit einer JEA-Sitzung herstellen, führen Sie `Get-Command` aus, und durchlaufen Sie die Ergebnisse , um die zulässigen Parameter zu überprüfen.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Wenn Sie eine C#-App erstellen, können Sie einen PowerShell-Runspace erstellen, der eine Verbindung mit einer JEA-Sitzung herstellt. Dazu müssen Sie den Namen der Konfiguration in einem [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo)-Objekt angeben.

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

## <a name="using-jea-with-powershell-direct"></a>Verwenden von JEA mit PowerShell Direct

Hyper-V in Windows 10 und Windows Server 2016 beinhaltet [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct). Mit dieser Funktion können Hyper-V-Administratoren virtuelle Computer mit PowerShell verwalten, und zwar unabhängig von der Netzwerkkonfiguration oder den Einstellungen für die Remoteverwaltung auf dem virtuellen Computer.

Durch die Verwendung von PowerShell Direct mit JEA können Sie einem Hyper-V-Administrator eingeschränkten Zugriff auf Ihren virtuellen Computer gewähren.
Dies kann hilfreich sein, wenn Sie die Netzwerkverbindung zu Ihrer VM verlieren und zur Reparatur der Netzwerkeinstellungen einen Datacenter-Administrator benötigen.

Für die Verwendung von JEA über PowerShell Direct ist keine weitere Konfiguration erforderlich. Allerdings muss das Gastbetriebssystem des virtuellen Computers Windows 10, Windows Server 2016 oder höher sein. Der Hyper-V-Administrator kann eine Verbindung mit dem JEA-Endpunkt herstellen und den `-VMName` oder den `-VMId`-Parameter auf PSRemoting-Cmdlets verwenden:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Das Erstellen eines dedizierten Benutzerkontos mit minimalen Berechtigungen wird empfohlen, um das System für die Verwendung durch einen Hyper-V-Administrator zu verwalten. Bedenken Sie, dass sich selbst Benutzer ohne Berechtigungen standardmäßig bei einem Windows-Computer anmelden und PowerShell uneingeschränkt verwenden können. Auf diese Weise können sie das Dateisystem durchsuchen und Informationen über Ihr Betriebssystem sammeln. Wenn ein Hyper-V-Administrator gesperrt werden und dessen Zugriff auf eine VM nur über PowerShell Direct mit JEA möglich sein soll, müssen Sie die lokalen Anmelderechte für das JEA-Konto des Hyper-V-Administrators verweigern.
