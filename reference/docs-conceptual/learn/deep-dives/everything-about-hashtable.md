---
title: Alles, was Sie schon immer über Hashtabellen wissen wollten
description: Hashtabellen spielen eine wichtige Rolle in PowerShell, daher sollten Sie mit dem Konzept vertraut sein.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 336c32cca351cc7d87f3300364c075ba7bd8aaeb
ms.sourcegitcommit: 0b9268e7b92fb76b47169b72e28de43e4bfe7fbf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/03/2020
ms.locfileid: "84307128"
---
# <a name="everything-you-wanted-to-know-about-hashtables"></a>Alles, was Sie schon immer über Hashtabellen wissen wollten

Heute möchte ich einen Schritt zurückgehen und über [Hashtabellen][] sprechen. Ich verwende sie die ganze Zeit. Nach dem Treffen unserer Benutzergruppe gestern habe ich sie einem anderen Benutzer erklärt und dabei festgestellt, dass mich dieselben Aspekte verwirren wie ihn. Hashtabellen spielen eine wichtige Rolle in PowerShell, daher sollten Sie mit dem Konzept vertraut sein.

> [!NOTE]
> Die [Originalversion][] dieses Artikels wurde im Blog von [@KevinMarquette][] veröffentlicht. Das PowerShell-Team dankt Kevin Marquette, dass er diesen Inhalt mit uns teilt. Weitere Informationen finden Sie in seinem Blog auf [PowerShellExplained.com][].

## <a name="hashtable-as-a-collection-of-things"></a>Hashtabellen als Auflistung

Sie sollten sich eine **Hashtabelle** zunächst als Auflistung in der herkömmlichen Definition einer Hashtabelle vorstellen. Diese Definition hilft dabei, die Funktionsweise von Hashtabellen zu verstehen – und dieses Grundverständnis ist erforderlich, wenn es später um fortgeschrittene Prozesse geht. Wenn dieses Grundverständnis fehlt, entsteht oft Verwirrung.

## <a name="what-is-an-array"></a>Was ist ein Array?

Bevor wir in das Thema **Hashtabelle** eintauchen, muss ich kurz auf [Arrays][] eingehen. Ein Array ist – zumindest für den Zweck der vorliegenden Diskussion – eine Liste oder Auflistung von Werten oder Objekten.

```powershell
$array = @(1,2,3,5,7,11)
```

Sobald Sie Ihre Elemente in ein Array eingefügt haben, können Sie `foreach` zum Durchlaufen der Liste oder einen Index zum Zugreifen auf einzelne Elemente im Array verwenden.

```powershell
foreach($item in $array)
{
    Write-Output $item
}

Write-Output $array[3]
```

Sie können auch auf die gleiche Weise Werte mit einem Index aktualisieren.

```powershell
$array[2] = 13
```

Damit habe ich praktisch nur an der Oberfläche von Arrays gekratzt, aber ich wollte sie auch nur für das Verständnis von Hashtabellen in den richtigen Kontext setzen.

## <a name="what-is-a-hashtable"></a>Was ist eine Hashtabelle?

Ich beginne mit einer grundlegenden technischen Beschreibung von Hashtabellen im Allgemeinen, bevor ich mit den weiteren Verwendungsmöglichkeiten in PowerShell fortfahre.

Eine Hashtabelle ist eine Datenstruktur – ganz ähnlich einem Array, außer dass jeder Wert (bzw. jedes Objekt) mithilfe eines Schlüssels gespeichert wird. Im Grunde ist es ein Schlüssel-Wert-Speicher. Als Erstes erstellen wir eine leere Hashtabelle.

```powershell
$ageList = @{}
```

Beachten Sie, dass zum Definieren einer Hashtabelle geschweifte statt runde Klammern verwendet werden. Dann fügen wir mithilfe eines Schlüssels ein Element hinzu:

```powershell
$key = 'Kevin'
$value = 36
$ageList.add( $key, $value )

$ageList.add( 'Alex', 9 )
```

Der Name der Person ist der Schlüssel, das Alter ist der Wert, den ich speichern möchte.

## <a name="using-the-brackets-for-access"></a>Verwenden von eckigen Klammern für den Zugriff

Sobald Sie Werte zur Hashtabelle hinzugefügt haben, können Sie diese mit demselben Schlüssel wieder abrufen (anstatt einen numerischen Index zu verwenden, wie es bei einem Array erforderlich wäre).

```powershell
$ageList['Kevin']
$ageList['Alex']
```

Wenn ich Kevins Alter abrufen möchte, verwende ich seinen Namen für den Zugriff. Wir können diesen Ansatz auch verwenden, um Werte zur Hashtabelle hinzuzufügen oder darin zu aktualisieren. Das funktioniert genauso wie die `add()`-Funktion von oben.

```powershell
$ageList = @{}

$key = 'Kevin'
$value = 36
$ageList[$key] = $value

$ageList['Alex'] = 9
```

Es gibt eine weitere Syntax, die Sie verwenden können, um auf Werte zuzugreifen und diese zu aktualisieren. Auf diese Syntax werde ich in einem späteren Abschnitt eingehen. Wenn Sie vor PowerShell eine andere Sprache verwendet haben, sollten diese Beispiele zu der Art und Weise passen, mit der Sie Hashtabellen bisher verwendet haben.

### <a name="creating-hashtables-with-values"></a>Erstellen von Hashtabellen mit Werten

Bisher habe ich in den Beispielen eine leere Hashtabelle erstellt. Sie können die Schlüssel und Werte beim Erstellen vorab auffüllen.

