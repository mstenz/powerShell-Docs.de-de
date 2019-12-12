---
title: Erstellen eines Cmdlets ohne Parameter | Microsoft-Dokumentation
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
ms.openlocfilehash: af41c2c9855310d047404114a07b27180a7aa8fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74415671"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="f46d7-102">Erstellen eines Cmdlet ohne Parameter</span><span class="sxs-lookup"><span data-stu-id="f46d7-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="f46d7-103">In diesem Abschnitt wird beschrieben, wie Sie ein Cmdlet erstellen, das Informationen vom lokalen Computer abruft, ohne Parameter zu verwenden, und dann die Informationen in die Pipeline schreibt.</span><span class="sxs-lookup"><span data-stu-id="f46d7-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="f46d7-104">Das hier beschriebene Cmdlet ist ein Get-proc-Cmdlet, das Informationen zu den Prozessen des lokalen Computers abruft und diese Informationen dann in der Befehlszeile anzeigt.</span><span class="sxs-lookup"><span data-stu-id="f46d7-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="f46d7-105">Beachten Sie, dass beim Schreiben von Cmdlets die Windows PowerShell-® Verweisassemblys auf den Datenträger heruntergeladen werden (standardmäßig unter "c:\Programme\Reference assemblies\microsoft\windowspowershell\v1.0").</span><span class="sxs-lookup"><span data-stu-id="f46d7-105">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span></span> <span data-ttu-id="f46d7-106">Sie sind nicht im globalen Assemblycache (GAC) installiert.</span><span class="sxs-lookup"><span data-stu-id="f46d7-106">They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="f46d7-107">Benennen des Cmdlets</span><span class="sxs-lookup"><span data-stu-id="f46d7-107">Naming the Cmdlet</span></span>

<span data-ttu-id="f46d7-108">Ein Cmdlet-Name besteht aus einem Verb, das die Aktion angibt, die das Cmdlet annimmt, und einem Substantiv, das die Elemente angibt, auf die das Cmdlet angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="f46d7-108">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="f46d7-109">Da das Get-proc-Beispiel-Cmdlet Prozess Objekte abruft, wird das Verb "Get" verwendet, das von der [System. Management. Automation. verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) -Enumeration definiert wird, und das Nomen "proc", um anzugeben, dass das Cmdlet für Prozesselemente funktioniert.</span><span class="sxs-lookup"><span data-stu-id="f46d7-109">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="f46d7-110">Verwenden Sie beim Benennen von Cmdlets keines der folgenden Zeichen: #, () {} [] &-/\ $; : "" < > &#124; ?</span><span class="sxs-lookup"><span data-stu-id="f46d7-110">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="f46d7-111">@ \` .</span><span class="sxs-lookup"><span data-stu-id="f46d7-111">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="f46d7-112">Auswählen eines Substantivs</span><span class="sxs-lookup"><span data-stu-id="f46d7-112">Choosing a Noun</span></span>

<span data-ttu-id="f46d7-113">Sie sollten ein bestimmtes Substantiv auswählen.</span><span class="sxs-lookup"><span data-stu-id="f46d7-113">You should choose a noun that is specific.</span></span> <span data-ttu-id="f46d7-114">Es empfiehlt sich, ein Singular-Substantiv zu verwenden, das mit einer verkürzten Version des Produkt namens versehen ist.</span><span class="sxs-lookup"><span data-stu-id="f46d7-114">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="f46d7-115">Ein Beispiel für einen Cmdlet-Namen dieses Typs ist "`Get-SQLServer`".</span><span class="sxs-lookup"><span data-stu-id="f46d7-115">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="f46d7-116">Auswählen eines Verbs</span><span class="sxs-lookup"><span data-stu-id="f46d7-116">Choosing a Verb</span></span>

