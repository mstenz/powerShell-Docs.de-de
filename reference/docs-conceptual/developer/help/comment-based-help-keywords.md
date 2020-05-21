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
ms.openlocfilehash: 3c5736be7066a749744482cb79edad2f53705f07
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564103"
---
# <a name="comment-based-help-keywords"></a>Schlüsselwörter in der kommentarbasierten Hilfe

In diesem Thema werden die Schlüsselwörter in der Kommentar basierten Hilfe aufgelistet und beschrieben.

## <a name="keywords-in-comment-based-help"></a>Schlüsselwörter in der Kommentar basierten Hilfe

Im folgenden finden Sie gültige Kommentar basierte Hilfe Schlüsselwörter. Sie werden in der Reihenfolge aufgelistet, in der Sie in der Regel in einem Hilfethema zusammen mit der vorgesehenen Verwendung angezeigt werden. Diese Schlüsselwörter können in beliebiger Reihenfolge in der Kommentar basierten Hilfe angezeigt werden, und es wird nicht zwischen Groß-und Kleinschreibung unterschieden.

Beachten Sie, dass das- `.ExternalHelp` Schlüsselwort Vorrang vor allen anderen Kommentar basierten Hilfe Schlüsselwörtern hat. Wenn `.ExternalHelp` vorhanden ist, zeigt das [Microsoft. PowerShell. Commands. gethelpcommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) -Cmdlet keine Kommentar basierte Hilfe an, auch wenn keine Hilfedatei gefunden werden kann, die mit dem Wert des-Schlüssel Worts übereinstimmt.

`.Synopsis`Eine kurze Beschreibung der Funktion oder des Skripts. Dieses Schlüsselwort kann nur einmal in jedem Thema verwendet werden.

`.Description`Eine ausführliche Beschreibung der Funktion oder des Skripts. Dieses Schlüsselwort kann nur einmal in jedem Thema verwendet werden.

`.Parameter`* \< Parameter Name>* die Beschreibung eines Parameters. Sie können `.Parameter` für jeden Parameter in der Funktion oder im Skript ein Schlüsselwort einschließen.

Die `.Parameter` Schlüsselwörter können in beliebiger Reihenfolge im Kommentar Block angezeigt werden, aber die Reihenfolge, in der die Parameter in der `Param` Anweisung oder Funktionsdeklaration angezeigt werden, bestimmt die Reihenfolge, in der die Parameter im Hilfethema angezeigt werden. Um die Reihenfolge der Parameter im Hilfethema zu ändern, ändern Sie die Reihenfolge der Parameter in der- `Param` Anweisung oder der-Funktionsdeklaration.

Sie können auch eine Parameter Beschreibung angeben, indem Sie einen Kommentar `Param` direkt vor dem Variablennamen des Parameters in der Anweisung platzieren. Wenn Sie sowohl einen `Param` Anweisungs Kommentar als auch ein `.Parameter` Schlüsselwort verwenden, wird die dem Schlüsselwort zugeordnete Beschreibung `.Parameter` verwendet, und der `Param` Anweisungs Kommentar wird ignoriert.

`.Example`Ein Beispiel Befehl, der die Funktion oder das Skript verwendet, optional gefolgt von der Beispielausgabe und einer Beschreibung. Wiederholen Sie dieses Schlüsselwort für jedes Beispiel.

`.Inputs`Die Microsoft .NET Framework-Typen von Objekten, die an die Funktion oder das Skript weitergeleitet werden können. Sie können auch eine Beschreibung der Eingabe Objekte einschließen.

`.Outputs`Der .NET Framework Typ der Objekte, die vom Cmdlet zurückgegeben werden. Sie können auch eine Beschreibung der zurückgegebenen Objekte einschließen.

`.Notes`Zusätzliche Informationen über die Funktion oder das Skript.

`.Link`Der Name eines verwandten Themas. Wiederholen Sie dieses Schlüsselwort für jedes verwandte Thema. Dieser Inhalt wird im Abschnitt Verwandte Links des Hilfe Themas angezeigt.

Das `.Link` Schlüsselwort Content kann auch eine Uniform Resource Identifier (URI) zu einer Online Version desselben Hilfe Themas enthalten. Die Online Version wird geöffnet, wenn Sie den `Online` -Parameter von "Get-Help" verwenden. Der URI muss mit "http" oder "https" beginnen.