```powershell
$ageList = @{
    Kevin = 36
    Alex  = 9
}
```

### <a name="as-a-lookup-table"></a>Als Nachschlagetabelle

Der wahre Wert dieser Art Hashtabelle liegt darin, dass Sie diese als Nachschlagetabelle verwenden können. Hier ist ein einfaches Beispiel.

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}

$server = $environments[$env]
```

In diesem Beispiel geben Sie eine Umgebung für die Variable `$env` an, und diese wählt den richtigen Server aus. Für eine solche Auswahl könnten Sie auch `switch($env){...}` verwenden, aber eine Hashtabelle ist eine gute Option.

Diese Option wird sogar noch besser, wenn Sie die Nachschlagetabelle zur späteren Verwendung dynamisch erstellen. Behalten Sie diesen Ansatz also im Hinterkopf, wenn Sie Querverweise benötigen. Dieser Ansatz wäre vermutlich noch häufiger zu finden, wenn die Pipefilterung mit `Where-Object` in PowerShell nicht so gut funktionieren würde. Wenn Sie sich jemals in einer Situation befinden, in der die Leistung eine große Rolle spielt, sollten Sie diesen Ansatz in Betracht ziehen.

Ich behaupte nicht, dass dieser Ansatz immer schneller ist, aber er passt in die Regel: [Wenn Leistung wichtig ist, probier es aus][].

#### <a name="multiselection"></a>Mehrfachauswahl

Im Allgemeinen sollten Sie sich eine Hashtabelle als Schlüssel-Wert-Paar vorstellen, in dem Sie einen Schlüssel bereitstellen und einen Wert erhalten. PowerShell ermöglicht die Bereitstellung eines Arrays aus Schlüsseln, um mehrere Werte abzurufen.

```powershell
$environments[@('QA','DEV')]
$environments[('QA','DEV')]
$environments['QA','DEV']
```

In diesem Beispiel verwende ich die Nachschlagetabelle von oben und stelle drei verschiedene Arraystile bereit, um die Übereinstimmungen abzurufen. Das ist ein verborgenes Juwel in PowerShell, das den meisten Benutzern nicht bekannt ist.

## <a name="iterating-hashtables"></a>Durchlaufen von Hashtabellen

Da eine Hashtabelle eine Auflistung aus Schlüssel-Wert-Paaren ist, durchlaufen Sie diese auf andere Weise als ein Array oder eine „normale“ Elementliste.

Wenn Sie die Hashtabelle weiterreichen, wird sie in der Pipe als ein einzelnes Objekt behandelt.

```powershell
PS> $ageList | Measure-Object
count : 1
```

Dies ist der Fall, auch wenn die `.count`-Eigenschaft Sie darüber informiert, wie viele Werte in der Tabelle enthalten sind.

```powershell
PS> $ageList.count
2
```

Sie können dieses Problem umgehen, indem Sie die `.values`-Eigenschaft verwenden, wenn Sie nur die Werte benötigen.

```powershell
PS> $ageList.values | Measure-Object -Average
Count   : 2
Average : 22.5
```

Häufig ist es sinnvoller, die Schlüssel aufzuzählen und für den Zugriff auf die Werte zu verwenden.

```powershell
PS> $ageList.keys | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_, $ageList[$_]
    Write-Output $message
}
Kevin is 36 years old
Alex is 9 years old
```

Nachfolgend sehen Sie dasselbe Beispiel mit einer `foreach(){...}`-Schleife.

```powershell
foreach($key in $ageList.keys)
{
    $message = '{0} is {1} years old' -f $key, $ageList[$key]
    Write-Output $message
}
```

Wir durchlaufen jeden Schlüssel in der Hashtabelle und verwenden ihn für den Zugriff auf den entsprechenden Wert. Dies ist ein gängiges Muster, wenn Hashtabellen als Auflistung eingesetzt werden.

### <a name="getenumerator"></a>GetEnumerator()

Damit kommen wir zu `GetEnumerator()` zum Durchlaufen der Hashtabelle.

```powershell
$ageList.GetEnumerator() | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_.key, $_.value
    Write-Output $message
}
```

Der Enumerator liefert alle Schlüssel-Wert-Paare nacheinander. Er wurde speziell für diesen Anwendungsfall entwickelt. Vielen Dank an [Mark Kraus](https://get-PowerShellblog.blogspot.com), dass er mich daran erinnert hat.

### <a name="badenumeration"></a>BadEnumeration

Ein wichtiges Detail: Sie können eine Hashtabelle nicht ändern, während sie aufgezählt wird. Wir beginnen mit unserem grundlegenden `$environments`-Beispiel:

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}
```

Jetzt versuchen wir, jeden Schlüssel auf denselben Serverwert festzulegen. Das geht schief.

```powershell
$environments.Keys | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}

An error occurred while enumerating through a collection: Collection was modified; enumeration operation may not execute.
+ CategoryInfo          : InvalidOperation: tableEnumerator:HashtableEnumerator) [], RuntimeException
+ FullyQualifiedErrorId : BadEnumeration
```

Das geht auch dann schief, wenn es so aussieht, als wäre alles in Ordnung:

```powershell
foreach($key in $environments.keys) {
    $environments[$key] = 'SrvDev03'
}

Collection was modified; enumeration operation may not execute.
    + CategoryInfo          : OperationStopped: (:) [], InvalidOperationException
    + FullyQualifiedErrorId : System.InvalidOperationException
```

Der Trick hierbei ist, die Schlüssel zu klonen, bevor die Enumeration erfolgt.

```powershell
$environments.Keys.Clone() | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}
```

