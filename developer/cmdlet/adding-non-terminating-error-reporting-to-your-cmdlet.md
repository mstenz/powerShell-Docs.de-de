---
title: Hinzufügen von Fehlerberichten ohne Abbruch zum Cmdlet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: a4426abec96cd922360aeef8c157b4e9f41a15b9
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322872"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="31adf-102">Hinzufügen von Berichten für Fehler ohne Abbruch zu Cmdlet</span><span class="sxs-lookup"><span data-stu-id="31adf-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="31adf-103">Cmdlets können nicht abschließende Fehler melden, indem Sie die [System. Management. Automation. Cmdlet. Write error][] -Methode aufrufen und weiterhin auf dem aktuellen Eingabe Objekt oder in weiteren eingehenden Pipeline Objekten arbeiten.</span><span class="sxs-lookup"><span data-stu-id="31adf-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError][] method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span>
<span data-ttu-id="31adf-104">In diesem Abschnitt wird erläutert, wie ein Cmdlet erstellt wird, das nicht abschließende Fehler von seinen Eingabe Verarbeitungsmethoden meldet.</span><span class="sxs-lookup"><span data-stu-id="31adf-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="31adf-105">Bei nicht beendenden Fehlern (sowie beim Beenden von Fehlern) muss das Cmdlet ein [System. Management. Automation. ErrorRecord][] -Objekt übergeben, das den Fehler identifiziert.</span><span class="sxs-lookup"><span data-stu-id="31adf-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord][] object identifying the error.</span></span>
<span data-ttu-id="31adf-106">Jeder Fehler Daten Satz wird durch eine eindeutige Zeichenfolge identifiziert, die als "Fehler Bezeichner" bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="31adf-106">Each error record is identified by a unique string called the "error identifier".</span></span>
<span data-ttu-id="31adf-107">Zusätzlich zum Bezeichner wird die Kategorie jedes Fehlers durch Konstanten angegeben, die durch eine [System. Management. Automation. ErrorCategory][] -Enumeration definiert werden.</span><span class="sxs-lookup"><span data-stu-id="31adf-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.ErrorCategory][] enumeration.</span></span>
<span data-ttu-id="31adf-108">Der Benutzer kann Fehler basierend auf der Kategorie anzeigen, indem er `$ErrorView` die Variable auf "categoryview" festlegt.</span><span class="sxs-lookup"><span data-stu-id="31adf-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="31adf-109">Weitere Informationen zu Fehler Datensätzen finden Sie unter [Windows PowerShell-Fehler Datensätze](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="31adf-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="31adf-110">Definieren des Cmdlets</span><span class="sxs-lookup"><span data-stu-id="31adf-110">Defining the Cmdlet</span></span>

