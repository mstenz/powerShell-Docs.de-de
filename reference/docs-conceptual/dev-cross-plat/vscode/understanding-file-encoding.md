---
title: Grundlegendes zur Dateicodierung in VS Code und PowerShell
description: Konfigurieren der Dateicodierung in VS Code und PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: 1333c5aedd5abd16078ac32979f19f38818a26c8
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809896"
---
# <a name="understanding-file-encoding-in-vs-code-and-powershell"></a>Grundlegendes zur Dateicodierung in VS Code und PowerShell

Wenn Sie mit VS Code PowerShell-Skripts erstellen und bearbeiten, ist es wichtig, dass Ihre Dateien im korrekten Zeichencodierungsformat gespeichert werden.

## <a name="what-is-file-encoding-and-why-is-it-important"></a>Was ist die Dateicodierung und weshalb ist sie wichtig?

VS Code fungiert als Schnittstelle zwischen einem Menschen, der Zeichenfolgen in einen Puffer eingibt, und dem Lesen/Schreiben von Byteblocks in das Dateisystem. Wenn VS Code eine Datei speichert, wird mithilfe einer Textcodierung festgelegt, in welche Bytes jedes Zeichen umgewandelt wird.

Wenn PowerShell ein Skript ausführt, muss es die Bytes in einer Datei entsprechend in Zeichen konvertieren, um die Datei in einem PowerShell-Programm zu rekonstruieren. Da VS Code die Datei schreibt und PowerShell diese liest, müssen sie dasselbe Codierungssystem verwenden. Die Analyse eines PowerShell-Skripts sieht folgendermaßen aus: *Bytes* -> *Zeichen* -> *Token* -> *abstrakte Syntaxstruktur* -> *Ausführung*.

Sowohl VS Code als auch PowerShell werden mit einer zweckmäßigen Standardcodierungskonfiguration installiert. Mit der Veröffentlichung von PowerShell Core v6.x hat sich die Standardcodierung von PowerShell jedoch geändert. Legen Sie Ihre VS Code- und PowerShell-Einstellungen entsprechend fest, um sicherzustellen, dass bei der Verwendung von PowerShell oder einer PowerShell-Erweiterung in VS Code keine Probleme auftreten.

## <a name="common-causes-of-encoding-issues"></a>Häufige Gründe für Codierungsprobleme

Codierungsprobleme treten auf, wenn die Codierung von VS Code oder der Skriptdatei nicht der Codierung entspricht, die von PowerShell erwartet wird. PowerShell hat keine Möglichkeit, die Dateicodierung automatisch zu bestimmen.