## <a name="hashtable-as-a-collection-of-properties"></a>Hashtabellen als Auflistung von Eigenschaften

Bisher wiesen alle Objekte, die wir in der Hashtabelle platziert haben, denselben Typ auf. Ich habe in allen Beispielen das Alter als Wert und den Namen der Personen als Schlüssel verwendet. Das ist eine hervorragende Vorgehensweise, wenn alle Objekte in Ihrer Auflistung einen Namen haben. Eine weiterer gängiger Einsatzzweck von Hashtabellen in PowerShell sind Auflistungen aus Eigenschaften, bei denen der Schlüssel der Name der Eigenschaft ist. Darum geht es im nächsten Beispiel.

### <a name="property-based-access"></a>Eigenschaftenbasierter Zugriff

Der Einsatz des eigenschaftenbasierten Zugriffs ändert die Dynamik von Hashtabellen und deren Verwendung in PowerShell. Hier sehen Sie das Beispiel von oben, die Schlüssel werden als Eigenschaften behandelt.

```powershell
$ageList = @{}
$ageList.Kevin = 35
$ageList.Alex = 9
```

Wie in den Beispielen oben fügt dieses Beispiel die Schlüssel hinzu, wenn sie in der Hashtabelle noch nicht vorhanden sind. Je nachdem, wie Sie Ihre Schlüssel definiert haben und wie Ihre Werte lauten, ist das entweder ein bisschen merkwürdig oder einfach perfekt. Das Beispiel mit der Altersliste hat bis zu diesem Punkt hervorragend funktioniert. Für den weiteren Verlauf benötigen wir aber ein neues Beispiel.

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
```

Und wir können `$person` wie folgt Attribute hinzufügen und darauf zugreifen.

```powershell
$person.city = 'Austin'
$person.state = 'TX'
```

Siehe da – plötzlich fühlt sich diese Hashtabelle an wie ein Objekt und verhält sich auch so. Es handelt sich noch immer um eine Auflistung von Elementen, daher gelten alle obigen Beispiele weiterhin. Wir gehen nur aus einem anderen Blickwinkel an das Ganze heran.

### <a name="checking-for-keys-and-values"></a>Überprüfen auf Schlüssel und Werte

In den meisten Fällen können Sie einfach folgendermaßen testen, ob ein Wert vorhanden ist:

```powershell
if( $person.age ){...}
```

Das sieht so einfach aus, war aber für mich eine Quelle zahlreicher Fehler, weil ich in meiner Logik ein wichtiges Detail übersehen hatte. Ich habe diese Anweisung verwendet, um zu testen, ob ein Schlüssel vorhanden ist. Wenn der Wert `$false` oder Null ist, gibt diese Anweisung unerwartet `$false` zurück.

```powershell
if( $person.age -ne $null ){...}
```

Damit lässt sich das Problem der Nullwerte umgehen, aber nicht das Problem von „$null“ im Gegensatz zu nicht vorhandenen Schlüsseln. In den meisten Fällen müssen Sie diesen Unterschied nicht machen, es gibt aber Funktionen, bei denen dies notwendig ist.

```powershell
if( $person.ContainsKey('age') ){...}
```

Wir haben auch eine `ContainsValue()`-Funktion für Situationen, in denen Sie auf einen Wert prüfen müssen, ohne den Schlüssel zu kennen oder die gesamte Auflistung zu durchlaufen.

### <a name="removing-and-clearing-keys"></a>Entfernen und Leeren von Schlüsseln

Sie können Schlüssel mit der Funktion `.Remove()` entfernen.

```powershell
$person.remove('age')
```

Indem Sie einen `$null`-Wert zuweisen, bleibt einfach ein Schlüssel mit einem `$null`-Wert übrig.

Eine gängige Vorgehensweise zum Leeren einer Hashtabelle besteht drin, diese in einer leeren Hashtabelle zu initialisieren.

```powershell
$person = @{}
```

Dies funktioniert zwar, aber Sie sollten stattdessen versuchen, die `clear()`-Funktion zu verwenden.

```powershell
$person.clear()
```

Dies ist einer der Fälle, in denen durch Verwendung der Funktion ein selbst dokumentierender Code entsteht und die Absichten des Codes sehr klar dargestellt werden.

## <a name="all-the-fun-stuff"></a>Alles, was Spaß macht

### <a name="ordered-hashtables"></a>Geordnete Hashtabellen

Standardmäßig sind Hashtabellen nicht geordnet (sortiert). Im herkömmlichen Kontext spielt die Reihenfolge keine Rolle, wenn Sie für den Zugriff auf Werte immer einen Schlüssel verwenden. Möglicherweise möchten Sie aber, dass die Eigenschaften in der von Ihnen definierten Reihenfolge bleiben. Glücklicherweise gibt es eine Möglichkeit, dies zu erreichen: mit dem Schlüsselwort `ordered`.

```powershell
$person = [ordered]@{
    name = 'Kevin'
    age  = 36
}
```

Wenn Sie die Schlüssel und Werte jetzt aufzählen, bleiben sie in der gegebenen Reihenfolge.

### <a name="inline-hashtables"></a>Inline-Hashtabellen

Wenn Sie eine Hashtabelle auf einer einzigen Zeile definieren, können Sie die Schlüssel-Wert-Paare mit Semikolons trennen.

```powershell
$person = @{ name = 'kevin'; age = 36; }
```

Das ist praktisch, wenn Sie sie in der Pipe erstellen.

### <a name="custom-expressions-in-common-pipeline-commands"></a>Benutzerdefinierte Ausdrücke in gängigen Pipelinebefehlen

Es gibt einige Cmdlets, die die Verwendung von Hashtabellen zum Erstellen benutzerdefinierter oder berechneter Eigenschaften unterstützen. Dies sehen wir meist bei `Select-Object` und `Format-Table`. Die Hashtabellen weisen eine spezielle Syntax auf, die bei vollständiger Erweiterung folgendermaßen aussieht.

```powershell
$property = @{
    name = 'totalSpaceGB'
    expression = { ($_.used + $_.free) / 1GB }
}
```

Das Cmdlet bezeichnet die Spalte mit `name`. `expression` ist ein Skriptblock, der ausgeführt wird, wobei `$_` der Wert des Objekts in der Pipe ist. Hier sehen Sie das Skript in Aktion:

```powershell
$drives = Get-PSDrive | Where Used
$drives | Select-Object -Properties name, $property

