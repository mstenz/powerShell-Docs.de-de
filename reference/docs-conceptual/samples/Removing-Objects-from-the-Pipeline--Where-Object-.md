---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Entfernen von Objekten aus der Pipeline – Where-Object
ms.openlocfilehash: 370e7745341b70c0794352a690d5750d21f53ac2
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737184"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="c0eb0-103">Entfernen von Objekten aus der Pipeline (Where-Object)</span><span class="sxs-lookup"><span data-stu-id="c0eb0-103">Removing Objects from the Pipeline (Where-Object)</span></span>

<span data-ttu-id="c0eb0-104">In PowerShell geschieht es häufig, dass Sie mehr Objekte als gewünscht generieren und an eine Pipeline übergeben.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-104">In PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="c0eb0-105">Mithilfe der `Format-*`-Cmdlets können Sie die anzuzeigenden Eigenschaften bestimmter Objekte angeben, aber auf diese Weise ist es nicht möglich, ganze Objekte aus der Anzeige zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-105">You can specify the properties of particular objects to display by using the `Format-*` cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="c0eb0-106">Möglicherweise möchten Sie die Objekte vor dem Ende einer Pipeline filtern, um nur für eine Teilmenge der ursprünglich generierten Objekte bestimmte Aktionen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-106">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="c0eb0-107">PowerShell umfasst ein `Where-Object`-Cmdlet, mit dem Sie jedes Objekt in der Pipeline testen können, um es nur dann an die Pipeline zu übergeben, wenn es eine bestimmte Testbedingung erfüllt.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-107">PowerShell includes a `Where-Object` cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="c0eb0-108">Objekte, die den Test nicht bestehen, werden aus der Pipeline entfernt.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-108">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="c0eb0-109">Sie geben die Testbedingung als Wert des Parameters **FilterScript** an.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-109">You supply the test condition as the value of the **FilterScript** parameter.</span></span>

## <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="c0eb0-110">Ausführen einfacher Tests mit „Where-Object“</span><span class="sxs-lookup"><span data-stu-id="c0eb0-110">Performing Simple Tests with Where-Object</span></span>

<span data-ttu-id="c0eb0-111">Der Wert von **FilterScript** ist ein *Skriptblock* – d. h. mindestens ein in geschweiften Klammern eingeschlossener PowerShell-Befehl (`{}`) –, der als TRUE oder FALSE ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-111">The value of **FilterScript** is a *script block* - one or more PowerShell commands surrounded by braces (`{}`) - that evaluates to true or false.</span></span> <span data-ttu-id="c0eb0-112">Diese Skriptblöcke können sehr einfach sein, aber ihre Erstellung erfordert Kenntnisse eines anderen PowerShell-Konzepts: Vergleichsoperatoren.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-112">These script blocks can be very simple, but creating them requires knowing about another PowerShell concept, comparison operators.</span></span> <span data-ttu-id="c0eb0-113">Mit einem Vergleichsoperator werden die Elemente auf den beiden Seiten des Operators verglichen.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-113">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="c0eb0-114">Vergleichsoperatoren beginnen mit einem Minuszeichen (`-`), gefolgt von einem Namen.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-114">Comparison operators begin with a hyphen character (`-`) and are followed by a name.</span></span> <span data-ttu-id="c0eb0-115">Die grundlegenden Vergleichsoperatoren können für nahezu jede Art von Objekt verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-115">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="c0eb0-116">Die erweiterten Vergleichsoperatoren können möglicherweise nur mit Text oder Arrays verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-116">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="c0eb0-117">Bei PowerShell-Vergleichsoperatoren wird beim Arbeiten mit Text die Groß-/Kleinschreibung standardmäßig nicht beachtet.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-117">By default, when working with text, PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="c0eb0-118">Aus Analysegründen werden Symbole wie `<`, `>` und `=` nicht als Vergleichsoperatoren verwendet.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-118">Due to parsing considerations, symbols such as `<`,`>`, and `=` are not used as comparison operators.</span></span> <span data-ttu-id="c0eb0-119">Stattdessen bestehen Vergleichsoperatoren aus Buchstaben.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-119">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="c0eb0-120">In der folgenden Tabelle sind die grundlegenden Vergleichsoperatoren aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-120">The basic comparison operators are listed in the following table.</span></span>

