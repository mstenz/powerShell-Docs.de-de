---
title: Schlüsselwörter in der kommentarbasierten Hilfe
ms.date: 06/09/2020
ms.openlocfilehash: fb737c19d7b7f4d003af3ba36bb396bac52d94e7
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893151"
---
# <a name="comment-based-help-keywords"></a>Schlüsselwörter in der kommentarbasierten Hilfe

In diesem Thema werden die Schlüsselwörter in der Kommentar basierten Hilfe aufgelistet und beschrieben.

## <a name="keywords-in-comment-based-help"></a>Schlüsselwörter in der Kommentar basierten Hilfe

Im folgenden finden Sie gültige Kommentar basierte Hilfe Schlüsselwörter. Sie werden in der Reihenfolge aufgelistet, in der Sie in der Regel in einem Hilfethema zusammen mit der vorgesehenen Verwendung angezeigt werden. Diese Schlüsselwörter können in beliebiger Reihenfolge in der Kommentar basierten Hilfe angezeigt werden, und es wird nicht zwischen Groß-und Kleinschreibung unterschieden.

Beachten Sie, dass das- `.EXTERNALHELP` Schlüsselwort Vorrang vor allen anderen Kommentar basierten Hilfe Schlüsselwörtern hat.
Wenn `.EXTERNALHELP` vorhanden ist, zeigt das [Microsoft. PowerShell. Commands. gethelpcommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) -Cmdlet keine Kommentar basierte Hilfe an, auch wenn keine Hilfedatei gefunden werden kann, die mit dem Wert des-Schlüssel Worts übereinstimmt.

## <a name="synopsis"></a>. Zusammenfassung

Eine kurze Beschreibung der Funktion oder des Skripts. Dieses Schlüsselwort kann nur einmal in jedem Thema verwendet werden.

## <a name="description"></a>. Beschreibung

Eine ausführliche Beschreibung der Funktion oder des Skripts. Dieses Schlüsselwort kann nur einmal in jedem Thema verwendet werden.

## <a name="parameter-parameter-name"></a>. Parame\<Parameter-Name>

Die Beschreibung eines Parameters. Sie können `.PARAMETER` für jeden Parameter in der Funktion oder im Skript ein Schlüsselwort einschließen.

Die `.PARAMETER` Schlüsselwörter können in beliebiger Reihenfolge im Kommentar Block angezeigt werden, aber die Reihenfolge, in der die Parameter in der `Param` Anweisung oder Funktionsdeklaration angezeigt werden, bestimmt die Reihenfolge, in der die Parameter im Hilfethema angezeigt werden. Um die Reihenfolge der Parameter im Hilfethema zu ändern, ändern Sie die Reihenfolge der Parameter in der- `Param` Anweisung oder der-Funktionsdeklaration.

Sie können auch eine Parameter Beschreibung angeben, indem Sie einen Kommentar `Param` direkt vor dem Variablennamen des Parameters in der Anweisung platzieren. Wenn Sie sowohl einen `Param` Anweisungs Kommentar als auch ein `.PARAMETER` Schlüsselwort verwenden, wird die dem Schlüsselwort zugeordnete Beschreibung `.PARAMETER` verwendet, und der `Param` Anweisungs Kommentar wird ignoriert.

## <a name="example"></a>. Beispiel

Ein Beispiel Befehl, der die Funktion oder das Skript verwendet, optional gefolgt von der Beispielausgabe und einer Beschreibung. Wiederholen Sie dieses Schlüsselwort für jedes Beispiel.

## <a name="inputs"></a>. Ungs

Die Microsoft .NET Framework-Typen von Objekten, die an die Funktion oder das Skript weitergeleitet werden können. Sie können auch eine Beschreibung der Eingabe Objekte einschließen.

## <a name="outputs"></a>. Ausgaben

Der .NET Framework Typ der Objekte, die vom Cmdlet zurückgegeben werden. Sie können auch eine Beschreibung der zurückgegebenen Objekte einschließen.

## <a name="notes"></a>. Anmerkungen

Zusätzliche Informationen über die Funktion oder das Skript.

## <a name="link"></a>. Verknüpfen

Der Name eines verwandten Themas. Wiederholen Sie dieses Schlüsselwort für jedes verwandte Thema. Dieser Inhalt wird im Abschnitt Verwandte Links des Hilfe Themas angezeigt.

Das `.LINK` Schlüsselwort Content kann auch eine Uniform Resource Identifier (URI) zu einer Online Version desselben Hilfe Themas enthalten. Die Online Version wird geöffnet, wenn Sie den- `Online` Parameter von verwenden `Get-Help` . Der URI muss mit "http" oder "https" beginnen.

## <a name="component"></a>. Zulieferern