Name     totalSpaceGB
----     ------------
C    238.472652435303
```

Ich habe das Ganze in einer Variable platziert, aber Sie könnten es auch inline definieren und bei der Gelegenheit `name` zu `n` sowie `expression` zu `e` verkürzen.

```powershell
$drives | Select-Object -properties name, @{n='totalSpaceGB';e={($_.used + $_.free) / 1GB}}
```

Mir persönlich gefällt nicht, dass Befehle damit so lang werden, und außerdem werden damit schlechte Angewohnheiten gefördert, in die ich nicht verfallen möchte. Ich erstelle eher eine neue Hashtabelle oder ein `pscustomobject` mit allen benötigten Feldern und Eigenschaften, als diesen Ansatz in Skripts zu verwenden. Es gibt aber sehr viel Code, in dem das so gehandhabt wird, daher wollte ich Sie darauf aufmerksam machen. Auf das Thema `pscustomobject` komme ich etwas später zurück.

### <a name="custom-sort-expression"></a>Benutzerdefinierter Sortierungsausdruck

Es ist einfach, eine Auflistung zu sortieren, wenn die Objekte die Daten enthalten, die Sie sortieren möchten. Sie können entweder vor dem Sortieren Daten zum Objekt hinzufügen oder einen benutzerdefinierten Ausdruck für `Sort-Object` erstellen.

```powershell
Get-ADUser | Sort-Object -Parameter @{ e={ Get-TotalSales $_.Name } }
```

In diesem Beispiel nehme ich eine Liste mit Benutzern und verwende ein benutzerdefiniertes Cmdlet, um zusätzliche Informationen nur zur Sortierung zu erhalten.

#### <a name="sort-a-list-of-hashtables"></a>Sortieren einer Liste von Hashtabellen

Wenn Sie eine Liste von Hashtabellen sortieren möchten, werden Sie feststellen, dass das `Sort-Object` die Schlüssel nicht als Eigenschaften behandelt. Dieses Problem können wir umgehen, indem wir einen benutzerdefinierten Sortierungsausdruck verwenden.

```powershell
$data = @(
    @{name='a'}
    @{name='c'}
    @{name='e'}
    @{name='f'}
    @{name='d'}
    @{name='b'}
)

$data | Sort-Object -Property @{e={$_.name}}
```

## <a name="splatting-hashtables-at-cmdlets"></a>Übergabe von Hashtabellen in Cmdlets per Splatting

Das ist eine meiner Lieblingsfunktionen für Hashtabellen, die viele Entwickler kaum kennen.
Der Gedanke dahinter: Anstatt alle Eigenschaften für ein Cmdlet in einer Zeile anzugeben, können Sie diese zuerst in eine Hashtabelle packen. Dann können Sie die Hashtabelle auf spezielle Weise an die Funktion übergeben.
Hier sehen Sie ein Beispiel für die „normale“ Erstellung eines DHCP-Bereichs.

```powershell
Add-DhcpServerv4Scope -Name 'TestNetwork' -StartRange'10.0.0.2' -EndRange '10.0.0.254' -SubnetMask '255.255.255.0' -Description 'Network for testlab A' -LeaseDuration (New-TimeSpan -Days 8) -Type "Both"
```

Ohne [Splatting][] müsste all dies auf einer einzigen Zeile definiert werden. Damit läuft die Zeile aus dem Bild oder wird an beliebigen Stellen umbrochen. Im Vergleich dazu ein Befehl, der Splatting verwendet.

```powershell
$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    SubnetMask  = '255.255.255.0'
    Description = 'Network for testlab A'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}
Add-DhcpServerv4Scope @DHCPScope
```

Die Verwendung des `@`-Zeichens anstelle von `$` ruft den Splat-Vorgang auf.

Nehmen Sie sich einen Moment Zeit, und genießen Sie, wie einfach dieses Beispiel zu lesen ist. Es handelt sich um exakt denselben Befehl mit exakt denselben Werten. Aber dieses zweite Beispiel lässt sich wesentlich einfacher verstehen und im weiteren Verlauf auch verwalten.

Ich verwende Splatting immer dann, wenn ein Befehl zu lang wird. Unter „zu lang“ verstehe ich Befehle, die dazu führen, dass mein Fenster nach rechts scrollt. Wenn ich drei Eigenschaften für eine Funktion benötige, stehen die Chancen gut, dass ich das Ganze zu einer Hashtabelle mit Splatting umschreibe.

### <a name="splatting-for-optional-parameters"></a>Splatting für optionale Parameter

Eine der häufigsten Gelegenheiten, bei denen ich Splatting verwende, ist die Verarbeitung von optionalen Parametern, die aus anderen Stellen meines Skripts stammen. Angenommen, ich habe eine Funktion, die einen `Get-CIMInstance`-Aufruf mit einem optionalen `$Credential`-Argument umschließt.

```powershell
$CIMParams = @{
    ClassName = 'Win32_Bios'
    ComputerName = $ComputerName
}

