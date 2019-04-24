---
title: Hinzufügen von nicht endenden Fehlerberichte an Ihr Cmdlet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: 3741982f81efa04d8fe7ab448fba5f2fdf4b0c01
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984237"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="60d82-102">Hinzufügen von Berichten für Fehler ohne Abbruch zu Cmdlet</span><span class="sxs-lookup"><span data-stu-id="60d82-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="60d82-103">-Cmdlets können Fehler ohne Abbruch durch den Aufruf melden die [System.Management.Automation.Cmdlet.WriteError][] Methode und weiterhin auf das aktuelle Eingabeobjekt oder weiteren eingehenden verwendet werden Objekte pipeline.</span><span class="sxs-lookup"><span data-stu-id="60d82-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError][] method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span>
<span data-ttu-id="60d82-104">In diesem Abschnitt wird erläutert, wie ein Cmdlet zu erstellen, die Fehler ohne Abbruch aus dessen eingabeverarbeitungsmethoden meldet.</span><span class="sxs-lookup"><span data-stu-id="60d82-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="60d82-105">Fehler ohne Abbruch (als auch Fehler mit Abbruch), muss das Cmdlet übergeben eine [System.Management.Automation.ErrorRecord][] Objekt, das den Fehler identifiziert.</span><span class="sxs-lookup"><span data-stu-id="60d82-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord][] object identifying the error.</span></span>
<span data-ttu-id="60d82-106">Jeden Error-Datensatz wird durch eine eindeutige Zeichenfolge, die Namen "Fehler-ID" gekennzeichnet.</span><span class="sxs-lookup"><span data-stu-id="60d82-106">Each error record is identified by a unique string called the "error identifier".</span></span>
<span data-ttu-id="60d82-107">Zusätzlich zu den Bezeichner, die Kategorie der einzelnen Fehler von definierten Konstanten gemäß einem [System.Management.Automation.ErrorCategory][] Enumeration.</span><span class="sxs-lookup"><span data-stu-id="60d82-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.ErrorCategory][] enumeration.</span></span>
<span data-ttu-id="60d82-108">Der Benutzer kann basierte auf ihrer Kategorie durch Festlegen von Fehlern anzeigen der `$ErrorView` Variable "CategoryView".</span><span class="sxs-lookup"><span data-stu-id="60d82-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="60d82-109">Weitere Informationen zu Datensätzen, finden Sie unter [Windows PowerShell-Fehlerdatensätze](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="60d82-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="60d82-110">Definieren das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="60d82-110">Defining the Cmdlet</span></span>

