---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a96a4a58dafa01fb43f5bdffb52ef833816148e7
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587294"
---
# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="3d85f-102">Neue Sprachfeatures in PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3d85f-102">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="3d85f-103">PowerShell 5.0 führt die folgenden neuen Sprachelemente in Windows PowerShell ein:</span><span class="sxs-lookup"><span data-stu-id="3d85f-103">PowerShell 5.0 introduces the following new language elements in Windows PowerShell:</span></span>

## <a name="class-keyword"></a><span data-ttu-id="3d85f-104">Schlüsselwort „Class“</span><span class="sxs-lookup"><span data-stu-id="3d85f-104">Class keyword</span></span>

<span data-ttu-id="3d85f-105">Das Schlüsselwort **class** definiert eine neue Klasse.</span><span class="sxs-lookup"><span data-stu-id="3d85f-105">The **class** keyword defines a new class.</span></span> <span data-ttu-id="3d85f-106">Es handelt sich um einen echten .NET Framework-Typ.</span><span class="sxs-lookup"><span data-stu-id="3d85f-106">This is a true .NET Framework type.</span></span>
<span data-ttu-id="3d85f-107">Klassenmember sind öffentlich, jedoch nur innerhalb des Geltungsbereichs des Moduls.</span><span class="sxs-lookup"><span data-stu-id="3d85f-107">Class members are public, but only public within the module scope.</span></span>
<span data-ttu-id="3d85f-108">Sie können auf den Typnamen nicht mittels einer Zeichenfolge verweisen (`New-Object` funktioniert z. B. nicht). In dieser Version können Sie zudem keinen Literaltyp (z. B. `[MyClass]`) außerhalb der Skript-/Moduldatei verwenden, in der die Klasse definiert ist.</span><span class="sxs-lookup"><span data-stu-id="3d85f-108">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script/module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="3d85f-109">Schlüsselwort „enum“ und Enumerationen</span><span class="sxs-lookup"><span data-stu-id="3d85f-109">Enum keyword and enumerations</span></span>

<span data-ttu-id="3d85f-110">Das Schlüsselwort **enum** wurde hinzugefügt, welches das Zeilenumbruchzeichen als Trennzeichen verwendet.</span><span class="sxs-lookup"><span data-stu-id="3d85f-110">Support for the **enum** keyword has been added, which uses newline as the delimiter.</span></span>
<span data-ttu-id="3d85f-111">Aktuelle Einschränkungen: Sie können einen Enumerator nicht hinsichtlich sich selbst definieren, aber Sie können, wie im folgenden Beispiel gezeigt, eine Enumeration hinsichtlich einer anderen Enumeration initialisieren.</span><span class="sxs-lookup"><span data-stu-id="3d85f-111">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize an enum in terms of another enum, as shown in the following example.</span></span>
<span data-ttu-id="3d85f-112">Darüber hinaus kann der Basistyp derzeit nicht angegeben werden. Er ist stets [int].</span><span class="sxs-lookup"><span data-stu-id="3d85f-112">Also, the base type cannot currently be specified; it is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="3d85f-113">Ein Enumeratorwert muss eine Konstante zur Analysezeit sein. Sie können ihn nicht auf das Ergebnis eines aufgerufenen Befehls festlegen.</span><span class="sxs-lookup"><span data-stu-id="3d85f-113">An enumerator value must be a parse time constant; you cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="3d85f-114">Enumerationen unterstützen arithmetische Operationen, wie im folgenden Beispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="3d85f-114">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a><span data-ttu-id="3d85f-115">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="3d85f-115">Import-DscResource</span></span>

<span data-ttu-id="3d85f-116">**Import-DscResource** ist jetzt ein tatsächlich dynamisches Schlüsselwort.</span><span class="sxs-lookup"><span data-stu-id="3d85f-116">**Import-DscResource** is now a true dynamic keyword.</span></span>
<span data-ttu-id="3d85f-117">PowerShell analysiert das Stammmodul des angegebenen Moduls und sucht Klassen, die das **DscResource**-Attribut enthalten.</span><span class="sxs-lookup"><span data-stu-id="3d85f-117">PowerShell parses the specified module’s root module, searching for classes that contain the **DscResource** attribute.</span></span>

## <a name="implementingassembly"></a><span data-ttu-id="3d85f-118">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="3d85f-118">ImplementingAssembly</span></span>