if($Credential)
{
    $CIMParams.Credential = $Credential
}

Get-CIMInstance @CIMParams
```

Als Erstes erstelle ich meine Hashtabelle mit allgemeinen Parametern. Dann füge ich `$Credential` hinzu, sofern vorhanden.
Da ich hier Splatting verwende, benötige ich den Aufruf von `Get-CIMInstance` nur einmal in meinem Code. Dieses Entwurfsmuster ist sehr übersichtlich und kann problemlos eine Vielzahl optionaler Parameter verarbeiten.

Um fair zu sein: Sie können Ihre Befehle so schreiben, dass `$null`-Werte für Parameter zulässig sind. Sie haben nur nicht immer Kontrolle über die anderen Befehle, die Sie aufrufen.

### <a name="multiple-splats"></a>Mehrere Splats

Sie können per Splatting mehrere Hashtabellen im selben Cmdlet übergeben. Sehen wir uns das ursprüngliche Splatting-Beispiel noch einmal an:

```powershell
$Common = @{
    SubnetMask  = '255.255.255.0'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}

$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    Description = 'Network for testlab A'
}

Add-DhcpServerv4Scope @DHCPScope @Common
```

Ich verwende diese Methode, wenn ich einen gemeinsamen Satz Parameter habe, die ich an sehr viele Befehle übergebe.

### <a name="splatting-for-clean-code"></a>Splatting für einen sauberen Code

Am Splatting eines einzelnen Parameters ist nichts auszusetzen, wenn Ihr Code dadurch sauberer wird.

```powershell
$log = @{Path = '.\logfile.log'}
Add-Content "logging this command" @log
```

### <a name="splatting-executables"></a>Splatting bei ausführbaren Dateien

Splatting funktioniert auch bei einigen ausführbaren Dateien, die eine `/param:value`-Syntax verwenden. `Robocopy.exe` beispielsweise weist einige Parameter wie die folgenden auf.

```powershell
$robo = @{R=1;W=1;MT=8}
robocopy source destination @robo
```

Ich weiß nicht, ob dies sehr nützlich ist, aber ich fand es interessant.

## <a name="adding-hashtables"></a>Hinzufügen von Hashtabellen

Hashtabellen unterstützen den Additionsoperator zum Kombinieren zweier Hashtabellen.

```powershell
$person += @{Zip = '78701'}
```

Das funktioniert aber nur, wenn die beiden Hashtabellen keinen gemeinsamen Schlüssel verwenden.

## <a name="nested-hashtables"></a>Geschachtelte Hashtabellen

Wir können Hashtabellen als Werte innerhalb einer Hashtabelle verwenden.

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
$person.location = @{}
$person.location.city = 'Austin'
$person.location.state = 'TX'
```

Ich habe mit einer einfachen Hashtabelle mit zwei Schlüsseln angefangen. Ich habe einen Schlüssel namens `location` mit einer leeren Hashtabelle hinzugefügt. Dann habe ich die letzten beiden Elemente zu dieser `location`-Hashtabelle hinzugefügt. Das Ganze geht auch inline.

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
    location = @{
        city  = 'Austin'
        state = 'TX'
    }
}
```

Damit wird dieselbe Hashtabelle erstellt, die Sie oben bereits gesehen haben, und auf die Eigenschaften wird auf dieselbe Weise zugegriffen.

```powershell
$person.location.city
Austin
```

Es gibt viele Ansätze für die Struktur Ihrer Objekte. Hier ein zweiter Blickwinkel auf eine geschachtelte Hashtabelle.

```powershell
$people = @{
    Kevin = @{
        age  = 36
        city = 'Austin'
    }
    Alex = @{
        age  = 9
        city = 'Austin'
    }
}
```

Hier vermischen sich die Konzepte der Verwendung von Hashtabellen als Auflistung von Objekten und als Auflistung von Eigenschaften. Auf die Werte kann immer noch ganz einfach zugegriffen werden, selbst dann, wenn sie auf eine von Ihnen bevorzugte Weise geschachtelt wurden.

```powershell
PS> $people.kevin.age
36
PS> $people.kevin['city']
Austin
PS> $people['Alex'].age
9
PS> $people['Alex']['City']
Austin
```

Ich verwende gerne die dot-Eigenschaft, wenn ich die Hashtabelle als Eigenschaft behandle. Das sind im Allgemeinen Dinge, die ich statisch in meinem Code definiert habe und auswendig weiß. Wenn ich die Liste durchlaufen oder programmgesteuert auf die Schlüssel zugreifen muss, verwende ich eckige Klammern, um den Schlüsselnamen anzugeben.

```powershell
foreach($name in $people.keys)
{
    $person = $people[$name]
    '{0}, age {1}, is in {2}' -f $name, $person.age, $person.city
}
```

Die Möglichkeit, Hashtabellen zu schachteln, bietet viel Flexibilität und jede Menge Optionen.

### <a name="looking-at-nested-hashtables"></a>Betrachten von geschachtelten Hashtabellen

Wenn Sie geschachtelte Hashtabellen verwenden, benötigen Sie eine einfache Möglichkeit, diese an der Konsole zu betrachten. Mit dieser letzten Hashtabelle beispielsweise erhalte ich folgende Ausgabe – und diese ist nicht besonders tief geschachtelt:

```powershell
PS> $people
Name                           Value
----                           -----
Kevin                          {age, city}
Alex                           {age, city}
```

Mein Lieblingsbefehl für die Betrachtung ist `ConvertTo-JSON`, weil dieser Befehl sehr sauber ist und ich JSON häufig auch für andere Dinge verwende.

```powershell
PS> $people | ConvertTo-Json
{
    "Kevin":  {
                "age":  36,
                "city":  "Austin"
            },
    "Alex":  {
                "age":  9,
                "city":  "Austin"
            }
}
```

Auch wenn Sie mit JSON nicht vertraut sind, sollten Sie erkennen können, wonach Sie suchen. Für solche strukturierten Daten gibt es auch den Befehl `Format-Custom`, aber mir gefällt die JSON-Ansicht besser.

## <a name="creating-objects"></a>Erstellen von Objekten

Manchmal benötigen Sie einfach nur ein Objekt, und eine Hashtabelle zum Speichern von Eigenschaften ist dafür nicht besonders gut geeignet. Üblicherweise möchten Sie die Schlüssel als Spaltennamen anzeigen. Das lässt sich ganz leicht mit einem `pscustomobject` erreichen.

```powershell
$person = [pscustomobject]@{
    name = 'Kevin'
    age  = 36
}

