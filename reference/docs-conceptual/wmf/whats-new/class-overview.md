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
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="c2823-103">Erstellen benutzerdefinierter Typen mithilfe von PowerShell-Klassen</span><span class="sxs-lookup"><span data-stu-id="c2823-103">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="c2823-104">PowerShell 5.0 hat die Möglichkeit zum Definieren von Klassen und anderen benutzerdefinierten Typen mithilfe formaler Syntax und Semantik hinzugefügt, die mit anderen objektorientierten Programmiersprachen vergleichbar sind.</span><span class="sxs-lookup"><span data-stu-id="c2823-104">PowerShell 5.0 added the ability to define classes and other user-defined types using formal syntax and semantics like other object-oriented programming languages.</span></span> <span data-ttu-id="c2823-105">Ziel ist es, Entwickler und IT-Experten zu ermöglichen, PowerShell für eine größere Anzahl von Anwendungsfällen zu nutzen, die Entwicklung von PowerShell-Elementen (z. B. DSC-Ressourcen) zu vereinfachen und die Abdeckung weiterer Verwaltungsschnittstellen zu beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="c2823-105">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="c2823-106">In dieser Version unterstützte Szenarien</span><span class="sxs-lookup"><span data-stu-id="c2823-106">Supported scenarios in this release</span></span>

- <span data-ttu-id="c2823-107">Definieren von DSC-Ressourcen und ihren zugehörigen Typen mithilfe der PowerShell-Sprache</span><span class="sxs-lookup"><span data-stu-id="c2823-107">Define DSC resources and their associated types by using the PowerShell language</span></span>
- <span data-ttu-id="c2823-108">Definieren benutzerdefinierter Typen in PowerShell mithilfe vertrauter objektorientierter Programmierkonstrukte, z. B. Klassen, Eigenschaften, Methoden usw.</span><span class="sxs-lookup"><span data-stu-id="c2823-108">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
- <span data-ttu-id="c2823-109">Unterstützung der Vererbung von Klassen in PowerShell und Basisklassen für DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="c2823-109">Inheritance support with class in PowerShell and class base DSC resource</span></span>
- <span data-ttu-id="c2823-110">Debuggen von Typen mithilfe der PowerShell-Sprache</span><span class="sxs-lookup"><span data-stu-id="c2823-110">Debug types by using the PowerShell language</span></span>
- <span data-ttu-id="c2823-111">Generieren und Behandeln von Ausnahmen mithilfe formaler Mechanismen auf der richtigen Ebene</span><span class="sxs-lookup"><span data-stu-id="c2823-111">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>

## <a name="declare-base-class"></a><span data-ttu-id="c2823-112">Deklarieren der Basisklasse</span><span class="sxs-lookup"><span data-stu-id="c2823-112">Declare Base Class</span></span>

<span data-ttu-id="c2823-113">Sie können eine PowerShell-Klasse als Basistyp für eine andere PowerShell-Klasse deklarieren.</span><span class="sxs-lookup"><span data-stu-id="c2823-113">You can declare a PowerShell class as a base type for another PowerShell class.</span></span>

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

<span data-ttu-id="c2823-114">Sie können auch vorhandene .NET Framework-Typen als Basisklassen verwenden:</span><span class="sxs-lookup"><span data-stu-id="c2823-114">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

### <a name="call-base-class-constructor"></a><span data-ttu-id="c2823-115">Aufrufen des Basisklassenkonstruktors</span><span class="sxs-lookup"><span data-stu-id="c2823-115">Call Base Class Constructor</span></span>

<span data-ttu-id="c2823-116">Um einen Basisklassenkonstruktor aus einer Unterklasse aufzurufen, verwenden Sie das Schlüsselwort **base**:</span><span class="sxs-lookup"><span data-stu-id="c2823-116">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

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

<span data-ttu-id="c2823-117">Wenn eine Basisklasse einen Standardkonstruktor (ohne Parameter) hat, können Sie einen expliziten Konstruktoraufruf weglassen:</span><span class="sxs-lookup"><span data-stu-id="c2823-117">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-method"></a><span data-ttu-id="c2823-118">Aufrufen der Basisklassenmethode</span><span class="sxs-lookup"><span data-stu-id="c2823-118">Call Base Class Method</span></span>