| <span data-ttu-id="c0eb0-121">Vergleichsoperator</span><span class="sxs-lookup"><span data-stu-id="c0eb0-121">Comparison Operator</span></span> |                  <span data-ttu-id="c0eb0-122">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="c0eb0-122">Meaning</span></span>                   |    <span data-ttu-id="c0eb0-123">Beispiel (gibt „true“ zurück)</span><span class="sxs-lookup"><span data-stu-id="c0eb0-123">Example (returns true)</span></span>    |
| ------------------- | ------------------------------------------ | ---------------------------- |
| <span data-ttu-id="c0eb0-124">-eq</span><span class="sxs-lookup"><span data-stu-id="c0eb0-124">-eq</span></span>                 | <span data-ttu-id="c0eb0-125">Ist gleich</span><span class="sxs-lookup"><span data-stu-id="c0eb0-125">is equal to</span></span>                                | <span data-ttu-id="c0eb0-126">1 -eq 1</span><span class="sxs-lookup"><span data-stu-id="c0eb0-126">1 -eq 1</span></span>                      |
| <span data-ttu-id="c0eb0-127">-ne</span><span class="sxs-lookup"><span data-stu-id="c0eb0-127">-ne</span></span>                 | <span data-ttu-id="c0eb0-128">Ist ungleich</span><span class="sxs-lookup"><span data-stu-id="c0eb0-128">Is not equal to</span></span>                            | <span data-ttu-id="c0eb0-129">1 -ne 2</span><span class="sxs-lookup"><span data-stu-id="c0eb0-129">1 -ne 2</span></span>                      |
| <span data-ttu-id="c0eb0-130">-lt</span><span class="sxs-lookup"><span data-stu-id="c0eb0-130">-lt</span></span>                 | <span data-ttu-id="c0eb0-131">Ist kleiner als</span><span class="sxs-lookup"><span data-stu-id="c0eb0-131">Is less than</span></span>                               | <span data-ttu-id="c0eb0-132">1 -lt 2</span><span class="sxs-lookup"><span data-stu-id="c0eb0-132">1 -lt 2</span></span>                      |
| <span data-ttu-id="c0eb0-133">-le</span><span class="sxs-lookup"><span data-stu-id="c0eb0-133">-le</span></span>                 | <span data-ttu-id="c0eb0-134">Ist kleiner als oder gleich</span><span class="sxs-lookup"><span data-stu-id="c0eb0-134">Is less than or equal to</span></span>                   | <span data-ttu-id="c0eb0-135">1 -le 2</span><span class="sxs-lookup"><span data-stu-id="c0eb0-135">1 -le 2</span></span>                      |
| <span data-ttu-id="c0eb0-136">-gt</span><span class="sxs-lookup"><span data-stu-id="c0eb0-136">-gt</span></span>                 | <span data-ttu-id="c0eb0-137">Ist größer als</span><span class="sxs-lookup"><span data-stu-id="c0eb0-137">Is greater than</span></span>                            | <span data-ttu-id="c0eb0-138">2 -gt 1</span><span class="sxs-lookup"><span data-stu-id="c0eb0-138">2 -gt 1</span></span>                      |
| <span data-ttu-id="c0eb0-139">-ge</span><span class="sxs-lookup"><span data-stu-id="c0eb0-139">-ge</span></span>                 | <span data-ttu-id="c0eb0-140">Ist größer als oder gleich</span><span class="sxs-lookup"><span data-stu-id="c0eb0-140">Is greater than or equal to</span></span>                | <span data-ttu-id="c0eb0-141">2 -ge 1</span><span class="sxs-lookup"><span data-stu-id="c0eb0-141">2 -ge 1</span></span>                      |
| <span data-ttu-id="c0eb0-142">-like</span><span class="sxs-lookup"><span data-stu-id="c0eb0-142">-like</span></span>               | <span data-ttu-id="c0eb0-143">Entspricht (Platzhaltervergleich für Text)</span><span class="sxs-lookup"><span data-stu-id="c0eb0-143">Is like (wildcard comparison for text)</span></span>     | <span data-ttu-id="c0eb0-144">"file.doc" -like "f\*.do?"</span><span class="sxs-lookup"><span data-stu-id="c0eb0-144">"file.doc" -like "f\*.do?"</span></span>    |
| <span data-ttu-id="c0eb0-145">-notlike</span><span class="sxs-lookup"><span data-stu-id="c0eb0-145">-notlike</span></span>            | <span data-ttu-id="c0eb0-146">Entspricht nicht (Platzhaltervergleich für Text)</span><span class="sxs-lookup"><span data-stu-id="c0eb0-146">Is not like (wildcard comparison for text)</span></span> | <span data-ttu-id="c0eb0-147">"file.doc" -notlike "p\*.doc"</span><span class="sxs-lookup"><span data-stu-id="c0eb0-147">"file.doc" -notlike "p\*.doc"</span></span> |
| <span data-ttu-id="c0eb0-148">-contains</span><span class="sxs-lookup"><span data-stu-id="c0eb0-148">-contains</span></span>           | <span data-ttu-id="c0eb0-149">Enthält</span><span class="sxs-lookup"><span data-stu-id="c0eb0-149">Contains</span></span>                                   | <span data-ttu-id="c0eb0-150">1,2,3 -contains 1</span><span class="sxs-lookup"><span data-stu-id="c0eb0-150">1,2,3 -contains 1</span></span>            |
| <span data-ttu-id="c0eb0-151">-notcontains</span><span class="sxs-lookup"><span data-stu-id="c0eb0-151">-notcontains</span></span>        | <span data-ttu-id="c0eb0-152">Enthält nicht</span><span class="sxs-lookup"><span data-stu-id="c0eb0-152">Does not contain</span></span>                           | <span data-ttu-id="c0eb0-153">1,2,3 -notcontains 4</span><span class="sxs-lookup"><span data-stu-id="c0eb0-153">1,2,3 -notcontains 4</span></span>         |