<span data-ttu-id="31adf-111">Der erste Schritt bei der Cmdlet-Erstellung ist die Benennung des Cmdlets und das Deklarieren der .NET-Klasse, die das Cmdlet implementiert.</span><span class="sxs-lookup"><span data-stu-id="31adf-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span>
<span data-ttu-id="31adf-112">Dieses Cmdlet ruft Prozessinformationen ab, daher lautet der hier gewählte Verb Name "Get".</span><span class="sxs-lookup"><span data-stu-id="31adf-112">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span>
<span data-ttu-id="31adf-113">(Fast jede Art von Cmdlet, das Informationen abrufen kann, kann die Befehlszeilen Eingabe verarbeiten.) Weitere Informationen zu genehmigten Cmdlet-Verben finden Sie unter [Cmdlet-Verb Namen](approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="31adf-113">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="31adf-114">Im folgenden finden Sie die Definition für dieses Get-proc-Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="31adf-114">The following is the definition for this Get-Proc cmdlet.</span></span>
<span data-ttu-id="31adf-115">Einzelheiten zu dieser Definition finden Sie unter [Erstellen des ersten Cmdlets](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="31adf-115">Details of this definition are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="31adf-116">Definieren von Parametern</span><span class="sxs-lookup"><span data-stu-id="31adf-116">Defining Parameters</span></span>

<span data-ttu-id="31adf-117">Bei Bedarf muss das Cmdlet Parameter für die Verarbeitung von Eingaben definieren.</span><span class="sxs-lookup"><span data-stu-id="31adf-117">If necessary, your cmdlet must define parameters for processing input.</span></span>
<span data-ttu-id="31adf-118">Dieses Cmdlet "Get-proc" definiert einen **namens** Parameter, wie unter [Hinzufügen von Parametern zur Verarbeitung der Befehlszeilen Eingabe](adding-parameters-that-process-command-line-input.md)beschrieben.</span><span class="sxs-lookup"><span data-stu-id="31adf-118">This Get-Proc cmdlet defines a **Name** parameter as described in [Adding Parameters that Process Command-Line Input](adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="31adf-119">Hier ist die Parameter Deklaration für den **Name** -Parameter dieses Get-proc-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="31adf-119">Here is the parameter declaration for the **Name** parameter of this Get-Proc cmdlet.</span></span>

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

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="31adf-120">Überschreiben von Eingabe Verarbeitungsmethoden</span><span class="sxs-lookup"><span data-stu-id="31adf-120">Overriding Input Processing Methods</span></span>

<span data-ttu-id="31adf-121">Alle Cmdlets müssen mindestens eine der Eingabe Verarbeitungsmethoden überschreiben, die von der [System. Management. Automation. Cmdlet][] -Klasse bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="31adf-121">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet][] class.</span></span>
<span data-ttu-id="31adf-122">Diese Methoden werden unter [Erstellen des ersten Cmdlets](creating-a-cmdlet-without-parameters.md)erläutert.</span><span class="sxs-lookup"><span data-stu-id="31adf-122">These methods are discussed in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="31adf-123">Ihr Cmdlet sollte jeden Datensatz so unabhängig wie möglich verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="31adf-123">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="31adf-124">Dieses Get-proc-Cmdlet überschreibt die [System. Management. Automation. Cmdlet. ProcessRecord][] -Methode, um den **namens** Parameter für die vom Benutzer oder einem Skript bereitgestellte Eingabe zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="31adf-124">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord][] method to handle the **Name** parameter for input provided by the user or a script.</span></span>
<span data-ttu-id="31adf-125">Diese Methode erhält die Prozesse für die einzelnen angeforderten Prozessnamen oder alle Prozesse, wenn kein Name angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="31adf-125">This method will get the processes for each requested process name or all processes if no name is provided.</span></span>
<span data-ttu-id="31adf-126">Details dieser außer Kraft Setzung werden bei [der Erstellung des ersten Cmdlets](creating-a-cmdlet-without-parameters.md)angegeben.</span><span class="sxs-lookup"><span data-stu-id="31adf-126">Details of this override are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="31adf-127">Dinge, die beim Melden von Fehlern beachtet werden sollten</span><span class="sxs-lookup"><span data-stu-id="31adf-127">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="31adf-128">Das [System. Management. Automation. ErrorRecord][] -Objekt, das das Cmdlet beim Schreiben eines Fehlers übergibt, erfordert im Kern eine Ausnahme.</span><span class="sxs-lookup"><span data-stu-id="31adf-128">The [System.Management.Automation.ErrorRecord][] object that the cmdlet passes when writing an error requires an exception at its core.</span></span>
<span data-ttu-id="31adf-129">Befolgen Sie die .NET-Richtlinien bei der Bestimmung der zu verwendenden Ausnahme.</span><span class="sxs-lookup"><span data-stu-id="31adf-129">Follow the .NET guidelines when determining the exception to use.</span></span>
<span data-ttu-id="31adf-130">Wenn der Fehler in der Semantik identisch mit einer vorhandenen Ausnahme ist, sollte das Cmdlet diese Ausnahme verwenden oder davon ableiten.</span><span class="sxs-lookup"><span data-stu-id="31adf-130">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span>
<span data-ttu-id="31adf-131">Andernfalls sollte eine neue Ausnahme-oder eine Ausnahme Hierarchie direkt von der [System. Exception][] -Klasse abgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="31adf-131">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception][] class.</span></span>

