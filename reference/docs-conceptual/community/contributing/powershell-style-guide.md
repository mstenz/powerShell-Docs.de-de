---
title: Styleguide für die PowerShell-Dokumentation
description: Dieser Artikel enthält die Stilregeln für das Schreiben von PowerShell-Dokumentation.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 90dc93d608440ce7388614b552c0cd873a385cd9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81624787"
---
# <a name="powershell-docs-style-guide"></a>Styleguide für die PowerShell-Dokumentation

Dieser Artikel enthält die spezifischen Stilanweisungen für Inhalte der PowerShell-Dokumentation. Dies geschieht ausgehend von den in der [Übersicht](overview.md#get-started-writing-docs) beschriebenen Informationen.

## <a name="product-terminology"></a>Produktterminologie

Es gibt mehrere Varianten von PowerShell.

- **PowerShell**: Dies ist die Standardvariante. Wir sehen im weiteren Verlauf PowerShell 7 und höhere Versionen als das eine echte PowerShell an.
- **PowerShell Core-** : PowerShell basierend auf .NET Core. Die Verwendung des Begriffs **Core** sollte auf Fälle beschränkt sein, in denen die Unterscheidung von Windows PowerShell erforderlich ist.
- **Windows PowerShell**:- PowerShell basierend auf .NET Framework. Windows PowerShell wird nur für Windows ausgeliefert und erfordert das gesamte Framework.

  Im Allgemeinen können Verweise auf „Windows PowerShell“ in der Dokumentation zu „PowerShell“ geändert werden.
  „Windows PowerShell“ sollte verwendet werden, wenn Windows PowerShell-spezifisches Verhalten beschrieben wird.

Verwandte Produkte

- **Visual Studio Code (VS Code)** : Dies ist der kostenlose Open Source-Editor von Microsoft. Bei der ersten Erwähnung sollte der vollständige Name verwendet werden. Anschließend können Sie **VS Code** verwenden. Verwenden Sie nicht „VSCode“.
- **PowerShell-Erweiterung für Visual Studio Code**: Mit dieser Erweiterung wird VS Code in die bevorzugte IDE für PowerShell umgewandelt. Bei der ersten Erwähnung sollte der vollständige Name verwendet werden. Anschließend können Sie **PowerShell-Erweiterung** verwenden.
- **Azure PowerShell**: Dies ist die Sammlung von PowerShell-Modulen, mit denen Azure-Dienste verwaltet werden.
- **Azure PowerShell**: Dies ist die Sammlung von PowerShell-Modulen, mit denen die Hybrid Cloud-Lösung von Microsoft verwaltet wird.

## <a name="markdown-specifics"></a>Besonderheiten von Markdown

Das Microsoft Open Publishing System (OPS), mit dem unsere Dokumentation erstellt wird, verwendet [markdig][], um die Markdown-Dokumente zu verarbeiten. Markdig analysiert die Dokumente auf der Grundlage der Regeln der aktuellen [CommonMark][]-Spezifikation.

Die neue CommonMark-Spezifikation ist weitaus strenger im Hinblick auf den Aufbau einiger Markdown-Elemente. Beachten Sie die Detailinformationen in diesem Dokument genau.

### <a name="blank-lines-spaces-and-tabs"></a>Leerzeilen, Leerzeichen und Tabstoppzeichen

Leerzeilen signalisieren darüber hinaus in Markdown das Ende eines Blocks. Zwischen Markdown-Blöcken unterschiedlicher Typen (z. B. zwischen einem Absatz und einer Liste oder einem Header) sollte eine einzelne Leerzeile stehen.

Entfernen Sie doppelte Leerzeilen. Mehrere Leerzeilen werden in HTML als eine einzelne Leerzeile dargestellt, das Einfügen oder Vorhandensein mehrerer Leerzeilen dient also keinem Zweck. Mehrere Leerzeilen innerhalb eines Codeblocks haben zur Folge, dass der Code nicht funktioniert.

Entfernen Sie zusätzliche Leerzeichen am Zeilenende.

> [!NOTE]
> Abstände sind in Markdown wichtig. Verwenden Sie immer Leerzeichen anstelle harter Tabstoppzeichen. Nachgestellte Leerzeichen können sich auf das Rendern von Markdown auswirken.

### <a name="titles-and-headings"></a>Titel und Überschriften

Verwenden Sie nur [ATX-Überschriften][atx] (#-Formatvorlage, im Gegensatz zu Überschriften der `=`- oder `-`-Formatvorlagen).

- Verwenden Sie normale Groß-/Kleinschreibung – nur Eigennamen und der erste Buchstabe eines Titels oder einer Überschrift sollten groß geschrieben werden
- Zwischen dem `#` und dem ersten Buchstaben des Titels muss ein einfaches Leerzeichen stehen
- Überschriften sollten von einer einzelnen Leerzeile umgeben sein
- Nur eine Überschrift der Ebene H1 pro Dokument
- Überschriftebenen sollten um 1 erhöht werden. Überspringen Sie keine Ebenen
- Verwenden Sie keine fette oder sonstige Auszeichnung in Überschriften

### <a name="limit-line-length-to-100-characters"></a>Begrenzen Sie die Zeilenlänge auf 100 Zeichen

Dies gilt für konzeptionelle Artikel und die Cmdlet-Referenz. Das Beschränken der Zeilenlänge verbessert die Lesbarkeit von git-Diffs und git-Verlauf. Es erleichtert außerdem anderen Autoren das Einbringen ihres Beitrags.

Verwenden Sie die Erweiterung [Reflow Markdown][reflow] in Visual Studio Code, um Absätze komfortabel umzubrechen, sodass sie in die erforderliche Zeilenlänge passen.

Klassische Hilfethemen (About_topics) sind auf 80 Zeichen beschränkt. Einzelheiten finden Sie unter [Bearbeiten von Referenzartikeln](./editing-cmdlet-ref.md#formatting-about_-files).

### <a name="lists"></a>Listen

Wenn Ihre Liste mehrere Sätze oder Absätze enthält, erwägen Sie eine Unterüberschrift anstelle einer Liste.

Eine Liste sollte von einer einzelnen Leerzeile umgeben sein.

#### <a name="unordered-lists"></a>Unsortierte Listen

Beenden Sie Listenelemente nicht mit einem Punkt, es sei denn, sie enthalten mehrere Sätze. Verwenden Sie das Bindestrich Zeichen (`-`) für Listenelement Aufzählungen. Dadurch wird die Verwechselung mit fettem oder kursivem Markup vermieden, für das das Sternchen [`*`] verwendet wird. Um einen Absatz oder andere Elemente unter einem Aufzählungselement einzuschließen, fügen Sie einen Zeilenumbruch ein, und richten Sie den Einzug am ersten Zeichen nach dem Aufzählungszeichen aus.

Beispiel:

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

Dies ist eine Liste, die Unterelemente unter einem Aufzählungselement enthält.

- Erstes Aufzählungselement

  Satz zur Erläuterung des ersten Aufzählungszeichens.

  - Untergeordnetes Aufzählungszeichen

    Satz zur Erläuterung des Unteraufzählungszeichens.

- Zweites Aufzählungszeichen
- Drittes Aufzählungszeichen

#### <a name="ordered-lists"></a>Sortierte Listen

Um einen Absatz oder andere Elemente unter einer Aufzählung einzuschließen, richten Sie den Einzug am ersten Zeichen nach der Elementnummer aus. Alle Elemente in einer Liste sollten die Nummer `1.` verwenden, statt jedes einzelne Element zu erhöhen. Beim Rendering erhöht Markdown den Wert automatisch. Dadurch wird die Neuanordnung von Elementen vereinfacht und der Einzug von untergeordnetem Inhalt standardisiert.

Beispiel:

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

Der resultierende Markdown wird wie folgt gerendert:

1. Fügen Sie für das erste Element ein einzelnes Leerzeichen nach der 1 ein. Lange Sätze sollten in die nächste Zeile umbrochen werden und müssen am ersten Zeichen hinter dem nummerierten Listenmarker ausgerichtet werden.

   Um ein zweites Element (wie dieses hier) aufzuführen, fügen Sie nach dem ersten Element einen Zeilenumbruch ein, und richten Sie die Einzüge aus. Der Einzug des zweiten Elements muss am ersten Zeichen hinter dem nummerierten Listenmarker ausgerichtet werden. Für einstellige Elemente wie dieses ziehen Sie in Spalte 4 ein. Für zweistellige Elemente, beispielsweise die Elementnummer 10, ziehen Sie in Spalte 5 ein.

1. Das nächste nummerierte Element beginnt hier.

### <a name="images"></a>Bilder

Die Syntax zum Einschließen eines Bilds lautet wie folgt:

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

Dabei stellt `alt text` eine kurze Beschreibung des Bilds und `<folder path>` einen relativen Pfad zum Bild dar. Alternativtext ist für Bildschirmsprachausgaben für Personen mit eingeschränktem Sehvermögen erforderlich. Er ist außerdem nützlich, falls das Bild aufgrund eines Bugs auf der Website nicht gerendert werden kann.

Bilder sollten in einem `media/<article-name>`-Ordner innerhalb des Ordners gespeichert werden, der den Artikel enthält.
Bilder sollten nicht von mehreren Artikeln gemeinsam genutzt werden. Erstellen Sie einen Ordner, der mit dem Dateinamen Ihres Artikels übereinstimmt, im `media`-Ordner. Kopieren Sie die Bilder für den Artikel in diesen neuen Ordner. Wenn ein Bild von mehreren Artikeln verwendet wird, muss jeder Bildordner eine Kopie der betreffenden Bilddatei aufweisen. Diese Vorgehensweise verhindert, dass eine Änderung am Bild in einem Artikel sich auf andere Artikel auswirkt.

Die folgenden Bilddateitypen werden unterstützt: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`

### <a name="markdown-extensions-supported-by-open-publishing"></a>Von Open Publishing unterstützte Markdown-Erweiterungen

Das [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) (Erstellungspaket für Microsoft-Dokumentation) enthält Tools, die für unser Veröffentlichungssystem spezifische Features unterstützen. Alerts (Warnungen) sind eine Markdown-Erweiterung zum Erstellen von Blockquotes, die auf docs.microsoft.com mit Farben und Symbolen gerendert werden, die die Bedeutung des Inhalts hervorheben. Die folgenden Warnungstypen werden unterstützt:

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

Diese Warnungen sehen auf docs.microsoft.com wie folgt aus:

Hinweis

> [!NOTE]
> Informationen, die der Benutzer selbst beim Durchblättern bemerken sollte.

Tipp

> [!TIP]
> Optionale Informationen, die einem Benutzer helfen sollen, erfolgreicher zu arbeiten.

Wichtig

> [!IMPORTANT]
> Wichtige Informationen, die für den Erfolg des Benutzers unabdingbar sind.

Achtung

> [!CAUTION]
> Negative potenzielle Folgen einer Aktion.

Warnung

> [!WARNING]
> Bestimmte gefährliche Folgen einer Aktion.

### <a name="hyperlinks"></a>Links

- Für Links muss die Markdown-Syntax `[friendlyname](url-or-path)` verwendet werden
- Links sollten nach Möglichkeit als HTTPS angegeben werden.
- Links müssen über einen Anzeigenamen verfügen, normalerweise den Titel des verknüpften Themas
- Alle Elemente im Abschnitt „Verwandte Links“ im unteren Bereich sollten mit einem Link versehen sein
- Verwenden Sie innerhalb der Klammern eines Links keine Graviszeichen und fette oder sonstige Auszeichnung.
- Reine URLs können verwendet werden, wenn Sie über einen bestimmten URI sprechen. Der URI muss in Graviszeichen eingeschlossen werden. Beispiel:

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content"></a>Verknüpfen mit anderen Inhalten

Das Veröffentlichungssystem unterstützt zwei Arten von Links:

Bei einem **URL-Link** kann es sich um einen URL-Pfad handeln, der relativ zum Stamm von docs.microsoft.com ist. Oder eine absolute URL, die die vollständige URL-Syntax enthält. Beispiel: `https:/github.com/MicrosoftDocs/PowerShell-Docs`

- Verwenden Sie URL-Links für die Verknüpfung mit Inhalten außerhalb der PowerShell-Dokumentation oder zwischen der Cmdlet-Referenz und konzeptionellen Artikeln innerhalb der PowerShell-Dokumentation. Die einfachste Möglichkeit zum Erstellen eines relativen Links besteht darin, die URL aus Ihrem Browser zu kopieren und dann `https://docs.microsoft.com/en-us` aus dem Wert zu entfernen, den Sie in Markdown einfügen.
- Schließen Sie keine Gebietsschemas in URLs in Microsoft-Eigenschaften ein (entfernen Sie beispielsweise `/en-us` aus dem URL).
- Entfernen Sie alle nicht benötigten Abfrageparameter aus dem URL, sofern Sie nicht eine Verknüpfung mit einer bestimmten Artikelversion herstellen müssen. Beispiele:
  - `?view=powershell-5.1`: dieser Parameter wird verwendet, um eine Verknüpfung mit einer bestimmten PowerShell-Version herzustellen
  - `?redirectedfrom=MSDN`: dieser Parameter wird zum URL hinzugefügt, wenn Sie von einem älteren Artikel zur neuen Version umgeleitet werden
- Alle URLs zu externen Websites sollten HTTPS verwenden, es sei denn, dies ist für die Zielwebsite ungültig.

Eine **Dateiverknüpfung** wird verwendet, um von einem Referenzartikel auf einen anderen oder von einem konzeptionellen Artikel auf einen anderen zu verweisen. Wenn Sie auf einen Referenzartikel für eine bestimmte PowerShell-Version verweisen müssen, müssen Sie einen URL-Link verwenden.

- Dateiverknüpfungen enthalten einen relativen Dateipfad (Beispiel: `../folder/file.md`)
- Alle Dateipfade enthalten Schrägstriche (`/`).

Deep Linking ist sowohl für URL-Links als auch für Dateiverknüpfungen zulässig. Fügen Sie den Anker am Ende des Zielpfads hinzu.
Beispiel:

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

Weitere Informationen finden Sie unter [Verwenden von Links in der Dokumentation](https://docs.microsoft.com/contribute/how-to-write-links).

## <a name="formatting-command-syntax-elements"></a>Formatieren von Befehlssyntaxelementen

- Verwenden Sie immer den vollständigen Namen für Cmdlets und Parameter. Vermeiden Sie die Verwendung von Aliasen, es sei denn, Sie möchten den Alias beispielhaft hervorheben.

- Eigenschaften, Parameter, Objekte, Typnamen, Klassennamen und Klassenmethoden sollten **fett** formatiert werden.
  - Eigenschafts- und Parameterwerte sollten in Graviszeichen (`` ` ``) eingeschlossen werden.
  - Verwenden Sie Graviszeichen, wenn Sie auf Typen verweisen, die in Klammern stehen. Beispiel: `[System.Io.FileInfo]`

- Schlüsselwörter, Cmdlet-Namen, Funktionen, Variablen, native EXE-Dateinamen, Dateipfade und Inlinesyntaxbeispiele sollten in Graviszeichen (`` ` ``) eingeschlossen werden.

  Beispiel:

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - Wenn Sie anhand des Namens auf einen Parameter verweisen, sollte der Name **fett** formatiert sein. Wenn Sie die Verwendung eines Parameters mit dem Bindestrichpräfix veranschaulichen, sollte der Parameter in Graviszeichen eingeschlossen sein. Beispiel:

    ```markdown
    The parameter's name is **Name**, but it is typed as `-Name` when used on the command
    line as a parameter.
    ```

  - Bei der beispielhaften Verwendung eines externen Befehls sollte das Beispiel in Graviszeichen eingeschlossen werden.
    Fügen Sie die Dateierweiterung immer in den nativen Befehl ein. Beispiel:

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    Durch das Einfügen der Dateierweiterung wird sichergestellt, dass der richtige Befehl gemäß der PowerShell-Rangfolge ausgeführt wird.

- Beim Schreiben eines konzeptionellen Artikels (im Gegensatz zu Referenzinhalt) sollte die erste Instanz eines Cmdlet-Namens per Link zur Dokumentation des Cmdlets verweisen. Verwenden Sie innerhalb der Klammern eines Links keine Graviszeichen und fette oder sonstige Auszeichnung.

  Beispiel:

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  Weitere Informationen finden Sie im Abschnitt [Links](#hyperlinks) in diesem Artikel.

## <a name="markdown-for-code-samples"></a>Markdown für Codebeispiele

Markdown unterstützt zwei verschiedene Codeformatvorlagen:

- **„span“-Elemente (inline)** : durch ein einzelnes Graviszeichen (`` ` ``) gekennzeichnet. Wird innerhalb eines Absatzes anstelle eines eigenständigen Blocks verwendet.
- **Codeblöcke**: ein mehrzeiliger Block, der in dreifache Graviszeichen-Zeichenfolgen (`` ``` ``) eingeschlossen ist. Codeblöcke können außerdem über eine Sprachbezeichnung im Anschluss an die Graviszeichen verfügen. Die Sprachbezeichnung ermöglicht Syntaxhervorhebung für die Inhalte des Codeblocks.

Alle Codeblöcke sollten in einem abgesetzten Codebereich (Code Fence) enthalten sein. Verwenden Sie bei Codeblöcken niemals einen Einzug. Markdown lässt dieses Muster zu, dies kann jedoch zu Problemen führen und sollte vermieden werden.

Bei einem Codeblock handelt es sich um eine oder mehrere Codezeilen, die in dreifache Graviszeichen (`` ``` ``) eingeschlossen sind.
Die Codebereichsmarkierungen müssen in einer eigenen Zeile vor und nach dem Codebeispiel stehen. Der Marker am Beginn des Codeblocks darf eine optionale Sprachbezeichnung aufweisen. Das Open Publishing System (OPS) von Microsoft verwendet die Sprachbezeichnung zur Unterstützung der Syntaxhervorhebungsfunktion.

Eine vollständige Liste der unterstützten Sprachtags finden Sie unter [Umgrenzte Codeblöcke](/contribute/code-in-docs#fenced-code-blocks) im zentralen Leitfaden für Mitwirkende.

OPS fügt außerdem eine Schaltfläche **Kopieren** hinzu, die die Inhalte des Codeblocks in die Zwischenablage kopiert. Dies ermöglicht es Ihnen, den Code schnell in ein Skript einzufügen, um das Codebeispiel zu testen. Allerdings sind nicht alle Beispiele in unserer Dokumentation für die Ausführung bestimmt. Einige Codeblöcke sind einfache Abbildungen eines PowerShell-Konzepts.

In unserer Dokumentation werden drei Arten von Codeblöcken verwendet:

1. Syntaxblöcke
1. Anschauliche Beispiele
1. Ausführbare Beispiele

### <a name="syntax-code-blocks"></a>Syntaxcodeblöcke

Mithilfe von Syntaxcodeblöcken wird die syntaktische Struktur eines Befehls beschrieben. Verwenden Sie keine Sprachtags für die Umgrenzung von Code. Dieses Beispiel veranschaulicht alle möglichen Parameter des `Get-Command`-Cmdlets.

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax]
  [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
  [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

Dieses Beispiel beschreibt die `for`-Anweisungen allgemein:

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a>Anschauliche Beispiele

Anschauliche Beispiele werden verwendet, um ein PowerShell-Konzept zu erläutern. Sie sind nicht dazu bestimmt, zur Ausführung in die Zwischenablage kopiert zu werden. Diese werden am häufigsten für einfache Beispiele verwendet, die sich leicht eingeben lassen und die leicht verständlich sind. Der Codeblock kann die PowerShell-Eingabeaufforderung und die Beispielausgabe umfassen.

Nachfolgend ist ein einfaches Beispiel gezeigt, das die PowerShell-Vergleichsoperatoren veranschaulicht. In diesem Fall wollen wir nicht, dass der Leser das Beispiel kopiert und ausführt.

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

### <a name="executable-examples"></a>Ausführbare Beispiele

Komplexe Beispiele oder Beispiele, die zum Kopieren und Ausführen erstellt werden, sollten das folgende Markup als Blockformatvorlage verwenden:

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

Die von PowerShell-Befehlen angezeigte Ausgabe sollte in einen **Output**-Codeblock eingeschlossen werden, um Syntaxhervorhebung zu vermeiden. Beispiel:

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

Die **Output**-Codebezeichnung ist keine offizielle „Sprache“, die vom Syntaxhervorhebungs-System unterstützt wird.
Diese Bezeichnung ist jedoch nützlich, da OPS dem Rahmen des Codefelds auf der Website die Bezeichnung „Output“ hinzufügt. Das „Output“-Codefeld hat keine Syntaxhervorhebung.

## <a name="coding-style-rules"></a>Regeln für Codeformatvorlagen

### <a name="avoid-line-continuation-in-code-samples"></a>Vermeiden Sie Zeilenfortsetzung in Codebeispielen

Vermeiden Sie die Verwendung von Zeilenfortsetzungszeichen (`` ` ``) in PowerShell-Codebeispielen. Sie sind schlecht zu sehen und können zu Problemen führen, wenn am Zeilenende zusätzliche Leerzeichen vorhanden sind.

- Verwenden Sie PowerShell-Aufteilung, um die Zeilenlänge für Cmdlets zu reduzieren, die viele Parameter aufweisen.
- Nutzen Sie die natürlichen Gelegenheiten für Zeilenumbrüche in PowerShell, etwa nach Pipesymbolen (`|`), öffnenden geschweiften Klammern, Klammern und eckigen Klammern.

### <a name="avoid-using-powershell-prompts-in-examples"></a>Vermeiden Sie die Verwendung von PowerShell-Eingabeaufforderungen in Beispielen

Von der Verwendung der Eingabeaufforderungs-Zeichenfolge wird abgeraten. Sie sollte auf Fälle beschränkt werden, deren Zweck die Veranschaulichung der Befehlszeilensyntax ist. Für die meisten dieser Beispiele sollte die Eingabeaufforderungs-Zeichenfolge `PS>` lauten. Diese Eingabeaufforderung ist unabhängig von betriebssystemspezifischen Indikatoren.

Eingabeaufforderungen sind für Beispiele erforderlich, die Befehle veranschaulichen, mit denen die Eingabeaufforderung geändert wird, oder wenn der angezeigte Pfad für das dargestellte Szenario relevant ist. Das folgende Beispiel zeigt, wie sich die Eingabeaufforderung ändert, wenn der Registrierungsanbieter verwendet wird.

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

### <a name="do-not-use-aliases-in-examples"></a>Verwenden Sie keine Aliase in Beispielen

Sie sollten für alle Cmdlets und Parameter immer den vollständigen Namen verwenden, es sei denn, Sie behandeln speziell den Alias. Namen von Cmdlets und Parametern müssen die richtige Pascal-Schreibweise verwenden.

### <a name="using-parameters-in-examples"></a>Verwenden von Parametern in Beispielen

Vermeiden Sie die Verwendung von Positionsparametern. Im Allgemeinen sollten Sie immer den Parameternamen in ein Beispiel aufnehmen, selbst wenn es sich um einen Positionsparameter handelt. Dies verringert die Gefahr von Missverständnissen in Ihren Beispielen.

## <a name="next-steps"></a>Nächste Schritte

[Bearbeiten der Cmdlet-Referenz](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
