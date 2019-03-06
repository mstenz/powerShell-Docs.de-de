---
title: Grundlegendes zur Dateicodierung in VSCode und PowerShell
description: Konfigurieren Sie die in VSCode und PowerShell-dateicodierung
ms.date: 02/28/2019
ms.openlocfilehash: f3b133b4bee7688821a5960429e2f26b69b01e12
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251472"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a><span data-ttu-id="3e545-103">Grundlegendes zur Dateicodierung in VSCode und PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e545-103">Understanding file encoding in VSCode and PowerShell</span></span>

<span data-ttu-id="3e545-104">Beim Verwenden von VS Code zum Erstellen und bearbeiten die PowerShell-Skripts ist es wichtig, dass Ihre Dateien gespeichert werden, verwenden das richtige Zeichen-Codierungsformat.</span><span class="sxs-lookup"><span data-stu-id="3e545-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="3e545-105">Was ist die dateicodierung, und warum es wichtig ist?</span><span class="sxs-lookup"><span data-stu-id="3e545-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="3e545-106">VSCode verwaltet die Schnittstelle zwischen einer menschlichen eingeben Zeichenfolgen mit Zeichen in einen Puffer und Byteblöcken lesen und Schreiben in das Dateisystem.</span><span class="sxs-lookup"><span data-stu-id="3e545-106">VSCode manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="3e545-107">Wenn eine Datei in VSCode gespeichert wird, wird eine textcodierung, die zu diesem Zweck verwendet.</span><span class="sxs-lookup"><span data-stu-id="3e545-107">When VSCode saves a file, it uses a text encoding to do this.</span></span>

<span data-ttu-id="3e545-108">Bei Ausführung eines Skripts durch PowerShell müssen sie auf ähnliche Weise die Bytes in einer Datei in Zeichen, die Datei in ein PowerShell-Programm zu rekonstruieren konvertieren.</span><span class="sxs-lookup"><span data-stu-id="3e545-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="3e545-109">Da VSCode die Datei schreibt, und PowerShell die Datei liest, müssen sie das gleiche System für die Codierung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="3e545-109">Since VSCode writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="3e545-110">Wird diese Art der Analyse ein PowerShell-Skript: *Bytes* -> *Zeichen* -> *Token*  ->   *abstrakte Syntaxstruktur* -> *Ausführung*.</span><span class="sxs-lookup"><span data-stu-id="3e545-110">This process of parsing a PowerShell script goes: *bytes* -> *characters* -> *tokens* -> *abstract syntax tree* -> *execution*.</span></span>

<span data-ttu-id="3e545-111">Mit einer sinnvolle Codierung Standardkonfiguration werden sowohl PowerShell als auch VSCode installiert.</span><span class="sxs-lookup"><span data-stu-id="3e545-111">Both VSCode and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="3e545-112">Allerdings hat die standardcodierung verwendet, die von PowerShell mit der Version von PowerShell Core (Version 6.x) geändert.</span><span class="sxs-lookup"><span data-stu-id="3e545-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="3e545-113">Um sicherzustellen, dass keine Probleme, die mithilfe von PowerShell oder die PowerShell-Erweiterung in Visual Studio Code haben, müssen Sie zum Konfigurieren der Einstellungen für VSCode und PowerShell ordnungsgemäß.</span><span class="sxs-lookup"><span data-stu-id="3e545-113">To ensure you have no problems using PowerShell or the PowerShell extension in VSCode, you need to configure your VSCode and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="3e545-114">Häufige Ursachen für Probleme-Codierung</span><span class="sxs-lookup"><span data-stu-id="3e545-114">Common causes of encoding issues</span></span>