<span data-ttu-id="60d82-111">Der erste Schritt bei der Cmdlet-Erstellung ist immer benennen das Cmdlet und .NET implementiert die Klasse, mit dem-Cmdlet deklarieren.</span><span class="sxs-lookup"><span data-stu-id="60d82-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span>
<span data-ttu-id="60d82-112">Dieses Cmdlet Ruft die Prozessinformationen, ab, der Namen des Verbs hier ausgewählten also "Get".</span><span class="sxs-lookup"><span data-stu-id="60d82-112">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span>
<span data-ttu-id="60d82-113">(Nahezu jede Art von Cmdlets, mit dem Informationen abgerufen werden, kann die Befehlszeileneingabe verarbeiten.) Weitere Informationen zu zulässigen Cmdlet-Verben, finden Sie unter [Cmdlet Verbnamen](approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="60d82-113">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="60d82-114">Im folgenden finden die Definition für dieses Cmdlet "Get-Proc".</span><span class="sxs-lookup"><span data-stu-id="60d82-114">The following is the definition for this Get-Proc cmdlet.</span></span>
<span data-ttu-id="60d82-115">Details zu dieser Definition werden in angegebenen [Erstellen Ihrer ersten Cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="60d82-115">Details of this definition are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="60d82-116">Definieren von Parametern</span><span class="sxs-lookup"><span data-stu-id="60d82-116">Defining Parameters</span></span>

<span data-ttu-id="60d82-117">Falls erforderlich, muss Ihr Cmdlet Parameter für die Verarbeitung von Eingaben definieren.</span><span class="sxs-lookup"><span data-stu-id="60d82-117">If necessary, your cmdlet must define parameters for processing input.</span></span>
<span data-ttu-id="60d82-118">Dieses Cmdlet "Get-Proc" definiert eine **Namen** Parameter wie beschrieben in [Hinzufügen von Parametern die Prozess-Command-Line-Eingabe](adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="60d82-118">This Get-Proc cmdlet defines a **Name** parameter as described in [Adding Parameters that Process Command-Line Input](adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="60d82-119">Hier folgt die Parameterdeklaration für die **Namen** Parameter des Cmdlets Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="60d82-119">Here is the parameter declaration for the **Name** parameter of this Get-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

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

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="60d82-120">Eingabeverarbeitungsmethoden überschreiben</span><span class="sxs-lookup"><span data-stu-id="60d82-120">Overriding Input Processing Methods</span></span>

<span data-ttu-id="60d82-121">Alle Cmdlets müssen mindestens eines der Eingabe, die Verarbeitung von bereitgestellten Methoden überschreiben die [System.Management.Automation.Cmdlet][] Klasse.</span><span class="sxs-lookup"><span data-stu-id="60d82-121">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet][] class.</span></span>
<span data-ttu-id="60d82-122">Diese Methoden finden Sie im [Erstellen Ihrer ersten Cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="60d82-122">These methods are discussed in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="60d82-123">Jeder Datensatz sollte Ihr Cmdlet so unabhängig wie möglich verarbeiten können.</span><span class="sxs-lookup"><span data-stu-id="60d82-123">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="60d82-124">Dieses Cmdlet "Get-Proc" überschreibt die [System.Management.Automation.Cmdlet.ProcessRecord][] Methode zum Behandeln der **Namen** Parameter für die Eingabe durch den Benutzer oder ein Skript bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="60d82-124">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord][] method to handle the **Name** parameter for input provided by the user or a script.</span></span>
<span data-ttu-id="60d82-125">Diese Methode erhalten die Prozesse für jede angeforderte Prozessname oder allen Prozessen, wenn kein Name angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="60d82-125">This method will get the processes for each requested process name or all processes if no name is provided.</span></span>
<span data-ttu-id="60d82-126">Details der Außerkraftsetzung erhalten [Erstellen Ihrer ersten Cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="60d82-126">Details of this override are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="60d82-127">Wichtige Aspekte beim Melden von Fehlern</span><span class="sxs-lookup"><span data-stu-id="60d82-127">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="60d82-128">Die [System.Management.Automation.ErrorRecord][] Objekt, mit das-Cmdlet übergibt, beim Schreiben eines Fehlers eine Ausnahme im Kern ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="60d82-128">The [System.Management.Automation.ErrorRecord][] object that the cmdlet passes when writing an error requires an exception at its core.</span></span>
<span data-ttu-id="60d82-129">Befolgen Sie die .NET-Richtlinien, wenn bestimmt wird die Ausnahme zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="60d82-129">Follow the .NET guidelines when determining the exception to use.</span></span>
<span data-ttu-id="60d82-130">Wenn der Fehler semantisch identisch mit einer vorhandenen Ausnahme ist, sollte das-Cmdlet im Grunde verwenden oder diese Ausnahme abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="60d82-130">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span>
<span data-ttu-id="60d82-131">Es sollte, andernfalls der abgeleitet werden, eine neue Ausnahme oder ausnahmenhierarchie direkt aus der [System.Exception][] Klasse.</span><span class="sxs-lookup"><span data-stu-id="60d82-131">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception][] class.</span></span>

<span data-ttu-id="60d82-132">Beim Erstellen des Fehler-IDs (Zugriff über die FullyQualifiedErrorId-Eigenschaft der Klasse ErrorRecord) sollten Sie Folgendes bedenken.</span><span class="sxs-lookup"><span data-stu-id="60d82-132">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="60d82-133">Verwenden von Zeichenfolgen, die für Diagnosezwecke, damit Sie beim Untersuchen des vollqualifizierten Bezeichners Worin den Fehler ermitteln können ist und wo der Fehler stammt vorgesehen sind.</span><span class="sxs-lookup"><span data-stu-id="60d82-133">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="60d82-134">Eine wohlgeformte vollqualifizierten Fehler-ID könnte folgendermaßen aussehen.</span><span class="sxs-lookup"><span data-stu-id="60d82-134">A well formed fully qualified error identifier might be as follows.</span></span>

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

<span data-ttu-id="60d82-135">Beachten Sie, dass im vorherigen Beispiel, die Fehler-ID (das erste Token) kennzeichnet den Fehler, und der verbleibende Teil gibt an, in dem der Fehler stammt.</span><span class="sxs-lookup"><span data-stu-id="60d82-135">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="60d82-136">Für komplexere Szenarien kann der Fehler-ID einen Punkt getrennte Token sein, die mit der Untersuchung analysiert werden können.</span><span class="sxs-lookup"><span data-stu-id="60d82-136">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span>
  <span data-ttu-id="60d82-137">Dadurch, dass Sie auch auf die die Fehler-ID als auch für die Fehlerkategorie für Bezeichner und Fehler verzweigen.</span><span class="sxs-lookup"><span data-stu-id="60d82-137">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="60d82-138">Das Cmdlet sollten unterschiedliche Codepfade Fehler Bezeichner zuweisen.</span><span class="sxs-lookup"><span data-stu-id="60d82-138">The cmdlet should assign specific error identifiers to different code paths.</span></span>
<span data-ttu-id="60d82-139">Bedenken Sie die folgende Informationen für die Zuweisung des Fehler-IDs:</span><span class="sxs-lookup"><span data-stu-id="60d82-139">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="60d82-140">Ein Bezeichner für den Fehler sollte während des Lebenszyklus des Cmdlet konstant bleibt.</span><span class="sxs-lookup"><span data-stu-id="60d82-140">An error identifier should remain constant throughout the cmdlet life cycle.</span></span>
  <span data-ttu-id="60d82-141">Die Semantik eines Bezeichners Fehler zwischen den Cmdlet-Versionen werden nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="60d82-141">Do not change the semantics of an error identifier between cmdlet versions.</span></span>

- <span data-ttu-id="60d82-142">Verwenden Sie Text für eine Fehler-ID, die nur sehr knapp entspricht der Fehler gemeldet wird.</span><span class="sxs-lookup"><span data-stu-id="60d82-142">Use text for an error identifier that tersely corresponds to the error being reported.</span></span>
  <span data-ttu-id="60d82-143">Verwenden Sie keine leer- oder Interpunktionszeichen.</span><span class="sxs-lookup"><span data-stu-id="60d82-143">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="60d82-144">Haben Sie Ihr Cmdlet nur die Fehler-IDs zu generieren, die reproduzierbar sind.</span><span class="sxs-lookup"><span data-stu-id="60d82-144">Have your cmdlet generate only error identifiers that are reproducible.</span></span>
  <span data-ttu-id="60d82-145">Beispielsweise sollten sie keinen Bezeichner generiert, der Prozess-ID enthält.</span><span class="sxs-lookup"><span data-stu-id="60d82-145">For example, it should not generate an identifier that includes a process identifier.</span></span>
  <span data-ttu-id="60d82-146">Fehler-IDs eignen sich für einen Benutzer nur dann, wenn diese Bezeichner entsprechen, die von anderen Benutzern, die das gleiche Problem bemerkt werden.</span><span class="sxs-lookup"><span data-stu-id="60d82-146">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="60d82-147">Nicht behandelte Ausnahmen werden nicht von PowerShell unter den folgenden Bedingungen abgefangen:</span><span class="sxs-lookup"><span data-stu-id="60d82-147">Unhandled exceptions are not caught by PowerShell in the following conditions:</span></span>

- <span data-ttu-id="60d82-148">Wenn ein Cmdlet erstellt einen neuen Thread und Code, der ausgeführt wird, dass Thread eine nicht behandelte Ausnahme auslöst, ist PowerShell fängt keine Fehler und der Prozess beendet wird.</span><span class="sxs-lookup"><span data-stu-id="60d82-148">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

- <span data-ttu-id="60d82-149">Verfügt ein Objekt für Code in seinem Destruktor oder die Dispose-Methoden, die eine nicht behandelte Ausnahme auslöst, ist PowerShell fängt keine Fehler und der Prozess beendet wird.</span><span class="sxs-lookup"><span data-stu-id="60d82-149">If an object has code in its destructor or Dispose methods that causes an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="60d82-150">Melden Sie Fehler ohne Abbruch</span><span class="sxs-lookup"><span data-stu-id="60d82-150">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="60d82-151">Eines der eingabeverarbeitungsmethoden kann einen Fehler ohne Abbruch melden, um die Ausgabe-Stream mit der [System.Management.Automation.Cmdlet.WriteError][] Methode.</span><span class="sxs-lookup"><span data-stu-id="60d82-151">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError][] method.</span></span>

<span data-ttu-id="60d82-152">Hier ist ein Codebeispiel aus diesem Get-Proc-Cmdlet, das veranschaulicht, den Aufruf von [System.Management.Automation.Cmdlet.WriteError][] von innerhalb der Überschreibung der der [System.Management.Automation.Cmdlet.ProcessRecord][] Methode.</span><span class="sxs-lookup"><span data-stu-id="60d82-152">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError][] from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord][] method.</span></span>
<span data-ttu-id="60d82-153">In diesem Fall wird der Aufruf ausgelöst, wenn das Cmdlet einen Prozess für eine angegebene Prozess-ID nicht finden kann.</span><span class="sxs-lookup"><span data-stu-id="60d82-153">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="60d82-154">Punkte zu beachten, die zum Schreiben von Fehler ohne Abbruch</span><span class="sxs-lookup"><span data-stu-id="60d82-154">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="60d82-155">Für einen Fehler ohne Abbruch muss das Cmdlet einen bestimmten Fehler-ID für jeden bestimmten Eingabeobjekt generiert.</span><span class="sxs-lookup"><span data-stu-id="60d82-155">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="60d82-156">Ein Cmdlet muss häufig die PowerShell-Aktion erzeugt einen Fehler ohne Abbruch ändern.</span><span class="sxs-lookup"><span data-stu-id="60d82-156">A cmdlet frequently needs to modify the PowerShell action produced by a nonterminating error.</span></span>
<span data-ttu-id="60d82-157">Hierzu können sie definieren die `ErrorAction` und `ErrorVariable` Parameter.</span><span class="sxs-lookup"><span data-stu-id="60d82-157">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span>
<span data-ttu-id="60d82-158">Definieren der `ErrorAction` -Parameter mit dem-Cmdlet zeigt die Benutzeroptionen [System.Management.Automation.ActionPreference][], können Sie die Aktion auch direkt beeinflussen, indem Sie festlegen der `$ErrorActionPreference` Variable.</span><span class="sxs-lookup"><span data-stu-id="60d82-158">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.ActionPreference][], you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="60d82-159">Das-Cmdlet kann Fehler ohne Abbruch speichern, um eine Variable mit dem `ErrorVariable` -Parameter, der die Einstellung nicht betroffen ist `ErrorAction`.</span><span class="sxs-lookup"><span data-stu-id="60d82-159">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span>
<span data-ttu-id="60d82-160">Fehler bei der können für eine vorhandene Fehlervariable angefügt werden durch das Hinzufügen ein Pluszeichen (+) am Anfang der Variablenname.</span><span class="sxs-lookup"><span data-stu-id="60d82-160">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="60d82-161">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="60d82-161">Code Sample</span></span>

