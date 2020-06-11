---
title: Schlüsselwörter in der kommentarbasierten Hilfe
ms.custom: ''
ms.date: 06/09/2020
ms.topic: article
ms.openlocfilehash: 674d0f99800595cbbd64a80d0e0c5aed22f3b45c
ms.sourcegitcommit: 4a283fe5419f47102e6c1de7060880a934842ee9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2020
ms.locfileid: "84671375"
---
# <a name="comment-based-help-keywords"></a><span data-ttu-id="390a4-102">Schlüsselwörter in der kommentarbasierten Hilfe</span><span class="sxs-lookup"><span data-stu-id="390a4-102">Comment-Based Help Keywords</span></span>

<span data-ttu-id="390a4-103">In diesem Thema werden die Schlüsselwörter in der Kommentar basierten Hilfe aufgelistet und beschrieben.</span><span class="sxs-lookup"><span data-stu-id="390a4-103">This topic lists and describes the keywords in comment-based help.</span></span>

## <a name="keywords-in-comment-based-help"></a><span data-ttu-id="390a4-104">Schlüsselwörter in der Kommentar basierten Hilfe</span><span class="sxs-lookup"><span data-stu-id="390a4-104">Keywords in Comment-Based Help</span></span>

<span data-ttu-id="390a4-105">Im folgenden finden Sie gültige Kommentar basierte Hilfe Schlüsselwörter.</span><span class="sxs-lookup"><span data-stu-id="390a4-105">The following are valid comment-based Help keywords.</span></span> <span data-ttu-id="390a4-106">Sie werden in der Reihenfolge aufgelistet, in der Sie in der Regel in einem Hilfethema zusammen mit der vorgesehenen Verwendung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="390a4-106">They are listed in the order in which they typically appear in a Help topic along with their intended use.</span></span> <span data-ttu-id="390a4-107">Diese Schlüsselwörter können in beliebiger Reihenfolge in der Kommentar basierten Hilfe angezeigt werden, und es wird nicht zwischen Groß-und Kleinschreibung unterschieden.</span><span class="sxs-lookup"><span data-stu-id="390a4-107">These keywords can appear in any order in the comment-based Help, and they are not case-sensitive.</span></span>

<span data-ttu-id="390a4-108">Beachten Sie, dass das- `.EXTERNALHELP` Schlüsselwort Vorrang vor allen anderen Kommentar basierten Hilfe Schlüsselwörtern hat.</span><span class="sxs-lookup"><span data-stu-id="390a4-108">Note that the `.EXTERNALHELP` keyword takes precedence over all other comment-based help keywords.</span></span>
<span data-ttu-id="390a4-109">Wenn `.EXTERNALHELP` vorhanden ist, zeigt das [Microsoft. PowerShell. Commands. gethelpcommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) -Cmdlet keine Kommentar basierte Hilfe an, auch wenn keine Hilfedatei gefunden werden kann, die mit dem Wert des-Schlüssel Worts übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="390a4-109">When `.EXTERNALHELP` is present, the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet does not display comment-based help, even when it cannot find a help file that matches the value of the keyword.</span></span>

## <a name="synopsis"></a><span data-ttu-id="390a4-110">. Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="390a4-110">.SYNOPSIS</span></span>

<span data-ttu-id="390a4-111">Eine kurze Beschreibung der Funktion oder des Skripts.</span><span class="sxs-lookup"><span data-stu-id="390a4-111">A brief description of the function or script.</span></span> <span data-ttu-id="390a4-112">Dieses Schlüsselwort kann nur einmal in jedem Thema verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="390a4-112">This keyword can be used only once in each topic.</span></span>

## <a name="description"></a><span data-ttu-id="390a4-113">. Beschreibung</span><span class="sxs-lookup"><span data-stu-id="390a4-113">.DESCRIPTION</span></span>

<span data-ttu-id="390a4-114">Eine ausführliche Beschreibung der Funktion oder des Skripts.</span><span class="sxs-lookup"><span data-stu-id="390a4-114">A detailed description of the function or script.</span></span> <span data-ttu-id="390a4-115">Dieses Schlüsselwort kann nur einmal in jedem Thema verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="390a4-115">This keyword can be used only once in each topic.</span></span>

## <a name="parameter-parameter-name"></a><span data-ttu-id="390a4-116">. Parame\<Parameter-Name></span><span class="sxs-lookup"><span data-stu-id="390a4-116">.PARAMETER \<Parameter-Name></span></span>