<span data-ttu-id="c0eb0-154">In `Where-Object`-Skriptblöcken dient die spezielle Variable `$_` zum Verweisen auf das aktuelle Objekt in der Pipeline.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-154">`Where-Object` script blocks use the special variable `$_` to refer to the current object in the pipeline.</span></span> <span data-ttu-id="c0eb0-155">Es folgt ein Beispiel für die Funktionsweise.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-155">Here is an example of how it works.</span></span> <span data-ttu-id="c0eb0-156">Wenn Sie über eine Liste mit Zahlen verfügen und nur diejenigen zurückgegeben möchten, die kleiner als 3 sind, können Sie die Zahlen mit `Where-Object` folgendermaßen filtern:</span><span class="sxs-lookup"><span data-stu-id="c0eb0-156">If you have a list of numbers, and only want to return the ones that are less than 3, you can use `Where-Object` to filter the numbers by typing:</span></span>

```
1,2,3,4 | Where-Object {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a><span data-ttu-id="c0eb0-157">Filtern basierend auf Objekteigenschaften</span><span class="sxs-lookup"><span data-stu-id="c0eb0-157">Filtering Based on Object Properties</span></span>

<span data-ttu-id="c0eb0-158">Da `$_` auf das aktuelle Pipelineobjekt verweist, können wir für unsere Tests auf seine Eigenschaften zugreifen.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-158">Since `$_` refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="c0eb0-159">Als Beispiel können wir uns die Klasse **Win32_SystemDriver** in WMI anschauen.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-159">As an example, we can look at the **Win32_SystemDriver** class in WMI.</span></span> <span data-ttu-id="c0eb0-160">Möglicherweise gibt es in einem bestimmten System Hunderte von Systemtreibern, Sie sind aber vielleicht nur an einer bestimmten Auswahl von Systemtreibern interessiert, z. B. an den Treibern, die gerade ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-160">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="c0eb0-161">Für die **Win32_SystemDriver**-Klasse lautet die relevante Eigenschaft **State**.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-161">For the **Win32_SystemDriver** class the relevant property is **State**.</span></span> <span data-ttu-id="c0eb0-162">Sie können die Systemtreiber so filtern, dass nur die ausgeführten Treiber ausgewählt werden. Geben Sie dazu Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="c0eb0-162">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq 'Running'}
```

<span data-ttu-id="c0eb0-163">Dies erzeugt immer noch eine lange Liste.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-163">This still produces a long list.</span></span> <span data-ttu-id="c0eb0-164">Vielleicht möchten Sie die Liste weiter filtern, um nur die Treiber auszuwählen, die automatisch gestartet werden. Hierzu testen Sie zusätzlich den **StartMode**-Wert:</span><span class="sxs-lookup"><span data-stu-id="c0eb0-164">You may want to filter to only select the drivers set to start automatically by testing the **StartMode** value as well:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Auto"}
```

```Output
DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
...
```

<span data-ttu-id="c0eb0-165">Dadurch erhalten Sie eine Vielzahl von Informationen, die Sie nicht mehr benötigen, da bekannt ist, dass die Treiber ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-165">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span>
<span data-ttu-id="c0eb0-166">In der Tat sind die einzigen Informationen, die Sie an dieser Stelle wahrscheinlich benötigen, der Name und der Anzeigename.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-166">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="c0eb0-167">Der folgende Befehl enthält nur diese zwei Eigenschaften, wodurch eine wesentlich vereinfachte Ausgabe erzeugt wird:</span><span class="sxs-lookup"><span data-stu-id="c0eb0-167">The following command includes only those two properties, resulting in much simpler output:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Manual"} |
      Format-Table -Property Name,DisplayName
```