<span data-ttu-id="c2823-119">Sie können vorhandene Methoden in Unterklassen überschreiben.</span><span class="sxs-lookup"><span data-stu-id="c2823-119">You can override existing methods in subclasses.</span></span> <span data-ttu-id="c2823-120">Deklarieren Sie dazu Methoden mit demselben Namen und derselben Signatur:</span><span class="sxs-lookup"><span data-stu-id="c2823-120">To do this, declare methods by using the same name and signature:</span></span>

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

<span data-ttu-id="c2823-121">Zum Aufrufen von Basisklassenmethoden aus überschriebenen Implementierungen der Basisklasse führen Sie beim Aufrufen eine Umwandlung in die Basisklasse (`[baseClass]$this`) durch.</span><span class="sxs-lookup"><span data-stu-id="c2823-121">To call base class methods from overridden implementations, cast to the base class (`[baseClass]$this`) on invocation:</span></span>

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

<span data-ttu-id="c2823-122">Alle PowerShell-Methoden sind virtuell.</span><span class="sxs-lookup"><span data-stu-id="c2823-122">All PowerShell methods are virtual.</span></span> <span data-ttu-id="c2823-123">Sie können nicht virtuelle .NET-Methoden in einer Unterklasse ausblenden, indem Sie dieselbe Syntax wie zum Überschreiben verwenden und indem Sie Methoden mit demselben Namen und derselben Signatur deklarieren.</span><span class="sxs-lookup"><span data-stu-id="c2823-123">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override, by declaring methods with same name and signature.</span></span>

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

### <a name="declare-implemented-interface"></a><span data-ttu-id="c2823-124">Deklarieren der implementierten Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="c2823-124">Declare Implemented Interface</span></span>

<span data-ttu-id="c2823-125">Sie können implementierte Schnittstellen nach Basistypen oder unmittelbar nach einem Doppelpunkt (:) deklarieren, wenn kein Basistyp angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="c2823-125">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="c2823-126">Trennen Sie alle Typnamen durch Kommas.</span><span class="sxs-lookup"><span data-stu-id="c2823-126">Separate all type names by using commas.</span></span> <span data-ttu-id="c2823-127">Dies entspricht der C#-Syntax.</span><span class="sxs-lookup"><span data-stu-id="c2823-127">It's similar to C# syntax.</span></span>

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

## <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="c2823-128">Neue Sprachfeatures in PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c2823-128">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="c2823-129">PowerShell 5.0 führt die folgenden neuen Sprachelemente in PowerShell ein:</span><span class="sxs-lookup"><span data-stu-id="c2823-129">PowerShell 5.0 introduces the following new language elements in PowerShell:</span></span>

### <a name="class-keyword"></a><span data-ttu-id="c2823-130">Schlüsselwort „Class“</span><span class="sxs-lookup"><span data-stu-id="c2823-130">Class keyword</span></span>

<span data-ttu-id="c2823-131">Das Schlüsselwort `class` definiert eine neue Klasse.</span><span class="sxs-lookup"><span data-stu-id="c2823-131">The `class` keyword defines a new class.</span></span> <span data-ttu-id="c2823-132">Es handelt sich um einen echten .NET Framework-Typ.</span><span class="sxs-lookup"><span data-stu-id="c2823-132">This is a true .NET Framework type.</span></span> <span data-ttu-id="c2823-133">Klassenmember sind öffentlich, jedoch nur innerhalb des Geltungsbereichs des Moduls.</span><span class="sxs-lookup"><span data-stu-id="c2823-133">Class members are public, but only public within the module scope.</span></span> <span data-ttu-id="c2823-134">Sie können auf den Typnamen nicht mittels einer Zeichenfolge verweisen (`New-Object` funktioniert z. B. nicht). In dieser Version können Sie zudem keinen Literaltyp (z. B. `[MyClass]`) außerhalb der Skript- oder Moduldatei verwenden, in der die Klasse definiert ist.</span><span class="sxs-lookup"><span data-stu-id="c2823-134">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script or module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="c2823-135">Schlüsselwort „enum“ und Enumerationen</span><span class="sxs-lookup"><span data-stu-id="c2823-135">Enum keyword and enumerations</span></span>