Es ist wahrscheinlicher, dass Codierungsprobleme auftreten, wenn Sie Zeichen verwenden, die nicht im [7-Bit-ASCII-Zeichensatz](https://ascii.cl/) enthalten sind. Beispiel:

<!-- markdownlint-disable MD038 -->
- Erweiterte Zeichen, bei denen es sich nicht um Buchstaben handelt – z. B. Geviertstrich (`—`), geschützte Leerzeichen (` `) oder doppelte linke Anführungszeichen (`"`)
- Lateinische Buchstaben mit Akzenten und Umlaute (`É`, `ü`)
- Nicht lateinische Zeichen wie Kyrillisch (`Д`, `Ц`)
- CJK-Zeichen (`本`, `화`, `が`)

Aus den folgenden Gründen kann es zu Codierungsproblemen kommen:

- Die Codierungen von VS Code und PowerShell weisen immer noch die Standardeinstellungen auf. Für PowerShell 5.1 und früher unterscheidet sich die Standardcodierung von derjenigen von VS Code.
- Ein weiterer Editor wurde geöffnet und hat die Datei in einer neuen Codierung überschrieben. Dies geschieht häufig mit der ISE.
- Die Datei wird in der Quellcodeverwaltung in einer Codierung eingecheckt, die sich von der von VS Code bzw. PowerShell erwarteten Codierung unterscheidet. Das kann passieren, wenn Beteiligte einen Editor mit anderen Codierungskonfigurationen verwenden.

### <a name="how-to-tell-when-you-have-encoding-issues"></a>Erkennen von Codierungsproblemen

Codierungsfehler treten häufig als Analysefehler in Skripts auf. Wenn Sie in Ihren Skripts ungewöhnliche Zeichensequenzen sehen, kann das der Grund für das Problem sein. Im Beispiel unten wird ein Halbgeviertstrich (`–`) als `â&euro;"` angezeigt:

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â&euro;"From $from â&euro;"To $recipient1 â&euro;"Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

Dieses Problem tritt auf, weil VS Code das Zeichen `–` in UTF-8 als `0xE2 0x80 0x93` codiert. Wenn diese Bytes als Windows-1252 decodiert werden, werden sie als die Zeichen `â&euro;"` interpretiert.

Weitere ungewöhnliche Zeichensequenzen, die Sie eventuell sehen, sind die folgenden:

<!-- markdownlint-disable MD038 -->
- `â&euro;"` anstelle von `–`
- `â&euro;"` anstelle von `—`
- `Ã„2` anstelle von `Ä`
- `Â` anstelle von ` ` (ein geschütztes Leerzeichen)
- `Ã&copy;` anstelle von `é`
<!-- markdownlint-enable MD038 -->

In dieser praktischen [Referenz](https://www.i18nqa.com/debug/utf8-debug.html) werden gängige Muster aufgelistet, die auf Codierungsprobleme zwischen UTF-8 und Windows-1252 hindeuten.

## <a name="how-the-powershell-extension-in-vs-code-interacts-with-encodings"></a>Interaktion der PowerShell-Erweiterung in VS Code mit Codierungen

Die PowerShell-Erweiterung interagiert auf unterschiedliche Weise mit den Skripts:

1. Wenn Skripts in VS Code bearbeitet werden, werden die Inhalte von VS Code an die Erweiterung gesendet. Das [Sprachserverprotokoll][] gibt vor, dass dieser Inhalt in UTF-8 übertragen wird. Deshalb ist es gar nicht möglich, dass die Erweiterung den Inhalt in einer falschen Codierung erhält.
2. Wenn Skripts direkt in der integrierten Konsole ausgeführt werden, liest PowerShell diese direkt aus der Datei. Wenn die Codierung von PowerShell sich von derjenigen von VS Code unterscheidet, kann es zu Problemen kommen.
3. Wenn ein Skript, das in VS Code geöffnet wird, auf ein anderes Skript verweist, das nicht in VS Code geöffnet ist, lädt die Erweiterung den Inhalt dieses Skripts aus dem Dateisystem. Die Standardeinstellung der PowerShell-Erweiterung ist UTF-8. Die Erkennung der [Bytereihenfolge-Marke][] oder Byte-Order Mark (BOM) wird jedoch verwendet, um die korrekte Codierung auszuwählen.

Das Problem tritt auf, wenn die Codierung von Formaten ohne BOM angenommen wird (z.B. [UTF-8][] ohne BOM und [Windows-1252][]). Die Standardeinstellung der PowerShell-Erweiterung ist UTF-8. Die Erweiterung kann die Codierungseinstellungen von VS Code nicht ändern. Weitere Informationen finden Sie im [Issue #824](https://github.com/Microsoft/VSCode/issues/824).

## <a name="choosing-the-right-encoding"></a>Entscheidung für die richtige Codierung

Unterschiedliche Systeme und Anwendungen können unterschiedliche Codierungen verwenden:

- In .NET Standard, im Internet und im Zusammenhang mit Linux ist UTF-8 mittlerweile die häufigste Codierung.
- Viele .NET Framework-Anwendungen verwenden [UTF-16][]. Aus historischen Gründen wird dies manchmal als „Unicode“ bezeichnet, ein Begriff, der mittlerweile einen breiten [Standard](https://en.wikipedia.org/wiki/Unicode) bezeichnet, der sowohl UTF-8 als auch UTF-16 umfasst.
- Unter Windows verwenden native Anwendungen aus der Zeit vor Unicode weiterhin standardmäßig Windows-1252.

Unicodecodierungen verwenden auch Bytereihenfolge-Marken. BOMs stehen am Textanfang, um einen Decoder darüber zu informieren, welche Codierung verwendet wird. Für Mehrbytecodierungen gibt die BOM auch die [Bytereihenfolge](https://en.wikipedia.org/wiki/Endianness) der Codierung an. BOMs sollen Bytes sein, die nur selten in Nicht-Unicodetexten auftauchen, sodass eine vorhandene BOM darauf hinweist, dass ein Text mit hoher Wahrscheinlichkeit Unicode ist.

BOMs sind optional und ihre Verwendung ist im Linux-Kontext nicht sonderlich beliebt, da eine verlässliche UTF-8-Konvention überall verwendet wird. Die meisten Linux-Anwendungen gehen davon aus, dass Eingaben in UTF-8 codiert sind. Die meisten Linux-Anwendungen erkennen eine BOM ordnungsgemäß und verarbeiten sie richtig. Einige Anwendungen erkennen sie jedoch nicht, was in Texten, die mit diesen Anwendungen bearbeitet wurden, zu ungewollten Abweichungen führt.

**Deshalb gilt Folgendes**:

- Wenn Sie überwiegend mit Windows-Anwendungen und Windows-PowerShell arbeiten, eignet sich UTF-8 mit BOM oder UTF-16 für Sie.
- Wenn Sie plattformübergreifend arbeiten, eignet sich UTF-8 mit BOM für Sie.
- Wenn Sie überwiegend in Linux-Kontexten arbeiten, ist UTF-8 ohne BOM die richtige Wahl für Sie.
- Windows-1252 und Latin-1 sind im Wesentlichen Legacycodierungen, die Sie wenn möglich vermeiden sollten.
  Es kann jedoch sein, dass ältere Windows-Anwendungen noch von diesen abhängig sind.
- Außerdem sollten Sie beachten, dass die Skriptsignierung [codierungsabhängig](https://github.com/PowerShell/PowerShell/issues/3466) ist, d.h., dass durch die Änderung der Codierung eines Skripts das Skript erneut signiert werden muss.

## <a name="configuring-vs-code"></a>Konfigurieren von VS Code

Die Standardcodierung von VS Code ist UTF-8 ohne BOM.

Navigieren Sie zu den VS Code-Einstelllungen (<kbd>STRG</kbd>+<kbd>,</kbd>), und legen Sie die Einstellung `"files.encoding"` fest, um die [Codierung in VS Code][] festzulegen:

```json
"files.encoding": "utf8bom"
```

U.a. die folgenden Werte sind möglich:

- `utf8`: [UTF-8] ohne BOM
- `utf8bom`: [UTF-8] mit BOM
- `utf16le`: Little-Endian [UTF-16]
- `utf16be`: Big-Endian [UTF-16]
- `windows1252`: [Windows-1252]

Sie sollte dafür eine Dropdownliste in der GUI-Ansicht und Vorschläge in der JSON-Ansicht sehen.

Sie können auch den folgenden Code hinzufügen, um die Codierung wenn möglich automatisch zu erkennen:

```json
"files.autoGuessEncoding": true
```

Wenn Sie nicht möchten, dass diese Einstellungen für alle Dateitypen gelten, können Sie in VS Code auch sprachspezifische Konfigurationen vornehmen. Sie können sprachspezifische Einstellungen erstellen, indem Sie Einstellungen in ein `[<language-name>]` einfügen. Beispiel:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>Konfiguration von PowerShell

Die Standardcodierung von PowerShell variiert je nach Version:

- In PowerShell 6 und höher, ist die Standardcodierung auf allen Plattformen UTF-8 ohne BOM.
- In Windows PowerShell ist die Standardcodierung normalerweise Windows-1252, eine Erweiterung von [Latin-1][], die auch als ISO 8859-1 bezeichnet wird.

In PowerShell 5 und höher können Sie die Standardcodierung mit dem folgenden Code herausfinden:

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

Mit dem folgenden [Skript](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) können Sie bestimmen, welche Codierung Ihre PowerShell-Sitzung für ein Skript ohne BOM annimmt.

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

Sie können in den Profileinstellungen PowerShell so konfigurieren, dass es eine bestimmte Codierung allgemeiner verwendet.
Weitere Informationen finden Sie in folgenden Artikeln:

- Antwort von [@mklement0] zum [Verwenden der PowerShell-Codierung auf Stack Overflow](https://stackoverflow.com/a/40098904).
- Blogbeitrag von [@rkeithhill] zum [Behandeln von UTF-8-Eingaben ohne BOM in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).

Die Verwendung einer bestimmten Eingabecodierung kann in PowerShell nicht erzwungen werden. PowerShell 5.1 und früher verwenden standardmäßig die Windows-1252-Codierung, wenn es keine BOM gibt. Aus Gründen der Interoperabilität empfiehlt es sich, Skripts in einem Unicodeformat mit BOM zu speichern.

> [!IMPORTANT]
> Alle Tools, die mit PowerShell-Skripten interagieren, können von der gewählten Codierung betroffen sein oder Ihre Skripts in ein anderes Codierungsformat umcodieren.

### <a name="existing-scripts"></a>Vorhandene Skripts

Skripts, die sich bereits im Dateisystem befinden, müssen möglicherweise in die neue Codierung umcodiert werden. In der unteren Leiste in VS Code wird UTF-8 angezeigt. Klicken Sie darauf, um die Aktionsleiste zu öffnen, und wählen Sie **Mit Codierung speichern** aus. Jetzt können Sie für diese Datei eine neue Codierung festlegen. Im Artikel zur [Codierung in VS Code][] finden Sie alle Anweisungen.

Wenn Sie mehrere Dateien erneut codieren müssen, können Sie das folgende Skript verwenden:

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>PowerShell Integrated Scripting Environment (ISE)

Wenn Sie auch Skripts mit der PowerShell ISE verwenden, müssen Sie dort Ihre Codierungseinstellungen synchronisieren.

Die ISE sollte eine BOM beachten. Es ist jedoch auch möglich, die [Codierung mit der Reflexion festzulegen](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).
Beachten Sie, dass diese Einstellung beim erneuten Öffnen nicht beibehalten wird.

### <a name="source-control-software"></a>Quellcodeverwaltungssoftware

Einige Quellcodeverwaltungstools wie z.B. Git ignorieren Codierungen. Git verfolgt nur die Bytes. Bei anderen Tools, z.B. Azure DevOps oder Mercurial, ist dies nicht der Fall. Einige Git-basierte Tools sind vom Decodieren von Text abhängig.

Wenn dies so ist, achten Sie auf Folgendes:

- Achten Sie darauf, dass die Textcodierung Ihrer Quellcodeverwaltung mit der Konfiguration in VS Code übereinstimmt.
- Achten Sie darauf, dass Ihre Dateien in der Quellcodeverwaltung in der entsprechenden Codierung eingecheckt werden.
- Achten Sie auf Änderungen der Codierung, die Sie von der Quellcodeverwaltung erhalten. Darauf deutet primär ein Unterschied hin, der Änderungen angibt, obwohl keine offensichtlichen Änderungen zu erkennen sind (weil sich nur Bytes aber keine Zeichen geändert haben).

### <a name="collaborators-environments"></a>Einstellungen Mitwirkender

Achten Sie neben der Quellcodeverwaltung auch darauf, dass Personen, die an freigegebenen Dateien mitwirken, keine Einstellungen haben, die Ihre Codierung durch das erneute Codieren von PowerShell-Dateien überschreiben.

### <a name="other-programs"></a>Andere Programme

Alle anderen Programme, die ein PowerShell-Skript lesen oder schreiben, codieren dieses möglicherweise neu.

Beispiele:

- Die Zwischenablage zum Kopieren und Einfügen eines Skripts. Dies geschieht z.B. in den folgenden Szenarios:
  - Kopieren eines Skripts in eine VM
  - Kopieren eines Skripts aus einer E-Mail oder von einer Webseite
  - Kopieren eines Skripts in ein oder aus einem Microsoft Word- oder PowerPoint-Dokument
- Andere Text-Editors, z.B.:
  - Notepad
  - vim
  - Andere PowerShell-Skript-Editors
- Textbearbeitungshilfsprogramme, z.B.:
  - `Get-Content`/`Set-Content`/`Out-File`
  - PowerShell-Umleitungsoperatoren wie `>` und `>>`
  - `sed`/`awk`
- Dateiübertragungsprogramme, z.B.:
  - Ein Webbrowser beim Herunterladen von Skripts
  - Eine Dateifreigabe

Einige dieser Tools arbeiten mit Bytes und nicht mit Text und andere bieten Codierungskonfigurationen. Wenn Sie eine Codierung konfigurieren müssen, muss diese mit der Codierung Ihres Editors übereinstimmen, um Probleme zu vermeiden.

## <a name="other-resources-on-encoding-in-powershell"></a>Weitere Informationen zur Codierung in PowerShell

Es gibt einige weitere nützliche Beiträge zur Codierung und Konfiguration der Codierung in PowerShell, die Sie sich ansehen können:

- die Zusammenfassung von [@mklement0] zum [Verwenden der PowerShell-Codierung auf Stack Overflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- Frühere Probleme bezüglich der Codierung bei VS Code und PowerShell:
  - [#1308](https://github.com/PowerShell/VSCode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/VSCode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/VSCode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/VSCode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/VSCode-powershell/issues/1751)
- [Der Klassiker: Zusammenfassung von *Joel on Software* zu Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [Codierung in .NET Standard](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)

[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[Bytereihenfolge-Marke]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Sprachserverprotokoll]: https://microsoft.github.io/language-server-protocol/
[Codierung in VS Code]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
