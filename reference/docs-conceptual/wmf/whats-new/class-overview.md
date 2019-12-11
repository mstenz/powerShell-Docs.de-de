---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Erstellen benutzerdefinierter Typen mithilfe von PowerShell-Klassen
ms.openlocfilehash: c2c50fb65ce4931fcf6ae529b4146df391c831c4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71147840"
---
# <a name="creating-custom-types-using-powershell-classes"></a>Erstellen benutzerdefinierter Typen mithilfe von PowerShell-Klassen

PowerShell 5.0 hat die Möglichkeit zum Definieren von Klassen und anderen benutzerdefinierten Typen mithilfe formaler Syntax und Semantik hinzugefügt, die mit anderen objektorientierten Programmiersprachen vergleichbar sind. Ziel ist es, Entwickler und IT-Experten zu ermöglichen, PowerShell für eine größere Anzahl von Anwendungsfällen zu nutzen, die Entwicklung von PowerShell-Elementen (z. B. DSC-Ressourcen) zu vereinfachen und die Abdeckung weiterer Verwaltungsschnittstellen zu beschleunigen.

## <a name="supported-scenarios-in-this-release"></a>In dieser Version unterstützte Szenarien

- Definieren von DSC-Ressourcen und ihren zugehörigen Typen mithilfe der PowerShell-Sprache
- Definieren benutzerdefinierter Typen in PowerShell mithilfe vertrauter objektorientierter Programmierkonstrukte, z. B. Klassen, Eigenschaften, Methoden usw.
- Unterstützung der Vererbung von Klassen in PowerShell und Basisklassen für DSC-Ressourcen
- Debuggen von Typen mithilfe der PowerShell-Sprache
- Generieren und Behandeln von Ausnahmen mithilfe formaler Mechanismen auf der richtigen Ebene

## <a name="declare-base-class"></a>Deklarieren der Basisklasse

Sie können eine PowerShell-Klasse als Basistyp für eine andere PowerShell-Klasse deklarieren.

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

Sie können auch vorhandene .NET Framework-Typen als Basisklassen verwenden:

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

### <a name="call-base-class-constructor"></a>Aufrufen des Basisklassenkonstruktors

Um einen Basisklassenkonstruktor aus einer Unterklasse aufzurufen, verwenden Sie das Schlüsselwort **base**:

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

Wenn eine Basisklasse einen Standardkonstruktor (ohne Parameter) hat, können Sie einen expliziten Konstruktoraufruf weglassen:

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-method"></a>Aufrufen der Basisklassenmethode

Sie können vorhandene Methoden in Unterklassen überschreiben. Deklarieren Sie dazu Methoden mit demselben Namen und derselben Signatur:

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

Zum Aufrufen von Basisklassenmethoden aus überschriebenen Implementierungen der Basisklasse führen Sie beim Aufrufen eine Umwandlung in die Basisklasse (`[baseClass]$this`) durch.

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

Alle PowerShell-Methoden sind virtuell. Sie können nicht virtuelle .NET-Methoden in einer Unterklasse ausblenden, indem Sie dieselbe Syntax wie zum Überschreiben verwenden und indem Sie Methoden mit demselben Namen und derselben Signatur deklarieren.

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

### <a name="declare-implemented-interface"></a>Deklarieren der implementierten Schnittstelle

Sie können implementierte Schnittstellen nach Basistypen oder unmittelbar nach einem Doppelpunkt (:) deklarieren, wenn kein Basistyp angegeben ist. Trennen Sie alle Typnamen durch Kommas. Dies entspricht der C#-Syntax.

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

## <a name="new-language-features-in-powershell-50"></a>Neue Sprachfeatures in PowerShell 5.0

PowerShell 5.0 führt die folgenden neuen Sprachelemente in PowerShell ein:

### <a name="class-keyword"></a>Schlüsselwort „Class“

