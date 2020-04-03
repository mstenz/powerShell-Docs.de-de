---
title: Bearbeiten von Referenzartikeln
description: In diesem Artikel werden die spezifischen Anforderungen für die Bearbeitung der Cmdlet-Referenz und „About_“-Themen in der PowerShell-Dokumentation erläutert.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 3aed1c14429310c57681397d4877a3a6f48400fd
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500977"
---
# <a name="editing-reference-articles"></a><span data-ttu-id="bd1a4-103">Bearbeiten von Referenzartikeln</span><span class="sxs-lookup"><span data-stu-id="bd1a4-103">Editing reference articles</span></span>

<span data-ttu-id="bd1a4-104">Cmdlet-Referenzartikel haben eine bestimmte Struktur,</span><span class="sxs-lookup"><span data-stu-id="bd1a4-104">Cmdlet reference articles have a specific structure.</span></span> <span data-ttu-id="bd1a4-105">die von [PlatyPS][] definiert wird.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-105">This structure is defined by [PlatyPS][].</span></span>
<span data-ttu-id="bd1a4-106">PlatyPS generiert die Cmdlet-Hilfe für PowerShell-Module in Markdown.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-106">PlatyPS generates the cmdlet help for PowerShell modules in Markdown.</span></span> <span data-ttu-id="bd1a4-107">Nach dem Bearbeiten der Markdowndateien wird PlatyPS verwendet, um die vom Cmdlet `Get-Help` verwendeten MAML-Hilfedateien zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-107">After editing the Markdown files, PlatyPS is used create the MAML help files used by the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="bd1a4-108">PlatyPS hat ein hartcodiertes Schema für die Cmdlet-Referenz, das in den Code geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-108">PlatyPS has a hard-coded schema for cmdlet reference that is written into the code.</span></span> <span data-ttu-id="bd1a4-109">Im Dokument [platyPS.schema.md][] wird versucht, diese Struktur zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-109">The [platyPS.schema.md][] document attempts to describe this structure.</span></span> <span data-ttu-id="bd1a4-110">Verstöße gegen das Schema führen zu Buildfehlern, die behoben werden müssen, bevor wir Ihren Beitrag annehmen können.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-110">Schema violations cause build errors that must be fixed before we can accept your contribution.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="bd1a4-111">Allgemeine Richtlinien</span><span class="sxs-lookup"><span data-stu-id="bd1a4-111">General guidelines</span></span>

- <span data-ttu-id="bd1a4-112">Entfernen Sie keine Headerstrukturen.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-112">Do not remove any of the header structures.</span></span> <span data-ttu-id="bd1a4-113">PlatyPS erwartet eine bestimmte Struktur von Headern.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-113">PlatyPS expects a specific set of headers.</span></span>
- <span data-ttu-id="bd1a4-114">Die Header **Input type** und **Output type** müssen einen Typ haben.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-114">The **Input type** and **Output type** headers must have a type.</span></span> <span data-ttu-id="bd1a4-115">Wenn das Cmdlet keine Eingabe annimmt oder keinen Wert zurückgibt, verwenden Sie den Wert `None`.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-115">If the cmdlet does not take input or return a value then use the value `None`.</span></span>
- <span data-ttu-id="bd1a4-116">Umgrenzte Codeblöcke sind nur im Abschnitt [Examples](#structuring-examples) zulässig.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-116">Fenced code blocks are only allowed in the [Examples](#structuring-examples) section.</span></span>
- <span data-ttu-id="bd1a4-117">„span“-Elemente in Inlinecode können in beliebigen Absätzen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-117">Inline code spans can be used in any paragraph.</span></span>

## <a name="formatting-about_-files"></a><span data-ttu-id="bd1a4-118">Formatieren von About_-Dateien</span><span class="sxs-lookup"><span data-stu-id="bd1a4-118">Formatting About_ files</span></span>

<span data-ttu-id="bd1a4-119">`About_*`-Dateien werden jetzt von [Pandoc][] statt von PlatyPS verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-119">`About_*` files are now processed by [Pandoc][], instead of PlatyPS.</span></span> <span data-ttu-id="bd1a4-120">`About_*`-Dateien sind für optimale Kompatibilität mit allen Versionen von PowerShell und den Veröffentlichungstools formatiert.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-120">`About_*` files are formatted for the best compatibility across all versions of PowerShell and with the publishing tools.</span></span>

<span data-ttu-id="bd1a4-121">Grundlegende Formatierungsleitlinien:</span><span class="sxs-lookup"><span data-stu-id="bd1a4-121">Basic formatting guidelines:</span></span>

- <span data-ttu-id="bd1a4-122">Zeilen auf 80 Zeichen begrenzen.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-122">Limit lines to 80 characters</span></span>
- <span data-ttu-id="bd1a4-123">Codeblöcke und -tabellen sind auf 76 Zeichen begrenzt, da Pandoc diese bei der Konvertierung in normalen Text um vier Leerzeichen einrückt.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-123">Code blocks and tables are limited to 76 characters because Pandoc indents these by four spaces during conversion to plain text</span></span>
- <span data-ttu-id="bd1a4-124">Tabellen müssen in 76 Zeichen passen.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-124">Tables need to fit within 76 characters</span></span>
  - <span data-ttu-id="bd1a4-125">Inhalt von Zellen manuell auf mehrere Zeilen umbrechen.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-125">Manually wrap contents of cells across multiple lines</span></span>
  - <span data-ttu-id="bd1a4-126">Öffnende und schließende `|`-Zeichen in jeder Zeile verwenden.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-126">Use opening and closing `|` characters on each line</span></span>
  - <span data-ttu-id="bd1a4-127">Ein funktionierendes Beispiel finden Sie unter [about_Comparison_Operators][about-example].</span><span class="sxs-lookup"><span data-stu-id="bd1a4-127">See a working example in [about_Comparison_Operators][about-example]</span></span>
- <span data-ttu-id="bd1a4-128">Pandoc-Sonderzeichen `\`,`$` und `<` verwenden.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-128">Using Pandoc special characters `\`,`$`, and `<`</span></span>
  - <span data-ttu-id="bd1a4-129">Innerhalb eines Headers müssen diese Zeichen mit einem führenden `\`-Zeichen als Escapezeichen versehen oder in Hochkommas (`` ` ``) gesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-129">Within a header - these characters must be escaped using a leading `\` character or enclosed in backticks (`` ` ``)</span></span>
  - <span data-ttu-id="bd1a4-130">Innerhalb eines Absatzes müssen diese Zeichen im Code zwischen „span“-Elementen platziert werden.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-130">Within a paragraph, these characters should be put into code spans.</span></span> <span data-ttu-id="bd1a4-131">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="bd1a4-131">For example:</span></span>

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

