---
title: Bearbeiten von Referenzartikeln
description: In diesem Artikel werden die spezifischen Anforderungen für die Bearbeitung der Cmdlet-Referenz und „About_“-Themen in der PowerShell-Dokumentation erläutert.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: e135f6cc81ba7537a535a08421e1ca9b2b2af573
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81624770"
---
# <a name="editing-reference-articles"></a><span data-ttu-id="014b7-103">Bearbeiten von Referenzartikeln</span><span class="sxs-lookup"><span data-stu-id="014b7-103">Editing reference articles</span></span>

<span data-ttu-id="014b7-104">Cmdlet-Referenzartikel weisen eine bestimmte Struktur auf.</span><span class="sxs-lookup"><span data-stu-id="014b7-104">Cmdlet reference articles have a specific structure.</span></span> <span data-ttu-id="014b7-105">Diese Struktur wird von [PlatyPS][] definiert.</span><span class="sxs-lookup"><span data-stu-id="014b7-105">This structure is defined by [PlatyPS][].</span></span>
<span data-ttu-id="014b7-106">PlatyPS generiert die Cmdlet-Hilfe für PowerShell-Module in Markdown.</span><span class="sxs-lookup"><span data-stu-id="014b7-106">PlatyPS generates the cmdlet help for PowerShell modules in Markdown.</span></span> <span data-ttu-id="014b7-107">Nach dem Bearbeiten der Markdowndateien wird PlatyPS verwendet, um die vom Cmdlet `Get-Help` verwendeten MAML-Hilfedateien zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="014b7-107">After editing the Markdown files, PlatyPS is used create the MAML help files used by the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="014b7-108">PlatyPS hat ein hartcodiertes Schema für die Cmdlet-Referenz, das in den Code geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="014b7-108">PlatyPS has a hard-coded schema for cmdlet reference that is written into the code.</span></span> <span data-ttu-id="014b7-109">Im Dokument [platyPS.schema.md][] wird versucht, diese Struktur zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="014b7-109">The [platyPS.schema.md][] document attempts to describe this structure.</span></span> <span data-ttu-id="014b7-110">Verstöße gegen das Schema führen zu Buildfehlern, die behoben werden müssen, bevor wir Ihren Beitrag annehmen können.</span><span class="sxs-lookup"><span data-stu-id="014b7-110">Schema violations cause build errors that must be fixed before we can accept your contribution.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="014b7-111">Allgemeine Richtlinien</span><span class="sxs-lookup"><span data-stu-id="014b7-111">General guidelines</span></span>

