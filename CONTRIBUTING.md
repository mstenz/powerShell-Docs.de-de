# <a name="contributing-to-powershell-documentation"></a>Mitwirkung an der PowerShell-Dokumentation

Vielen Dank für Ihr Interesse an der PowerShell-Dokumentation! Nachfolgend finden Sie Einzelheiten dazu, wie Sie Beiträge zu unserer technischen Dokumentation beisteuern können.

>Allgemeine Informationen zu den ersten Schritten mit Git und GitHub finden Sie in der [Hilfe zu GitHub](https://help.github.com/). 

## <a name="sign-a-cla"></a>Unterzeichnen einer CLA

Bevor Sie an den PowerShell-Repositorys mitwirken können, müssen Sie [eine Microsoft Contribution Licensing Agreement (CLA) unterzeichnen](https://cla.microsoft.com/). Wenn Sie bereits in der Vergangenheit Beiträge zu PowerShell-Repositorys beigesteuert haben, herzlichen Glückwunsch! Sie haben diesen Schritt bereits durchgeführt.

## <a name="providing-feedback-on-powershell-documentation"></a>Senden von Feedback zu PowerShell-Dokumentation

Sie können auf Fehler hinweisen, Änderungen vorschlagen oder neue Themen anfordern, indem Sie auf der [Seite mit Problemen im Zusammenhang mit dem Repository der PowerShell-Dokumente](https://github.com/PowerShell/PowerShell-Docs/issues) ein [Problem erstellen](https://help.github.com/articles/creating-an-issue/).

Probleme werden regelmäßig von Mitgliedern des PowerShell-Dokumentationsteams überprüft, gesichtet, zugewiesen und entsprechend behandelt.

## <a name="writing-powershell-documentation"></a>Schreiben von PowerShell-Dokumentation

Eine der einfachsten Möglichkeiten, an der PowerShell mitzuwirken, besteht darin, beim Verfassen und Bearbeiten der Dokumentation zu helfen. Unsere gesamte auf GitHub gehostete Dokumentation wird mit [GitHub Flavored Markdown](https://help.github.com/articles/github-flavored-markdown/) geschrieben.

## <a name="making-minor-edits-to-existing-topics"></a>Durchführen kleinerer Änderungen an vorhandenen Themen

Um [eine vorhandene Datei zu bearbeiten](https://help.github.com/articles/editing-files-in-another-user-s-repository/), navigieren Sie einfach zur entsprechenden Datei, und klicken Sie auf die Schaltfläche „Bearbeiten“. GitHub erstellt automatisch eine eigene Verzweigung unseres Repositorys für Sie, in der Sie die Änderungen vornehmen können. Sobald Sie fertig sind, speichern Sie Ihre Änderungen, und senden Sie eine [Pull-Anforderung](https://help.github.com/articles/creating-a-pull-request/) an den *Staging*-Branch des Repositorys der [PowerShell-Dokumente](https://github.com/PowerShell/PowerShell-Docs). Nachdem Sie die Pull-Anforderung erstellt haben, werden Ihre Änderungen von jemandem aus dem PowerShell-Dokumentationsteam überprüft und ggf. in den *Staging*-Branch übernommen.

## <a name="making-major-edits-to-existing-topics"></a>Durchführen größerer Änderungen an vorhandenen Themen

Wenn Sie wesentliche Änderungen an einem vorhandenen Artikel vornehmen, Bildern hinzufügen oder ändern oder einen neuen Artikel beisteuern möchten, müssen Sie die eigene GitHub-Verzweigung manuell erstellen und auf den lokalen Computer klonen. Eine Verzweigung ist ein GitHub-basiertes Replikat des Hauptrepositorys unter Ihrem GitHub-Konto, das Ihnen eine Arbeitskopie bereitstellt, das Sie isoliert verwenden können. Aus Ihrer Verzweigung werden dann die Pull-Anforderungen erstellt. Entsprechend ist ein Klon ein lokales Replikat des Repositorys, das in diesem Fall ein Klon Ihrer Verzweigung ist. Der Klon ermöglicht Ihnen, Git-Repositorys offline zu bearbeiten und dazu leistungsfähigere systemeigene Softwaretools zu verwenden.

Der Workflow zum Ausführen größerer Änderungen an vorhandener Dokumentation sieht wie folgt aus:

1. [Erstellen Sie eine Verzweigung](https://help.github.com/articles/fork-a-repo/) des Repository der [PowerShell-Dokumente](https://github.com/PowerShell/PowerShell-Docs).
2. [Erstellen Sie einen Klon Ihrer Verzweigung](https://help.github.com/articles/cloning-a-repository/) auf Ihrem lokalen Computer.
3. Erstellen Sie einen neuen lokalen Branch in Ihrem geklonten Repository.
4. Ändern Sie die Dateien, die Sie aktualisieren möchten, in einem Markdown-Editor. 
   Nachstehend finden Sie häufig verwendete Markdown-Editoren.
5. [Übertragen Sie Ihren lokalen Branch per Push](https://help.github.com/articles/pushing-to-a-remote/) an Ihre Verzweigung.
6. [Erstellen Sie eine Pull-Anforderung](https://help.github.com/articles/creating-a-pull-request/) an den *Staging*-Branch des Repositorys der [PowerShell-Dokumente](https://github.com/PowerShell/PowerShell-Docs) .

## <a name="creating-new-topics"></a>Erstellen neuer Themen

Wenn Sie neue Dokumentation beisteuern möchten, durchsuchen Sie zuerst die [Probleme, die als „in Bearbeitung“ markiert sind](https://github.com/PowerShell/PowerShell-Docs/labels/in%20progress), um sicherzustellen, dass die entsprechenden Themen nicht bereits in Arbeit sind.
Wenn bisher niemand an dem geplanten Thema zu arbeiten scheint:

* Öffnen Sie ein neues Problem, und markieren Sie es als „in Bearbeitung“ (wenn Sie ein Mitglied der PowerShell-Organisation sind), oder fügen Sie „in Bearbeitung“ als Kommentar hinzu, um anderen Benutzern mitzuteilen, woran Sie gerade arbeiten.
* Führen Sie den gleichen Workflow wie oben beschrieben aus, wenn Sie wichtige Änderungen an vorhandenen Themen vornehmen möchten.
* Bearbeiten Sie das `TOC.md`-Thema (im Ordner der obersten Ebene des jeweiligen Dokumentationssatzes), um Ihre neuen Themen zum Inhaltsverzeichnis hinzuzufügen. 
  Entscheiden Sie, wohin das neue Thema im Inhaltsverzeichnis gehört, und fügen Sie auf der entsprechenden Ebene eine Überschrift mit einem Link zu Ihrem Thema hinzu (`[My topic title](relative path to my topic)`).

## <a name="markdown-editors"></a>Markdown-Editoren

Hier finden Sie einige Markdown-Editoren, die Sie ausprobieren können:

* [Visual Studio Code](https://code.visualstudio.com)
* [Markdown Pad](http://markdownpad.com/)
* [Atom](https://atom.io/)
* [Sublime Text](http://www.sublimetext.com/)


## <a name="github-flavored-markdown-gfm"></a>GitHub Flavored Markdown (GFM)

Für alle Artikel in diesem Repository wurde [GitHub Flavored Markdown (GFM)](https://help.github.com/articles/github-flavored-markdown/) verwendet.

Grundlegende GFM-Syntaxelemente sind z. B: folgende:

* **Zeilenumbrüche oder Absätze:** In Markdown gibt es die HTML-Elemente `<br />` oder `<p />` nicht. Stattdessen wird ein neuer Absatz durch eine leere Zeile zwischen zwei Textblöcken festgelegt.

> **Hinweis**: Fügen Sie nach jedem Satz eine einzelne neue Zeile ein, um die Befehlszeilenausgabe der Unterschiede und des Verlaufs zu vereinfachen.
Dies wurde derzeit nicht für alle PowerShell-Dokumente berücksichtigt, aber wir arbeiten daran, dass dieser Standard mit der Zeit erreicht wird. Sie können gerne dabei helfen. 

* **Kursiv:** Das HTML-Element `<em>some text</em>` wird als `*some text*` geschrieben.
* **Fett:** Das HTML-Element `<strong>some text</strong>` wird als `**some text**` geschrieben.
* **Überschriften:** HTML-Überschriften werden durch `#`-Zeichen am Anfang der Zeile gekennzeichnet. 
  Die Anzahl der `#`-Zeichen entspricht der hierarchischen Ebene der Überschrift (z. B. `#` = `<h1>` und `###` = ```<h3>```).
* **Nummerierte Listen:** Wenn Sie eine nummerierte (geordnete) Liste erstellen möchten, beginnen Sie die Zeile mit `1. `.  
  Wenn Sie in einem Listenelement mehrere Elemente angeben möchten, formatieren Sie die Liste wie folgt:
```        
1.  For the first element (like this one), insert a tab stop after the 1. 

    To include a second element (like this one), insert a line break after the first and align indentations.
```
So erhalten Sie folgende Ausgabe:

1.  Fügen Sie für das erste Element (wie dieses hier) einen Tabstopp nach der 1 ein. 

    Um ein zweites Element (wie dieses hier) aufzuführen, fügen Sie nach dem ersten Element einen Zeilenumbruch ein, und richten Sie die Einzüge aus.

* **Aufzählungen:** Aufzählungen (ungeordnete Listen) sind mit geordneten Listen zu vergleichen, wobei die `1. ` jedoch entweder durch `* `, `- ` oder `+ ` ersetzt wird. Listen mit mehreren Elementen funktionieren genauso wie geordnete Listen.
* **Links:** Die Syntax für einen Link sieht folgendermaßen aus: `[visible link text](link URL)`.
* **Link zu einem anderen Thema innerhalb des gleichen Dokumentationssatzes:** Ein Dokumentationssatz ist ein Ordner der obersten Ebene in diesem Repository (z. B. „DSC“, „Skripting“).
    Die Syntax für einen Link zu einem Thema im gleichen Dokumentationssatz sieht folgendermaßen aus: `[topic title](relative path to topic)`. 
    Weitere Informationen finden Sie unter [Relative Links in Infodateien](https://help.github.com/articles/relative-links-in-readmes/). 
    Um einen Link zu einem Thema in einem anderen Ordner der obersten Ebene hinzuzufügen, verwenden Sie die URL der veröffentlichten Seite, wie oben beschrieben.
