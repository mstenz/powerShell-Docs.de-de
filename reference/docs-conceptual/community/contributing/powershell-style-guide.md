---
title: Styleguide für die PowerShell-Dokumentation
description: Dieser Artikel enthält die Stilregeln für das Schreiben von PowerShell-Dokumentation.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 964536c5195c3bb8abd98b5996a96fc7b9362489
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402577"
---
# <a name="powershell-docs-style-guide"></a><span data-ttu-id="14d5c-103">Styleguide für die PowerShell-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="14d5c-103">PowerShell-Docs style guide</span></span>

<span data-ttu-id="14d5c-104">Dieser Artikel enthält die spezifischen Stilanweisungen für Inhalte der PowerShell-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="14d5c-104">This article provides style guidance specific to the PowerShell-Docs content.</span></span> <span data-ttu-id="14d5c-105">Dies geschieht ausgehend von den in der [Übersicht](overview.md#get-started-writing-docs) beschriebenen Informationen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-105">This builds on the information outlined in the [Overview](overview.md#get-started-writing-docs).</span></span>

## <a name="product-terminology"></a><span data-ttu-id="14d5c-106">Produktterminologie</span><span class="sxs-lookup"><span data-stu-id="14d5c-106">Product Terminology</span></span>

<span data-ttu-id="14d5c-107">Es gibt mehrere Varianten von PowerShell.</span><span class="sxs-lookup"><span data-stu-id="14d5c-107">There are several variants of PowerShell.</span></span>
<span data-ttu-id="14d5c-108">In dieser Tabelle werden einige der unterschiedlichen Begriffe definiert, die bei der Erörterung von PowerShell verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="14d5c-108">This table defines some of the different terms used to discuss PowerShell.</span></span>

- <span data-ttu-id="14d5c-109">**PowerShell**: Dies ist die Standardvariante.</span><span class="sxs-lookup"><span data-stu-id="14d5c-109">**PowerShell** - This is the default.</span></span> <span data-ttu-id="14d5c-110">Wir sehen im weiteren Verlauf PowerShell 7 und höhere Versionen als das eine echte PowerShell an.</span><span class="sxs-lookup"><span data-stu-id="14d5c-110">We consider PowerShell 7 and beyond to be the one, true PowerShell going forward.</span></span>

- <span data-ttu-id="14d5c-111">**PowerShell Core-** : PowerShell basierend auf .NET Core.</span><span class="sxs-lookup"><span data-stu-id="14d5c-111">**PowerShell Core** - PowerShell built on .NET Core.</span></span> <span data-ttu-id="14d5c-112">Die Verwendung des Begriffs **Core** sollte auf Fälle beschränkt sein, in denen die Unterscheidung von Windows PowerShell erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="14d5c-112">Usage of the term **Core** should be limited to cases where it is necessary to differentiate it from Windows PowerShell.</span></span>

- <span data-ttu-id="14d5c-113">**Windows PowerShell**:- PowerShell basierend auf .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="14d5c-113">**Windows PowerShell** - PowerShell built on .NET Framework.</span></span> <span data-ttu-id="14d5c-114">Windows PowerShell wird nur für Windows ausgeliefert und erfordert das gesamte Framework.</span><span class="sxs-lookup"><span data-stu-id="14d5c-114">Windows PowerShell ships only on Windows and requires the complete Framework.</span></span>

<span data-ttu-id="14d5c-115">Im Allgemeinen können Verweise auf „Windows PowerShell“ in der Dokumentation zu „PowerShell“ geändert werden.</span><span class="sxs-lookup"><span data-stu-id="14d5c-115">In general, references to "Windows PowerShell" in documentation can be changed to "PowerShell".</span></span>
<span data-ttu-id="14d5c-116">„Windows PowerShell“ sollte **nicht** geändert werden, wenn Windows-spezifische Technologien behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="14d5c-116">"Windows PowerShell" should **not** be changed when Windows-specific technology is being discussed.</span></span>

## <a name="markdown-specifics"></a><span data-ttu-id="14d5c-117">Besonderheiten von Markdown</span><span class="sxs-lookup"><span data-stu-id="14d5c-117">Markdown specifics</span></span>

<span data-ttu-id="14d5c-118">Das Microsoft Open Publishing System (OPS), mit dem unsere Dokumentation erstellt wird, verwendet [markdig][], um die Markdown-Dokumente zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="14d5c-118">The Microsoft Open Publishing System (OPS) that builds our documentation uses [markdig][] to process the Markdown documents.</span></span> <span data-ttu-id="14d5c-119">Markdig analysiert die Dokumente auf der Grundlage der Regeln der aktuellen [CommonMark][]-Spezifikation.</span><span class="sxs-lookup"><span data-stu-id="14d5c-119">Markdig parses the documents based on the rules of the latest [CommonMark][] specification.</span></span>

<span data-ttu-id="14d5c-120">Die neue CommonMark-Spezifikation ist weitaus strenger im Hinblick auf den Aufbau einiger Markdown-Elemente.</span><span class="sxs-lookup"><span data-stu-id="14d5c-120">The new CommonMark spec is much stricter about the construction of some Markdown elements.</span></span> <span data-ttu-id="14d5c-121">Beachten Sie die Detailinformationen in diesem Dokument genau.</span><span class="sxs-lookup"><span data-stu-id="14d5c-121">Pay close attention to the details provided in this document.</span></span>

### <a name="blank-lines-spaces-and-tabs"></a><span data-ttu-id="14d5c-122">Leerzeilen, Leerzeichen und Tabstoppzeichen</span><span class="sxs-lookup"><span data-stu-id="14d5c-122">Blank lines, spaces, and tabs</span></span>

<span data-ttu-id="14d5c-123">Entfernen Sie doppelte Leerzeilen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-123">Remove duplicate blank lines.</span></span> <span data-ttu-id="14d5c-124">Mehrere Leerzeilen werden in HTML als einzelne Leerzeile dargestellt, sodass es keinen Grund für mehrere Leerzeilen gibt.</span><span class="sxs-lookup"><span data-stu-id="14d5c-124">Multiple blank lines render as a single blank line in HTML so there is not purpose for multiple blank lines.</span></span>

<span data-ttu-id="14d5c-125">Leerzeilen signalisieren darüber hinaus in Markdown das Ende eines Blocks.</span><span class="sxs-lookup"><span data-stu-id="14d5c-125">Blank lines also signal the end of a block in Markdown.</span></span> <span data-ttu-id="14d5c-126">Zwischen Markdown-Blöcken unterschiedlicher Typen (z. B. zwischen einem Absatz und einer Liste oder einem Header) sollte eine einzelne Leerzeile stehen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-126">There should be a single blank between Markdown blocks of different types (for example, between a paragraph and a list or header).</span></span>

> [!NOTE]
> <span data-ttu-id="14d5c-127">Abstände sind in Markdown wichtig.</span><span class="sxs-lookup"><span data-stu-id="14d5c-127">Spacing is significant in Markdown.</span></span> <span data-ttu-id="14d5c-128">Verwenden Sie immer Leerzeichen anstelle harter Tabstoppzeichen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-128">Always uses spaces instead of hard tabs.</span></span> <span data-ttu-id="14d5c-129">Entfernen Sie zusätzliche Leerzeichen am Zeilenende.</span><span class="sxs-lookup"><span data-stu-id="14d5c-129">Remove extra spaces at the end of lines.</span></span>

### <a name="titles-and-headings"></a><span data-ttu-id="14d5c-130">Titel und Überschriften</span><span class="sxs-lookup"><span data-stu-id="14d5c-130">Titles and headings</span></span>

<span data-ttu-id="14d5c-131">Verwenden Sie nur [ATX-Überschriften][atx] (#-Formatvorlage, im Gegensatz zu Überschriften der `=`- oder `-`-Formatvorlagen).</span><span class="sxs-lookup"><span data-stu-id="14d5c-131">Only use [ATX headings][atx] (# style, as opposed to `=` or `-` style headers).</span></span>

- <span data-ttu-id="14d5c-132">Verwenden Sie normale Groß-/Kleinschreibung – nur Eigennamen und der erste Buchstabe eines Titels oder einer Überschrift sollten groß geschrieben werden</span><span class="sxs-lookup"><span data-stu-id="14d5c-132">Use sentence case - only proper nouns and the first letter of a title or header should be capitalized</span></span>
- <span data-ttu-id="14d5c-133">Zwischen dem `#` und dem ersten Buchstaben des Titels muss ein einfaches Leerzeichen stehen</span><span class="sxs-lookup"><span data-stu-id="14d5c-133">There must be a single space between the `#` and the first letter of the heading</span></span>
- <span data-ttu-id="14d5c-134">Überschriften sollten von einer einzelnen Leerzeile umgeben sein</span><span class="sxs-lookup"><span data-stu-id="14d5c-134">Headings should be surrounded by a single blank line</span></span>
- <span data-ttu-id="14d5c-135">Nur eine Überschrift der Ebene H1 pro Dokument</span><span class="sxs-lookup"><span data-stu-id="14d5c-135">Only one H1 per document</span></span>
- <span data-ttu-id="14d5c-136">Überschriftebenen sollten um 1 erhöht werden.</span><span class="sxs-lookup"><span data-stu-id="14d5c-136">Header levels should increment by one.</span></span> <span data-ttu-id="14d5c-137">Überspringen Sie keine Ebenen</span><span class="sxs-lookup"><span data-stu-id="14d5c-137">Do not skip levels</span></span>
- <span data-ttu-id="14d5c-138">Verwenden Sie keine fette oder sonstige Auszeichnung in Überschriften</span><span class="sxs-lookup"><span data-stu-id="14d5c-138">Do not use bold or other markup in headers</span></span>

### <a name="limit-line-length-to-100-characters"></a><span data-ttu-id="14d5c-139">Begrenzen Sie die Zeilenlänge auf 100 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14d5c-139">Limit line length to 100 characters</span></span>

<span data-ttu-id="14d5c-140">Dies gilt für konzeptionelle Artikel und die Cmdlet-Referenz.</span><span class="sxs-lookup"><span data-stu-id="14d5c-140">This applies to conceptual articles and cmdlet reference.</span></span> <span data-ttu-id="14d5c-141">Klassische Hilfethemen (About_topics) sind auf 80 Zeichen beschränkt.</span><span class="sxs-lookup"><span data-stu-id="14d5c-141">About_topics are limited to 80 characters.</span></span>
<span data-ttu-id="14d5c-142">Das Beschränken der Zeilenlänge verbessert die Lesbarkeit von git-Diffs und git-Verlauf.</span><span class="sxs-lookup"><span data-stu-id="14d5c-142">Limiting the line length improves the readability git diffs and history.</span></span> <span data-ttu-id="14d5c-143">Es erleichtert außerdem anderen Autoren das Einbringen ihres Beitrags.</span><span class="sxs-lookup"><span data-stu-id="14d5c-143">It also makes it easier for other writers to make contributions.</span></span>

<span data-ttu-id="14d5c-144">Verwenden Sie die Erweiterung [Reflow Markdown][reflow] in Visual Studio Code, um Absätze komfortabel umzubrechen, sodass sie in die erforderliche Zeilenlänge passen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-144">Use the [Reflow Markdown][reflow] extension in Visual Studio Code to easily reflow paragraphs to fit the prescribed line length.</span></span>

### <a name="lists"></a><span data-ttu-id="14d5c-145">Listen</span><span class="sxs-lookup"><span data-stu-id="14d5c-145">Lists</span></span>

<span data-ttu-id="14d5c-146">Wenn Ihre Liste mehrere Sätze oder Absätze enthält, erwägen Sie eine Unterüberschrift anstelle einer Liste.</span><span class="sxs-lookup"><span data-stu-id="14d5c-146">If your list contains multiple sentences or paragraphs, consider using a sub-level header rather than a list.</span></span>

<span data-ttu-id="14d5c-147">Eine Liste sollte von einer einzelnen Leerzeile umgeben sein.</span><span class="sxs-lookup"><span data-stu-id="14d5c-147">List should be surrounded by a single blank line.</span></span>

#### <a name="unordered-lists"></a><span data-ttu-id="14d5c-148">Unsortierte Listen</span><span class="sxs-lookup"><span data-stu-id="14d5c-148">Unordered lists</span></span>

<span data-ttu-id="14d5c-149">Beenden Sie Listenelemente nicht mit einem Punkt, es sei denn, sie enthalten mehrere Sätze.</span><span class="sxs-lookup"><span data-stu-id="14d5c-149">Do not end list items with a period unless they contain multiple sentences.</span></span> <span data-ttu-id="14d5c-150">Verwenden Sie das Bindestrich Zeichen (`-`) für Listenelement Aufzählungen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-150">Use the hyphen character (`-`) for list item bullets.</span></span> <span data-ttu-id="14d5c-151">Dadurch wird die Verwechselung mit fettem oder kursivem Markup vermieden, für das das Sternchen [`*`] verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="14d5c-151">This avoids confusion with bold or italic markup that uses the asterisk [`*`].</span></span> <span data-ttu-id="14d5c-152">Um einen Absatz oder andere Elemente unter einem Aufzählungselement einzuschließen, fügen Sie einen Zeilenumbruch ein, und richten Sie den Einzug am ersten Zeichen nach dem Aufzählungszeichen aus.</span><span class="sxs-lookup"><span data-stu-id="14d5c-152">To include a paragraph or other elements under a bullet item, insert a line break and align indentation with the first character after the bullet.</span></span>

<span data-ttu-id="14d5c-153">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="14d5c-153">For example:</span></span>

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

<span data-ttu-id="14d5c-154">Dies ist eine Liste, die Unterelemente unter einem Aufzählungselement enthält.</span><span class="sxs-lookup"><span data-stu-id="14d5c-154">This is a list that contains sub-elements under a bullet item.</span></span>

- <span data-ttu-id="14d5c-155">Erstes Aufzählungselement</span><span class="sxs-lookup"><span data-stu-id="14d5c-155">First bullet item</span></span>

  <span data-ttu-id="14d5c-156">Satz zur Erläuterung des ersten Aufzählungszeichens.</span><span class="sxs-lookup"><span data-stu-id="14d5c-156">Sentence explaining the first bullet.</span></span>

  - <span data-ttu-id="14d5c-157">Untergeordnetes Aufzählungszeichen</span><span class="sxs-lookup"><span data-stu-id="14d5c-157">Sub-bullet item</span></span>

    <span data-ttu-id="14d5c-158">Satz zur Erläuterung des Unteraufzählungszeichens.</span><span class="sxs-lookup"><span data-stu-id="14d5c-158">Sentence explaining the sub-bullet.</span></span>

- <span data-ttu-id="14d5c-159">Zweites Aufzählungszeichen</span><span class="sxs-lookup"><span data-stu-id="14d5c-159">Second bullet item</span></span>
- <span data-ttu-id="14d5c-160">Drittes Aufzählungszeichen</span><span class="sxs-lookup"><span data-stu-id="14d5c-160">Third bullet item</span></span>

#### <a name="ordered-lists"></a><span data-ttu-id="14d5c-161">Sortierte Listen</span><span class="sxs-lookup"><span data-stu-id="14d5c-161">Ordered lists</span></span>

<span data-ttu-id="14d5c-162">Um einen Absatz oder andere Elemente unter einer Aufzählung einzuschließen, richten Sie den Einzug am ersten Zeichen nach der Elementnummer aus.</span><span class="sxs-lookup"><span data-stu-id="14d5c-162">To include a paragraph or other elements under a numbered item, align indentation with the first character after the item number.</span></span> <span data-ttu-id="14d5c-163">Alle Elemente in einer Liste sollten die Nummer `1.` verwenden, statt jedes einzelne Element zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-163">All items in a numbered listed should use the number `1.` rather than incrementing each item.</span></span> <span data-ttu-id="14d5c-164">Beim Rendering erhöht Markdown den Wert automatisch.</span><span class="sxs-lookup"><span data-stu-id="14d5c-164">Markdown rendering increments the value automatically.</span></span> <span data-ttu-id="14d5c-165">Dadurch wird die Neuanordnung von Elementen vereinfacht und der Einzug von untergeordnetem Inhalt standardisiert.</span><span class="sxs-lookup"><span data-stu-id="14d5c-165">This makes reordering items easier and standardizes the indentation of subordinate content.</span></span>

<span data-ttu-id="14d5c-166">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="14d5c-166">For example:</span></span>

```markdown
1. For the first element, insert a single space after the 1. Long sentences should be
   wrapped to the next line and must line up with the first character after the numbered
   list marker.

   To include a second element (like this one), insert a line break after the first
   and align indentations. The indentation of the second element must line up with
   the first character after the numbered list marker. For single digit items, like
   this one, you indent to column 4. For double digits items, for example item number
   10, you indent to column 5.

1. The next numbered item starts here.
```

<span data-ttu-id="14d5c-167">Der resultierende Markdown wird wie folgt gerendert:</span><span class="sxs-lookup"><span data-stu-id="14d5c-167">The resulting Markdown is rendered as follows:</span></span>

1. <span data-ttu-id="14d5c-168">Fügen Sie für das erste Element ein einzelnes Leerzeichen nach der 1 ein.</span><span class="sxs-lookup"><span data-stu-id="14d5c-168">For the first element, insert a single space after the 1.</span></span> <span data-ttu-id="14d5c-169">Lange Sätze sollten in die nächste Zeile umbrochen werden und müssen am ersten Zeichen hinter dem nummerierten Listenmarker ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="14d5c-169">Long sentences should be wrapped to the next line and must line up with the first character after the numbered list marker.</span></span>

   <span data-ttu-id="14d5c-170">Um ein zweites Element (wie dieses hier) aufzuführen, fügen Sie nach dem ersten Element einen Zeilenumbruch ein, und richten Sie die Einzüge aus.</span><span class="sxs-lookup"><span data-stu-id="14d5c-170">To include a second element (like this one), insert a line break after the first and align indentations.</span></span> <span data-ttu-id="14d5c-171">Der Einzug des zweiten Elements muss am ersten Zeichen hinter dem nummerierten Listenmarker ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="14d5c-171">The indentation of the second element must line up with the first character after the numbered list marker.</span></span> <span data-ttu-id="14d5c-172">Für einstellige Elemente wie dieses ziehen Sie in Spalte 4 ein.</span><span class="sxs-lookup"><span data-stu-id="14d5c-172">For single digit items, like this one, you indent to column 4.</span></span> <span data-ttu-id="14d5c-173">Für zweistellige Elemente, beispielsweise die Elementnummer 10, ziehen Sie in Spalte 5 ein.</span><span class="sxs-lookup"><span data-stu-id="14d5c-173">For double digits items, for example item number 10, you indent to column 5.</span></span>

1. <span data-ttu-id="14d5c-174">Das nächste nummerierte Element beginnt hier.</span><span class="sxs-lookup"><span data-stu-id="14d5c-174">The next numbered item starts here.</span></span>

### <a name="formatting-command-syntax-elements"></a><span data-ttu-id="14d5c-175">Formatieren von Befehlssyntaxelementen</span><span class="sxs-lookup"><span data-stu-id="14d5c-175">Formatting command syntax elements</span></span>

- <span data-ttu-id="14d5c-176">Verwenden Sie immer den vollständigen Namen für Cmdlets und Parameter.</span><span class="sxs-lookup"><span data-stu-id="14d5c-176">Always use the full name for cmdlets and parameters.</span></span> <span data-ttu-id="14d5c-177">Vermeiden Sie die Verwendung von Aliasen, es sei denn, Sie möchten den Alias beispielhaft hervorheben.</span><span class="sxs-lookup"><span data-stu-id="14d5c-177">Avoid using aliases unless you are specifically demonstrating the alias.</span></span>

- <span data-ttu-id="14d5c-178">Innerhalb eines Absatzes sollten Schlüsselwörter der Sprache, Namen von Cmdlets, Variablen und Dateipfade in Graviszeichen (`` ` ``) eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="14d5c-178">Within a paragraph, language keywords, cmdlet names, variables, and file paths should be wrapped in backtick (`` ` ``) characters.</span></span> <span data-ttu-id="14d5c-179">Eigenschaften, Parameter und Klassennamen sollten **fett** formatiert sein.</span><span class="sxs-lookup"><span data-stu-id="14d5c-179">Property, parameter, and class names should be **bold**.</span></span>

  <span data-ttu-id="14d5c-180">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="14d5c-180">For example:</span></span>

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

- <span data-ttu-id="14d5c-181">Wenn Sie anhand des Namens auf einen Parameter verweisen, sollte der Name **fett** formatiert sein.</span><span class="sxs-lookup"><span data-stu-id="14d5c-181">When referring to a parameter by name, the name should be **bold**.</span></span> <span data-ttu-id="14d5c-182">Wenn Sie die Verwendung eines Parameters mit dem Bindestrichpräfix veranschaulichen, sollte der Parameter in Graviszeichen eingeschlossen sein.</span><span class="sxs-lookup"><span data-stu-id="14d5c-182">When illustrating the use of a parameter with the hyphen prefix, the parameter should be wrapped in backticks.</span></span> <span data-ttu-id="14d5c-183">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="14d5c-183">For example:</span></span>

  ```markdown
  The parameter's name is **Name**, but it is typed as `-Name` when used on the command
  line as a parameter.
  ```

- <span data-ttu-id="14d5c-184">Beim Verweis auf externe Befehle (EXEs, Skripts usw.) sollte der Befehlsname fett, ganz in Kleinbuchstaben (bzw. am Satzanfang mit großem erstem Buchstaben) geschrieben werden und die passende Dateierweiterung beinhalten.</span><span class="sxs-lookup"><span data-stu-id="14d5c-184">When referring to external commands (EXEs, scripts, etc.), the command name should be bold, all lowercase (or capitalized if at the beginning of a sentence), and include the appropriate file extension.</span></span> <span data-ttu-id="14d5c-185">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="14d5c-185">For example:</span></span>

  ```markdown
  For example, on Windows systems, you can use the `net start` and `net stop` commands
  to start and stop a service. **Sc.exe** is another service control tool for Windows.
  That name does not fit into the naming pattern for the **net.exe** service commands.
  ```

- <span data-ttu-id="14d5c-186">Bei der beispielhaften Verwendung eines externen Befehls sollte das Beispiel in Graviszeichen eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="14d5c-186">When showing example usage of an external command, the example should be wrapped in backticks.</span></span>
  <span data-ttu-id="14d5c-187">Bei bestehenden Namenskonflikten mit einem Alias müssen Sie die Dateierweiterung in das Befehlsbeispiel aufnehmen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-187">When there is a name collisions with an alias you must include the file extension in the command example.</span></span> <span data-ttu-id="14d5c-188">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="14d5c-188">For example:</span></span>

  ```markdown
  To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
  ```

- <span data-ttu-id="14d5c-189">Beim Schreiben eines konzeptionellen Artikels (im Gegensatz zu Referenzinhalt) sollte die erste Instanz eines Cmdlet-Namens per Link zur Dokumentation des Cmdlets verweisen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-189">When writing a conceptual article (as opposed to reference content), the first instance of a cmdlet name should be hyperlinked to the cmdlet documentation.</span></span> <span data-ttu-id="14d5c-190">Verwenden Sie innerhalb der Klammern eines Links keine Graviszeichen und fette oder sonstige Auszeichnung.</span><span class="sxs-lookup"><span data-stu-id="14d5c-190">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

  <span data-ttu-id="14d5c-191">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="14d5c-191">For example:</span></span>

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  <span data-ttu-id="14d5c-192">Weitere Informationen finden Sie im Abschnitt [Links](#hyperlinks) in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="14d5c-192">For more information, see [Hyperlinks](#hyperlinks) section of this article.</span></span>

### <a name="images"></a><span data-ttu-id="14d5c-193">Bilder</span><span class="sxs-lookup"><span data-stu-id="14d5c-193">Images</span></span>

<span data-ttu-id="14d5c-194">Die Syntax zum Einschließen eines Bilds lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="14d5c-194">The syntax to include an image is:</span></span>

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

<span data-ttu-id="14d5c-195">Dabei stellt `alt text` eine kurze Beschreibung des Bilds und `<folder path>` einen relativen Pfad zum Bild dar.</span><span class="sxs-lookup"><span data-stu-id="14d5c-195">Where `alt text` is a brief description of the image and `<folder path>` is a relative path to the image.</span></span> <span data-ttu-id="14d5c-196">Alternativtext ist für Bildschirmsprachausgaben für Personen mit eingeschränktem Sehvermögen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="14d5c-196">Alternate text is required for screen readers for the visually impaired.</span></span> <span data-ttu-id="14d5c-197">Er ist außerdem nützlich, falls das Bild aufgrund eines Bugs auf der Website nicht gerendert werden kann.</span><span class="sxs-lookup"><span data-stu-id="14d5c-197">It is also useful in case there is a site bug where the image cannot be rendered.</span></span>

<span data-ttu-id="14d5c-198">Bilder sollten in einem `media/<article-name>`-Ordner innerhalb des Ordners gespeichert werden, der den Artikel enthält.</span><span class="sxs-lookup"><span data-stu-id="14d5c-198">Images should be stored in a `media/<article-name>` folder within the folder containing the article.</span></span>
<span data-ttu-id="14d5c-199">Bilder sollten nicht von mehreren Artikeln gemeinsam genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="14d5c-199">Images should not be shared between articles.</span></span> <span data-ttu-id="14d5c-200">Erstellen Sie einen Ordner, der mit dem Dateinamen Ihres Artikels übereinstimmt, im `media`-Ordner.</span><span class="sxs-lookup"><span data-stu-id="14d5c-200">Create a folder that matches the filename of your article under the `media` folder.</span></span> <span data-ttu-id="14d5c-201">Kopieren Sie die Bilder für den Artikel in diesen neuen Ordner.</span><span class="sxs-lookup"><span data-stu-id="14d5c-201">Copy the images for that article to that new folder.</span></span> <span data-ttu-id="14d5c-202">Wenn ein Bild von mehreren Artikeln verwendet wird, muss jeder Bildordner eine Kopie der betreffenden Bilddatei aufweisen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-202">If an image is used by multiple articles, each image folder must have a copy of that image file.</span></span> <span data-ttu-id="14d5c-203">Diese Vorgehensweise verhindert, dass eine Änderung am Bild in einem Artikel sich auf andere Artikel auswirkt.</span><span class="sxs-lookup"><span data-stu-id="14d5c-203">This practice prevents a change to an image in one article affecting another article.</span></span>

<span data-ttu-id="14d5c-204">Die folgenden Bilddateitypen werden unterstützt: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span><span class="sxs-lookup"><span data-stu-id="14d5c-204">The following image file types are supported: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span></span>

### <a name="markdown-extensions-supported-by-open-publishing"></a><span data-ttu-id="14d5c-205">Von Open Publishing unterstützte Markdown-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="14d5c-205">Markdown extensions supported by Open Publishing</span></span>

<span data-ttu-id="14d5c-206">Das [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) (Erstellungspaket für Microsoft-Dokumentation) enthält Tools, die für unser Veröffentlichungssystem spezifische Features unterstützen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-206">The [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contains tools that support features unique to our publishing system.</span></span> <span data-ttu-id="14d5c-207">Alerts (Warnungen) sind eine Markdown-Erweiterung zum Erstellen von Blockquotes, die auf docs.microsoft.com mit Farben und Symbolen gerendert werden, die auf die Bedeutung des Inhalts hinweisen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-207">Alerts are a Markdown extension to create block quotes that render on docs.microsoft.com with colors and icons that indicate the significance of the content.</span></span> <span data-ttu-id="14d5c-208">Die folgenden Warnungstypen werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="14d5c-208">The following alert types are supported:</span></span>

```markdown
> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Essential information required for user success.

> [!CAUTION]
> Negative potential consequences of an action.

> [!WARNING]
> Dangerous certain consequences of an action.
```

<span data-ttu-id="14d5c-209">Diese Warnungen sehen auf docs.microsoft.com wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="14d5c-209">These alerts look like this on docs.microsoft.com:</span></span>

> [!NOTE]
> <span data-ttu-id="14d5c-210">Informationen, die der Benutzer selbst beim Durchblättern bemerken sollte.</span><span class="sxs-lookup"><span data-stu-id="14d5c-210">Information the user should notice even if skimming.</span></span>

> [!TIP]
> <span data-ttu-id="14d5c-211">Optionale Informationen, die einem Benutzer helfen sollen, erfolgreicher zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="14d5c-211">Optional information to help a user be more successful.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="14d5c-212">Wichtige Informationen, die für den Erfolg des Benutzers unabdingbar sind.</span><span class="sxs-lookup"><span data-stu-id="14d5c-212">Essential information required for user success.</span></span>

> [!CAUTION]
> <span data-ttu-id="14d5c-213">Negative potenzielle Folgen einer Aktion.</span><span class="sxs-lookup"><span data-stu-id="14d5c-213">Negative potential consequences of an action.</span></span>

> [!WARNING]
> <span data-ttu-id="14d5c-214">Bestimmte gefährliche Folgen einer Aktion.</span><span class="sxs-lookup"><span data-stu-id="14d5c-214">Dangerous certain consequences of an action.</span></span>

## <a name="hyperlinks"></a><span data-ttu-id="14d5c-215">Links</span><span class="sxs-lookup"><span data-stu-id="14d5c-215">Hyperlinks</span></span>

- <span data-ttu-id="14d5c-216">Vermeiden Sie die Verwendung von unformatierten URLs.</span><span class="sxs-lookup"><span data-stu-id="14d5c-216">Avoid using bare URLs.</span></span> <span data-ttu-id="14d5c-217">Links sollten die Markdownsyntax `[friendlyname](url-or-path)` verwenden</span><span class="sxs-lookup"><span data-stu-id="14d5c-217">Links should use Markdown syntax `[friendlyname](url-or-path)`</span></span>
- <span data-ttu-id="14d5c-218">Unformatierte URLs dürfen verwendet werden, wenn es erforderlich ist, sollten aber in Graviszeichen eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="14d5c-218">Bare URLs may be used when necessary, but should be enclosed in backticks.</span></span> <span data-ttu-id="14d5c-219">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="14d5c-219">For example:</span></span>

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

- <span data-ttu-id="14d5c-220">URL-Links sollten nach Möglichkeit als HTTPS angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="14d5c-220">URL links should be HTTPS when possible.</span></span>
- <span data-ttu-id="14d5c-221">Links müssen über einen Anzeigenamen verfügen, normalerweise den Titel des verknüpften Themas</span><span class="sxs-lookup"><span data-stu-id="14d5c-221">Links must have a friendly name, usually the title of the linked topic</span></span>
- <span data-ttu-id="14d5c-222">Alle Elemente im Abschnitt „Verwandte Links“ am unteren Rand sollten mit einem Link versehen sein.</span><span class="sxs-lookup"><span data-stu-id="14d5c-222">All items in the "related links" section at the bottom should be hyperlinked.</span></span>
- <span data-ttu-id="14d5c-223">Verwenden Sie innerhalb der Klammern eines Links keine Graviszeichen und fette oder sonstige Auszeichnung.</span><span class="sxs-lookup"><span data-stu-id="14d5c-223">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

### <a name="linking-to-other-content"></a><span data-ttu-id="14d5c-224">Verknüpfen mit anderen Inhalten</span><span class="sxs-lookup"><span data-stu-id="14d5c-224">Linking to other content</span></span>

<span data-ttu-id="14d5c-225">Das Veröffentlichungssystem unterstützt zwei Arten von Links: URLs und Dateiverknüpfungen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-225">There are two types of hyperlinks supported by the publishing system: URLs and file links.</span></span>

<span data-ttu-id="14d5c-226">Ein URL-Link kann ein URL-Pfad sein, der relativ zum Stamm von docs.microsoft.com ist.</span><span class="sxs-lookup"><span data-stu-id="14d5c-226">A URL link can be a URL path that is relative to the root of docs.microsoft.com.</span></span> <span data-ttu-id="14d5c-227">Oder eine absolute URL, die die vollständige URL-Syntax enthält.</span><span class="sxs-lookup"><span data-stu-id="14d5c-227">Or an absolute URL that include the full URL syntax.</span></span> <span data-ttu-id="14d5c-228">(Beispiel: `https:/github.com/MicrosoftDocs/PowerShell-Docs`)</span><span class="sxs-lookup"><span data-stu-id="14d5c-228">(For example: `https:/github.com/MicrosoftDocs/PowerShell-Docs`)</span></span>

- <span data-ttu-id="14d5c-229">Verwenden Sie URL-Links für die Verknüpfung mit Inhalten außerhalb der PowerShell-Dokumentation oder zwischen der Cmdlet-Referenz und konzeptionellen Artikeln innerhalb der PowerShell-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="14d5c-229">Use URL links when linking to content outside of PowerShell-Docs or between cmdlet reference and conceptual articles within PowerShell-docs.</span></span>
- <span data-ttu-id="14d5c-230">Die einfachste Möglichkeit zum Erstellen eines relativen Links besteht darin, die URL aus Ihrem Browser zu kopieren und dann `https://docs.microsoft.com/en-us` aus dem Wert zu entfernen, den Sie in Markdown einfügen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-230">The simplest way to link create a relative link is to copy the URL from your browser then remove `https://docs.microsoft.com/en-us` from the value you paste into markdown.</span></span>
   - <span data-ttu-id="14d5c-231">Schließen Sie keine Gebietsschemas in URLs in Microsoft-Eigenschaften ein (entfernen Sie beispielsweise</span><span class="sxs-lookup"><span data-stu-id="14d5c-231">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="14d5c-232">„/en-US“ aus der URL).</span><span class="sxs-lookup"><span data-stu-id="14d5c-232">remove "/en-us" from URL).</span></span>
- <span data-ttu-id="14d5c-233">Alle URLs zu externen Websites sollten HTTPS verwenden, es sei denn, dies ist für die Zielwebsite ungültig.</span><span class="sxs-lookup"><span data-stu-id="14d5c-233">All URLs to external websites should use HTTPS unless that is not valid for the target site.</span></span>

<span data-ttu-id="14d5c-234">Eine Dateiverknüpfung wird verwendet, um von einem Referenzartikel auf einen anderen oder von einem konzeptionellen Artikel auf einen anderen zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-234">A file link is used to link from one reference article to another, or from one conceptual article to another.</span></span> <span data-ttu-id="14d5c-235">Wenn Sie auf einen Referenzartikel für eine bestimmte Version von PowerShell verweisen müssen, müssen Sie einen URL-Link verwenden.</span><span class="sxs-lookup"><span data-stu-id="14d5c-235">If you need to link to a reference article for a specific version of PowerShell, then you need to use a URL link.</span></span>

- <span data-ttu-id="14d5c-236">Dateiverknüpfungen enthalten einen relativen Dateipfad (Beispiel: `../folder/file.md`)</span><span class="sxs-lookup"><span data-stu-id="14d5c-236">File links contain a relative file path (for example: `../folder/file.md`)</span></span>
- <span data-ttu-id="14d5c-237">Alle Dateipfade enthalten Schrägstriche (`/`).</span><span class="sxs-lookup"><span data-stu-id="14d5c-237">All file paths use forward-slash (`/`) characters</span></span>

## <a name="formatting-code-samples"></a><span data-ttu-id="14d5c-238">Formatieren von Codebeispielen</span><span class="sxs-lookup"><span data-stu-id="14d5c-238">Formatting code samples</span></span>

<span data-ttu-id="14d5c-239">Markdown unterstützt zwei verschiedene Codeformatvorlagen:</span><span class="sxs-lookup"><span data-stu-id="14d5c-239">Markdown supports two different code styles:</span></span>

- <span data-ttu-id="14d5c-240">Codestrecken (inline): durch ein einzelnes Graviszeichen (`` ` ``) gekennzeichnet.</span><span class="sxs-lookup"><span data-stu-id="14d5c-240">Code spans (inline) - marked by a single backtick (`` ` ``) character.</span></span> <span data-ttu-id="14d5c-241">Wird innerhalb eines Absatzes anstelle eines eigenständigen Blocks verwendet.</span><span class="sxs-lookup"><span data-stu-id="14d5c-241">Used within a paragraph rather than as a standalone block.</span></span>
- <span data-ttu-id="14d5c-242">Codeblöcke: ein mehrzeiliger Block, der in dreifache Graviszeichen-Zeichenfolgen (`` ``` ``) eingeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="14d5c-242">Code blocks - a multi-line block surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="14d5c-243">Codeblöcke können außerdem über eine Sprachbezeichnung im Anschluss an die Graviszeichen verfügen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-243">Code blocks may also have a language label following the backticks.</span></span> <span data-ttu-id="14d5c-244">Die Sprachbezeichnung ermöglicht Syntaxhervorhebung für die Inhalte des Codeblocks.</span><span class="sxs-lookup"><span data-stu-id="14d5c-244">The language label enables syntax highlighting for the contents of the code block.</span></span>

### <a name="using-code-blocks"></a><span data-ttu-id="14d5c-245">Verwenden von Codeblöcken</span><span class="sxs-lookup"><span data-stu-id="14d5c-245">Using code blocks</span></span>

<span data-ttu-id="14d5c-246">Markdown ermöglicht Einzüge zum Kennzeichnen eines Codeblocks, dieses Muster kann jedoch problematisch sein und sollte vermieden werden.</span><span class="sxs-lookup"><span data-stu-id="14d5c-246">Markdown allows for indentation to signify a code block, but this pattern can be problematic and should be avoided.</span></span> <span data-ttu-id="14d5c-247">Alle Codeblöcke sollten in einem abgesetzten Codebereich (Code Fence) enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="14d5c-247">All code blocks should be contained in a code fence.</span></span> <span data-ttu-id="14d5c-248">Ein Codebereich ist ein Block von Code, der in dreifache Graviszeichen-Zeichenfolgen (`` ``` ``) eingeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="14d5c-248">A code fence is a block of code surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="14d5c-249">Die Codebereichsmarkierungen müssen in einer eigenen Zeile vor und nach dem Codebeispiel stehen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-249">The code fence markers must be on their own line before and after the code sample.</span></span> <span data-ttu-id="14d5c-250">Der Marker am Beginn des Codeblocks darf eine optionale Sprachbezeichnung aufweisen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-250">The marker at the start of the code block may have an optional language label.</span></span> <span data-ttu-id="14d5c-251">Das Open Publishing System (OPS) von Microsoft verwendet die Sprachbezeichnung zur Unterstützung der Syntaxhervorhebungsfunktion.</span><span class="sxs-lookup"><span data-stu-id="14d5c-251">Microsoft's Open Publishing System (OPS) uses the language label to support the syntax highlighting feature.</span></span>

<span data-ttu-id="14d5c-252">OPS fügt außerdem eine Schaltfläche **Kopieren** hinzu, die die Inhalte des Codeblocks in die Zwischenablage kopiert.</span><span class="sxs-lookup"><span data-stu-id="14d5c-252">OPS also adds a **Copy** button that copies the contents of the code block to the clipboard.</span></span> <span data-ttu-id="14d5c-253">Dies ermöglicht es Ihnen, den Code schnell in ein Skript einzufügen, um das Codebeispiel zu testen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-253">This allows you to quickly paste the code into a script for testing the code example.</span></span> <span data-ttu-id="14d5c-254">Allerdings sind nicht alle Beispiele in unserer Dokumentation dafür bestimmt, ausgeführt zu werden.</span><span class="sxs-lookup"><span data-stu-id="14d5c-254">However, not all examples in our documentation are intended to be run.</span></span> <span data-ttu-id="14d5c-255">Einige Codeblöcke sind einfache Abbildungen eines PowerShell-Konzepts.</span><span class="sxs-lookup"><span data-stu-id="14d5c-255">Some code blocks are simple illustrations of a PowerShell concept.</span></span>

<span data-ttu-id="14d5c-256">In unserer Dokumentation werden zwei Arten von Codeblöcken verwendet:</span><span class="sxs-lookup"><span data-stu-id="14d5c-256">There are two types code blocks used in our documentation:</span></span>

1. <span data-ttu-id="14d5c-257">Anschauliche Beispiele</span><span class="sxs-lookup"><span data-stu-id="14d5c-257">Illustrative examples</span></span>
2. <span data-ttu-id="14d5c-258">Ausführbare Beispiele</span><span class="sxs-lookup"><span data-stu-id="14d5c-258">Executable examples</span></span>

### <a name="syntax-code-blocks"></a><span data-ttu-id="14d5c-259">Syntaxcodeblöcke</span><span class="sxs-lookup"><span data-stu-id="14d5c-259">Syntax code blocks</span></span>

<span data-ttu-id="14d5c-260">Dieses Beispiel veranschaulicht alle möglichen Parameter des `Get-Command`-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="14d5c-260">This example illustrates all the possible parameters of the `Get-Command` cmdlet.</span></span>

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
  [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
  [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

<span data-ttu-id="14d5c-261">Dieses Beispiel beschreibt die `for`-Anweisungen allgemein:</span><span class="sxs-lookup"><span data-stu-id="14d5c-261">This example describes the `for` statement in generalized terms:</span></span>

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a><span data-ttu-id="14d5c-262">Anschauliche Beispiele</span><span class="sxs-lookup"><span data-stu-id="14d5c-262">Illustrative examples</span></span>

<span data-ttu-id="14d5c-263">Anschauliche Beispiele werden verwendet, um ein PowerShell-Konzept zu erläutern.</span><span class="sxs-lookup"><span data-stu-id="14d5c-263">Illustrative examples are used to explain a PowerShell concept.</span></span> <span data-ttu-id="14d5c-264">Sie sind nicht dazu bestimmt, zur Ausführung in die Zwischenablage kopiert zu werden.</span><span class="sxs-lookup"><span data-stu-id="14d5c-264">They are not meant to be copied to the clipboard for execution.</span></span> <span data-ttu-id="14d5c-265">Diese werden am häufigsten für einfache Beispiele verwendet, die sich leicht eingeben lassen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-265">These are most commonly used for simple examples that are easy to type.</span></span>
<span data-ttu-id="14d5c-266">Sie werden außerdem für Syntaxbeispiele verwendet, mit denen Sie die Syntax eines Befehls veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-266">They are also used for syntax examples where you are illustrating the syntax of a command.</span></span> <span data-ttu-id="14d5c-267">Der Codeblock kann auch Beispielausgabe des veranschaulichten Befehls enthalten.</span><span class="sxs-lookup"><span data-stu-id="14d5c-267">The code block may contain example output from the command being illustrated.</span></span>

<span data-ttu-id="14d5c-268">Hier ist ein einfaches Beispiel, das einen PowerShell-Vergleichsoperator veranschaulicht:</span><span class="sxs-lookup"><span data-stu-id="14d5c-268">Here is a simple example illustrating a PowerShell comparison operators:</span></span>

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS>  1,2,3 -eq 2
2

PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```
~~~

<span data-ttu-id="14d5c-269">Beachten Sie, dass in diesem Beispiel die vereinfachte PowerShell-Eingabeaufforderung und die resultierende Ausgabe dargestellt sind.</span><span class="sxs-lookup"><span data-stu-id="14d5c-269">Note that this example has the simplified PowerShell prompt and shows the resulting output.</span></span> <span data-ttu-id="14d5c-270">In diesem Fall wollen wir nicht, dass der Leser das Beispiel kopiert und ausführt.</span><span class="sxs-lookup"><span data-stu-id="14d5c-270">In this case, we don't intend the reader to copy and run this example.</span></span>

### <a name="executable-examples"></a><span data-ttu-id="14d5c-271">Ausführbare Beispiele</span><span class="sxs-lookup"><span data-stu-id="14d5c-271">Executable examples</span></span>

<span data-ttu-id="14d5c-272">Komplexere Beispiele oder Beispiele, die für ein sinnvolles Kopieren und Ausführen erstellt wurden, sollten das folgende Markup als Blockformatvorlage verwenden:</span><span class="sxs-lookup"><span data-stu-id="14d5c-272">More complex examples or examples that are intended to be useful to copy and execute should use the following block-style markup:</span></span>

~~~markdown
```powershell
<PowerShell code goes here>
```
~~~

<span data-ttu-id="14d5c-273">Die von PowerShell-Befehlen angezeigte Ausgabe sollte in einen **Output**-Codeblock eingeschlossen werden, um Syntaxhervorhebung zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="14d5c-273">The output displayed by PowerShell commands should be enclosed in an **Output** code block to prevent syntax highlighting.</span></span> <span data-ttu-id="14d5c-274">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="14d5c-274">For example:</span></span>

~~~markdown
```powershell
Get-Command -Module Microsoft.PowerShell.Security
```

```Output
CommandType  Name                        Version    Source
-----------  ----                        -------    ------
Cmdlet       ConvertFrom-SecureString    3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       ConvertTo-SecureString      3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-CmsMessage              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Credential              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-PfxCertificate          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       New-FileCatalog             3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Protect-CmsMessage          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Test-FileCatalog            3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Unprotect-CmsMessage        3.0.0.0    Microsoft.PowerShell.Security
```
~~~

<span data-ttu-id="14d5c-275">Die **Output**-Codebezeichnung ist keine offizielle „Sprache“, die vom Syntaxhervorhebungs-System unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="14d5c-275">The **Output** code label is not an official "language" supported by the syntax highlighting system.</span></span>
<span data-ttu-id="14d5c-276">Diese Bezeichnung ist jedoch nützlich, da OPS dem Rahmen des Codefelds auf der Website die Bezeichnung „Output“ hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="14d5c-276">However, this label is useful because OPS adds the "Output" label to the code box frame on the web page.</span></span> <span data-ttu-id="14d5c-277">Das „Output“-Codefeld hat keine Syntaxhervorhebung.</span><span class="sxs-lookup"><span data-stu-id="14d5c-277">The "Output" code box has no syntax highlighting.</span></span>

## <a name="coding-style-rules"></a><span data-ttu-id="14d5c-278">Regeln für Codeformatvorlagen</span><span class="sxs-lookup"><span data-stu-id="14d5c-278">Coding style rules</span></span>

### <a name="avoid-line-continuation-in-code-samples"></a><span data-ttu-id="14d5c-279">Vermeiden Sie Zeilenfortsetzung in Codebeispielen</span><span class="sxs-lookup"><span data-stu-id="14d5c-279">Avoid line continuation in code samples</span></span>

<span data-ttu-id="14d5c-280">Vermeiden Sie die Verwendung von Zeilenfortsetzungszeichen (`` ` ``) in PowerShell-Codebeispielen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-280">Avoid using line continuation characters (`` ` ``) in PowerShell code examples.</span></span> <span data-ttu-id="14d5c-281">Sie sind schlecht zu sehen und können zu Problemen führen, wenn am Zeilenende zusätzliche Leerzeichen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="14d5c-281">These are hard to see and can cause problems if there are extra spaces at the end of the line.</span></span>

- <span data-ttu-id="14d5c-282">Verwenden Sie PowerShell-Aufteilung, um die Zeilenlänge für Cmdlets zu reduzieren, die viele Parameter aufweisen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-282">Use PowerShell splatting to reduce line length for cmdlets that have a lot of parameters.</span></span>
- <span data-ttu-id="14d5c-283">Nutzen Sie die natürlichen Gelegenheiten für Zeilenumbrüche in PowerShell, etwa nach Pipesymbolen (`|`), öffnenden geschweiften Klammern, Klammern und eckigen Klammern.</span><span class="sxs-lookup"><span data-stu-id="14d5c-283">Take advantage of PowerShell's natural line break opportunities, like after pipe (`|`) characters, opening braces, parentheses, and brackets.</span></span>

### <a name="avoid-using-powershell-prompts-in-examples"></a><span data-ttu-id="14d5c-284">Vermeiden Sie die Verwendung von PowerShell-Eingabeaufforderungen in Beispielen</span><span class="sxs-lookup"><span data-stu-id="14d5c-284">Avoid using PowerShell prompts in examples</span></span>

<span data-ttu-id="14d5c-285">Von der Verwendung der Eingabeaufforderungs-Zeichenfolge wird abgeraten. Sie sollte auf Fälle beschränkt werden, deren Zweck die Veranschaulichung der Befehlszeilensyntax ist.</span><span class="sxs-lookup"><span data-stu-id="14d5c-285">Use of the prompt string is discouraged and should be limited to scenarios that are meant to illustrate command line usage.</span></span> <span data-ttu-id="14d5c-286">Für die meisten dieser Beispiele sollte die Eingabeaufforderungs-Zeichenfolge `PS>` lauten.</span><span class="sxs-lookup"><span data-stu-id="14d5c-286">For most of these examples, the prompt string should be `PS>`.</span></span> <span data-ttu-id="14d5c-287">Diese Eingabeaufforderung ist unabhängig von betriebssystemspezifischen Indikatoren.</span><span class="sxs-lookup"><span data-stu-id="14d5c-287">This prompt is independent of OS-specific indicators.</span></span>

<span data-ttu-id="14d5c-288">Eingabeaufforderungen sind für Beispiele erforderlich, die Befehle veranschaulichen, mit denen die Eingabeaufforderung geändert wird, oder wenn der angezeigte Pfad für das dargestellte Szenario relevant ist.</span><span class="sxs-lookup"><span data-stu-id="14d5c-288">Prompts are required for examples that illustrate commands that alter the prompt or when the path displayed is significant to the scenario being illustrated.</span></span> <span data-ttu-id="14d5c-289">Das folgende Beispiel zeigt, wie sich die Eingabeaufforderung ändert, wenn der Registrierungsanbieter verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="14d5c-289">The following example illustrates how the prompt changes when using the Registry provider.</span></span>

```powershell
PS C:\> cd HKCU:\System\
PS HKCU:\System\> dir

    Hive: HKEY_CURRENT_USER\System

Name                   Property
----                   --------
CurrentControlSet
GameConfigStore        GameDVR_Enabled                       : 1
                       GameDVR_FSEBehaviorMode               : 2
                       Win32_AutoGameModeDefaultProfile      : {2, 0, 1, 0...}
                       Win32_GameModeRelatedProcesses        : {1, 0, 1, 0...}
                       GameDVR_HonorUserFSEBehaviorMode      : 0
                       GameDVR_DXGIHonorFSEWindowsCompatible : 0
```

### <a name="do-not-use-aliases-in-examples"></a><span data-ttu-id="14d5c-290">Verwenden Sie keine Aliase in Beispielen</span><span class="sxs-lookup"><span data-stu-id="14d5c-290">Do not use aliases in examples</span></span>

<span data-ttu-id="14d5c-291">Sie sollten für alle Cmdlets und Parameter immer den vollständigen Namen verwenden, es sei denn, Sie behandeln speziell den Alias.</span><span class="sxs-lookup"><span data-stu-id="14d5c-291">You should always use the full name of all cmdlets and parameters unless you are specifically talking about the alias.</span></span> <span data-ttu-id="14d5c-292">Namen von Cmdlets und Parametern müssen die richtige, im Code definierte Schreibweise verwenden.</span><span class="sxs-lookup"><span data-stu-id="14d5c-292">Cmdlet and parameter names must use the proper spelling defined in the code.</span></span>

### <a name="using-parameters-in-examples"></a><span data-ttu-id="14d5c-293">Verwenden von Parametern in Beispielen</span><span class="sxs-lookup"><span data-stu-id="14d5c-293">Using parameters in examples</span></span>

<span data-ttu-id="14d5c-294">Vermeiden Sie die Verwendung von Positionsparametern.</span><span class="sxs-lookup"><span data-stu-id="14d5c-294">Avoid using positional parameters.</span></span> <span data-ttu-id="14d5c-295">Im Allgemeinen sollten Sie immer den Parameternamen in ein Beispiel aufnehmen, auch bei Positionsparametern.</span><span class="sxs-lookup"><span data-stu-id="14d5c-295">In general, you should use always include the parameter name in an example, even if the parameter positional.</span></span> <span data-ttu-id="14d5c-296">Dies verringert die Gefahr von Missverständnissen in Ihren Beispielen.</span><span class="sxs-lookup"><span data-stu-id="14d5c-296">This reduces the chance of confusion in your examples.</span></span>

## <a name="next-steps"></a><span data-ttu-id="14d5c-297">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="14d5c-297">Next steps</span></span>

[<span data-ttu-id="14d5c-298">Bearbeiten der Cmdlet-Referenz</span><span class="sxs-lookup"><span data-stu-id="14d5c-298">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