<span data-ttu-id="c2823-136">Das Schlüsselwort `enum` wurde hinzugefügt, welches das Zeilenumbruchzeichen als Trennzeichen verwendet.</span><span class="sxs-lookup"><span data-stu-id="c2823-136">Support for the `enum` keyword has been added, which uses newline as the delimiter.</span></span> <span data-ttu-id="c2823-137">Zurzeit können Sie einen Enumerator nicht hinsichtlich sich selbst definieren.</span><span class="sxs-lookup"><span data-stu-id="c2823-137">Currently, you cannot define an enumerator in terms of itself.</span></span> <span data-ttu-id="c2823-138">Sie können aber, wie im folgenden Beispiel gezeigt, eine Enumeration hinsichtlich einer anderen Enumeration initialisieren.</span><span class="sxs-lookup"><span data-stu-id="c2823-138">However, you can initialize an enum in terms of another enum, as shown in the following example.</span></span> <span data-ttu-id="c2823-139">Darüber hinaus kann der Basistyp nicht angegeben werden. Er ist stets `[int]`.</span><span class="sxs-lookup"><span data-stu-id="c2823-139">Also, the base type cannot be specified; it is always `[int]`.</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="c2823-140">Ein Enumeratorwert muss eine Konstante zur Analysezeit sein.</span><span class="sxs-lookup"><span data-stu-id="c2823-140">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="c2823-141">Sie können ihn nicht auf das Ergebnis eines aufgerufenen Befehls festlegen.</span><span class="sxs-lookup"><span data-stu-id="c2823-141">You cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="c2823-142">Enumerationen unterstützen arithmetische Operationen, wie im folgenden Beispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c2823-142">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a><span data-ttu-id="c2823-143">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="c2823-143">Import-DscResource</span></span>

<span data-ttu-id="c2823-144">`Import-DscResource` ist jetzt ein tatsächlich dynamisches Schlüsselwort.</span><span class="sxs-lookup"><span data-stu-id="c2823-144">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="c2823-145">PowerShell analysiert das Stammmodul des angegebenen Moduls und sucht Klassen, die das **DscResource**-Attribut enthalten.</span><span class="sxs-lookup"><span data-stu-id="c2823-145">PowerShell parses the specified module's root module, searching for classes that contain the **DscResource** attribute.</span></span>

### <a name="implementingassembly"></a><span data-ttu-id="c2823-146">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="c2823-146">ImplementingAssembly</span></span>

<span data-ttu-id="c2823-147">Eine neue Feld **ImplementingAssembly** wurde zu **ModuleInfo** hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="c2823-147">A new field, **ImplementingAssembly**, has been added to **ModuleInfo**.</span></span> <span data-ttu-id="c2823-148">Es ist auf die dynamische Assembly, die für ein Skriptmodul erstellt wird, wenn das Skript Klassen definiert, oder die geladene Assembly für binäre Module festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c2823-148">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="c2823-149">Falls **ModuleType** = **Manifest**, wird es nicht festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c2823-149">It is not set when **ModuleType** is **Manifest**.</span></span>

<span data-ttu-id="c2823-150">Über eine Reflexion auf das Feld **ImplementingAssembly** werden Ressourcen in einem Modul ermittelt.</span><span class="sxs-lookup"><span data-stu-id="c2823-150">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="c2823-151">Dies bedeutet, dass Sie Ressourcen ermitteln können, die in PowerShell oder anderen verwalteten Sprachen geschrieben wurden.</span><span class="sxs-lookup"><span data-stu-id="c2823-151">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="c2823-152">Felder mit Initialisierern:</span><span class="sxs-lookup"><span data-stu-id="c2823-152">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="c2823-153">`Static` wird unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c2823-153">`Static` is supported.</span></span> <span data-ttu-id="c2823-154">Es funktioniert wie ein Attribut, ebenso wie die Typeinschränkungen.</span><span class="sxs-lookup"><span data-stu-id="c2823-154">It works like an attribute, as do the type constraints.</span></span> <span data-ttu-id="c2823-155">Es kann in beliebiger Reihenfolge angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="c2823-155">It can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="c2823-156">Ein Typ ist optional.</span><span class="sxs-lookup"><span data-stu-id="c2823-156">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="c2823-157">Alle Member sind öffentlich.</span><span class="sxs-lookup"><span data-stu-id="c2823-157">All members are public.</span></span>