<span data-ttu-id="390a4-117">Die Beschreibung eines Parameters.</span><span class="sxs-lookup"><span data-stu-id="390a4-117">The description of a parameter.</span></span> <span data-ttu-id="390a4-118">Sie können `.PARAMETER` für jeden Parameter in der Funktion oder im Skript ein Schlüsselwort einschließen.</span><span class="sxs-lookup"><span data-stu-id="390a4-118">You can include a `.PARAMETER` keyword for each parameter in the function or script.</span></span>

<span data-ttu-id="390a4-119">Die `.PARAMETER` Schlüsselwörter können in beliebiger Reihenfolge im Kommentar Block angezeigt werden, aber die Reihenfolge, in der die Parameter in der `Param` Anweisung oder Funktionsdeklaration angezeigt werden, bestimmt die Reihenfolge, in der die Parameter im Hilfethema angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="390a4-119">The `.PARAMETER` keywords can appear in any order in the comment block, but the order in which the parameters appear in the `Param` statement or function declaration determines the order in which the parameters appear in Help topic.</span></span> <span data-ttu-id="390a4-120">Um die Reihenfolge der Parameter im Hilfethema zu ändern, ändern Sie die Reihenfolge der Parameter in der- `Param` Anweisung oder der-Funktionsdeklaration.</span><span class="sxs-lookup"><span data-stu-id="390a4-120">To change the order of parameters in the Help topic, change the order of the parameters in the `Param` statement or function declaration.</span></span>

<span data-ttu-id="390a4-121">Sie können auch eine Parameter Beschreibung angeben, indem Sie einen Kommentar `Param` direkt vor dem Variablennamen des Parameters in der Anweisung platzieren.</span><span class="sxs-lookup"><span data-stu-id="390a4-121">You can also specify a parameter description by placing a comment in the `Param` statement immediately before the parameter variable name.</span></span> <span data-ttu-id="390a4-122">Wenn Sie sowohl einen `Param` Anweisungs Kommentar als auch ein `.PARAMETER` Schlüsselwort verwenden, wird die dem Schlüsselwort zugeordnete Beschreibung `.PARAMETER` verwendet, und der `Param` Anweisungs Kommentar wird ignoriert.</span><span class="sxs-lookup"><span data-stu-id="390a4-122">If you use both a `Param` statement comment and a `.PARAMETER` keyword, the description associated with the `.PARAMETER` keyword is used, and the `Param` statement comment is ignored.</span></span>

## <a name="example"></a><span data-ttu-id="390a4-123">. Beispiel</span><span class="sxs-lookup"><span data-stu-id="390a4-123">.EXAMPLE</span></span>

<span data-ttu-id="390a4-124">Ein Beispiel Befehl, der die Funktion oder das Skript verwendet, optional gefolgt von der Beispielausgabe und einer Beschreibung.</span><span class="sxs-lookup"><span data-stu-id="390a4-124">A sample command that uses the function or script, optionally followed by sample output and a description.</span></span> <span data-ttu-id="390a4-125">Wiederholen Sie dieses Schlüsselwort für jedes Beispiel.</span><span class="sxs-lookup"><span data-stu-id="390a4-125">Repeat this keyword for each example.</span></span>

## <a name="inputs"></a><span data-ttu-id="390a4-126">. Ungs</span><span class="sxs-lookup"><span data-stu-id="390a4-126">.INPUTS</span></span>

<span data-ttu-id="390a4-127">Die Microsoft .NET Framework-Typen von Objekten, die an die Funktion oder das Skript weitergeleitet werden können.</span><span class="sxs-lookup"><span data-stu-id="390a4-127">The Microsoft .NET Framework types of objects that can be piped to the function or script.</span></span> <span data-ttu-id="390a4-128">Sie können auch eine Beschreibung der Eingabe Objekte einschließen.</span><span class="sxs-lookup"><span data-stu-id="390a4-128">You can also include a description of the input objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="390a4-129">. Ausgaben</span><span class="sxs-lookup"><span data-stu-id="390a4-129">.OUTPUTS</span></span>

<span data-ttu-id="390a4-130">Der .NET Framework Typ der Objekte, die vom Cmdlet zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="390a4-130">The .NET Framework type of the objects that the cmdlet returns.</span></span> <span data-ttu-id="390a4-131">Sie können auch eine Beschreibung der zurückgegebenen Objekte einschließen.</span><span class="sxs-lookup"><span data-stu-id="390a4-131">You can also include a description of the returned objects.</span></span>

## <a name="notes"></a><span data-ttu-id="390a4-132">. Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="390a4-132">.NOTES</span></span>

