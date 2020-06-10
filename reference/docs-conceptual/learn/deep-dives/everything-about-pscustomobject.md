---
title: Was Sie schon immer über PSCustomObject wissen wollten
description: PSCustomObject ist eine einfache Möglichkeit zum Erstellen strukturierter Daten.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: fbc8b5b6d2cfafaa75fa820f420762a1804074ac
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149493"
---
# <a name="everything-you-wanted-to-know-about-pscustomobject"></a>Was Sie schon immer über PSCustomObject wissen wollten

`PSCustomObject` ist ein großartiges Tool, das Sie Ihrer PowerShell-Toolsammlung hinzufügen können. Lassen Sie uns mit den Grundlagen beginnen und dann zu den komplexeren Features vorarbeiten. Zweck von `PSCustomObject` ist das Bieten einer einfachen Möglichkeit zum Erstellen strukturierter Daten. Werfen Sie einen Blick auf das erste Beispiel, um eine bessere Vorstellung davon zu bekommen, was das bedeutet.

> [!NOTE]
> Die [Originalversion][] dieses Artikels ist im Blog von [@KevinMarquette][] erschienen. Das PowerShell-Team dankt Kevin Marquette, dass er diesen Inhalt mit uns teilt. Weitere Informationen finden Sie in seinem Blog auf [PowerShellExplained.com][].

## <a name="creating-a-pscustomobject"></a>Erstellen eines PSCustomObject

Ich verwende `[PSCustomObject]` sehr gern in PowerShell. Das Erstellen eines nützlichen Objekts war noch nie so einfach.
Aus diesem Grund überspringe ich alle anderen Möglichkeiten zum Erstellen eines Objekts, aber ich muss erwähnen, dass die meisten dieser Beispiele sich auf PowerShell 3.0 und neuer beziehen.

```powershell
$myObject = [PSCustomObject]@{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
```

Diese Methode funktioniert bei mir gut, weil ich für so gut wie alles Hashtabellen nutze. Aber es gibt Situationen, in denen ich möchte, dass PowerShell Hashtabellen eher wie ein Objekt behandelt. Den Unterschied merken Sie erst, wenn Sie `Format-Table` oder `Export-CSV` einsetzen möchten und Ihnen klar wird, dass eine Hashtabelle nur eine Sammlung von Schlüssel-Wert-Paaren ist.

Sie können dann wie bei einem normalen Objekt auf die Werte zugreifen und sie verwenden.

```powershell
$myObject.Name
```

### <a name="converting-a-hashtable"></a>Konvertieren einer Hashtabelle

Wo ich gerade beim Thema bin, wussten Sie, dass Sie dies tun können:

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
$myObject = [pscustomobject]$myHashtable
```

Ich erstelle das Objekt am liebsten von Grund auf, aber es gibt Fälle, in denen Sie zunächst mit einer Hashtabelle arbeiten müssen. Dieses Beispiel funktioniert, weil der Konstruktor eine Hashtabelle für die Objekteigenschaften verwendet. Ein wichtiger Hinweis ist, dass diese Methode zwar funktioniert, aber kein exaktes Pendant darstellt. Der größte Unterschied besteht darin, dass die Reihenfolge der Eigenschaften nicht beibehalten wird.

### <a name="legacy-approach"></a>Methode für ältere PowerShell-Versionen

Sie haben vielleicht gesehen, dass `New-Object` zum Erstellen benutzerdefinierter Objekte genutzt wird.

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}

$myObject = New-Object -TypeName PSObject -Property $myHashtable
```

Diese Methode ist zwar etwas langsamer, könnte aber bei älteren Versionen von PowerShell die beste Wahl sein.

### <a name="saving-to-a-file"></a>Speichern in einer Datei

Ich finde, die beste Möglichkeit, eine Hashtabelle in einer Datei zu speichern, ist die Speicherung als JSON. Sie können sie zurück in ein `[PSCusomObject]` importieren.

```powershell
$myObject | ConvertTo-Json -depth 1- | Set-Content -Path $Path
$myObject = Get-Content -Path $Path | ConvertFrom-Json
```

Weitere Möglichkeiten, Objekte in einer Datei zu speichern, beschreibe ich in meinem Artikel über [die vielen Möglichkeiten, Daten in Dateien zu lesen und zu schreiben][].

## <a name="working-with-properties"></a>Arbeiten mit Eigenschaften

### <a name="adding-properties"></a>Hinzufügen von Eigenschaften