Das Schlüsselwort `class` definiert eine neue Klasse. Es handelt sich um einen echten .NET Framework-Typ. Klassenmember sind öffentlich, jedoch nur innerhalb des Geltungsbereichs des Moduls. Sie können auf den Typnamen nicht mittels einer Zeichenfolge verweisen (`New-Object` funktioniert z. B. nicht). In dieser Version können Sie zudem keinen Literaltyp (z. B. `[MyClass]`) außerhalb der Skript- oder Moduldatei verwenden, in der die Klasse definiert ist.

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a>Schlüsselwort „enum“ und Enumerationen

Das Schlüsselwort `enum` wurde hinzugefügt, welches das Zeilenumbruchzeichen als Trennzeichen verwendet. Zurzeit können Sie einen Enumerator nicht hinsichtlich sich selbst definieren. Sie können aber, wie im folgenden Beispiel gezeigt, eine Enumeration hinsichtlich einer anderen Enumeration initialisieren. Darüber hinaus kann der Basistyp nicht angegeben werden. Er ist stets `[int]`.

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Ein Enumeratorwert muss eine Konstante zur Analysezeit sein. Sie können ihn nicht auf das Ergebnis eines aufgerufenen Befehls festlegen.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Enumerationen unterstützen arithmetische Operationen, wie im folgenden Beispiel dargestellt.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a>Import-DscResource

`Import-DscResource` ist jetzt ein tatsächlich dynamisches Schlüsselwort. PowerShell analysiert das Stammmodul des angegebenen Moduls und sucht Klassen, die das **DscResource**-Attribut enthalten.

### <a name="implementingassembly"></a>ImplementingAssembly

Eine neue Feld **ImplementingAssembly** wurde zu **ModuleInfo** hinzugefügt. Es ist auf die dynamische Assembly, die für ein Skriptmodul erstellt wird, wenn das Skript Klassen definiert, oder die geladene Assembly für binäre Module festgelegt. Falls **ModuleType** = **Manifest**, wird es nicht festgelegt.

Über eine Reflexion auf das Feld **ImplementingAssembly** werden Ressourcen in einem Modul ermittelt. Dies bedeutet, dass Sie Ressourcen ermitteln können, die in PowerShell oder anderen verwalteten Sprachen geschrieben wurden.

Felder mit Initialisierern:

```powershell
[int] $i = 5
```

`Static` wird unterstützt. Es funktioniert wie ein Attribut, ebenso wie die Typeinschränkungen. Es kann in beliebiger Reihenfolge angegeben werden.

```powershell
static [int] $count = 0
```

Ein Typ ist optional.

```powershell
$s = "hello"
```

Alle Member sind öffentlich.

### <a name="constructors-and-instantiation"></a>Konstruktoren und Instanziierung