$person

name  age
----  ---
Kevin  36
```

Auch wenn Sie das Objekt anfänglich nicht als `pscustomobject` erstellen, können Sie es bei Bedarf später umwandeln.

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}

[pscustomobject]$person

name  age
----  ---
Kevin  36
```

Ich habe bereits eine detaillierte Rezension zu [pscustomobject][] verfasst, die Sie sich im Anschluss ansehen sollten. Die Rezension baut auf den Informationen auf, die Sie hier erhalten.

## <a name="reading-and-writing-hashtables-to-file"></a>Lesen und Schreiben von Hashtabellen in einer Datei

### <a name="saving-to-csv"></a>Speichern in CSV

Die Schwierigkeit, eine Hashtabelle in einer CSV-Datei zu speichern, ist eins der Probleme, die ich weiter oben bereits erwähnte. Konvertieren Sie Ihre Hashtabelle in ein `pscustomobject`, und schon lässt sie sich ordnungsgemäß als CSV speichern. Es ist hilfreich, wenn Sie mit einem `pscustomobject` beginnen, sodass die Spaltenreihenfolge beibehalten wird. Sie können aber auch bei Bedarf ein vorhandenes Objekt in ein `pscustomobject` umwandeln.

```powershell
$person | ForEach-Object{ [pscustomobject]$_ } | Export-CSV -Path $path
```

Ich kann es nur noch einmal empfehlen: Sehen Sie sich meine Rezension zur Verwendung von [pscustomobject][] an.

### <a name="saving-a-nested-hashtable-to-file"></a>Speichern einer geschachtelten Hashtabelle in einer Datei

Wenn ich eine geschachtelte Hashtabelle in einer Datei speichern und dann wieder in den Code einlesen muss, verwende ich dafür JSON-Cmdlets.

```powershell
$people | ConvertTo-JSON | Set-Content -Path $path
$people = Get-Content -Path $path -Raw | ConvertFrom-JSON
```

Bei dieser Methode sind zwei wichtige Punkte zu beachten. Erstens: JSON wird auf mehreren Zeilen geschrieben, daher muss ich zum erneuten Einlesen in einer einzigen Zeichenfolge die `-Raw`-Option verwenden. Der zweite Punkt ist, dass das importierte Objekt keine `[hashtable]` mehr ist. Es ist jetzt ein `[pscustomobject]`, und das kann zu Problemen führen, wenn Sie nicht damit rechnen.

Achten Sie auf Hashtabellen mit vielen Schachtelungsebenen. Wenn Sie diese in JSON konvertieren, erhalten Sie möglicherweise nicht die erwarteten Ergebnisse.

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json

{
  "a": {
    "b": {
      "c": "System.Collections.Hashtable"
    }
  }
}
```

Verwenden Sie den **Depth**-Parameter, um sicherzustellen, dass alle geschachtelten Hashtabellen erweitert wurden.

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json -Depth 3

{
  "a": {
    "b": {
      "c": {
        "d": "e"
      }
    }
  }
}
```

Wenn Sie beim Import eine `[hashtable]` benötigen, müssen Sie die Befehle `Export-CliXml` und `Import-CliXml` verwenden.

### <a name="converting-json-to-hashtable"></a>Konvertieren von JSON in eine Hashtabelle

Wenn Sie JSON-Code in eine `[hashtable]` konvertieren müssen, kenne ich eine Möglichkeit mit dem [JavaScriptSerializer][] in .NET.

```powershell
[Reflection.Assembly]::LoadWithPartialName("System.Web.Script.Serialization")
$JSSerializer = [System.Web.Script.Serialization.JavaScriptSerializer]::new()
$JSSerializer.Deserialize($json,'Hashtable')
```

Ab PowerShell v6 verwendet die JSON-Unterstützung JSON.NET von NewtonSoft und die zugehörige Hashtabellenunterstützung.

```powershell
'{ "a": "b" }' | ConvertFrom-Json -AsHashtable

Name      Value
----      -----
a         b
```

In PowerShell 6.2 wurde der **Depth**-Parameter zu `ConvertFrom-Json` hinzugefügt. Der Standardwert für **Depth** ist 1024.

### <a name="reading-directly-from-a-file"></a>Direktes Lesen aus einer Datei

Wenn Sie über eine Datei verfügen, die eine Hashtabelle mit PowerShell-Syntax enthält, gibt es eine Möglichkeit, diese Tabelle direkt zu importieren.