Sie können Ihrem `PSCustomObject` weiterhin mit `Add-Member` neue Eigenschaften hinzufügen.

```powershell
$myObject | Add-Member -MemberType NoteProperty -Name `ID` -Value 'KevinMarquette'

$myObject.ID
```

### <a name="remove-properties"></a>Entfernen von Eigenschaften

Sie können Eigenschaften auch aus einem Objekt entfernen.

```powershell
$myObject.psobject.properties.remove('ID')
```

`psobject` ist eine verborgene Eigenschaft, die Ihnen Zugriff auf grundlegende Objektmetadaten bietet.

### <a name="enumerating-property-names"></a>Aufzählen von Eigenschaftsnamen

Gelegentlich benötigen Sie eine Liste mit den Namen aller Eigenschaften eines Objekts.

```powershell
$myObject | Get-Member -MemberType NoteProperty | Select -ExpandProperty Name
```

Wir können diese Liste auch aus der `psobject`-Eigenschaft abrufen.

```powershell
$myobject.psobject.properties.name
```

### <a name="dynamically-accessing-properties"></a>Dynamisches Zugreifen auf Eigenschaften

Ich habe bereits erwähnt, dass Sie auf Eigenschaftswerte direkt zugreifen können.

```powershell
$myObject.Name
```

Sie können eine Zeichenfolge für den Eigenschaftsnamen nutzen und sie funktioniert trotzdem.

```powershell
$myObject.'Name'
```

Wir können noch einen Schritt weitergehen und eine Variable für den Eigenschaftsnamen verwenden.

```powershell
$property = 'Name'
$myObject.$property
```

Ich weiß, das sieht seltsam aus, aber es funktioniert.

### <a name="convert-pscustomboject-into-a-hashtable"></a>Konvertieren von PSCustomObject in eine Hashtabelle

Zur Fortsetzung des letzten Abschnitts können Sie die Eigenschaften dynamisch durchlaufen und daraus eine Hashtabelle erstellen.

```powershell
$hashtable = @{}
foreach( $property in $myobject.psobject.properties.name )
{
    $hashtable[$property] = $myObject.$property
}
```

### <a name="testing-for-properties"></a>Testen auf Eigenschaften

Wenn Sie wissen müssen, ob eine Eigenschaft vorhanden ist, können Sie einfach prüfen, ob diese Eigenschaft einen Wert hat.

```powershell
if( $null -ne $myObject.ID )
```

Aber wenn der Wert `$null` sein könnte und Sie trotzdem auf diesen prüfen müssen, können Sie `psobject.properties` darauf untersuchen.

```powershell
if( $myobject.psobject.properties.match('ID') )
```

## <a name="adding-object-methods"></a>Hinzufügen von Objektmethoden

Wenn Sie einem Objekt eine Skriptmethode hinzufügen müssen, können Sie dies mit `Add-Member` und einem `ScriptBlock` tun. Sie müssen die automatische Variable `this` verwenden, um auf das aktuelle Objekt zu verweisen. Hier ist ein `scriptblock` zum Umwandeln eines Objekts in eine Hashtabelle. (gleicher Code aus dem letzten Beispiel)

```powershell
$ScriptBlock = {
    $hashtable = @{}
    foreach( $property in $this.psobject.properties.name )
    {
        $hashtable[$property] = $this.$property
    }
    return $hashtable
}
```

Dann fügen wir ihn unserem Objekt als Skripteigenschaft hinzu.

```powershell
$memberParam = @{
    MemberType = "ScriptMethod"
    InputObject = $myobject
    Name = "ToHashtable"
    Value = $scriptBlock
}
Add-Member @memberParam
```

Anschließend können wir unsere Funktion wie folgt aufrufen:

```powershell
$myObject.ToHashtable()
```

### <a name="objects-vs-value-types"></a>Objekte im Vergleich zu Werttypen

Objekte und Werttypen behandeln Variablenzuweisungen nicht auf gleiche Weise. Wenn Sie Werttypen einander zuweisen, wird nur der Wert in die neue Variable kopiert.

```powershell
$first = 1
$second = $first
$second = 2
```

In diesem Fall ist `$first` gleich 1 und `$second` gleich 2.

