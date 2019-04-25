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
ms.openlocfilehash: cc014487a680747ad59437052f79d4576154a1cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082548"
---
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="0ac03-102">Windows PowerShell-Host: Schnellstart</span><span class="sxs-lookup"><span data-stu-id="0ac03-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="0ac03-103">Um Windows PowerShell in Ihrer Anwendung zu hosten, verwenden Sie die [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) Klasse.</span><span class="sxs-lookup"><span data-stu-id="0ac03-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span> <span data-ttu-id="0ac03-104">Diese Klasse stellt Methoden, die zum Erstellen einer Pipeline von Befehlen, und führen Sie dann diese Befehle in einem Runspace.</span><span class="sxs-lookup"><span data-stu-id="0ac03-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span> <span data-ttu-id="0ac03-105">Die einfachste Möglichkeit, eine hostanwendung erstellen, ist mit dem standardmäßigen Runspace.</span><span class="sxs-lookup"><span data-stu-id="0ac03-105">The simplest way to create a host application is to use the default runspace.</span></span> <span data-ttu-id="0ac03-106">Der standardmäßigen Runspace enthält alle Windows PowerShell Core-Befehle.</span><span class="sxs-lookup"><span data-stu-id="0ac03-106">The default runspace contains all of the core Windows PowerShell commands.</span></span> <span data-ttu-id="0ac03-107">Wenn Sie Ihre Anwendung nur eine Teilmenge der Windows PowerShell-Befehle verfügbar machen möchten, müssen Sie einen benutzerdefinierten Runspace erstellen.</span><span class="sxs-lookup"><span data-stu-id="0ac03-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="0ac03-108">Mithilfe der standardmäßigen runspace</span><span class="sxs-lookup"><span data-stu-id="0ac03-108">Using the default runspace</span></span>

<span data-ttu-id="0ac03-109">Zum Starten wir den standardmäßigen Runspace verwenden und mit den Methoden der der [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) Klasse, um Befehle, Parameter, Anweisungen und Skripts zu einer Pipeline hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="0ac03-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="0ac03-110">AddCommand</span><span class="sxs-lookup"><span data-stu-id="0ac03-110">AddCommand</span></span>