<span data-ttu-id="31adf-132">Beachten Sie beim Erstellen von Fehler bezeichgern (auf die über die fullyqualifiederrorid-Eigenschaft der ErrorRecord-Klasse zugegriffen wird) Folgendes:</span><span class="sxs-lookup"><span data-stu-id="31adf-132">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="31adf-133">Verwenden Sie Zeichen folgen, die zu Diagnose Zwecken dienen, damit Sie bei der Überprüfung des voll qualifizierten Bezeichners ermitteln können, welcher Fehler vorliegt und wo der Fehler aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="31adf-133">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="31adf-134">Ein wohlgeformter voll qualifizierter Fehler Bezeichner kann wie folgt lauten.</span><span class="sxs-lookup"><span data-stu-id="31adf-134">A well formed fully qualified error identifier might be as follows.</span></span>

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

<span data-ttu-id="31adf-135">Beachten Sie, dass im vorherigen Beispiel der Fehler Bezeichner (das erste Token) angibt, was der Fehler ist, und der verbleibende Teil gibt an, wo der Fehler aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="31adf-135">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="31adf-136">Bei komplexeren Szenarios kann der Fehler Bezeichner ein Punkt getrenntes Token sein, das bei der Überprüfung analysiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="31adf-136">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span>
  <span data-ttu-id="31adf-137">Dies ermöglicht es Ihnen, die Teile des Fehler Bezeichners sowie den Fehler Bezeichner und die Fehler Kategorie zu verzweigen.</span><span class="sxs-lookup"><span data-stu-id="31adf-137">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="31adf-138">Mit dem-Cmdlet sollten bestimmte Fehler Bezeichner verschiedenen Codepfade zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="31adf-138">The cmdlet should assign specific error identifiers to different code paths.</span></span>
<span data-ttu-id="31adf-139">Beachten Sie bei der Zuweisung von Fehler bezeichmern die folgenden Informationen:</span><span class="sxs-lookup"><span data-stu-id="31adf-139">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="31adf-140">Ein Fehler Bezeichner sollte während des gesamten Lebenszyklus des Cmdlets konstant bleiben.</span><span class="sxs-lookup"><span data-stu-id="31adf-140">An error identifier should remain constant throughout the cmdlet life cycle.</span></span>
  <span data-ttu-id="31adf-141">Ändern Sie nicht die Semantik eines Fehler Bezeichners zwischen den Cmdlet-Versionen.</span><span class="sxs-lookup"><span data-stu-id="31adf-141">Do not change the semantics of an error identifier between cmdlet versions.</span></span>

- <span data-ttu-id="31adf-142">Verwenden Sie Text für einen Fehler Bezeichner, der dem gemeldeten Fehler entspricht.</span><span class="sxs-lookup"><span data-stu-id="31adf-142">Use text for an error identifier that tersely corresponds to the error being reported.</span></span>
  <span data-ttu-id="31adf-143">Verwenden Sie keine Leerzeichen oder Interpunktions Zeichen.</span><span class="sxs-lookup"><span data-stu-id="31adf-143">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="31adf-144">Verwenden Sie das Cmdlet, um nur Fehler Bezeichner zu generieren, die reproduzierbar sind.</span><span class="sxs-lookup"><span data-stu-id="31adf-144">Have your cmdlet generate only error identifiers that are reproducible.</span></span>
  <span data-ttu-id="31adf-145">Beispielsweise sollte kein Bezeichner generiert werden, der einen Prozess Bezeichner enthält.</span><span class="sxs-lookup"><span data-stu-id="31adf-145">For example, it should not generate an identifier that includes a process identifier.</span></span>
  <span data-ttu-id="31adf-146">Fehler Bezeichner sind nur dann für einen Benutzer nützlich, wenn Sie bezeichmern entsprechen, die von anderen Benutzern erkannt werden, die das gleiche Problem aufweisen.</span><span class="sxs-lookup"><span data-stu-id="31adf-146">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="31adf-147">Nicht behandelte Ausnahmen werden von PowerShell unter den folgenden Bedingungen nicht abgefangen:</span><span class="sxs-lookup"><span data-stu-id="31adf-147">Unhandled exceptions are not caught by PowerShell in the following conditions:</span></span>

