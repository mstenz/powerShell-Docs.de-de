---
title: Schnellstart für Windows PowerShell-Host | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 390eb2d0153c65967d8c0711c852aa6e13fe4660
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855102"
---
# <a name="windows-powershell-host-quickstart"></a>Windows PowerShell-Host: Schnellstart

Um Windows PowerShell in Ihrer Anwendung zu hosten, verwenden Sie die [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) Klasse.
Diese Klasse stellt Methoden, die zum Erstellen einer Pipeline von Befehlen, und führen Sie dann diese Befehle in einem Runspace.
Die einfachste Möglichkeit, eine hostanwendung erstellen, ist mit dem standardmäßigen Runspace.
Der standardmäßigen Runspace enthält alle Windows PowerShell Core-Befehle.
Wenn Sie Ihre Anwendung nur eine Teilmenge der Windows PowerShell-Befehle verfügbar machen möchten, müssen Sie einen benutzerdefinierten Runspace erstellen.

## <a name="using-the-default-runspace"></a>Mithilfe der standardmäßigen runspace

Zum Starten wir den standardmäßigen Runspace verwenden und mit den Methoden der der [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) Klasse, um Befehle, Parameter, Anweisungen und Skripts zu einer Pipeline hinzuzufügen.

### <a name="addcommand"></a>AddCommand

Sie verwenden die [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) Methode, um Befehle an die Pipeline hinzuzufügen.
Nehmen wir beispielsweise an, dass die Liste der ausgeführten Prozesse auf dem Computer abgerufen werden soll.
Die Möglichkeit zum Ausführen dieses Befehls lautet wie folgt aus.

1. Erstellen Sie eine [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) Objekt.

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. Fügen Sie den Befehl aus, dem Sie ausführen möchten.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. Rufen Sie den Befehl.

   ```csharp
   ps.Invoke();
   ```

Wenn die AddCommand-Methode mehrmals aufrufen, vor dem Aufruf der [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) -Methode, das Ergebnis des ersten Befehls über die Pipeline an das zweite und So weiter.
Wenn Sie nicht das Ergebnis eines vorherigen Befehls an einen Befehl übergeben möchten, fügen Sie ihn durch Aufrufen der [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) stattdessen.

### <a name="addparameter"></a>AddParameter

Im vorherige Beispiel führt einen einzelnen Befehl ohne Parameter aus.
Sie können Parameter an den Befehl hinzufügen, mit der [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) Methode.
Der folgende Code ruft beispielsweise eine Liste aller Prozesse mit dem Namen `PowerShell` auf dem Computer ausgeführt.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

Sie können zusätzliche Parameter hinzufügen, durch die AddParameter Methode wiederholt aufrufen.

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

Sie können auch ein Wörterbuch von Parameternamen und Werte hinzufügen, durch den Aufruf der [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) Methode.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

Sie können mithilfe von Batchverarbeitung simulieren die [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) -Methode, die eine zusätzliche Anweisung bis zum Ende der Pipeline hinzugefügt.
Der folgende Code Ruft eine Liste der ausgeführten Prozesse mit dem Namen `PowerShell`, und ruft anschließend die Liste der ausgeführten Dienste.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

Sie können ein vorhandenes Skript ausführen, durch den Aufruf der [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) Methode.
Im folgenden Beispiel wird die Pipeline ein Skript hinzugefügt und wird ausgeführt.
In diesem Beispiel wird vorausgesetzt, es ist bereits ein Skript namens `MyScript.ps1` in einem Ordner namens `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

Es gibt auch eine Version der Methode, die einen booleschen namens Parameter AddScript `useLocalScope`.
Wenn dieser Parameter, um festgelegt wird `true`, und klicken Sie dann das Skript im lokalen Bereich ausgeführt wird.
Der folgende Code führt das Skript im lokalen Bereich.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>Erstellen einen benutzerdefinierten runspace

Während der in den vorherigen Beispielen verwendete standardrunspace aller Befehle verwenden Windows PowerShell Core geladen wird, können Sie einen benutzerdefinierten Runspace erstellen, der nur eine angegebene Teilmenge aller Befehle lädt.
Möglicherweise möchten Sie hierzu zur Verbesserung der Leistung (Laden eine größere Anzahl von Befehlen ist eine leistungsverschlechterung), oder die Funktionalität des Benutzers für Vorgänge einschränken.
Ein Runspace, der nur eine begrenzte Anzahl von Befehlen verfügbar macht, wird einen eingeschränkten Runspace aufgerufen.
Um einem eingeschränkten Runspace zu erstellen, verwenden Sie die [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) und [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) Klassen.

### <a name="creating-an-initialsessionstate-object"></a>Erstellen eines Objekts InitialSessionState

Um einen benutzerdefinierten Runspace zu erstellen, erstellen Sie zuerst eine [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) Objekt.
Im folgenden Beispiel verwenden wir die [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) , einen Runspace erstellen, nach dem Erstellen eines standardmäßigen InitialSessionState-Objekts.

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a>Einschränken des Runspaces

Im vorherigen Beispiel erstellten wir den Standardwert [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt, das alle von der integrierten Windows PowerShell-Kern lädt.
Wir könnten auch aufgerufen haben die [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) Methode zum Erstellen eines InitialSessionState-Objekts, das nur die Befehle in der Microsoft.PowerShell.Core laden -Snap-in.
Um einen stärker eingeschränkten Runspace zu erstellen, müssen Sie ein leeres InitialSessionState-Objekt erstellen, durch den Aufruf der [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) -Methode, und fügen Sie dann die Befehle aus, um die InitialSessionState.

Mit dem Runspace, der nur die Befehle, die Sie angeben, lädt bietet erheblich bessere Leistung.

Sie verwenden die Methoden der [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) Klasse, um Cmdlets für den anfänglichen Sitzungsstatus zu definieren.
Das folgende Beispiel erstellt eine leere anfänglichen Sitzungsstatus, und klicken Sie dann definiert und fügt die `Get-Command` und `Import-Module` Befehle aus, um den anfänglichen Sitzungsstatus.
Anschließend erstellen wir einen Runspace, die von diesem anfänglichen Sitzungsstatus eingeschränkt, und führen Sie die Befehle in diesen Runspace.

Erstellen Sie den anfänglichen Sitzungsstatus.

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

Definieren und Hinzufügen von Befehlen zu den anfänglichen Sitzungsstatus.

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

Erstellen und Öffnen des Runspaces.

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

Führt einen Befehl aus, und zeigen das Ergebnis.

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

Bei der Ausführung wird die Ausgabe dieses Codes wie folgt aussehen.

```powershell
Get-Command
Import-Module
```