<span data-ttu-id="390a4-133">Zusätzliche Informationen über die Funktion oder das Skript.</span><span class="sxs-lookup"><span data-stu-id="390a4-133">Additional information about the function or script.</span></span>

## <a name="link"></a><span data-ttu-id="390a4-134">. Verknüpfen</span><span class="sxs-lookup"><span data-stu-id="390a4-134">.LINK</span></span>

<span data-ttu-id="390a4-135">Der Name eines verwandten Themas.</span><span class="sxs-lookup"><span data-stu-id="390a4-135">The name of a related topic.</span></span> <span data-ttu-id="390a4-136">Wiederholen Sie dieses Schlüsselwort für jedes verwandte Thema.</span><span class="sxs-lookup"><span data-stu-id="390a4-136">Repeat this keyword for each related topic.</span></span> <span data-ttu-id="390a4-137">Dieser Inhalt wird im Abschnitt Verwandte Links des Hilfe Themas angezeigt.</span><span class="sxs-lookup"><span data-stu-id="390a4-137">This content appears in the Related Links section of the Help topic.</span></span>

<span data-ttu-id="390a4-138">Das `.LINK` Schlüsselwort Content kann auch eine Uniform Resource Identifier (URI) zu einer Online Version desselben Hilfe Themas enthalten.</span><span class="sxs-lookup"><span data-stu-id="390a4-138">The `.LINK` keyword content can also include a Uniform Resource Identifier (URI) to an online version of the same Help topic.</span></span> <span data-ttu-id="390a4-139">Die Online Version wird geöffnet, wenn Sie den- `Online` Parameter von verwenden `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="390a4-139">The online version opens when you use the `Online` parameter of `Get-Help`.</span></span> <span data-ttu-id="390a4-140">Der URI muss mit "http" oder "https" beginnen.</span><span class="sxs-lookup"><span data-stu-id="390a4-140">The URI must begin with "http" or "https".</span></span>

## <a name="component"></a><span data-ttu-id="390a4-141">. Zulieferern</span><span class="sxs-lookup"><span data-stu-id="390a4-141">.COMPONENT</span></span>

<span data-ttu-id="390a4-142">Der Name der Technologie oder des Features, die bzw. das von der Funktion oder dem Skript verwendet wird bzw. mit dem Sie verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="390a4-142">The name of the technology or feature that the function or script uses, or to which it is related.</span></span>
<span data-ttu-id="390a4-143">Der **Component** -Parameter von `Get-Help` verwendet diesen Wert, um die von zurückgegebenen Suchergebnisse zu filtern `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="390a4-143">The **Component** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="role"></a><span data-ttu-id="390a4-144">. Spielen</span><span class="sxs-lookup"><span data-stu-id="390a4-144">.Role</span></span>

<span data-ttu-id="390a4-145">Der Name der Benutzerrolle für das Hilfethema.</span><span class="sxs-lookup"><span data-stu-id="390a4-145">The name of the user role for the help topic.</span></span> <span data-ttu-id="390a4-146">Der **Role** -Parameter von `Get-Help` verwendet diesen Wert, um die von zurückgegebenen Suchergebnisse zu filtern `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="390a4-146">The **Role** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="functionality"></a><span data-ttu-id="390a4-147">. Alitäts</span><span class="sxs-lookup"><span data-stu-id="390a4-147">.FUNCTIONALITY</span></span>

<span data-ttu-id="390a4-148">Die Schlüsselwörter, die die beabsichtigte Verwendung der Funktion beschreiben.</span><span class="sxs-lookup"><span data-stu-id="390a4-148">The keywords that describe the intended use of the function.</span></span> <span data-ttu-id="390a4-149">Der- **Funktions** Parameter von `Get-Help` verwendet diesen Wert, um die von zurückgegebenen Suchergebnisse zu filtern `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="390a4-149">The **Functionality** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="forwardhelptargetname-command-name"></a><span data-ttu-id="390a4-150">. Forwardhelptargetname\<Command-Name></span><span class="sxs-lookup"><span data-stu-id="390a4-150">.FORWARDHELPTARGETNAME \<Command-Name></span></span>

<span data-ttu-id="390a4-151">Leitet das Hilfethema für den angegebenen Befehl um.</span><span class="sxs-lookup"><span data-stu-id="390a4-151">Redirects to the Help topic for the specified command.</span></span> <span data-ttu-id="390a4-152">Sie können Benutzer zu jedem beliebigen Hilfethema umleiten, einschließlich der Hilfe Themen für eine Funktion, ein Skript, ein Cmdlet oder einen Anbieter.</span><span class="sxs-lookup"><span data-stu-id="390a4-152">You can redirect users to any Help topic, including Help topics for a function, script, cmdlet, or provider.</span></span>

