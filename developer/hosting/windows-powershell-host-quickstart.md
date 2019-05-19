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
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="193d6-102">Windows PowerShell-Host: Schnellstart</span><span class="sxs-lookup"><span data-stu-id="193d6-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="193d6-103">Um Windows PowerShell in Ihrer Anwendung zu hosten, verwenden Sie die [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) Klasse.</span><span class="sxs-lookup"><span data-stu-id="193d6-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span>
<span data-ttu-id="193d6-104">Diese Klasse stellt Methoden, die zum Erstellen einer Pipeline von Befehlen, und führen Sie dann diese Befehle in einem Runspace.</span><span class="sxs-lookup"><span data-stu-id="193d6-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span>
<span data-ttu-id="193d6-105">Die einfachste Möglichkeit, eine hostanwendung erstellen, ist mit dem standardmäßigen Runspace.</span><span class="sxs-lookup"><span data-stu-id="193d6-105">The simplest way to create a host application is to use the default runspace.</span></span>
<span data-ttu-id="193d6-106">Der standardmäßigen Runspace enthält alle Windows PowerShell Core-Befehle.</span><span class="sxs-lookup"><span data-stu-id="193d6-106">The default runspace contains all of the core Windows PowerShell commands.</span></span>
<span data-ttu-id="193d6-107">Wenn Sie Ihre Anwendung nur eine Teilmenge der Windows PowerShell-Befehle verfügbar machen möchten, müssen Sie einen benutzerdefinierten Runspace erstellen.</span><span class="sxs-lookup"><span data-stu-id="193d6-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="193d6-108">Mithilfe der standardmäßigen runspace</span><span class="sxs-lookup"><span data-stu-id="193d6-108">Using the default runspace</span></span>

<span data-ttu-id="193d6-109">Zum Starten wir den standardmäßigen Runspace verwenden und mit den Methoden der der [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) Klasse, um Befehle, Parameter, Anweisungen und Skripts zu einer Pipeline hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="193d6-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="193d6-110">AddCommand</span><span class="sxs-lookup"><span data-stu-id="193d6-110">AddCommand</span></span>