- <span data-ttu-id="014b7-112">Entfernen Sie keine Headerstrukturen.</span><span class="sxs-lookup"><span data-stu-id="014b7-112">Do not remove any of the header structures.</span></span> <span data-ttu-id="014b7-113">PlatyPS erwartet eine bestimmte Struktur von Headern.</span><span class="sxs-lookup"><span data-stu-id="014b7-113">PlatyPS expects a specific set of headers.</span></span>
- <span data-ttu-id="014b7-114">Die Header **Input type** und **Output type** müssen einen Typ haben.</span><span class="sxs-lookup"><span data-stu-id="014b7-114">The **Input type** and **Output type** headers must have a type.</span></span> <span data-ttu-id="014b7-115">Wenn das Cmdlet keine Eingabe annimmt oder keinen Wert zurückgibt, verwenden Sie den Wert `None`.</span><span class="sxs-lookup"><span data-stu-id="014b7-115">If the cmdlet does not take input or return a value then use the value `None`.</span></span>
- <span data-ttu-id="014b7-116">Umgrenzte Codeblöcke sind nur im Abschnitt [Examples](#structuring-examples) zulässig.</span><span class="sxs-lookup"><span data-stu-id="014b7-116">Fenced code blocks are only allowed in the [Examples](#structuring-examples) section.</span></span>
- <span data-ttu-id="014b7-117">„span“-Elemente in Inlinecode können in beliebigen Absätzen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="014b7-117">Inline code spans can be used in any paragraph.</span></span>

## <a name="formatting-about_-files"></a><span data-ttu-id="014b7-118">Formatieren von About_-Dateien</span><span class="sxs-lookup"><span data-stu-id="014b7-118">Formatting About_ files</span></span>

<span data-ttu-id="014b7-119">`About_*`-Dateien werden in Markdown geschrieben, jedoch als Nur-Text-Dateien weitergegeben.</span><span class="sxs-lookup"><span data-stu-id="014b7-119">`About_*` files are written in Markdown but are shipped as plain text files.</span></span> <span data-ttu-id="014b7-120">Wir verwenden [Pandoc][], um die Markdown-Dateien in Nur-Text-Dateien umzuwandeln.</span><span class="sxs-lookup"><span data-stu-id="014b7-120">We use [Pandoc][] to convert the Markdown to plain text.</span></span> <span data-ttu-id="014b7-121">`About_*`-Dateien sind für optimale Kompatibilität mit allen Versionen von PowerShell und den Veröffentlichungstools formatiert.</span><span class="sxs-lookup"><span data-stu-id="014b7-121">`About_*` files are formatted for the best compatibility across all versions of PowerShell and with the publishing tools.</span></span>

<span data-ttu-id="014b7-122">Grundlegende Formatierungsleitlinien:</span><span class="sxs-lookup"><span data-stu-id="014b7-122">Basic formatting guidelines:</span></span>

- <span data-ttu-id="014b7-123">Beschränken Sie Zeilen auf 80 Zeichen.</span><span class="sxs-lookup"><span data-stu-id="014b7-123">Limit lines to 80 characters.</span></span> <span data-ttu-id="014b7-124">Pandoc fügt bei einigen Markdown-Blöcken einen Einzug ein, sodass diese Blöcke angepasst werden müssen.</span><span class="sxs-lookup"><span data-stu-id="014b7-124">Pandoc indents some Markdown blocks so those block must be adjusted.</span></span>
  - <span data-ttu-id="014b7-125">Codeblöcke sind auf 76 Zeichen beschränkt</span><span class="sxs-lookup"><span data-stu-id="014b7-125">Code blocks are limited to 76 characters</span></span>
  - <span data-ttu-id="014b7-126">Tabellen sind auf 76 Zeichen beschränkt</span><span class="sxs-lookup"><span data-stu-id="014b7-126">Tables are limited 76 characters</span></span>
  - <span data-ttu-id="014b7-127">Blockquotes (und Alerts) sind auf 78 Zeichen beschränkt</span><span class="sxs-lookup"><span data-stu-id="014b7-127">Blockquotes (and Alerts) are limited 78 characters</span></span>

- <span data-ttu-id="014b7-128">Verwenden der speziellen Pandoc-Metazeichen: `\`, `$` und `<`</span><span class="sxs-lookup"><span data-stu-id="014b7-128">Using Pandoc's special meta-characters `\`,`$`, and `<`</span></span>
  - <span data-ttu-id="014b7-129">Innerhalb eines Headers müssen diese Zeichen mit einem führenden `\`-Zeichen als Escapezeichen versehen oder mit Graviszeichen (`` ` ``) zwischen „span“-Elementen eingefügt werden</span><span class="sxs-lookup"><span data-stu-id="014b7-129">Within a header - these characters must be escaped using a leading `\` character or enclosed in code spans using backticks (`` ` ``)</span></span>
  - <span data-ttu-id="014b7-130">Innerhalb eines Absatzes müssen diese Zeichen im Code zwischen „span“-Elementen platziert werden.</span><span class="sxs-lookup"><span data-stu-id="014b7-130">Within a paragraph, these characters should be put into code spans.</span></span> <span data-ttu-id="014b7-131">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="014b7-131">For example:</span></span>

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

