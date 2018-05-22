---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: e4588e8c69efb965cd33c273ad09a8bef8e9bf16
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a>Extrahieren und Analysieren von strukturierten Objekten aus einer Zeichenfolge
Auch das Cmdlet „ConvertFrom-String“ weist einige neue Funktionen auf:

-   Die „ExtentText“-Eigenschaft wird standardmäßig entfernt. Sie können sie mit dem „-IncludeExtent“-Parameter einschließen.

-   Viele Fehlerbehebungen beim lernenden Algorithmus basierend auf Feedback von MVPs und Community.

-   Neuer „-UpdateTemplate“-Parameter zum Speichern der Ergebnisse des lernenden Algorithmus in einem Kommentar in der Vorlagendatei. Dadurch wird der Lernprozess (die langsamste Phase) zu einem einmaligen Aufwand. Das Ausführen von „Convert-String“ mit einer Vorlage, die den codierten lernenden Algorithmus enthält, erfolgt nun fast unmittelbar.


<a name="extract-and-parse-structured-objects-out-of-string-content"></a>Extrahieren und Analysieren von strukturierten Objekten aus einer Zeichenfolge
----------------------------------------------------------

In Zusammenarbeit mit [Microsoft Research](http://research.microsoft.com/) wurde das neue Cmdlet **ConvertFrom-String** hinzugefügt.

Dieses Cmdlet unterstützt zwei Modi: getrennte Analyse und von einem automatisch generierten Beispiel gesteuerte Analyse.

Bei der getrennten Analyse wird die Eingabe standardmäßig bei Leerzeichen getrennt, wobei den resultierenden Gruppen Eigenschaftsnamen zugewiesen werden. Sie können das Trennzeichen anpassen:

> 1 \[C:\\temp\] &gt;&gt; „Hello World“ | ConvertFrom-String | Format-Table -Auto

P1    P2
--    --

Das Cmdlet unterstützt auch die von einem automatisch generierten Beispiel gesteuerte Analyse basierend auf den Forschungsarbeiten zu [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) von [Microsoft Research](http://research.microsoft.com).

Nehmen wir zum Einstieg ein textbasiertes Adressbuch:

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

    Thomas Hardy

    Seattle, WA

    Christina Berglund

    Redmond, WA

    Hanna Moos

    Puyallup, WA

Kopieren Sie einige Beispiele in eine Datei, die Sie als Vorlage verwenden werden:

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA



Setzen Sie Daten, die Sie extrahieren möchten, in geschweifte Klammern, und geben Sie ihnen einen Namen. Da die **Name**-Eigenschaft und ihre zugehörigen anderen Eigenschaften mehrfach vorkommen können, müssen Sie ein Sternchen (\*) verwenden, um anzugeben, dass dadurch mehrere Datensätze generiert werden (statt eine Reihe von Eigenschaften in einen Datensatz zu extrahieren):

    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}

Ausgehend von diesen Beispielen kann **ConvertFrom-String** nun eine objektbasierte Ausgabe automatisch aus Eingabedateien mit ähnlicher Struktur extrahieren.

> 2 \[C:\\temp\]
>
> &gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto
>
> ExtentText                     Name               City     State
> ----------                     ----               ----     -----
> Ana Trujillo...                Ana Trujillo       Redmond  WA Antonio Moreno...              Antonio Moreno     Renton   WA Thomas Hardy...                Thomas Hardy       Seattle  WA Christina Berglund...          Christina Berglund Redmond  WA Hanna Moos...                  Hanna Moos         Puyallup WA

Um extrahierten Text weiter zu bearbeiten, erfasst die **ExtentText**-Eigenschaft den unformatierten Text, anhand dessen der Datensatz extrahiert wurde. Wenn Sie Feedback zu diesem Feature geben oder Inhalte teilen möchten, bei denen beim Schreiben von Beispielen Probleme auftreten, senden Sie eine E-Mail an <psdmfb@microsoft.com>.