PowerShell-Klassen können Konstruktoren besitzen. Sie haben denselben Namen wie ihre Klasse. Konstruktoren können überladen werden. Statische Konstruktoren werden unterstützt. Eigenschaften mit Initialisierungsausdrücken werden vor dem Ausführen von Code in einem Konstruktor initialisiert. Statische Eigenschaften werden vor dem Hauptteil eines statischen Konstruktors initialisiert. Instanzeigenschaften werden vor dem Hauptteil des nicht statischen Konstruktors initialisiert. Derzeit gibt es keine Syntax zum Aufrufen eines Konstruktors aus einem anderen Konstruktor (wie die C\#-Syntax „: this()“). Die Problemumgehung besteht darin, eine allgemeine `Init()`-Methode zu definieren.

#### <a name="creating-instances"></a>Erstellen von Instanzen

> [!NOTE]
> In PowerShell 5.0 funktioniert `New-Object` nicht mit Klassen, die in PowerShell definiert werden. Außerdem ist der Typname nur lexikalisch sichtbar, was bedeutet, dass er außerhalb des Moduls oder Skripts, das die Klasse definiert, nicht sichtbar ist. Funktionen können Instanzen einer in PowerShell definierten Klasse zurückgeben. Diese Instanzen funktionieren außerhalb des Moduls oder Skripts.

1. Instanziieren mithilfe des Standardkonstruktors.

   ```powershell
   $a = [MyClass]::new()
   ```

1. Aufruf eines Konstruktors mit einem Parameter

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. Übergeben eines Arrays an einen Konstruktor mit mehreren Parametern.

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

Die pseudostatische Methode `new()` funktioniert mit .NET-Typen, wie im folgenden Beispiel gezeigt.

```powershell
[hashtable]::new()
```

#### <a name="discovering-constructors"></a>Ermitteln von Konstruktoren

Sie können jetzt Konstruktorüberladungen mit `Get-Member` oder wie in diesem Beispiel anzeigen:

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

`Get-Member -Static` listet Konstruktoren auf, sodass Sie Überladungen wie andere Methoden anzeigen können. Die Leistung dieser Syntax ist auch erheblich schneller als `New-Object`.

### <a name="methods"></a>Methoden

Eine PowerShell-Klassenmethode wird als **Skriptblock** mit nur einem „end“-Block implementiert. Alle Methoden sind öffentlich. Nachstehend sehen Sie ein Beispiel der Definition einer Methode namens **DoSomething**.

```powershell
class MyClass
{
    DoSomething($x)
    {
        $this._doSomething($x) # method syntax
    }
    private _doSomething($a) {}
}
```

Methodenaufruf:

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

Überladene Methoden werden ebenfalls unterstützt.

### <a name="properties"></a>Eigenschaften

Alle Eigenschaften sind öffentlich. Eigenschaften erfordern ein Zeilenumbruchzeichen oder Semikolon. Wenn kein Objekttyp angegeben ist, ist der Eigenschaftentyp „object“.

Eigenschaften, die Validierungs- oder Argumenttransformationsattribute verwenden (z. B. `[ValidateSet("aaa")]`), funktionieren wie erwartet.

### <a name="hidden"></a>Hidden

Mit `Hidden` wurde ein neues Schlüsselwort hinzugefügt. `Hidden` kann auf Eigenschaften und Methoden (einschließlich Konstruktoren) angewendet werden.

Ausgeblendete Member sind öffentlich, werden aber in der Ausgabe von `Get-Member` nicht angezeigt, es sei denn, der `-Force`-Parameter wird hinzugefügt. Ausgeblendete Member sind bei Verwenden der Befehlszeilenergänzung oder von IntelliSense nicht enthalten, es sei denn, die Ergänzung erfolgt in der Klasse, die das ausgeblendete Member definiert.

Das neue Attribut **System.Management.Automation.HiddenAttribute** wurde hinzugefügt, damit C\#-Code in PowerShell die gleiche Semantik haben kann.

### <a name="return-types"></a>Rückgabetypen

Der Rückgabetyp ist ein Vertrag. Der Rückgabewert wird in den erwarteten Typ konvertiert. Falls kein Rückgabetyp angegeben wird, ist der Rückgabetyp **void**. Es gibt kein Streaming von Objekten. Objekte können nicht absichtlich oder versehentlich in die Pipeline geschrieben werden.

### <a name="attributes"></a>Attributes

Die beiden neuen Attribute **DscResource** und **DscProperty** wurden hinzugefügt.

### <a name="lexical-scoping-of-variables"></a>Lexikalische Eingrenzung von Variablen

Das folgende Beispiel zeigt, wie die lexikalische Eingrenzung in dieser Version funktioniert.

```powershell
$d = 42 # Script scope

function bar
{
    $d = 0 # Function scope
    [MyClass]::DoSomething()
}

class MyClass
{
    static [object] DoSomething()
    {
        return $d # error, not found dynamically
        return $script:d # no error
        $d = $script:d
        return $d # no error, found lexically
    }
}

$v = bar
$v -eq $d # true
```

## <a name="end-to-end-example"></a>End-to-End-Beispiel

Das folgende Beispiel erstellt einige benutzerdefinierte Klassen, um eine HTML-Sprache des Typs DSL (Dynamic Style Sheet Language) zu implementieren. Dann werden im Beispiel Hilfsfunktionen hinzugefügt, um spezifische Elementtypen als Teil der Elementklasse zu erstellen, wie z. B. Überschriftsformate und Tabellen, damit Typen nicht außerhalb des Geltungsbereichs eines Moduls verwendet werden können.

```powershell
# Classes that define the structure of the document
#
class Html
{
    [string] $docType
    [HtmlHead] $Head
    [Element[]] $Body

    [string] Render()
    {
        $text = "<html>`n<head>`n"
        $text += $this.Head
        $text += "`n</head>`n<body>`n"
        $text += $this.Body -join "`n" # Render all of the body elements
        $text += "</body>`n</html>"
        return $text
    }
    [string] ToString() { return $this.Render() }
}

