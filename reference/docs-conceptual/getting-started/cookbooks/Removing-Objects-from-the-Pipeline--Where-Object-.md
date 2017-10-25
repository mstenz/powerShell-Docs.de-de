---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Entfernen von Objekten aus der Pipeline – Where-Object"
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: 4140c4c3ebb26223d03ca139992fedf6e184a38b
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2017
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="4a8b1-103">Entfernen von Objekten aus der Pipeline (Where-Object)</span><span class="sxs-lookup"><span data-stu-id="4a8b1-103">Removing Objects from the Pipeline (Where-Object)</span></span>
<span data-ttu-id="4a8b1-104">In Windows PowerShell geschieht es häufig, dass Sie mehr Objekte als gewünscht generieren und an eine Pipeline übergeben.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-104">In Windows PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="4a8b1-105">Mithilfe der **Format**-Cmdlets können Sie die Eigenschaften bestimmter Objekte angeben, die angezeigt werden sollen, aber dies hilft dabei, ganze Objekte aus der Anzeige zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-105">You can specify the properties of particular objects to display by using the **Format** cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="4a8b1-106">Möglicherweise möchten Sie die Objekte vor dem Ende einer Pipeline filtern, um nur für eine Teilmenge der ursprünglich generierten Objekte bestimmte Aktionen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-106">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="4a8b1-107">Windows PowerShell enthält ein **Where-Object**-Cmdlet, mit dem Sie jedes Objekt in der Pipeline testen können, um es nur dann an die Pipeline zu übergeben, wenn es eine bestimmte Testbedingung erfüllt.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-107">Windows PowerShell includes a **Where-Object** cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="4a8b1-108">Objekte, die den Test nicht bestehen, werden aus der Pipeline entfernt.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-108">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="4a8b1-109">Sie geben die Testbedingung als Wert des Parameters **Where-ObjectFilterScript** an.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-109">You supply the test condition as the value of the **Where-ObjectFilterScript** parameter.</span></span>

### <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="4a8b1-110">Ausführen einfacher Tests mit „Where-Object“</span><span class="sxs-lookup"><span data-stu-id="4a8b1-110">Performing Simple Tests with Where-Object</span></span>
<span data-ttu-id="4a8b1-111">Der Wert von **FilterScript** ist ein *Skriptblock* (d.h. ein oder mehrere, in geschweifte Klammern {} eingeschlossene Windows PowerShell-Befehle), der als „true“ oder „false“ ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-111">The value of **FilterScript** is a *script block* -  one or more Windows PowerShell commands surrounded by braces {} - that evaluates to true or false.</span></span> <span data-ttu-id="4a8b1-112">Diese Skriptblöcke können sehr einfach sein, aber ihre Erstellung erfordert Kenntnisse eines anderen Windows PowerShell-Konzepts: Vergleichsoperatoren.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-112">These script blocks can be very simple, but creating them requires knowing about another Windows PowerShell concept, comparison operators.</span></span> <span data-ttu-id="4a8b1-113">Mit einem Vergleichsoperator werden die Elemente auf den beiden Seiten des Operators verglichen.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-113">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="4a8b1-114">Vergleichsoperatoren beginnen mit einem Minuszeichen (-), gefolgt von einem Namen.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-114">Comparison operators begin with a '-' character and are followed by a name.</span></span> <span data-ttu-id="4a8b1-115">Die grundlegenden Vergleichsoperatoren können für nahezu jede Art von Objekt verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-115">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="4a8b1-116">Die erweiterten Vergleichsoperatoren können möglicherweise nur mit Text oder Arrays verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-116">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="4a8b1-117">Bei Windows PowerShell-Vergleichsoperatoren wird beim Arbeiten mit Text die Groß-/Kleinschreibung standardmäßig nicht beachtet.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-117">By default, when working with text, Windows PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="4a8b1-118">Aufgrund von Analyseaspekten werden Symbole wie <, > und = nicht als Vergleichsoperatoren verwendet.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-118">Due to parsing considerations, symbols such as <,>, and = are not used as comparison operators.</span></span> <span data-ttu-id="4a8b1-119">Stattdessen bestehen Vergleichsoperatoren aus Buchstaben.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-119">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="4a8b1-120">In der folgenden Tabelle sind die grundlegenden Vergleichsoperatoren aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-120">The basic comparison operators are listed in the following table.</span></span>