<span data-ttu-id="f46d7-117">Sie sollten ein Verb aus dem Satz genehmigter Cmdlet-Verb Namen verwenden.</span><span class="sxs-lookup"><span data-stu-id="f46d7-117">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="f46d7-118">Weitere Informationen zu den genehmigten Cmdlet-Verben finden Sie unter [Cmdlet-Verb Namen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="f46d7-118">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="f46d7-119">Definieren der Cmdlet-Klasse</span><span class="sxs-lookup"><span data-stu-id="f46d7-119">Defining the Cmdlet Class</span></span>

<span data-ttu-id="f46d7-120">Nachdem Sie einen Cmdlet-Namen ausgewählt haben, definieren Sie eine .NET-Klasse, um das Cmdlet zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="f46d7-120">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="f46d7-121">Hier ist die Klassendefinition für dieses Beispiel-Get-proc-Cmdlet:</span><span class="sxs-lookup"><span data-stu-id="f46d7-121">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="f46d7-122">Beachten Sie, dass das [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) -Attribut, das mit der Syntax `[Cmdlet(verb, noun, ...)]`, vor der Klassendefinition verwendet wird, um diese Klasse als Cmdlet zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="f46d7-122">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="f46d7-123">Dies ist das einzige erforderliche Attribut für alle Cmdlets und ermöglicht es der Windows PowerShell-Laufzeit, Sie ordnungsgemäß aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="f46d7-123">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="f46d7-124">Sie können Attribut Schlüsselwörter festlegen, um die Klasse bei Bedarf weiter zu deklarieren.</span><span class="sxs-lookup"><span data-stu-id="f46d7-124">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="f46d7-125">Beachten Sie, dass die Attribut Deklaration für die getproccommand-Beispiel Klasse nur die Substantiv-und Verb Namen für das Get-proc-Cmdlet deklariert.</span><span class="sxs-lookup"><span data-stu-id="f46d7-125">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="f46d7-126">Für alle Windows PowerShell-Attribut Klassen entsprechen die Schlüsselwörter, die Sie festlegen können, den Eigenschaften der Attribut Klasse.</span><span class="sxs-lookup"><span data-stu-id="f46d7-126">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="f46d7-127">Wenn Sie die Klasse des Cmdlets benennen, empfiehlt es sich, den Cmdlet-Namen im Klassennamen widerzuspiegeln.</span><span class="sxs-lookup"><span data-stu-id="f46d7-127">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="f46d7-128">Verwenden Sie hierzu das Format "verbnouncommand", und ersetzen Sie "Verb" und "Substantiv" durch das Verb und das Substantiv, das im Cmdlet-Namen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f46d7-128">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="f46d7-129">Wie in der vorherigen Klassendefinition gezeigt, definiert das Get-proc-Beispiel Cmdlet eine Klasse mit dem Namen "getproccommand", die von der Basisklasse " [System. Management. Automation. Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) " abgeleitet ist.</span><span class="sxs-lookup"><span data-stu-id="f46d7-129">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f46d7-130">Wenn Sie ein Cmdlet definieren möchten, das direkt auf die Windows PowerShell-Laufzeit zugreift, sollte Ihre .NET-Klasse von der Basisklasse " [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) " abgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="f46d7-130">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="f46d7-131">Weitere Informationen zu dieser Klasse finden Sie unter [Erstellen eines Cmdlets zum Definieren von Parameter Sätzen](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="f46d7-131">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f46d7-132">Die-Klasse für ein Cmdlet muss explizit als public gekennzeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="f46d7-132">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="f46d7-133">Klassen, die nicht als public gekennzeichnet sind, werden standardmäßig intern verwendet und werden von der Windows PowerShell-Laufzeit nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="f46d7-133">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="f46d7-134">Windows PowerShell verwendet den [Microsoft. PowerShell. Commands](/dotnet/api/Microsoft.PowerShell.Commands) -Namespace für die Cmdlet-Klassen.</span><span class="sxs-lookup"><span data-stu-id="f46d7-134">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="f46d7-135">Es wird empfohlen, die Cmdlet-Klassen in einem Befehle-Namespace ihres API-Namespace zu platzieren, z. b. xxx. PS. Commands.</span><span class="sxs-lookup"><span data-stu-id="f46d7-135">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="f46d7-136">Überschreiben einer Eingabe Verarbeitungsmethode</span><span class="sxs-lookup"><span data-stu-id="f46d7-136">Overriding an Input Processing Method</span></span>

<span data-ttu-id="f46d7-137">Die [System. Management. Automation. Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) -Klasse stellt drei Haupt Eingabe-Verarbeitungsmethoden bereit, von denen das Cmdlet überschrieben werden muss.</span><span class="sxs-lookup"><span data-stu-id="f46d7-137">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="f46d7-138">Weitere Informationen zur Verarbeitung von Datensätzen in Windows PowerShell finden Sie unter [Funktionsweise von Windows PowerShell](/previous-versions//ms714658(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="f46d7-138">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

<span data-ttu-id="f46d7-139">Für alle Typen von Eingaben Ruft die Windows PowerShell-Runtime [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) auf, um die Verarbeitung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="f46d7-139">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="f46d7-140">Wenn das Cmdlet einige Vorverarbeitungs-oder Setup Vorgänge ausführen muss, kann dies durch Überschreiben dieser Methode durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="f46d7-140">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="f46d7-141">Windows PowerShell verwendet den Begriff "Datensatz", um den Satz von Parameterwerten zu beschreiben, die beim Aufrufen eines Cmdlets bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="f46d7-141">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="f46d7-142">Wenn das Cmdlet Pipeline Eingaben annimmt, muss es die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode und optional die [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methode überschreiben.</span><span class="sxs-lookup"><span data-stu-id="f46d7-142">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="f46d7-143">Ein Cmdlet kann z. b. beide Methoden überschreiben, wenn es die gesamte Eingabe mithilfe von [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) sammelt und dann die Eingabe als Ganzes anstelle eines Elements, wie das `Sort-Object`-Cmdlet, verhält.</span><span class="sxs-lookup"><span data-stu-id="f46d7-143">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="f46d7-144">Wenn das Cmdlet keine Pipeline Eingaben annimmt, sollte es die [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methode überschreiben.</span><span class="sxs-lookup"><span data-stu-id="f46d7-144">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="f46d7-145">Beachten Sie, dass diese Methode häufig anstelle von [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) verwendet wird, wenn das Cmdlet nicht gleichzeitig auf einem Element agieren kann, wie es bei einem Sortierungs-Cmdlet der Fall ist.</span><span class="sxs-lookup"><span data-stu-id="f46d7-145">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="f46d7-146">Da dieses Beispiel-Cmdlet "Get-proc" eine Pipeline Eingabe empfangen muss, überschreibt es die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode und verwendet die Standard Implementierungen für " [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) " und " [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)".</span><span class="sxs-lookup"><span data-stu-id="f46d7-146">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="f46d7-147">Die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Überschreibung ruft Prozesse ab und schreibt Sie mithilfe der [System. Management. Automation. Cmdlet. Write-Object](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) -Methode in die Befehlszeile.</span><span class="sxs-lookup"><span data-stu-id="f46d7-147">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

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

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="f46d7-148">Dinge, die bei der Eingabe Verarbeitung beachtet werden sollten</span><span class="sxs-lookup"><span data-stu-id="f46d7-148">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="f46d7-149">Die Standard Quelle für die Eingabe ist ein explizites Objekt (z. b. eine Zeichenfolge), das vom Benutzer in der Befehlszeile bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="f46d7-149">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="f46d7-150">Weitere Informationen finden Sie unter [Erstellen eines Cmdlets zum Verarbeiten von Befehlszeilen Eingaben](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="f46d7-150">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="f46d7-151">Eine Eingabe Verarbeitungsmethode kann auch Eingaben vom Ausgabe Objekt eines upstreamcmdlets in der Pipeline empfangen.</span><span class="sxs-lookup"><span data-stu-id="f46d7-151">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="f46d7-152">Weitere Informationen finden Sie unter [Erstellen eines Cmdlets für die Verarbeitung von Pipeline Eingaben](./adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="f46d7-152">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="f46d7-153">Beachten Sie, dass das Cmdlet Eingaben von einer Kombination von Befehlszeilen-und Pipeline Quellen empfangen kann.</span><span class="sxs-lookup"><span data-stu-id="f46d7-153">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="f46d7-154">Das downstreamcmdlet gibt möglicherweise für längere Zeit oder gar nicht zurück.</span><span class="sxs-lookup"><span data-stu-id="f46d7-154">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="f46d7-155">Aus diesem Grund sollte die Eingabe Verarbeitungsmethode in Ihrem Cmdlet keine Sperren bei Aufrufen von [System. Management. Automation. Cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)enthalten, insbesondere sperren, für die der Bereich die Cmdlet-Instanz überschreitet.</span><span class="sxs-lookup"><span data-stu-id="f46d7-155">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f46d7-156">Cmdlets sollten niemals [System. Console. Write teline \*](/dotnet/api/System.Console.WriteLine) oder die entsprechende-Entsprechung aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="f46d7-156">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="f46d7-157">Wenn die Verarbeitung abgeschlossen ist, kann das Cmdlet Objektvariablen zum Bereinigen aufweisen (z. b., wenn ein Datei Handle in der [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -Methode geöffnet wird und das Handle für die Verwendung durch [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)geöffnet bleibt).</span><span class="sxs-lookup"><span data-stu-id="f46d7-157">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="f46d7-158">Beachten Sie, dass die Windows PowerShell-Laufzeit nicht immer die [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methode aufruft, die die Objekt Bereinigung durchführen soll.</span><span class="sxs-lookup"><span data-stu-id="f46d7-158">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="f46d7-159">Beispielsweise kann " [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) " nicht aufgerufen werden, wenn das Cmdlet in der Mitte abgebrochen wird oder wenn in einem beliebigen Teil des Cmdlets ein Abbruch Fehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="f46d7-159">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="f46d7-160">Daher sollte ein Cmdlet, das die Objekt Bereinigung erfordert, das komplette [System. iverwerf-](/dotnet/api/System.IDisposable) Muster implementieren, einschließlich des Finalizers, damit die Laufzeit sowohl [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) als auch [System. iverwerf. verwerfen \*](/dotnet/api/System.IDisposable.Dispose) am Ende der Verarbeitung abrufen kann.</span><span class="sxs-lookup"><span data-stu-id="f46d7-160">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f46d7-161">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="f46d7-161">Code Sample</span></span>

<span data-ttu-id="f46d7-162">Den gesamten C# Beispielcode finden Sie unter [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="f46d7-162">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="f46d7-163">Definieren von Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="f46d7-163">Defining Object Types and Formatting</span></span>

<span data-ttu-id="f46d7-164">Windows PowerShell übergibt Informationen zwischen Cmdlets mithilfe von .NET-Objekten.</span><span class="sxs-lookup"><span data-stu-id="f46d7-164">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="f46d7-165">Folglich muss ein Cmdlet möglicherweise seinen eigenen Typ definieren, oder das Cmdlet muss möglicherweise einen vorhandenen Typ erweitern, der von einem anderen Cmdlet bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="f46d7-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="f46d7-166">Weitere Informationen zum Definieren neuer Typen oder zum Erweitern vorhandener Typen finden Sie unter [Erweitern von Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="f46d7-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="f46d7-167">Cmdlet wird aufgebaut</span><span class="sxs-lookup"><span data-stu-id="f46d7-167">Building the Cmdlet</span></span>

<span data-ttu-id="f46d7-168">Nachdem Sie ein Cmdlet implementiert haben, müssen Sie es über ein Windows PowerShell-Snap-in bei Windows PowerShell registrieren.</span><span class="sxs-lookup"><span data-stu-id="f46d7-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="f46d7-169">Weitere Informationen zum Registrieren von Cmdlets finden [Sie unter Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="f46d7-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="f46d7-170">Testen des Cmdlets</span><span class="sxs-lookup"><span data-stu-id="f46d7-170">Testing the Cmdlet</span></span>

<span data-ttu-id="f46d7-171">Wenn das Cmdlet bei Windows PowerShell registriert wurde, können Sie es in der Befehlszeile testen.</span><span class="sxs-lookup"><span data-stu-id="f46d7-171">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="f46d7-172">Der Code für das Beispiel-Cmdlet "Get-proc" ist klein, verwendet jedoch weiterhin die Windows PowerShell-Laufzeit und ein vorhandenes .NET-Objekt, das ausreichend ist, um es zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="f46d7-172">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="f46d7-173">Testen Sie es, um besser zu verstehen, was Get-proc tun kann und wie seine Ausgabe verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="f46d7-173">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="f46d7-174">Weitere Informationen zur Verwendung von Cmdlets über die Befehlszeile finden Sie unter [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="f46d7-174">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="f46d7-175">Starten Sie Windows PowerShell, und holen Sie sich die aktuellen Prozesse, die auf dem Computer ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="f46d7-175">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="f46d7-176">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f46d7-176">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="f46d7-177">Weisen Sie den Cmdlet-Ergebnissen eine Variable zu, um die Bearbeitung zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="f46d7-177">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="f46d7-178">Gibt die Anzahl der Prozesse an.</span><span class="sxs-lookup"><span data-stu-id="f46d7-178">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="f46d7-179">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f46d7-179">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="f46d7-180">Ruft einen bestimmten Prozess ab.</span><span class="sxs-lookup"><span data-stu-id="f46d7-180">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="f46d7-181">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f46d7-181">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="f46d7-182">Hiermit wird die Startzeit dieses Prozesses angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f46d7-182">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="f46d7-183">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f46d7-183">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="f46d7-184">Holen Sie die Prozesse, für die die Anzahl der Handles größer als 500 ist, und sortieren Sie das Ergebnis.</span><span class="sxs-lookup"><span data-stu-id="f46d7-184">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="f46d7-185">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f46d7-185">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="f46d7-186">Verwenden Sie das Cmdlet "`Get-Member`", um die für die einzelnen Prozesse verfügbaren Eigenschaften aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="f46d7-186">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="f46d7-187">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f46d7-187">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="f46d7-188">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f46d7-188">See Also</span></span>

[<span data-ttu-id="f46d7-189">Erstellen eines Cmdlets zur Verarbeitung der Befehlszeilen Eingabe</span><span class="sxs-lookup"><span data-stu-id="f46d7-189">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="f46d7-190">Erstellen eines Cmdlets zum Verarbeiten von Pipeline Eingaben</span><span class="sxs-lookup"><span data-stu-id="f46d7-190">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="f46d7-191">Erstellen eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="f46d7-191">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="f46d7-192">[Erweitern von Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="f46d7-192">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="f46d7-193">[Funktionsweise von Windows PowerShell](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="f46d7-193">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="f46d7-194">[Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="f46d7-194">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="f46d7-195">Windows PowerShell-Referenz</span><span class="sxs-lookup"><span data-stu-id="f46d7-195">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="f46d7-196">Cmdlet-Beispiele</span><span class="sxs-lookup"><span data-stu-id="f46d7-196">Cmdlet Samples</span></span>](./cmdlet-samples.md)