- <span data-ttu-id="014b7-132">Tabellen müssen in 76 Zeichen passen.</span><span class="sxs-lookup"><span data-stu-id="014b7-132">Tables need to fit within 76 characters</span></span>
  - <span data-ttu-id="014b7-133">Inhalt von Zellen manuell auf mehrere Zeilen umbrechen.</span><span class="sxs-lookup"><span data-stu-id="014b7-133">Manually wrap contents of cells across multiple lines</span></span>
  - <span data-ttu-id="014b7-134">Öffnende und schließende `|`-Zeichen in jeder Zeile verwenden.</span><span class="sxs-lookup"><span data-stu-id="014b7-134">Use opening and closing `|` characters on each line</span></span>
  - <span data-ttu-id="014b7-135">Das folgende Beispiel zeigt den ordnungsgemäßen Aufbau einer Tabelle mit Informationen, bei der mehrere Zeilen innerhalb einer Zelle umbrochen werden.</span><span class="sxs-lookup"><span data-stu-id="014b7-135">The following example illustrates how to properly construct a table that contains information that wraps on multiple lines within a cell.</span></span>

    ~~~markdown
    ```
    |Operator|Description                |Example                          |
    |--------|---------------------------|---------------------------------|
    |`-is`   |Returns TRUE when the input|`(get-date) -is [DateTime]`      |
    |        |is an instance of the      |`True`                           |
    |        |specified .NET type.       |                                 |
    |`-isNot`|Returns TRUE when the input|`(get-date) -isNot [DateTime]`   |
    |        |not an instance of the     |`False`                          |
    |        |specified.NET type.        |                                 |
    |`-as`   |Converts the input to the  |`"5/7/07" -as [DateTime]`        |
    |        |specified .NET type.       |`Monday, May 7, 2007 12:00:00 AM`|
    ```
    ~~~

    > [!NOTE]
    > <span data-ttu-id="014b7-136">Die Beschränkung von 76 Spalten gilt nur für `About_*`-Themen.</span><span class="sxs-lookup"><span data-stu-id="014b7-136">The 76-column limitation applies only to `About_*` topics.</span></span> <span data-ttu-id="014b7-137">In konzeptionellen oder Cmdlet-Referenzartikeln können breite Spalten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="014b7-137">You can use wide columns in conceptual or cmdlet reference articles.</span></span>

## <a name="structuring-examples"></a><span data-ttu-id="014b7-138">Beispiele für die Strukturierung</span><span class="sxs-lookup"><span data-stu-id="014b7-138">Structuring examples</span></span>

<span data-ttu-id="014b7-139">Im PlatyPS-Schema ist der Header **EXAMPLES** ein H2-Header und jedes Beispiel ein H3-Header.</span><span class="sxs-lookup"><span data-stu-id="014b7-139">In the PlatyPS schema, the **EXAMPLES** header is an H2 header and each example is an H3 header.</span></span>

<span data-ttu-id="014b7-140">Innerhalb eines Beispiels erlaubt das Schema nicht das Trennen von Codeblöcken durch Absätze.</span><span class="sxs-lookup"><span data-stu-id="014b7-140">Within an example, the schema does not allow code blocks to be separated by paragraphs.</span></span> <span data-ttu-id="014b7-141">Das unterstützte Schema ist wie folgt:</span><span class="sxs-lookup"><span data-stu-id="014b7-141">The supported schema is:</span></span>

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

<span data-ttu-id="014b7-142">Nummerieren Sie jedes Beispiel, und fügen Sie einen Kurztitel hinzu.</span><span class="sxs-lookup"><span data-stu-id="014b7-142">Number each example and add a brief title.</span></span>

<span data-ttu-id="014b7-143">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="014b7-143">For example:</span></span>

### <a name="example-1-get-cmdlets-functions-and-aliases"></a><span data-ttu-id="014b7-144">Beispiel 1: Abrufen von Cmdlets, Funktionen und Aliasen</span><span class="sxs-lookup"><span data-stu-id="014b7-144">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="014b7-145">Dieser Befehl ruft die PowerShell-Cmdlets, Funktionen und Aliase ab, die auf dem Computer installiert sind.</span><span class="sxs-lookup"><span data-stu-id="014b7-145">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <a name="example-2-get-commands-in-the-current-session"></a><span data-ttu-id="014b7-146">Beispiel 2: Abrufen von Befehlen in der aktuellen Sitzung</span><span class="sxs-lookup"><span data-stu-id="014b7-146">Example 2: Get commands in the current session</span></span>

```powershell
Get-Command -ListImported
```

## <a name="next-steps"></a><span data-ttu-id="014b7-147">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="014b7-147">Next steps</span></span>

[<span data-ttu-id="014b7-148">Checkliste für die Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="014b7-148">Editorial checklist</span></span>](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: /PowerShell/module/Microsoft.PowerShell.Core/About/about_Comparison_Operators
[Pandoc]: https://pandoc.org