```powershell
$content = Get-Content -Path $Path -Raw -ErrorAction Stop
$scriptBlock = [scriptblock]::Create( $content )
$scriptBlock.CheckRestrictedLanguage( $allowedCommands, $allowedVariables, $true )
$hashtable = ( & $scriptBlock )
```

Dieser Code importiert die Dateiinhalte in einen `scriptblock` und führt dann eine Überprüfung durch, um sicherzustellen, dass keine weiteren PowerShell-Befehle vorhanden sind. Erst dann erfolgt die Ausführung.

Übrigens: Wussten Sie, dass ein Modulmanifest (die PSD1-Datei) einfach eine Hashtabelle ist?

## <a name="keys-can-be-any-object"></a>Bei Schlüsseln kann es sich um jedes Objekt handeln

In den meisten Fällen sind Schlüssel einfach nur Zeichenfolgen. Daher können wir Anführungszeichen um so ziemlich jede Zeichenfolge setzen und diese damit zu einem Schlüssel machen.

```powershell
$person = @{
    'full name' = 'Kevin Marquette'
    '#' = 3978
}
$person['full name']
```

Sie können einige lustige Sachen anstellen, von denen Sie möglicherweise noch nichts wussten.

```powershell
$person.'full name'

$key = 'full name'
$person.$key
```

Aber nur weil Sie etwas machen können, heißt das noch lange nicht, dass es auch ratsam ist. Dieses letzte Beispiel riecht förmlich danach, dass ein Fehler auftritt, und kann von anderen Personen, die Ihren Code lesen, leicht missverstanden werden.

Aus technischer Sicht müssen Schlüssel keine Zeichenfolgen sein, sie sind aber leichter verständlich, wenn Sie nur Zeichenfolgen verwenden. Die Indizierung funktioniert aber nicht so gut mit komplexen Schlüsseln.

```powershell
$ht = @{ @(1,2,3) = "a" }
$ht

Name                           Value
----                           -----
{1, 2, 3}                      a
```

Auf einen Wert in der Hashtabelle kann nicht immer anhand des zugehörigen Schlüssels zugegriffen werden. Beispiel:

```powershell
$key = $ht.keys[0]
$ht.$key
$ht[$key]
a
```

Die Memberzugriffsnotation (`.`) gibt nichts zurück. Die Arrayindexnotation (`[]`) dagegen funktioniert.

## <a name="use-in-automatic-variables"></a>Verwenden in automatischen Variablen

### <a name="psboundparameters"></a>$PSBoundParameters

[$PSBoundParameters][] ist eine automatische Variable, die nur im Kontext einer Funktion existiert.
Sie enthält alle Parameter, mit denen die Funktion aufgerufen wurde. Die Variable ist nicht direkt eine Hashtabelle, dieser aber so ähnlich, dass Sie sie als eine solche behandeln können.

Das bedeutet, dass Sie auch Schlüssel entfernen und die Variable per Splatting an andere Funktionen übergeben können. Wenn Sie selbst Proxyfunktionen schreiben, sollten Sie sich diese Variable näher ansehen.

Weitere Informationen finden Sie unter [about_Automatic_Variables][].

### <a name="psboundparameters-gotcha"></a>PSBoundParameters

Ein wichtiger Aspekt, den Sie bei dieser Variable immer beachten sollten, ist die Tatsache, dass sie nur die Werte enthält, die als Parameter an sie übergeben werden. Wenn Sie auch über Parameter mit Standardwerten verfügen, diese aber vom Aufrufer nicht übergeben werden, enthält `$PSBoundParameters` diese Werte nicht. Dieser Aspekt wird häufig übersehen.

### <a name="psdefaultparametervalues"></a>$PSDefaultParameterValues

Mit dieser automatischen Variable können Sie jedem Cmdlet Standardwerte zuweisen, ohne das Cmdlet zu ändern.
Sehen Sie sich folgendes Beispiel an.

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "UTF8"
```

Dieses Beispiel fügt der Hashtabelle `$PSDefaultParameterValues` einen Eintrag hinzu, der `UTF8` als Standardwert für den Parameter `Out-File -Encoding` festlegt. Die Variable ist sitzungsspezifisch, daher sollten Sie sie in Ihrem `$profile` platzieren.

Ich verwende sie sehr häufig, um vorab Werte zuzuweisen, die ich dauernd eingebe.

```powershell
$PSDefaultParameterValues[ "Connect-VIServer:Server" ] = 'VCENTER01.contoso.local'
```

Die Variable akzeptiert auch Platzhalter, Sie können also Werte per Massenvorgang festlegen. Hier einige Anwendungsbeispiele:

```powershell
$PSDefaultParameterValues[ "Get-*:Verbose" ] = $true
$PSDefaultParameterValues[ "*:Credential" ] = Get-Credential
```

Eine detailliertere Beschreibung finden Sie in diesem großartigen Artikel zu [Automatische Standardwerte][] von [Michael Sorens][].

## <a name="regex-matches"></a>$Matches für reguläre Ausdrücke

Wenn Sie den Operator `-match` verwenden, wird eine automatische Variable namens `$matches` mit den Ergebnissen der Übereinstimmung erstellt. Wenn Ihr regulärer Ausdruck Teilausdrücke enthält, werden diese ebenfalls aufgelistet.

```powershell
$message = 'My SSN is 123-45-6789.'

$message -match 'My SSN is (.+)\.'
$Matches[0]
$Matches[1]
```

### <a name="named-matches"></a>Benannte Übereinstimmungen

Das ist eins meiner Lieblingsfeatures, das leider nicht sehr bekannt ist. Wenn Sie eine benannte Übereinstimmung für einen regulären Ausdruck verwenden, können Sie anhand des Namens auf die Übereinstimmung zugreifen.

```powershell
$message = 'My Name is Kevin and my SSN is 123-45-6789.'

