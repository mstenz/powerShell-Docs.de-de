---
title: Unterstützung für Platzhalter in Cmdlet-Parametern
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 19644c5bc186a5554d6b134a67fc7c4d7aa7b64c
ms.sourcegitcommit: a02ccbeaa17c0e513d6c4a21b877c88ac7725458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104450"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Unterstützung für Platzhalter in Cmdlet-Parametern

Häufig müssen Sie ein Cmdlet so entwerfen, dass es für eine Gruppe von Ressourcen und nicht für eine einzelne Ressource ausgeführt wird. Beispielsweise muss ein Cmdlet möglicherweise alle Dateien in einem Datenspeicher mit dem gleichen Namen oder der gleichen Erweiterung suchen. Beim Entwerfen eines Cmdlets, das für eine Gruppe von Ressourcen ausgeführt werden soll, müssen Sie Unterstützung für Platzhalter Zeichen bereitstellen.

> [!NOTE]
> Die Verwendung von Platzhalter Zeichen wird manchmalals "glob" bezeichnet.

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>Windows PowerShell-Cmdlets, die Platzhalter verwenden

 Viele Windows PowerShell-Cmdlets unterstützen Platzhalter Zeichen für Ihre Parameterwerte. Beispielsweise unterstützt fast jedes Cmdlet mit dem `Name` - `Path` Parameter oder dem-Parameter Platzhalter Zeichen für diese Parameter. (Obwohl die meisten Cmdlets, die `Path` über einen Parameter verfügen `LiteralPath` , auch über einen Parameter verfügen, der keine Platzhalter Zeichen unterstützt.) Der folgende Befehl zeigt, wie ein Platzhalter Zeichen verwendet wird, um alle Cmdlets in der aktuellen Sitzung zurückzugeben, deren Name das Get-Verb enthält.

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a>Unterstützte Platzhalter Zeichen

Windows PowerShell unterstützt die folgenden Platzhalter Zeichen.

| Wild |                             Beschreibung                             |  Beispiel   |     Treffer      | Stimmt nicht überein mit |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | Entspricht 0 (null) oder mehr Zeichen, beginnend an der angegebenen Position. | `a*`       | A, AG, Apple     |                |
| ?        | Entspricht einem beliebigen Zeichen an der angegebenen Position.                     | `?n`       | Ein, in, ein       | an            |
| [ ]      | Entspricht einem Zeichenbereich.                                       | `[a-l]ook` | Buch, Kochen, ansehen | Nook, hat     |
| [ ]      | Entspricht den angegebenen Zeichen                                    | `[bn]ook`  | Buch, Nook       | Kochen, sehen     |

Wenn Sie Cmdlets entwerfen, die Platzhalter Zeichen unterstützen, lassen Sie Kombinationen von Platzhalter Zeichen zu. Der folgende Befehl verwendet z. b. `Get-ChildItem` das Cmdlet zum Abrufen aller txt-Dateien, die sich im Ordner c:\techdocs befinden und mit den Buchstaben "a" bis "l" beginnen.

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

Der vorherige Befehl verwendet den Bereichs `[a-l]` Platzhalter, um anzugeben, dass der Dateiname mit den Zeichen "a" bis "l" beginnen soll, und verwendet das `*` Platzhalter Zeichen als Platzhalter für alle Zeichen zwischen dem ersten Buchstaben des Datei namens und. die Erweiterung " **. txt** ".

Im folgenden Beispiel wird ein Bereichs Halter Muster verwendet, das den Buchstaben "d" ausschließt, aber alle anderen Buchstaben von "a" bis "f" umfasst.

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a>Verarbeiten von Literalzeichen in Platzhalter Mustern

Wenn das von Ihnen angegebene Platzhalter Muster Literalzeichen enthält, die nicht als Platzhalter Zeichen interpretiert werden sollen, verwenden Sie`` ` ``das Graviszeichen-Zeichen () als Escapezeichen. Wenn Sie die Literalzeichen int der PowerShell-API angeben, verwenden Sie einen einzigen Backtick. Wenn Sie an der PowerShell-Eingabeaufforderung Literalzeichen angeben, verwenden Sie zwei Backticks.

Das folgende Muster enthält z. b. zwei eckige Klammern, die wörtlich genommen werden müssen.

Wenn Sie in der PowerShell-API verwendet wird, verwenden Sie:

- "John Smith \`[* ']"

Wenn Sie von der PowerShell-Eingabeaufforderung verwendet wird:

- "John Smith \` \`[*\`']"

Dieses Muster entspricht "John Smith [Marketing]" oder "John Smith [Development]". Beispiel:

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a>Cmdlet-Ausgabe und Platzhalter Zeichen

Wenn Cmdlet-Parameter Platzhalter Zeichen unterstützen, generiert der Vorgang normalerweise eine Array Ausgabe.
Gelegentlich ist es nicht sinnvoll, eine Array Ausgabe zu unterstützen, da der Benutzer möglicherweise nur ein einzelnes Element verwendet. Beispielsweise unterstützt `Set-Location` das Cmdlet die Array Ausgabe nicht, da der Benutzer nur einen einzigen Speicherort festlegt. In diesem Fall unterstützt das Cmdlet weiterhin Platzhalter Zeichen, aber es erzwingt die Auflösung an einem einzelnen Speicherort.

## <a name="see-also"></a>Siehe auch

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Wildcardpattern-Klasse](/dotnet/api/system.management.automation.wildcardpattern)