### <a name="constructors-and-instantiation"></a><span data-ttu-id="c2823-158">Konstruktoren und Instanziierung</span><span class="sxs-lookup"><span data-stu-id="c2823-158">Constructors and instantiation</span></span>

<span data-ttu-id="c2823-159">PowerShell-Klassen können Konstruktoren besitzen.</span><span class="sxs-lookup"><span data-stu-id="c2823-159">PowerShell classes can have constructors.</span></span> <span data-ttu-id="c2823-160">Sie haben denselben Namen wie ihre Klasse.</span><span class="sxs-lookup"><span data-stu-id="c2823-160">They have the same name as their class.</span></span> <span data-ttu-id="c2823-161">Konstruktoren können überladen werden.</span><span class="sxs-lookup"><span data-stu-id="c2823-161">Constructors can be overloaded.</span></span> <span data-ttu-id="c2823-162">Statische Konstruktoren werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c2823-162">Static constructors are supported.</span></span> <span data-ttu-id="c2823-163">Eigenschaften mit Initialisierungsausdrücken werden vor dem Ausführen von Code in einem Konstruktor initialisiert.</span><span class="sxs-lookup"><span data-stu-id="c2823-163">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="c2823-164">Statische Eigenschaften werden vor dem Hauptteil eines statischen Konstruktors initialisiert. Instanzeigenschaften werden vor dem Hauptteil des nicht statischen Konstruktors initialisiert.</span><span class="sxs-lookup"><span data-stu-id="c2823-164">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="c2823-165">Derzeit gibt es keine Syntax zum Aufrufen eines Konstruktors aus einem anderen Konstruktor (wie die C\#-Syntax „: this()“).</span><span class="sxs-lookup"><span data-stu-id="c2823-165">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="c2823-166">Die Problemumgehung besteht darin, eine allgemeine `Init()`-Methode zu definieren.</span><span class="sxs-lookup"><span data-stu-id="c2823-166">The workaround is to define a common `Init()` method.</span></span>

#### <a name="creating-instances"></a><span data-ttu-id="c2823-167">Erstellen von Instanzen</span><span class="sxs-lookup"><span data-stu-id="c2823-167">Creating instances</span></span>

> [!NOTE]
> <span data-ttu-id="c2823-168">In PowerShell 5.0 funktioniert `New-Object` nicht mit Klassen, die in PowerShell definiert werden.</span><span class="sxs-lookup"><span data-stu-id="c2823-168">In PowerShell 5.0, `New-Object` does not work with classes defined in PowerShell.</span></span> <span data-ttu-id="c2823-169">Außerdem ist der Typname nur lexikalisch sichtbar, was bedeutet, dass er außerhalb des Moduls oder Skripts, das die Klasse definiert, nicht sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="c2823-169">Also, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="c2823-170">Funktionen können Instanzen einer in PowerShell definierten Klasse zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="c2823-170">Functions can return instances of a class defined in PowerShell.</span></span> <span data-ttu-id="c2823-171">Diese Instanzen funktionieren außerhalb des Moduls oder Skripts.</span><span class="sxs-lookup"><span data-stu-id="c2823-171">Those instances work outside of the module or script.</span></span>

1. <span data-ttu-id="c2823-172">Instanziieren mithilfe des Standardkonstruktors.</span><span class="sxs-lookup"><span data-stu-id="c2823-172">Instantiating by using the default constructor.</span></span>

   ```powershell
   $a = [MyClass]::new()
   ```