## <a name="forwardhelpcategory-category"></a><span data-ttu-id="390a4-153">. Forwardhelpcategory\<Category></span><span class="sxs-lookup"><span data-stu-id="390a4-153">.FORWARDHELPCATEGORY \<Category></span></span>

<span data-ttu-id="390a4-154">Gibt die Hilfe Kategorie des Elements in an `.FORWARDHELPTARGETNAME` .</span><span class="sxs-lookup"><span data-stu-id="390a4-154">Specifies the Help category of the item in `.FORWARDHELPTARGETNAME`.</span></span> <span data-ttu-id="390a4-155">Verwenden Sie dieses Schlüsselwort, um Konflikte zu vermeiden, wenn Befehle mit demselben Namen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="390a4-155">Use this keyword to avoid conflicts when there are commands with the same name.</span></span>

<span data-ttu-id="390a4-156">Gültige Werte sind:</span><span class="sxs-lookup"><span data-stu-id="390a4-156">Valid values are:</span></span>

- <span data-ttu-id="390a4-157">Alias</span><span class="sxs-lookup"><span data-stu-id="390a4-157">Alias</span></span>
- <span data-ttu-id="390a4-158">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="390a4-158">Cmdlet</span></span>
- <span data-ttu-id="390a4-159">HelpFile</span><span class="sxs-lookup"><span data-stu-id="390a4-159">HelpFile</span></span>
- <span data-ttu-id="390a4-160">Funktion</span><span class="sxs-lookup"><span data-stu-id="390a4-160">Function</span></span>
- <span data-ttu-id="390a4-161">Anbieter</span><span class="sxs-lookup"><span data-stu-id="390a4-161">Provider</span></span>
- <span data-ttu-id="390a4-162">Allgemein</span><span class="sxs-lookup"><span data-stu-id="390a4-162">General</span></span>
- <span data-ttu-id="390a4-163">Häufig gestellte Fragen</span><span class="sxs-lookup"><span data-stu-id="390a4-163">FAQ</span></span>
- <span data-ttu-id="390a4-164">Glossar</span><span class="sxs-lookup"><span data-stu-id="390a4-164">Glossary</span></span>
- <span data-ttu-id="390a4-165">ScriptCommand</span><span class="sxs-lookup"><span data-stu-id="390a4-165">ScriptCommand</span></span>
- <span data-ttu-id="390a4-166">Externalscript</span><span class="sxs-lookup"><span data-stu-id="390a4-166">ExternalScript</span></span>
- <span data-ttu-id="390a4-167">Filtern</span><span class="sxs-lookup"><span data-stu-id="390a4-167">Filter</span></span>
- <span data-ttu-id="390a4-168">All</span><span class="sxs-lookup"><span data-stu-id="390a4-168">All</span></span>

## <a name="remotehelprunspace-pssession-variable"></a><span data-ttu-id="390a4-169">. Remotehelprunspace\<PSSession-variable></span><span class="sxs-lookup"><span data-stu-id="390a4-169">.REMOTEHELPRUNSPACE \<PSSession-variable></span></span>

<span data-ttu-id="390a4-170">Gibt eine Sitzung an, die das Hilfethema enthält.</span><span class="sxs-lookup"><span data-stu-id="390a4-170">Specifies a session that contains the Help topic.</span></span> <span data-ttu-id="390a4-171">Geben Sie eine Variable ein, die eine PSSession enthält.</span><span class="sxs-lookup"><span data-stu-id="390a4-171">Enter a variable that contains a PSSession.</span></span> <span data-ttu-id="390a4-172">Dieses Schlüsselwort wird vom `Export-PSSession` Cmdlet verwendet, um die Hilfe Themen für die exportierten Befehle zu suchen.</span><span class="sxs-lookup"><span data-stu-id="390a4-172">This keyword is used by the `Export-PSSession` cmdlet to find the Help topics for the exported commands.</span></span>

## <a name="externalhelp-xml-help-file"></a><span data-ttu-id="390a4-173">. Externalhelp "\<XML Help File></span><span class="sxs-lookup"><span data-stu-id="390a4-173">.EXTERNALHELP \<XML Help File></span></span>

<span data-ttu-id="390a4-174">Gibt den Pfad und/oder den Namen einer XML-basierten Hilfedatei für das Skript oder die Funktion an.</span><span class="sxs-lookup"><span data-stu-id="390a4-174">Specifies the path and/or name of an XML-based Help file for the script or function.</span></span>

