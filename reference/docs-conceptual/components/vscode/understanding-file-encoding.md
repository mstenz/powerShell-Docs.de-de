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
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a>Grundlegendes zur Dateicodierung in VSCode und PowerShell

Beim Verwenden von VS Code zum Erstellen und bearbeiten die PowerShell-Skripts ist es wichtig, dass Ihre Dateien gespeichert werden, verwenden das richtige Zeichen-Codierungsformat.

## <a name="what-is-file-encoding-and-why-is-it-important"></a>Was ist die dateicodierung, und warum es wichtig ist?

VSCode verwaltet die Schnittstelle zwischen einer menschlichen eingeben Zeichenfolgen mit Zeichen in einen Puffer und Byteblöcken lesen und Schreiben in das Dateisystem. Wenn eine Datei in VSCode gespeichert wird, wird eine textcodierung, die zu diesem Zweck verwendet.

Bei Ausführung eines Skripts durch PowerShell müssen sie auf ähnliche Weise die Bytes in einer Datei in Zeichen, die Datei in ein PowerShell-Programm zu rekonstruieren konvertieren. Da VSCode die Datei schreibt, und PowerShell die Datei liest, müssen sie das gleiche System für die Codierung zu verwenden. Wird diese Art der Analyse ein PowerShell-Skript: *Bytes* -> *Zeichen* -> *Token*  ->   *abstrakte Syntaxstruktur* -> *Ausführung*.

Mit einer sinnvolle Codierung Standardkonfiguration werden sowohl PowerShell als auch VSCode installiert. Allerdings hat die standardcodierung verwendet, die von PowerShell mit der Version von PowerShell Core (Version 6.x) geändert. Um sicherzustellen, dass keine Probleme, die mithilfe von PowerShell oder die PowerShell-Erweiterung in Visual Studio Code haben, müssen Sie zum Konfigurieren der Einstellungen für VSCode und PowerShell ordnungsgemäß.

## <a name="common-causes-of-encoding-issues"></a>Häufige Ursachen für Probleme-Codierung

Codierung Probleme auftreten, wenn die Codierung des VSCode oder Ihre Skriptdatei nicht übereinstimmt, ist die erwartete Codierung von PowerShell. Es gibt keine Möglichkeit für PowerShell, um die dateicodierung automatisch zu ermitteln.

