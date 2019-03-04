---
title: Hinzufügen von Parametern, die Pipelineeingabe verarbeiten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: c790d20a792bcdb4a34485e53375560e129433a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854536"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="12ba9-102">Hinzufügen von Parametern, die Pipelineeingaben verarbeiten</span><span class="sxs-lookup"><span data-stu-id="12ba9-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="12ba9-103">Eine Ursache für die Eingabe für ein Cmdlet handelt es sich um ein Objekt für die Pipeline, die von einem upstream-Cmdlet stammt.</span><span class="sxs-lookup"><span data-stu-id="12ba9-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="12ba9-104">In diesem Abschnitt wird beschrieben, wie zum Hinzufügen eines Parameters an das Get-Proc-Cmdlet (beschrieben [Erstellen Ihrer ersten Cmdlet](./creating-a-cmdlet-without-parameters.md)), damit das Cmdlet Pipelineobjekte verarbeitet werden kann.</span><span class="sxs-lookup"><span data-stu-id="12ba9-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="12ba9-105">Das Get-Proc-Cmdlet verwendet einen `Name` Parameter, die Eingaben von einem Pipelineobjekt akzeptiert Prozess auf dem lokalen Computer, die basierend auf den angegebenen Namen abruft und anschließend Informationen über die Prozesse in der Befehlszeile angezeigt.</span><span class="sxs-lookup"><span data-stu-id="12ba9-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

<span data-ttu-id="12ba9-106">Die folgenden: Themen in diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="12ba9-106">Topics in this section include the following:</span></span>