1. <span data-ttu-id="c2823-173">Aufruf eines Konstruktors mit einem Parameter</span><span class="sxs-lookup"><span data-stu-id="c2823-173">Calling a constructor with a parameter</span></span>

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. <span data-ttu-id="c2823-174">Übergeben eines Arrays an einen Konstruktor mit mehreren Parametern.</span><span class="sxs-lookup"><span data-stu-id="c2823-174">Passing an array to a constructor with multiple parameters.</span></span>

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

<span data-ttu-id="c2823-175">Die pseudostatische Methode `new()` funktioniert mit .NET-Typen, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="c2823-175">The pseudo-static method `new()` works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

#### <a name="discovering-constructors"></a><span data-ttu-id="c2823-176">Ermitteln von Konstruktoren</span><span class="sxs-lookup"><span data-stu-id="c2823-176">Discovering constructors</span></span>

<span data-ttu-id="c2823-177">Sie können jetzt Konstruktorüberladungen mit `Get-Member` oder wie in diesem Beispiel anzeigen:</span><span class="sxs-lookup"><span data-stu-id="c2823-177">You can now see constructor overloads with `Get-Member`, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

<span data-ttu-id="c2823-178">`Get-Member -Static` listet Konstruktoren auf, sodass Sie Überladungen wie andere Methoden anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="c2823-178">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="c2823-179">Die Leistung dieser Syntax ist auch erheblich schneller als `New-Object`.</span><span class="sxs-lookup"><span data-stu-id="c2823-179">The performance of this syntax is also considerably faster than `New-Object`.</span></span>

### <a name="methods"></a><span data-ttu-id="c2823-180">Methoden</span><span class="sxs-lookup"><span data-stu-id="c2823-180">Methods</span></span>

<span data-ttu-id="c2823-181">Eine PowerShell-Klassenmethode wird als **Skriptblock** mit nur einem „end“-Block implementiert.</span><span class="sxs-lookup"><span data-stu-id="c2823-181">A PowerShell class method is implemented as a **ScriptBlock** that has only an end block.</span></span> <span data-ttu-id="c2823-182">Alle Methoden sind öffentlich.</span><span class="sxs-lookup"><span data-stu-id="c2823-182">All methods are public.</span></span> <span data-ttu-id="c2823-183">Nachstehend sehen Sie ein Beispiel der Definition einer Methode namens **DoSomething**.</span><span class="sxs-lookup"><span data-stu-id="c2823-183">The following shows an example of defining a method named **DoSomething**.</span></span>

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

<span data-ttu-id="c2823-184">Methodenaufruf:</span><span class="sxs-lookup"><span data-stu-id="c2823-184">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="c2823-185">Überladene Methoden werden ebenfalls unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c2823-185">Overloaded methods are also supported.</span></span>

### <a name="properties"></a><span data-ttu-id="c2823-186">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="c2823-186">Properties</span></span>

<span data-ttu-id="c2823-187">Alle Eigenschaften sind öffentlich.</span><span class="sxs-lookup"><span data-stu-id="c2823-187">All properties are public.</span></span> <span data-ttu-id="c2823-188">Eigenschaften erfordern ein Zeilenumbruchzeichen oder Semikolon.</span><span class="sxs-lookup"><span data-stu-id="c2823-188">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="c2823-189">Wenn kein Objekttyp angegeben ist, ist der Eigenschaftentyp „object“.</span><span class="sxs-lookup"><span data-stu-id="c2823-189">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="c2823-190">Eigenschaften, die Validierungs- oder Argumenttransformationsattribute verwenden (z. B. `[ValidateSet("aaa")]`), funktionieren wie erwartet.</span><span class="sxs-lookup"><span data-stu-id="c2823-190">Properties that use validation or argument transformation attributes (like `[ValidateSet("aaa")]`) work as expected.</span></span>

### <a name="hidden"></a><span data-ttu-id="c2823-191">Hidden</span><span class="sxs-lookup"><span data-stu-id="c2823-191">Hidden</span></span>