Sie sind eher selten Codierung Probleme bei der Verwendung von Zeichen, die nicht in der [7-Bit-ASCII-Zeichensatz](https://ascii.cl/). Beispiel:

- Akzent lateinische Zeichen (`É`, `ü`)
- Nicht-lateinische Zeichen wie Kyrillisch (`Д`, `Ц`)
- Han Chinesisch (`脚`, `本`)

Häufige Gründe für die Codierung Probleme sind:

- Die Codierungen von VSCode und PowerShell wurden die Standardeinstellungen nicht geändert wurde. Für PowerShell 5.1 oder unterhalb der Standardkapazität ist die Codierung VSCodes unterscheidet.
- Einem anderen Editor wurden geöffnet und die Datei in eine neue Codierung überschrieben. Dies geschieht häufig mit der ISE.
- Die Datei wird überprüft, in die quellcodeverwaltung in einer Codierung, die sich unterscheidet, von welcher VSCode oder PowerShell erwartet. Dies kann passieren, wenn Mitarbeiter Editoren mit unterschiedlichen Codierung Konfigurationen verwenden.

### <a name="how-to-tell-when-you-have-encoding-issues"></a>Wie Sie feststellen, wenn die Codierung Probleme haben

Häufig Codierungsfehler bieten sich die als Fehler in Skripts analysiert. Wenn Sie in Ihrem Skript seltsame Zeichensequenzen finden, kann dies das Problem sein. Im folgenden Beispiel wird ein Gedankenstrich (`–`) wird angezeigt als Zeichen `â€“`:

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

Dieses Problem tritt auf, da VSCode das Zeichen codiert `–` in UTF-8, wie die Bytes `0xE2 0x80 0x93`.
Wenn diese Bytes als Windows-1252 decodiert werden, werden sie als Zeichen interpretiert `â€“`.

Einige ungewöhnliche Zeichensequenzen, die möglicherweise gehören:

- `â€“` anstelle von `–`
- `â€”` anstelle von `—`
- `Ã„2` anstelle von `Ä`
- `Â` anstelle von ` ` (geschütztes Leerzeichen)
- `Ã©` anstelle von `é`

Diesem praktischen [Verweis](https://www.i18nqa.com/debug/utf8-debug.html) listet häufige Muster angegeben, die eine Codierung UTF-8/Windows-1252-Problem hinweisen.

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a>Interaktion zwischen die PowerShell-Erweiterung in Visual Studio Code und Codierungen

Die PowerShell-Erweiterung interagiert mit Skripts in eine Reihe von Möglichkeiten:

1. Wenn Skripts in Visual Studio Code bearbeitet werden, werden die Inhalte von VSCode an der Erweiterung gesendet. Die [Sprachserverprotokoll][] ist es erforderlich, dass dieser Inhalt in UTF-8 übertragen wird. Aus diesem Grund ist es nicht möglich, für die Erweiterung aus, um die falsche Codierung zu erhalten.
2. Wenn Skripts direkt in die integrierte Konsole ausgeführt werden, können sie die Datei von PowerShell direkt gelesen werden. Tf PowerShells Codierung unterscheidet sich die VSCode, etwas kann hier falsch.
3. Wenn ein Skript, das in Visual Studio Code geöffnet ist ein weiteres Skript, das nicht in Visual Studio Code geöffnet ist verweist, fragt die Erweiterung des Skripts Inhalt aus dem Dateisystem geladen. Die PowerShell-Erweiterung standardmäßig UTF-8-Codierung, verwendet jedoch [Bytereihenfolge-Marke][], oder die BOM, Erkennung, um die richtige Codierung auszuwählen.

Das Problem tritt auf, wenn vorausgesetzt, die Codierung der BOM-freie Formate (z. B. [UTF-8][] ohne BOM und [Windows-1252][]).
Die PowerShell-Erweiterung standardmäßig in UTF-8. Die Erweiterung kann VSCodes-codierungseinstellungen nicht ändern.
Weitere Informationen finden Sie unter [Problem #824](https://github.com/Microsoft/vscode/issues/824).

## <a name="choosing-the-right-encoding"></a>Auswählen der richtigen Codierung

Verschiedene Systeme und Anwendungen können unterschiedliche Codierungen verwenden:

- In .NET Standard ist im Web, und klicken Sie in der Linux-Welt UTF-8 jetzt die vorherrschende Codierung.
- Viele .NET Framework-Anwendungen verwenden die [UTF-16][]. Aus Verlaufsgründen, dies wird manchmal als "Unicode" bezeichnet, ein Begriff, die jetzt bezieht sich auf eine große Bandbreite an [standard](https://en.wikipedia.org/wiki/Unicode) , enthält sowohl UTF-8 und UTF-16.
- Auf Windows weiterhin viele native Anwendungen, die Unicode sind älter als Windows-1252 wird standardmäßig verwendet.

Unicode-Codierungen können auch das Konzept Byte-Order mark, (BOM). Stücklisten treten am Anfang von Text in einem Decoder mitteilen, welche Codierung, die der Text verwendet wird. Für Multibyte-Codierungen, die BOM gibt auch an [endiancharakteristik](https://en.wikipedia.org/wiki/Endianness) der Codierung. Stücklisten dienen als Bytes, die nur selten in nicht-Unicode-Text auftreten, sodass eine sinnvolle Prognose, dass Text Unicode ist, wenn eine BOM vorhanden ist.

Stücklisten sind optional, und der Einführung ist in der Linux-Welt so beliebt, da eine verlässliche Konvention UTF-8 überall dort verwendet wird. Die meisten Linux-Anwendungen wird davon ausgegangen, dass die Texteingabe in UTF-8 codiert ist. Während viele Linux-Anwendungen werden erkannt und ordnungsgemäß verarbeiten, eine Bytereihenfolge-Marke, eine Zahl ist dies nicht zu Artefakten in Text, die mit diesen Anwendungen bearbeitet.

**Deshalb gilt Folgendes**:

- Wenn Sie sich in erster Linie mit Windows-Anwendungen und Windows PowerShell arbeiten, sollten Sie vorziehen, eine Codierung wie UTF-8 mit BOM oder UTF-16.
- Wenn Sie plattformübergreifend arbeiten, sollten Sie die UTF-8 mit BOM vorziehen.
- Wenn Sie sich in erster Linie in Linux zugeordneten Kontexte arbeiten, sollten Sie die UTF-8 ohne BOM vorziehen.
- Windows-1252 und Lateinisch-1 sind im Wesentlichen ältere Codierungen, die Sie nach Möglichkeit vermeiden sollten.
  Allerdings können einige älteren Windows-Anwendungen hängen von diesen.
- Es ist auch erwähnenswert, dass das Signieren von Skripts ist [Codierung abhängiges](https://github.com/PowerShell/PowerShell/issues/3466), d. h. eine Änderung der Codierung eines signierten Skripts benötigen Erneutes Signieren.

## <a name="configuring-vscode"></a>Konfigurieren von VSCode

VSCode die standardcodierung ist UTF-8 ohne BOM.

Festzulegende [VSCode Codierung des][], wechseln Sie zu den Einstellungen für VSCode (<kbd>STRG<kbd>+</kbd>,</kbd>) und legen Sie die `"files.encoding"` Einstellung:

```json
"files.encoding": "utf8bom"
```

Einige Werte sind möglich:

- `utf8`: [UTF-8] ohne BOM
- `utf8bom`: [UTF-8] mit BOM
- `utf16le`: Little-endian- [UTF-16]
- `utf16be`: Big-Endian [UTF-16]
- `windows1252`: [Windows-1252]

Sie sollten eine Dropdownliste für diese erhalten, in der GUI-Ansicht oder vervollständigungen für sie in der JSON-Code anzeigen.

Sie können auch automatische Erkennung der Codierung Wenn möglich Folgendes hinzufügen:

```json
"files.autoGuessEncoding": true
```

Wenn Sie nicht, dass diese Einstellungen beeinflussen alle Dateitypen möchten, ermöglicht es VSCode auch auf die sprachenspezifische Konfigurationen aus. Erstellen Sie eine sprachspezifische-Einstellung, indem Sie die Einstellungen im Platzieren einer `[<language-name>]` Feld. Beispiel:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>Konfigurieren von PowerShell

PowerShell standardcodierung variiert je nach Version:

- In PowerShell 6 und höher ist die standardcodierung UTF-8 ohne BOM auf allen Plattformen.
- In Windows PowerShell die standardcodierung ist in der Regel Windows-1252, eine Erweiterung der [latin-1][], auch bekannt als ISO 8859-1.

Finden Sie in PowerShell 5 + standardcodierung dabei:

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

Die folgenden [Skript](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) kann verwendet werden, um zu bestimmen, was die Codierung der PowerShell-Sitzungs ein Skript ohne Bytereihenfolge-Marke leitet.

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

Es ist möglich, PowerShell, um die Verwendung einer bestimmten Codierung unter Verwendung allgemeiner profileinstellungen zu konfigurieren. Weitere Informationen finden Sie in folgenden Artikeln:

- [@mklement0]die [Antworten zu den PowerShell-Codierung auf StackOverflow](https://stackoverflow.com/a/40098904).
- [@rkeithhill]die [Blogbeitrag zum Umgang mit BOM-freie UTF-8-Eingabe in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).

Es ist nicht möglich, um PowerShell für eine bestimmte Eingabe-Codierung verwendet wird, zu erzwingen. PowerShell 5.1 und unten standardmäßig die Windows-1252-Codierung, wenn keine BOM vorhanden ist. Aus Gründen der Interoperabilität empfiehlt es sich um Skripts in einem Unicode-Format mit einer BOM speichern.

> [!IMPORTANT]
> Von anderen Tools müssen Sie, dass die Fingereingabe PowerShell-Skripts können durch Ihre codierungsmöglichkeiten beeinflusst werden, oder erneut codieren Ihre Skripts in eine andere Codierung.

### <a name="existing-scripts"></a>Vorhandene Skripts

Skripts, die bereits auf dem Dateisystem möglicherweise erneut auf die neue ausgewählte Codierung codiert werden müssen. In der unteren Leiste von Visual Studio Code sehen Sie die Bezeichnung UTF-8. Klicken Sie auf, um der Aktionsleiste öffnen, und wählen **mit Codierung speichern**. Sie können jetzt auswählen, eine neue Codierung für diese Datei. Finden Sie unter [VSCode Codierung des][] ausführliche Anleitungen.

Wenn Sie mehrere Dateien erneut codieren müssen, können Sie das folgende Skript aus:

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>PowerShell Integrated Scripting Environment (ISE)

Wenn Sie auch Skripts mithilfe der PowerShell ISE bearbeiten, müssen Sie Ihre Codierung Einstellungen synchronisieren.

Die ISE sollte eine Bytereihenfolge-Marke berücksichtigt, aber es ist auch möglich, verwenden Reflektion, um [legen Sie die Codierung](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).
Beachten Sie, dass dies zwischen Start-UPS beibehalten werden, wäre nicht.

### <a name="source-control-software"></a>Software für die quellcodeverwaltung

Einige quellcodeverwaltungstools wie Git, ignorieren Sie Codierungen. Git verfolgt nur die Bytes.
Andere, wie TFS oder Mercurial, sind nicht dazu berechtigt. Decodieren von Text ist sogar einige Git-basierten Tools abhängig.

Wenn dies der Fall ist, stellen Sie sicher, dass Sie:

- Konfigurieren Sie die textcodierung, die in Ihrer quellcodeverwaltung entsprechend Ihrem VSCode-Konfiguration.
- Stellen Sie sicher, dass alle Dateien in die quellcodeverwaltung in der relevanten Codierung aktiviert sind.
- Seien Sie vorsichtig bei der Änderungen in die Codierung, die über die quellcodeverwaltung empfangen wurden. Ein Schlüssel Anzeichen für dieses werden einen Vergleich, der angibt, ändert sich jedoch, in denen anscheinend nichts geändert haben (da Bytes enthalten, aber Zeichen nicht enthalten).

### <a name="collaborators-environments"></a>Wort-Umgebungen

Über das Konfigurieren der quellcodeverwaltung, stellen Sie sicher, dass Ihre Mitarbeiter auf alle Dateien, die Sie freigeben Einstellungen, die die Codierung vorhanden sind von neu codieren zu PowerShell-Dateien zu überschreiben.

### <a name="other-programs"></a>Andere Programme

Jedes andere Programm, das Lesen oder schreiben ein PowerShell-Skript kann es erneut zu codieren.

Beispiele:

- Verwenden der Zwischenablage zu kopieren und fügen ein Skript. Dies ist häufig in Szenarien wie etwa:
  - Kopieren ein Skript in einem virtuellen Computer
  - Kopieren ein Skript aus einer e-Mail oder einer Webseite
  - Kopieren ein Skript aus, in oder aus einem Microsoft Word oder PowerPoint-Dokument
- Weitere Text-Editoren, z. B.:
  - Editor
  - vim
  - Alle anderen PowerShell-Skript-editor
- Textbearbeitung Hilfsprogramme, z.B.:
  - `Get-Content`/`Set-Content`/`Out-File`
  - Wie Sie PowerShell Umleitungsoperatoren `>` und `>>`
  - `sed`/`awk`
- File Transfer-Programme, z. B.:
  - Einen Webbrowser, der beim Herunterladen von Skripts
  - Eine Dateifreigabe

Einige dieser Tools behandeln, in Byte anstatt von Text, aber andere Codierung Konfigurationen bieten. In diesen Fällen Sie eine Codierung zu konfigurieren müssen, müssen Sie dafür identisch mit den Editor Codierung, um Probleme zu vermeiden.

## <a name="other-resources-on-encoding-in-powershell"></a>Weitere Ressourcen für die Codierung in PowerShell

Es gibt einige andere nützliche Beiträge zu codieren, und konfigurieren die Codierung in PowerShell, die zu lesen sind:

- [@mklement0]die [Zusammenfassung der PowerShell-Codierung auf StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- Frühere Ausgaben, die auf Vscode-PowerShell für die Codierung Probleme geöffnet werden:
  - [#1308](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [Das klassische *Joel on Software* zu schreiben, zu Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [Im .NET Standard-Codierung](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[Bytereihenfolge-Marke]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Sprachserverprotokoll]: https://microsoft.github.io/language-server-protocol/
[VSCode Codierung des]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support