<span data-ttu-id="3d85f-119">Das neue Feld **ImplementingAssembly** wurde „ModuleInfo“ hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="3d85f-119">A new field, **ImplementingAssembly**, has been added to ModuleInfo.</span></span> <span data-ttu-id="3d85f-120">Es ist auf die dynamische Assembly, die für ein Skriptmodul erstellt wird, wenn das Skript Klassen definiert, oder die geladene Assembly für binäre Module festgelegt.</span><span class="sxs-lookup"><span data-stu-id="3d85f-120">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="3d85f-121">Falls „ModuleType = Manifest“, wird es nicht festgelegt.</span><span class="sxs-lookup"><span data-stu-id="3d85f-121">It is not set when ModuleType = Manifest.</span></span>

<span data-ttu-id="3d85f-122">Über eine Reflektion auf das Feld **ImplementingAssembly** werden Ressourcen in einem Modul ermittelt.</span><span class="sxs-lookup"><span data-stu-id="3d85f-122">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="3d85f-123">Dies bedeutet, dass Sie Ressourcen ermitteln können, die in PowerShell oder anderen verwalteten Sprachen geschrieben wurden.</span><span class="sxs-lookup"><span data-stu-id="3d85f-123">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="3d85f-124">Felder mit Initialisierern:</span><span class="sxs-lookup"><span data-stu-id="3d85f-124">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="3d85f-125">„Static“ wird unterstützt und funktioniert wie Typeinschränkungen wie ein Attribut, weshalb die Angabe in beliebiger Reihenfolge erfolgen kann.</span><span class="sxs-lookup"><span data-stu-id="3d85f-125">Static is supported; it works like an attribute, as do the type constraints, so it can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="3d85f-126">Ein Typ ist optional.</span><span class="sxs-lookup"><span data-stu-id="3d85f-126">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="3d85f-127">Alle Member sind öffentlich.</span><span class="sxs-lookup"><span data-stu-id="3d85f-127">All members are public.</span></span>

## <a name="constructors-and-instantiation"></a><span data-ttu-id="3d85f-128">Konstruktoren und Instanziierung</span><span class="sxs-lookup"><span data-stu-id="3d85f-128">Constructors and instantiation</span></span>

<span data-ttu-id="3d85f-129">Windows PowerShell-Klassen können Konstruktoren haben, die den gleichen Namen wie ihre Klasse haben.</span><span class="sxs-lookup"><span data-stu-id="3d85f-129">Windows PowerShell classes can have constructors; they have the same name as their class.</span></span> <span data-ttu-id="3d85f-130">Konstruktoren können überladen werden.</span><span class="sxs-lookup"><span data-stu-id="3d85f-130">Constructors can be overloaded.</span></span> <span data-ttu-id="3d85f-131">Statische Konstruktoren werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3d85f-131">Static constructors are supported.</span></span> <span data-ttu-id="3d85f-132">Eigenschaften mit Initialisierungsausdrücken werden vor dem Ausführen von Code in einem Konstruktor initialisiert.</span><span class="sxs-lookup"><span data-stu-id="3d85f-132">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="3d85f-133">Statische Eigenschaften werden vor dem Hauptteil eines statischen Konstruktors initialisiert. Instanzeigenschaften werden vor dem Hauptteil des nicht statischen Konstruktors initialisiert.</span><span class="sxs-lookup"><span data-stu-id="3d85f-133">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="3d85f-134">Derzeit gibt es keine Syntax zum Aufrufen eines Konstruktors aus einem anderen Konstruktor (wie die C\#-Syntax „: this()“).</span><span class="sxs-lookup"><span data-stu-id="3d85f-134">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="3d85f-135">Eine Behelfslösung ist das Definieren einer allgemeinen „Init“-Methode.</span><span class="sxs-lookup"><span data-stu-id="3d85f-135">The workaround is to define a common Init method.</span></span>

<span data-ttu-id="3d85f-136">Es folgen Methoden zum Instanziieren von Klassen in dieser Version.</span><span class="sxs-lookup"><span data-stu-id="3d85f-136">The following are ways of instantiating classes in this release.</span></span>

<span data-ttu-id="3d85f-137">Instanziieren mithilfe des Standardkonstruktors.</span><span class="sxs-lookup"><span data-stu-id="3d85f-137">Instantiating by using the default constructor.</span></span> <span data-ttu-id="3d85f-138">Beachten Sie, dass „New-Object“ in dieser Version nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="3d85f-138">Note that New-Object is not supported in this release.</span></span>

```powershell
$a = [MyClass]::new()
```