<span data-ttu-id="390a4-175">Das- `.EXTERNALHELP` Schlüsselwort weist das [Microsoft. PowerShell. Commands. gethelpcommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) -Cmdlet an, Hilfe für das Skript oder die Funktion in einer XML-basierten Datei zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="390a4-175">The `.EXTERNALHELP` keyword tells the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet to get help for the script or function in an XML-based file.</span></span> <span data-ttu-id="390a4-176">Das `.EXTERNALHELP` Schlüsselwort ist erforderlich, wenn eine XML-basierte Hilfedatei für ein Skript oder eine Funktion verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="390a4-176">The `.EXTERNALHELP` keyword is required when using an XML-based help file for a script or function.</span></span> <span data-ttu-id="390a4-177">Ohne diese findet `Get-Help` keine Hilfedatei für die Funktion oder das Skript.</span><span class="sxs-lookup"><span data-stu-id="390a4-177">Without it, `Get-Help` will not find a help file for the function or script.</span></span>

<span data-ttu-id="390a4-178">Das- `.EXTERNALHELP` Schlüsselwort hat Vorrang vor allen anderen Kommentar basierten Hilfe Schlüsselwörtern.</span><span class="sxs-lookup"><span data-stu-id="390a4-178">The `.EXTERNALHELP` keyword takes precedence over all other comment-based help keywords.</span></span> <span data-ttu-id="390a4-179">Wenn `.EXTERNALHELP` vorhanden ist, zeigt das [Microsoft. PowerShell. Commands. gethelpcommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) -Cmdlet keine Kommentar basierte Hilfe an, auch wenn keine Hilfedatei gefunden werden kann, die mit dem Wert des-Schlüssel Worts übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="390a4-179">When `.EXTERNALHELP` is present, the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet does not display comment-based help, even when it cannot find a help file that matches the value of the keyword.</span></span>

<span data-ttu-id="390a4-180">Wenn die Funktion von einem Skript Modul exportiert wird, sollte der Wert von `.EXTERNALHELP` ein Dateiname ohne Pfad sein.</span><span class="sxs-lookup"><span data-stu-id="390a4-180">When the function is exported by a script module, the value of `.EXTERNALHELP` should be a filename without a path.</span></span> <span data-ttu-id="390a4-181">`Get-Help`sucht die Datei in einem Gebiets Schema spezifischen Unterverzeichnis des Modul Verzeichnisses.</span><span class="sxs-lookup"><span data-stu-id="390a4-181">`Get-Help` looks for the file in a locale-specific subdirectory of the module directory.</span></span> <span data-ttu-id="390a4-182">Der Dateiname hat keine Anforderungen, aber eine bewährte Vorgehensweise ist die Verwendung des folgenden Dateinamen Formats: `<ScriptModule>.psm1-help.xml` .</span><span class="sxs-lookup"><span data-stu-id="390a4-182">There are no requirements for the filename, but a best practice is to use the following filename format: `<ScriptModule>.psm1-help.xml`.</span></span>

<span data-ttu-id="390a4-183">Wenn die Funktion keinem Modul zugeordnet ist, fügen Sie einen Pfad und einen Dateinamen in den Wert des `.EXTERNALHELP` Schlüssel Worts ein.</span><span class="sxs-lookup"><span data-stu-id="390a4-183">When the function is not associated with a module, include a path and filename in the value of the `.EXTERNALHELP` keyword.</span></span> <span data-ttu-id="390a4-184">Wenn der angegebene Pfad zur XML-Datei Benutzeroberflächen kulturspezifische Unterverzeichnisse enthält, `Get-Help` durchsucht die Unterverzeichnisse rekursiv nach einer XML-Datei mit dem Namen des Skripts oder der Funktion in Übereinstimmung mit den für Windows eingerichteten sprach Fall Back Standards, ebenso wie bei allen XML-basierten Hilfe Themen.</span><span class="sxs-lookup"><span data-stu-id="390a4-184">If the specified path to the XML file contains UI-culture-specific subdirectories, `Get-Help` searches the subdirectories recursively for an XML file with the name of the script or function in accordance with the language fallback standards established for Windows, just as it does for all XML-based Help topics.</span></span>

<span data-ttu-id="390a4-185">Weitere Informationen zum XML-basierten Hilfedatei Format in der Cmdlet-Hilfe finden Sie unter [Schreiben der Windows PowerShell-Cmdlet-Hilfe](./writing-help-for-windows-powershell-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="390a4-185">For more information about the cmdlet Help XML-based Help file format, see [Writing Windows PowerShell Cmdlet Help](./writing-help-for-windows-powershell-cmdlets.md).</span></span>