|<span data-ttu-id="4a8b1-121">Vergleichsoperator</span><span class="sxs-lookup"><span data-stu-id="4a8b1-121">Comparison Operator</span></span>|<span data-ttu-id="4a8b1-122">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="4a8b1-122">Meaning</span></span>|<span data-ttu-id="4a8b1-123">Beispiel (gibt „true“ zurück)</span><span class="sxs-lookup"><span data-stu-id="4a8b1-123">Example (returns true)</span></span>|
|-----------------------|-----------|--------------------------|
|<span data-ttu-id="4a8b1-124">-eq</span><span class="sxs-lookup"><span data-stu-id="4a8b1-124">-eq</span></span>|<span data-ttu-id="4a8b1-125">Ist gleich</span><span class="sxs-lookup"><span data-stu-id="4a8b1-125">is equal to</span></span>|<span data-ttu-id="4a8b1-126">1 -eq 1</span><span class="sxs-lookup"><span data-stu-id="4a8b1-126">1 -eq 1</span></span>|
|<span data-ttu-id="4a8b1-127">-ne</span><span class="sxs-lookup"><span data-stu-id="4a8b1-127">-ne</span></span>|<span data-ttu-id="4a8b1-128">Ist ungleich</span><span class="sxs-lookup"><span data-stu-id="4a8b1-128">Is not equal to</span></span>|<span data-ttu-id="4a8b1-129">1 -ne 2</span><span class="sxs-lookup"><span data-stu-id="4a8b1-129">1 -ne 2</span></span>|
|<span data-ttu-id="4a8b1-130">-lt</span><span class="sxs-lookup"><span data-stu-id="4a8b1-130">-lt</span></span>|<span data-ttu-id="4a8b1-131">Ist kleiner als</span><span class="sxs-lookup"><span data-stu-id="4a8b1-131">Is less than</span></span>|<span data-ttu-id="4a8b1-132">1 -lt 2</span><span class="sxs-lookup"><span data-stu-id="4a8b1-132">1 -lt 2</span></span>|
|<span data-ttu-id="4a8b1-133">-le</span><span class="sxs-lookup"><span data-stu-id="4a8b1-133">-le</span></span>|<span data-ttu-id="4a8b1-134">Ist kleiner als oder gleich</span><span class="sxs-lookup"><span data-stu-id="4a8b1-134">Is less than or equal to</span></span>|<span data-ttu-id="4a8b1-135">1 -le 2</span><span class="sxs-lookup"><span data-stu-id="4a8b1-135">1 -le 2</span></span>|
|<span data-ttu-id="4a8b1-136">-gt</span><span class="sxs-lookup"><span data-stu-id="4a8b1-136">-gt</span></span>|<span data-ttu-id="4a8b1-137">Ist größer als</span><span class="sxs-lookup"><span data-stu-id="4a8b1-137">Is greater than</span></span>|<span data-ttu-id="4a8b1-138">2 -gt 1</span><span class="sxs-lookup"><span data-stu-id="4a8b1-138">2 -gt 1</span></span>|
|<span data-ttu-id="4a8b1-139">-ge</span><span class="sxs-lookup"><span data-stu-id="4a8b1-139">-ge</span></span>|<span data-ttu-id="4a8b1-140">Ist größer als oder gleich</span><span class="sxs-lookup"><span data-stu-id="4a8b1-140">Is greater than or equal to</span></span>|<span data-ttu-id="4a8b1-141">2 -ge 1</span><span class="sxs-lookup"><span data-stu-id="4a8b1-141">2 -ge 1</span></span>|
|<span data-ttu-id="4a8b1-142">-like</span><span class="sxs-lookup"><span data-stu-id="4a8b1-142">-like</span></span>|<span data-ttu-id="4a8b1-143">Entspricht (Platzhaltervergleich für Text)</span><span class="sxs-lookup"><span data-stu-id="4a8b1-143">Is like (wildcard comparison for text)</span></span>|<span data-ttu-id="4a8b1-144">"file.doc" -like "f\*.do?"</span><span class="sxs-lookup"><span data-stu-id="4a8b1-144">"file.doc" -like "f\*.do?"</span></span>|
|<span data-ttu-id="4a8b1-145">-notlike</span><span class="sxs-lookup"><span data-stu-id="4a8b1-145">-notlike</span></span>|<span data-ttu-id="4a8b1-146">Entspricht nicht (Platzhaltervergleich für Text)</span><span class="sxs-lookup"><span data-stu-id="4a8b1-146">Is not like (wildcard comparison for text)</span></span>|<span data-ttu-id="4a8b1-147">"file.doc" -notlike "p\*.doc"</span><span class="sxs-lookup"><span data-stu-id="4a8b1-147">"file.doc" -notlike "p\*.doc"</span></span>|
|<span data-ttu-id="4a8b1-148">-contains</span><span class="sxs-lookup"><span data-stu-id="4a8b1-148">-contains</span></span>|<span data-ttu-id="4a8b1-149">Enthält</span><span class="sxs-lookup"><span data-stu-id="4a8b1-149">Contains</span></span>|<span data-ttu-id="4a8b1-150">1,2,3 -contains 1</span><span class="sxs-lookup"><span data-stu-id="4a8b1-150">1,2,3 -contains 1</span></span>|
|<span data-ttu-id="4a8b1-151">-notcontains</span><span class="sxs-lookup"><span data-stu-id="4a8b1-151">-notcontains</span></span>|<span data-ttu-id="4a8b1-152">Enthält nicht</span><span class="sxs-lookup"><span data-stu-id="4a8b1-152">Does not contain</span></span>|<span data-ttu-id="4a8b1-153">1,2,3 -notcontains 4</span><span class="sxs-lookup"><span data-stu-id="4a8b1-153">1,2,3 -notcontains 4</span></span>|

