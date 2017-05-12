---
manager: carmonm
ms.topic: article
author: rpsqrd
ms.author: ryanpu
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-12-05
title: Verwenden von JEA
ms.technology: powershell
ms.openlocfilehash: 62e5f74d60b2fd09e302ecc12996f97e90b73f2f
ms.sourcegitcommit: 6057e6d22ef8a2095af610e0d681e751366a9773
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/08/2017
---
# <a name="using-jea"></a>Verwenden von JEA

> Gilt für: Windows PowerShell 5.0

Dieses Thema beschreibt die verschiedenen Möglichkeiten, um eine Verbindung zu einem JEA-Endpunkt herzustellen und ihn zu verwenden.

## <a name="using-jea-interactively"></a>Interaktives Verwenden von JEA

Wenn Sie Ihre JEA-Konfiguration testen oder Benutzer einfache Aufgaben ausführen sollen, können Sie JEA wie eine normale PowerShell-Remoting-Sitzung verwenden.
Für komplexe Remotingaufgaben empfehlen wir stattdessen [implizites Remoting](#using-jea-with-implicit-remoting), da Ihre Benutzer auf diese Weise lokal mit Datenobjekten arbeiten können, was ihre Aufgabe erleichtert.

Wenn Sie JEA interaktiv verwenden möchten, ist Folgendes erforderlich:
- der Name des Computers, mit dem Sie eine Verbindung herstellen (möglicherweise der lokale Computer)
- der Name des auf diesem Computer registrierten JEA-Endpunkts
- die Anmeldeinformationen für den Computer mit Zugriff auf den JEA-Endpunkt

Anhand dieser Informationen können Sie eine JEA-Sitzung starten und [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) oder [Enter-PSSession](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/enter-pssession) verwenden.

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Wenn das Konto, bei dem Sie zurzeit angemeldet sind, Zugriff auf den JEA-Endpunkt hat, können Sie den Parameter `-Credential` auslassen.

Wenn die PowerShell-Aufforderung sich zu `[localhost]: PS>` ändert, wissen Sie, dass Sie ab jetzt mit der JEA-Remotesitzung interagieren.
Sie können `Get-Command` ausführen, um zu überprüfen, welche Befehle verfügbar sind.
Wenden Sie sich an Ihren Administrator, um zu erfahren, ob für die verfügbaren Parameter Einschränkungen gelten oder zulässige Parameterwerte vorliegen.

Zur Erinnerung: JEA-Sitzungen werden im NoLanguage-Modus ausgeführt. Daher stehen einige der klassischen Verwendungsmöglichkeiten von PowerShell möglicherweise nicht zur Verfügung.
Beispielsweise können Sie keine Variablen zum Speichern von Daten nutzen oder die Eigenschaften der von Cmdlets zurückgegebenen Objekte überprüfen.
Das unten stehende Beispiel zeigt, wie Sie PowerShell heute verwenden können, und zwei Möglichkeiten, wie Sie den gleichen Befehl im NoLanguage-Modus ausführen.

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

Für eine komplexere Verwendung des Befehls, die diesen Ansatz erschwert, sollten Sie [implizites Remoting](#using-jea-with-implicit-remoting) oder das [Erstellen von benutzerdefinierten Funktionen](role-capabilities.md#creating-custom-functions) in Erwägung ziehen, um die gewünschte Funktionalität nutzen zu können.

## <a name="using-jea-with-implicit-remoting"></a>Verwenden von JEA mit implizitem Remoting

PowerShell bietet ein alternatives Remotingmodell, bei dem Sie Proxy-Cmdlets von einem Remotecomputer auf den lokalen Computer importieren und mit ihnen interagieren können, als wären es lokale Befehle.
Dies wird als „implizites Remoting“ bezeichnet und wird in folgendem englischsprachigen Blogbeitrag anschaulich erklärt: [*Hey, Scripting Guy!*](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/)
Implizites Remoting bietet sich besonders für die Arbeit mit JEA an, da Sie auf diese Weise mit JEA-Cmdlets im FullLangue-Modus arbeiten können.
Dies bedeutet, dass Sie die Vervollständigung mittels Tabstopptaste und Variablen nutzen, Objekte bearbeiten und sogar lokale Skripts verwenden können, um eine Automatisierung leichter gegen einen JEA-Endpunkt auszuführen.
Jedes Mal, wenn Sie einen Proxybefehl aufrufen, werden die Daten an den JEA-Endpunkt auf dem Remotecomputer gesendet und dort ausgeführt.

Mithilfe von implizitem Remoting können Sie Cmdlets aus einer vorhandenen PowerShell-Sitzung importieren.
Sie können optional den Namen der einzelnen Proxy-Cmdlets eine Zeichenfolge Ihrer Wahl vorausstellen, um besser hervorzuheben, welche Befehle zum Remotesystem gehören.
Ein temporäres Skriptmodul mit allen Proxybefehlen wird erstellt und kann für die Dauer Ihrer lokalen PowerShell-Sitzung verwendet werden.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Einige Systeme können möglicherweise aufgrund von Einschränkungen in den Standard-JEA-Cmdlets keine vollständige JEA-Sitzung importieren.
> Dies können Sie umgehen, indem Sie nur die von Ihnen benötigten Befehle aus der JEA-Sitzung importieren und ihre Namen explizit für den `-CommandName` Parameter angeben.
> Ein zukünftiges Update wird dieses Problem berücksichtigen und die vollständigen JEA-Sitzungen auf den betroffenen Systemen importieren.

Wenn Sie aufgrund von Einschränkungen auf den JEA-Standardparametern keine JEA-Sitzung importieren können, führen Sie die nachfolgenden Schritte aus, um die Standardbefehle aus dem importierten Satz herauszufiltern.
Sie können weiterhin Befehle wie `Select-Object` ausführen. Sie verwenden dabei allerdings nur die auf Ihrem Computer installierte lokale Version und nicht die Remoteversion in der JEA-Sitzung.

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

Sie können die Proxy-Cmdlets aus dem impliziten Remotingvorgang auch mithilfe von [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession) beibehalten.
Weitere Informationen zum impliziten Remoting finden Sie in der Hilfedokumentation zu [Import-PSSession](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) und [Import-Module](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/import-module).

## <a name="using-jea-programatically"></a>Programmgesteuertes Verwenden von JEA

JEA kann auch in Automatisierungssystemen und Benutzeranwendungen wie z.B. internen Helpdesk-Apps und Websites verwendet werden.
Dabei wird genauso vorgegangen wie beim Erstellen von Apps, die mit uneingeschränkten PowerShell-Endpunkten kommunizieren. Das Programm muss jedoch unterstützen, dass JEA die Befehle beschränkt, die in der Remotesitzung ausgeführt werden können.

Für einfache, einmalige Vorgänge können Sie [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) zum Ausführen einer Reihe von Befehlen mit JEA verwenden.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Um festzustellen, welche Befehle zur Verfügung stehen, wenn Sie eine Verbindung mit einer JEA-Sitzung herstellen, führen Sie `Get-Command` aus, und durchlaufen Sie die Ergebnisse , um die zulässigen Parameter zu überprüfen.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Wenn Sie eine C#-App erstellen, können Sie einen PowerShell-Runspace erstellen, der eine Verbindung mit einer JEA-Sitzung herstellt. Dazu müssen Sie den Namen der Konfiguration in einem [WSManConnectionInfo](https://msdn.microsoft.com/en-us/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx)-Objekt angeben.

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

## <a name="using-jea-with-powershell-direct"></a>Verwenden von JEA mit PowerShell Direct

Hyper-V in Windows 10 und Windows Server 2016 bieten [PowerShell Direct](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/vmsession). Mit dieser Funktion können Hyper-V-Administratoren virtuelle Computer mit PowerShell verwalten, und zwar unabhängig von der Netzwerkkonfiguration oder den Einstellungen für die Remoteverwaltung auf dem virtuellen Computer.

Sie können PowerShell direkt mit JEA verwenden und einem Hyper-V-Administrator beschränkten Zugriff auf Ihren virtuellen Computer geben. Dies kann sinnvoll sein, wenn Sie die Netzwerkkonnektivität zur Ihrer VM verlieren und ein Datencenter-Administrator die Einstellungen des Netzwerks beheben muss.

Für die Verwendung von JEA über PowerShell Direct ist keine weitere Konfiguration erforderlich. Das auf dem virtuellen Computer ausgeführte Betriebssystem muss jedoch Windows 10 oder Windows Server 2016 sein.
Der Hyper-V-Administrator kann eine Verbindung mit dem JEA-Endpunkt herstellen und den `-VMName` oder den `-VMId`-Parameter auf PSRemoting-Cmdlets verwenden:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Es wird dringend empfohlen, einen dedizierten lokalen Benutzer zu erstellen, der über keine weiteren Berechtigungen zum Verwalten des Systems verfügt, das Ihre Hyper-V-Administratoren verwenden.
Berücksichtigen Sie, dass sich selbst Benutzer ohne Rechte standardmäßig weiterhin an einem Windows-Computer anmelden und PowerShell uneingeschränkt verwenden können.
Auf diese Weise können sie das Dateisystem (teilweise) durchsuchen und mehr über Ihre OS-Umgebung erfahren.
Wenn ein Hyper-V-Administrator nur über PowerShell Direct mit JEA auf eine VM zugreifen soll, müssen Sie die lokalen Anmelderechte für das JEA-Konto des Hyper-V-Administrators verweigern.
