---
title: Erstellen ein Cmdlet ohne Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: 2685215f41c96955fc662d5eee27fc0e7a31da83
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733965"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="3e922-102">Erstellen eines Cmdlet ohne Parameter</span><span class="sxs-lookup"><span data-stu-id="3e922-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="3e922-103">In diesem Abschnitt wird beschrieben, wie ein Cmdlet zu erstellen, die Ruft Informationen aus dem lokalen Computer, ohne die Verwendung von Parametern ab, und klicken Sie dann die Informationen in die Pipeline geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="3e922-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="3e922-104">Das hier beschriebene Cmdlet ist ein Get-Proc-Cmdlet, das Informationen über die Prozesse des lokalen Computers abgerufen, und klicken Sie dann in der Befehlszeile angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3e922-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="3e922-105">Denken Sie daran, dass beim Schreiben von Cmdlets, die Verweisassemblys Windows PowerShell® auf der Festplatte (standardmäßig unter C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0) heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="3e922-105">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span></span> <span data-ttu-id="3e922-106">Sie sind nicht in den globalen Assemblycache (GAC) installiert.</span><span class="sxs-lookup"><span data-stu-id="3e922-106">They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="3e922-107">Benennen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e922-107">Naming the Cmdlet</span></span>

<span data-ttu-id="3e922-108">Ein Cmdlet-Name besteht aus ein Verb an, der angibt, dass das Cmdlet die Aktion und ein Substantiv, der die Elemente angibt, denen mit dem-Cmdlet verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="3e922-108">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="3e922-109">Da dieses Beispiel-Cmdlet "Get-Proc" Prozessobjekte abgerufen wird, verwendet es das Verb "Get", definiert durch die [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) Enumeration und das Nomen "Proc", um anzugeben, dass das Cmdlet auf dem Verarbeiten von Elementen funktioniert.</span><span class="sxs-lookup"><span data-stu-id="3e922-109">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="3e922-110">Bei der Benennung von Cmdlets verwenden Sie nicht die folgenden Zeichen: #, () {} [] & - / \ $;: "' <> &#124; ?</span><span class="sxs-lookup"><span data-stu-id="3e922-110">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="3e922-111">@ \` .</span><span class="sxs-lookup"><span data-stu-id="3e922-111">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="3e922-112">Ein Nomen auswählen</span><span class="sxs-lookup"><span data-stu-id="3e922-112">Choosing a Noun</span></span>

<span data-ttu-id="3e922-113">Sie sollten ein Substantiv auswählen, die spezifisch sind.</span><span class="sxs-lookup"><span data-stu-id="3e922-113">You should choose a noun that is specific.</span></span> <span data-ttu-id="3e922-114">Es wird empfohlen, ein Nomen im singular eine verkürzte Version der Name des Produkts mit dem Präfix verwenden.</span><span class="sxs-lookup"><span data-stu-id="3e922-114">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="3e922-115">Ein Beispiel-Cmdlet-Namen dieses Typs ist "`Get-SQLServer`".</span><span class="sxs-lookup"><span data-stu-id="3e922-115">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="3e922-116">Ein Verb auswählen</span><span class="sxs-lookup"><span data-stu-id="3e922-116">Choosing a Verb</span></span>