- [<span data-ttu-id="12ba9-107">Definieren die Cmdlet-Klasse</span><span class="sxs-lookup"><span data-stu-id="12ba9-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="12ba9-108">Definieren von Eingaben aus der Pipeline</span><span class="sxs-lookup"><span data-stu-id="12ba9-108">Defining Input from the Pipeline</span></span>](#Defining-Input-from-the-Pipeline)

- [<span data-ttu-id="12ba9-109">Überschreiben einer Eingabeverarbeitungsmethode</span><span class="sxs-lookup"><span data-stu-id="12ba9-109">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="12ba9-110">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="12ba9-110">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="12ba9-111">Definieren von Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="12ba9-111">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="12ba9-112">Erstellen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="12ba9-112">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="12ba9-113">Testen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="12ba9-113">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="12ba9-114">Definieren die Cmdlet-Klasse</span><span class="sxs-lookup"><span data-stu-id="12ba9-114">Defining the Cmdlet Class</span></span>

<span data-ttu-id="12ba9-115">Der erste Schritt bei der Cmdlet-Erstellung ist immer benennen das Cmdlet und .NET implementiert die Klasse, mit dem-Cmdlet deklarieren.</span><span class="sxs-lookup"><span data-stu-id="12ba9-115">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="12ba9-116">Dieses Cmdlet Ruft die Prozessinformationen, ab, der Namen des Verbs hier ausgewählten also "Get".</span><span class="sxs-lookup"><span data-stu-id="12ba9-116">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="12ba9-117">(Nahezu jede Art von Cmdlets, mit dem Informationen abgerufen werden, kann die Befehlszeileneingabe verarbeiten.) Weitere Informationen zu zulässigen Cmdlet-Verben, finden Sie unter [Cmdlet Verbnamen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="12ba9-117">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="12ba9-118">Im folgenden finden die Definition für dieses Cmdlet "Get-Proc".</span><span class="sxs-lookup"><span data-stu-id="12ba9-118">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="12ba9-119">Details zu dieser Definition werden in angegebenen [Erstellen Ihrer ersten Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="12ba9-119">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="12ba9-120">Definieren von Eingaben aus der Pipeline</span><span class="sxs-lookup"><span data-stu-id="12ba9-120">Defining Input from the Pipeline</span></span>

<span data-ttu-id="12ba9-121">Dieser Abschnitt beschreibt, wie Sie Eingaben aus der Pipeline für ein Cmdlet definieren.</span><span class="sxs-lookup"><span data-stu-id="12ba9-121">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="12ba9-122">Dieses Cmdlet "Get-Proc" definiert eine Eigenschaft, steht die `Name` Parameter wie in beschrieben [Hinzufügen von Parametern, die Eingabe über die Befehlszeile](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="12ba9-122">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span> <span data-ttu-id="12ba9-123">(Siehe das Thema allgemeine Informationen zum Deklarieren von Parametern.)</span><span class="sxs-lookup"><span data-stu-id="12ba9-123">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="12ba9-124">Wenn ein Cmdlet Pipelineeingabe verarbeiten muss, muss es jedoch seine Parameter an die Eingabe von Werten durch die Windows PowerShell-Laufzeit gebunden haben.</span><span class="sxs-lookup"><span data-stu-id="12ba9-124">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="12ba9-125">Zu diesem Zweck fügen Sie der `ValueFromPipeline` Schlüsselwort oder Hinzufügen der `ValueFromPipelineByProperty` Schlüsselwort, um die [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Attributdeklaration.</span><span class="sxs-lookup"><span data-stu-id="12ba9-125">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="12ba9-126">Geben Sie die `ValueFromPipeline` Schlüsselwort, wenn das Cmdlet das vollständige Eingabeobjekt greift auf.</span><span class="sxs-lookup"><span data-stu-id="12ba9-126">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="12ba9-127">Geben Sie die `ValueFromPipelineByProperty` , wenn das Cmdlet greift, nur eine Eigenschaft des Objekts auf.</span><span class="sxs-lookup"><span data-stu-id="12ba9-127">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="12ba9-128">Hier folgt die Parameterdeklaration für die `Name` Parameter des Cmdlets Get-Proc, die Pipelineeingabe akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="12ba9-128">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

<span data-ttu-id="12ba9-129">Im vorherigen Deklaration wird das `ValueFromPipeline` Schlüsselwort `true` , damit die Windows PowerShell-Laufzeit den Parameter auf das eingehende Objekt gebunden wird, wenn das Objekt den gleichen Typ wie der Parameter ist oder wenn es in den gleichen Typ umgewandelt werden kann.</span><span class="sxs-lookup"><span data-stu-id="12ba9-129">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="12ba9-130">Die `ValueFromPipelineByPropertyName` Schlüsselwort wird ebenfalls für festgelegt `true` , damit die Windows PowerShell-Laufzeit überprüft das eingehende Objekt für eine `Name` Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="12ba9-130">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="12ba9-131">Wenn das eingehende Objekt um eine solche Eigenschaft verfügt, kann die Laufzeit verbindet die `Name` Parameter, um die `Name` -Eigenschaft des eingehenden Objekts.</span><span class="sxs-lookup"><span data-stu-id="12ba9-131">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="12ba9-132">Die Einstellung der `ValueFromPipeline` Attribut Schlüsselwort, für die Einstellung für ein Parameter Vorrang vor hat der `ValueFromPipelineByPropertyName` Schlüsselwort.</span><span class="sxs-lookup"><span data-stu-id="12ba9-132">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="12ba9-133">Überschreiben einer Eingabeverarbeitungsmethode</span><span class="sxs-lookup"><span data-stu-id="12ba9-133">Overriding an Input Processing Method</span></span>

<span data-ttu-id="12ba9-134">Ist Ihr Cmdlet Pipelineeingabe behandelt, muss sie die entsprechenden eingabeverarbeitungsmethoden außer Kraft zu setzen.</span><span class="sxs-lookup"><span data-stu-id="12ba9-134">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="12ba9-135">Die grundlegende eingabeverarbeitungsmethoden entstehen in [Erstellen Ihrer ersten Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="12ba9-135">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="12ba9-136">Dieses Cmdlet "Get-Proc" überschreibt die [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode zum Behandeln der `Name` Parametereingabe, die durch den Benutzer oder ein Skript bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="12ba9-136">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="12ba9-137">Diese Methode erhalten die Prozesse für jede angeforderte Prozessname oder allen Prozessen, wenn kein Name angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="12ba9-137">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="12ba9-138">Beachten Sie, dass in [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), den Aufruf von [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) ist die Ausgabemechanismus zum Senden von Ausgabeobjekte an die Pipeline.</span><span class="sxs-lookup"><span data-stu-id="12ba9-138">Notice that within [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="12ba9-139">Der zweite Parameter des Aufrufs, `enumerateCollection`, nastaven NA hodnotu `true` informieren die Windows PowerShell-Laufzeit zum Auflisten von Arrays von Prozessobjekten und Schreiben einen Prozess zu einem Zeitpunkt, an die Befehlszeile.</span><span class="sxs-lookup"><span data-stu-id="12ba9-139">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument of this call tells
      // PowerShell to enumerate the array, and send one process at a
      // time to the pipeline.
      WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="12ba9-140">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="12ba9-140">Code Sample</span></span>

<span data-ttu-id="12ba9-141">Für die vollständige C# Beispielcode, finden Sie unter [Beispiel mit GetProcessSample03](./getprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="12ba9-141">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="12ba9-142">Definieren von Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="12ba9-142">Defining Object Types and Formatting</span></span>

<span data-ttu-id="12ba9-143">Windows PowerShell übergibt Informationen zwischen Cmdlets, die mithilfe von .NET-Objekten.</span><span class="sxs-lookup"><span data-stu-id="12ba9-143">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="12ba9-144">Daher müssen möglicherweise ein Cmdlet seinen eigenen Typ definieren, oder das-Cmdlet zum Erweitern eines vorhandenen Typs, der durch ein anderes Cmdlet angegeben müssen.</span><span class="sxs-lookup"><span data-stu-id="12ba9-144">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="12ba9-145">Weitere Informationen zum Definieren neuer Typen, oder erweitern vorhandene Typen finden Sie unter [Objekttypen erweitern und Formatierung](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="12ba9-145">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="12ba9-146">Erstellen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="12ba9-146">Building the Cmdlet</span></span>

<span data-ttu-id="12ba9-147">Nach der Implementierung eines Cmdlets müssen sie über ein Windows PowerShell-Snap-in mit Windows PowerShell registriert werden.</span><span class="sxs-lookup"><span data-stu-id="12ba9-147">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="12ba9-148">Weitere Informationen zum Registrieren von Cmdlets finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="12ba9-148">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="12ba9-149">Testen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="12ba9-149">Testing the Cmdlet</span></span>

<span data-ttu-id="12ba9-150">Wenn Ihr Cmdlet in Windows PowerShell registriert wurde, testen Sie es in der Befehlszeile aus ausführen.</span><span class="sxs-lookup"><span data-stu-id="12ba9-150">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="12ba9-151">Testen Sie z. B. den Code für die Beispiel-Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="12ba9-151">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="12ba9-152">Weitere Informationen zur Verwendung von Cmdlets, über die Befehlszeile finden Sie unter den [erste Schritte mit Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="12ba9-152">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="12ba9-153">Geben Sie an der Windows PowerShell-Eingabeaufforderung die folgenden Befehle zum Abrufen der Namen der entsprechenden Prozesse über die Pipeline aus.</span><span class="sxs-lookup"><span data-stu-id="12ba9-153">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

    ```powershell
    PS> type ProcessNames | get-proc
    ```

<span data-ttu-id="12ba9-154">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="12ba9-154">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- <span data-ttu-id="12ba9-155">Geben Sie die folgenden Zeilen rufen die Prozessobjekte, die eine `Name` Eigenschaft von den Prozessen, die Namen "IEXPLORE".</span><span class="sxs-lookup"><span data-stu-id="12ba9-155">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="12ba9-156">Dieses Beispiel verwendet die `Get-Process` Cmdlet (bereitgestellt vom Windows PowerShell) als upstream-Befehl zum Abrufen der Prozesse "IEXPLORE".</span><span class="sxs-lookup"><span data-stu-id="12ba9-156">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

    ```powershell
    PS> get-process iexplore | get-proc
    ```

<span data-ttu-id="12ba9-157">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="12ba9-157">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a><span data-ttu-id="12ba9-158">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="12ba9-158">See Also</span></span>

[<span data-ttu-id="12ba9-159">Hinzufügen von Parametern, die über die Befehlszeileneingabe verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="12ba9-159">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="12ba9-160">Erstellen eines ersten Cmdlets</span><span class="sxs-lookup"><span data-stu-id="12ba9-160">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="12ba9-161">Erweitern die Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="12ba9-161">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="12ba9-162">So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen</span><span class="sxs-lookup"><span data-stu-id="12ba9-162">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="12ba9-163">Windows PowerShell-Referenz</span><span class="sxs-lookup"><span data-stu-id="12ba9-163">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="12ba9-164">Cmdlet-Beispiele</span><span class="sxs-lookup"><span data-stu-id="12ba9-164">Cmdlet Samples</span></span>](./cmdlet-samples.md)