Objektvariablen enthalten einen Verweis auf das tatsächliche Objekt. Wenn Sie ein Objekt einer neuen Variablen zuweisen, verweist es immer noch auf dasselbe Objekt.

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third
$fourth.Key = 4
```

Da `$third` und `$fourth` auf dieselbe Instanz eines Objekts verweisen, sind sowohl `$third.key` als auch `$fourth.Key` gleich 4.

### <a name="psobjectcopy"></a>psobject.copy()

Wenn Sie eine originalgetreue Kopie eines Objekts benötigen, können Sie es klonen.

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third.psobject.copy()
$fourth.Key = 4
```

Beim Klonen wird eine flache Kopie des Objekts erstellt. Es gibt jetzt verschiedene Instanzen, wobei in diesem Beispiel `$third.key` gleich 3 und `$fourth.Key` gleich 4 ist.

Ich nenne dies eine flache Kopie, weil es geschachtelte Objekte gibt (bei denen die Eigenschaften andere Objekte enthalten). Nur die Werte auf oberster Ebene werden kopiert. Die untergeordneten Objekte verweisen aufeinander.

### <a name="pstypename-for-custom-object-types"></a>PSTypeName für benutzerdefinierte Objekttypen

Jetzt, da wir ein Objekt haben, können wir noch ein paar Dinge damit anstellen, die möglicherweise nicht ganz so offensichtlich sind. Als Erstes müssen wir ihm einen `PSTypeName` zuweisen. Dies erfolgt meist so:

```powershell
$myObject.PSObject.TypeNames.Insert(0,"My.Object")
```

In diesem [Beitrag von /u/markekraus][] habe ich vor Kurzem eine weitere Möglichkeit entdeckt. Ich habe ein wenig recherchiert und weitere Beiträge zu der Idee von [Adam Bertram][] und [Mike Shepard][] gefunden, in denen sie über diesen Ansatz sprechen, der es Ihnen erlaubt, ihn inline zu definieren.

```powershell
$myObject = [PSCustomObject]@{
    PSTypeName = 'My.Object'
    Name       = 'Kevin'
    Language   = 'PowerShell'
    State      = 'Texas'
}
```

Es gefällt mir, wie gut das einfach zur Sprache passt. Nachdem wir nun über ein Objekt mit einem ordnungsgemäßen Typnamen verfügen, können wir weitere Aktionen ausführen.

## <a name="using-defaultpropertyset-the-long-way"></a>Verwenden von DefaultPropertySet (Langfassung)

PowerShell entscheidet für uns, welche Eigenschaften standardmäßig angezeigt werden. Bei vielen der nativen Befehle gibt es die [Formatierungsdatei][] `.ps1xml`, die alle anfallenden Aufgaben übernimmt. In diesem [Beitrag von Boe Prox][] gibt es eine weitere Möglichkeit, wie wir dies nur mithilfe von PowerShell auf unser benutzerdefiniertes Objekt anwenden können. Wir können ihm ein `MemberSet` zur Verfügung stehen.

```powershell
$defaultDisplaySet = 'Name','Language'
$defaultDisplayPropertySet = New-Object System.Management.Automation.PSPropertySet(‘DefaultDisplayPropertySet’,[string[]]$defaultDisplaySet)
$PSStandardMembers = [System.Management.Automation.PSMemberInfo[]]@($defaultDisplayPropertySet)
$MyObject | Add-Member MemberSet PSStandardMembers $PSStandardMembers
```

Wenn mein Objekt nun einfach in der Shell verwendet wird, zeigt es standardmäßig nur diese Eigenschaften.

### <a name="update-typedata-with-defaultpropertyset"></a>Update-TypeData mit DefaultPropertySet

Das ist zwar ganz nett, aber ich habe kürzlich in [PowerShell unplugged 2016 mit Jeffrey Snover und Don Jones][psunplugged] eine bessere Möglichkeit gesehen. Jeffrey nutzte [Update-TypeData][], um die Standardeigenschaften anzugeben.

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    DefaultDisplayPropertySet = 'Name','Language'
}
Update-TypeData @TypeData
```

Das ist so einfach, dass ich mich fast daran erinnern könnte, wenn ich diesen Beitrag nicht als Schnellreferenz hätte. Jetzt kann ich ganz einfach Objekte mit vielen Eigenschaften erstellen und trotzdem eine ansprechende, übersichtliche Ansicht bieten, wenn ich sie in der Shell betrachte. Wenn ich auf diese anderen Eigenschaften zugreifen oder sie einsehen muss, sind sie immer noch da.

```powershell
$myObject | Format-List *
```

### <a name="update-typedata-with-scriptproperty"></a>Update-TypeData mit ScriptProperty

Etwas anderes, was ich in diesem Video erfahren habe, war das Erstellen von Skripteigenschaften für Ihre Objekte. Dies wäre ein guter Zeitpunkt, darauf hinzuweisen, dass dies auch für bestehende Objekte gilt.

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    MemberType = 'ScriptProperty'
    MemberName = 'UpperCaseName'
    Value = {$this.Name.toUpper()}
}
Update-TypeData @TypeData
```