Der Name der Technologie oder des Features, die bzw. das von der Funktion oder dem Skript verwendet wird bzw. mit dem Sie verknüpft ist.
Der **Component** -Parameter von `Get-Help` verwendet diesen Wert, um die von zurückgegebenen Suchergebnisse zu filtern `Get-Help` .

## <a name="role"></a>. Spielen

Der Name der Benutzerrolle für das Hilfethema. Der **Role** -Parameter von `Get-Help` verwendet diesen Wert, um die von zurückgegebenen Suchergebnisse zu filtern `Get-Help` .

## <a name="functionality"></a>. Alitäts

Die Schlüsselwörter, die die beabsichtigte Verwendung der Funktion beschreiben. Der- **Funktions** Parameter von `Get-Help` verwendet diesen Wert, um die von zurückgegebenen Suchergebnisse zu filtern `Get-Help` .

## <a name="forwardhelptargetname-command-name"></a>. Forwardhelptargetname\<Command-Name>

Leitet das Hilfethema für den angegebenen Befehl um. Sie können Benutzer zu jedem beliebigen Hilfethema umleiten, einschließlich der Hilfe Themen für eine Funktion, ein Skript, ein Cmdlet oder einen Anbieter.

## <a name="forwardhelpcategory-category"></a>. Forwardhelpcategory\<Category>

Gibt die Hilfe Kategorie des Elements in an `.FORWARDHELPTARGETNAME` . Verwenden Sie dieses Schlüsselwort, um Konflikte zu vermeiden, wenn Befehle mit demselben Namen vorhanden sind.

Gültige Werte sind:

- Alias
- Cmdlet
- HelpFile
- Funktion
- Anbieter
- Allgemein
- Häufig gestellte Fragen
- Glossar
- ScriptCommand
- Externalscript
- Filter
- All

## <a name="remotehelprunspace-pssession-variable"></a>. Remotehelprunspace\<PSSession-variable>

Gibt eine Sitzung an, die das Hilfethema enthält. Geben Sie eine Variable ein, die eine PSSession enthält. Dieses Schlüsselwort wird vom `Export-PSSession` Cmdlet verwendet, um die Hilfe Themen für die exportierten Befehle zu suchen.

## <a name="externalhelp-xml-help-file"></a>. Externalhelp "\<XML Help File>

Gibt den Pfad und/oder den Namen einer XML-basierten Hilfedatei für das Skript oder die Funktion an.

Das- `.EXTERNALHELP` Schlüsselwort weist das [Microsoft. PowerShell. Commands. gethelpcommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) -Cmdlet an, Hilfe für das Skript oder die Funktion in einer XML-basierten Datei zu erhalten. Das `.EXTERNALHELP` Schlüsselwort ist erforderlich, wenn eine XML-basierte Hilfedatei für ein Skript oder eine Funktion verwendet wird. Ohne diese findet `Get-Help` keine Hilfedatei für die Funktion oder das Skript.

Das- `.EXTERNALHELP` Schlüsselwort hat Vorrang vor allen anderen Kommentar basierten Hilfe Schlüsselwörtern. Wenn `.EXTERNALHELP` vorhanden ist, zeigt das [Microsoft. PowerShell. Commands. gethelpcommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) -Cmdlet keine Kommentar basierte Hilfe an, auch wenn keine Hilfedatei gefunden werden kann, die mit dem Wert des-Schlüssel Worts übereinstimmt.

Wenn die Funktion von einem Skript Modul exportiert wird, sollte der Wert von `.EXTERNALHELP` ein Dateiname ohne Pfad sein. `Get-Help`sucht die Datei in einem Gebiets Schema spezifischen Unterverzeichnis des Modul Verzeichnisses. Der Dateiname hat keine Anforderungen, aber eine bewährte Vorgehensweise ist die Verwendung des folgenden Dateinamen Formats: `<ScriptModule>.psm1-help.xml` .

Wenn die Funktion keinem Modul zugeordnet ist, fügen Sie einen Pfad und einen Dateinamen in den Wert des `.EXTERNALHELP` Schlüssel Worts ein. Wenn der angegebene Pfad zur XML-Datei Benutzeroberflächen kulturspezifische Unterverzeichnisse enthält, `Get-Help` durchsucht die Unterverzeichnisse rekursiv nach einer XML-Datei mit dem Namen des Skripts oder der Funktion in Übereinstimmung mit den für Windows eingerichteten sprach Fall Back Standards, ebenso wie bei allen XML-basierten Hilfe Themen.

Weitere Informationen zum XML-basierten Hilfedatei Format in der Cmdlet-Hilfe finden Sie unter [Schreiben der Windows PowerShell-Cmdlet-Hilfe](./writing-help-for-windows-powershell-cmdlets.md).