if($message -match 'My Name is (?<Name>.+) and my SSN is (?<SSN>.+)\.')
{
    $Matches.Name
    $Matches.SSN
}
```

Im Beispiel oben ist `(?<Name>.*)` ein benannter Teilausdruck. Dieser Wert wird dann in der Eigenschaft `$Matches.Name` platziert.

## <a name="group-object--ashashtable"></a>Group-Object -AsHashtable

Ein wenig bekanntes Feature von `Group-Object` ist die Tatsache, dass damit einige Datasets in eine Hashtabelle umgewandelt werden können.

```powershell
Import-CSV $Path | Group-Object -AsHashtable -Property email
```

Jede Zeile wird in eine Hashtabelle eingefügt, und für den Zugriff wird die angegebene Eigenschaft als Schlüssel verwendet.

## <a name="copying-hashtables"></a>Kopieren von Hashtabellen

Ein wichtiger Aspekt, der Ihnen bewusst sein muss: Hashtabellen sind Objekte. Und jede Variable ist nur ein Verweis auf ein Objekt. Das bedeutet, dass es mehr Arbeit ist, eine gültige Kopie einer Hashtabelle zu erstellen.

### <a name="assigning-reference-types"></a>Zuweisen von Verweistypen

Wenn Sie über eine Hashtabelle verfügen und diese einer zweiten Variable zuweisen, verweisen beide Variablen auf dieselbe Hashtabelle.

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [copy]
```

Dieses Beispiel verdeutlicht, dass es sich um dieselbe Hashtabelle handelt, denn eine Änderung der Werte in der einen Tabelle ändert auch die Werte in der anderen. Dies gilt auch, wenn Sie Hashtabellen an andere Funktionen übergeben. Wenn diese Funktionen Änderungen an dieser Hashtabelle vornehmen, wird die ursprüngliche Tabelle ebenfalls geändert.

### <a name="shallow-copies-single-level"></a>Flache Kopien mit einer Ebene

Bei einer einfachen Hashtabelle wie im obigen Beispiel können wir `.Clone()` verwenden, um eine flache Kopie zu erstellen.

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig.Clone()
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [orig]
```

So können wir einige grundlegende Änderungen an der einen Tabelle vornehmen, die sich nicht auf die andere auswirken.

### <a name="shallow-copies-nested"></a>Flache Kopien, geschachtelt

Diese Kopien werden als „flach“ bezeichnet, weil nur die grundlegenden Eigenschaften kopiert werden. Wenn eine dieser Eigenschaften ein Verweistyp ist (z. B. eine andere Hashtabelle), zeigen diese geschachtelten Objekte weiterhin aufeinander.

```powershell
PS> $orig = @{
        person=@{
            name='orig'
        }
    }
PS> $copy = $orig.Clone()
PS> $copy.person.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.person.name
PS> 'Orig: [{0}]' -f $orig.person.name

Copy: [copy]
Orig: [copy]
```

Sie sehen also: Obwohl ich die Hashtabelle geklont habe, wurde der Verweis auf `person` nicht geklont. Wir müssen eine tiefe Kopie erstellen, um tatsächlich eine zweite Hashtabelle zu erhalten, die nicht mit der ersten verknüpft ist.

### <a name="deep-copies"></a>Tiefe Kopien

Während ich diesen Artikel schreibe, ist mir keine clevere Möglichkeit bekannt, einfach eine tiefe Kopie einer Hashtabelle zu erstellen (und diese als Hashtabelle beizubehalten). Wahrscheinlich muss so etwas noch geschrieben werden.
Hier sehen Sie eine schnelle Methode.

```powershell
function Get-DeepClone
{
    [CmdletBinding()]
    param(
        $InputObject
    )
    process
    {
        if($InputObject -is [hashtable]) {
            $clone = @{}
            foreach($key in $InputObject.keys)
            {
                $clone[$key] = Get-DeepClone $InputObject[$key]
            }
            return $clone
        } else {
            return $InputObject
        }
    }
}
```

Dieses Beispiel verarbeitet keine anderen Verweistypen oder Arrays, aber es ist schon mal ein guter Anfang.

## <a name="anything-else"></a>Noch etwas?

Ich habe hier in kurzer Zeit sehr viele Aspekte vorgestellt. Ich hoffe, dass Sie hier etwas Neues erfahren haben oder einige Aspekte besser verstehen, wenn Sie diesen Artikel erneut lesen. Da ich das komplette Spektrum dieses Features abgedeckt habe, gibt es sicherlich einige Aspekte, die Sie zurzeit noch nicht betreffen. Das ist mir völlig klar, und ich habe damit gerechnet – je nachdem, wie viel und häufig Sie mit PowerShell arbeiten.

<!-- link references -->
[Originalversion]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Hashtabellen]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Wenn Leistung wichtig ist, probier es aus]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best%20Practices/Performance.md
[Splatting]: /powershell/module/microsoft.powershell.core/about/about_splatting
[pscustomobject]: everything-about-pscustomobject.md
[JavaScriptSerializer]: /dotnet/api/system.web.script.serialization.javascriptserializer?view=netframework-4.8
[PSBoundParameters]: https://tommymaynard.com/the-psboundparameters-automatic-variable-2016/
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[Automatische Standardwerte]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Michael Sorens]: http://cleancode.sourceforge.net/wwwdoc/about.html