<span data-ttu-id="3d85f-139">Aufruf eines Konstruktors mit einem Parameter</span><span class="sxs-lookup"><span data-stu-id="3d85f-139">Calling a constructor with a parameter</span></span>

```powershell
$b = [MyClass]::new(42)
```

<span data-ttu-id="3d85f-140">Übergeben ein Arrays an einen Konstruktor mit mehreren Parametern</span><span class="sxs-lookup"><span data-stu-id="3d85f-140">Passing an array to a constructor with multiple parameters</span></span>
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

<span data-ttu-id="3d85f-141">In dieser Version funktioniert „New-Object“ nicht mit Klassen, die in Windows PowerShell definiert werden.</span><span class="sxs-lookup"><span data-stu-id="3d85f-141">In this release, New-Object does not work with classes defined in Windows PowerShell.</span></span> <span data-ttu-id="3d85f-142">Außerdem ist bei dieser Version der Typname nur lexikalisch sichtbar, was bedeutet, dass er außerhalb des Moduls oder Skripts, das die Klasse definiert, nicht sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="3d85f-142">Also for this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="3d85f-143">Funktionen können Instanzen einer Klasse zurückgeben, die in Windows PowerShell definiert wurden. Instanzen funktionieren auch außerhalb des Moduls oder Skripts.</span><span class="sxs-lookup"><span data-stu-id="3d85f-143">Functions can return instances of a class defined in Windows PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="3d85f-144">`Get-Member -Static` listet Konstruktoren auf, sodass Sie Überladungen wie andere Methoden anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="3d85f-144">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="3d85f-145">Die Leistung dieser Syntax ist auch erheblich schneller als „New-Object“.</span><span class="sxs-lookup"><span data-stu-id="3d85f-145">The performance of this syntax is also considerably faster than New-Object.</span></span>

<span data-ttu-id="3d85f-146">Die pseudostatische Methode **new** funktioniert mit .NET-Typen, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="3d85f-146">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

<span data-ttu-id="3d85f-147">Sie können jetzt Konstruktorüberladungen mit „Get-Member“ oder wie in diesem Beispiel anzeigen:</span><span class="sxs-lookup"><span data-stu-id="3d85f-147">You can now see constructor overloads with Get-Member, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a><span data-ttu-id="3d85f-148">Methoden</span><span class="sxs-lookup"><span data-stu-id="3d85f-148">Methods</span></span>

<span data-ttu-id="3d85f-149">Eine Windows PowerShell-Klassenmethode wird als Skriptblock mit nur einem „end“-Block implementiert.</span><span class="sxs-lookup"><span data-stu-id="3d85f-149">A Windows PowerShell class method is implemented as a ScriptBlock that has only an end block.</span></span> <span data-ttu-id="3d85f-150">Alle Methoden sind öffentlich.</span><span class="sxs-lookup"><span data-stu-id="3d85f-150">All methods are public.</span></span> <span data-ttu-id="3d85f-151">Nachstehend sehen Sie ein Beispiel der Definition einer Methode namens **DoSomething**.</span><span class="sxs-lookup"><span data-stu-id="3d85f-151">The following shows an example of defining a method named **DoSomething**.</span></span>

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

<span data-ttu-id="3d85f-152">Methodenaufruf:</span><span class="sxs-lookup"><span data-stu-id="3d85f-152">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="3d85f-153">Überladene Methoden, d. h. Methoden mit demselben Namen wie eine vorhandene Methode, aber mit unterschiedlichen angegebenen Werten, werden ebenfalls unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3d85f-153">Overloaded methods--that is, those that are named the same as an existing method, but differentiated by their specified values--are also supported.</span></span>

## <a name="properties"></a><span data-ttu-id="3d85f-154">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="3d85f-154">Properties</span></span>

<span data-ttu-id="3d85f-155">Alle Eigenschaften sind öffentlich.</span><span class="sxs-lookup"><span data-stu-id="3d85f-155">All properties are public.</span></span> <span data-ttu-id="3d85f-156">Eigenschaften erfordern ein Zeilenumbruchzeichen oder Semikolon.</span><span class="sxs-lookup"><span data-stu-id="3d85f-156">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="3d85f-157">Wenn kein Objekttyp angegeben ist, ist der Eigenschaftentyp „object“.</span><span class="sxs-lookup"><span data-stu-id="3d85f-157">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="3d85f-158">Eigenschaften, die Validierungs- oder Argumenttransformationsattribute verwenden (z. B. `[ValidateSet("aaa")]`), funktionieren wie erwartet.</span><span class="sxs-lookup"><span data-stu-id="3d85f-158">Properties that use validation attributes or argument transformation attributes (e.g. `[ValidateSet("aaa")]`) work as expected.</span></span>

