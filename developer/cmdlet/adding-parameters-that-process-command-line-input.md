---
title: Hinzufügen von Parametern, die Verarbeiten der Befehlszeileneingabe | Microsoft-Dokumentation
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
ms.openlocfilehash: c9ad84c5bcb6826fcf51db9a1f1a578a65a1f275
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854947"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="f8c24-102">Hinzufügen von Parametern, die Befehlszeileneingaben verarbeiten</span><span class="sxs-lookup"><span data-stu-id="f8c24-102">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="f8c24-103">Eine Ursache für die Eingabe für ein Cmdlet ist die Befehlszeile an.</span><span class="sxs-lookup"><span data-stu-id="f8c24-103">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="f8c24-104">In diesem Thema wird beschrieben, wie zum Hinzufügen eines Parameters, der **Get-Proc** Cmdlet (die beschrieben wird, im [Erstellen Ihrer ersten Cmdlet](./creating-a-cmdlet-without-parameters.md)), damit das Cmdlet die Eingabe aus dem lokalen Computer, die basierend auf explizite verarbeiten kann Objekte, die an das Cmdlet übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="f8c24-104">This topic describes how to add a parameter to the **Get-Proc** cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="f8c24-105">Die **Get-Proc** beschriebenen Cmdlets Ruft die Prozesse, die basierend auf ihren Namen hier ab und zeigt anschließend Informationen über die Prozesse, an der Eingabeaufforderung.</span><span class="sxs-lookup"><span data-stu-id="f8c24-105">The **Get-Proc** cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="f8c24-106">Definieren die Cmdlet-Klasse</span><span class="sxs-lookup"><span data-stu-id="f8c24-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="f8c24-107">Der erste Schritt bei der Cmdlet-Erstellung ist die Cmdlet-Namen und die Deklaration von .NET Framework-Klasse, die die Cmdlets implementiert.</span><span class="sxs-lookup"><span data-stu-id="f8c24-107">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="f8c24-108">Dieses Cmdlet Ruft die Prozessinformationen, ab, die hier ausgewählte Verbnamen also "Get".</span><span class="sxs-lookup"><span data-stu-id="f8c24-108">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="f8c24-109">(Nahezu jede Art von Cmdlets, mit dem Informationen abgerufen werden, kann die Befehlszeileneingabe verarbeiten.) Weitere Informationen zu zulässigen Cmdlet-Verben, finden Sie unter [Cmdlet Verbnamen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="f8c24-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="f8c24-110">Hier ist die Klassendeklaration für die **Get-Proc** Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f8c24-110">Here's the class declaration for the **Get-Proc** cmdlet.</span></span> <span data-ttu-id="f8c24-111">Informationen zu dieser Definition finden Sie in [Erstellen Ihrer ersten Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="f8c24-111">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="f8c24-112">Deklarieren von Parametern</span><span class="sxs-lookup"><span data-stu-id="f8c24-112">Declaring Parameters</span></span>

<span data-ttu-id="f8c24-113">Cmdlet-Parameter ermöglicht den Benutzer als Eingabe für das-Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f8c24-113">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="f8c24-114">Im folgenden Beispiel **Get-Proc** und `Get-Member` sind die Namen der Pipeline-Cmdlets und `MemberType` ist ein Parameter für die `Get-Member` Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f8c24-114">In the following example, **Get-Proc** and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="f8c24-115">Der Parameter hat das Argument "-Eigenschaft."</span><span class="sxs-lookup"><span data-stu-id="f8c24-115">The parameter has the argument "property."</span></span>

<span data-ttu-id="f8c24-116">**PS > Get-Proc; `get-member` Membertype - Eigenschaft**</span><span class="sxs-lookup"><span data-stu-id="f8c24-116">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="f8c24-117">Um Parameter für ein Cmdlet zu deklarieren, müssen Sie zunächst die Eigenschaften definieren, die die Parameter darstellen.</span><span class="sxs-lookup"><span data-stu-id="f8c24-117">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="f8c24-118">In der **Get-Proc** -Cmdlet, um der einzige Parameter ist `Name`, die in diesem Fall den Namen des abzurufenden Objekts Prozess .NET Framework darstellt.</span><span class="sxs-lookup"><span data-stu-id="f8c24-118">In the **Get-Proc** cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="f8c24-119">Folglich definiert die Cmdlet-Klasse eine Eigenschaft vom Typzeichenfolge, ein Array von Namen zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="f8c24-119">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="f8c24-120">Hier folgt die Parameterdeklaration für die `Name` Parameter, der die **Get-Proc** Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f8c24-120">Here's the parameter declaration for the `Name` parameter of the **Get-Proc** cmdlet.</span></span>

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

<span data-ttu-id="f8c24-121">Um die Windows PowerShell-Laufzeit darüber zu informieren, die diese Eigenschaft ist die `Name` -Parameter ein [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) Attribut hinzugefügt wird, auf die Eigenschaftsdefinition.</span><span class="sxs-lookup"><span data-stu-id="f8c24-121">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="f8c24-122">Die grundlegende Syntax zum Deklarieren von dieses Attribut ist `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="f8c24-122">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="f8c24-123">Parameter muss explizit als öffentlich markiert werden.</span><span class="sxs-lookup"><span data-stu-id="f8c24-123">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="f8c24-124">Parameter, die nicht als öffentlicher Standard auf interne gekennzeichnet sind und nicht von der Windows PowerShell-Laufzeit gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="f8c24-124">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="f8c24-125">Dieses Cmdlet verwendet ein Array von Zeichenfolgen für die `Name` Parameter.</span><span class="sxs-lookup"><span data-stu-id="f8c24-125">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="f8c24-126">Wenn möglich, sollte Ihr Cmdlet auch definieren einen Parameter als Array, da dadurch das Cmdlet, um mehr als ein Element zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="f8c24-126">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="f8c24-127">Wichtige Fakten über Parameterdefinitionen</span><span class="sxs-lookup"><span data-stu-id="f8c24-127">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="f8c24-128">Vordefinierte Windows PowerShell-Parameter und Datentypen sollte so weit wie möglich ist, um sicherzustellen, dass Ihr Cmdlet kompatibel mit Windows PowerShell-Cmdlets ist wiederverwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f8c24-128">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="f8c24-129">Wenn alle Cmdlets, die vordefinierten verwenden z. B. `Id` Parametername, der eine Ressource, die Benutzer schnell die Bedeutung des Parameters, unabhängig davon, welche Cmdlets, die bei Verwendung von verstehen.</span><span class="sxs-lookup"><span data-stu-id="f8c24-129">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="f8c24-130">Im Grunde genommen, Parameternamen gelten dieselben Regeln wie bei Variablennamen in der common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="f8c24-130">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="f8c24-131">Weitere Informationen zu Parameternamen finden Sie unter [Cmdlet-Parameternamen](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span><span class="sxs-lookup"><span data-stu-id="f8c24-131">For more information about parameter naming, see [Cmdlet Parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span></span>

- <span data-ttu-id="f8c24-132">Windows PowerShell sind einige Parameternamen, um eine konsistente benutzererfahrung reserviert.</span><span class="sxs-lookup"><span data-stu-id="f8c24-132">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="f8c24-133">Verwenden Sie nicht diese Parameternamen: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, und `OutBuffer`.</span><span class="sxs-lookup"><span data-stu-id="f8c24-133">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="f8c24-134">Darüber hinaus sind die folgenden Aliase für diese Parameternamen reserviert: `vb`, `db`, `ea`, `ev`, `ov`, und `ob`.</span><span class="sxs-lookup"><span data-stu-id="f8c24-134">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="f8c24-135">`Name` ist ein einfache und häufige Parameternamen in Ihre Cmdlets empfohlen.</span><span class="sxs-lookup"><span data-stu-id="f8c24-135">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="f8c24-136">Es ist besser, wählen Sie einen Parameternamen wie folgt als ein komplexer Name, der für ein bestimmtes Cmdlet eindeutig und schwer zu merken ist.</span><span class="sxs-lookup"><span data-stu-id="f8c24-136">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="f8c24-137">Parameter sind in Windows PowerShell, Groß-/Kleinschreibung, auch wenn standardmäßig die Shell Fall beibehalten.</span><span class="sxs-lookup"><span data-stu-id="f8c24-137">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="f8c24-138">Kleinschreibung bei den Argumenten, hängt von den Vorgang des-Cmdlets ab.</span><span class="sxs-lookup"><span data-stu-id="f8c24-138">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="f8c24-139">Argumente werden als in der Befehlszeile angegebenen auf einen Parameter übergeben.</span><span class="sxs-lookup"><span data-stu-id="f8c24-139">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="f8c24-140">Beispiele für andere Parameterdeklarationen, finden Sie unter [Cmdletparameter](./cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="f8c24-140">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="f8c24-141">Deklarieren Sie Parameter als Positionsparameter oder benannte</span><span class="sxs-lookup"><span data-stu-id="f8c24-141">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="f8c24-142">Ein Cmdlet muss jeder Parameter als Positionsparameter oder benannten Parameter festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f8c24-142">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="f8c24-143">Beide Arten von Parametern akzeptieren einzelne Argumente, die mehrere Argumente, die durch Kommas getrennt, und boolesche Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="f8c24-143">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="f8c24-144">Ein boolescher Parameter, die so genannte eine *wechseln*, nur boolesche Einstellungen behandelt.</span><span class="sxs-lookup"><span data-stu-id="f8c24-144">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="f8c24-145">Der Schalter wird verwendet, um das Vorhandensein des Parameters zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="f8c24-145">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="f8c24-146">Der empfohlene Standardwert ist `false`.</span><span class="sxs-lookup"><span data-stu-id="f8c24-146">The recommended default is `false`.</span></span>

<span data-ttu-id="f8c24-147">Das Beispiel **Get-Proc** Cmdlet definiert die `Name` Parameter als Positionsparameter an Position 0.</span><span class="sxs-lookup"><span data-stu-id="f8c24-147">The sample **Get-Proc** cmdlet defines the `Name` parameter as a positional parameter with position 0.</span></span> <span data-ttu-id="f8c24-148">Dies bedeutet, dass das erste Argument, die, das der Benutzer in der Befehlszeile gibt, für diesen Parameter automatisch eingefügt wird.</span><span class="sxs-lookup"><span data-stu-id="f8c24-148">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="f8c24-149">Wenn Sie einen benannten Parameter definieren möchten, für die der Benutzer angeben muss der Parameternamen in der Befehlszeile aus, lassen Sie die `Position` Schlüsselwort aus der Deklaration des Attributs.</span><span class="sxs-lookup"><span data-stu-id="f8c24-149">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="f8c24-150">Wenn der Parameter benannt werden müssen, empfehlen wir, dass Sie die am häufigsten verwendeten Parameter mit Feldern fester Breite vornehmen, damit Benutzer nicht den Parameternamen eingeben müssen.</span><span class="sxs-lookup"><span data-stu-id="f8c24-150">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="f8c24-151">Deklarieren Sie Parameter als obligatorisch oder Optional</span><span class="sxs-lookup"><span data-stu-id="f8c24-151">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="f8c24-152">Ein Cmdlet muss jeder Parameter als ein optionales oder einen obligatorischen Parameter festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="f8c24-152">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="f8c24-153">Im Beispiel **Get-Proc** -Cmdlet, das `Name` Parameter als optional definiert werden, da die `Mandatory` Schlüsselwort ist nicht in der Attributdeklaration festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f8c24-153">In the sample **Get-Proc** cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="f8c24-154">Unterstützung von Parametervalidierung</span><span class="sxs-lookup"><span data-stu-id="f8c24-154">Supporting Parameter Validation</span></span>

<span data-ttu-id="f8c24-155">Im Beispiel **Get-Proc** Fügt ein Attribut eingabeüberprüfung [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), zu der `Name` Parameter, um die Validierung zu aktivieren, die die die Eingabe ist keine `null` noch leer.</span><span class="sxs-lookup"><span data-stu-id="f8c24-155">The sample **Get-Proc** cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="f8c24-156">Dieses Attribut ist eine der mehrere Validierungsattribute, die von Windows PowerShell bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="f8c24-156">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="f8c24-157">Beispiele für andere Validierungsattribute, finden Sie unter [Überprüfen der Parametereingabe](./validating-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="f8c24-157">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="f8c24-158">Überschreiben einer Eingabeverarbeitungsmethode</span><span class="sxs-lookup"><span data-stu-id="f8c24-158">Overriding an Input Processing Method</span></span>

<span data-ttu-id="f8c24-159">Wenn Ihr Cmdlet zum Verarbeiten der Befehlszeileneingabe wird, muss er die entsprechenden eingabeverarbeitungsmethoden überschreiben.</span><span class="sxs-lookup"><span data-stu-id="f8c24-159">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="f8c24-160">Die grundlegende eingabeverarbeitungsmethoden entstehen in [Erstellen Ihrer ersten Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="f8c24-160">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="f8c24-161">Die **Get-Proc** Cmdlet überschreibt die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode zum Behandeln der `Name` Parametereingabe, die durch den Benutzer oder ein Skript bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="f8c24-161">The **Get-Proc** cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="f8c24-162">Diese Methode ruft die Prozesse für jede angeforderte Prozessname oder alle Prozesse an, wenn kein Name angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="f8c24-162">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="f8c24-163">Beachten Sie, dass in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), den Aufruf von [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) ist die Ausgabe Mechanismus zum Senden der Ausgabe Objekte in der Pipeline.</span><span class="sxs-lookup"><span data-stu-id="f8c24-163">Notice that in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="f8c24-164">Der zweite Parameter des Aufrufs, `enumerateCollection`, nastaven NA hodnotu `true` informieren die Windows PowerShell-Laufzeit zum Aufzählen der Matrix von Prozessobjekten und Schreiben einen Prozess zu einem Zeitpunkt, an die Befehlszeile.</span><span class="sxs-lookup"><span data-stu-id="f8c24-164">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="f8c24-165">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="f8c24-165">Code Sample</span></span>

<span data-ttu-id="f8c24-166">Für die vollständige C# Beispielcode, finden Sie unter [GetProcessSample02-Beispiel](./getprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="f8c24-166">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="f8c24-167">Definieren von Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="f8c24-167">Defining Object Types and Formatting</span></span>

<span data-ttu-id="f8c24-168">Windows PowerShell übergibt Informationen zwischen Cmdlets mithilfe von .NET Framework-Objekten.</span><span class="sxs-lookup"><span data-stu-id="f8c24-168">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="f8c24-169">Daher müssen möglicherweise ein Cmdlet seinen eigenen Typ definieren oder ein Cmdlets müssen zum Erweitern eines vorhandenen Typs, der durch ein anderes Cmdlet bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="f8c24-169">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="f8c24-170">Weitere Informationen zum Definieren neuer Typen, oder erweitern vorhandene Typen finden Sie unter [Objekttypen erweitern und Formatierung](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="f8c24-170">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="f8c24-171">Erstellen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8c24-171">Building the Cmdlet</span></span>

<span data-ttu-id="f8c24-172">Nachdem Sie ein Cmdlet implementiert haben, müssen Sie es mit einem Windows PowerShell-Snap-in mit Windows PowerShell registrieren.</span><span class="sxs-lookup"><span data-stu-id="f8c24-172">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="f8c24-173">Weitere Informationen zum Registrieren von Cmdlets finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="f8c24-173">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="f8c24-174">Testen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8c24-174">Testing the Cmdlet</span></span>

<span data-ttu-id="f8c24-175">Wenn Ihr Cmdlet mit Windows PowerShell registriert ist, können Sie es testen, indem Sie sie in der Befehlszeile ausführen.</span><span class="sxs-lookup"><span data-stu-id="f8c24-175">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="f8c24-176">Hier sind zwei Möglichkeiten, den Code für das beispielcmdlet testen.</span><span class="sxs-lookup"><span data-stu-id="f8c24-176">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="f8c24-177">Weitere Informationen zur Verwendung von Cmdlets, über die Befehlszeile finden Sie unter [erste Schritte mit Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="f8c24-177">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="f8c24-178">Verwenden Sie an der Windows PowerShell-Eingabeaufforderung den folgenden Befehl zum Auflisten von Internet Explorer-Prozess, mit der Namen "IEXPLORE".</span><span class="sxs-lookup"><span data-stu-id="f8c24-178">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

    ```powershell
    PS> get-proc -name iexplore
    ```

<span data-ttu-id="f8c24-179">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f8c24-179">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- <span data-ttu-id="f8c24-180">Um die Internet Explorer, Outlook und Editor-Prozesse, die mit dem Namen "IEXPLORE" aufzulisten, verwenden Sie "OUTLOOK" und "Editor" den folgenden Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="f8c24-180">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="f8c24-181">Wenn mehrere Prozesse, werden alle von ihnen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f8c24-181">If there are multiple processes, all of them are displayed.</span></span>

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

<span data-ttu-id="f8c24-182">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f8c24-182">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a><span data-ttu-id="f8c24-183">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f8c24-183">See Also</span></span>

[<span data-ttu-id="f8c24-184">Hinzufügen von Parametern, die Eingabe der Prozesspipeline</span><span class="sxs-lookup"><span data-stu-id="f8c24-184">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="f8c24-185">Erstellen eines ersten Cmdlets</span><span class="sxs-lookup"><span data-stu-id="f8c24-185">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="f8c24-186">Erweitern die Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="f8c24-186">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="f8c24-187">So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen</span><span class="sxs-lookup"><span data-stu-id="f8c24-187">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="f8c24-188">Windows PowerShell-Referenz</span><span class="sxs-lookup"><span data-stu-id="f8c24-188">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="f8c24-189">Cmdlet-Beispiele</span><span class="sxs-lookup"><span data-stu-id="f8c24-189">Cmdlet Samples</span></span>](./cmdlet-samples.md)
