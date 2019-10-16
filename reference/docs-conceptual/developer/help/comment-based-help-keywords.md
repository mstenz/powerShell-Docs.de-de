---
title: Kommentar basierte Hilfe Schlüsselwörter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab90ec96-77f5-42e3-9c7e-2f4156ec207f
caps.latest.revision: 6
ms.openlocfilehash: 534a6c9a43326c8a01b2181c7a799286fa4d3997
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361359"
---
# <a name="comment-based-help-keywords"></a>Schlüsselwörter in der kommentarbasierten Hilfe

In diesem Thema werden die Schlüsselwörter in der Kommentar basierten Hilfe aufgelistet und beschrieben.

## <a name="keywords-in-comment-based-help"></a>Schlüsselwörter in der Kommentar basierten Hilfe

Im folgenden finden Sie gültige Kommentar basierte Hilfe Schlüsselwörter. Sie werden in der Reihenfolge aufgelistet, in der Sie in der Regel in einem Hilfethema zusammen mit der vorgesehenen Verwendung angezeigt werden. Diese Schlüsselwörter können in beliebiger Reihenfolge in der Kommentar basierten Hilfe angezeigt werden, und es wird nicht zwischen Groß-und Kleinschreibung unterschieden.

Beachten Sie, dass das `.ExternalHelp`-Schlüsselwort Vorrang vor allen anderen Kommentar basierten Hilfe Schlüsselwörtern hat. Wenn `.ExternalHelp` vorhanden ist, zeigt das [Microsoft. PowerShell. Commands. gethelpcommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) -Cmdlet keine Kommentar basierte Hilfe an, auch wenn keine Hilfedatei gefunden werden kann, die mit dem Wert des-Schlüssel Worts übereinstimmt.

`.Synopsis` eine kurze Beschreibung der Funktion oder des Skripts. Dieses Schlüsselwort kann nur einmal in jedem Thema verwendet werden.

`.Description` eine ausführliche Beschreibung der Funktion oder des Skripts. Dieses Schlüsselwort kann nur einmal in jedem Thema verwendet werden.

`.Parameter` *\<Parameter-Name >* die Beschreibung eines Parameters. Sie können ein `.Parameter`-Schlüsselwort für jeden Parameter in der Funktion oder im Skript einschließen.

Die `.Parameter`-Schlüsselwörter können in beliebiger Reihenfolge im Kommentar Block vorkommen, aber die Reihenfolge, in der die Parameter in der `Param`-Anweisung oder-Funktionsdeklaration angezeigt werden, bestimmt die Reihenfolge, in der die Parameter in Hilfe Themen angezeigt werden. Um die Reihenfolge der Parameter im Hilfethema zu ändern, ändern Sie die Reihenfolge der Parameter in der `Param`-Anweisung oder der Funktionsdeklaration.

Sie können auch eine Parameter Beschreibung angeben, indem Sie einen Kommentar in der `Param`-Anweisung direkt vor dem Variablennamen des Parameters platzieren. Wenn Sie sowohl einen `Param`-Anweisungs Kommentar als auch ein `.Parameter`-Schlüsselwort verwenden, wird die Beschreibung verwendet, die dem `.Parameter`-Schlüsselwort zugeordnet ist, und der `Param`-Anweisungs Kommentar wird ignoriert.

`.Example` ein Beispiel Befehl, der die Funktion oder das Skript verwendet, optional gefolgt von der Beispielausgabe und einer Beschreibung. Wiederholen Sie dieses Schlüsselwort für jedes Beispiel.

`.Inputs` die Microsoft .NET Framework-Typen von Objekten, die an die Funktion oder das Skript weitergeleitet werden können. Sie können auch eine Beschreibung der Eingabe Objekte einschließen.

`.Outputs` der .NET Framework Typ der Objekte, die vom Cmdlet zurückgegeben werden. Sie können auch eine Beschreibung der zurückgegebenen Objekte einschließen.

`.Notes` zusätzliche Informationen über die Funktion oder das Skript.

`.Link` den Namen eines verwandten Themas. Wiederholen Sie dieses Schlüsselwort für jedes verwandte Thema. Dieser Inhalt wird im Abschnitt Verwandte Links des Hilfe Themas angezeigt.

Der Inhalt des Schlüssel Worts "`.Link`" kann auch eine Uniform Resource Identifier (URI) für eine Online Version desselben Hilfe Themas enthalten. Die Online Version wird geöffnet, wenn Sie den `Online`-Parameter von Get-Help verwenden. Der URI muss mit "http" oder "https" beginnen.