Sie können dies vor oder nach der Erstellung Ihres Objekts tun, wobei es weiterhin funktionieren wird. Das ist der Unterschied zur Nutzung von `Add-Member` mit einer Skripteigenschaft. Wenn Sie `Add-Member` wie zuvor beschrieben nutzen, ist es nur in dieser speziellen Instanz des Objekts vorhanden. Dieser gilt für alle Objekte mit diesem `TypeName`.

## <a name="function-parameters"></a>Funktionsparameter

Sie können diese benutzerdefinierten Typen jetzt für Parameter in Ihren Funktionen und Skripts nutzen. Sie können diese benutzerdefinierten Objekte von einer Funktion erstellen lassen und sie dann an andere Funktionen übergeben.

```powershell
param( [PSTypeName('My.Object')]$Data )
```

PowerShell setzt voraus, dass das Objekt dem von Ihnen angegebenen Typ entspricht. Ein Validierungsfehler wird automatisch ausgelöst, wenn der Typ nicht übereinstimmt, um Ihnen in Ihrem Code den Testschritt dafür zu ersparen. Ein großartiges Beispiel dafür, PowerShell das tun zu lassen, was es am besten kann.

### <a name="function-outputtype"></a>OutputType von Funktion

Sie können für Ihre erweiterten Funktionen auch einen `OutputType` definieren.

```powershell
function Get-MyObject
{
    [OutputType('My.Object')]
    [CmdletBinding()]
        param
        (
            ...
```

Der Wert des Attributs **OutputType** ist nur ein Dokumentationshinweis. Er ist nicht vom Funktionscode abgeleitet bzw. wird nicht mit der tatsächlichen Funktionsausgabe verglichen.

Der Hauptgrund für die Nutzung eines Ausgabetyps besteht darin, dass Metainformationen zu Ihrer Funktion Ihre Absichten widerspiegeln sollen. Dinge wie `Get-Command` und `Get-Help`, die sich Ihre Entwicklungsumgebung zunutze machen kann. Wenn Sie weitere Informationen wünschen, werfen Sie einen Blick in die Hilfe dazu: [about_Functions_OutputTypeAttribute][].

Wenn Sie mit Pester Komponententests Ihrer Funktionen durchführen, wäre es eine gute Idee, die Ausgabeobjekte zu überprüfen, die Ihrem **OutputType** entsprechen. Dadurch könnten Variablen abgefangen werden, die sonst durchfallen würden, obwohl sie das nicht sollten.

## <a name="closing-thoughts"></a>Schlussbemerkung

In diesem Artikel ging es um `[PSCustomObject]`, aber viele dieser Informationen gelten für Objekte im Allgemeinen.

Ich habe die meisten dieser Features schon einmal im Vorübergehen gesehen, aber bislang nicht als eine Sammlung von Informationen zu `PSCustomObject` präsentiert bekommen. Erst letzte Woche bin ich über ein weiteres gestolpert und war überrascht, dass ich es vorher noch nicht gesehen hatte. Ich wollte all diese Ideen zusammenbringen, damit Sie hoffentlich das große Ganze sehen und sich im Bedarfsfall Ihrer Möglichkeiten bewusst sind. Ich hoffe, Sie haben etwas gelernt und können eine Möglichkeit finden, dies in Ihre Skripts einzubauen.

<!-- link references -->
[Originalversion]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Beitrag von Boe Prox]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[Formatierungsdatei]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[about_Functions_OutputTypeAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute
[Die vielen Möglichkeiten, Daten in Dateien zu lesen und zu schreiben]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[Beitrag von /u/markekraus]: https://www.reddit.com/r/PowerShell/comments/590awc/is_it_possible_to_initialize_a_pscustoobject_with/
[Adam Bertram]: http://www.adamtheautomator.com/building-custom-object-types-PowerShell-pstypename/
[Mike Shepard]: https://powershellstation.com/2016/05/22/custom-objects-and-pstypename/
[psunplugged]: https://www.youtube.com/watch?v=Ab46gHXNm8Q
[Update-TypeData]: /powershell/module/microsoft.powershell.utility/update-typedata