- <span data-ttu-id="31adf-148">Wenn ein Cmdlet einen neuen Thread erstellt und Code, der in diesem Thread ausgeführt wird, eine nicht behandelte Ausnahme auslöst, wird der Fehler von PowerShell nicht abgefangen, und der Prozess wird beendet.</span><span class="sxs-lookup"><span data-stu-id="31adf-148">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

- <span data-ttu-id="31adf-149">Wenn ein Objekt über Code im Debuggen verfügt oder Methoden verwerfen, die zu einer nicht behandelten Ausnahme geführt haben, wird der Fehler von PowerShell nicht abgefangen, und der Prozess wird beendet.</span><span class="sxs-lookup"><span data-stu-id="31adf-149">If an object has code in its destructor or Dispose methods that causes an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="31adf-150">Melden von nicht abschließenden Fehlern</span><span class="sxs-lookup"><span data-stu-id="31adf-150">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="31adf-151">Jede der Eingabe Verarbeitungsmethoden kann mithilfe der [System. Management. Automation. Cmdlet. Write error][] -Methode einen Fehler ohne Abbruch an den Ausgabestream melden.</span><span class="sxs-lookup"><span data-stu-id="31adf-151">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError][] method.</span></span>

<span data-ttu-id="31adf-152">Im folgenden finden Sie ein Codebeispiel aus diesem Get-proc-Cmdlet, das den [System. Management. Automation. Cmdlet. Write error][] -Befehl in der Überschreibung der [System. Management. Automation. Cmdlet. ProcessRecord][] -Methode veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="31adf-152">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError][] from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord][] method.</span></span>
<span data-ttu-id="31adf-153">In diesem Fall wird der-Befehl durchgeführt, wenn das Cmdlet keinen Prozess für einen angegebenen Prozess Bezeichner finden kann.</span><span class="sxs-lookup"><span data-stu-id="31adf-153">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

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

### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="31adf-154">Dinge, die Sie beim Schreiben von Fehlern bei der nicht Beendigung</span><span class="sxs-lookup"><span data-stu-id="31adf-154">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="31adf-155">Bei einem Fehler ohne Abbruch muss das Cmdlet einen bestimmten Fehler Bezeichner für jedes bestimmte Eingabe Objekt generieren.</span><span class="sxs-lookup"><span data-stu-id="31adf-155">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="31adf-156">Ein Cmdlet muss häufig die PowerShell-Aktion ändern, die von einem Fehler ohne Abbruch erzeugt wird.</span><span class="sxs-lookup"><span data-stu-id="31adf-156">A cmdlet frequently needs to modify the PowerShell action produced by a nonterminating error.</span></span>
<span data-ttu-id="31adf-157">Hierzu können Sie den-Parameter und `ErrorAction` den `ErrorVariable` -Parameter definieren.</span><span class="sxs-lookup"><span data-stu-id="31adf-157">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span>
<span data-ttu-id="31adf-158">Wenn Sie den `ErrorAction` Parameter definieren, zeigt das Cmdlet die Benutzeroptionen [System. Management. Automation. Action Preference][]an. Sie können die Aktion auch direkt beeinflussen, `$ErrorActionPreference` indem Sie die Variable festlegen.</span><span class="sxs-lookup"><span data-stu-id="31adf-158">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.ActionPreference][], you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="31adf-159">Mithilfe `ErrorVariable` des-Parameters, der nicht von der-Einstellung von `ErrorAction`betroffen ist, kann das Cmdlet nicht abschließende Fehler in einer Variablen speichern.</span><span class="sxs-lookup"><span data-stu-id="31adf-159">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span>
<span data-ttu-id="31adf-160">Fehler können an eine vorhandene Fehler Variable angehängt werden, indem ein Pluszeichen (+) am Anfang des Variablen namens hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="31adf-160">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="31adf-161">Code Beispiel</span><span class="sxs-lookup"><span data-stu-id="31adf-161">Code Sample</span></span>