<span data-ttu-id="3e545-115">Codierung Probleme auftreten, wenn die Codierung des VSCode oder Ihre Skriptdatei nicht übereinstimmt, ist die erwartete Codierung von PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e545-115">Encoding problems occur when the encoding of VSCode or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="3e545-116">Es gibt keine Möglichkeit für PowerShell, um die dateicodierung automatisch zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="3e545-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="3e545-117">Sie sind eher selten Codierung Probleme bei der Verwendung von Zeichen, die nicht in der [7-Bit-ASCII-Zeichensatz](https://ascii.cl/).</span><span class="sxs-lookup"><span data-stu-id="3e545-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="3e545-118">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="3e545-118">For example:</span></span>

- <span data-ttu-id="3e545-119">Akzent lateinische Zeichen (`É`, `ü`)</span><span class="sxs-lookup"><span data-stu-id="3e545-119">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="3e545-120">Nicht-lateinische Zeichen wie Kyrillisch (`Д`, `Ц`)</span><span class="sxs-lookup"><span data-stu-id="3e545-120">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="3e545-121">Han Chinesisch (`脚`, `本`)</span><span class="sxs-lookup"><span data-stu-id="3e545-121">Han Chinese (`脚`, `本`)</span></span>

<span data-ttu-id="3e545-122">Häufige Gründe für die Codierung Probleme sind:</span><span class="sxs-lookup"><span data-stu-id="3e545-122">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="3e545-123">Die Codierungen von VSCode und PowerShell wurden die Standardeinstellungen nicht geändert wurde.</span><span class="sxs-lookup"><span data-stu-id="3e545-123">The encodings of VSCode and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="3e545-124">Für PowerShell 5.1 oder unterhalb der Standardkapazität ist die Codierung VSCodes unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="3e545-124">For PowerShell 5.1 and below, the default encoding is different from VSCode's.</span></span>
- <span data-ttu-id="3e545-125">Einem anderen Editor wurden geöffnet und die Datei in eine neue Codierung überschrieben.</span><span class="sxs-lookup"><span data-stu-id="3e545-125">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="3e545-126">Dies geschieht häufig mit der ISE.</span><span class="sxs-lookup"><span data-stu-id="3e545-126">This often happens with the ISE.</span></span>
- <span data-ttu-id="3e545-127">Die Datei wird überprüft, in die quellcodeverwaltung in einer Codierung, die sich unterscheidet, von welcher VSCode oder PowerShell erwartet.</span><span class="sxs-lookup"><span data-stu-id="3e545-127">The file is checked into source control in an encoding that is different from what VSCode or PowerShell expects.</span></span> <span data-ttu-id="3e545-128">Dies kann passieren, wenn Mitarbeiter Editoren mit unterschiedlichen Codierung Konfigurationen verwenden.</span><span class="sxs-lookup"><span data-stu-id="3e545-128">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="3e545-129">Wie Sie feststellen, wenn die Codierung Probleme haben</span><span class="sxs-lookup"><span data-stu-id="3e545-129">How to tell when you have encoding issues</span></span>

<span data-ttu-id="3e545-130">Häufig Codierungsfehler bieten sich die als Fehler in Skripts analysiert.</span><span class="sxs-lookup"><span data-stu-id="3e545-130">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="3e545-131">Wenn Sie in Ihrem Skript seltsame Zeichensequenzen finden, kann dies das Problem sein.</span><span class="sxs-lookup"><span data-stu-id="3e545-131">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="3e545-132">Im folgenden Beispiel wird ein Gedankenstrich (`–`) wird angezeigt als Zeichen `â€“`:</span><span class="sxs-lookup"><span data-stu-id="3e545-132">In the example below, an en-dash (`–`) appears as the characters `â€“`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="3e545-133">Dieses Problem tritt auf, da VSCode das Zeichen codiert `–` in UTF-8, wie die Bytes `0xE2 0x80 0x93`.</span><span class="sxs-lookup"><span data-stu-id="3e545-133">This problem occurs because VSCode encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span>
<span data-ttu-id="3e545-134">Wenn diese Bytes als Windows-1252 decodiert werden, werden sie als Zeichen interpretiert `â€“`.</span><span class="sxs-lookup"><span data-stu-id="3e545-134">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€“`.</span></span>

<span data-ttu-id="3e545-135">Einige ungewöhnliche Zeichensequenzen, die möglicherweise gehören:</span><span class="sxs-lookup"><span data-stu-id="3e545-135">Some strange character sequences that you might see include:</span></span>

- <span data-ttu-id="3e545-136">`â€“` anstelle von `–`</span><span class="sxs-lookup"><span data-stu-id="3e545-136">`â€“` instead of `–`</span></span>
- <span data-ttu-id="3e545-137">`â€”` anstelle von `—`</span><span class="sxs-lookup"><span data-stu-id="3e545-137">`â€”` instead of `—`</span></span>
- <span data-ttu-id="3e545-138">`Ã„2` anstelle von `Ä`</span><span class="sxs-lookup"><span data-stu-id="3e545-138">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="3e545-139">`Â` anstelle von ` ` (geschütztes Leerzeichen)</span><span class="sxs-lookup"><span data-stu-id="3e545-139">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="3e545-140">`Ã©` anstelle von `é`</span><span class="sxs-lookup"><span data-stu-id="3e545-140">`Ã©` instead of `é`</span></span>

<span data-ttu-id="3e545-141">Diesem praktischen [Verweis](https://www.i18nqa.com/debug/utf8-debug.html) listet häufige Muster angegeben, die eine Codierung UTF-8/Windows-1252-Problem hinweisen.</span><span class="sxs-lookup"><span data-stu-id="3e545-141">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a><span data-ttu-id="3e545-142">Interaktion zwischen die PowerShell-Erweiterung in Visual Studio Code und Codierungen</span><span class="sxs-lookup"><span data-stu-id="3e545-142">How the PowerShell extension in VSCode interacts with encodings</span></span>

<span data-ttu-id="3e545-143">Die PowerShell-Erweiterung interagiert mit Skripts in eine Reihe von Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="3e545-143">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="3e545-144">Wenn Skripts in Visual Studio Code bearbeitet werden, werden die Inhalte von VSCode an der Erweiterung gesendet.</span><span class="sxs-lookup"><span data-stu-id="3e545-144">When scripts are edited in VSCode, the contents are sent by VSCode to the extension.</span></span> <span data-ttu-id="3e545-145">Die [Sprachserverprotokoll][] ist es erforderlich, dass dieser Inhalt in UTF-8 übertragen wird.</span><span class="sxs-lookup"><span data-stu-id="3e545-145">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="3e545-146">Aus diesem Grund ist es nicht möglich, für die Erweiterung aus, um die falsche Codierung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="3e545-146">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
2. <span data-ttu-id="3e545-147">Wenn Skripts direkt in die integrierte Konsole ausgeführt werden, können sie die Datei von PowerShell direkt gelesen werden.</span><span class="sxs-lookup"><span data-stu-id="3e545-147">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="3e545-148">Tf PowerShells Codierung unterscheidet sich die VSCode, etwas kann hier falsch.</span><span class="sxs-lookup"><span data-stu-id="3e545-148">Tf PowerShell's encoding differs from VSCode's, something can go wrong here.</span></span>
3. <span data-ttu-id="3e545-149">Wenn ein Skript, das in Visual Studio Code geöffnet ist ein weiteres Skript, das nicht in Visual Studio Code geöffnet ist verweist, fragt die Erweiterung des Skripts Inhalt aus dem Dateisystem geladen.</span><span class="sxs-lookup"><span data-stu-id="3e545-149">When a script that is open in VSCode references another script that is not open in VSCode, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="3e545-150">Die PowerShell-Erweiterung standardmäßig UTF-8-Codierung, verwendet jedoch [Bytereihenfolge-Marke][], oder die BOM, Erkennung, um die richtige Codierung auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="3e545-150">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="3e545-151">Das Problem tritt auf, wenn vorausgesetzt, die Codierung der BOM-freie Formate (z. B. [UTF-8][] ohne BOM und [Windows-1252][]).</span><span class="sxs-lookup"><span data-stu-id="3e545-151">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span>
<span data-ttu-id="3e545-152">Die PowerShell-Erweiterung standardmäßig in UTF-8.</span><span class="sxs-lookup"><span data-stu-id="3e545-152">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="3e545-153">Die Erweiterung kann VSCodes-codierungseinstellungen nicht ändern.</span><span class="sxs-lookup"><span data-stu-id="3e545-153">The extension cannot change VSCode's encoding settings.</span></span>
<span data-ttu-id="3e545-154">Weitere Informationen finden Sie unter [Problem #824](https://github.com/Microsoft/vscode/issues/824).</span><span class="sxs-lookup"><span data-stu-id="3e545-154">For more information, see [issue #824](https://github.com/Microsoft/vscode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="3e545-155">Auswählen der richtigen Codierung</span><span class="sxs-lookup"><span data-stu-id="3e545-155">Choosing the right encoding</span></span>

<span data-ttu-id="3e545-156">Verschiedene Systeme und Anwendungen können unterschiedliche Codierungen verwenden:</span><span class="sxs-lookup"><span data-stu-id="3e545-156">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="3e545-157">In .NET Standard ist im Web, und klicken Sie in der Linux-Welt UTF-8 jetzt die vorherrschende Codierung.</span><span class="sxs-lookup"><span data-stu-id="3e545-157">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="3e545-158">Viele .NET Framework-Anwendungen verwenden die [UTF-16][].</span><span class="sxs-lookup"><span data-stu-id="3e545-158">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="3e545-159">Aus Verlaufsgründen, dies wird manchmal als "Unicode" bezeichnet, ein Begriff, die jetzt bezieht sich auf eine große Bandbreite an [standard](https://en.wikipedia.org/wiki/Unicode) , enthält sowohl UTF-8 und UTF-16.</span><span class="sxs-lookup"><span data-stu-id="3e545-159">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="3e545-160">Auf Windows weiterhin viele native Anwendungen, die Unicode sind älter als Windows-1252 wird standardmäßig verwendet.</span><span class="sxs-lookup"><span data-stu-id="3e545-160">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="3e545-161">Unicode-Codierungen können auch das Konzept Byte-Order mark, (BOM).</span><span class="sxs-lookup"><span data-stu-id="3e545-161">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="3e545-162">Stücklisten treten am Anfang von Text in einem Decoder mitteilen, welche Codierung, die der Text verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3e545-162">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="3e545-163">Für Multibyte-Codierungen, die BOM gibt auch an [endiancharakteristik](https://en.wikipedia.org/wiki/Endianness) der Codierung.</span><span class="sxs-lookup"><span data-stu-id="3e545-163">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="3e545-164">Stücklisten dienen als Bytes, die nur selten in nicht-Unicode-Text auftreten, sodass eine sinnvolle Prognose, dass Text Unicode ist, wenn eine BOM vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3e545-164">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="3e545-165">Stücklisten sind optional, und der Einführung ist in der Linux-Welt so beliebt, da eine verlässliche Konvention UTF-8 überall dort verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3e545-165">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="3e545-166">Die meisten Linux-Anwendungen wird davon ausgegangen, dass die Texteingabe in UTF-8 codiert ist.</span><span class="sxs-lookup"><span data-stu-id="3e545-166">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="3e545-167">Während viele Linux-Anwendungen werden erkannt und ordnungsgemäß verarbeiten, eine Bytereihenfolge-Marke, eine Zahl ist dies nicht zu Artefakten in Text, die mit diesen Anwendungen bearbeitet.</span><span class="sxs-lookup"><span data-stu-id="3e545-167">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="3e545-168">**Deshalb gilt Folgendes**:</span><span class="sxs-lookup"><span data-stu-id="3e545-168">**Therefore**:</span></span>

- <span data-ttu-id="3e545-169">Wenn Sie sich in erster Linie mit Windows-Anwendungen und Windows PowerShell arbeiten, sollten Sie vorziehen, eine Codierung wie UTF-8 mit BOM oder UTF-16.</span><span class="sxs-lookup"><span data-stu-id="3e545-169">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="3e545-170">Wenn Sie plattformübergreifend arbeiten, sollten Sie die UTF-8 mit BOM vorziehen.</span><span class="sxs-lookup"><span data-stu-id="3e545-170">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="3e545-171">Wenn Sie sich in erster Linie in Linux zugeordneten Kontexte arbeiten, sollten Sie die UTF-8 ohne BOM vorziehen.</span><span class="sxs-lookup"><span data-stu-id="3e545-171">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="3e545-172">Windows-1252 und Lateinisch-1 sind im Wesentlichen ältere Codierungen, die Sie nach Möglichkeit vermeiden sollten.</span><span class="sxs-lookup"><span data-stu-id="3e545-172">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="3e545-173">Allerdings können einige älteren Windows-Anwendungen hängen von diesen.</span><span class="sxs-lookup"><span data-stu-id="3e545-173">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="3e545-174">Es ist auch erwähnenswert, dass das Signieren von Skripts ist [Codierung abhängiges](https://github.com/PowerShell/PowerShell/issues/3466), d. h. eine Änderung der Codierung eines signierten Skripts benötigen Erneutes Signieren.</span><span class="sxs-lookup"><span data-stu-id="3e545-174">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vscode"></a><span data-ttu-id="3e545-175">Konfigurieren von VSCode</span><span class="sxs-lookup"><span data-stu-id="3e545-175">Configuring VSCode</span></span>

<span data-ttu-id="3e545-176">VSCode die standardcodierung ist UTF-8 ohne BOM.</span><span class="sxs-lookup"><span data-stu-id="3e545-176">VSCode's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="3e545-177">Festzulegende [VSCode Codierung des][], wechseln Sie zu den Einstellungen für VSCode (<kbd>STRG<kbd>+</kbd>,</kbd>) und legen Sie die `"files.encoding"` Einstellung:</span><span class="sxs-lookup"><span data-stu-id="3e545-177">To set [VSCode's encoding][], go to the VSCode settings (<kbd>Ctrl<kbd>+</kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="3e545-178">Einige Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="3e545-178">Some possible values are:</span></span>

- <span data-ttu-id="3e545-179">`utf8`: [UTF-8] ohne BOM</span><span class="sxs-lookup"><span data-stu-id="3e545-179">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="3e545-180">`utf8bom`: [UTF-8] mit BOM</span><span class="sxs-lookup"><span data-stu-id="3e545-180">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="3e545-181">`utf16le`: Little-endian- [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="3e545-181">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="3e545-182">`utf16be`: Big-Endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="3e545-182">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="3e545-183">`windows1252`: [Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="3e545-183">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="3e545-184">Sie sollten eine Dropdownliste für diese erhalten, in der GUI-Ansicht oder vervollständigungen für sie in der JSON-Code anzeigen.</span><span class="sxs-lookup"><span data-stu-id="3e545-184">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="3e545-185">Sie können auch automatische Erkennung der Codierung Wenn möglich Folgendes hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="3e545-185">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="3e545-186">Wenn Sie nicht, dass diese Einstellungen beeinflussen alle Dateitypen möchten, ermöglicht es VSCode auch auf die sprachenspezifische Konfigurationen aus.</span><span class="sxs-lookup"><span data-stu-id="3e545-186">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="3e545-187">Erstellen Sie eine sprachspezifische-Einstellung, indem Sie die Einstellungen im Platzieren einer `[<language-name>]` Feld.</span><span class="sxs-lookup"><span data-stu-id="3e545-187">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="3e545-188">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="3e545-188">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="3e545-189">Konfigurieren von PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e545-189">Configuring PowerShell</span></span>

<span data-ttu-id="3e545-190">PowerShell standardcodierung variiert je nach Version:</span><span class="sxs-lookup"><span data-stu-id="3e545-190">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="3e545-191">In PowerShell 6 und höher ist die standardcodierung UTF-8 ohne BOM auf allen Plattformen.</span><span class="sxs-lookup"><span data-stu-id="3e545-191">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="3e545-192">In Windows PowerShell die standardcodierung ist in der Regel Windows-1252, eine Erweiterung der [latin-1][], auch bekannt als ISO 8859-1.</span><span class="sxs-lookup"><span data-stu-id="3e545-192">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="3e545-193">Finden Sie in PowerShell 5 + standardcodierung dabei:</span><span class="sxs-lookup"><span data-stu-id="3e545-193">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="3e545-194">Die folgenden [Skript](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) kann verwendet werden, um zu bestimmen, was die Codierung der PowerShell-Sitzungs ein Skript ohne Bytereihenfolge-Marke leitet.</span><span class="sxs-lookup"><span data-stu-id="3e545-194">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

<span data-ttu-id="3e545-195">Es ist möglich, PowerShell, um die Verwendung einer bestimmten Codierung unter Verwendung allgemeiner profileinstellungen zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="3e545-195">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span> <span data-ttu-id="3e545-196">Weitere Informationen finden Sie in folgenden Artikeln:</span><span class="sxs-lookup"><span data-stu-id="3e545-196">See the following articles:</span></span>

- <span data-ttu-id="3e545-197">[@mklement0]die [Antworten zu den PowerShell-Codierung auf StackOverflow](https://stackoverflow.com/a/40098904).</span><span class="sxs-lookup"><span data-stu-id="3e545-197">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="3e545-198">[@rkeithhill]die [Blogbeitrag zum Umgang mit BOM-freie UTF-8-Eingabe in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span><span class="sxs-lookup"><span data-stu-id="3e545-198">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="3e545-199">Es ist nicht möglich, um PowerShell für eine bestimmte Eingabe-Codierung verwendet wird, zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="3e545-199">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="3e545-200">PowerShell 5.1 und unten standardmäßig die Windows-1252-Codierung, wenn keine BOM vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3e545-200">PowerShell 5.1 and below default to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="3e545-201">Aus Gründen der Interoperabilität empfiehlt es sich um Skripts in einem Unicode-Format mit einer BOM speichern.</span><span class="sxs-lookup"><span data-stu-id="3e545-201">For interoperability reasons, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e545-202">Von anderen Tools müssen Sie, dass die Fingereingabe PowerShell-Skripts können durch Ihre codierungsmöglichkeiten beeinflusst werden, oder erneut codieren Ihre Skripts in eine andere Codierung.</span><span class="sxs-lookup"><span data-stu-id="3e545-202">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="3e545-203">Vorhandene Skripts</span><span class="sxs-lookup"><span data-stu-id="3e545-203">Existing scripts</span></span>

<span data-ttu-id="3e545-204">Skripts, die bereits auf dem Dateisystem möglicherweise erneut auf die neue ausgewählte Codierung codiert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="3e545-204">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="3e545-205">In der unteren Leiste von Visual Studio Code sehen Sie die Bezeichnung UTF-8.</span><span class="sxs-lookup"><span data-stu-id="3e545-205">In the bottom bar of VSCode, you'll see the label UTF-8.</span></span> <span data-ttu-id="3e545-206">Klicken Sie auf, um der Aktionsleiste öffnen, und wählen **mit Codierung speichern**.</span><span class="sxs-lookup"><span data-stu-id="3e545-206">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="3e545-207">Sie können jetzt auswählen, eine neue Codierung für diese Datei.</span><span class="sxs-lookup"><span data-stu-id="3e545-207">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="3e545-208">Finden Sie unter [VSCode Codierung des][] ausführliche Anleitungen.</span><span class="sxs-lookup"><span data-stu-id="3e545-208">See [VSCode's encoding][] for full instructions.</span></span>

<span data-ttu-id="3e545-209">Wenn Sie mehrere Dateien erneut codieren müssen, können Sie das folgende Skript aus:</span><span class="sxs-lookup"><span data-stu-id="3e545-209">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="3e545-210">PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="3e545-210">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="3e545-211">Wenn Sie auch Skripts mithilfe der PowerShell ISE bearbeiten, müssen Sie Ihre Codierung Einstellungen synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="3e545-211">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="3e545-212">Die ISE sollte eine Bytereihenfolge-Marke berücksichtigt, aber es ist auch möglich, verwenden Reflektion, um [legen Sie die Codierung](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span><span class="sxs-lookup"><span data-stu-id="3e545-212">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="3e545-213">Beachten Sie, dass dies zwischen Start-UPS beibehalten werden, wäre nicht.</span><span class="sxs-lookup"><span data-stu-id="3e545-213">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="3e545-214">Software für die quellcodeverwaltung</span><span class="sxs-lookup"><span data-stu-id="3e545-214">Source control software</span></span>

<span data-ttu-id="3e545-215">Einige quellcodeverwaltungstools wie Git, ignorieren Sie Codierungen. Git verfolgt nur die Bytes.</span><span class="sxs-lookup"><span data-stu-id="3e545-215">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span>
<span data-ttu-id="3e545-216">Andere, wie TFS oder Mercurial, sind nicht dazu berechtigt.</span><span class="sxs-lookup"><span data-stu-id="3e545-216">Others, like TFS or Mercurial, may not.</span></span> <span data-ttu-id="3e545-217">Decodieren von Text ist sogar einige Git-basierten Tools abhängig.</span><span class="sxs-lookup"><span data-stu-id="3e545-217">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="3e545-218">Wenn dies der Fall ist, stellen Sie sicher, dass Sie:</span><span class="sxs-lookup"><span data-stu-id="3e545-218">When this is the case, make sure you:</span></span>

- <span data-ttu-id="3e545-219">Konfigurieren Sie die textcodierung, die in Ihrer quellcodeverwaltung entsprechend Ihrem VSCode-Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="3e545-219">Configure the text encoding in your source control to match your VSCode configuration.</span></span>
- <span data-ttu-id="3e545-220">Stellen Sie sicher, dass alle Dateien in die quellcodeverwaltung in der relevanten Codierung aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="3e545-220">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="3e545-221">Seien Sie vorsichtig bei der Änderungen in die Codierung, die über die quellcodeverwaltung empfangen wurden.</span><span class="sxs-lookup"><span data-stu-id="3e545-221">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="3e545-222">Ein Schlüssel Anzeichen für dieses werden einen Vergleich, der angibt, ändert sich jedoch, in denen anscheinend nichts geändert haben (da Bytes enthalten, aber Zeichen nicht enthalten).</span><span class="sxs-lookup"><span data-stu-id="3e545-222">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="3e545-223">Wort-Umgebungen</span><span class="sxs-lookup"><span data-stu-id="3e545-223">Collaborators' environments</span></span>

<span data-ttu-id="3e545-224">Über das Konfigurieren der quellcodeverwaltung, stellen Sie sicher, dass Ihre Mitarbeiter auf alle Dateien, die Sie freigeben Einstellungen, die die Codierung vorhanden sind von neu codieren zu PowerShell-Dateien zu überschreiben.</span><span class="sxs-lookup"><span data-stu-id="3e545-224">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="3e545-225">Andere Programme</span><span class="sxs-lookup"><span data-stu-id="3e545-225">Other programs</span></span>

<span data-ttu-id="3e545-226">Jedes andere Programm, das Lesen oder schreiben ein PowerShell-Skript kann es erneut zu codieren.</span><span class="sxs-lookup"><span data-stu-id="3e545-226">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="3e545-227">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="3e545-227">Some examples are:</span></span>

- <span data-ttu-id="3e545-228">Verwenden der Zwischenablage zu kopieren und fügen ein Skript.</span><span class="sxs-lookup"><span data-stu-id="3e545-228">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="3e545-229">Dies ist häufig in Szenarien wie etwa:</span><span class="sxs-lookup"><span data-stu-id="3e545-229">This is common in scenarios like:</span></span>
  - <span data-ttu-id="3e545-230">Kopieren ein Skript in einem virtuellen Computer</span><span class="sxs-lookup"><span data-stu-id="3e545-230">Copying a script into a VM</span></span>
  - <span data-ttu-id="3e545-231">Kopieren ein Skript aus einer e-Mail oder einer Webseite</span><span class="sxs-lookup"><span data-stu-id="3e545-231">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="3e545-232">Kopieren ein Skript aus, in oder aus einem Microsoft Word oder PowerPoint-Dokument</span><span class="sxs-lookup"><span data-stu-id="3e545-232">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="3e545-233">Weitere Text-Editoren, z. B.:</span><span class="sxs-lookup"><span data-stu-id="3e545-233">Other text editors, such as:</span></span>
  - <span data-ttu-id="3e545-234">Editor</span><span class="sxs-lookup"><span data-stu-id="3e545-234">Notepad</span></span>
  - <span data-ttu-id="3e545-235">vim</span><span class="sxs-lookup"><span data-stu-id="3e545-235">vim</span></span>
  - <span data-ttu-id="3e545-236">Alle anderen PowerShell-Skript-editor</span><span class="sxs-lookup"><span data-stu-id="3e545-236">Any other PowerShell script editor</span></span>
- <span data-ttu-id="3e545-237">Textbearbeitung Hilfsprogramme, z.B.:</span><span class="sxs-lookup"><span data-stu-id="3e545-237">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="3e545-238">Wie Sie PowerShell Umleitungsoperatoren `>` und `>>`</span><span class="sxs-lookup"><span data-stu-id="3e545-238">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="3e545-239">File Transfer-Programme, z. B.:</span><span class="sxs-lookup"><span data-stu-id="3e545-239">File transfer programs, like:</span></span>
  - <span data-ttu-id="3e545-240">Einen Webbrowser, der beim Herunterladen von Skripts</span><span class="sxs-lookup"><span data-stu-id="3e545-240">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="3e545-241">Eine Dateifreigabe</span><span class="sxs-lookup"><span data-stu-id="3e545-241">A file share</span></span>

<span data-ttu-id="3e545-242">Einige dieser Tools behandeln, in Byte anstatt von Text, aber andere Codierung Konfigurationen bieten.</span><span class="sxs-lookup"><span data-stu-id="3e545-242">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="3e545-243">In diesen Fällen Sie eine Codierung zu konfigurieren müssen, müssen Sie dafür identisch mit den Editor Codierung, um Probleme zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="3e545-243">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="3e545-244">Weitere Ressourcen für die Codierung in PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e545-244">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="3e545-245">Es gibt einige andere nützliche Beiträge zu codieren, und konfigurieren die Codierung in PowerShell, die zu lesen sind:</span><span class="sxs-lookup"><span data-stu-id="3e545-245">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="3e545-246">[@mklement0]die [Zusammenfassung der PowerShell-Codierung auf StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="3e545-246">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="3e545-247">Frühere Ausgaben, die auf Vscode-PowerShell für die Codierung Probleme geöffnet werden:</span><span class="sxs-lookup"><span data-stu-id="3e545-247">Previous issues opened on vscode-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="3e545-248">#1308</span><span class="sxs-lookup"><span data-stu-id="3e545-248">#1308</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [<span data-ttu-id="3e545-249">#1628</span><span class="sxs-lookup"><span data-stu-id="3e545-249">#1628</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [<span data-ttu-id="3e545-250">#1680</span><span class="sxs-lookup"><span data-stu-id="3e545-250">#1680</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [<span data-ttu-id="3e545-251">#1744</span><span class="sxs-lookup"><span data-stu-id="3e545-251">#1744</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [<span data-ttu-id="3e545-252">#1751</span><span class="sxs-lookup"><span data-stu-id="3e545-252">#1751</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [<span data-ttu-id="3e545-253">Das klassische *Joel on Software* zu schreiben, zu Unicode</span><span class="sxs-lookup"><span data-stu-id="3e545-253">The classic *Joel on Software* write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="3e545-254">Im .NET Standard-Codierung</span><span class="sxs-lookup"><span data-stu-id="3e545-254">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[Bytereihenfolge-Marke]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Sprachserverprotokoll]: https://microsoft.github.io/language-server-protocol/
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[VSCode Codierung des]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VSCode's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support