<span data-ttu-id="c2823-192">Mit `Hidden` wurde ein neues Schlüsselwort hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="c2823-192">A new keyword, `Hidden`, has been added.</span></span> <span data-ttu-id="c2823-193">`Hidden` kann auf Eigenschaften und Methoden (einschließlich Konstruktoren) angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="c2823-193">`Hidden` can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="c2823-194">Ausgeblendete Member sind öffentlich, werden aber in der Ausgabe von `Get-Member` nicht angezeigt, es sei denn, der `-Force`-Parameter wird hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="c2823-194">Hidden members are public, but do not appear in the output of `Get-Member` unless the `-Force` parameter is added.</span></span> <span data-ttu-id="c2823-195">Ausgeblendete Member sind bei Verwenden der Befehlszeilenergänzung oder von IntelliSense nicht enthalten, es sei denn, die Ergänzung erfolgt in der Klasse, die das ausgeblendete Member definiert.</span><span class="sxs-lookup"><span data-stu-id="c2823-195">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="c2823-196">Das neue Attribut **System.Management.Automation.HiddenAttribute** wurde hinzugefügt, damit C\#-Code in PowerShell die gleiche Semantik haben kann.</span><span class="sxs-lookup"><span data-stu-id="c2823-196">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C\# code can have the same semantics within PowerShell.</span></span>

### <a name="return-types"></a><span data-ttu-id="c2823-197">Rückgabetypen</span><span class="sxs-lookup"><span data-stu-id="c2823-197">Return types</span></span>

<span data-ttu-id="c2823-198">Der Rückgabetyp ist ein Vertrag.</span><span class="sxs-lookup"><span data-stu-id="c2823-198">Return type is a contract.</span></span> <span data-ttu-id="c2823-199">Der Rückgabewert wird in den erwarteten Typ konvertiert.</span><span class="sxs-lookup"><span data-stu-id="c2823-199">The return value is converted to the expected type.</span></span> <span data-ttu-id="c2823-200">Falls kein Rückgabetyp angegeben wird, ist der Rückgabetyp **void**.</span><span class="sxs-lookup"><span data-stu-id="c2823-200">If no return type is specified, the return type is **void**.</span></span> <span data-ttu-id="c2823-201">Es gibt kein Streaming von Objekten.</span><span class="sxs-lookup"><span data-stu-id="c2823-201">There is no streaming of objects.</span></span> <span data-ttu-id="c2823-202">Objekte können nicht absichtlich oder versehentlich in die Pipeline geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="c2823-202">Objects cannot be written to the pipeline either intentionally or by accident.</span></span>

### <a name="attributes"></a><span data-ttu-id="c2823-203">Attributes</span><span class="sxs-lookup"><span data-stu-id="c2823-203">Attributes</span></span>

<span data-ttu-id="c2823-204">Die beiden neuen Attribute **DscResource** und **DscProperty** wurden hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="c2823-204">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

### <a name="lexical-scoping-of-variables"></a><span data-ttu-id="c2823-205">Lexikalische Eingrenzung von Variablen</span><span class="sxs-lookup"><span data-stu-id="c2823-205">Lexical scoping of variables</span></span>

<span data-ttu-id="c2823-206">Das folgende Beispiel zeigt, wie die lexikalische Eingrenzung in dieser Version funktioniert.</span><span class="sxs-lookup"><span data-stu-id="c2823-206">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="c2823-207">End-to-End-Beispiel</span><span class="sxs-lookup"><span data-stu-id="c2823-207">End-to-End Example</span></span>

<span data-ttu-id="c2823-208">Das folgende Beispiel erstellt einige benutzerdefinierte Klassen, um eine HTML-Sprache des Typs DSL (Dynamic Style Sheet Language) zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="c2823-208">The following example creates some custom classes to implement an HTML dynamic style sheet language (DSL).</span></span> <span data-ttu-id="c2823-209">Dann werden im Beispiel Hilfsfunktionen hinzugefügt, um spezifische Elementtypen als Teil der Elementklasse zu erstellen, wie z. B. Überschriftsformate und Tabellen, damit Typen nicht außerhalb des Geltungsbereichs eines Moduls verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="c2823-209">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
