---
title: Kommentarbasierte Hilfe-Schlüsselwörter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab90ec96-77f5-42e3-9c7e-2f4156ec207f
caps.latest.revision: 6
ms.openlocfilehash: af8a151070d26ffe236800076115c964f625e572
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058078"
---
# <a name="comment-based-help-keywords"></a>Schlüsselwörter in der kommentarbasierten Hilfe

Dieses Thema enthält und beschreibt die Schlüsselwörter in kommentarbasierte Hilfe.

## <a name="keywords-in-comment-based-help"></a>Schlüsselwörter in befehlsbasierte Hilfe

Im folgenden werden die gültigen kommentarbasierte Hilfe-Schlüsselwörter. Sie werden in der Reihenfolge aufgeführt, in denen sie in der Regel in einem Hilfethema zusammen mit ihrem Verwendungszweck aufgeführt. Diese Schlüsselwörter können in beliebiger Reihenfolge in der kommentarbasierten Hilfe angezeigt werden, und sie sind nicht Groß-/Kleinschreibung beachtet.

Beachten Sie, dass die `.ExternalHelp` Schlüsselwort hat Vorrang vor allen anderen kommentarbasierte Hilfe-Schlüsselwörter. Wenn `.ExternalHelp` vorhanden ist, die [Microsoft.PowerShell.Commands.Get-Help](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) Cmdlet zeigt keine kommentarbasierte Hilfe, selbst wenn er eine Hilfedatei, die den Wert des Schlüsselworts entspricht nicht finden kann.

`.Synopsis` Eine kurze Beschreibung der Funktion oder des Skripts. Dieses Schlüsselwort kann nur einmal in jedem Thema verwendet werden.

`.Description` Eine ausführliche Beschreibung der Funktion oder des Skripts. Dieses Schlüsselwort kann nur einmal in jedem Thema verwendet werden.

`.Parameter` *\<Parameter-Name >* die Beschreibung eines Parameters. Sie können einschließen, eine `.Parameter` -Schlüsselwort für jeden Parameter in der Funktion oder einem Skript.

Die `.Parameter` Schlüsselwörter können angezeigt werden, in beliebiger Reihenfolge in den Kommentarblock, aber die Reihenfolge der Parameter in der `Param` -Anweisung oder Funktionsdeklaration, bestimmt die Reihenfolge, die in der die Parameter im Hilfethema angezeigt werden. Um die Reihenfolge der Parameter im Hilfethema zu ändern, ändern Sie die Reihenfolge der Parameter in der `Param` -Anweisung oder Funktionsdeklaration.

Sie können auch eine Beschreibung des Parameters angeben, indem ein Kommentar in der `Param` Anweisung unmittelbar vor der Parameter-Variablenname. Wenn Sie beide verwenden eine `Param` Anweisung Kommentar und eine `.Parameter` -Schlüsselwort, das die zugeordnete Beschreibung der `.Parameter` Schlüsselwort verwendet wird, und die `Param` Anweisung Kommentar wird ignoriert.

`.Example` Ein Beispielbefehl, der die Funktion bzw. das Skript, optional gefolgt von der Ausgabe des Beispiels und eine Beschreibung verwendet. Wiederholen Sie dieses Schlüsselwort für jedes Beispiel.

`.Inputs` Die Microsoft .NET Framework-Typen von Objekten, die an die Funktion oder einem Skript übergeben werden können. Sie können auch eine Beschreibung der Eingabeobjekte einschließen.

`.Outputs` Der .NET Framework-Typ, der die Objekte, die mit dem Cmdlet zurückgegeben werden soll. Sie können auch eine Beschreibung der zurückgegebenen Objekte einschließen.

`.Notes` Weitere Informationen zu der Funktion oder ein Skript.

`.Link` Der Name der verwandten Thema. Wiederholen Sie dieses Schlüsselwort zu jedem verwandten Thema. Dieser Inhalt wird im Abschnitt "Verwandte Links" des Hilfethemas angezeigt.

Die `.Link` Schlüsselwort Inhalt kann auch ein Uniform Resource Identifier (URI) auf eine Onlineversion des Hilfethemas gleichen enthalten. Öffnet die Onlineversion, bei der Verwendung der `Online` Parameter von Get-Help. Der URI muss mit "http" oder "Https" beginnen.