<span data-ttu-id="4a8b1-154">In „Where-Object“-Skriptblöcken dient die spezielle Variable „$_“ zum Verweisen auf das aktuelle Objekt in der Pipeline.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-154">Where-Object script blocks use the special variable '$_' to refer to the current object in the pipeline.</span></span> <span data-ttu-id="4a8b1-155">Es folgt ein Beispiel für die Funktionsweise.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-155">Here is an example of how it works.</span></span> <span data-ttu-id="4a8b1-156">Wenn Sie über eine Liste mit Zahlen verfügen und nur diejenigen zurückgegeben möchten, die kleiner als 3 sind, können Sie die Zahlen mit „Where-Object“ folgendermaßen filtern:</span><span class="sxs-lookup"><span data-stu-id="4a8b1-156">If you have a list of numbers, and only want to return the ones that are less than 3, you can use Where-Object to filter the numbers by typing:</span></span>

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

### <a name="filtering-based-on-object-properties"></a><span data-ttu-id="4a8b1-157">Filtern basierend auf Objekteigenschaften</span><span class="sxs-lookup"><span data-stu-id="4a8b1-157">Filtering Based on Object Properties</span></span>
<span data-ttu-id="4a8b1-158">Da „$_“ auf das aktuelle Pipelineobjekt verweist, können wir für unsere Tests auf seine Eigenschaften zugreifen.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-158">Since $_ refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="4a8b1-159">Als Beispiel können wir uns die Klasse „Win32_SystemDriver“ in WMI anschauen.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-159">As an example, we can look at the Win32_SystemDriver class in WMI.</span></span> <span data-ttu-id="4a8b1-160">Möglicherweise gibt es in einem bestimmten System Hunderte von Systemtreibern, Sie sind aber vielleicht nur an einer bestimmten Auswahl von Systemtreibern interessiert, z. B. an den Treibern, die gerade ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-160">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="4a8b1-161">Wenn Sie „Get-Member“ verwenden, um „Win32_SystemDriver“-Elemente anzuzeigen (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**) sehen Sie, dass die relevante Eigenschaft „State“ ist und den Wert „Running“ aufweist, wenn der Treiber ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-161">If you use Get-Member to view Win32_SystemDriver members (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**) you will see that the relevant property is State, and that it has a value of "Running" when the driver is running.</span></span> <span data-ttu-id="4a8b1-162">Sie können die Systemtreiber so filtern, dass nur die ausgeführten Treiber ausgewählt werden. Geben Sie dazu Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="4a8b1-162">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"}
```

<span data-ttu-id="4a8b1-163">Dies erzeugt immer noch eine lange Liste.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-163">This still produces a long list.</span></span> <span data-ttu-id="4a8b1-164">Möglicherweise möchten Sie die Liste weiter filtern, um nur die Treiber auszuwählen, die automatisch gestartet werden. Verwenden Sie dazu außerdem den „StartMode“-Wert:</span><span class="sxs-lookup"><span data-stu-id="4a8b1-164">You may want to filter to only select the drivers set to start automatically by testing the StartMode value as well:</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Auto"}

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
```

