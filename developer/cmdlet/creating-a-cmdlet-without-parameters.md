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
ms.openlocfilehash: c380b28570c955de6f41152fd617f5c1b0f9e4bd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068333"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="0a474-102">Erstellen eines Cmdlet ohne Parameter</span><span class="sxs-lookup"><span data-stu-id="0a474-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="0a474-103">In diesem Abschnitt wird beschrieben, wie ein Cmdlet zu erstellen, die Ruft Informationen aus dem lokalen Computer, ohne die Verwendung von Parametern ab, und klicken Sie dann die Informationen in die Pipeline geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="0a474-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="0a474-104">Das hier beschriebene Cmdlet ist ein Get-Proc-Cmdlet, das Informationen über die Prozesse des lokalen Computers abgerufen, und klicken Sie dann in der Befehlszeile angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0a474-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

<span data-ttu-id="0a474-105">Die folgenden: Themen in diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="0a474-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="0a474-106">Benennen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0a474-106">Naming the Cmdlet</span></span>](#Naming-the-Cmdlet)

- [<span data-ttu-id="0a474-107">Definieren die Cmdlet-Klasse</span><span class="sxs-lookup"><span data-stu-id="0a474-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="0a474-108">Überschreiben einer Eingabeverarbeitungsmethode</span><span class="sxs-lookup"><span data-stu-id="0a474-108">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="0a474-109">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="0a474-109">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="0a474-110">Definieren von Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="0a474-110">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="0a474-111">Erstellen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0a474-111">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="0a474-112">Testen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0a474-112">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

> [!NOTE]
> <span data-ttu-id="0a474-113">Denken Sie daran, dass beim Schreiben von Cmdlets, die Verweisassemblys Windows PowerShell® auf der Festplatte (standardmäßig unter C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0) heruntergeladen werden. Sie sind nicht in den globalen Assemblycache (GAC) installiert.</span><span class="sxs-lookup"><span data-stu-id="0a474-113">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="0a474-114">Benennen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0a474-114">Naming the Cmdlet</span></span>

<span data-ttu-id="0a474-115">Ein Cmdlet-Name besteht aus ein Verb an, der angibt, dass das Cmdlet die Aktion und ein Substantiv, der die Elemente angibt, denen mit dem-Cmdlet verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="0a474-115">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="0a474-116">Da dieses Beispiel-Cmdlet "Get-Proc" Prozessobjekte abgerufen wird, verwendet es das Verb "Get", definiert durch die [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) Enumeration und das Nomen "Proc", um anzugeben, dass das Cmdlet auf dem Verarbeiten von Elementen funktioniert.</span><span class="sxs-lookup"><span data-stu-id="0a474-116">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="0a474-117">Bei der Benennung von Cmdlets verwenden Sie nicht die folgenden Zeichen: #, () {} [] & - / \ $;: "' <> &#124; ?</span><span class="sxs-lookup"><span data-stu-id="0a474-117">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="0a474-118">@ \` .</span><span class="sxs-lookup"><span data-stu-id="0a474-118">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="0a474-119">Ein Nomen auswählen</span><span class="sxs-lookup"><span data-stu-id="0a474-119">Choosing a Noun</span></span>

<span data-ttu-id="0a474-120">Sie sollten ein Substantiv auswählen, die spezifisch sind.</span><span class="sxs-lookup"><span data-stu-id="0a474-120">You should choose a noun that is specific.</span></span> <span data-ttu-id="0a474-121">Es wird empfohlen, ein Nomen im singular eine verkürzte Version der Name des Produkts mit dem Präfix verwenden.</span><span class="sxs-lookup"><span data-stu-id="0a474-121">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="0a474-122">Ein Beispiel-Cmdlet-Namen dieses Typs ist "`Get-SQLServer`".</span><span class="sxs-lookup"><span data-stu-id="0a474-122">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="0a474-123">Ein Verb auswählen</span><span class="sxs-lookup"><span data-stu-id="0a474-123">Choosing a Verb</span></span>

<span data-ttu-id="0a474-124">Sie sollten ein Verb in der Menge von genehmigten Verb cmdletnamen verwenden.</span><span class="sxs-lookup"><span data-stu-id="0a474-124">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="0a474-125">Weitere Informationen zu den genehmigten Cmdlet-Verben, finden Sie unter [Cmdlet Verbnamen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="0a474-125">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="0a474-126">Definieren die Cmdlet-Klasse</span><span class="sxs-lookup"><span data-stu-id="0a474-126">Defining the Cmdlet Class</span></span>

<span data-ttu-id="0a474-127">Nachdem Sie einen Cmdlet-Namen ausgewählt haben, definieren Sie eine .NET-Klasse, um das-Cmdlet zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="0a474-127">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="0a474-128">So sieht die Definition der Klasse für dieses Beispiel Get-Proc-Cmdlet aus:</span><span class="sxs-lookup"><span data-stu-id="0a474-128">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="0a474-129">Beachten Sie, dass vor der Klassendefinition den [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) Attribut, mit der Syntax `[Cmdlet(verb, noun, ...)]`, dient zum Identifizieren dieser Klasse als Cmdlet verwendet.</span><span class="sxs-lookup"><span data-stu-id="0a474-129">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="0a474-130">Dies ist das einzige erforderliche Attribut für alle Cmdlets, und es ermöglicht, dass die Windows PowerShell-Laufzeit sie richtig aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="0a474-130">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="0a474-131">Sie können die Attribut-Stichworte, um weitere Deklarieren der Klasse bei Bedarf festlegen.</span><span class="sxs-lookup"><span data-stu-id="0a474-131">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="0a474-132">Denken Sie daran, dass die Attributdeklaration für unser Beispiel GetProcCommand-Klasse nur die Nomen und Verb-Namen für das Cmdlet "Get-Proc" deklariert.</span><span class="sxs-lookup"><span data-stu-id="0a474-132">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="0a474-133">Für alle Klassen in einer Windows PowerShell-Attribut entsprechen die Schlüsselwörter, die Sie festlegen können, die Eigenschaften der Attributklasse.</span><span class="sxs-lookup"><span data-stu-id="0a474-133">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="0a474-134">Bei der Benennung von der Klasse des-Cmdlets ist es empfiehlt sich, den Cmdlet-Namen in den Namen der Klasse entsprechen.</span><span class="sxs-lookup"><span data-stu-id="0a474-134">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="0a474-135">Klicken Sie zu diesem Zweck verwenden Sie das Formular "VerbNounCommand", und Ersetzen Sie "Verb" und "Nomen", mit dem Verb und Substantiv im Cmdlet-Namen verwendet.</span><span class="sxs-lookup"><span data-stu-id="0a474-135">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="0a474-136">Wie in der vorherigen Klassendefinition angezeigt wird, wird die Beispiel-Cmdlet "Get-Proc" definiert eine Klasse namens GetProcCommand, abgeleitet von der [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) Basisklasse.</span><span class="sxs-lookup"><span data-stu-id="0a474-136">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0a474-137">Wenn Sie möchten ein Cmdlet definieren, der die Windows PowerShell-Laufzeit direkt zugreift, sollte die Klasse .NET leiten Sie von der [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) Basisklasse.</span><span class="sxs-lookup"><span data-stu-id="0a474-137">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="0a474-138">Weitere Informationen zu dieser Klasse finden Sie unter [erstellen ein Cmdlet, Parametersätze definiert](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="0a474-138">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0a474-139">Die Klasse für ein Cmdlet muss explizit als öffentlich markiert werden.</span><span class="sxs-lookup"><span data-stu-id="0a474-139">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="0a474-140">Klassen, die nicht als öffentlich markiert werden werden standardmäßig auf interne und werden von der Windows PowerShell-Laufzeit nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="0a474-140">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="0a474-141">Windows PowerShell verwendet die [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) Namespace-URI für die Cmdlet-Klassen.</span><span class="sxs-lookup"><span data-stu-id="0a474-141">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="0a474-142">Es wird empfohlen, um die Cmdlet-Klassen in einem Namespace Befehle für Ihren API-Namespace, z. B. xxx.PS.Commands zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="0a474-142">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="0a474-143">Überschreiben einer Eingabeverarbeitungsmethode</span><span class="sxs-lookup"><span data-stu-id="0a474-143">Overriding an Input Processing Method</span></span>

<span data-ttu-id="0a474-144">Die [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) Klasse enthält drei wichtigsten Eingabeverarbeitung-Methoden, die mindestens eine der Ihr Cmdlet muss außer Kraft setzen.</span><span class="sxs-lookup"><span data-stu-id="0a474-144">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="0a474-145">Weitere Informationen zur Verarbeitung von Datensätzen in Windows PowerShell finden Sie unter [Funktionsweise von Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span><span class="sxs-lookup"><span data-stu-id="0a474-145">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span></span>

<span data-ttu-id="0a474-146">Für alle Arten von Eingaben, die Windows PowerShell-Laufzeit ruft [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) um Verarbeitung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="0a474-146">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="0a474-147">Wenn Ihr Cmdlet einige vorverarbeitung oder Setup durchführen muss, können sie dazu diese Methode überschreiben.</span><span class="sxs-lookup"><span data-stu-id="0a474-147">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="0a474-148">Windows PowerShell verwendet den Begriff "Datensatz", beschreiben den Satz von Parameterwerten, die bereitgestellt werden, wenn ein Cmdlet aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="0a474-148">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="0a474-149">Wenn Ihr Cmdlet Pipelineeingabe akzeptiert, müssen sie überschreiben die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode, und optional die [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)Methode.</span><span class="sxs-lookup"><span data-stu-id="0a474-149">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="0a474-150">Beispielsweise kann ein Cmdlet beide Methoden überschreiben, wenn Sie dieses Tool sammelt alle Benutzereingabe mit [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) und klicken Sie dann auf die Eingabe als Ganzes und nicht als ein Element zu einem Zeitpunkt, als die `Sort-Object` Cmdlet bewirkt.</span><span class="sxs-lookup"><span data-stu-id="0a474-150">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="0a474-151">Wenn Ihr Cmdlet keine Pipelineeingabe akzeptiert, sollte sie überschreiben die [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Methode.</span><span class="sxs-lookup"><span data-stu-id="0a474-151">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="0a474-152">Beachten Sie, dass diese Methode häufig, anstelle von verwendet wird [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) Wenn das-Cmdlet kann nicht für ein Element zu einem Zeitpunkt wie der Fall für ein Cmdlet sortiert ist.</span><span class="sxs-lookup"><span data-stu-id="0a474-152">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="0a474-153">Da dieses Beispiel-Cmdlet "Get-Proc" Pipelineeingabe empfangen muss, überschreibt es die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode und verwendet die standardimplementierungen für [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) und [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span><span class="sxs-lookup"><span data-stu-id="0a474-153">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="0a474-154">Die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) "Override" Ruft die Prozesse ab und schreibt sie in der Befehlszeile mithilfe der [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) Methode.</span><span class="sxs-lookup"><span data-stu-id="0a474-154">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

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

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="0a474-155">Wichtige Fakten über Verarbeitung von Benutzereingaben</span><span class="sxs-lookup"><span data-stu-id="0a474-155">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="0a474-156">Die standardmäßige Quelle für die Eingabe ist ein expliziter Objekt (z. B. eine Zeichenfolge), die vom Benutzer in der Befehlszeile angegeben.</span><span class="sxs-lookup"><span data-stu-id="0a474-156">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="0a474-157">Weitere Informationen finden Sie unter [erstellen ein Cmdlet, um die Eingabe über die Befehlszeile](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="0a474-157">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="0a474-158">Ein eingabeverarbeitungsmethode kann Eingabe auch die Ausgabe-Objekt von einem upstream-Cmdlet für die Pipeline empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="0a474-158">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="0a474-159">Weitere Informationen finden Sie unter [erstellen ein Cmdlet zum Prozess Pipelineeingabe](./adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="0a474-159">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="0a474-160">Beachten Sie, dass Ihr Cmdlet empfangen von Eingaben aus einer Kombination von Befehlszeilen und pipeline kann Datenquellen.</span><span class="sxs-lookup"><span data-stu-id="0a474-160">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="0a474-161">Das Cmdlet "downstream" möglicherweise kein lange oder überhaupt nicht zurück.</span><span class="sxs-lookup"><span data-stu-id="0a474-161">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="0a474-162">Aus diesem Grund die eingabeverarbeitungsmethode in Ihrem Cmdlet sollte nicht richten Sperren während des Aufrufs [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), insbesondere Sperren, die für die der Bereich reicht hinter der Cmdlet-Instanz bis.</span><span class="sxs-lookup"><span data-stu-id="0a474-162">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0a474-163">Cmdlets sollten niemals Aufrufen [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) oder dessen Entsprechung.</span><span class="sxs-lookup"><span data-stu-id="0a474-163">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="0a474-164">Ihr Cmdlet möglicherweise Objektvariablen bereinigt werden, wenn sie abgeschlossen ist verarbeiten (z. B. wenn ein Dateihandle in geöffnet der [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -Methode und behält das Handle öffnen für die Verwendung von [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span><span class="sxs-lookup"><span data-stu-id="0a474-164">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="0a474-165">Es ist wichtig zu beachten, dass die Windows PowerShell-Laufzeit nicht immer rufen die [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methode, die Bereinigung Objekte ausführen soll.</span><span class="sxs-lookup"><span data-stu-id="0a474-165">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="0a474-166">Z. B. [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) kann nicht aufgerufen werden, wenn das Cmdlet Zielpfads abgebrochen wird oder wenn ein Abbruch tritt Fehler in einem beliebigen Teil des Cmdlets auf.</span><span class="sxs-lookup"><span data-stu-id="0a474-166">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="0a474-167">Aus diesem Grund sollte ein Cmdlet, das Objekt Bereinigung erfordert die vollständige implementieren [System.IDisposable](/dotnet/api/System.IDisposable) Muster, einschließlich des Finalizers, sodass beide von die Laufzeit aufgerufen werden kann [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) und [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) am Ende der Verarbeitung.</span><span class="sxs-lookup"><span data-stu-id="0a474-167">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="0a474-168">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="0a474-168">Code Sample</span></span>

<span data-ttu-id="0a474-169">Für die vollständige C# Beispielcode, finden Sie unter [GetProcessSample01-Beispiel](./getprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="0a474-169">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="0a474-170">Definieren von Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="0a474-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="0a474-171">Windows PowerShell übergibt Informationen zwischen Cmdlets, die mithilfe von .NET-Objekten.</span><span class="sxs-lookup"><span data-stu-id="0a474-171">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="0a474-172">Daher müssen möglicherweise ein Cmdlet seinen eigenen Typ definieren, oder das-Cmdlet zum Erweitern eines vorhandenen Typs, der durch ein anderes Cmdlet angegeben müssen.</span><span class="sxs-lookup"><span data-stu-id="0a474-172">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="0a474-173">Weitere Informationen zum Definieren neuer Typen, oder erweitern vorhandene Typen finden Sie unter [Objekttypen erweitern und Formatierung](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="0a474-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="0a474-174">Erstellen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0a474-174">Building the Cmdlet</span></span>

<span data-ttu-id="0a474-175">Nach der Implementierung eines Cmdlets, müssen Sie es mit Windows PowerShell über eine Windows PowerShell-Snap-in registrieren.</span><span class="sxs-lookup"><span data-stu-id="0a474-175">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="0a474-176">Weitere Informationen zum Registrieren von Cmdlets finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="0a474-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="0a474-177">Testen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0a474-177">Testing the Cmdlet</span></span>

<span data-ttu-id="0a474-178">Wenn Ihr Cmdlet in Windows PowerShell registriert wurde, können Sie es testen, indem Sie sie in der Befehlszeile ausführen.</span><span class="sxs-lookup"><span data-stu-id="0a474-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="0a474-179">Der Code für unsere Beispiel-Get-Proc-Cmdlet ist klein, aber es verwendet weiterhin die Windows PowerShell-Laufzeit und eine vorhandene .NET-Objekt, das ausreichend, um es zu nutzen ist.</span><span class="sxs-lookup"><span data-stu-id="0a474-179">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="0a474-180">Wir testen, um besser zu verstehen, was mit Get-Proc möglich ist und wie die Ausgabe verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="0a474-180">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="0a474-181">Weitere Informationen zur Verwendung von Cmdlets, über die Befehlszeile finden Sie unter den [erste Schritte mit Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="0a474-181">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="0a474-182">Starten Sie Windows PowerShell, und erhalten Sie die aktuellen Prozessen auf dem Computer ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="0a474-182">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="0a474-183">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0a474-183">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="0a474-184">Weisen Sie eine Variable, auf die Cmdlet-Ergebnisse für eine einfachere Bearbeitung.</span><span class="sxs-lookup"><span data-stu-id="0a474-184">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="0a474-185">Ruft die Anzahl von Prozessen.</span><span class="sxs-lookup"><span data-stu-id="0a474-185">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="0a474-186">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0a474-186">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="0a474-187">Rufen Sie einen bestimmten Prozess.</span><span class="sxs-lookup"><span data-stu-id="0a474-187">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="0a474-188">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0a474-188">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="0a474-189">Die Startzeit für diesen Prozess zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="0a474-189">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="0a474-190">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0a474-190">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="0a474-191">Rufen Sie die Prozesse, die für die Anzahl der Handles größer als 500 ist, und sortieren Sie des Ergebnisses.</span><span class="sxs-lookup"><span data-stu-id="0a474-191">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="0a474-192">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0a474-192">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="0a474-193">Verwenden der `Get-Member` -Cmdlet zum Auflisten der Eigenschaften, die für jeden Prozess zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="0a474-193">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="0a474-194">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0a474-194">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="0a474-195">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0a474-195">See Also</span></span>

[<span data-ttu-id="0a474-196">Erstellen ein Cmdlet aus, um über die Befehlszeile verarbeiten</span><span class="sxs-lookup"><span data-stu-id="0a474-196">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="0a474-197">Erstellen ein Cmdlet aus, um die Pipelineeingabe zu verarbeiten</span><span class="sxs-lookup"><span data-stu-id="0a474-197">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="0a474-198">Vorgehensweise: Erstellen eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="0a474-198">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="0a474-199">Erweitern die Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="0a474-199">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="0a474-200">Funktionsweise von Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a474-200">How Windows PowerShell Works</span></span>](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[<span data-ttu-id="0a474-201">So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen</span><span class="sxs-lookup"><span data-stu-id="0a474-201">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="0a474-202">Windows PowerShell-Referenz</span><span class="sxs-lookup"><span data-stu-id="0a474-202">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="0a474-203">Cmdlet-Beispiele</span><span class="sxs-lookup"><span data-stu-id="0a474-203">Cmdlet Samples</span></span>](./cmdlet-samples.md)