class HtmlHead
{
    $Title
    $Base
    $Link
    $Style
    $Meta
    $Script
    [string] Render() { return "<title>$($this.Title)</title>" }
    [string] ToString() { return $this.Render() }
}

class Element
{
    [string] $Tag
    [string] $Text
    [hashtable] $Attributes
    [string] Render() {
        $attributesText= ""
        if ($this.Attributes)
        {
            foreach ($attr in $this.Attributes.Keys)
            {
                #BUGBUG - need to validate keys against attribute
                $attributesText += " $attr=`"$($this.Attributes[$attr])\`""
            }
        }
        return "<$($this.tag)${attributesText}>$($this.text)</$($this.tag)>`n"
    }
[string] ToString() { return $this.Render() }
}

#
# Helper functions for creating specific element types on top of the classes.
# These are required because types aren't visible outside of the module.
#

function H1 { [Element] @{ Tag = "H1" ; Text = $args.foreach{$_} -join " " }}
function H2 { [Element] @{ Tag = "H2" ; Text = $args.foreach{$_} -join " " }}
function H3 { [Element] @{ Tag = "H3" ; Text = $args.foreach{$_} -join " " }}
function P { [Element] @{ Tag = "P" ; Text = $args.foreach{$_} -join " " }}
function B { [Element] @{ Tag = "B" ; Text = $args.foreach{$_} -join " " }}
function I { [Element] @{ Tag = "I" ; Text = $args.foreach{$_} -join " " }}
function HREF
{
    param (
        $Name,
        $Link
    )
    return [Element] @{
        Tag = "A"
        Attributes = @{ HREF = $link }
        Text = $name
    }
}
function Table
{
    param (
    [Parameter(Mandatory)]
    [object[]]
        $Data,
    [Parameter()]
    [string[]]
        $Properties = "*",
    [Parameter()]
    [hashtable]
        $Attributes = @{ border=2; cellpadding=2; cellspacing=2 }
    )
$bodyText = ""
# Add the header tags
$bodyText += $Properties.foreach{TH $_}
# Add the rows
$bodyText += foreach ($row in $Data)
    {
        TR (-join $Properties.Foreach{ TD ($row.$_) } )
    }

    $table = [Element] @{
        Tag = "Table"
        Attributes = $Attributes
        Text = $bodyText
    }
$table
}
function TH { ([Element] @{ Tag = "TH" ; Text = $args.foreach{$_} -join " " }) }
function TR { ([Element] @{ Tag = "TR" ; Text = $args.foreach{$_} -join " " }) }
function TD { ([Element] @{ Tag = "TD" ; Text = $args.foreach{$_} -join " " }) }
function Style

{
    return [Element] @{
        Tag = "style"
        Text = "$args"
    }
}

# Takes a hash table, casts it to and HTML document
# and then returns the resulting type.
#
function Html ([HTML] $doc) { return $doc }
```