<span data-ttu-id="3e922-117">Sie sollten ein Verb in der Menge von genehmigten Verb cmdletnamen verwenden.</span><span class="sxs-lookup"><span data-stu-id="3e922-117">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="3e922-118">Weitere Informationen zu den genehmigten Cmdlet-Verben, finden Sie unter [Cmdlet Verbnamen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="3e922-118">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="3e922-119">Definieren die Cmdlet-Klasse</span><span class="sxs-lookup"><span data-stu-id="3e922-119">Defining the Cmdlet Class</span></span>

<span data-ttu-id="3e922-120">Nachdem Sie einen Cmdlet-Namen ausgewählt haben, definieren Sie eine .NET-Klasse, um das-Cmdlet zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="3e922-120">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="3e922-121">So sieht die Definition der Klasse für dieses Beispiel Get-Proc-Cmdlet aus:</span><span class="sxs-lookup"><span data-stu-id="3e922-121">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="3e922-122">Beachten Sie, dass vor der Klassendefinition den [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) Attribut, mit der Syntax `[Cmdlet(verb, noun, ...)]`, dient zum Identifizieren dieser Klasse als Cmdlet verwendet.</span><span class="sxs-lookup"><span data-stu-id="3e922-122">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="3e922-123">Dies ist das einzige erforderliche Attribut für alle Cmdlets, und es ermöglicht, dass die Windows PowerShell-Laufzeit sie richtig aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="3e922-123">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="3e922-124">Sie können die Attribut-Stichworte, um weitere Deklarieren der Klasse bei Bedarf festlegen.</span><span class="sxs-lookup"><span data-stu-id="3e922-124">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="3e922-125">Denken Sie daran, dass die Attributdeklaration für unser Beispiel GetProcCommand-Klasse nur die Nomen und Verb-Namen für das Cmdlet "Get-Proc" deklariert.</span><span class="sxs-lookup"><span data-stu-id="3e922-125">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="3e922-126">Für alle Klassen in einer Windows PowerShell-Attribut entsprechen die Schlüsselwörter, die Sie festlegen können, die Eigenschaften der Attributklasse.</span><span class="sxs-lookup"><span data-stu-id="3e922-126">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="3e922-127">Bei der Benennung von der Klasse des-Cmdlets ist es empfiehlt sich, den Cmdlet-Namen in den Namen der Klasse entsprechen.</span><span class="sxs-lookup"><span data-stu-id="3e922-127">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="3e922-128">Klicken Sie zu diesem Zweck verwenden Sie das Formular "VerbNounCommand", und Ersetzen Sie "Verb" und "Nomen", mit dem Verb und Substantiv im Cmdlet-Namen verwendet.</span><span class="sxs-lookup"><span data-stu-id="3e922-128">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="3e922-129">Wie in der vorherigen Klassendefinition angezeigt wird, wird die Beispiel-Cmdlet "Get-Proc" definiert eine Klasse namens GetProcCommand, abgeleitet von der [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) Basisklasse.</span><span class="sxs-lookup"><span data-stu-id="3e922-129">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e922-130">Wenn Sie möchten ein Cmdlet definieren, der die Windows PowerShell-Laufzeit direkt zugreift, sollte die Klasse .NET leiten Sie von der [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) Basisklasse.</span><span class="sxs-lookup"><span data-stu-id="3e922-130">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="3e922-131">Weitere Informationen zu dieser Klasse finden Sie unter [erstellen ein Cmdlet, Parametersätze definiert](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="3e922-131">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3e922-132">Die Klasse für ein Cmdlet muss explizit als öffentlich markiert werden.</span><span class="sxs-lookup"><span data-stu-id="3e922-132">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="3e922-133">Klassen, die nicht als öffentlich markiert werden werden standardmäßig auf interne und werden von der Windows PowerShell-Laufzeit nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="3e922-133">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="3e922-134">Windows PowerShell verwendet die [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) Namespace-URI für die Cmdlet-Klassen.</span><span class="sxs-lookup"><span data-stu-id="3e922-134">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="3e922-135">Es wird empfohlen, um die Cmdlet-Klassen in einem Namespace Befehle für Ihren API-Namespace, z. B. xxx.PS.Commands zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="3e922-135">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="3e922-136">Überschreiben einer Eingabeverarbeitungsmethode</span><span class="sxs-lookup"><span data-stu-id="3e922-136">Overriding an Input Processing Method</span></span>

<span data-ttu-id="3e922-137">Die [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) Klasse enthält drei wichtigsten Eingabeverarbeitung-Methoden, die mindestens eine der Ihr Cmdlet muss außer Kraft setzen.</span><span class="sxs-lookup"><span data-stu-id="3e922-137">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="3e922-138">Weitere Informationen zur Verarbeitung von Datensätzen in Windows PowerShell finden Sie unter [Funktionsweise von Windows PowerShell](/previous-versions//ms714658(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="3e922-138">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

<span data-ttu-id="3e922-139">Für alle Arten von Eingaben, die Windows PowerShell-Laufzeit ruft [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) um Verarbeitung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="3e922-139">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="3e922-140">Wenn Ihr Cmdlet einige vorverarbeitung oder Setup durchführen muss, können sie dazu diese Methode überschreiben.</span><span class="sxs-lookup"><span data-stu-id="3e922-140">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="3e922-141">Windows PowerShell verwendet den Begriff "Datensatz", beschreiben den Satz von Parameterwerten, die bereitgestellt werden, wenn ein Cmdlet aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="3e922-141">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="3e922-142">Wenn Ihr Cmdlet Pipelineeingabe akzeptiert, müssen sie überschreiben die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode, und optional die [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)Methode.</span><span class="sxs-lookup"><span data-stu-id="3e922-142">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="3e922-143">Beispielsweise kann ein Cmdlet beide Methoden überschreiben, wenn Sie dieses Tool sammelt alle Benutzereingabe mit [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) und klicken Sie dann auf die Eingabe als Ganzes und nicht als ein Element zu einem Zeitpunkt, als die `Sort-Object` Cmdlet bewirkt.</span><span class="sxs-lookup"><span data-stu-id="3e922-143">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="3e922-144">Wenn Ihr Cmdlet keine Pipelineeingabe akzeptiert, sollte sie überschreiben die [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Methode.</span><span class="sxs-lookup"><span data-stu-id="3e922-144">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="3e922-145">Beachten Sie, dass diese Methode häufig, anstelle von verwendet wird [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) Wenn das-Cmdlet kann nicht für ein Element zu einem Zeitpunkt wie der Fall für ein Cmdlet sortiert ist.</span><span class="sxs-lookup"><span data-stu-id="3e922-145">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="3e922-146">Da dieses Beispiel-Cmdlet "Get-Proc" Pipelineeingabe empfangen muss, überschreibt es die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode und verwendet die standardimplementierungen für [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) und [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span><span class="sxs-lookup"><span data-stu-id="3e922-146">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="3e922-147">Die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) "Override" Ruft die Prozesse ab und schreibt sie in der Befehlszeile mithilfe der [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) Methode.</span><span class="sxs-lookup"><span data-stu-id="3e922-147">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="3e922-148">Wichtige Fakten über Verarbeitung von Benutzereingaben</span><span class="sxs-lookup"><span data-stu-id="3e922-148">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="3e922-149">Die standardmäßige Quelle für die Eingabe ist ein expliziter Objekt (z. B. eine Zeichenfolge), die vom Benutzer in der Befehlszeile angegeben.</span><span class="sxs-lookup"><span data-stu-id="3e922-149">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="3e922-150">Weitere Informationen finden Sie unter [erstellen ein Cmdlet, um die Eingabe über die Befehlszeile](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="3e922-150">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="3e922-151">Ein eingabeverarbeitungsmethode kann Eingabe auch die Ausgabe-Objekt von einem upstream-Cmdlet für die Pipeline empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="3e922-151">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="3e922-152">Weitere Informationen finden Sie unter [erstellen ein Cmdlet zum Prozess Pipelineeingabe](./adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="3e922-152">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="3e922-153">Beachten Sie, dass Ihr Cmdlet empfangen von Eingaben aus einer Kombination von Befehlszeilen und pipeline kann Datenquellen.</span><span class="sxs-lookup"><span data-stu-id="3e922-153">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="3e922-154">Das Cmdlet "downstream" möglicherweise kein lange oder überhaupt nicht zurück.</span><span class="sxs-lookup"><span data-stu-id="3e922-154">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="3e922-155">Aus diesem Grund die eingabeverarbeitungsmethode in Ihrem Cmdlet sollte nicht richten Sperren während des Aufrufs [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), insbesondere Sperren, die für die der Bereich reicht hinter der Cmdlet-Instanz bis.</span><span class="sxs-lookup"><span data-stu-id="3e922-155">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e922-156">Cmdlets sollten niemals Aufrufen [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) oder dessen Entsprechung.</span><span class="sxs-lookup"><span data-stu-id="3e922-156">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="3e922-157">Ihr Cmdlet möglicherweise Objektvariablen bereinigt werden, wenn sie abgeschlossen ist verarbeiten (z. B. wenn ein Dateihandle in geöffnet der [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -Methode und behält das Handle öffnen für die Verwendung von [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span><span class="sxs-lookup"><span data-stu-id="3e922-157">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="3e922-158">Es ist wichtig zu beachten, dass die Windows PowerShell-Laufzeit nicht immer rufen die [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methode, die Bereinigung Objekte ausführen soll.</span><span class="sxs-lookup"><span data-stu-id="3e922-158">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="3e922-159">Z. B. [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) kann nicht aufgerufen werden, wenn das Cmdlet Zielpfads abgebrochen wird oder wenn ein Abbruch tritt Fehler in einem beliebigen Teil des Cmdlets auf.</span><span class="sxs-lookup"><span data-stu-id="3e922-159">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="3e922-160">Aus diesem Grund sollte ein Cmdlet, das Objekt Bereinigung erfordert die vollständige implementieren [System.IDisposable](/dotnet/api/System.IDisposable) Muster, einschließlich des Finalizers, sodass beide von die Laufzeit aufgerufen werden kann [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) und [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) am Ende der Verarbeitung.</span><span class="sxs-lookup"><span data-stu-id="3e922-160">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3e922-161">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="3e922-161">Code Sample</span></span>

<span data-ttu-id="3e922-162">Für die vollständige C# Beispielcode, finden Sie unter [GetProcessSample01-Beispiel](./getprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3e922-162">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="3e922-163">Definieren von Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="3e922-163">Defining Object Types and Formatting</span></span>

<span data-ttu-id="3e922-164">Windows PowerShell übergibt Informationen zwischen Cmdlets, die mithilfe von .NET-Objekten.</span><span class="sxs-lookup"><span data-stu-id="3e922-164">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="3e922-165">Daher müssen möglicherweise ein Cmdlet seinen eigenen Typ definieren, oder das-Cmdlet zum Erweitern eines vorhandenen Typs, der durch ein anderes Cmdlet angegeben müssen.</span><span class="sxs-lookup"><span data-stu-id="3e922-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="3e922-166">Weitere Informationen zum Definieren neuer Typen, oder erweitern vorhandene Typen finden Sie unter [Objekttypen erweitern und Formatierung](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="3e922-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="3e922-167">Erstellen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e922-167">Building the Cmdlet</span></span>

<span data-ttu-id="3e922-168">Nach der Implementierung eines Cmdlets, müssen Sie es mit Windows PowerShell über eine Windows PowerShell-Snap-in registrieren.</span><span class="sxs-lookup"><span data-stu-id="3e922-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="3e922-169">Weitere Informationen zum Registrieren von Cmdlets finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="3e922-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="3e922-170">Testen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e922-170">Testing the Cmdlet</span></span>

<span data-ttu-id="3e922-171">Wenn Ihr Cmdlet in Windows PowerShell registriert wurde, können Sie es testen, indem Sie sie in der Befehlszeile ausführen.</span><span class="sxs-lookup"><span data-stu-id="3e922-171">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="3e922-172">Der Code für unsere Beispiel-Get-Proc-Cmdlet ist klein, aber es verwendet weiterhin die Windows PowerShell-Laufzeit und eine vorhandene .NET-Objekt, das ausreichend, um es zu nutzen ist.</span><span class="sxs-lookup"><span data-stu-id="3e922-172">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="3e922-173">Wir testen, um besser zu verstehen, was mit Get-Proc möglich ist und wie die Ausgabe verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="3e922-173">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="3e922-174">Weitere Informationen zur Verwendung von Cmdlets, über die Befehlszeile finden Sie unter den [erste Schritte mit Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="3e922-174">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="3e922-175">Starten Sie Windows PowerShell, und erhalten Sie die aktuellen Prozessen auf dem Computer ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="3e922-175">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="3e922-176">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3e922-176">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="3e922-177">Weisen Sie eine Variable, auf die Cmdlet-Ergebnisse für eine einfachere Bearbeitung.</span><span class="sxs-lookup"><span data-stu-id="3e922-177">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="3e922-178">Ruft die Anzahl von Prozessen.</span><span class="sxs-lookup"><span data-stu-id="3e922-178">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="3e922-179">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3e922-179">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="3e922-180">Rufen Sie einen bestimmten Prozess.</span><span class="sxs-lookup"><span data-stu-id="3e922-180">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="3e922-181">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3e922-181">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="3e922-182">Die Startzeit für diesen Prozess zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="3e922-182">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="3e922-183">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3e922-183">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="3e922-184">Rufen Sie die Prozesse, die für die Anzahl der Handles größer als 500 ist, und sortieren Sie des Ergebnisses.</span><span class="sxs-lookup"><span data-stu-id="3e922-184">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="3e922-185">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3e922-185">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="3e922-186">Verwenden der `Get-Member` -Cmdlet zum Auflisten der Eigenschaften, die für jeden Prozess zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="3e922-186">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="3e922-187">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3e922-187">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="3e922-188">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3e922-188">See Also</span></span>

[<span data-ttu-id="3e922-189">Erstellen ein Cmdlet aus, um über die Befehlszeile verarbeiten</span><span class="sxs-lookup"><span data-stu-id="3e922-189">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="3e922-190">Erstellen ein Cmdlet aus, um die Pipelineeingabe zu verarbeiten</span><span class="sxs-lookup"><span data-stu-id="3e922-190">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="3e922-191">Vorgehensweise: Erstellen eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="3e922-191">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="3e922-192">[Erweitern die Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="3e922-192">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="3e922-193">[Funktionsweise von Windows PowerShell](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="3e922-193">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="3e922-194">[So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="3e922-194">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="3e922-195">Windows PowerShell-Referenz</span><span class="sxs-lookup"><span data-stu-id="3e922-195">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="3e922-196">Cmdlet-Beispiele</span><span class="sxs-lookup"><span data-stu-id="3e922-196">Cmdlet Samples</span></span>](./cmdlet-samples.md)