`.Component`Die Technologie oder das Feature, das von der Funktion oder dem Skript verwendet wird bzw. mit der es verknüpft ist. Dieser Inhalt wird angezeigt, wenn der Get-Help-Befehl den- `Component` Parameter von Get-Help enthält.

`.Role`Die Benutzerrolle für das Hilfethema. Dieser Inhalt wird angezeigt, wenn der Get-Help-Befehl den- `Role` Parameter von Get-Help enthält.

`.Functionality`Die beabsichtigte Verwendung der Funktion. Dieser Inhalt wird angezeigt, wenn der Get-Help-Befehl den- `Functionality` Parameter von Get-Help enthält.

`.ForwardHelpTargetName``<Command-Name>`Leitet das Hilfethema für den angegebenen Befehl um. Sie können Benutzer zu jedem beliebigen Hilfethema umleiten, einschließlich der Hilfe Themen für eine Funktion, ein Skript, ein Cmdlet oder einen Anbieter.

`.ForwardHelpCategory``<Category>`Gibt die Hilfe Kategorie des Elements in forwardhelptargetname an. Gültige Werte sind "Alias", "Cmdlet", "HelpFile", "Function", "Provider", "allgemeine Fragen", "Glossar", "ScriptCommand", "externalscript" Verwenden Sie dieses Schlüsselwort, um Konflikte zu vermeiden, wenn Befehle mit demselben Namen vorhanden sind.

`.RemoteHelpRunspace``<PSSession-variable>`Gibt eine Sitzung an, die das Hilfethema enthält. Geben Sie eine Variable ein, die eine PSSession enthält. Dieses Schlüsselwort wird vom `Export-PSSession` Cmdlet verwendet, um die Hilfe Themen für die exportierten Befehle zu suchen.

`.ExternalHelp``<XML Help File>`Gibt den Pfad und/oder den Namen einer XML-basierten Hilfedatei für das Skript oder die Funktion an.

Das- `.ExternalHelp` Schlüsselwort weist das [Microsoft. PowerShell. Commands. gethelpcommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) -Cmdlet an, Hilfe für das Skript oder die Funktion in einer XML-basierten Datei zu erhalten. Die **. Das externalhelp** -Schlüsselwort ist erforderlich, wenn eine XML-basierte Hilfedatei für ein Skript oder eine Funktion verwendet wird. Ohne diese findet `Get-Help` keine Hilfedatei für die Funktion oder das Skript.

Das- `.ExternalHelp` Schlüsselwort hat Vorrang vor allen anderen Kommentar basierten Hilfe Schlüsselwörtern. Wenn `.ExternalHelp` vorhanden ist, zeigt das [Microsoft. PowerShell. Commands. gethelpcommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) -Cmdlet keine Kommentar basierte Hilfe an, auch wenn keine Hilfedatei gefunden werden kann, die mit dem Wert des-Schlüssel Worts übereinstimmt.

Wenn die Funktion von einem Skript Modul exportiert wird, sollte der Wert von `.ExternalHelp` ein Dateiname ohne Pfad sein. `Get-Help`sucht die Datei in einem Gebiets Schema spezifischen Unterverzeichnis des Modul Verzeichnisses. Der Dateiname ist nicht erforderlich, aber es wird empfohlen, das folgende Format zu verwenden: `<ScriptModule>.psm1-help.xml` .

Wenn die Funktion keinem Modul zugeordnet ist, fügen Sie einen Pfad und einen Dateinamen in den Wert von ein **. Externalhelp** -Schlüsselwort. Wenn der angegebene Pfad zur XML-Datei Benutzeroberflächen kulturspezifische Unterverzeichnisse enthält, `Get-Help` durchsucht die Unterverzeichnisse rekursiv nach einer XML-Datei mit dem Namen des Skripts oder der Funktion in Übereinstimmung mit den für Windows eingerichteten sprach Fall Back Standards, ebenso wie bei allen XML-basierten Hilfe Themen.

Weitere Informationen zum XML-basierten Hilfedatei Format in der Cmdlet-Hilfe finden Sie unter [Schreiben der Windows PowerShell-Cmdlet-Hilfe](./writing-help-for-windows-powershell-cmdlets.md).