<span data-ttu-id="60d82-162">Für die vollständige C# Beispielcode, finden Sie unter [GetProcessSample04 Beispiel](./getprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="60d82-162">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="60d82-163">Definieren von Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="60d82-163">Define Object Types and Formatting</span></span>

<span data-ttu-id="60d82-164">PowerShell übergibt Informationen zwischen Cmdlets, die mithilfe von .NET-Objekten.</span><span class="sxs-lookup"><span data-stu-id="60d82-164">PowerShell passes information between cmdlets using .NET objects.</span></span>
<span data-ttu-id="60d82-165">Daher müssen möglicherweise ein Cmdlet seinen eigenen Typ definieren, oder das-Cmdlet zum Erweitern eines vorhandenen Typs, der durch ein anderes Cmdlet angegeben müssen.</span><span class="sxs-lookup"><span data-stu-id="60d82-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span>
<span data-ttu-id="60d82-166">Weitere Informationen zum Definieren neuer Typen, oder erweitern vorhandene Typen finden Sie unter [Objekttypen erweitern und Formatierung](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="60d82-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="60d82-167">Erstellen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="60d82-167">Building the Cmdlet</span></span>

<span data-ttu-id="60d82-168">Nach der Implementierung eines Cmdlets, müssen Sie es mit Windows PowerShell über eine Windows PowerShell-Snap-in registrieren.</span><span class="sxs-lookup"><span data-stu-id="60d82-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span>
<span data-ttu-id="60d82-169">Weitere Informationen zum Registrieren von Cmdlets finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="60d82-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="60d82-170">Testen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="60d82-170">Testing the Cmdlet</span></span>

<span data-ttu-id="60d82-171">Wenn Ihr Cmdlet mit PowerShell registriert wurde, können Sie es testen, indem Sie sie in der Befehlszeile ausführen.</span><span class="sxs-lookup"><span data-stu-id="60d82-171">When your cmdlet has been registered with PowerShell, you can test it by running it on the command line.</span></span>
<span data-ttu-id="60d82-172">Testen Sie nun das Beispiel-Get-Proc-Cmdlet, um festzustellen, ob es sich um ein Fehler gemeldet:</span><span class="sxs-lookup"><span data-stu-id="60d82-172">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="60d82-173">Starten Sie PowerShell, und verwenden Sie das Get-Proc-Cmdlet zum Abrufen der Prozesse, die mit dem Namen "TEST".</span><span class="sxs-lookup"><span data-stu-id="60d82-173">Start PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

    ```powershell
    PS> get-proc -name test
    ```

<span data-ttu-id="60d82-174">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="60d82-174">The following output appears.</span></span>

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a><span data-ttu-id="60d82-175">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="60d82-175">See Also</span></span>

[<span data-ttu-id="60d82-176">Hinzufügen von Parametern, die Eingabe der Prozesspipeline</span><span class="sxs-lookup"><span data-stu-id="60d82-176">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="60d82-177">Hinzufügen von Parametern, die Befehlszeileneingabe verarbeiten</span><span class="sxs-lookup"><span data-stu-id="60d82-177">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="60d82-178">Erstellen eines ersten Cmdlets</span><span class="sxs-lookup"><span data-stu-id="60d82-178">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="60d82-179">Erweitern die Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="60d82-179">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="60d82-180">So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen</span><span class="sxs-lookup"><span data-stu-id="60d82-180">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="60d82-181">Windows PowerShell-Referenz</span><span class="sxs-lookup"><span data-stu-id="60d82-181">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="60d82-182">Cmdlet-Beispiele</span><span class="sxs-lookup"><span data-stu-id="60d82-182">Cmdlet Samples</span></span>](./cmdlet-samples.md)

[System.Exception]: /dotnet/api/System.Exception
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
