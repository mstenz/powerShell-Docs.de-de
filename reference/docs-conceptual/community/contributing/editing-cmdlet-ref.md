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
# <a name="editing-reference-articles"></a>Bearbeiten von Referenzartikeln

Cmdlet-Referenzartikel haben eine bestimmte Struktur, die von [PlatyPS][] definiert wird.
PlatyPS generiert die Cmdlet-Hilfe für PowerShell-Module in Markdown. Nach dem Bearbeiten der Markdowndateien wird PlatyPS verwendet, um die vom Cmdlet `Get-Help` verwendeten MAML-Hilfedateien zu erstellen.

PlatyPS hat ein hartcodiertes Schema für die Cmdlet-Referenz, das in den Code geschrieben wird. Im Dokument [platyPS.schema.md][] wird versucht, diese Struktur zu beschreiben. Verstöße gegen das Schema führen zu Buildfehlern, die behoben werden müssen, bevor wir Ihren Beitrag annehmen können.

## <a name="general-guidelines"></a>Allgemeine Richtlinien

- Entfernen Sie keine Headerstrukturen. PlatyPS erwartet eine bestimmte Struktur von Headern.
- Die Header **Input type** und **Output type** müssen einen Typ haben. Wenn das Cmdlet keine Eingabe annimmt oder keinen Wert zurückgibt, verwenden Sie den Wert `None`.
- Umgrenzte Codeblöcke sind nur im Abschnitt [Examples](#structuring-examples) zulässig.
- „span“-Elemente in Inlinecode können in beliebigen Absätzen verwendet werden.

## <a name="formatting-about_-files"></a>Formatieren von About_-Dateien

`About_*`-Dateien werden jetzt von [Pandoc][] statt von PlatyPS verarbeitet. `About_*`-Dateien sind für optimale Kompatibilität mit allen Versionen von PowerShell und den Veröffentlichungstools formatiert.

Grundlegende Formatierungsleitlinien:

- Zeilen auf 80 Zeichen begrenzen.
- Codeblöcke und -tabellen sind auf 76 Zeichen begrenzt, da Pandoc diese bei der Konvertierung in normalen Text um vier Leerzeichen einrückt.
- Tabellen müssen in 76 Zeichen passen.
  - Inhalt von Zellen manuell auf mehrere Zeilen umbrechen.
  - Öffnende und schließende `|`-Zeichen in jeder Zeile verwenden.
  - Ein funktionierendes Beispiel finden Sie unter [about_Comparison_Operators][about-example].
- Pandoc-Sonderzeichen `\`,`$` und `<` verwenden.
  - Innerhalb eines Headers müssen diese Zeichen mit einem führenden `\`-Zeichen als Escapezeichen versehen oder in Hochkommas (`` ` ``) gesetzt werden.
  - Innerhalb eines Absatzes müssen diese Zeichen im Code zwischen „span“-Elementen platziert werden. Beispiel:

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

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