<span data-ttu-id="193d6-111">Sie verwenden die [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) Methode, um Befehle an die Pipeline hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="193d6-111">You use the [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method to add commands to the pipeline.</span></span>
<span data-ttu-id="193d6-112">Nehmen wir beispielsweise an, dass die Liste der ausgeführten Prozesse auf dem Computer abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="193d6-112">For example, suppose you want to get the list of running processes on the machine.</span></span>
<span data-ttu-id="193d6-113">Die Möglichkeit zum Ausführen dieses Befehls lautet wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="193d6-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="193d6-114">Erstellen Sie eine [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) Objekt.</span><span class="sxs-lookup"><span data-stu-id="193d6-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="193d6-115">Fügen Sie den Befehl aus, dem Sie ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="193d6-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="193d6-116">Rufen Sie den Befehl.</span><span class="sxs-lookup"><span data-stu-id="193d6-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="193d6-117">Wenn die AddCommand-Methode mehrmals aufrufen, vor dem Aufruf der [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) -Methode, das Ergebnis des ersten Befehls über die Pipeline an das zweite und So weiter.</span><span class="sxs-lookup"><span data-stu-id="193d6-117">If you call the AddCommand method more than once before you call the [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span>
<span data-ttu-id="193d6-118">Wenn Sie nicht das Ergebnis eines vorherigen Befehls an einen Befehl übergeben möchten, fügen Sie ihn durch Aufrufen der [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) stattdessen.</span><span class="sxs-lookup"><span data-stu-id="193d6-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="193d6-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="193d6-119">AddParameter</span></span>

<span data-ttu-id="193d6-120">Im vorherige Beispiel führt einen einzelnen Befehl ohne Parameter aus.</span><span class="sxs-lookup"><span data-stu-id="193d6-120">The previous example executes a single command without any parameters.</span></span>
<span data-ttu-id="193d6-121">Sie können Parameter an den Befehl hinzufügen, mit der [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) Methode.</span><span class="sxs-lookup"><span data-stu-id="193d6-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method.</span></span>
<span data-ttu-id="193d6-122">Der folgende Code ruft beispielsweise eine Liste aller Prozesse mit dem Namen `PowerShell` auf dem Computer ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="193d6-122">For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="193d6-123">Sie können zusätzliche Parameter hinzufügen, durch die AddParameter Methode wiederholt aufrufen.</span><span class="sxs-lookup"><span data-stu-id="193d6-123">You can add additional parameters by calling the AddParameter method repeatedly.</span></span>

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

<span data-ttu-id="193d6-124">Sie können auch ein Wörterbuch von Parameternamen und Werte hinzufügen, durch den Aufruf der [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) Methode.</span><span class="sxs-lookup"><span data-stu-id="193d6-124">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="193d6-125">AddStatement</span><span class="sxs-lookup"><span data-stu-id="193d6-125">AddStatement</span></span>

<span data-ttu-id="193d6-126">Sie können mithilfe von Batchverarbeitung simulieren die [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) -Methode, die eine zusätzliche Anweisung bis zum Ende der Pipeline hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="193d6-126">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline.</span></span>
<span data-ttu-id="193d6-127">Der folgende Code Ruft eine Liste der ausgeführten Prozesse mit dem Namen `PowerShell`, und ruft anschließend die Liste der ausgeführten Dienste.</span><span class="sxs-lookup"><span data-stu-id="193d6-127">The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="193d6-128">AddScript</span><span class="sxs-lookup"><span data-stu-id="193d6-128">AddScript</span></span>

<span data-ttu-id="193d6-129">Sie können ein vorhandenes Skript ausführen, durch den Aufruf der [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) Methode.</span><span class="sxs-lookup"><span data-stu-id="193d6-129">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span>
<span data-ttu-id="193d6-130">Im folgenden Beispiel wird die Pipeline ein Skript hinzugefügt und wird ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="193d6-130">The following example adds a script to the pipeline and runs it.</span></span>
<span data-ttu-id="193d6-131">In diesem Beispiel wird vorausgesetzt, es ist bereits ein Skript namens `MyScript.ps1` in einem Ordner namens `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="193d6-131">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="193d6-132">Es gibt auch eine Version der Methode, die einen booleschen namens Parameter AddScript `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="193d6-132">There is also a version of the AddScript method that takes a boolean parameter named `useLocalScope`.</span></span>
<span data-ttu-id="193d6-133">Wenn dieser Parameter, um festgelegt wird `true`, und klicken Sie dann das Skript im lokalen Bereich ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="193d6-133">If this parameter is set to `true`, then the script is run in the local scope.</span></span>
<span data-ttu-id="193d6-134">Der folgende Code führt das Skript im lokalen Bereich.</span><span class="sxs-lookup"><span data-stu-id="193d6-134">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="193d6-135">Erstellen einen benutzerdefinierten runspace</span><span class="sxs-lookup"><span data-stu-id="193d6-135">Creating a custom runspace</span></span>

<span data-ttu-id="193d6-136">Während der in den vorherigen Beispielen verwendete standardrunspace aller Befehle verwenden Windows PowerShell Core geladen wird, können Sie einen benutzerdefinierten Runspace erstellen, der nur eine angegebene Teilmenge aller Befehle lädt.</span><span class="sxs-lookup"><span data-stu-id="193d6-136">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span>
<span data-ttu-id="193d6-137">Möglicherweise möchten Sie hierzu zur Verbesserung der Leistung (Laden eine größere Anzahl von Befehlen ist eine leistungsverschlechterung), oder die Funktionalität des Benutzers für Vorgänge einschränken.</span><span class="sxs-lookup"><span data-stu-id="193d6-137">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span>
<span data-ttu-id="193d6-138">Ein Runspace, der nur eine begrenzte Anzahl von Befehlen verfügbar macht, wird einen eingeschränkten Runspace aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="193d6-138">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span>
<span data-ttu-id="193d6-139">Um einem eingeschränkten Runspace zu erstellen, verwenden Sie die [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) und [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) Klassen.</span><span class="sxs-lookup"><span data-stu-id="193d6-139">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="193d6-140">Erstellen eines Objekts InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="193d6-140">Creating an InitialSessionState object</span></span>

<span data-ttu-id="193d6-141">Um einen benutzerdefinierten Runspace zu erstellen, erstellen Sie zuerst eine [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) Objekt.</span><span class="sxs-lookup"><span data-stu-id="193d6-141">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>
<span data-ttu-id="193d6-142">Im folgenden Beispiel verwenden wir die [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) , einen Runspace erstellen, nach dem Erstellen eines standardmäßigen InitialSessionState-Objekts.</span><span class="sxs-lookup"><span data-stu-id="193d6-142">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default InitialSessionState object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="193d6-143">Einschränken des Runspaces</span><span class="sxs-lookup"><span data-stu-id="193d6-143">Constraining the runspace</span></span>

<span data-ttu-id="193d6-144">Im vorherigen Beispiel erstellten wir den Standardwert [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt, das alle von der integrierten Windows PowerShell-Kern lädt.</span><span class="sxs-lookup"><span data-stu-id="193d6-144">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span>
<span data-ttu-id="193d6-145">Wir könnten auch aufgerufen haben die [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) Methode zum Erstellen eines InitialSessionState-Objekts, das nur die Befehle in der Microsoft.PowerShell.Core laden -Snap-in.</span><span class="sxs-lookup"><span data-stu-id="193d6-145">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span>
<span data-ttu-id="193d6-146">Um einen stärker eingeschränkten Runspace zu erstellen, müssen Sie ein leeres InitialSessionState-Objekt erstellen, durch den Aufruf der [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) -Methode, und fügen Sie dann die Befehle aus, um die InitialSessionState.</span><span class="sxs-lookup"><span data-stu-id="193d6-146">To create a more constrained runspace, you must create an empty InitialSessionState object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="193d6-147">Mit dem Runspace, der nur die Befehle, die Sie angeben, lädt bietet erheblich bessere Leistung.</span><span class="sxs-lookup"><span data-stu-id="193d6-147">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="193d6-148">Sie verwenden die Methoden der [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) Klasse, um Cmdlets für den anfänglichen Sitzungsstatus zu definieren.</span><span class="sxs-lookup"><span data-stu-id="193d6-148">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>
<span data-ttu-id="193d6-149">Das folgende Beispiel erstellt eine leere anfänglichen Sitzungsstatus, und klicken Sie dann definiert und fügt die `Get-Command` und `Import-Module` Befehle aus, um den anfänglichen Sitzungsstatus.</span><span class="sxs-lookup"><span data-stu-id="193d6-149">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span>
<span data-ttu-id="193d6-150">Anschließend erstellen wir einen Runspace, die von diesem anfänglichen Sitzungsstatus eingeschränkt, und führen Sie die Befehle in diesen Runspace.</span><span class="sxs-lookup"><span data-stu-id="193d6-150">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="193d6-151">Erstellen Sie den anfänglichen Sitzungsstatus.</span><span class="sxs-lookup"><span data-stu-id="193d6-151">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="193d6-152">Definieren und Hinzufügen von Befehlen zu den anfänglichen Sitzungsstatus.</span><span class="sxs-lookup"><span data-stu-id="193d6-152">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="193d6-153">Erstellen und Öffnen des Runspaces.</span><span class="sxs-lookup"><span data-stu-id="193d6-153">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="193d6-154">Führt einen Befehl aus, und zeigen das Ergebnis.</span><span class="sxs-lookup"><span data-stu-id="193d6-154">Execute a command and show the result.</span></span>

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

<span data-ttu-id="193d6-155">Bei der Ausführung wird die Ausgabe dieses Codes wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="193d6-155">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