`.Component` die Technologie oder das Feature, die bzw. das von der Funktion oder dem Skript verwendet wird bzw. mit der es verknüpft ist. Dieser Inhalt wird angezeigt, wenn der Befehl "Get-Help" den `Component`-Parameter von "Get-Help" enthält.

`.Role` die Benutzerrolle für das Hilfethema. Dieser Inhalt wird angezeigt, wenn der Befehl "Get-Help" den `Role`-Parameter von "Get-Help" enthält.

`.Functionality` die beabsichtigte Verwendung der Funktion. Dieser Inhalt wird angezeigt, wenn der Befehl "Get-Help" den `Functionality`-Parameter von "Get-Help" enthält.

`.ForwardHelpTargetName` `<Command-Name>` leitet zum Hilfethema für den angegebenen Befehl um. Sie können Benutzer zu jedem beliebigen Hilfethema umleiten, einschließlich der Hilfe Themen für eine Funktion, ein Skript, ein Cmdlet oder einen Anbieter.

`.ForwardHelpCategory` `<Category>` gibt die Hilfe Kategorie des Elements in forwardhelptargetname an. Gültige Werte sind "Alias", "Cmdlet", "HelpFile", "Function", "Provider", "allgemeine Fragen", "Glossar", "ScriptCommand", "externalscript" Verwenden Sie dieses Schlüsselwort, um Konflikte zu vermeiden, wenn Befehle mit demselben Namen vorhanden sind.

`.RemoteHelpRunspace` `<PSSession-variable>` gibt eine Sitzung an, die das Hilfethema enthält. Geben Sie eine Variable ein, die eine PSSession enthält. Dieses Schlüsselwort wird vom `Export-PSSession`-Cmdlet verwendet, um die Hilfe Themen für die exportierten Befehle zu suchen.

`.ExternalHelp` `<XML Help File>` gibt den Pfad und/oder den Namen einer XML-basierten Hilfedatei für das Skript oder die Funktion an.

Das Schlüsselwort "`.ExternalHelp`" weist das [Microsoft. PowerShell. Commands. gethelpcommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) -Cmdlet an, Hilfe für das Skript oder die Funktion in einer XML-basierten Datei zu erhalten. Die **. Das externalhelp** -Schlüsselwort ist erforderlich, wenn eine XML-basierte Hilfedatei für ein Skript oder eine Funktion verwendet wird. Ohne ihn findet `Get-Help` keine Hilfedatei für die Funktion oder das Skript.

Das Schlüsselwort "`.ExternalHelp`" hat Vorrang vor allen anderen Kommentar basierten Hilfe Schlüsselwörtern. Wenn `.ExternalHelp` vorhanden ist, zeigt das [Microsoft. PowerShell. Commands. gethelpcommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) -Cmdlet keine Kommentar basierte Hilfe an, auch wenn keine Hilfedatei gefunden werden kann, die mit dem Wert des-Schlüssel Worts übereinstimmt.

Wenn die Funktion von einem Skript Modul exportiert wird, sollte der Wert von `.ExternalHelp` ein Dateiname ohne Pfad sein. `Get-Help` sucht nach der Datei in einem Gebiets Schema spezifischen Unterverzeichnis des Modul Verzeichnisses. Der Dateiname ist nicht erforderlich, es wird jedoch empfohlen, das folgende Dateinamen Format zu verwenden: `<ScriptModule>.psm1-help.xml`.

Wenn die Funktion keinem Modul zugeordnet ist, fügen Sie einen Pfad und einen Dateinamen in den Wert von ein **. Externalhelp** -Schlüsselwort. Wenn der angegebene Pfad zur XML-Datei Benutzeroberflächen kulturspezifische Unterverzeichnisse enthält, durchsucht `Get-Help` die Unterverzeichnisse rekursiv nach einer XML-Datei mit dem Namen des Skripts oder der Funktion in Übereinstimmung mit den für Windows eingerichteten sprach Fall Back Standards. genau wie bei allen XML-basierten Hilfe Themen.

Weitere Informationen zum XML-basierten Hilfedatei Format in der Cmdlet-Hilfe finden Sie unter [Schreiben der Windows PowerShell-Cmdlet-Hilfe](./writing-help-for-windows-powershell-cmdlets.md).