---
title: Checkliste für die Bearbeitung
description: Dies ist eine zusammengefasste Liste mit Regeln für die Bearbeitung der PowerShell-Dokumentation.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 511e0c323e1a3256039e819d06f32f6e1ac42767
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060335"
---
# <a name="editors-checklist"></a><span data-ttu-id="ffc46-103">Checkliste für die Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="ffc46-103">Editor's checklist</span></span>

<span data-ttu-id="ffc46-104">Dies ist eine Zusammenfassung der Regeln, die beim Schreiben neuer oder Aktualisieren bestehender Artikel gelten.</span><span class="sxs-lookup"><span data-stu-id="ffc46-104">This is a summary of rules to apply when writing new or updating existing articles.</span></span> <span data-ttu-id="ffc46-105">Ausführliche Erläuterungen und Beispiele zu diesen Regeln finden Sie in anderen Artikeln des Leitfadens für Mitwirkende.</span><span class="sxs-lookup"><span data-stu-id="ffc46-105">See other articles in the Contributor's Guide for detailed explanations and examples of these rules.</span></span>

## <a name="metadata"></a><span data-ttu-id="ffc46-106">Metadaten</span><span class="sxs-lookup"><span data-stu-id="ffc46-106">Metadata</span></span>

- <span data-ttu-id="ffc46-107">`ms.date`: muss das Format **MM/TT/JJJJ** haben</span><span class="sxs-lookup"><span data-stu-id="ffc46-107">`ms.date`: must be in the format **MM/DD/YYYY**</span></span>
  - <span data-ttu-id="ffc46-108">Datum ändern, sobald eine signifikante oder sachliche Aktualisierung vorliegt</span><span class="sxs-lookup"><span data-stu-id="ffc46-108">Change the date when there is a significant or factual update</span></span>
    - <span data-ttu-id="ffc46-109">Neuorganisieren des Artikels</span><span class="sxs-lookup"><span data-stu-id="ffc46-109">Reorganizing the article</span></span>
    - <span data-ttu-id="ffc46-110">Beheben sachlicher Fehler</span><span class="sxs-lookup"><span data-stu-id="ffc46-110">Fixing factual errors</span></span>
    - <span data-ttu-id="ffc46-111">Hinzufügen neuer Informationen</span><span class="sxs-lookup"><span data-stu-id="ffc46-111">Adding new information</span></span>
  - <span data-ttu-id="ffc46-112">Das Datum nicht ändern, wenn die Aktualisierung unerheblich ist</span><span class="sxs-lookup"><span data-stu-id="ffc46-112">Do not change the date if the update is insignificant</span></span>
    - <span data-ttu-id="ffc46-113">Korrigieren von Rechtschreibfehlern und Formatierung</span><span class="sxs-lookup"><span data-stu-id="ffc46-113">Fixing typos and formatting</span></span>
- <span data-ttu-id="ffc46-114">`title`: eindeutige Zeichenfolge mit 43-59 Zeichen einschließlich Leerzeichen</span><span class="sxs-lookup"><span data-stu-id="ffc46-114">`title`: unique string of 43-59 chars including spaces</span></span>
  - <span data-ttu-id="ffc46-115">Standortbezeichner nicht einschließen (wird automatisch generiert)</span><span class="sxs-lookup"><span data-stu-id="ffc46-115">Do not include site identifier (it is auto-generated)</span></span>
  - <span data-ttu-id="ffc46-116">Nur ersten Buchstaben des Satzes und von Eigennamen großschreiben</span><span class="sxs-lookup"><span data-stu-id="ffc46-116">Use sentence case - capitalize only the first word and any proper nouns</span></span>
- <span data-ttu-id="ffc46-117">`description`: 115-145 Zeichen einschließlich Leerzeichen. Diese Zusammenfassung wird im Suchergebnis angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ffc46-117">`description`: 115-145 characters including spaces - this abstract displays in the search result</span></span>

## <a name="formatting"></a><span data-ttu-id="ffc46-118">Formatierung</span><span class="sxs-lookup"><span data-stu-id="ffc46-118">Formatting</span></span>