<span data-ttu-id="0ac03-111">Sie verwenden die [System.Management.Automation.Powershell.AddCommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) Methode der [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) Klasse, um Befehle an die Pipeline hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="0ac03-111">You use the [System.Management.Automation.Powershell.AddCommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands to the pipeline.</span></span> <span data-ttu-id="0ac03-112">Nehmen wir beispielsweise an, dass die Liste der ausgeführten Prozesse auf dem Computer abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="0ac03-112">For example, suppose you want to get the list of running processes on the machine.</span></span> <span data-ttu-id="0ac03-113">Die Möglichkeit zum Ausführen dieses Befehls lautet wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="0ac03-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="0ac03-114">Erstellen Sie eine [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) Objekt.</span><span class="sxs-lookup"><span data-stu-id="0ac03-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="0ac03-115">Fügen Sie den Befehl aus, dem Sie ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="0ac03-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="0ac03-116">Rufen Sie den Befehl.</span><span class="sxs-lookup"><span data-stu-id="0ac03-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="0ac03-117">Aufrufen der [System.Management.Automation.Powershell.AddCommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) Methode, die mehr als einmal vor dem Aufruf der [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) -Methode, die das Ergebnis der ersten Befehl wird über die Pipeline zum zweiten und So weiter.</span><span class="sxs-lookup"><span data-stu-id="0ac03-117">If you call the [System.Management.Automation.Powershell.AddCommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="0ac03-118">Wenn Sie nicht das Ergebnis eines vorherigen Befehls an einen Befehl übergeben möchten, fügen Sie ihn durch Aufrufen der [System.Management.Automation.Powershell.AddStatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) stattdessen.</span><span class="sxs-lookup"><span data-stu-id="0ac03-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="0ac03-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="0ac03-119">AddParameter</span></span>

<span data-ttu-id="0ac03-120">Im vorherige Beispiel führt einen einzelnen Befehl ohne Parameter aus.</span><span class="sxs-lookup"><span data-stu-id="0ac03-120">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="0ac03-121">Sie können Parameter an den Befehl hinzufügen, mit der [System.Management.Automation.PSCommand.AddParameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) z. B. der folgende Code ruft Methode eine Liste aller Prozesse mit dem Namen `PowerShell` unter der Computer.</span><span class="sxs-lookup"><span data-stu-id="0ac03-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="0ac03-122">Sie können zusätzliche Parameter hinzufügen, durch den Aufruf [System.Management.Automation.PSCommand.AddParameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) wiederholt.</span><span class="sxs-lookup"><span data-stu-id="0ac03-122">You can add additional parameters by calling [System.Management.Automation.PSCommand.AddParameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

<span data-ttu-id="0ac03-123">Sie können auch ein Wörterbuch von Parameternamen und Werte hinzufügen, durch den Aufruf der [System.Management.Automation.PowerShell.AddParameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) Methode.</span><span class="sxs-lookup"><span data-stu-id="0ac03-123">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="0ac03-124">AddStatement</span><span class="sxs-lookup"><span data-stu-id="0ac03-124">AddStatement</span></span>

<span data-ttu-id="0ac03-125">Sie können mithilfe von Batchverarbeitung simulieren die [System.Management.Automation.PowerShell.AddStatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) -Methode, die an das Ende der Pipeline eine zusätzliche Anweisung der folgende Code eine Liste fügt ruft der ausgeführten Prozesse mit dem Namen `PowerShell`, und ruft anschließend die Liste der ausgeführten Dienste.</span><span class="sxs-lookup"><span data-stu-id="0ac03-125">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="0ac03-126">AddScript</span><span class="sxs-lookup"><span data-stu-id="0ac03-126">AddScript</span></span>

<span data-ttu-id="0ac03-127">Sie können ein vorhandenes Skript ausführen, durch den Aufruf der [System.Management.Automation.PowerShell.AddScript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) Methode.</span><span class="sxs-lookup"><span data-stu-id="0ac03-127">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="0ac03-128">Im folgenden Beispiel wird die Pipeline ein Skript hinzugefügt und wird ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="0ac03-128">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="0ac03-129">In diesem Beispiel wird vorausgesetzt, es ist bereits ein Skript namens `MyScript.ps1` in einem Ordner namens `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="0ac03-129">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="0ac03-130">Es gibt auch eine Version der [System.Management.Automation.PowerShell.AddScript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) -Methode, die einen booleschen namens Parameter `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="0ac03-130">There is also a version of the [System.Management.Automation.PowerShell.AddScript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="0ac03-131">Wenn dieser Parameter, um festgelegt wird `true`, und klicken Sie dann das Skript im lokalen Bereich ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="0ac03-131">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="0ac03-132">Der folgende Code führt das Skript im lokalen Bereich.</span><span class="sxs-lookup"><span data-stu-id="0ac03-132">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="0ac03-133">Erstellen einen benutzerdefinierten runspace</span><span class="sxs-lookup"><span data-stu-id="0ac03-133">Creating a custom runspace</span></span>

<span data-ttu-id="0ac03-134">Während der in den vorherigen Beispielen verwendete standardrunspace aller Befehle verwenden Windows PowerShell Core geladen wird, können Sie einen benutzerdefinierten Runspace erstellen, der nur eine angegebene Teilmenge aller Befehle lädt.</span><span class="sxs-lookup"><span data-stu-id="0ac03-134">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span> <span data-ttu-id="0ac03-135">Möglicherweise möchten Sie hierzu zur Verbesserung der Leistung (Laden eine größere Anzahl von Befehlen ist eine leistungsverschlechterung), oder die Funktionalität des Benutzers für Vorgänge einschränken.</span><span class="sxs-lookup"><span data-stu-id="0ac03-135">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span> <span data-ttu-id="0ac03-136">Ein Runspace, der nur eine begrenzte Anzahl von Befehlen verfügbar macht, wird einen eingeschränkten Runspace aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="0ac03-136">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span> <span data-ttu-id="0ac03-137">Um einem eingeschränkten Runspace zu erstellen, verwenden Sie die [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) und [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) Klassen.</span><span class="sxs-lookup"><span data-stu-id="0ac03-137">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="0ac03-138">Erstellen eines Objekts InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="0ac03-138">Creating an InitialSessionState object</span></span>

<span data-ttu-id="0ac03-139">Um einen benutzerdefinierten Runspace zu erstellen, erstellen Sie zuerst eine [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) Objekt.</span><span class="sxs-lookup"><span data-stu-id="0ac03-139">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span> <span data-ttu-id="0ac03-140">Im folgenden Beispiel verwenden wir die [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) , einen Runspace erstellen, nach dem Erstellen einer standardmäßigen [System.Management.Automation.Runspaces.InitialSessionState ](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) Objekt.</span><span class="sxs-lookup"><span data-stu-id="0ac03-140">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="0ac03-141">Einschränken des Runspaces</span><span class="sxs-lookup"><span data-stu-id="0ac03-141">Constraining the runspace</span></span>

<span data-ttu-id="0ac03-142">Im vorherigen Beispiel erstellten wir den Standardwert [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt, das alle von der integrierten Windows PowerShell-Kern lädt.</span><span class="sxs-lookup"><span data-stu-id="0ac03-142">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span> <span data-ttu-id="0ac03-143">Wir könnten auch aufgerufen haben die [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) Methode zum Erstellen eines InitialSessionState-Objekts, das nur die Befehle in der Microsoft.PowerShell.Core laden -Snap-in.</span><span class="sxs-lookup"><span data-stu-id="0ac03-143">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span> <span data-ttu-id="0ac03-144">Um einen stärker eingeschränkten Runspace zu erstellen, müssen Sie eine leere erstellen [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt durch Aufrufen der [ System.Management.Automation.Runspaces.InitialSessionState.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) -Methode, und dann die InitialSessionState Befehle hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="0ac03-144">To create a more constrained runspace, you must create an empty [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="0ac03-145">Mit dem Runspace, der nur die Befehle, die Sie angeben, lädt bietet erheblich bessere Leistung.</span><span class="sxs-lookup"><span data-stu-id="0ac03-145">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="0ac03-146">Sie verwenden die Methoden der [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) Klasse, um Cmdlets für den anfänglichen Sitzungsstatus zu definieren.</span><span class="sxs-lookup"><span data-stu-id="0ac03-146">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span> <span data-ttu-id="0ac03-147">Das folgende Beispiel erstellt eine leere anfänglichen Sitzungsstatus, und klicken Sie dann definiert und fügt die `Get-Command` und `Import-Module` Befehle aus, um den anfänglichen Sitzungsstatus.</span><span class="sxs-lookup"><span data-stu-id="0ac03-147">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span> <span data-ttu-id="0ac03-148">Anschließend erstellen wir einen Runspace, die von diesem anfänglichen Sitzungsstatus eingeschränkt, und führen Sie die Befehle in diesen Runspace.</span><span class="sxs-lookup"><span data-stu-id="0ac03-148">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="0ac03-149">Erstellen Sie den anfänglichen Sitzungsstatus.</span><span class="sxs-lookup"><span data-stu-id="0ac03-149">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="0ac03-150">Definieren und Hinzufügen von Befehlen zu den anfänglichen Sitzungsstatus.</span><span class="sxs-lookup"><span data-stu-id="0ac03-150">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="0ac03-151">Erstellen und Öffnen des Runspaces.</span><span class="sxs-lookup"><span data-stu-id="0ac03-151">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="0ac03-152">Führt einen Befehl aus, und zeigen das Ergebnis.</span><span class="sxs-lookup"><span data-stu-id="0ac03-152">Execute a command and show the result.</span></span>

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

<span data-ttu-id="0ac03-153">Bei der Ausführung wird die Ausgabe dieses Codes wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="0ac03-153">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