## <a name="hidden"></a><span data-ttu-id="3d85f-159">Hidden</span><span class="sxs-lookup"><span data-stu-id="3d85f-159">Hidden</span></span>

<span data-ttu-id="3d85f-160">Mit **Hidden** wurde ein neues Schlüsselwort hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="3d85f-160">A new keyword, **Hidden**, has been added.</span></span> <span data-ttu-id="3d85f-161">**Hidden** kann auf Eigenschaften und Methoden (einschließlich Konstruktoren) angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="3d85f-161">**Hidden** can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="3d85f-162">Ausgeblendete Member sind öffentlich, werden aber in der Ausgabe von „Get-Member“ nicht angezeigt, es sei denn, der „-Force“-Parameter wird hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="3d85f-162">Hidden members are public, but do not appear in the output of Get-Member unless the -Force parameter is added.</span></span>

<span data-ttu-id="3d85f-163">Ausgeblendete Member sind bei Verwenden der Befehlszeilenergänzung oder von IntelliSense nicht enthalten, es sei denn, die Ergänzung erfolgt in der Klasse, die das ausgeblendete Member definiert.</span><span class="sxs-lookup"><span data-stu-id="3d85f-163">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="3d85f-164">Das neue Attribut **System.Management.Automation.HiddenAttribute** wurde hinzugefügt, damit C#-Code in Windows PowerShell die gleiche Semantik haben kann.</span><span class="sxs-lookup"><span data-stu-id="3d85f-164">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C# code can have the same semantics within Windows PowerShell.</span></span>

## <a name="return-types"></a><span data-ttu-id="3d85f-165">Rückgabetypen</span><span class="sxs-lookup"><span data-stu-id="3d85f-165">Return types</span></span>

<span data-ttu-id="3d85f-166">Der Rückgabetyp ist ein Vertrag. Der Rückgabewert wird in den erwarteten Typ konvertiert.</span><span class="sxs-lookup"><span data-stu-id="3d85f-166">Return type is a contract; the return value is converted to the expected type.</span></span> <span data-ttu-id="3d85f-167">Falls kein Rückgabetyp angegeben wird, ist der Rückgabetyp „void“.</span><span class="sxs-lookup"><span data-stu-id="3d85f-167">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="3d85f-168">Es gibt kein Streaming von Objekten. Objekte können nicht absichtlich oder versehentlich in die Pipeline geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="3d85f-168">There is no streaming of objects; objects cannot be written to the pipeline either intentionally or by accident.</span></span>

## <a name="attributes"></a><span data-ttu-id="3d85f-169">Attributes</span><span class="sxs-lookup"><span data-stu-id="3d85f-169">Attributes</span></span>

<span data-ttu-id="3d85f-170">Die beiden neuen Attribute **DscResource** und **DscProperty** wurden hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="3d85f-170">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

## <a name="lexical-scoping-of-variables"></a><span data-ttu-id="3d85f-171">Lexikalische Eingrenzung von Variablen</span><span class="sxs-lookup"><span data-stu-id="3d85f-171">Lexical scoping of variables</span></span>

<span data-ttu-id="3d85f-172">Das folgende Beispiel zeigt, wie die lexikalische Eingrenzung in dieser Version funktioniert.</span><span class="sxs-lookup"><span data-stu-id="3d85f-172">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="3d85f-173">End-to-End-Beispiel</span><span class="sxs-lookup"><span data-stu-id="3d85f-173">End-to-End Example</span></span>

<span data-ttu-id="3d85f-174">Das folgende Beispiel erstellt mehrere neue, benutzerdefinierte Klassen, um eine HTML-Sprache des Typs DSL (Dynamic Style Sheet Language) zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="3d85f-174">The following example creates several new, custom classes to implement an HTML dynamic style sheet language (DSL).</span></span>
<span data-ttu-id="3d85f-175">Dann werden im Beispiel Hilfsfunktionen hinzugefügt, um spezifische Elementtypen als Teil der Elementklasse zu erstellen, wie z. B. Überschriftsformate und Tabellen, damit Typen nicht außerhalb des Geltungsbereichs eines Moduls verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="3d85f-175">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
# These are required because types aren’t visible outside of the module.
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