`.Component` Die Technologie oder Funktion, die die Funktion bzw. das Skript verwendet, oder mit dem es verknüpft ist. Dieser Inhalt wird angezeigt, wenn es sich bei den Get-Help-Befehl enthält den `Component` Parameter von Get-Help.

`.Role` Die Benutzerrolle für das Hilfethema. Dieser Inhalt wird angezeigt, wenn es sich bei den Get-Help-Befehl enthält den `Role` Parameter von Get-Help.

`.Functionality` Die beabsichtigte Verwendung der Funktion. Dieser Inhalt wird angezeigt, wenn es sich bei den Get-Help-Befehl enthält den `Functionality` Parameter von Get-Help.

`.ForwardHelpTargetName` `<Command-Name>` Leitet das Hilfethema für den angegebenen Befehl. Sie können die Benutzer zu allen Hilfethemen, einschließlich der Hilfethemen für eine Funktion, Skripts, Cmdlet oder Anbieter umleiten.

`.ForwardHelpCategory` `<Category>` Gibt den Hilfe-Kategorie des Elements im ForwardHelpTargetName an. Gültige Werte sind Alias, Cmdlet, HelpFile, -Funktion, Anbieter, allgemeine, häufig gestellte Fragen, Glossar, Skriptbefehl, ExternalScript, filtern oder alle. Verwenden Sie dieses Schlüsselwort, um Konflikte zu vermeiden, wenn Befehle mit dem gleichen Namen vorhanden sind.

`.RemoteHelpRunspace` `<PSSession-variable>` Gibt eine Sitzung, die das Hilfethema enthält. Geben Sie eine Variable, die eine PSSession enthält. Dieses Schlüsselwort wird verwendet, durch die `Export-PSSession` Cmdlet, um die Hilfethemen für die exportierten Befehle zu finden.

`.ExternalHelp` `<XML Help File>` Gibt den Pfad und/oder Namen einer XML-basierte Hilfedatei für das Skript oder eine Funktion.

Die `.ExternalHelp` -Schlüsselwort teilt dem [Microsoft.PowerShell.Commands.Get-Help](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) Cmdlet zum Abrufen von Hilfe für das Skript oder eine Funktion in eine XML-Datei. Die **. ExternalHelp** -Schlüsselwort ist erforderlich, wenn eine XML-basierte Hilfedatei für ein Skript oder eine Funktion verwenden. Ohne diese `Get-Help` eine Hilfedatei für die Funktion bzw. das Skript wird nicht gefunden.

Die `.ExternalHelp` Schlüsselwort hat Vorrang vor allen anderen kommentarbasierte Hilfe-Schlüsselwörter. Wenn `.ExternalHelp` vorhanden ist, die [Microsoft.PowerShell.Commands.Get-Help](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) Cmdlet zeigt keine kommentarbasierte Hilfe, selbst wenn er eine Hilfedatei, die den Wert des Schlüsselworts entspricht nicht finden kann.

Wenn die Funktion wird durch ein Skriptmodul, den Wert des exportiert `.ExternalHelp` sollte ein Dateinamen ohne Pfad sein. `Get-Help` Sucht nach der Datei in einem gebietsschemaspezifischen Unterverzeichnis des Modulverzeichnisses. Es gibt keine Anforderungen für den Dateinamen, aber eine bewährte Methode ist, verwenden Sie das folgende Namensformat für die Datei: `<ScriptModule>.psm1-help.xml`.

Wenn die Funktion keinem Modul zugeordnet ist, schließen Sie einen Pfad und Dateinamen ein, in den Wert des der **. ExternalHelp** Schlüsselwort. Wenn der angegebene Pfad der XML-Datei UI-kulturspezifischen Unterverzeichnissen enthält `Get-Help` durchsucht die Unterverzeichnisse rekursiv für eine XML-Datei durch den Namen des Skripts bzw. einer Funktion in Übereinstimmung mit der Sprache, die fallback-Standards für eingerichtet Windows, wird genau wie für alle XML-basierte Hilfethemen.

Weitere Informationen zu den Cmdlet-Hilfe XML-basierte Hilfedatei-Format, finden Sie unter [Schreiben von Windows PowerShell-Cmdlet-Hilfe](./writing-help-for-windows-powershell-cmdlets.md).