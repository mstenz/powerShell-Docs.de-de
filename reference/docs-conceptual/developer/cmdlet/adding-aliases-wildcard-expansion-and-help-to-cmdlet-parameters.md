---
title: Hinzufügen von Aliasen, Platzhalter Erweiterungen und Hilfe zu Cmdlet-Parametern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: d210a852a90d94df2ab360dd86f0b83a396330e3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74415659"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="1f2db-102">Hinzufügen von Aliasen, Platzhaltererweiterung und Hilfe zu Cmdlet-Parametern</span><span class="sxs-lookup"><span data-stu-id="1f2db-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="1f2db-103">In diesem Abschnitt wird beschrieben, wie Aliase, Platzhalter Erweiterung und Hilfe Meldungen den Parametern des Cmdlets "-Beendigung-proc" hinzugefügt werden (siehe [Erstellen eines Cmdlets, das das System ändert](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="1f2db-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="1f2db-104">Dieses Cmdlet "Pause-proc" versucht, Prozesse zu unterbinden, die mithilfe des Cmdlets "Get-proc" abgerufen werden (siehe [Erstellen des ersten Cmdlets](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="1f2db-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="1f2db-105">Definieren des Cmdlets</span><span class="sxs-lookup"><span data-stu-id="1f2db-105">Defining the Cmdlet</span></span>

<span data-ttu-id="1f2db-106">Der erste Schritt bei der Cmdlet-Erstellung ist die Benennung des Cmdlets und das Deklarieren der .NET-Klasse, die das Cmdlet implementiert.</span><span class="sxs-lookup"><span data-stu-id="1f2db-106">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="1f2db-107">Da Sie ein Cmdlet schreiben, um das System zu ändern, sollte es entsprechend benannt werden.</span><span class="sxs-lookup"><span data-stu-id="1f2db-107">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="1f2db-108">Da dieses Cmdlet System Prozesse stoppt, wird das Verb "Stopp", das von der [System. Management. Automation. verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) -Klasse definiert wird, mit dem Substantiv "proc" verwendet, um den Prozess anzugeben.</span><span class="sxs-lookup"><span data-stu-id="1f2db-108">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="1f2db-109">Weitere Informationen zu genehmigten Cmdlet-Verben finden Sie unter [Cmdlet-Verb Namen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="1f2db-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="1f2db-110">Der folgende Code stellt die Klassendefinition für dieses Cmdlet "Pause-proc" dar.</span><span class="sxs-lookup"><span data-stu-id="1f2db-110">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="1f2db-111">Definieren von Parametern für die System Änderung</span><span class="sxs-lookup"><span data-stu-id="1f2db-111">Defining Parameters for System Modification</span></span>

<span data-ttu-id="1f2db-112">Ihr Cmdlet muss Parameter definieren, die Systemänderungen und Benutzer Feedback unterstützen.</span><span class="sxs-lookup"><span data-stu-id="1f2db-112">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="1f2db-113">Mit dem-Cmdlet sollte ein `Name` Parameter oder eine entsprechende-Entsprechung definiert werden, damit das Cmdlet das System durch eine bestimmte Art von Bezeichner ändern kann.</span><span class="sxs-lookup"><span data-stu-id="1f2db-113">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="1f2db-114">Außerdem sollte das Cmdlet die `Force`-und `PassThru` Parameter definieren.</span><span class="sxs-lookup"><span data-stu-id="1f2db-114">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="1f2db-115">Weitere Informationen zu diesen Parametern finden Sie unter [Erstellen eines Cmdlets, das das System ändert](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="1f2db-115">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="1f2db-116">Definieren eines parameteralias</span><span class="sxs-lookup"><span data-stu-id="1f2db-116">Defining a Parameter Alias</span></span>

<span data-ttu-id="1f2db-117">Ein parameteralias kann ein alternativer Name oder ein gut definierter Kurzname mit einem oder zwei Buchstaben für einen Cmdlet-Parameter sein.</span><span class="sxs-lookup"><span data-stu-id="1f2db-117">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="1f2db-118">In beiden Fällen besteht das Ziel der Verwendung von Aliasen darin, den Benutzereintrag von der Befehlszeile aus zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="1f2db-118">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="1f2db-119">Windows PowerShell unterstützt Parameter Aliase über das [System. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) -Attribut, das die Deklarations Syntax [Alias ()] verwendet.</span><span class="sxs-lookup"><span data-stu-id="1f2db-119">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="1f2db-120">Der folgende Code zeigt, wie dem `Name`-Parameter ein Alias hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="1f2db-120">The following code shows how an alias is added to the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

<span data-ttu-id="1f2db-121">Zusätzlich zur Verwendung des [System. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) -Attributs führt die Windows PowerShell-Laufzeit eine partielle namens Übereinstimmung aus, auch wenn keine Aliase angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="1f2db-121">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="1f2db-122">Wenn das Cmdlet z. b. über einen `FileName`-Parameter verfügt und der einzige Parameter ist, der mit `F`beginnt, kann der Benutzer `Filename`, `Filenam`, `File`, `Fi`oder `F` eingeben und den Eintrag weiterhin als `FileName` Parameter erkennen.</span><span class="sxs-lookup"><span data-stu-id="1f2db-122">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="1f2db-123">Erstellen von Hilfe für Parameter</span><span class="sxs-lookup"><span data-stu-id="1f2db-123">Creating Help for Parameters</span></span>

<span data-ttu-id="1f2db-124">Mit Windows PowerShell können Sie Hilfe für Cmdlet-Parameter erstellen.</span><span class="sxs-lookup"><span data-stu-id="1f2db-124">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="1f2db-125">Verwenden Sie dies für alle Parameter, die für die Systemänderung und das Benutzer Feedback verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1f2db-125">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="1f2db-126">Für jeden Parameter zur Unterstützung der Hilfe können Sie das `HelpMessage` Attribute-Schlüsselwort in der [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Attribut Deklaration festlegen.</span><span class="sxs-lookup"><span data-stu-id="1f2db-126">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="1f2db-127">Dieses Schlüsselwort definiert den Text, der dem Benutzer zur Unterstützung bei der Verwendung des-Parameters angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="1f2db-127">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="1f2db-128">Sie können auch das `HelpMessageBaseName`-Schlüsselwort festlegen, um den Basis Namen einer Ressource zu identifizieren, die für die Nachricht verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="1f2db-128">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="1f2db-129">Wenn Sie dieses Schlüsselwort festlegen, müssen Sie auch das `HelpMessageResourceId`-Schlüsselwort festlegen, um den Ressourcen Bezeichner anzugeben.</span><span class="sxs-lookup"><span data-stu-id="1f2db-129">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="1f2db-130">Der folgende Code aus diesem Cmdlet "halte-proc" definiert das `HelpMessage` attributsschlüsselwort für den Parameter "`Name`".</span><span class="sxs-lookup"><span data-stu-id="1f2db-130">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="1f2db-131">Überschreiben einer Eingabe Verarbeitungsmethode</span><span class="sxs-lookup"><span data-stu-id="1f2db-131">Overriding an Input Processing Method</span></span>

<span data-ttu-id="1f2db-132">Ihr Cmdlet muss eine Eingabe Verarbeitungsmethode überschreiben, meistens handelt es sich hierbei um [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="1f2db-132">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="1f2db-133">Wenn Sie das System ändern, sollte das Cmdlet die Methoden " [System. Management. Automation. Cmdlet. schuldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) " und " [System. Management. Automation. Cmdlet.-dcontinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) " anrufen, damit der Benutzer Feedback bereitstellen kann, bevor eine Änderung vorgenommen wird.</span><span class="sxs-lookup"><span data-stu-id="1f2db-133">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="1f2db-134">Weitere Informationen zu diesen Methoden finden Sie unter [Erstellen eines Cmdlets, das das System ändert](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="1f2db-134">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="1f2db-135">Unterstützung für Platzhalter</span><span class="sxs-lookup"><span data-stu-id="1f2db-135">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="1f2db-136">Um die Auswahl mehrerer Objekte zu ermöglichen, kann das Cmdlet die Klassen " [System. Management. Automation. wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) " und " [System. Management. Automation. wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) " verwenden, um die Unterstützung für Platzhalter Erweiterungen für Parameter Eingaben bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="1f2db-136">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="1f2db-137">Beispiele für Platzhalter Muster sind LSA \*, \*. txt und [a-c]\*.</span><span class="sxs-lookup"><span data-stu-id="1f2db-137">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="1f2db-138">Verwenden Sie das backanführungs Zeichen (') als Escapezeichen, wenn das Muster ein Zeichen enthält, das buchstäblich verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="1f2db-138">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="1f2db-139">Platzhalter Erweiterungen von Datei-und Pfadnamen sind Beispiele für gängige Szenarien, in denen das Cmdlet möglicherweise die Unterstützung von Pfad Eingaben zulässt, wenn die Auswahl mehrerer Objekte erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="1f2db-139">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="1f2db-140">Häufig wird das Dateisystem angezeigt, in dem ein Benutzer alle Dateien im aktuellen Ordner anzeigen möchte.</span><span class="sxs-lookup"><span data-stu-id="1f2db-140">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="1f2db-141">Sie sollten eine angepasste Platzhalter Muster Vergleichs Implementierung nur selten benötigen.</span><span class="sxs-lookup"><span data-stu-id="1f2db-141">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="1f2db-142">In diesem Fall sollte Ihr Cmdlet entweder die vollständige POSIX 1003,2-und 3,13-Spezifikation für die Platzhalter Erweiterung oder die folgende vereinfachte Teilmenge unterstützen:</span><span class="sxs-lookup"><span data-stu-id="1f2db-142">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="1f2db-143">**Fragezeichen (?).**</span><span class="sxs-lookup"><span data-stu-id="1f2db-143">**Question mark (?).**</span></span> <span data-ttu-id="1f2db-144">Entspricht einem beliebigen Zeichen an der angegebenen Position.</span><span class="sxs-lookup"><span data-stu-id="1f2db-144">Matches any character at the specified location.</span></span>

- <span data-ttu-id="1f2db-145">**Sternchen (\*).**</span><span class="sxs-lookup"><span data-stu-id="1f2db-145">**Asterisk (\*).**</span></span> <span data-ttu-id="1f2db-146">Entspricht 0 (null) oder mehr Zeichen, beginnend an der angegebenen Position.</span><span class="sxs-lookup"><span data-stu-id="1f2db-146">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="1f2db-147">**Öffnende eckige Klammer ([).**</span><span class="sxs-lookup"><span data-stu-id="1f2db-147">**Open bracket ([).**</span></span> <span data-ttu-id="1f2db-148">Führt einen Muster Klammer Ausdruck ein, der Zeichen oder einen Zeichenbereich enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="1f2db-148">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="1f2db-149">Wenn ein Bereich erforderlich ist, wird ein Bindestrich (-) verwendet, um den Bereich anzugeben.</span><span class="sxs-lookup"><span data-stu-id="1f2db-149">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="1f2db-150">**Schließende Klammer (]).**</span><span class="sxs-lookup"><span data-stu-id="1f2db-150">**Close bracket (]).**</span></span> <span data-ttu-id="1f2db-151">Beendet einen Muster Klammer Ausdruck.</span><span class="sxs-lookup"><span data-stu-id="1f2db-151">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="1f2db-152">**Escape-Escapezeichen (').**</span><span class="sxs-lookup"><span data-stu-id="1f2db-152">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="1f2db-153">Gibt an, dass das nächste Zeichen wörtlich genommen werden soll.</span><span class="sxs-lookup"><span data-stu-id="1f2db-153">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="1f2db-154">Beachten Sie, dass bei der Angabe des backanführungs Zeichens von der Befehlszeile aus (im Gegensatz zur programmgesteuerten Angabe) das Escapezeichen für das Back-End zweimal angegeben werden muss.</span><span class="sxs-lookup"><span data-stu-id="1f2db-154">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="1f2db-155">Weitere Informationen zu Platzhalter Mustern finden Sie [unter unterstützen von Platzhaltern in Cmdlet-Parametern](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="1f2db-155">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="1f2db-156">Der folgende Code zeigt, wie Sie Platzhalter Optionen festlegen und das Platzhalter Muster definieren, das zum Auflösen des `Name`-Parameters für dieses Cmdlet verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="1f2db-156">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="1f2db-157">Der folgende Code zeigt, wie Sie überprüfen, ob der Prozess Name mit dem definierten Platzhalter Muster übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="1f2db-157">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="1f2db-158">Beachten Sie, dass in diesem Fall, wenn der Prozess Name nicht mit dem Muster identisch ist, das Cmdlet fortgesetzt wird, um den nächsten Prozessnamen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="1f2db-158">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="1f2db-159">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="1f2db-159">Code Sample</span></span>

<span data-ttu-id="1f2db-160">Den gesamten C# Beispielcode finden Sie unter [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="1f2db-160">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="1f2db-161">Definieren von Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="1f2db-161">Define Object Types and Formatting</span></span>

<span data-ttu-id="1f2db-162">Windows PowerShell übergibt Informationen zwischen Cmdlets mithilfe von .NET-Objekten.</span><span class="sxs-lookup"><span data-stu-id="1f2db-162">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="1f2db-163">Folglich muss ein Cmdlet möglicherweise seinen eigenen Typ definieren, oder das Cmdlet muss möglicherweise einen vorhandenen Typ erweitern, der von einem anderen Cmdlet bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="1f2db-163">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="1f2db-164">Weitere Informationen zum Definieren neuer Typen oder zum Erweitern vorhandener Typen finden Sie unter [Erweitern von Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="1f2db-164">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="1f2db-165">Cmdlet wird aufgebaut</span><span class="sxs-lookup"><span data-stu-id="1f2db-165">Building the Cmdlet</span></span>

<span data-ttu-id="1f2db-166">Nachdem ein Cmdlet implementiert wurde, muss es über ein Windows PowerShell-Snap-in in Windows PowerShell registriert werden.</span><span class="sxs-lookup"><span data-stu-id="1f2db-166">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="1f2db-167">Weitere Informationen zum Registrieren von Cmdlets finden [Sie unter Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="1f2db-167">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="1f2db-168">Testen des Cmdlets</span><span class="sxs-lookup"><span data-stu-id="1f2db-168">Testing the Cmdlet</span></span>

<span data-ttu-id="1f2db-169">Wenn das Cmdlet bei Windows PowerShell registriert wurde, können Sie es in der Befehlszeile testen.</span><span class="sxs-lookup"><span data-stu-id="1f2db-169">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="1f2db-170">Testen Sie das Beispiel-Cmdlet "Stopp-proc".</span><span class="sxs-lookup"><span data-stu-id="1f2db-170">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="1f2db-171">Weitere Informationen zur Verwendung von Cmdlets über die Befehlszeile finden Sie unter [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="1f2db-171">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="1f2db-172">Starten Sie Windows PowerShell, und verwenden Sie "Break-proc", um einen Prozess mit dem ProcessName-Alias für den `Name`-Parameter zu starten.</span><span class="sxs-lookup"><span data-stu-id="1f2db-172">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="1f2db-173">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1f2db-173">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="1f2db-174">Legen Sie den folgenden Eintrag in der Befehlszeile ab.</span><span class="sxs-lookup"><span data-stu-id="1f2db-174">Make the following entry on the command line.</span></span> <span data-ttu-id="1f2db-175">Da der Name-Parameter obligatorisch ist, werden Sie dazu aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="1f2db-175">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="1f2db-176">Eingabe von "!?"</span><span class="sxs-lookup"><span data-stu-id="1f2db-176">Entering "!?"</span></span> <span data-ttu-id="1f2db-177">Ruft den Hilfetext auf, der dem-Parameter zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="1f2db-177">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="1f2db-178">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1f2db-178">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="1f2db-179">Führen Sie nun den folgenden Eintrag aus, um alle Prozesse anzuhalten, die dem Platzhalter Muster "\* Note\*" entsprechen.</span><span class="sxs-lookup"><span data-stu-id="1f2db-179">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="1f2db-180">Sie werden dazu aufgefordert, jeden Prozess anzuhalten, der mit dem Muster übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="1f2db-180">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="1f2db-181">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1f2db-181">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="1f2db-182">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1f2db-182">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="1f2db-183">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1f2db-183">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="1f2db-184">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1f2db-184">See Also</span></span>

[<span data-ttu-id="1f2db-185">Erstellen Sie ein Cmdlet, das das System ändert.</span><span class="sxs-lookup"><span data-stu-id="1f2db-185">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="1f2db-186">Erstellen eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="1f2db-186">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="1f2db-187">[Erweitern von Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="1f2db-187">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="1f2db-188">[Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="1f2db-188">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="1f2db-189">Unterstützen von Platzhaltern in Cmdlet-Parametern</span><span class="sxs-lookup"><span data-stu-id="1f2db-189">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="1f2db-190">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1f2db-190">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
