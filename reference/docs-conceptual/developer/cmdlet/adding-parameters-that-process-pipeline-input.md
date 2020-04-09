---
title: Hinzufügen von Parametern, die Pipeline Eingaben verarbeiten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: 4966ac274713899e7ea9e0c375dca220a972a1b5
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978728"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="f9c99-102">Hinzufügen von Parametern, die Pipelineeingaben verarbeiten</span><span class="sxs-lookup"><span data-stu-id="f9c99-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="f9c99-103">Eine Eingabe Quelle für ein Cmdlet ist ein Objekt in der Pipeline, das aus einem Upstream-Cmdlet stammt.</span><span class="sxs-lookup"><span data-stu-id="f9c99-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="f9c99-104">In diesem Abschnitt wird beschrieben, wie Sie dem Get-proc-Cmdlet (beschrieben unter [Erstellen des ersten Cmdlets](./creating-a-cmdlet-without-parameters.md)) einen Parameter hinzufügen, damit das Cmdlet Pipeline Objekte verarbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="f9c99-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="f9c99-105">Dieses Get-proc-Cmdlet verwendet einen `Name` Parameter, der Eingaben von einem Pipeline Objekt akzeptiert, Prozessinformationen auf der Grundlage der angegebenen Namen vom lokalen Computer abruft und dann Informationen zu den Prozessen in der Befehlszeile anzeigt.</span><span class="sxs-lookup"><span data-stu-id="f9c99-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="f9c99-106">Definieren der Cmdlet-Klasse</span><span class="sxs-lookup"><span data-stu-id="f9c99-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="f9c99-107">Der erste Schritt bei der Cmdlet-Erstellung ist die Benennung des Cmdlets und das Deklarieren der .NET-Klasse, die das Cmdlet implementiert.</span><span class="sxs-lookup"><span data-stu-id="f9c99-107">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="f9c99-108">Dieses Cmdlet ruft Prozessinformationen ab, daher lautet der hier gewählte Verb Name "Get".</span><span class="sxs-lookup"><span data-stu-id="f9c99-108">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="f9c99-109">(Fast jede Art von Cmdlet, das Informationen abrufen kann, kann die Befehlszeilen Eingabe verarbeiten.) Weitere Informationen zu genehmigten Cmdlet-Verben finden Sie unter [Cmdlet-Verb Namen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="f9c99-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="f9c99-110">Im folgenden finden Sie die Definition für dieses Get-proc-Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f9c99-110">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="f9c99-111">Einzelheiten zu dieser Definition finden Sie unter [Erstellen des ersten Cmdlets](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="f9c99-111">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="f9c99-112">Definieren von Eingaben aus der Pipeline</span><span class="sxs-lookup"><span data-stu-id="f9c99-112">Defining Input from the Pipeline</span></span>

<span data-ttu-id="f9c99-113">In diesem Abschnitt wird beschrieben, wie Eingaben aus der Pipeline für ein Cmdlet definiert werden.</span><span class="sxs-lookup"><span data-stu-id="f9c99-113">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="f9c99-114">Dieses Get-proc-Cmdlet definiert eine Eigenschaft, die den `Name`-Parameter darstellt, wie unter [Hinzufügen von Parametern zur Verarbeitung der Befehlszeilen Eingabe](./adding-parameters-that-process-command-line-input.md)beschrieben.</span><span class="sxs-lookup"><span data-stu-id="f9c99-114">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>
<span data-ttu-id="f9c99-115">(In diesem Thema finden Sie allgemeine Informationen zum Deklarieren von Parametern.)</span><span class="sxs-lookup"><span data-stu-id="f9c99-115">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="f9c99-116">Wenn jedoch ein Cmdlet Pipeline Eingaben verarbeiten muss, muss die Parameter von der Windows PowerShell-Laufzeit an die Eingabewerte gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="f9c99-116">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="f9c99-117">Zu diesem Zweck müssen Sie das `ValueFromPipeline`-Schlüsselwort hinzufügen oder das `ValueFromPipelineByProperty`-Schlüsselwort der [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Attribut Deklaration hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f9c99-117">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="f9c99-118">Geben Sie das `ValueFromPipeline`-Schlüsselwort an, wenn das Cmdlet auf das gesamte Eingabe Objekt zugreift.</span><span class="sxs-lookup"><span data-stu-id="f9c99-118">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="f9c99-119">Geben Sie den `ValueFromPipelineByProperty` an, wenn das Cmdlet nur auf eine Eigenschaft des Objekts zugreift.</span><span class="sxs-lookup"><span data-stu-id="f9c99-119">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="f9c99-120">Im folgenden finden Sie die Parameter Deklaration für den `Name`-Parameter dieses Get-proc-Cmdlets, das Pipeline Eingaben annimmt.</span><span class="sxs-lookup"><span data-stu-id="f9c99-120">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="35-44":::

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

<span data-ttu-id="f9c99-121">In der vorherigen Deklaration wird das `ValueFromPipeline`-Schlüsselwort auf `true` festgelegt, damit die Windows PowerShell-Laufzeit den Parameter an das eingehende Objekt bindet, wenn das Objekt dem gleichen Typ wie der-Parameter entspricht, oder, wenn es in denselben Typ umgewandelt werden kann.</span><span class="sxs-lookup"><span data-stu-id="f9c99-121">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="f9c99-122">Das `ValueFromPipelineByPropertyName`-Schlüsselwort ist auch auf `true` festgelegt, damit die Windows PowerShell-Laufzeit das eingehende Objekt auf eine `Name` Eigenschaft überprüft.</span><span class="sxs-lookup"><span data-stu-id="f9c99-122">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="f9c99-123">Wenn das eingehende Objekt eine solche Eigenschaft aufweist, bindet die Laufzeit den `Name`-Parameter an die `Name`-Eigenschaft des eingehenden Objekts.</span><span class="sxs-lookup"><span data-stu-id="f9c99-123">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="f9c99-124">Die Einstellung des `ValueFromPipeline` Attribute-Schlüssel Worts für einen Parameter hat Vorrang vor der-Einstellung für das `ValueFromPipelineByPropertyName`-Schlüsselwort.</span><span class="sxs-lookup"><span data-stu-id="f9c99-124">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="f9c99-125">Überschreiben einer Eingabe Verarbeitungsmethode</span><span class="sxs-lookup"><span data-stu-id="f9c99-125">Overriding an Input Processing Method</span></span>

<span data-ttu-id="f9c99-126">Wenn das Cmdlet Pipeline Eingaben verarbeiten soll, müssen die entsprechenden Eingabe Verarbeitungsmethoden überschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="f9c99-126">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="f9c99-127">Die grundlegenden Eingabe Verarbeitungsmethoden werden beim [Erstellen des ersten Cmdlets](./creating-a-cmdlet-without-parameters.md)eingeführt.</span><span class="sxs-lookup"><span data-stu-id="f9c99-127">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="f9c99-128">Dieses Get-proc-Cmdlet überschreibt die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode, um die vom Benutzer oder einem Skript bereitgestellten `Name` Parameter Eingaben zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="f9c99-128">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="f9c99-129">Diese Methode erhält die Prozesse für die einzelnen angeforderten Prozessnamen oder alle Prozesse, wenn kein Name angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="f9c99-129">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="f9c99-130">Beachten Sie, dass innerhalb von [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)der Aufrufe von [Write Object (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) der Ausgabe Mechanismus zum Senden von Ausgabe Objekten an die Pipeline ist.</span><span class="sxs-lookup"><span data-stu-id="f9c99-130">Notice that within [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="f9c99-131">Der zweite Parameter dieses Aufrufes, `enumerateCollection`, ist auf `true` festgelegt, um der Windows PowerShell-Laufzeit mitzuteilen, das Array von Prozess Objekten aufzulisten und jeweils einen Prozess in die Befehlszeile zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="f9c99-131">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="f9c99-132">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="f9c99-132">Code Sample</span></span>

<span data-ttu-id="f9c99-133">Den gesamten C# Beispielcode finden Sie unter [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="f9c99-133">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="f9c99-134">Definieren von Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="f9c99-134">Defining Object Types and Formatting</span></span>

<span data-ttu-id="f9c99-135">Windows PowerShell übergibt Informationen zwischen Cmdlets mithilfe von .NET-Objekten.</span><span class="sxs-lookup"><span data-stu-id="f9c99-135">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="f9c99-136">Folglich muss ein Cmdlet möglicherweise seinen eigenen Typ definieren, oder das Cmdlet muss möglicherweise einen vorhandenen Typ erweitern, der von einem anderen Cmdlet bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="f9c99-136">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="f9c99-137">Weitere Informationen zum Definieren neuer Typen oder zum Erweitern vorhandener Typen finden Sie unter [Erweitern von Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="f9c99-137">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="f9c99-138">Cmdlet wird aufgebaut</span><span class="sxs-lookup"><span data-stu-id="f9c99-138">Building the Cmdlet</span></span>

<span data-ttu-id="f9c99-139">Nachdem Sie ein Cmdlet implementiert haben, muss es über ein Windows PowerShell-Snap-in in Windows PowerShell registriert werden.</span><span class="sxs-lookup"><span data-stu-id="f9c99-139">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="f9c99-140">Weitere Informationen zum Registrieren von Cmdlets finden [Sie unter Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="f9c99-140">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="f9c99-141">Testen des Cmdlets</span><span class="sxs-lookup"><span data-stu-id="f9c99-141">Testing the Cmdlet</span></span>

<span data-ttu-id="f9c99-142">Wenn das Cmdlet bei Windows PowerShell registriert wurde, testen Sie es, indem Sie es in der Befehlszeile ausführen.</span><span class="sxs-lookup"><span data-stu-id="f9c99-142">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="f9c99-143">Testen Sie z. b. den Code für das Beispiel-Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f9c99-143">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="f9c99-144">Weitere Informationen zur Verwendung von Cmdlets über die Befehlszeile finden Sie unter [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="f9c99-144">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="f9c99-145">Geben Sie an der Windows PowerShell-Eingabeaufforderung die folgenden Befehle ein, um die Prozessnamen über die Pipeline abzurufen.</span><span class="sxs-lookup"><span data-stu-id="f9c99-145">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

  ```powershell
  PS> type ProcessNames | get-proc
  ```

  <span data-ttu-id="f9c99-146">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f9c99-146">The following output appears.</span></span>

  ```
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
  -------  ------  -----   ----- -----   ------    --  -----------
      809      21  40856    4448    147    9.50  2288  iexplore
      737      21  26036   16348    144   22.03  3860  iexplore
       39       2   1024     388     30    0.08  3396  notepad
     3927      62  71836   26984    467  195.19  1848  OUTLOOK
  ```

- <span data-ttu-id="f9c99-147">Geben Sie die folgenden Zeilen ein, um die Prozess Objekte zu erhalten, die über eine `Name`-Eigenschaft aus den Prozessen mit dem Namen "Iexplore" verfügen.</span><span class="sxs-lookup"><span data-stu-id="f9c99-147">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="f9c99-148">In diesem Beispiel wird das `Get-Process`-Cmdlet (von Windows PowerShell bereitgestellt) als upstreambefehl zum Abrufen der iexplore-Prozesse verwendet.</span><span class="sxs-lookup"><span data-stu-id="f9c99-148">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

  ```powershell
  PS> get-process iexplore | get-proc
  ```

  <span data-ttu-id="f9c99-149">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f9c99-149">The following output appears.</span></span>

  ```
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
  -------  ------  -----   ----- -----   ------    --  -----------
      801      21  40720    6544    142    9.52  2288  iexplore
      726      21  25872   16652    138   22.09  3860  iexplore
      801      21  40720    6544    142    9.52  2288  iexplore
      726      21  25872   16652    138   22.09  3860  iexplore
  ```

## <a name="see-also"></a><span data-ttu-id="f9c99-150">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f9c99-150">See Also</span></span>

[<span data-ttu-id="f9c99-151">Hinzufügen von Parametern zur Verarbeitung der Befehlszeilen Eingabe</span><span class="sxs-lookup"><span data-stu-id="f9c99-151">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="f9c99-152">Erstellen Ihres ersten Cmdlets</span><span class="sxs-lookup"><span data-stu-id="f9c99-152">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

<span data-ttu-id="f9c99-153">[Erweitern von Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="f9c99-153">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="f9c99-154">[Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="f9c99-154">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="f9c99-155">Windows PowerShell-Referenz</span><span class="sxs-lookup"><span data-stu-id="f9c99-155">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="f9c99-156">Cmdlet-Beispiele</span><span class="sxs-lookup"><span data-stu-id="f9c99-156">Cmdlet Samples</span></span>](./cmdlet-samples.md)