<span data-ttu-id="4a8b1-165">Dadurch erhalten Sie eine Vielzahl von Informationen, die Sie nicht mehr benötigen, da bekannt ist, dass die Treiber ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-165">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span> <span data-ttu-id="4a8b1-166">In der Tat sind die einzigen Informationen, die Sie an dieser Stelle wahrscheinlich benötigen, der Name und der Anzeigename.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-166">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="4a8b1-167">Der folgende Befehl enthält nur diese zwei Eigenschaften, wodurch eine wesentlich vereinfachte Ausgabe erzeugt wird:</span><span class="sxs-lookup"><span data-stu-id="4a8b1-167">The following command includes only those two properties, resulting in much simpler output:</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Manual"} | Format-Table -Property Name,DisplayName

Name                                    DisplayName
----                                    -----------
AsyncMac                                RAS Asynchronous Media Driver
Fdc                                     Floppy Disk Controller Driver
Flpydisk                                Floppy Disk Driver
Gpc                                     Generic Packet Classifier
IpNat                                   IP Network Address Translator
mouhid                                  Mouse HID Driver
MRxDAV                                  WebDav Client Redirector
mssmbios                                Microsoft System Management BIOS Driver
```

<span data-ttu-id="4a8b1-168">Der oben stehende Befehl enthält zwei „Where-Object“-Elemente, die aber mit Hilfe des logischen Operators „-and“ wie folgt in einem einzigen „Where-Object“-Element ausgedrückt werden können:</span><span class="sxs-lookup"><span data-stu-id="4a8b1-168">There are two Where-Object elements in the above command, but they can be expressed in a single Where-Object element by using the -and logical operator, like this:</span></span>

```
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq "Running") -and ($_.StartMode -eq "Manual") } | Format-Table -Property Name,DisplayName
```

<span data-ttu-id="4a8b1-169">In der folgenden Tabelle sind die standardmäßigen logischen Operatoren aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="4a8b1-169">The standard logical operators are listed in the following table.</span></span>

|<span data-ttu-id="4a8b1-170">Logischer Operator</span><span class="sxs-lookup"><span data-stu-id="4a8b1-170">Logical Operator</span></span>|<span data-ttu-id="4a8b1-171">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="4a8b1-171">Meaning</span></span>|<span data-ttu-id="4a8b1-172">Beispiel (gibt „true“ zurück)</span><span class="sxs-lookup"><span data-stu-id="4a8b1-172">Example (returns true)</span></span>|
|--------------------|-----------|--------------------------|
|<span data-ttu-id="4a8b1-173">-and</span><span class="sxs-lookup"><span data-stu-id="4a8b1-173">-and</span></span>|<span data-ttu-id="4a8b1-174">Logisches „Und“; „true“, wenn beide Seiten zutreffen</span><span class="sxs-lookup"><span data-stu-id="4a8b1-174">Logical and; true if both sides are true</span></span>|<span data-ttu-id="4a8b1-175">(1 -eq 1) -and (2 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="4a8b1-175">(1 -eq 1) -and (2 -eq 2)</span></span>|
|<span data-ttu-id="4a8b1-176">-or</span><span class="sxs-lookup"><span data-stu-id="4a8b1-176">-or</span></span>|<span data-ttu-id="4a8b1-177">Logisches „Oder“; „true“, wenn eine der beiden Seiten zutrifft</span><span class="sxs-lookup"><span data-stu-id="4a8b1-177">Logical or; true if either side is true</span></span>|<span data-ttu-id="4a8b1-178">(1 -eq 1) -or (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="4a8b1-178">(1 -eq 1) -or (1 -eq 2)</span></span>|
|<span data-ttu-id="4a8b1-179">-not</span><span class="sxs-lookup"><span data-stu-id="4a8b1-179">-not</span></span>|<span data-ttu-id="4a8b1-180">Logisches „Nicht“; kehrt „true“ und „false“ um</span><span class="sxs-lookup"><span data-stu-id="4a8b1-180">Logical not; reverses true and false</span></span>|<span data-ttu-id="4a8b1-181">-not (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="4a8b1-181">-not (1 -eq 2)</span></span>|
|\!|<span data-ttu-id="4a8b1-182">Logisches „Nicht“; kehrt „true“ und „false“ um</span><span class="sxs-lookup"><span data-stu-id="4a8b1-182">Logical not; reverses true and false</span></span>|<span data-ttu-id="4a8b1-183">\!(1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="4a8b1-183">\!(1 -eq 2)</span></span>|

