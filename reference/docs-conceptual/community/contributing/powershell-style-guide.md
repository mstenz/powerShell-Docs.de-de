---
title: Styleguide für die PowerShell-Dokumentation
description: Dieser Artikel enthält die Stilregeln für das Schreiben von PowerShell-Dokumentation.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: b60ad9a4965e75cc5f68309604f1893e5757f351
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83690849"
---
# <a name="powershell-docs-style-guide"></a><span data-ttu-id="7c92b-103">Styleguide für die PowerShell-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="7c92b-103">PowerShell-Docs style guide</span></span>

<span data-ttu-id="7c92b-104">Dieser Artikel enthält die spezifischen Stilanweisungen für Inhalte der PowerShell-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="7c92b-104">This article provides style guidance specific to the PowerShell-Docs content.</span></span> <span data-ttu-id="7c92b-105">Dies geschieht ausgehend von den in der [Übersicht](overview.md#get-started-writing-docs) beschriebenen Informationen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-105">This builds on the information outlined in the [Overview](overview.md#get-started-writing-docs).</span></span>

## <a name="product-terminology"></a><span data-ttu-id="7c92b-106">Produktterminologie</span><span class="sxs-lookup"><span data-stu-id="7c92b-106">Product Terminology</span></span>

<span data-ttu-id="7c92b-107">Es gibt mehrere Varianten von PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7c92b-107">There are several variants of PowerShell.</span></span>

- <span data-ttu-id="7c92b-108">**PowerShell**: Dies ist die Standardvariante.</span><span class="sxs-lookup"><span data-stu-id="7c92b-108">**PowerShell** - This is the default.</span></span> <span data-ttu-id="7c92b-109">Wir sehen im weiteren Verlauf PowerShell 7 und höhere Versionen als das eine echte PowerShell an.</span><span class="sxs-lookup"><span data-stu-id="7c92b-109">We consider PowerShell 7 and beyond to be the one, true PowerShell going forward.</span></span>
- <span data-ttu-id="7c92b-110">**PowerShell Core-** : PowerShell basierend auf .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7c92b-110">**PowerShell Core** - PowerShell built on .NET Core.</span></span> <span data-ttu-id="7c92b-111">Die Verwendung des Begriffs **Core** sollte auf Fälle beschränkt sein, in denen die Unterscheidung von Windows PowerShell erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="7c92b-111">Usage of the term **Core** should be limited to cases where it is necessary to differentiate it from Windows PowerShell.</span></span>
- <span data-ttu-id="7c92b-112">**Windows PowerShell**:- PowerShell basierend auf .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7c92b-112">**Windows PowerShell** - PowerShell built on .NET Framework.</span></span> <span data-ttu-id="7c92b-113">Windows PowerShell wird nur für Windows ausgeliefert und erfordert das gesamte Framework.</span><span class="sxs-lookup"><span data-stu-id="7c92b-113">Windows PowerShell ships only on Windows and requires the complete Framework.</span></span>

  <span data-ttu-id="7c92b-114">Im Allgemeinen können Verweise auf „Windows PowerShell“ in der Dokumentation zu „PowerShell“ geändert werden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-114">In general, references to "Windows PowerShell" in documentation can be changed to "PowerShell".</span></span>
  <span data-ttu-id="7c92b-115">„Windows PowerShell“ sollte verwendet werden, wenn Windows PowerShell-spezifisches Verhalten beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="7c92b-115">"Windows PowerShell" should be used when "Windows PowerShell"-specific behavior is being discussed.</span></span>

<span data-ttu-id="7c92b-116">Verwandte Produkte</span><span class="sxs-lookup"><span data-stu-id="7c92b-116">Related products</span></span>

- <span data-ttu-id="7c92b-117">**Visual Studio Code (VS Code)** : Dies ist der kostenlose Open Source-Editor von Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7c92b-117">**Visual Studio Code (VS Code)** - This is Microsoft's free, open source editor.</span></span> <span data-ttu-id="7c92b-118">Bei der ersten Erwähnung sollte der vollständige Name verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-118">At first mention, the full name should be used.</span></span> <span data-ttu-id="7c92b-119">Anschließend können Sie **VS Code** verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-119">After that you may use **VS Code**.</span></span> <span data-ttu-id="7c92b-120">Verwenden Sie nicht „VSCode“.</span><span class="sxs-lookup"><span data-stu-id="7c92b-120">Do not use "VSCode".</span></span>
- <span data-ttu-id="7c92b-121">**PowerShell-Erweiterung für Visual Studio Code**: Mit dieser Erweiterung wird VS Code in die bevorzugte IDE für PowerShell umgewandelt.</span><span class="sxs-lookup"><span data-stu-id="7c92b-121">**PowerShell Extension for Visual Studio Code** - The extension turns VS Code into the preferred IDE for PowerShell.</span></span> <span data-ttu-id="7c92b-122">Bei der ersten Erwähnung sollte der vollständige Name verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-122">At first mention, the full name should be used.</span></span> <span data-ttu-id="7c92b-123">Anschließend können Sie **PowerShell-Erweiterung** verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-123">After that you may use **PowerShell extension**.</span></span>
- <span data-ttu-id="7c92b-124">**Azure PowerShell**: Dies ist die Sammlung von PowerShell-Modulen, mit denen Azure-Dienste verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-124">**Azure PowerShell** - This is the collection of PowerShell modules used to manage Azure services.</span></span>
- <span data-ttu-id="7c92b-125">**Azure PowerShell**: Dies ist die Sammlung von PowerShell-Modulen, mit denen die Hybrid Cloud-Lösung von Microsoft verwaltet wird.</span><span class="sxs-lookup"><span data-stu-id="7c92b-125">**Azure Stack PowerShell** - This is the collection of PowerShell modules used to manage Microsoft's hybrid cloud solution.</span></span>

## <a name="markdown-specifics"></a><span data-ttu-id="7c92b-126">Besonderheiten von Markdown</span><span class="sxs-lookup"><span data-stu-id="7c92b-126">Markdown specifics</span></span>

<span data-ttu-id="7c92b-127">Das Microsoft Open Publishing System (OPS), mit dem unsere Dokumentation erstellt wird, verwendet [markdig][], um die Markdown-Dokumente zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="7c92b-127">The Microsoft Open Publishing System (OPS) that builds our documentation uses [markdig][] to process the Markdown documents.</span></span> <span data-ttu-id="7c92b-128">Markdig analysiert die Dokumente auf der Grundlage der Regeln der aktuellen [CommonMark][]-Spezifikation.</span><span class="sxs-lookup"><span data-stu-id="7c92b-128">Markdig parses the documents based on the rules of the latest [CommonMark][] specification.</span></span>

<span data-ttu-id="7c92b-129">Die neue CommonMark-Spezifikation ist weitaus strenger im Hinblick auf den Aufbau einiger Markdown-Elemente.</span><span class="sxs-lookup"><span data-stu-id="7c92b-129">The new CommonMark spec is much stricter about the construction of some Markdown elements.</span></span> <span data-ttu-id="7c92b-130">Beachten Sie die Detailinformationen in diesem Dokument genau.</span><span class="sxs-lookup"><span data-stu-id="7c92b-130">Pay close attention to the details provided in this document.</span></span>

### <a name="blank-lines-spaces-and-tabs"></a><span data-ttu-id="7c92b-131">Leerzeilen, Leerzeichen und Tabstoppzeichen</span><span class="sxs-lookup"><span data-stu-id="7c92b-131">Blank lines, spaces, and tabs</span></span>

<span data-ttu-id="7c92b-132">Leerzeilen signalisieren darüber hinaus in Markdown das Ende eines Blocks.</span><span class="sxs-lookup"><span data-stu-id="7c92b-132">Blank lines also signal the end of a block in Markdown.</span></span> <span data-ttu-id="7c92b-133">Zwischen Markdown-Blöcken unterschiedlicher Typen (z. B. zwischen einem Absatz und einer Liste oder einem Header) sollte eine einzelne Leerzeile stehen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-133">There should be a single blank between Markdown blocks of different types (for example, between a paragraph and a list or header).</span></span>

<span data-ttu-id="7c92b-134">Entfernen Sie doppelte Leerzeilen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-134">Remove duplicate blank lines.</span></span> <span data-ttu-id="7c92b-135">Mehrere Leerzeilen werden in HTML als eine einzelne Leerzeile dargestellt, das Einfügen oder Vorhandensein mehrerer Leerzeilen dient also keinem Zweck.</span><span class="sxs-lookup"><span data-stu-id="7c92b-135">Multiple blank lines render as a single blank line in HTML so there is no purpose for multiple blank lines.</span></span> <span data-ttu-id="7c92b-136">Mehrere Leerzeilen innerhalb eines Codeblocks haben zur Folge, dass der Code nicht funktioniert.</span><span class="sxs-lookup"><span data-stu-id="7c92b-136">Multiple blank lines within a code block break the code block.</span></span>

<span data-ttu-id="7c92b-137">Entfernen Sie zusätzliche Leerzeichen am Zeilenende.</span><span class="sxs-lookup"><span data-stu-id="7c92b-137">Remove extra spaces at the end of lines.</span></span>

> [!NOTE]
> <span data-ttu-id="7c92b-138">Abstände sind in Markdown wichtig.</span><span class="sxs-lookup"><span data-stu-id="7c92b-138">Spacing is significant in Markdown.</span></span> <span data-ttu-id="7c92b-139">Verwenden Sie immer Leerzeichen anstelle harter Tabstoppzeichen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-139">Always uses spaces instead of hard tabs.</span></span> <span data-ttu-id="7c92b-140">Nachgestellte Leerzeichen können sich auf das Rendern von Markdown auswirken.</span><span class="sxs-lookup"><span data-stu-id="7c92b-140">Trailing spaces can change how Markdown renders.</span></span>

### <a name="titles-and-headings"></a><span data-ttu-id="7c92b-141">Titel und Überschriften</span><span class="sxs-lookup"><span data-stu-id="7c92b-141">Titles and headings</span></span>

<span data-ttu-id="7c92b-142">Verwenden Sie nur [ATX-Überschriften][atx] (#-Formatvorlage, im Gegensatz zu Überschriften der `=`- oder `-`-Formatvorlagen).</span><span class="sxs-lookup"><span data-stu-id="7c92b-142">Only use [ATX headings][atx] (# style, as opposed to `=` or `-` style headers).</span></span>

- <span data-ttu-id="7c92b-143">Verwenden Sie normale Groß-/Kleinschreibung – nur Eigennamen und der erste Buchstabe eines Titels oder einer Überschrift sollten groß geschrieben werden</span><span class="sxs-lookup"><span data-stu-id="7c92b-143">Use sentence case - only proper nouns and the first letter of a title or header should be capitalized</span></span>
- <span data-ttu-id="7c92b-144">Zwischen dem `#` und dem ersten Buchstaben des Titels muss ein einfaches Leerzeichen stehen</span><span class="sxs-lookup"><span data-stu-id="7c92b-144">There must be a single space between the `#` and the first letter of the heading</span></span>
- <span data-ttu-id="7c92b-145">Überschriften sollten von einer einzelnen Leerzeile umgeben sein</span><span class="sxs-lookup"><span data-stu-id="7c92b-145">Headings should be surrounded by a single blank line</span></span>
- <span data-ttu-id="7c92b-146">Nur eine Überschrift der Ebene H1 pro Dokument</span><span class="sxs-lookup"><span data-stu-id="7c92b-146">Only one H1 per document</span></span>
- <span data-ttu-id="7c92b-147">Überschriftebenen sollten um 1 erhöht werden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-147">Header levels should increment by one.</span></span> <span data-ttu-id="7c92b-148">Überspringen Sie keine Ebenen</span><span class="sxs-lookup"><span data-stu-id="7c92b-148">Do not skip levels</span></span>
- <span data-ttu-id="7c92b-149">Verwenden Sie keine fette oder sonstige Auszeichnung in Überschriften</span><span class="sxs-lookup"><span data-stu-id="7c92b-149">Do not use bold or other markup in headers</span></span>

### <a name="limit-line-length-to-100-characters"></a><span data-ttu-id="7c92b-150">Begrenzen Sie die Zeilenlänge auf 100 Zeichen</span><span class="sxs-lookup"><span data-stu-id="7c92b-150">Limit line length to 100 characters</span></span>

<span data-ttu-id="7c92b-151">Dies gilt für konzeptionelle Artikel und die Cmdlet-Referenz.</span><span class="sxs-lookup"><span data-stu-id="7c92b-151">This applies to conceptual articles and cmdlet reference.</span></span> <span data-ttu-id="7c92b-152">Das Beschränken der Zeilenlänge verbessert die Lesbarkeit von git-Diffs und git-Verlauf.</span><span class="sxs-lookup"><span data-stu-id="7c92b-152">Limiting the line length improves the readability of git diffs and history.</span></span> <span data-ttu-id="7c92b-153">Es erleichtert außerdem anderen Autoren das Einbringen ihres Beitrags.</span><span class="sxs-lookup"><span data-stu-id="7c92b-153">It also makes it easier for other writers to make contributions.</span></span>

<span data-ttu-id="7c92b-154">Verwenden Sie die Erweiterung [Reflow Markdown][reflow] in Visual Studio Code, um Absätze komfortabel umzubrechen, sodass sie in die erforderliche Zeilenlänge passen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-154">Use the [Reflow Markdown][reflow] extension in Visual Studio Code to easily reflow paragraphs to fit the prescribed line length.</span></span>

<span data-ttu-id="7c92b-155">Klassische Hilfethemen (About_topics) sind auf 80 Zeichen beschränkt.</span><span class="sxs-lookup"><span data-stu-id="7c92b-155">About_topics are limited to 80 characters.</span></span> <span data-ttu-id="7c92b-156">Einzelheiten finden Sie unter [Bearbeiten von Referenzartikeln](./editing-cmdlet-ref.md#formatting-about_-files).</span><span class="sxs-lookup"><span data-stu-id="7c92b-156">For more specific information, see [Editing reference articles](./editing-cmdlet-ref.md#formatting-about_-files).</span></span>

### <a name="lists"></a><span data-ttu-id="7c92b-157">Listen</span><span class="sxs-lookup"><span data-stu-id="7c92b-157">Lists</span></span>

<span data-ttu-id="7c92b-158">Wenn Ihre Liste mehrere Sätze oder Absätze enthält, erwägen Sie eine Unterüberschrift anstelle einer Liste.</span><span class="sxs-lookup"><span data-stu-id="7c92b-158">If your list contains multiple sentences or paragraphs, consider using a sub-level header rather than a list.</span></span>

<span data-ttu-id="7c92b-159">Eine Liste sollte von einer einzelnen Leerzeile umgeben sein.</span><span class="sxs-lookup"><span data-stu-id="7c92b-159">List should be surrounded by a single blank line.</span></span>

#### <a name="unordered-lists"></a><span data-ttu-id="7c92b-160">Unsortierte Listen</span><span class="sxs-lookup"><span data-stu-id="7c92b-160">Unordered lists</span></span>

<span data-ttu-id="7c92b-161">Beenden Sie Listenelemente nicht mit einem Punkt, es sei denn, sie enthalten mehrere Sätze.</span><span class="sxs-lookup"><span data-stu-id="7c92b-161">Do not end list items with a period unless they contain multiple sentences.</span></span> <span data-ttu-id="7c92b-162">Verwenden Sie das Bindestrich Zeichen (`-`) für Listenelement Aufzählungen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-162">Use the hyphen character (`-`) for list item bullets.</span></span> <span data-ttu-id="7c92b-163">Dadurch wird die Verwechselung mit fettem oder kursivem Markup vermieden, für das das Sternchen [`*`] verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="7c92b-163">This avoids confusion with bold or italic markup that uses the asterisk [`*`].</span></span> <span data-ttu-id="7c92b-164">Um einen Absatz oder andere Elemente unter einem Aufzählungselement einzuschließen, fügen Sie einen Zeilenumbruch ein, und richten Sie den Einzug am ersten Zeichen nach dem Aufzählungszeichen aus.</span><span class="sxs-lookup"><span data-stu-id="7c92b-164">To include a paragraph or other elements under a bullet item, insert a line break and align indentation with the first character after the bullet.</span></span>

<span data-ttu-id="7c92b-165">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="7c92b-165">For example:</span></span>

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

<span data-ttu-id="7c92b-166">Dies ist eine Liste, die Unterelemente unter einem Aufzählungselement enthält.</span><span class="sxs-lookup"><span data-stu-id="7c92b-166">This is a list that contains sub-elements under a bullet item.</span></span>

- <span data-ttu-id="7c92b-167">Erstes Aufzählungselement</span><span class="sxs-lookup"><span data-stu-id="7c92b-167">First bullet item</span></span>

  <span data-ttu-id="7c92b-168">Satz zur Erläuterung des ersten Aufzählungszeichens.</span><span class="sxs-lookup"><span data-stu-id="7c92b-168">Sentence explaining the first bullet.</span></span>

  - <span data-ttu-id="7c92b-169">Untergeordnetes Aufzählungszeichen</span><span class="sxs-lookup"><span data-stu-id="7c92b-169">Sub-bullet item</span></span>

    <span data-ttu-id="7c92b-170">Satz zur Erläuterung des Unteraufzählungszeichens.</span><span class="sxs-lookup"><span data-stu-id="7c92b-170">Sentence explaining the sub-bullet.</span></span>

- <span data-ttu-id="7c92b-171">Zweites Aufzählungszeichen</span><span class="sxs-lookup"><span data-stu-id="7c92b-171">Second bullet item</span></span>
- <span data-ttu-id="7c92b-172">Drittes Aufzählungszeichen</span><span class="sxs-lookup"><span data-stu-id="7c92b-172">Third bullet item</span></span>

#### <a name="ordered-lists"></a><span data-ttu-id="7c92b-173">Sortierte Listen</span><span class="sxs-lookup"><span data-stu-id="7c92b-173">Ordered lists</span></span>

<span data-ttu-id="7c92b-174">Um einen Absatz oder andere Elemente unter einer Aufzählung einzuschließen, richten Sie den Einzug am ersten Zeichen nach der Elementnummer aus.</span><span class="sxs-lookup"><span data-stu-id="7c92b-174">To include a paragraph or other elements under a numbered item, align indentation with the first character after the item number.</span></span> <span data-ttu-id="7c92b-175">Alle Elemente in einer Liste sollten die Nummer `1.` verwenden, statt jedes einzelne Element zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-175">All items in a numbered listed should use the number `1.` rather than incrementing each item.</span></span> <span data-ttu-id="7c92b-176">Beim Rendering erhöht Markdown den Wert automatisch.</span><span class="sxs-lookup"><span data-stu-id="7c92b-176">Markdown rendering increments the value automatically.</span></span> <span data-ttu-id="7c92b-177">Dadurch wird die Neuanordnung von Elementen vereinfacht und der Einzug von untergeordnetem Inhalt standardisiert.</span><span class="sxs-lookup"><span data-stu-id="7c92b-177">This makes reordering items easier and standardizes the indentation of subordinate content.</span></span>

<span data-ttu-id="7c92b-178">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="7c92b-178">For example:</span></span>

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

<span data-ttu-id="7c92b-179">Der resultierende Markdown wird wie folgt gerendert:</span><span class="sxs-lookup"><span data-stu-id="7c92b-179">The resulting Markdown is rendered as follows:</span></span>

1. <span data-ttu-id="7c92b-180">Fügen Sie für das erste Element ein einzelnes Leerzeichen nach der 1 ein.</span><span class="sxs-lookup"><span data-stu-id="7c92b-180">For the first element, insert a single space after the 1.</span></span> <span data-ttu-id="7c92b-181">Lange Sätze sollten in die nächste Zeile umbrochen werden und müssen am ersten Zeichen hinter dem nummerierten Listenmarker ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-181">Long sentences should be wrapped to the next line and must line up with the first character after the numbered list marker.</span></span>

   <span data-ttu-id="7c92b-182">Um ein zweites Element (wie dieses hier) aufzuführen, fügen Sie nach dem ersten Element einen Zeilenumbruch ein, und richten Sie die Einzüge aus.</span><span class="sxs-lookup"><span data-stu-id="7c92b-182">To include a second element (like this one), insert a line break after the first and align indentations.</span></span> <span data-ttu-id="7c92b-183">Der Einzug des zweiten Elements muss am ersten Zeichen hinter dem nummerierten Listenmarker ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-183">The indentation of the second element must line up with the first character after the numbered list marker.</span></span> <span data-ttu-id="7c92b-184">Für einstellige Elemente wie dieses ziehen Sie in Spalte 4 ein.</span><span class="sxs-lookup"><span data-stu-id="7c92b-184">For single digit items, like this one, you indent to column 4.</span></span> <span data-ttu-id="7c92b-185">Für zweistellige Elemente, beispielsweise die Elementnummer 10, ziehen Sie in Spalte 5 ein.</span><span class="sxs-lookup"><span data-stu-id="7c92b-185">For double digits items, for example item number 10, you indent to column 5.</span></span>

1. <span data-ttu-id="7c92b-186">Das nächste nummerierte Element beginnt hier.</span><span class="sxs-lookup"><span data-stu-id="7c92b-186">The next numbered item starts here.</span></span>

### <a name="images"></a><span data-ttu-id="7c92b-187">Bilder</span><span class="sxs-lookup"><span data-stu-id="7c92b-187">Images</span></span>

<span data-ttu-id="7c92b-188">Die Syntax zum Einschließen eines Bilds lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="7c92b-188">The syntax to include an image is:</span></span>

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

<span data-ttu-id="7c92b-189">Dabei stellt `alt text` eine kurze Beschreibung des Bilds und `<folder path>` einen relativen Pfad zum Bild dar.</span><span class="sxs-lookup"><span data-stu-id="7c92b-189">Where `alt text` is a brief description of the image and `<folder path>` is a relative path to the image.</span></span> <span data-ttu-id="7c92b-190">Alternativtext ist für Bildschirmsprachausgaben für Personen mit eingeschränktem Sehvermögen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="7c92b-190">Alternate text is required for screen readers for the visually impaired.</span></span> <span data-ttu-id="7c92b-191">Er ist außerdem nützlich, falls das Bild aufgrund eines Bugs auf der Website nicht gerendert werden kann.</span><span class="sxs-lookup"><span data-stu-id="7c92b-191">It is also useful in case there is a site bug where the image cannot be rendered.</span></span>

<span data-ttu-id="7c92b-192">Bilder sollten in einem `media/<article-name>`-Ordner innerhalb des Ordners gespeichert werden, der den Artikel enthält.</span><span class="sxs-lookup"><span data-stu-id="7c92b-192">Images should be stored in a `media/<article-name>` folder within the folder containing the article.</span></span>
<span data-ttu-id="7c92b-193">Bilder sollten nicht von mehreren Artikeln gemeinsam genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-193">Images should not be shared between articles.</span></span> <span data-ttu-id="7c92b-194">Erstellen Sie einen Ordner, der mit dem Dateinamen Ihres Artikels übereinstimmt, im `media`-Ordner.</span><span class="sxs-lookup"><span data-stu-id="7c92b-194">Create a folder that matches the filename of your article under the `media` folder.</span></span> <span data-ttu-id="7c92b-195">Kopieren Sie die Bilder für den Artikel in diesen neuen Ordner.</span><span class="sxs-lookup"><span data-stu-id="7c92b-195">Copy the images for that article to that new folder.</span></span> <span data-ttu-id="7c92b-196">Wenn ein Bild von mehreren Artikeln verwendet wird, muss jeder Bildordner eine Kopie der betreffenden Bilddatei aufweisen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-196">If an image is used by multiple articles, each image folder must have a copy of that image file.</span></span> <span data-ttu-id="7c92b-197">Diese Vorgehensweise verhindert, dass eine Änderung am Bild in einem Artikel sich auf andere Artikel auswirkt.</span><span class="sxs-lookup"><span data-stu-id="7c92b-197">This practice prevents a change to an image in one article affecting another article.</span></span>

<span data-ttu-id="7c92b-198">Die folgenden Bilddateitypen werden unterstützt: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span><span class="sxs-lookup"><span data-stu-id="7c92b-198">The following image file types are supported: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span></span>

### <a name="markdown-extensions-supported-by-open-publishing"></a><span data-ttu-id="7c92b-199">Von Open Publishing unterstützte Markdown-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="7c92b-199">Markdown extensions supported by Open Publishing</span></span>

<span data-ttu-id="7c92b-200">Das [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) (Erstellungspaket für Microsoft-Dokumentation) enthält Tools, die für unser Veröffentlichungssystem spezifische Features unterstützen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-200">The [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contains tools that support features unique to our publishing system.</span></span> <span data-ttu-id="7c92b-201">Alerts (Warnungen) sind eine Markdown-Erweiterung zum Erstellen von Blockquotes, die auf docs.microsoft.com mit Farben und Symbolen gerendert werden, die die Bedeutung des Inhalts hervorheben.</span><span class="sxs-lookup"><span data-stu-id="7c92b-201">Alerts are a Markdown extension to create blockquotes that render on docs.microsoft.com with colors and icons that highlight the significance of the content.</span></span> <span data-ttu-id="7c92b-202">Die folgenden Warnungstypen werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="7c92b-202">The following alert types are supported:</span></span>

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

<span data-ttu-id="7c92b-203">Diese Warnungen sehen auf docs.microsoft.com wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="7c92b-203">These alerts look like this on docs.microsoft.com:</span></span>

<span data-ttu-id="7c92b-204">Hinweis</span><span class="sxs-lookup"><span data-stu-id="7c92b-204">Note block</span></span>

> [!NOTE]
> <span data-ttu-id="7c92b-205">Informationen, die der Benutzer selbst beim Durchblättern bemerken sollte.</span><span class="sxs-lookup"><span data-stu-id="7c92b-205">Information the user should notice even if skimming.</span></span>

<span data-ttu-id="7c92b-206">Tipp</span><span class="sxs-lookup"><span data-stu-id="7c92b-206">Tip block</span></span>

> [!TIP]
> <span data-ttu-id="7c92b-207">Optionale Informationen, die einem Benutzer helfen sollen, erfolgreicher zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="7c92b-207">Optional information to help a user be more successful.</span></span>

<span data-ttu-id="7c92b-208">Wichtig</span><span class="sxs-lookup"><span data-stu-id="7c92b-208">Important block</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7c92b-209">Wichtige Informationen, die für den Erfolg des Benutzers unabdingbar sind.</span><span class="sxs-lookup"><span data-stu-id="7c92b-209">Essential information required for user success.</span></span>

<span data-ttu-id="7c92b-210">Achtung</span><span class="sxs-lookup"><span data-stu-id="7c92b-210">Caution block</span></span>

> [!CAUTION]
> <span data-ttu-id="7c92b-211">Negative potenzielle Folgen einer Aktion.</span><span class="sxs-lookup"><span data-stu-id="7c92b-211">Negative potential consequences of an action.</span></span>

<span data-ttu-id="7c92b-212">Warnung</span><span class="sxs-lookup"><span data-stu-id="7c92b-212">Warning block</span></span>

> [!WARNING]
> <span data-ttu-id="7c92b-213">Bestimmte gefährliche Folgen einer Aktion.</span><span class="sxs-lookup"><span data-stu-id="7c92b-213">Dangerous certain consequences of an action.</span></span>

### <a name="hyperlinks"></a><span data-ttu-id="7c92b-214">Links</span><span class="sxs-lookup"><span data-stu-id="7c92b-214">Hyperlinks</span></span>

- <span data-ttu-id="7c92b-215">Für Links muss die Markdown-Syntax `[friendlyname](url-or-path)` verwendet werden</span><span class="sxs-lookup"><span data-stu-id="7c92b-215">Hyperlinks must use Markdown syntax `[friendlyname](url-or-path)`</span></span>
- <span data-ttu-id="7c92b-216">Links sollten nach Möglichkeit als HTTPS angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-216">Links should be HTTPS when possible.</span></span>
- <span data-ttu-id="7c92b-217">Links müssen über einen Anzeigenamen verfügen, normalerweise den Titel des verknüpften Themas</span><span class="sxs-lookup"><span data-stu-id="7c92b-217">Links must have a friendly name, usually the title of the linked topic</span></span>
- <span data-ttu-id="7c92b-218">Alle Elemente im Abschnitt „Verwandte Links“ im unteren Bereich sollten mit einem Link versehen sein</span><span class="sxs-lookup"><span data-stu-id="7c92b-218">All items in the "related links" section at the bottom should be hyperlinked</span></span>
- <span data-ttu-id="7c92b-219">Verwenden Sie innerhalb der Klammern eines Links keine Graviszeichen und fette oder sonstige Auszeichnung.</span><span class="sxs-lookup"><span data-stu-id="7c92b-219">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>
- <span data-ttu-id="7c92b-220">Reine URLs können verwendet werden, wenn Sie über einen bestimmten URI sprechen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-220">Bare URLs may be used when you are talking about a specific URI.</span></span> <span data-ttu-id="7c92b-221">Der URI muss in Graviszeichen eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-221">The URI must be enclosed in backticks.</span></span> <span data-ttu-id="7c92b-222">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="7c92b-222">For example:</span></span>

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content"></a><span data-ttu-id="7c92b-223">Verknüpfen mit anderen Inhalten</span><span class="sxs-lookup"><span data-stu-id="7c92b-223">Linking to other content</span></span>

<span data-ttu-id="7c92b-224">Das Veröffentlichungssystem unterstützt zwei Arten von Links:</span><span class="sxs-lookup"><span data-stu-id="7c92b-224">There are two types of hyperlinks supported by the publishing system:</span></span>

<span data-ttu-id="7c92b-225">Bei einem **URL-Link** kann es sich um einen URL-Pfad handeln, der relativ zum Stamm von docs.microsoft.com ist.</span><span class="sxs-lookup"><span data-stu-id="7c92b-225">A **URL link** can be a URL path that is relative to the root of docs.microsoft.com.</span></span> <span data-ttu-id="7c92b-226">Oder eine absolute URL, die die vollständige URL-Syntax enthält.</span><span class="sxs-lookup"><span data-stu-id="7c92b-226">Or an absolute URL that include the full URL syntax.</span></span> <span data-ttu-id="7c92b-227">Beispiel: `https:/github.com/MicrosoftDocs/PowerShell-Docs`</span><span class="sxs-lookup"><span data-stu-id="7c92b-227">For example: `https:/github.com/MicrosoftDocs/PowerShell-Docs`</span></span>

- <span data-ttu-id="7c92b-228">Verwenden Sie URL-Links für die Verknüpfung mit Inhalten außerhalb der PowerShell-Dokumentation oder zwischen der Cmdlet-Referenz und konzeptionellen Artikeln innerhalb der PowerShell-Dokumentation. Die einfachste Möglichkeit zum Erstellen eines relativen Links besteht darin, die URL aus Ihrem Browser zu kopieren und dann `https://docs.microsoft.com/en-us` aus dem Wert zu entfernen, den Sie in Markdown einfügen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-228">Use URL links when linking to content outside of PowerShell-Docs or between cmdlet reference and conceptual articles within PowerShell-docs. The simplest way to create a relative link is to copy the URL from your browser then remove `https://docs.microsoft.com/en-us` from the value you paste into markdown.</span></span>
- <span data-ttu-id="7c92b-229">Schließen Sie keine Gebietsschemas in URLs in Microsoft-Eigenschaften ein (entfernen Sie beispielsweise</span><span class="sxs-lookup"><span data-stu-id="7c92b-229">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="7c92b-230">`/en-us` aus dem URL).</span><span class="sxs-lookup"><span data-stu-id="7c92b-230">remove `/en-us` from URL).</span></span>
- <span data-ttu-id="7c92b-231">Entfernen Sie alle nicht benötigten Abfrageparameter aus dem URL, sofern Sie nicht eine Verknüpfung mit einer bestimmten Artikelversion herstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-231">Remove any unnecessary query parameters from the URL unless you need to link to a specific version of an article.</span></span> <span data-ttu-id="7c92b-232">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="7c92b-232">Examples:</span></span>
  - <span data-ttu-id="7c92b-233">`?view=powershell-5.1`: dieser Parameter wird verwendet, um eine Verknüpfung mit einer bestimmten PowerShell-Version herzustellen</span><span class="sxs-lookup"><span data-stu-id="7c92b-233">`?view=powershell-5.1` - this is used to link to a specific version of PowerShell</span></span>
  - <span data-ttu-id="7c92b-234">`?redirectedfrom=MSDN`: dieser Parameter wird zum URL hinzugefügt, wenn Sie von einem älteren Artikel zur neuen Version umgeleitet werden</span><span class="sxs-lookup"><span data-stu-id="7c92b-234">`?redirectedfrom=MSDN` - this is added to the URL when you get redirected from an old article to its new location</span></span>
- <span data-ttu-id="7c92b-235">Alle URLs zu externen Websites sollten HTTPS verwenden, es sei denn, dies ist für die Zielwebsite ungültig.</span><span class="sxs-lookup"><span data-stu-id="7c92b-235">All URLs to external websites should use HTTPS unless that is not valid for the target site.</span></span>

<span data-ttu-id="7c92b-236">Eine **Dateiverknüpfung** wird verwendet, um von einem Referenzartikel auf einen anderen oder von einem konzeptionellen Artikel auf einen anderen zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-236">A **file link** is used to link from one reference article to another, or from one conceptual article to another.</span></span> <span data-ttu-id="7c92b-237">Wenn Sie auf einen Referenzartikel für eine bestimmte PowerShell-Version verweisen müssen, müssen Sie einen URL-Link verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-237">If you need to link to a reference article for a specific version of PowerShell, then you must use a URL link.</span></span>

- <span data-ttu-id="7c92b-238">Dateiverknüpfungen enthalten einen relativen Dateipfad (Beispiel: `../folder/file.md`)</span><span class="sxs-lookup"><span data-stu-id="7c92b-238">File links contain a relative file path (for example: `../folder/file.md`)</span></span>
- <span data-ttu-id="7c92b-239">Alle Dateipfade enthalten Schrägstriche (`/`).</span><span class="sxs-lookup"><span data-stu-id="7c92b-239">All file paths use forward-slash (`/`) characters</span></span>

<span data-ttu-id="7c92b-240">Deep Linking ist sowohl für URL-Links als auch für Dateiverknüpfungen zulässig.</span><span class="sxs-lookup"><span data-stu-id="7c92b-240">Deep linking is allowed on both URL and file links.</span></span> <span data-ttu-id="7c92b-241">Fügen Sie den Anker am Ende des Zielpfads hinzu.</span><span class="sxs-lookup"><span data-stu-id="7c92b-241">Add the anchor to the end of the target path.</span></span>
<span data-ttu-id="7c92b-242">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="7c92b-242">For example:</span></span>

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

<span data-ttu-id="7c92b-243">Weitere Informationen finden Sie unter [Verwenden von Links in der Dokumentation](https://docs.microsoft.com/contribute/how-to-write-links).</span><span class="sxs-lookup"><span data-stu-id="7c92b-243">For more information, see [Use links in documentation](https://docs.microsoft.com/contribute/how-to-write-links).</span></span>

## <a name="formatting-command-syntax-elements"></a><span data-ttu-id="7c92b-244">Formatieren von Befehlssyntaxelementen</span><span class="sxs-lookup"><span data-stu-id="7c92b-244">Formatting command syntax elements</span></span>

- <span data-ttu-id="7c92b-245">Verwenden Sie immer den vollständigen Namen für Cmdlets und Parameter.</span><span class="sxs-lookup"><span data-stu-id="7c92b-245">Always use the full name for cmdlets and parameters.</span></span> <span data-ttu-id="7c92b-246">Vermeiden Sie die Verwendung von Aliasen, es sei denn, Sie möchten den Alias beispielhaft hervorheben.</span><span class="sxs-lookup"><span data-stu-id="7c92b-246">Avoid using aliases unless you are specifically demonstrating the alias.</span></span>

- <span data-ttu-id="7c92b-247">Eigenschaften, Parameter, Objekte, Typnamen, Klassennamen und Klassenmethoden sollten **fett** formatiert werden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-247">Property, parameter, object, type names, class names, class methods should be **bold**.</span></span>
  - <span data-ttu-id="7c92b-248">Eigenschafts- und Parameterwerte sollten in Graviszeichen (`` ` ``) eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-248">Property and parameter values should be wrapped in backticks (`` ` ``).</span></span>
  - <span data-ttu-id="7c92b-249">Verwenden Sie Graviszeichen, wenn Sie auf Typen verweisen, die in Klammern stehen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-249">When referring to types using the bracketed style, use backticks.</span></span> <span data-ttu-id="7c92b-250">Beispiel: `[System.Io.FileInfo]`</span><span class="sxs-lookup"><span data-stu-id="7c92b-250">For example: `[System.Io.FileInfo]`</span></span>

- <span data-ttu-id="7c92b-251">Schlüsselwörter, Cmdlet-Namen, Funktionen, Variablen, native EXE-Dateinamen, Dateipfade und Inlinesyntaxbeispiele sollten in Graviszeichen (`` ` ``) eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-251">Language keywords, cmdlet names, functions, variables, native EXEs, file paths, and inline syntax examples should be wrapped in backtick (`` ` ``) characters.</span></span>

  <span data-ttu-id="7c92b-252">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="7c92b-252">For example:</span></span>

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - <span data-ttu-id="7c92b-253">Wenn Sie anhand des Namens auf einen Parameter verweisen, sollte der Name **fett** formatiert sein.</span><span class="sxs-lookup"><span data-stu-id="7c92b-253">When referring to a parameter by name, the name should be **bold**.</span></span> <span data-ttu-id="7c92b-254">Wenn Sie die Verwendung eines Parameters mit dem Bindestrichpräfix veranschaulichen, sollte der Parameter in Graviszeichen eingeschlossen sein.</span><span class="sxs-lookup"><span data-stu-id="7c92b-254">When illustrating the use of a parameter with the hyphen prefix, the parameter should be wrapped in backticks.</span></span> <span data-ttu-id="7c92b-255">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="7c92b-255">For example:</span></span>

    ```markdown
    The parameter's name is **Name**, but it is typed as `-Name` when used on the command
    line as a parameter.
    ```

  - <span data-ttu-id="7c92b-256">Bei der beispielhaften Verwendung eines externen Befehls sollte das Beispiel in Graviszeichen eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-256">When showing example usage of an external command, the example should be wrapped in backticks.</span></span>
    <span data-ttu-id="7c92b-257">Fügen Sie die Dateierweiterung immer in den nativen Befehl ein.</span><span class="sxs-lookup"><span data-stu-id="7c92b-257">Always include the file extension in the native command.</span></span> <span data-ttu-id="7c92b-258">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="7c92b-258">For example:</span></span>

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    <span data-ttu-id="7c92b-259">Durch das Einfügen der Dateierweiterung wird sichergestellt, dass der richtige Befehl gemäß der PowerShell-Rangfolge ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7c92b-259">Including the file extension ensures that the correct command is executed according PowerShell's command precedence.</span></span>

- <span data-ttu-id="7c92b-260">Beim Schreiben eines konzeptionellen Artikels (im Gegensatz zu Referenzinhalt) sollte die erste Instanz eines Cmdlet-Namens per Link zur Dokumentation des Cmdlets verweisen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-260">When writing a conceptual article (as opposed to reference content), the first instance of a cmdlet name should be hyperlinked to the cmdlet documentation.</span></span> <span data-ttu-id="7c92b-261">Verwenden Sie innerhalb der Klammern eines Links keine Graviszeichen und fette oder sonstige Auszeichnung.</span><span class="sxs-lookup"><span data-stu-id="7c92b-261">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

  <span data-ttu-id="7c92b-262">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="7c92b-262">For example:</span></span>

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  <span data-ttu-id="7c92b-263">Weitere Informationen finden Sie im Abschnitt [Links](#hyperlinks) in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="7c92b-263">For more information, see [Hyperlinks](#hyperlinks) section of this article.</span></span>

## <a name="markdown-for-code-samples"></a><span data-ttu-id="7c92b-264">Markdown für Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="7c92b-264">Markdown for code samples</span></span>

<span data-ttu-id="7c92b-265">Markdown unterstützt zwei verschiedene Codeformatvorlagen:</span><span class="sxs-lookup"><span data-stu-id="7c92b-265">Markdown supports two different code styles:</span></span>

- <span data-ttu-id="7c92b-266">**„span“-Elemente (inline)** : durch ein einzelnes Graviszeichen (`` ` ``) gekennzeichnet.</span><span class="sxs-lookup"><span data-stu-id="7c92b-266">**Code spans (inline)** - marked by a single backtick (`` ` ``) character.</span></span> <span data-ttu-id="7c92b-267">Wird innerhalb eines Absatzes anstelle eines eigenständigen Blocks verwendet.</span><span class="sxs-lookup"><span data-stu-id="7c92b-267">Used within a paragraph rather than as a standalone block.</span></span>
- <span data-ttu-id="7c92b-268">**Codeblöcke**: ein mehrzeiliger Block, der in dreifache Graviszeichen-Zeichenfolgen (`` ``` ``) eingeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="7c92b-268">**Code blocks** - a multi-line block surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="7c92b-269">Codeblöcke können außerdem über eine Sprachbezeichnung im Anschluss an die Graviszeichen verfügen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-269">Code blocks may also have a language label following the backticks.</span></span> <span data-ttu-id="7c92b-270">Die Sprachbezeichnung ermöglicht Syntaxhervorhebung für die Inhalte des Codeblocks.</span><span class="sxs-lookup"><span data-stu-id="7c92b-270">The language label enables syntax highlighting for the contents of the code block.</span></span>

<span data-ttu-id="7c92b-271">Alle Codeblöcke sollten in einem abgesetzten Codebereich (Code Fence) enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="7c92b-271">All code blocks should be contained in a code fence.</span></span> <span data-ttu-id="7c92b-272">Verwenden Sie bei Codeblöcken niemals einen Einzug.</span><span class="sxs-lookup"><span data-stu-id="7c92b-272">Never use indentation for code blocks.</span></span> <span data-ttu-id="7c92b-273">Markdown lässt dieses Muster zu, dies kann jedoch zu Problemen führen und sollte vermieden werden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-273">Markdown allows this pattern but it can be problematic and should be avoided.</span></span>

<span data-ttu-id="7c92b-274">Bei einem Codeblock handelt es sich um eine oder mehrere Codezeilen, die in dreifache Graviszeichen (`` ``` ``) eingeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="7c92b-274">A code block is one or more lines of code surrounded by a triple-backtick (`` ``` ``) code fence.</span></span>
<span data-ttu-id="7c92b-275">Die Codebereichsmarkierungen müssen in einer eigenen Zeile vor und nach dem Codebeispiel stehen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-275">The code fence markers must be on their own line before and after the code sample.</span></span> <span data-ttu-id="7c92b-276">Der Marker am Beginn des Codeblocks darf eine optionale Sprachbezeichnung aufweisen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-276">The marker at the start of the code block may have an optional language label.</span></span> <span data-ttu-id="7c92b-277">Das Open Publishing System (OPS) von Microsoft verwendet die Sprachbezeichnung zur Unterstützung der Syntaxhervorhebungsfunktion.</span><span class="sxs-lookup"><span data-stu-id="7c92b-277">Microsoft's Open Publishing System (OPS) uses the language label to support the syntax highlighting feature.</span></span>

<span data-ttu-id="7c92b-278">Eine vollständige Liste der unterstützten Sprachtags finden Sie unter [Umgrenzte Codeblöcke](/contribute/code-in-docs#fenced-code-blocks) im zentralen Leitfaden für Mitwirkende.</span><span class="sxs-lookup"><span data-stu-id="7c92b-278">For a full list of supported language tags, see [Fenced code blocks](/contribute/code-in-docs#fenced-code-blocks) in the centralized contributor guide.</span></span>

<span data-ttu-id="7c92b-279">OPS fügt außerdem eine Schaltfläche **Kopieren** hinzu, die die Inhalte des Codeblocks in die Zwischenablage kopiert.</span><span class="sxs-lookup"><span data-stu-id="7c92b-279">OPS also adds a **Copy** button that copies the contents of the code block to the clipboard.</span></span> <span data-ttu-id="7c92b-280">Dies ermöglicht es Ihnen, den Code schnell in ein Skript einzufügen, um das Codebeispiel zu testen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-280">This allows you to quickly paste the code into a script to test the code sample.</span></span> <span data-ttu-id="7c92b-281">Allerdings sind nicht alle Beispiele in unserer Dokumentation für die Ausführung bestimmt.</span><span class="sxs-lookup"><span data-stu-id="7c92b-281">However, not all examples in our documentation are intended to be run as-is.</span></span> <span data-ttu-id="7c92b-282">Einige Codeblöcke sind einfache Abbildungen eines PowerShell-Konzepts.</span><span class="sxs-lookup"><span data-stu-id="7c92b-282">Some code blocks are simple illustrations of a PowerShell concept.</span></span>

<span data-ttu-id="7c92b-283">In unserer Dokumentation werden drei Arten von Codeblöcken verwendet:</span><span class="sxs-lookup"><span data-stu-id="7c92b-283">There are three types code blocks used in our documentation:</span></span>

1. <span data-ttu-id="7c92b-284">Syntaxblöcke</span><span class="sxs-lookup"><span data-stu-id="7c92b-284">Syntax blocks</span></span>
1. <span data-ttu-id="7c92b-285">Anschauliche Beispiele</span><span class="sxs-lookup"><span data-stu-id="7c92b-285">Illustrative examples</span></span>
1. <span data-ttu-id="7c92b-286">Ausführbare Beispiele</span><span class="sxs-lookup"><span data-stu-id="7c92b-286">Executable examples</span></span>

### <a name="syntax-code-blocks"></a><span data-ttu-id="7c92b-287">Syntaxcodeblöcke</span><span class="sxs-lookup"><span data-stu-id="7c92b-287">Syntax code blocks</span></span>

<span data-ttu-id="7c92b-288">Mithilfe von Syntaxcodeblöcken wird die syntaktische Struktur eines Befehls beschrieben.</span><span class="sxs-lookup"><span data-stu-id="7c92b-288">Syntax code blocks are used to describe the syntactic structure of a command.</span></span> <span data-ttu-id="7c92b-289">Verwenden Sie keine Sprachtags für die Umgrenzung von Code.</span><span class="sxs-lookup"><span data-stu-id="7c92b-289">Do not use a language tag on the code fence.</span></span> <span data-ttu-id="7c92b-290">Dieses Beispiel veranschaulicht alle möglichen Parameter des `Get-Command`-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="7c92b-290">This example illustrates all the possible parameters of the `Get-Command` cmdlet.</span></span>

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax]
  [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
  [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

<span data-ttu-id="7c92b-291">Dieses Beispiel beschreibt die `for`-Anweisungen allgemein:</span><span class="sxs-lookup"><span data-stu-id="7c92b-291">This example describes the `for` statement in generalized terms:</span></span>

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a><span data-ttu-id="7c92b-292">Anschauliche Beispiele</span><span class="sxs-lookup"><span data-stu-id="7c92b-292">Illustrative examples</span></span>

<span data-ttu-id="7c92b-293">Anschauliche Beispiele werden verwendet, um ein PowerShell-Konzept zu erläutern.</span><span class="sxs-lookup"><span data-stu-id="7c92b-293">Illustrative examples are used to explain a PowerShell concept.</span></span> <span data-ttu-id="7c92b-294">Sie sind nicht dazu bestimmt, zur Ausführung in die Zwischenablage kopiert zu werden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-294">They are not meant to be copied to the clipboard for execution.</span></span> <span data-ttu-id="7c92b-295">Diese werden am häufigsten für einfache Beispiele verwendet, die sich leicht eingeben lassen und die leicht verständlich sind.</span><span class="sxs-lookup"><span data-stu-id="7c92b-295">These are most commonly used for simple examples that are easy to type and easy to understand.</span></span> <span data-ttu-id="7c92b-296">Der Codeblock kann die PowerShell-Eingabeaufforderung und die Beispielausgabe umfassen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-296">The code block can include the PowerShell prompt and example output.</span></span>

<span data-ttu-id="7c92b-297">Nachfolgend ist ein einfaches Beispiel gezeigt, das die PowerShell-Vergleichsoperatoren veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="7c92b-297">Here is a simple example illustrating the PowerShell comparison operators.</span></span> <span data-ttu-id="7c92b-298">In diesem Fall wollen wir nicht, dass der Leser das Beispiel kopiert und ausführt.</span><span class="sxs-lookup"><span data-stu-id="7c92b-298">In this case, we don't intend the reader to copy and run this example.</span></span>

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

### <a name="executable-examples"></a><span data-ttu-id="7c92b-299">Ausführbare Beispiele</span><span class="sxs-lookup"><span data-stu-id="7c92b-299">Executable examples</span></span>

<span data-ttu-id="7c92b-300">Komplexe Beispiele oder Beispiele, die zum Kopieren und Ausführen erstellt werden, sollten das folgende Markup als Blockformatvorlage verwenden:</span><span class="sxs-lookup"><span data-stu-id="7c92b-300">Complex examples, or examples that are intended to be copied and executed, should use the following block-style markup:</span></span>

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

<span data-ttu-id="7c92b-301">Die von PowerShell-Befehlen angezeigte Ausgabe sollte in einen **Output**-Codeblock eingeschlossen werden, um Syntaxhervorhebung zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-301">The output displayed by PowerShell commands should be enclosed in an **Output** code block to prevent syntax highlighting.</span></span> <span data-ttu-id="7c92b-302">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="7c92b-302">For example:</span></span>

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

<span data-ttu-id="7c92b-303">Die **Output**-Codebezeichnung ist keine offizielle „Sprache“, die vom Syntaxhervorhebungs-System unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="7c92b-303">The **Output** code label is not an official "language" supported by the syntax highlighting system.</span></span>
<span data-ttu-id="7c92b-304">Diese Bezeichnung ist jedoch nützlich, da OPS dem Rahmen des Codefelds auf der Website die Bezeichnung „Output“ hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="7c92b-304">However, this label is useful because OPS adds the "Output" label to the code box frame on the web page.</span></span> <span data-ttu-id="7c92b-305">Das „Output“-Codefeld hat keine Syntaxhervorhebung.</span><span class="sxs-lookup"><span data-stu-id="7c92b-305">The "Output" code box has no syntax highlighting.</span></span>

## <a name="coding-style-rules"></a><span data-ttu-id="7c92b-306">Regeln für Codeformatvorlagen</span><span class="sxs-lookup"><span data-stu-id="7c92b-306">Coding style rules</span></span>

### <a name="avoid-line-continuation-in-code-samples"></a><span data-ttu-id="7c92b-307">Vermeiden Sie Zeilenfortsetzung in Codebeispielen</span><span class="sxs-lookup"><span data-stu-id="7c92b-307">Avoid line continuation in code samples</span></span>

<span data-ttu-id="7c92b-308">Vermeiden Sie die Verwendung von Zeilenfortsetzungszeichen (`` ` ``) in PowerShell-Codebeispielen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-308">Avoid using line continuation characters (`` ` ``) in PowerShell code examples.</span></span> <span data-ttu-id="7c92b-309">Sie sind schlecht zu sehen und können zu Problemen führen, wenn am Zeilenende zusätzliche Leerzeichen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="7c92b-309">These are hard to see and can cause problems if there are extra spaces at the end of the line.</span></span>

- <span data-ttu-id="7c92b-310">Verwenden Sie PowerShell-Aufteilung, um die Zeilenlänge für Cmdlets zu reduzieren, die viele Parameter aufweisen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-310">Use PowerShell splatting to reduce line length for cmdlets that have a lot of parameters.</span></span>
- <span data-ttu-id="7c92b-311">Nutzen Sie die natürlichen Gelegenheiten für Zeilenumbrüche in PowerShell, etwa nach Pipesymbolen (`|`), öffnenden geschweiften Klammern, Klammern und eckigen Klammern.</span><span class="sxs-lookup"><span data-stu-id="7c92b-311">Take advantage of PowerShell's natural line break opportunities, like after pipe (`|`) characters, opening braces, parentheses, and brackets.</span></span>

### <a name="avoid-using-powershell-prompts-in-examples"></a><span data-ttu-id="7c92b-312">Vermeiden Sie die Verwendung von PowerShell-Eingabeaufforderungen in Beispielen</span><span class="sxs-lookup"><span data-stu-id="7c92b-312">Avoid using PowerShell prompts in examples</span></span>

<span data-ttu-id="7c92b-313">Von der Verwendung der Eingabeaufforderungs-Zeichenfolge wird abgeraten. Sie sollte auf Fälle beschränkt werden, deren Zweck die Veranschaulichung der Befehlszeilensyntax ist.</span><span class="sxs-lookup"><span data-stu-id="7c92b-313">Use of the prompt string is discouraged and should be limited to scenarios that are meant to illustrate command line usage.</span></span> <span data-ttu-id="7c92b-314">Für die meisten dieser Beispiele sollte die Eingabeaufforderungs-Zeichenfolge `PS>` lauten.</span><span class="sxs-lookup"><span data-stu-id="7c92b-314">For most of these examples, the prompt string should be `PS>`.</span></span> <span data-ttu-id="7c92b-315">Diese Eingabeaufforderung ist unabhängig von betriebssystemspezifischen Indikatoren.</span><span class="sxs-lookup"><span data-stu-id="7c92b-315">This prompt is independent of OS-specific indicators.</span></span>

<span data-ttu-id="7c92b-316">Eingabeaufforderungen sind für Beispiele erforderlich, die Befehle veranschaulichen, mit denen die Eingabeaufforderung geändert wird, oder wenn der angezeigte Pfad für das dargestellte Szenario relevant ist.</span><span class="sxs-lookup"><span data-stu-id="7c92b-316">Prompts are required for examples that illustrate commands that alter the prompt or when the path displayed is significant to the scenario being illustrated.</span></span> <span data-ttu-id="7c92b-317">Das folgende Beispiel zeigt, wie sich die Eingabeaufforderung ändert, wenn der Registrierungsanbieter verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="7c92b-317">The following example illustrates how the prompt changes when using the Registry provider.</span></span>

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

### <a name="do-not-use-aliases-in-examples"></a><span data-ttu-id="7c92b-318">Verwenden Sie keine Aliase in Beispielen</span><span class="sxs-lookup"><span data-stu-id="7c92b-318">Do not use aliases in examples</span></span>

<span data-ttu-id="7c92b-319">Sie sollten für alle Cmdlets und Parameter immer den vollständigen Namen verwenden, es sei denn, Sie behandeln speziell den Alias.</span><span class="sxs-lookup"><span data-stu-id="7c92b-319">You should always use the full name of all cmdlets and parameters unless you are specifically talking about the alias.</span></span> <span data-ttu-id="7c92b-320">Namen von Cmdlets und Parametern müssen die richtige Pascal-Schreibweise verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c92b-320">Cmdlet and parameter names must use the proper Pascal-cased names.</span></span>

### <a name="using-parameters-in-examples"></a><span data-ttu-id="7c92b-321">Verwenden von Parametern in Beispielen</span><span class="sxs-lookup"><span data-stu-id="7c92b-321">Using parameters in examples</span></span>

<span data-ttu-id="7c92b-322">Vermeiden Sie die Verwendung von Positionsparametern.</span><span class="sxs-lookup"><span data-stu-id="7c92b-322">Avoid using positional parameters.</span></span> <span data-ttu-id="7c92b-323">Im Allgemeinen sollten Sie immer den Parameternamen in ein Beispiel aufnehmen, selbst wenn es sich um einen Positionsparameter handelt.</span><span class="sxs-lookup"><span data-stu-id="7c92b-323">In general, you should always include the parameter name in an example, even if the parameter is positional.</span></span> <span data-ttu-id="7c92b-324">Dies verringert die Gefahr von Missverständnissen in Ihren Beispielen.</span><span class="sxs-lookup"><span data-stu-id="7c92b-324">This reduces the chance of confusion in your examples.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7c92b-325">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="7c92b-325">Next steps</span></span>

[<span data-ttu-id="7c92b-326">Bearbeiten der Cmdlet-Referenz</span><span class="sxs-lookup"><span data-stu-id="7c92b-326">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