<span data-ttu-id="31adf-162">Den gesamten C# Beispielcode finden Sie unter [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="31adf-162">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="31adf-163">Definieren von Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="31adf-163">Define Object Types and Formatting</span></span>

<span data-ttu-id="31adf-164">PowerShell übergibt Informationen zwischen Cmdlets mithilfe von .NET-Objekten.</span><span class="sxs-lookup"><span data-stu-id="31adf-164">PowerShell passes information between cmdlets using .NET objects.</span></span>
<span data-ttu-id="31adf-165">Folglich muss ein Cmdlet möglicherweise seinen eigenen Typ definieren, oder das Cmdlet muss möglicherweise einen vorhandenen Typ erweitern, der von einem anderen Cmdlet bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="31adf-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span>
<span data-ttu-id="31adf-166">Weitere Informationen zum Definieren neuer Typen oder zum Erweitern vorhandener Typen finden Sie unter [Erweitern von Objekttypen und Formatierung](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="31adf-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="31adf-167">Cmdlet wird aufgebaut</span><span class="sxs-lookup"><span data-stu-id="31adf-167">Building the Cmdlet</span></span>

<span data-ttu-id="31adf-168">Nachdem Sie ein Cmdlet implementiert haben, müssen Sie es über ein Windows PowerShell-Snap-in bei Windows PowerShell registrieren.</span><span class="sxs-lookup"><span data-stu-id="31adf-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span>
<span data-ttu-id="31adf-169">Weitere Informationen zum Registrieren von Cmdlets finden [Sie unter Registrieren von Cmdlets, Anbietern und Host Anwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="31adf-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="31adf-170">Testen des Cmdlets</span><span class="sxs-lookup"><span data-stu-id="31adf-170">Testing the Cmdlet</span></span>

<span data-ttu-id="31adf-171">Wenn das Cmdlet in PowerShell registriert wurde, können Sie es in der Befehlszeile testen.</span><span class="sxs-lookup"><span data-stu-id="31adf-171">When your cmdlet has been registered with PowerShell, you can test it by running it on the command line.</span></span>
<span data-ttu-id="31adf-172">Testen Sie das Get-proc-Beispiel Cmdlet, um zu sehen, ob es einen Fehler meldet:</span><span class="sxs-lookup"><span data-stu-id="31adf-172">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="31adf-173">Starten Sie PowerShell, und verwenden Sie das Get-proc-Cmdlet zum Abrufen der Prozesse mit dem Namen "Test".</span><span class="sxs-lookup"><span data-stu-id="31adf-173">Start PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

    ```powershell
    PS> get-proc -name test
    ```

<span data-ttu-id="31adf-174">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="31adf-174">The following output appears.</span></span>

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a><span data-ttu-id="31adf-175">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="31adf-175">See Also</span></span>

[<span data-ttu-id="31adf-176">Hinzufügen von Parametern, die Pipeline Eingaben verarbeiten</span><span class="sxs-lookup"><span data-stu-id="31adf-176">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="31adf-177">Hinzufügen von Parametern zur Verarbeitung der Befehlszeilen Eingabe</span><span class="sxs-lookup"><span data-stu-id="31adf-177">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="31adf-178">Erstellen Ihres ersten Cmdlets</span><span class="sxs-lookup"><span data-stu-id="31adf-178">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="31adf-179">Erweitern von Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="31adf-179">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="31adf-180">Registrieren von Cmdlets, Anbietern und Host Anwendungen</span><span class="sxs-lookup"><span data-stu-id="31adf-180">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="31adf-181">Windows PowerShell-Referenz</span><span class="sxs-lookup"><span data-stu-id="31adf-181">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="31adf-182">Cmdlet-Beispiele</span><span class="sxs-lookup"><span data-stu-id="31adf-182">Cmdlet Samples</span></span>](./cmdlet-samples.md)

[System. Exception]: /dotnet/api/System.Exception
[System.Exception]: /dotnet/api/System.Exception
[System. Management. Automation. Action Preference]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System. Management. Automation. Cmdlet. ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System. Management. Automation. Cmdlet. Write error]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System. Management. Automation. Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System. Management. Automation. ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System. Management. Automation. ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
