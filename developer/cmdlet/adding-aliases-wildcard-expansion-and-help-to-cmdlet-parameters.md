---
title: Hinzufügen von Platzhaltererweiterung, Aliase und Cmdlet-Parameter sollte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: 0f025213087e6f308adf8e597fc01c1320251f76
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859326"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="3a08b-102">Hinzufügen von Aliasen, Platzhaltererweiterung und Hilfe zu Cmdlet-Parametern</span><span class="sxs-lookup"><span data-stu-id="3a08b-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="3a08b-103">In diesem Abschnitt wird beschrieben, wie Aliase, platzhaltererweiterung, hinzufügen und Hilfe von Nachrichten an die Parameter des Cmdlets Stop-Prozessor (beschrieben [ein Cmdlets zu erstellen, ändert das System](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="3a08b-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="3a08b-104">Dieses Cmdlet Stop-Prozessor versucht, Sie Prozesse beenden, die mit dem Get-Proc-Cmdlet abgerufen werden (beschrieben [Erstellen Ihrer ersten Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="3a08b-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="3a08b-105">Die folgenden: Themen in diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="3a08b-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="3a08b-106">Definieren das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3a08b-106">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="3a08b-107">Definieren von Parametern für die System-Änderung</span><span class="sxs-lookup"><span data-stu-id="3a08b-107">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="3a08b-108">Definieren einen Parameteralias</span><span class="sxs-lookup"><span data-stu-id="3a08b-108">Defining a Parameter Alias</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="3a08b-109">Hilfe für Parameter erstellen</span><span class="sxs-lookup"><span data-stu-id="3a08b-109">Creating Help for Parameters</span></span>](#Creating-Help-for-Parameters)

- [<span data-ttu-id="3a08b-110">Überschreiben einer Eingabeverarbeitungsmethode</span><span class="sxs-lookup"><span data-stu-id="3a08b-110">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="3a08b-111">Unterstützung von Platzhaltererweiterung</span><span class="sxs-lookup"><span data-stu-id="3a08b-111">Supporting Wildcard Expansion</span></span>](#Supporting-Wildcard-Expansion)

- [<span data-ttu-id="3a08b-112">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="3a08b-112">Code Sample</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="3a08b-113">Definieren von Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="3a08b-113">Defining Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="3a08b-114">Erstellen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3a08b-114">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="3a08b-115">Testen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3a08b-115">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="3a08b-116">Definieren das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3a08b-116">Defining the Cmdlet</span></span>

<span data-ttu-id="3a08b-117">Der erste Schritt bei der Cmdlet-Erstellung ist immer benennen das Cmdlet und .NET implementiert die Klasse, mit dem-Cmdlet deklarieren.</span><span class="sxs-lookup"><span data-stu-id="3a08b-117">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="3a08b-118">Da Sie ein Cmdlet aus, um das System ändern, schreiben, sollten sie entsprechend benannt werden.</span><span class="sxs-lookup"><span data-stu-id="3a08b-118">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="3a08b-119">Da dieses Cmdlet Systemprozesse beendet wird, verwendet es das Verb "Stop", definiert durch die [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) Klasse, mit dem Namen "Proc" an Prozess.</span><span class="sxs-lookup"><span data-stu-id="3a08b-119">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="3a08b-120">Weitere Informationen zu zulässigen Cmdlet-Verben, finden Sie unter [Cmdlet Verbnamen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="3a08b-120">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="3a08b-121">Der folgende Code ist die Definition der Klasse für dieses Cmdlet Stop-Prozessor.</span><span class="sxs-lookup"><span data-stu-id="3a08b-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="3a08b-122">Definieren von Parametern für die System-Änderung</span><span class="sxs-lookup"><span data-stu-id="3a08b-122">Defining Parameters for System Modification</span></span>

<span data-ttu-id="3a08b-123">Ihr Cmdlet muss Parameter, die Unterstützung von Änderungen und Feedback von Benutzern zu definieren.</span><span class="sxs-lookup"><span data-stu-id="3a08b-123">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="3a08b-124">Sollte das Cmdlet definieren eine `Name` Parameter oder einer entsprechenden Gruppe, damit das Cmdlet das System von einer bestimmten Art des Bezeichners ändern kann.</span><span class="sxs-lookup"><span data-stu-id="3a08b-124">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="3a08b-125">Darüber hinaus sollte das Cmdlet definieren die `Force` und `PassThru` Parameter.</span><span class="sxs-lookup"><span data-stu-id="3a08b-125">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="3a08b-126">Weitere Informationen zu diesen Parametern finden Sie unter [ein Cmdlets zu erstellen, ändert das System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="3a08b-126">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="3a08b-127">Definieren einen Parameteralias</span><span class="sxs-lookup"><span data-stu-id="3a08b-127">Defining a Parameter Alias</span></span>

<span data-ttu-id="3a08b-128">Ein parameteralias kann es sich um einen alternativen Namen oder einen klar definierten Buchstaben 1 oder 2 Buchstaben Kurznamen für ein Cmdlet-Parameter sein.</span><span class="sxs-lookup"><span data-stu-id="3a08b-128">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="3a08b-129">Das Ziel der using-Aliase werden in beiden Fällen Eintrag des Benutzers über die Befehlszeile zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="3a08b-129">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="3a08b-130">Windows PowerShell unterstützt parameteraliase über die [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) -Attribut, das die Syntax zum Deklarieren [Alias()] verwendet.</span><span class="sxs-lookup"><span data-stu-id="3a08b-130">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="3a08b-131">Der folgende Code zeigt, wie ein Alias hinzugefügt wird die `Name` Parameter.</span><span class="sxs-lookup"><span data-stu-id="3a08b-131">The following code shows how an alias is added to the `Name` parameter.</span></span>

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

<span data-ttu-id="3a08b-132">Zusätzlich zur Verwendung der [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) -Attribut, die Windows PowerShell-Laufzeit führt teilweise namensübereinstimmung, auch wenn keine Aliase angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="3a08b-132">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="3a08b-133">Wenn Ihr Cmdlet hat beispielsweise eine `FileName` Parameter und d. h. der einzige Parameter, die mit beginnt `F`, der Benutzer eingeben kann `Filename`, `Filenam`, `File`, `Fi`, oder `F` und erkennen Sie immer noch die Je nach den `FileName` Parameter.</span><span class="sxs-lookup"><span data-stu-id="3a08b-133">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="3a08b-134">Hilfe für Parameter erstellen</span><span class="sxs-lookup"><span data-stu-id="3a08b-134">Creating Help for Parameters</span></span>

<span data-ttu-id="3a08b-135">Windows PowerShell können Sie Hilfe für Cmdlet-Parameter zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3a08b-135">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="3a08b-136">Hierzu für jeden Parameter, die für die Änderung und der Benutzer Feedback zum plattformbenachrichtigungssystem verwendet.</span><span class="sxs-lookup"><span data-stu-id="3a08b-136">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="3a08b-137">Für jeden Parameter, um Hilfe zu unterstützen, können Sie festlegen der `HelpMessage` Attribut-Schlüsselwort in der [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Attributdeklaration.</span><span class="sxs-lookup"><span data-stu-id="3a08b-137">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="3a08b-138">Dieses Schlüsselwort definiert, den Text, der den Benutzer zur Unterstützung bei der mit dem Parameter angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3a08b-138">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="3a08b-139">Sie können auch Festlegen der `HelpMessageBaseName` Schlüsselwort zum Identifizieren der Basisname der Ressource, für die Nachricht verwendet.</span><span class="sxs-lookup"><span data-stu-id="3a08b-139">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="3a08b-140">Wenn Sie dieses Schlüsselwort festlegen, müssen Sie auch Festlegen der `HelpMessageResourceId` Schlüsselwort, um die Ressourcen-ID angeben.</span><span class="sxs-lookup"><span data-stu-id="3a08b-140">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="3a08b-141">Der folgende Code aus diesem Stop-Proc-Cmdlet definiert die `HelpMessage` Attribut-Schlüsselwort für die `Name` Parameter.</span><span class="sxs-lookup"><span data-stu-id="3a08b-141">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="3a08b-142">Überschreiben einer Eingabeverarbeitungsmethode</span><span class="sxs-lookup"><span data-stu-id="3a08b-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="3a08b-143">Ihr Cmdlet ein eingabeverarbeitungsmethode muss überschrieben werden, am häufigsten [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="3a08b-143">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="3a08b-144">Wenn Sie das System ändern zu können, sollte das-Cmdlet Aufrufen der [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) und [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methoden, um die Benutzer, Feedback zu geben, bevor eine Änderung vorgenommen wird.</span><span class="sxs-lookup"><span data-stu-id="3a08b-144">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="3a08b-145">Weitere Informationen zu diesen Methoden finden Sie unter [ein Cmdlets zu erstellen, ändert das System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="3a08b-145">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="3a08b-146">Unterstützung von Platzhaltererweiterung</span><span class="sxs-lookup"><span data-stu-id="3a08b-146">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="3a08b-147">Um die Auswahl mehrerer Objekte zu ermöglichen, Ihr Cmdlet verwenden, kann die [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) und [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) Klassen das Bereitstellen Unterstützung von Platzhalterzeichen-Erweiterung für den Parameter eingeben.</span><span class="sxs-lookup"><span data-stu-id="3a08b-147">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="3a08b-148">Beispiele für Platzhaltermuster sind Lsa \* \*txt- und [a-c]\*.</span><span class="sxs-lookup"><span data-stu-id="3a08b-148">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="3a08b-149">Verwenden Sie das invertierte Hochkomma (') als Escapezeichen verwendet werden, wenn das Muster, ein Zeichen enthält, die buchstäblich verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="3a08b-149">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="3a08b-150">Platzhalter-Erweiterungen von Datei-und Pfadnamen sind Beispiele für häufige Szenarien, in dem das Cmdlet sollten, um Unterstützung für Pfad Eingaben zu ermöglichen, wenn die Auswahl mehrerer Objekte erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="3a08b-150">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="3a08b-151">Ein häufiges Szenario ist im Dateisystem, in denen ein Benutzer möchte auf alle Dateien im aktuellen Ordner finden Sie unter.</span><span class="sxs-lookup"><span data-stu-id="3a08b-151">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="3a08b-152">Sie sollten eine übereinstimmende benutzerdefinierte Platzhalter-Muster-Implementierung nur selten benötigen.</span><span class="sxs-lookup"><span data-stu-id="3a08b-152">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="3a08b-153">In diesem Fall sollte Ihr Cmdlet entweder das vollständige POSIX 1003.2 wie 3,13 Spezifikation für die platzhaltererweiterung oder die folgende vereinfachte Teilmenge unterstützen:</span><span class="sxs-lookup"><span data-stu-id="3a08b-153">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="3a08b-154">**Fragezeichen (?).**</span><span class="sxs-lookup"><span data-stu-id="3a08b-154">**Question mark (?).**</span></span> <span data-ttu-id="3a08b-155">Entspricht jedem Zeichen an der angegebenen Position.</span><span class="sxs-lookup"><span data-stu-id="3a08b-155">Matches any character at the specified location.</span></span>

- <span data-ttu-id="3a08b-156">**Sternchen (\*).**</span><span class="sxs-lookup"><span data-stu-id="3a08b-156">**Asterisk (\*).**</span></span> <span data-ttu-id="3a08b-157">Entspricht null oder mehr Zeichen beginnend am angegebenen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="3a08b-157">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="3a08b-158">**Öffnende Klammer ([]).**</span><span class="sxs-lookup"><span data-stu-id="3a08b-158">**Open bracket ([).**</span></span> <span data-ttu-id="3a08b-159">Führt einen Klammerausdruck Muster, der Zeichen oder einen Bereich von Zeichen enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="3a08b-159">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="3a08b-160">Wenn ein Bereich erforderlich ist, wird ein Bindestrich (-) an, dass der Bereich verwendet.</span><span class="sxs-lookup"><span data-stu-id="3a08b-160">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="3a08b-161">**Geschweiften Klammer (]).**</span><span class="sxs-lookup"><span data-stu-id="3a08b-161">**Close bracket (]).**</span></span> <span data-ttu-id="3a08b-162">Einen Klammerausdruck Muster wird beendet.</span><span class="sxs-lookup"><span data-stu-id="3a08b-162">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="3a08b-163">**Back-Quote Escape-Zeichen (').**</span><span class="sxs-lookup"><span data-stu-id="3a08b-163">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="3a08b-164">Gibt an, dass das nächste Zeichen Literal verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="3a08b-164">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="3a08b-165">Denken Sie beim Angeben der invertierte Hochkomma über die Befehlszeile (im Gegensatz zu programmgesteuert angeben) das Back-Quote Escapezeichen zweimal muss angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="3a08b-165">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="3a08b-166">Weitere Informationen zu Platzhaltermustern finden Sie unter [unterstützen Platzhalter in der Cmdlet-Parameter](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="3a08b-166">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="3a08b-167">Der folgende Code zeigt, wie Platzhalteroptionen festlegen, und definieren das Platzhaltermuster verwendet für die Auflösung der `Name` -Parameter für dieses Cmdlet aus.</span><span class="sxs-lookup"><span data-stu-id="3a08b-167">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="3a08b-168">Der folgende Code zeigt die Vorgehensweise: testen, ob der Name des Prozesses der definierten Platzhaltermuster übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="3a08b-168">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="3a08b-169">Beachten Sie, dass in diesem Fall, wenn der Name des Prozesses nicht mit das Muster übereinstimmt, das Cmdlet auf weiterhin den nächsten Prozessnamen abzurufen.</span><span class="sxs-lookup"><span data-stu-id="3a08b-169">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="3a08b-170">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="3a08b-170">Code Sample</span></span>

<span data-ttu-id="3a08b-171">Für die vollständige C# Beispielcode, finden Sie unter [StopProcessSample03 Beispiel](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3a08b-171">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="3a08b-172">Definieren von Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="3a08b-172">Define Object Types and Formatting</span></span>

<span data-ttu-id="3a08b-173">Windows PowerShell übergibt Informationen zwischen Cmdlets, die mithilfe von .NET-Objekten.</span><span class="sxs-lookup"><span data-stu-id="3a08b-173">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="3a08b-174">Daher müssen möglicherweise ein Cmdlet seinen eigenen Typ definieren, oder das-Cmdlet zum Erweitern eines vorhandenen Typs, der durch ein anderes Cmdlet angegeben müssen.</span><span class="sxs-lookup"><span data-stu-id="3a08b-174">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="3a08b-175">Weitere Informationen zum Definieren neuer Typen, oder erweitern vorhandene Typen finden Sie unter [Objekttypen erweitern und Formatierung](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="3a08b-175">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="3a08b-176">Erstellen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3a08b-176">Building the Cmdlet</span></span>

<span data-ttu-id="3a08b-177">Nach der Implementierung eines Cmdlets, müssen sie über ein Windows PowerShell-Snap-in mit Windows PowerShell registriert werden.</span><span class="sxs-lookup"><span data-stu-id="3a08b-177">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="3a08b-178">Weitere Informationen zum Registrieren von Cmdlets finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="3a08b-178">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="3a08b-179">Testen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3a08b-179">Testing the Cmdlet</span></span>

<span data-ttu-id="3a08b-180">Wenn Ihr Cmdlet in Windows PowerShell registriert wurde, können Sie es testen, indem Sie sie in der Befehlszeile ausführen.</span><span class="sxs-lookup"><span data-stu-id="3a08b-180">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="3a08b-181">Testen Sie nun das Beispiel beenden-Proc-Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3a08b-181">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="3a08b-182">Weitere Informationen zur Verwendung von Cmdlets, über die Befehlszeile finden Sie unter den [erste Schritte mit Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="3a08b-182">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="3a08b-183">Starten Sie Windows PowerShell, und verwenden Sie Stop-Proc beim Beenden eines Prozesses mit der ProcessName-Alias für die `Name` Parameter.</span><span class="sxs-lookup"><span data-stu-id="3a08b-183">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="3a08b-184">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3a08b-184">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="3a08b-185">Nehmen Sie den folgenden Eintrag in der Befehlszeile ein.</span><span class="sxs-lookup"><span data-stu-id="3a08b-185">Make the following entry on the command line.</span></span> <span data-ttu-id="3a08b-186">Da es sich bei der Name-Parameter obligatorisch ist, werden Sie dazu aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="3a08b-186">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="3a08b-187">Eingeben von "!"</span><span class="sxs-lookup"><span data-stu-id="3a08b-187">Entering "!?"</span></span> <span data-ttu-id="3a08b-188">der Hilfetext, der dem Parameter zugeordnet wird.</span><span class="sxs-lookup"><span data-stu-id="3a08b-188">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="3a08b-189">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3a08b-189">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="3a08b-190">Stellen Sie jetzt den folgenden Eintrag zum Beenden aller Prozesse, die das Platzhaltermuster entsprechen "\* Hinweis\*".</span><span class="sxs-lookup"><span data-stu-id="3a08b-190">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="3a08b-191">Sie werden aufgefordert, vor dem Beenden der einzelnen Prozesse mit dem Muster übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="3a08b-191">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="3a08b-192">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3a08b-192">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="3a08b-193">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3a08b-193">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="3a08b-194">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3a08b-194">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="3a08b-195">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3a08b-195">See Also</span></span>

[<span data-ttu-id="3a08b-196">Erstellen Sie ein Cmdlet, das das System geändert wird</span><span class="sxs-lookup"><span data-stu-id="3a08b-196">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="3a08b-197">Vorgehensweise: Erstellen eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="3a08b-197">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="3a08b-198">Erweitern die Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="3a08b-198">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="3a08b-199">So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen</span><span class="sxs-lookup"><span data-stu-id="3a08b-199">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="3a08b-200">Unterstützung von Platzhaltern in der Cmdlet-Parameter</span><span class="sxs-lookup"><span data-stu-id="3a08b-200">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="3a08b-201">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3a08b-201">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
