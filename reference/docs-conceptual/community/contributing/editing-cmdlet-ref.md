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
# <a name="editing-reference-articles"></a>Bearbeiten von Referenzartikeln

Cmdlet-Referenzartikel weisen eine bestimmte Struktur auf. Diese Struktur wird von [PlatyPS][] definiert.
PlatyPS generiert die Cmdlet-Hilfe für PowerShell-Module in Markdown. Nach dem Bearbeiten der Markdowndateien wird PlatyPS verwendet, um die vom Cmdlet `Get-Help` verwendeten MAML-Hilfedateien zu erstellen.

PlatyPS hat ein hartcodiertes Schema für die Cmdlet-Referenz, das in den Code geschrieben wird. Im Dokument [platyPS.schema.md][] wird versucht, diese Struktur zu beschreiben. Verstöße gegen das Schema führen zu Buildfehlern, die behoben werden müssen, bevor wir Ihren Beitrag annehmen können.

## <a name="general-guidelines"></a>Allgemeine Richtlinien

- Entfernen Sie keine Headerstrukturen. PlatyPS erwartet eine bestimmte Struktur von Headern.
- Die Header **Input type** und **Output type** müssen einen Typ haben. Wenn das Cmdlet keine Eingabe annimmt oder keinen Wert zurückgibt, verwenden Sie den Wert `None`.
- Umgrenzte Codeblöcke sind nur im Abschnitt [Examples](#structuring-examples) zulässig.
- „span“-Elemente in Inlinecode können in beliebigen Absätzen verwendet werden.

## <a name="formatting-about_-files"></a>Formatieren von About_-Dateien

`About_*`-Dateien werden in Markdown geschrieben, jedoch als Nur-Text-Dateien weitergegeben. Wir verwenden [Pandoc][], um die Markdown-Dateien in Nur-Text-Dateien umzuwandeln. `About_*`-Dateien sind für optimale Kompatibilität mit allen Versionen von PowerShell und den Veröffentlichungstools formatiert.

Grundlegende Formatierungsleitlinien:

- Beschränken Sie Zeilen auf 80 Zeichen. Pandoc fügt bei einigen Markdown-Blöcken einen Einzug ein, sodass diese Blöcke angepasst werden müssen.
  - Codeblöcke sind auf 76 Zeichen beschränkt
  - Tabellen sind auf 76 Zeichen beschränkt
  - Blockquotes (und Alerts) sind auf 78 Zeichen beschränkt

- Verwenden der speziellen Pandoc-Metazeichen: `\`, `$` und `<`
  - Innerhalb eines Headers müssen diese Zeichen mit einem führenden `\`-Zeichen als Escapezeichen versehen oder mit Graviszeichen (`` ` ``) zwischen „span“-Elementen eingefügt werden
  - Innerhalb eines Absatzes müssen diese Zeichen im Code zwischen „span“-Elementen platziert werden. Beispiel:

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

- Tabellen müssen in 76 Zeichen passen.
  - Inhalt von Zellen manuell auf mehrere Zeilen umbrechen.
  - Öffnende und schließende `|`-Zeichen in jeder Zeile verwenden.
  - Das folgende Beispiel zeigt den ordnungsgemäßen Aufbau einer Tabelle mit Informationen, bei der mehrere Zeilen innerhalb einer Zelle umbrochen werden.

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
    > Die Beschränkung von 76 Spalten gilt nur für `About_*`-Themen. In konzeptionellen oder Cmdlet-Referenzartikeln können breite Spalten verwendet werden.

## <a name="structuring-examples"></a>Beispiele für die Strukturierung

Im PlatyPS-Schema ist der Header **EXAMPLES** ein H2-Header und jedes Beispiel ein H3-Header.

Innerhalb eines Beispiels erlaubt das Schema nicht das Trennen von Codeblöcken durch Absätze. Das unterstützte Schema ist wie folgt:

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

Nummerieren Sie jedes Beispiel, und fügen Sie einen Kurztitel hinzu.

Beispiel:

### <a name="example-1-get-cmdlets-functions-and-aliases"></a>Beispiel 1: Abrufen von Cmdlets, Funktionen und Aliasen

Dieser Befehl ruft die PowerShell-Cmdlets, Funktionen und Aliase ab, die auf dem Computer installiert sind.

```powershell
Get-Command
```

### <a name="example-2-get-commands-in-the-current-session"></a>Beispiel 2: Abrufen von Befehlen in der aktuellen Sitzung

```powershell
Get-Command -ListImported
```

## <a name="next-steps"></a>Nächste Schritte

[Checkliste für die Bearbeitung](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: /PowerShell/module/Microsoft.PowerShell.Core/About/about_Comparison_Operators
[Pandoc]: https://pandoc.org