- <span data-ttu-id="ffc46-119">Elemente, die inline in einem Absatz angezeigt werden, in Hochkommas setzen</span><span class="sxs-lookup"><span data-stu-id="ffc46-119">Backtick syntax elements that appear, inline, within a paragraph</span></span>
  - <span data-ttu-id="ffc46-120">Cmdlet-Namen: `Verb-Noun`</span><span class="sxs-lookup"><span data-stu-id="ffc46-120">Cmdlet names `Verb-Noun`</span></span>
  - <span data-ttu-id="ffc46-121">Variable: `$counter`</span><span class="sxs-lookup"><span data-stu-id="ffc46-121">Variable `$counter`</span></span>
  - <span data-ttu-id="ffc46-122">Syntaktische Beispiele: `Verb-Noun -Parameter`</span><span class="sxs-lookup"><span data-stu-id="ffc46-122">Syntactic examples `Verb-Noun -Parameter`</span></span>
  - <span data-ttu-id="ffc46-123">Dateipfade: `C:\Program Files\PowerShell`, `/usr/bin/pwsh`</span><span class="sxs-lookup"><span data-stu-id="ffc46-123">File paths `C:\Program Files\PowerShell`, `/usr/bin/pwsh`</span></span>
  - <span data-ttu-id="ffc46-124">URLs, auf die im Dokument nicht geklickt werden soll</span><span class="sxs-lookup"><span data-stu-id="ffc46-124">URLs that are not meant to be clickable in the document</span></span>
- <span data-ttu-id="ffc46-125">Eigenschaftsnamen, Parameterwerte, Parameternamen, Klassennamen, Modulnamen, Entitätsnamen, Objekt- oder Typnamen fett formatieren</span><span class="sxs-lookup"><span data-stu-id="ffc46-125">Use bold for property names, parameter values, parameter names, class names, module names, entity names, object or type names</span></span>
  - <span data-ttu-id="ffc46-126">Fett wird für semantisches Markup verwendet, nicht zur Betonung</span><span class="sxs-lookup"><span data-stu-id="ffc46-126">Bold is used for semantic markup, not emphasis</span></span>
  - <span data-ttu-id="ffc46-127">Fett: Sternchen `**`</span><span class="sxs-lookup"><span data-stu-id="ffc46-127">Bold - use asterisks `**`</span></span>
- <span data-ttu-id="ffc46-128">Kursiv: Unterstrich `_`</span><span class="sxs-lookup"><span data-stu-id="ffc46-128">Italic - use underscore `_`</span></span>
  - <span data-ttu-id="ffc46-129">Wird nur zur Betonung verwendet, nicht für semantisches Markup</span><span class="sxs-lookup"><span data-stu-id="ffc46-129">Only used for emphasis, not for semantic markup</span></span>
- <span data-ttu-id="ffc46-130">Zeilenumbrüche bei 100 Spalten (oder 80 für **about_Topics**)</span><span class="sxs-lookup"><span data-stu-id="ffc46-130">Line breaks at 100 columns (or at 80 for **about_Topics**)</span></span>
- <span data-ttu-id="ffc46-131">Keine harten Tabstoppzeichen, nur Leerzeichen verwenden</span><span class="sxs-lookup"><span data-stu-id="ffc46-131">No hard tabs - use spaces only</span></span>
- <span data-ttu-id="ffc46-132">Nachgestellte Leerzeichen in Zeilen</span><span class="sxs-lookup"><span data-stu-id="ffc46-132">No trailing spaces on lines</span></span>

### <a name="headers"></a><span data-ttu-id="ffc46-133">Header</span><span class="sxs-lookup"><span data-stu-id="ffc46-133">Headers</span></span>

