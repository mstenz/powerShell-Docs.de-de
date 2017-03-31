# <a name="style-guide-for-powershell-docs"></a>Styleguide für PowerShell-Dokumente


## <a name="titlesheadings"></a>Titel/Überschriften

* Titel/Überschriften (alles, dem \# vorangestellt ist) müssen mit einem Zeilenumbruch ausgeführt werden
* Nur der erste Buchstaben des Titels und alle Eigennamen im Titel sollten groß geschrieben werden
* Nur 1 H1 pro Dokument
* Wenn Sie Referenzinhalte bearbeiten, werden die H2s von platyPS vorgeschriebenen und sollten nicht hinzugefügt oder entfernt werden, da dies zu einer Buildunterbrechung führt
* Verwenden Sie nur \#-Stilheader (im Gegensatz zum „=“ oder dem Stilheader \-)

### <a name="correct"></a>Richtig

```
# Header 1

## Header 2

### Header 3

```

### <a name="incorrect"></a>Falsch

```
Header 1
========

Header 2
--------

### Header 3
```

## <a name="syntax"></a>Syntax

* Verwenden Sie \` bei der Kommunikation über ein Cmdlet im Absatz, um Cmdlet-Namen zu markieren
  * Beim Schreiben eines Artikels (im Gegensatz zu Referenzinhalt) sollte die erste Instanz eines Cmdlet-Namens ein Link zur Cmdlet-Dokumentation sein
* Alle Blöcke der PowerShell-Syntax sollten &#96;&#96;&#96;powershell verwenden
* Starten Sie PowerShell-Befehle nicht mit „C:\ PS>“
* Ausgabe, die von PowerShell-Befehlen ausgegeben wurde, sollte kommentiert werden, um sie am Empfangen von Syntaxhervorhebung zu hindern
* Eigenschaftsnamen und Parameternamen sollten **fett** geschrieben werden


## <a name="lists"></a>Listen

* Beenden Sie Listenelemente nicht mit einem Punkt (sofern sie nicht mehrere Sätze enthalten)
* Wenn Ihre Liste mehrere Sätze enthält, erwägen Sie die Verwendung eines Header 3/4/5 (falls zutreffend) unter Ihrer primären Idee

## <a name="links"></a>Links

* Links werden immer mit MarkDown-Syntax `[friendlyname](url)` gekennzeichnet
* Links sollten einen Anzeigenamen haben, falls zutreffend, am besten den Titel der verknüpften Seite
  * **Ausnahme**: Links zu Seiten, die nicht von Microsoft stammen, sollten nur eine URL enthalten
* Alle Elemente im Abschnitt „Verwandte Links“ am unteren Rand sollten mit einem Link versehen sein. 

## <a name="line-breaks"></a>Zeilenumbrüche

* Sie müssen semantische Zeilenumbrüche einschließen
* Sie sollten Zeilen auf 100 Zeichen einschränken (Element öffnen: Tools helfen uns dies zu überprüfen).
* Sie können zusätzliche Zeilenumbrüche für PS4+ entfernen, aber NICHT für ps3 (Überprüfung erforderlich)
