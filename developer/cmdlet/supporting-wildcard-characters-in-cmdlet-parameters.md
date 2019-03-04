---
title: Unterstützung von Platzhalterzeichen in der Cmdlet-Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 296490e4692e72f823be0b00aee90dc8c3dc9131
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862516"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Unterstützung für Platzhalter in Cmdlet-Parametern

Häufig müssen Sie ein Cmdlet zum Ausführen für eine Gruppe von Ressourcen nicht für eine einzelne Ressource zu entwerfen. Suchen alle Dateien in einem Datenspeicher, die den gleichen Namen oder die Erweiterung kann z. B. ein Cmdlet müssen. Sie müssen Unterstützung für Platzhalterzeichen angeben, beim Entwerfen eines Cmdlets, das für eine Gruppe von Ressourcen ausgeführt wird.

> [!NOTE]
> Verwenden von Platzhalterzeichen wird mitunter als *Platzhaltermuster*.

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>Windows PowerShell-Cmdlets, die Platzhalter verwenden

 Viele Windows PowerShell-Cmdlets unterstützen Platzhalterzeichen für die Parameterwerte. Verfügt beispielsweise fast alle Cmdlets, die über eine `Name` oder `Path` Parameter unterstützt Platzhalterzeichen für diese Parameter. (Zwar die meisten Cmdlets, die eine `Path` Parameter haben. auch eine `LiteralPath` Parameter, der Platzhalterzeichen nicht unterstützt.) Der folgende Befehl zeigt, wie ein Platzhalterzeichen verwendet wird, um alle Cmdlets in der aktuellen Sitzung zurückzugeben, deren Name das Get-Verb enthält.

 **PS > Get-Command Get -\***

## <a name="supported-wildcard-characters"></a>Unterstützte Platzhalterzeichen

Windows PowerShell unterstützt die folgenden Platzhalterzeichen handeln.

|Platzhalterzeichen|Beschreibung|Beispiel|Treffer|Stimmt nicht überein mit|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|Entspricht null oder mehr Zeichen, beginnend mit der angegebenen Position|a*|A, ag, Apple||
|?|Übereinstimmungen Anycharacter an der angegebenen position|? n|Ein im, auf|ausgeführt wurde|
|[ ]|Entspricht einen Bereich von Zeichen|[a-l]ook|Buch, Cook, suchen|dauerte|
|[ ]|Stimmt mit den angegebenen Zeichen|[bc]ook|Buch, cook|Suchen Sie|

Wenn Sie Cmdlets, die Platzhalterzeichen unterstützt entwerfen, können Sie für Kombinationen von Platzhalterzeichen. Beispielsweise der folgende Befehl verwendet den `Get-ChildItem` Cmdlet zum Abrufen von alle TXT-Dateien, die sich im Ordner c:\Techdocs und, beginnen mit den Buchstaben "a" bis "l."

**get-childitem c:\techdocs\\[a-l]\*.txt**

Der vorherige Befehl verwendet den Bereich Platzhalter **[a-l]** um anzugeben, dass der Dateiname mit den Zeichen "a" bis "l." beginnen soll Anschließend verwendet der Befehl die * Platzhalterzeichen als Platzhalter für alle Zeichen zwischen den ersten Buchstaben des Dateinamens und der Erweiterung TXT.

Im folgenden Beispiel wird ein Bereich Platzhaltermuster, die ohne des Buchstabens "d", aber mit umfasst alle anderen Buchstaben von "a" bis "f."

**Get-Childitem c:\techdocs\\[a-Cef]\*txt**

## <a name="handling-literal-characters-in-wildcard-patterns"></a>Behandeln von Literalzeichen in Platzhaltermuster

Wenn die Platzhaltermuster, das Sie angeben, Literalzeichen enthält, verwenden Sie ein rückwärts geneigtes Apostroph (') als Escapezeichen ein. Wenn Sie programmgesteuert Literalzeichen angeben, verwenden Sie ein einzelnes Hochkomma. Wenn Sie literale Zeichen an der Eingabeaufforderung angeben, verwenden Sie zwei Graviszeichen. Im folgenden Format enthält beispielsweise zwei eckige Klammern, die buchstäblich berücksichtigt werden müssen.

"John Smith \`[*"] "(programmgesteuert angegeben)

"John Smith \` \`[*\`"] "(an der Eingabeaufforderung angegeben)

Diesem Muster entsprechen "John Smith [Marketing]" oder "John Smith [Entwicklung]".

## <a name="cmdlet-output-and-wildcard-characters"></a>Platzhalterzeichen und Cmdlet-Ausgabe

Bei der cmdletparameter Platzhalterzeichen unterstützt, generiert ein Cmdlet-Vorgang in der Regel eine arrayausgabe. In einigen Fällen ist es nicht sinnvoll, unterstützt ein Array ausgegeben werden, da der Benutzer möglicherweise nur ein einziges Element zu einem Zeitpunkt verwendet. Z. B. die `Set-Location` Cmdlet unterstützt ein Array ausgeben, da der Benutzer mit nur einem einzigen Ort festlegt. In diesem Fall das Cmdlet immer noch unterstützt Platzhalterzeichen an zentraler Stelle Auflösung wird erzwungen.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[WildcardPattern-Klasse](/dotnet/api/system.management.automation.wildcardpattern)