- <span data-ttu-id="ffc46-134">H1 als Erstes. Nur ein H1 pro Artikel</span><span class="sxs-lookup"><span data-stu-id="ffc46-134">H1 is first - only one H1 per article</span></span>
- <span data-ttu-id="ffc46-135">Nur [ATX-Header](https://github.github.com/gfm/#atx-headings) verwenden</span><span class="sxs-lookup"><span data-stu-id="ffc46-135">Use [ATX Headers](https://github.github.com/gfm/#atx-headings) only</span></span>
- <span data-ttu-id="ffc46-136">Ersten Buchstaben in allen Headern großschreiben</span><span class="sxs-lookup"><span data-stu-id="ffc46-136">Use sentence case for all headers</span></span>
- <span data-ttu-id="ffc46-137">Keine Ebenen überspringen: kein H3 ohne H2</span><span class="sxs-lookup"><span data-stu-id="ffc46-137">Do not skip levels - no H3 without an H2</span></span>
- <span data-ttu-id="ffc46-138">Maximale Tiefe von H3 oder H4</span><span class="sxs-lookup"><span data-stu-id="ffc46-138">Max depth of H3 or H4</span></span>
- <span data-ttu-id="ffc46-139">Leerzeile davor und dahinter</span><span class="sxs-lookup"><span data-stu-id="ffc46-139">Blank line before and after</span></span>
- <span data-ttu-id="ffc46-140">PlatyPS erzwingt bestimmte Header in seinem Schema. Keine Header hinzufügen oder entfernen</span><span class="sxs-lookup"><span data-stu-id="ffc46-140">PlatyPS enforces specific headers in its schema - do not add or remove headers</span></span>

### <a name="code-blocks"></a><span data-ttu-id="ffc46-141">Codeblöcke</span><span class="sxs-lookup"><span data-stu-id="ffc46-141">Code blocks</span></span>

- <span data-ttu-id="ffc46-142">Leerzeile davor und dahinter</span><span class="sxs-lookup"><span data-stu-id="ffc46-142">Blank line before and after</span></span>
- <span data-ttu-id="ffc46-143">Codeumgrenzungen in Form von Tags verwenden: **PowerShell**, **Ausgabe** oder andere geeignete Sprach-ID</span><span class="sxs-lookup"><span data-stu-id="ffc46-143">Use tagged code fences - **powershell**, **Output**, or other appropriate language ID</span></span>
- <span data-ttu-id="ffc46-144">Umgrenzung ohne Tags: Syntaxblöcke oder andere Shells</span><span class="sxs-lookup"><span data-stu-id="ffc46-144">Untagged fence - syntax blocks or other shells</span></span>
- <span data-ttu-id="ffc46-145">Legen Sie **Ausgabe** in einem separaten Codeblock ab, außer für einfache Beispiele, bei denen Sie nicht beabsichtigen, dass der Leser auf die Schaltfläche **Kopieren** klickt.</span><span class="sxs-lookup"><span data-stu-id="ffc46-145">Put **Output** in separate code block except for simple examples where you don't intend the for the reader to use the **Copy** button</span></span>
- <span data-ttu-id="ffc46-146">Siehe die Liste der [unterstützten Sprachen](/contribute/code-in-docs#supported-languages)</span><span class="sxs-lookup"><span data-stu-id="ffc46-146">See list of [supported languages](/contribute/code-in-docs#supported-languages)</span></span>

### <a name="lists"></a><span data-ttu-id="ffc46-147">Listen</span><span class="sxs-lookup"><span data-stu-id="ffc46-147">Lists</span></span>

- <span data-ttu-id="ffc46-148">Ordnungsgemäß eingerückt</span><span class="sxs-lookup"><span data-stu-id="ffc46-148">Indented properly</span></span>
- <span data-ttu-id="ffc46-149">Leerzeile vor dem ersten und hinter dem letzten Element</span><span class="sxs-lookup"><span data-stu-id="ffc46-149">Blank line before first item and after last item</span></span>
- <span data-ttu-id="ffc46-150">Aufzählungszeichen: Bindestrich (`-`) verwenden, keine Sternchen (`*`) –zu leicht mit Betonung zu verwechseln</span><span class="sxs-lookup"><span data-stu-id="ffc46-150">Bullet - use hyphen (`-`) not asterisk (`*`) - too easy to confuse with emphasis</span></span>
- <span data-ttu-id="ffc46-151">Bei nummerierten Listen lauten alle Zahlen „1“.</span><span class="sxs-lookup"><span data-stu-id="ffc46-151">For numbered lists, all numbers are "1."</span></span>

## <a name="terminology"></a><span data-ttu-id="ffc46-152">Begriff</span><span class="sxs-lookup"><span data-stu-id="ffc46-152">Terminology</span></span>

- <span data-ttu-id="ffc46-153">PowerShell verglichen mit Windows PowerShell verglichen mit PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="ffc46-153">PowerShell vs. Windows PowerShell vs. PowerShell Core</span></span>
- <span data-ttu-id="ffc46-154">Siehe [Produktterminologie](powershell-style-guide.md#product-terminology)</span><span class="sxs-lookup"><span data-stu-id="ffc46-154">See [Product Terminology](powershell-style-guide.md#product-terminology)</span></span>

## <a name="cmdlet-reference-examples"></a><span data-ttu-id="ffc46-155">Cmdlet-Referenz: Beispiele</span><span class="sxs-lookup"><span data-stu-id="ffc46-155">Cmdlet reference examples</span></span>

- <span data-ttu-id="ffc46-156">Mindestens ein Beispiel muss in der Cmdlet-Referenz vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="ffc46-156">Must have at least one example in cmdlet reference</span></span>
- <span data-ttu-id="ffc46-157">Beispiele sollten gerade nur so viel Code enthalten, um die Verwendung zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="ffc46-157">Examples should be just enough code to demonstrate the usage</span></span>
- <span data-ttu-id="ffc46-158">PowerShell-Syntax</span><span class="sxs-lookup"><span data-stu-id="ffc46-158">PowerShell syntax</span></span>
  - <span data-ttu-id="ffc46-159">Vollständige Namen von Cmdlets und Parametern verwenden – keine Aliase</span><span class="sxs-lookup"><span data-stu-id="ffc46-159">Use full names of cmdlets and parameters - no aliases</span></span>
  - <span data-ttu-id="ffc46-160">Aufteilung von Parametern verwenden, wenn die Befehlszeile zu lang wird</span><span class="sxs-lookup"><span data-stu-id="ffc46-160">Use splatting for parameters when the command line gets too long</span></span>
  - <span data-ttu-id="ffc46-161">Hochkommas zur Zeilenfortsetzung vermeiden, nur bei Bedarf verwenden</span><span class="sxs-lookup"><span data-stu-id="ffc46-161">Avoid using line continuation backticks - only use when necessary</span></span>
- <span data-ttu-id="ffc46-162">Die PowerShell-Eingabeaufforderung (`PS>`) entfernen oder vereinfachen, außer wenn für das Beispiel erforderlich</span><span class="sxs-lookup"><span data-stu-id="ffc46-162">Remove or simplify the PowerShell prompt (`PS>`) except where required for the example</span></span>
- <span data-ttu-id="ffc46-163">Das Cmdlet-Referenzbeispiel muss dem folgenden PlatyPS-Schema folgen</span><span class="sxs-lookup"><span data-stu-id="ffc46-163">Cmdlet reference example must follow the following PlatyPS schema</span></span>

  ~~~Markdown
  ### Example 1 - Descriptive title

  Zero or more short descriptive paragraphs explaining the context of the example followed by one or
  more code blocks. Recommend at least one and no more than two.

  ```powershell
  ... one or more PowerShell code statements ...
  ```

  ```Output
  Example output of the code above.
  ```

  Zero or more optional follow up paragraphs that explain the details of the code and output.
  ~~~

- <span data-ttu-id="ffc46-164">Setzen Sie keine Absätze zwischen die Codeblöcke.</span><span class="sxs-lookup"><span data-stu-id="ffc46-164">Do not put paragraphs between the code blocks.</span></span> <span data-ttu-id="ffc46-165">Der gesamte beschreibende Inhalt muss vor oder hinter den Codeblöcken stehen.</span><span class="sxs-lookup"><span data-stu-id="ffc46-165">All descriptive content must come before or after the code blocks.</span></span>

## <a name="linking-to-other-documents"></a><span data-ttu-id="ffc46-166">Verknüpfen mit anderen Dokumenten</span><span class="sxs-lookup"><span data-stu-id="ffc46-166">Linking to other documents</span></span>

- <span data-ttu-id="ffc46-167">Verknüpfung außerhalb des Docsets oder zwischen Cmdlet-Referenz und konzeptuellen Inhalten</span><span class="sxs-lookup"><span data-stu-id="ffc46-167">Linking outside the docset or between cmdlet reference and conceptual</span></span>
  - <span data-ttu-id="ffc46-168">Relative URLs beim Verknüpfen mit docs.microsoft.com verwenden (`https://docs.microsoft.com/en-us` entfernen)</span><span class="sxs-lookup"><span data-stu-id="ffc46-168">Use relative URLs when linking to docs.microsoft.com (remove `https://docs.microsoft.com/en-us`)</span></span>
  - <span data-ttu-id="ffc46-169">Gebietsschemas nicht in URLs für Microsoft-Eigenschaften einbeziehen (z. B.</span><span class="sxs-lookup"><span data-stu-id="ffc46-169">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="ffc46-170">`/en-us` aus URL entfernen)</span><span class="sxs-lookup"><span data-stu-id="ffc46-170">remove `/en-us` from URL)</span></span>
  - <span data-ttu-id="ffc46-171">Alle URLs zu externen Websites müssen HTTPS verwenden, es sei denn, dies gilt nicht für die Zielwebsite</span><span class="sxs-lookup"><span data-stu-id="ffc46-171">All URLs to external websites should use HTTPS unless that is not valid for the target site</span></span>
- <span data-ttu-id="ffc46-172">Innerhalb des Docsets</span><span class="sxs-lookup"><span data-stu-id="ffc46-172">Within docset</span></span>
  - <span data-ttu-id="ffc46-173">Link zu Dateipfad (z. B. `../folder/file.md`)</span><span class="sxs-lookup"><span data-stu-id="ffc46-173">Link to file path (e.g. `../folder/file.md`)</span></span>
  - <span data-ttu-id="ffc46-174">Alle Dateipfade enthalten Schrägstriche (`/`).</span><span class="sxs-lookup"><span data-stu-id="ffc46-174">All file paths use forward-slash (`/`) characters</span></span>
- <span data-ttu-id="ffc46-175">Bildlinks müssen eindeutigen alternativen Text enthalten.</span><span class="sxs-lookup"><span data-stu-id="ffc46-175">Image links should have unique alt text</span></span>