```Output
Name              DisplayName
----              -----------
AsyncMac               RAS Asynchronous Media Driver
bindflt                Windows Bind Filter Driver
bowser                 Browser
CompositeBus           Composite Bus Enumerator Driver
condrv                 Console Driver
HdAudAddService        Microsoft 1.1 UAA Function Driver for High Definition Audio Service
HDAudBus               Microsoft UAA Bus Driver for High Definition Audio
HidUsb                 Microsoft HID Class Driver
HTTP                   HTTP Service
igfx                   igfx
IntcDAud               Intel(R) Display Audio
intelppm               Intel Processor Driver
...
```

<span data-ttu-id="c0eb0-168">Der Befehl oben umfasst zwei `Where-Object`-Elemente, die aber mithilfe des logischen Operators `-and` wie folgt in einem einzigen `Where-Object`-Element ausgedrückt werden können:</span><span class="sxs-lookup"><span data-stu-id="c0eb0-168">There are two `Where-Object` elements in the above command, but they can be expressed in a single `Where-Object` element by using the `-and` logical operator, like this:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual')} |
    Format-Table -Property Name,DisplayName
```

<span data-ttu-id="c0eb0-169">In der folgenden Tabelle sind die standardmäßigen logischen Operatoren aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="c0eb0-169">The standard logical operators are listed in the following table.</span></span>

| <span data-ttu-id="c0eb0-170">Logischer Operator</span><span class="sxs-lookup"><span data-stu-id="c0eb0-170">Logical Operator</span></span> |                 <span data-ttu-id="c0eb0-171">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="c0eb0-171">Meaning</span></span>                  |  <span data-ttu-id="c0eb0-172">Beispiel (gibt „true“ zurück)</span><span class="sxs-lookup"><span data-stu-id="c0eb0-172">Example (returns true)</span></span>  |
| ---------------- | ---------------------------------------- | ------------------------ |
| <span data-ttu-id="c0eb0-173">-and</span><span class="sxs-lookup"><span data-stu-id="c0eb0-173">-and</span></span>             | <span data-ttu-id="c0eb0-174">Logisches „Und“; „true“, wenn beide Seiten zutreffen</span><span class="sxs-lookup"><span data-stu-id="c0eb0-174">Logical and; true if both sides are true</span></span> | <span data-ttu-id="c0eb0-175">(1 -eq 1) -and (2 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="c0eb0-175">(1 -eq 1) -and (2 -eq 2)</span></span> |
| <span data-ttu-id="c0eb0-176">-or</span><span class="sxs-lookup"><span data-stu-id="c0eb0-176">-or</span></span>              | <span data-ttu-id="c0eb0-177">Logisches „Oder“; „true“, wenn eine der beiden Seiten zutrifft</span><span class="sxs-lookup"><span data-stu-id="c0eb0-177">Logical or; true if either side is true</span></span>  | <span data-ttu-id="c0eb0-178">(1 -eq 1) -or (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="c0eb0-178">(1 -eq 1) -or (1 -eq 2)</span></span>  |
| <span data-ttu-id="c0eb0-179">-not</span><span class="sxs-lookup"><span data-stu-id="c0eb0-179">-not</span></span>             | <span data-ttu-id="c0eb0-180">Logisches „Nicht“; kehrt „true“ und „false“ um</span><span class="sxs-lookup"><span data-stu-id="c0eb0-180">Logical not; reverses true and false</span></span>     | <span data-ttu-id="c0eb0-181">-not (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="c0eb0-181">-not (1 -eq 2)</span></span>           |
| \!               | <span data-ttu-id="c0eb0-182">Logisches „Nicht“; kehrt „true“ und „false“ um</span><span class="sxs-lookup"><span data-stu-id="c0eb0-182">Logical not; reverses true and false</span></span>     | <span data-ttu-id="c0eb0-183">\!(1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="c0eb0-183">\!(1 -eq 2)</span></span>              |
