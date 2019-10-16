---
title: Hinzufügen von Parametern, die Befehlszeilen Eingaben verarbeiten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: 7db93af33717dc4802ed915793f6cd570cfb48f6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364629"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="dbe52-102">Hinzufügen von Parametern, die Befehlszeileneingaben verarbeiten</span><span class="sxs-lookup"><span data-stu-id="dbe52-102">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="dbe52-103">Eine Eingabe Quelle für ein Cmdlet ist die Befehlszeile.</span><span class="sxs-lookup"><span data-stu-id="dbe52-103">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="dbe52-104">In diesem Thema wird beschrieben, wie Sie dem **Get-proc-** Cmdlet (das unter Erstellen des [ersten Cmdlets](./creating-a-cmdlet-without-parameters.md)beschrieben wird) einen Parameter hinzufügen, damit das Cmdlet Eingaben vom lokalen Computer auf der Grundlage von expliziten Objekten verarbeiten kann, die an das Cmdlet übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="dbe52-104">This topic describes how to add a parameter to the **Get-Proc** cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="dbe52-105">Das hier beschriebene **Get-proc-** Cmdlet ruft Prozesse auf Grundlage ihrer Namen ab und zeigt dann Informationen zu den Prozessen an einer Eingabeaufforderung an.</span><span class="sxs-lookup"><span data-stu-id="dbe52-105">The **Get-Proc** cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="dbe52-106">Definieren der Cmdlet-Klasse</span><span class="sxs-lookup"><span data-stu-id="dbe52-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="dbe52-107">Der erste Schritt bei der Cmdlet-Erstellung ist die Cmdlet-Benennung und die Deklaration der .NET Framework Klasse, die das Cmdlet implementiert.</span><span class="sxs-lookup"><span data-stu-id="dbe52-107">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="dbe52-108">Dieses Cmdlet ruft Prozessinformationen ab, sodass der hier gewählte Verb Name "Get" lautet.</span><span class="sxs-lookup"><span data-stu-id="dbe52-108">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="dbe52-109">(Fast jede Art von Cmdlet, das Informationen abrufen kann, kann die Befehlszeilen Eingabe verarbeiten.) Weitere Informationen zu genehmigten Cmdlet-Verben finden Sie unter [Cmdlet-Verb Namen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="dbe52-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="dbe52-110">Hier ist die Klassen Deklaration für das **Get-proc-** Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dbe52-110">Here's the class declaration for the **Get-Proc** cmdlet.</span></span> <span data-ttu-id="dbe52-111">Details zu dieser Definition finden Sie unter [Erstellen des ersten Cmdlets](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="dbe52-111">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="dbe52-112">Deklarieren der Parameter</span><span class="sxs-lookup"><span data-stu-id="dbe52-112">Declaring Parameters</span></span>

<span data-ttu-id="dbe52-113">Mit einem Cmdlet-Parameter kann der Benutzereingaben für das Cmdlet bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="dbe52-113">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="dbe52-114">Im folgenden Beispiel sind **Get-proc** und `Get-Member` die Namen von Pipeline-Cmdlets, und `MemberType` ist ein Parameter für das Cmdlet `Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="dbe52-114">In the following example, **Get-Proc** and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="dbe52-115">Der-Parameter hat das Argument "Property".</span><span class="sxs-lookup"><span data-stu-id="dbe52-115">The parameter has the argument "property."</span></span>

<span data-ttu-id="dbe52-116">**PS > Get-proc; `get-member`-Mitgliedschaftstyp (Eigenschaft)**</span><span class="sxs-lookup"><span data-stu-id="dbe52-116">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="dbe52-117">Um Parameter für ein Cmdlet zu deklarieren, müssen Sie zunächst die Eigenschaften definieren, die die Parameter darstellen.</span><span class="sxs-lookup"><span data-stu-id="dbe52-117">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="dbe52-118">Im **Get-proc-** Cmdlet ist der einzige Parameter `Name`, der in diesem Fall den Namen des abzurufenden .NET Framework Prozess Objekts darstellt.</span><span class="sxs-lookup"><span data-stu-id="dbe52-118">In the **Get-Proc** cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="dbe52-119">Daher definiert die Cmdlet-Klasse eine Eigenschaft vom Typ "String", um ein Array von Namen zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="dbe52-119">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="dbe52-120">Hier ist die Parameter Deklaration für den `Name`-Parameter des **Get-proc-** Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="dbe52-120">Here's the parameter declaration for the `Name` parameter of the **Get-Proc** cmdlet.</span></span>

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<span data-ttu-id="dbe52-121">Um die Windows PowerShell-Laufzeit darüber zu informieren, dass diese Eigenschaft der `Name`-Parameter ist, wird der Eigenschafts Definition ein [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Attribut hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="dbe52-121">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="dbe52-122">Die grundlegende Syntax zum Deklarieren dieses Attributs ist `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="dbe52-122">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="dbe52-123">Ein Parameter muss explizit als public gekennzeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="dbe52-123">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="dbe52-124">Parameter, die nicht als öffentlich gekennzeichnet sind, sind standardmäßig intern und werden von der Windows PowerShell-Laufzeit nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="dbe52-124">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="dbe52-125">Dieses Cmdlet verwendet ein Zeichen folgen Array für den Parameter "`Name`".</span><span class="sxs-lookup"><span data-stu-id="dbe52-125">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="dbe52-126">Wenn möglich, sollte Ihr Cmdlet auch einen Parameter als Array definieren, da das Cmdlet somit mehr als ein Element annehmen kann.</span><span class="sxs-lookup"><span data-stu-id="dbe52-126">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="dbe52-127">Dinge, die Sie über Parameter Definitionen merken müssen</span><span class="sxs-lookup"><span data-stu-id="dbe52-127">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="dbe52-128">Vordefinierte Windows PowerShell-Parameternamen und-Datentypen sollten so weit wie möglich wieder verwendet werden, um sicherzustellen, dass Ihr Cmdlet mit Windows PowerShell-Cmdlets kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="dbe52-128">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="dbe52-129">Wenn beispielsweise alle Cmdlets den vordefinierten `Id`-Parameternamen verwenden, um eine Ressource zu identifizieren, kann der Benutzer die Bedeutung des Parameters unabhängig davon, welches Cmdlet verwendet wird, leicht verstehen.</span><span class="sxs-lookup"><span data-stu-id="dbe52-129">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="dbe52-130">Im Grunde folgen Parameternamen denselben Regeln wie die, die für Variablennamen im Common Language Runtime (CLR) verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="dbe52-130">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="dbe52-131">Weitere Informationen zum Benennen von Parametern finden [Sie unter Cmdlet-Parameternamen](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span><span class="sxs-lookup"><span data-stu-id="dbe52-131">For more information about parameter naming, see [Cmdlet Parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span></span>

- <span data-ttu-id="dbe52-132">Windows PowerShell reserviert einige Parameternamen, um eine konsistente Benutzer Leistung zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="dbe52-132">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="dbe52-133">Verwenden Sie diese Parameternamen nicht: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable` und `OutBuffer`.</span><span class="sxs-lookup"><span data-stu-id="dbe52-133">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="dbe52-134">Außerdem sind die folgenden Aliase für diese Parameternamen reserviert: `vb`, `db`, `ea`, `ev`, `ov` und `ob`.</span><span class="sxs-lookup"><span data-stu-id="dbe52-134">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="dbe52-135">`Name` ist ein einfacher und allgemeiner Parameter Name, der für die Verwendung in ihren Cmdlets empfohlen wird.</span><span class="sxs-lookup"><span data-stu-id="dbe52-135">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="dbe52-136">Es empfiehlt sich, einen Parameternamen wie diesen als einen komplexen Namen auszuwählen, der für ein bestimmtes Cmdlet eindeutig ist und schwer zu merken ist.</span><span class="sxs-lookup"><span data-stu-id="dbe52-136">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="dbe52-137">Bei Parametern wird in Windows PowerShell die Groß-/Kleinschreibung nicht beachtet, obwohl die Shell standardmäßig die groß-</span><span class="sxs-lookup"><span data-stu-id="dbe52-137">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="dbe52-138">Die Groß-/Kleinschreibung der Argumente hängt von der Operation des Cmdlets ab.</span><span class="sxs-lookup"><span data-stu-id="dbe52-138">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="dbe52-139">Argumente werden an einen Parameter übergeben, wie in der Befehlszeile angegeben.</span><span class="sxs-lookup"><span data-stu-id="dbe52-139">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="dbe52-140">Beispiele für andere Parameter Deklarationen finden Sie unter [Cmdlet-Parameter](./cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="dbe52-140">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="dbe52-141">Deklarieren von Parametern als Positions-oder benannte Parameter</span><span class="sxs-lookup"><span data-stu-id="dbe52-141">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="dbe52-142">Ein Cmdlet muss jeden Parameter entweder als Positions Parameter oder als benannten Parameter festlegen.</span><span class="sxs-lookup"><span data-stu-id="dbe52-142">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="dbe52-143">Beide Arten von Parametern akzeptieren einzelne Argumente, mehrere durch Kommas getrennte Argumente und boolesche Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="dbe52-143">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="dbe52-144">Bei einem booleschen Parameter, der auch als *Switch*bezeichnet wird, werden nur boolesche Einstellungen behandelt.</span><span class="sxs-lookup"><span data-stu-id="dbe52-144">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="dbe52-145">Der-Schalter wird verwendet, um das vorhanden sein des-Parameters zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="dbe52-145">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="dbe52-146">Der empfohlene Standardwert ist `false`.</span><span class="sxs-lookup"><span data-stu-id="dbe52-146">The recommended default is `false`.</span></span>

<span data-ttu-id="dbe52-147">Das **Get-proc-** Beispiel Cmdlet definiert den `Name`-Parameter als Positions Parameter mit der Position 0.</span><span class="sxs-lookup"><span data-stu-id="dbe52-147">The sample **Get-Proc** cmdlet defines the `Name` parameter as a positional parameter with position 0.</span></span> <span data-ttu-id="dbe52-148">Dies bedeutet, dass das erste Argument, das der Benutzer in der Befehlszeile eingibt, automatisch für diesen Parameter eingefügt wird.</span><span class="sxs-lookup"><span data-stu-id="dbe52-148">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="dbe52-149">Wenn Sie einen benannten Parameter definieren möchten, für den der Benutzer den Parameternamen in der Befehlszeile angeben muss, lassen Sie das Schlüsselwort `Position` aus der Attribut Deklaration aus.</span><span class="sxs-lookup"><span data-stu-id="dbe52-149">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="dbe52-150">Wenn Parameter nicht benannt werden müssen, empfiehlt es sich, die am häufigsten verwendeten Parameter positionell zu machen, damit Benutzer den Parameternamen nicht eingeben müssen.</span><span class="sxs-lookup"><span data-stu-id="dbe52-150">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="dbe52-151">Deklarieren von Parametern als obligatorisch oder optional</span><span class="sxs-lookup"><span data-stu-id="dbe52-151">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="dbe52-152">Ein Cmdlet muss jeden Parameter entweder als optionalen oder als obligatorischen Parameter festlegen.</span><span class="sxs-lookup"><span data-stu-id="dbe52-152">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="dbe52-153">Im Beispiel- **Get-proc-** Cmdlet wird der `Name`-Parameter als optional definiert, da das Schlüsselwort `Mandatory` nicht in der Attribut Deklaration festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="dbe52-153">In the sample **Get-Proc** cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="dbe52-154">Unterstützende Parameter Validierung</span><span class="sxs-lookup"><span data-stu-id="dbe52-154">Supporting Parameter Validation</span></span>

<span data-ttu-id="dbe52-155">Das **Get-proc-** Beispiel Cmdlet fügt dem `Name`-Parameter ein Eingabe Validierungs Attribut ( [System. Management. Automation. validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute)) hinzu, um die Validierung zu aktivieren, dass die Eingabe weder `null` noch leer ist.</span><span class="sxs-lookup"><span data-stu-id="dbe52-155">The sample **Get-Proc** cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="dbe52-156">Dieses Attribut ist eines von mehreren Validierungs Attributen, die von Windows PowerShell bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="dbe52-156">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="dbe52-157">Beispiele für andere Validierungs Attribute finden Sie unter [Validieren von Parameter Eingaben](./validating-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="dbe52-157">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="dbe52-158">Überschreiben einer Eingabe Verarbeitungsmethode</span><span class="sxs-lookup"><span data-stu-id="dbe52-158">Overriding an Input Processing Method</span></span>

<span data-ttu-id="dbe52-159">Wenn das Cmdlet die Befehlszeilen Eingabe verarbeiten soll, müssen die entsprechenden Eingabe Verarbeitungsmethoden überschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="dbe52-159">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="dbe52-160">Die grundlegenden Eingabe Verarbeitungsmethoden werden beim [Erstellen des ersten Cmdlets](./creating-a-cmdlet-without-parameters.md)eingeführt.</span><span class="sxs-lookup"><span data-stu-id="dbe52-160">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="dbe52-161">Das **Get-proc-** Cmdlet überschreibt die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode, um die vom Benutzer oder einem Skript bereitgestellten `Name`-Parameter Eingaben zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="dbe52-161">The **Get-Proc** cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="dbe52-162">Diese Methode ruft die Prozesse für die einzelnen angeforderten Prozessnamen ab oder alle für Prozesse, wenn kein Name angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="dbe52-162">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="dbe52-163">Beachten Sie, dass in [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)der [System. Management. Automation. Cmdlet. Write-Object% 28system. Object% 2csystem. Boolean %29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) als Ausgabe Mechanismus für das Senden von Ausgabe Objekten an das ine.</span><span class="sxs-lookup"><span data-stu-id="dbe52-163">Notice that in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="dbe52-164">Der zweite Parameter dieses Aufrufes (`enumerateCollection`) ist auf `true` festgelegt, um die Windows PowerShell-Laufzeit anzuweisen, das Ausgabe Array von Prozess Objekten aufzulisten und jeweils einen Prozess in die Befehlszeile zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="dbe52-164">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

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
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="dbe52-165">Code Beispiel</span><span class="sxs-lookup"><span data-stu-id="dbe52-165">Code Sample</span></span>

<span data-ttu-id="dbe52-166">Den gesamten C# Beispielcode finden Sie unter [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="dbe52-166">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="dbe52-167">Definieren von Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="dbe52-167">Defining Object Types and Formatting</span></span>

<span data-ttu-id="dbe52-168">Windows PowerShell übergibt mithilfe .NET Framework-Objekten Informationen zwischen Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="dbe52-168">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="dbe52-169">Folglich muss ein Cmdlet möglicherweise seinen eigenen Typ definieren, oder ein Cmdlet muss möglicherweise einen vorhandenen Typ erweitern, der von einem anderen Cmdlet bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="dbe52-169">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="dbe52-170">Weitere Informationen zum Definieren neuer Typen oder zum Erweitern vorhandener Typen finden Sie unter [Erweitern von Objekttypen und Formatierung](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="dbe52-170">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="dbe52-171">Cmdlet wird aufgebaut</span><span class="sxs-lookup"><span data-stu-id="dbe52-171">Building the Cmdlet</span></span>

<span data-ttu-id="dbe52-172">Nachdem Sie ein Cmdlet implementiert haben, müssen Sie es mithilfe eines Windows PowerShell-Snap-Ins bei Windows PowerShell registrieren.</span><span class="sxs-lookup"><span data-stu-id="dbe52-172">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="dbe52-173">Weitere Informationen zum Registrieren von Cmdlets finden [Sie unter Registrieren von Cmdlets, Anbietern und Host Anwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="dbe52-173">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="dbe52-174">Testen des Cmdlets</span><span class="sxs-lookup"><span data-stu-id="dbe52-174">Testing the Cmdlet</span></span>

<span data-ttu-id="dbe52-175">Wenn Ihr Cmdlet bei Windows PowerShell registriert ist, können Sie es in der Befehlszeile testen.</span><span class="sxs-lookup"><span data-stu-id="dbe52-175">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="dbe52-176">Im folgenden finden Sie zwei Möglichkeiten, den Code für das-Beispiel-Cmdlet zu testen.</span><span class="sxs-lookup"><span data-stu-id="dbe52-176">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="dbe52-177">Weitere Informationen zur Verwendung von Cmdlets über die Befehlszeile finden Sie unter [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="dbe52-177">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="dbe52-178">Führen Sie an der Windows PowerShell-Eingabeaufforderung den folgenden Befehl aus, um den Internet Explorer-Prozess mit dem Namen "Iexplore" aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="dbe52-178">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

    ```powershell
    PS> get-proc -name iexplore
    ```

<span data-ttu-id="dbe52-179">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="dbe52-179">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- <span data-ttu-id="dbe52-180">Verwenden Sie den folgenden Befehl, um die Internet Explorer-, Outlook-und Notepad-Prozesse mit dem Namen "Iexplore", "Outlook" und "Notepad" aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="dbe52-180">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="dbe52-181">Wenn mehrere Prozesse vorhanden sind, werden alle angezeigt.</span><span class="sxs-lookup"><span data-stu-id="dbe52-181">If there are multiple processes, all of them are displayed.</span></span>

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

<span data-ttu-id="dbe52-182">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="dbe52-182">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a><span data-ttu-id="dbe52-183">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="dbe52-183">See Also</span></span>

[<span data-ttu-id="dbe52-184">Hinzufügen von Parametern, die Pipeline Eingaben verarbeiten</span><span class="sxs-lookup"><span data-stu-id="dbe52-184">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="dbe52-185">Erstellen Ihres ersten Cmdlets</span><span class="sxs-lookup"><span data-stu-id="dbe52-185">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="dbe52-186">Erweitern von Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="dbe52-186">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="dbe52-187">Registrieren von Cmdlets, Anbietern und Host Anwendungen</span><span class="sxs-lookup"><span data-stu-id="dbe52-187">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="dbe52-188">Windows PowerShell-Referenz</span><span class="sxs-lookup"><span data-stu-id="dbe52-188">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="dbe52-189">Cmdlet-Beispiele</span><span class="sxs-lookup"><span data-stu-id="dbe52-189">Cmdlet Samples</span></span>](./cmdlet-samples.md)