## <a name="structuring-examples"></a><span data-ttu-id="bd1a4-132">Beispiele für die Strukturierung</span><span class="sxs-lookup"><span data-stu-id="bd1a4-132">Structuring examples</span></span>

<span data-ttu-id="bd1a4-133">Im PlatyPS-Schema ist der Header **EXAMPLES** ein H2-Header und jedes Beispiel ein H3-Header.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-133">In the PlatyPS schema, the **EXAMPLES** header is an H2 header and each example is an H3 header.</span></span>

<span data-ttu-id="bd1a4-134">Innerhalb eines Beispiels erlaubt das Schema nicht das Trennen von Codeblöcken durch Absätze.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-134">Within an example, the schema does not allow code blocks to be separated by paragraphs.</span></span> <span data-ttu-id="bd1a4-135">Das unterstützte Schema ist wie folgt:</span><span class="sxs-lookup"><span data-stu-id="bd1a4-135">The supported schema is:</span></span>

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

<span data-ttu-id="bd1a4-136">Nummerieren Sie jedes Beispiel, und fügen Sie einen Kurztitel hinzu.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-136">Number each example and add a brief title.</span></span>

<span data-ttu-id="bd1a4-137">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="bd1a4-137">For example:</span></span>

### <a name="example-1-get-cmdlets-functions-and-aliases"></a><span data-ttu-id="bd1a4-138">Beispiel 1: Abrufen von Cmdlets, Funktionen und Aliasen</span><span class="sxs-lookup"><span data-stu-id="bd1a4-138">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="bd1a4-139">Dieser Befehl ruft die PowerShell-Cmdlets, Funktionen und Aliase ab, die auf dem Computer installiert sind.</span><span class="sxs-lookup"><span data-stu-id="bd1a4-139">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <a name="example-2-get-commands-in-the-current-session"></a><span data-ttu-id="bd1a4-140">Beispiel 2: Abrufen von Befehlen in der aktuellen Sitzung</span><span class="sxs-lookup"><span data-stu-id="bd1a4-140">Example 2: Get commands in the current session</span></span>

```powershell
Get-Command -ListImported
```

## <a name="next-steps"></a><span data-ttu-id="bd1a4-141">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="bd1a4-141">Next steps</span></span>

[<span data-ttu-id="bd1a4-142">Checkliste für die Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="bd1a4-142">Editorial checklist</span></span>](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: /PowerShell/module/Microsoft.PowerShell.Core/About/about_Comparison_Operators
[Pandoc]: https://pandoc.org
