---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Verwenden von „Format“-Befehlen zum Ändern der Ausgabeanzeige
ms.openlocfilehash: a1712dade1e7508c0c4a004685bd1bb04a126f74
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030059"
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="52196-103">Verwenden von „Format“-Befehlen zum Ändern der Ausgabeanzeige</span><span class="sxs-lookup"><span data-stu-id="52196-103">Using Format Commands to Change Output View</span></span>

<span data-ttu-id="52196-104">Windows PowerShell hat eine Reihe von Cmdlets, mit denen Sie steuern können, welche Eigenschaften für bestimmte Objekte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="52196-104">Windows PowerShell has a set of cmdlets that allow you to control which properties are displayed for particular objects.</span></span> <span data-ttu-id="52196-105">Der Name jedes dieser Cmdlets beginnt mit dem Verb **Format**.</span><span class="sxs-lookup"><span data-stu-id="52196-105">The names of all the cmdlets begin with the verb **Format**.</span></span> <span data-ttu-id="52196-106">In diesen Cmdlets können Sie eine oder mehrere anzuzeigende Eigenschaften auswählen.</span><span class="sxs-lookup"><span data-stu-id="52196-106">They let you select one or more properties to show.</span></span>

<span data-ttu-id="52196-107">Die **Format**-Cmdlets sind**Format-Wide**, **Format-List**, **Format-Table** und **Format-Custom**.</span><span class="sxs-lookup"><span data-stu-id="52196-107">The **Format** cmdlets are **Format-Wide**, **Format-List**, **Format-Table**, and **Format-Custom**.</span></span> <span data-ttu-id="52196-108">In dieser Benutzeranleitung werden nur die Cmdlets **Format-Wide**, **Format-List** und **Format-Table** beschrieben.</span><span class="sxs-lookup"><span data-stu-id="52196-108">We will only describe the **Format-Wide**, **Format-List**, and **Format-Table** cmdlets in this user's guide.</span></span>

<span data-ttu-id="52196-109">Jedes „Format“-Cmdlet hat Standardeigenschaften, die verwendet werden, wenn Sie keine bestimmten anzuzeigenden Eigenschaften angeben.</span><span class="sxs-lookup"><span data-stu-id="52196-109">Each format cmdlet has default properties that will be used if you do not specify specific properties to display.</span></span> <span data-ttu-id="52196-110">Für jedes Cmdlet wird außerdem derselbe Parametername, **Property**, verwendet, um anzugeben, welche Eigenschaften angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="52196-110">Each cmdlet also uses the same parameter name, **Property**, to specify which properties you want to display.</span></span> <span data-ttu-id="52196-111">Weil **Format-Wide** nur eine einzelne Eigenschaft anzeigt, übernimmt deren **Property**-Parameter nur einen einzelnen Wert, wogegen die „Property“-Parameter von **Format-List** und **Format-Table** eine Liste von Eigenschaftsnamen akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="52196-111">Because **Format-Wide** only shows a single property, its **Property** parameter only takes a single value, but the property parameters of **Format-List** and **Format-Table** will accept a list of property names.</span></span>

<span data-ttu-id="52196-112">Wenn Sie den Befehl **Get-Process -Name powershell** verwenden, wenn zwei Instanzen von Windows PowerShell ausgeführt werden, erhalten Sie eine Ausgabe, die folgendermaßen aussieht:</span><span class="sxs-lookup"><span data-stu-id="52196-112">If you use the command **Get-Process -Name powershell** with two instances of Windows PowerShell running, you get output that looks like this:</span></span>

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

<span data-ttu-id="52196-113">Im Rest dieses Abschnitts wird untersucht, wie mit **Format**-Cmdlets die Art und Weise der Ausgabeanzeige dieses Befehl geändert werden kann.</span><span class="sxs-lookup"><span data-stu-id="52196-113">In the rest of this section, we will explore how to use **Format** cmdlets to change the way the output of this command is displayed.</span></span>

## <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="52196-114">Verwenden von „Format-Wide“ für die Ausgabe eines einzelnen Elements</span><span class="sxs-lookup"><span data-stu-id="52196-114">Using Format-Wide for Single-Item Output</span></span>

<span data-ttu-id="52196-115">Das Cmdlet `Format-Wide` zeigt standardmäßig nur die Standardeigenschaft eines Objekts an.</span><span class="sxs-lookup"><span data-stu-id="52196-115">The `Format-Wide` cmdlet, by default, displays only the default property of an object.</span></span>
<span data-ttu-id="52196-116">Die Informationen, die zu dem jeweiligen Objekt gehören, werden in einer einzelnen Spalte angezeigt:</span><span class="sxs-lookup"><span data-stu-id="52196-116">The information associated with each object is displayed in a single column:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide
```

```output
Format-Custom                          Format-Hex
Format-List                            Format-Table
Format-Wide
```

<span data-ttu-id="52196-117">Sie können auch eine nicht standardmäßige Eigenschaft angeben:</span><span class="sxs-lookup"><span data-stu-id="52196-117">You can also specify a non-default property:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```output
Custom                                 Hex
List                                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="52196-118">Steuern der „Format-Wide“-Anzeige mit Spalte</span><span class="sxs-lookup"><span data-stu-id="52196-118">Controlling Format-Wide Display with Column</span></span>

<span data-ttu-id="52196-119">Mit dem Cmdlet `Format-Wide` können Sie immer nur jeweils eine Eigenschaft anzeigen.</span><span class="sxs-lookup"><span data-stu-id="52196-119">With the `Format-Wide` cmdlet, you can only display a single property at a time.</span></span>
<span data-ttu-id="52196-120">Dadurch ist es zum Anzeigen einfacher Listen geeignet, in denen nur ein Element pro Zeile aufgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="52196-120">This makes it useful for displaying simple lists that show only one element per line.</span></span>
<span data-ttu-id="52196-121">Um eine einfache Liste zu erhalten, legen Sie den Wert des **Column**-Parameter auf 1 fest, indem Sie Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="52196-121">To get a simple listing, set the value of the **Column** parameter to 1 by typing:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 1
```

```output
Custom
Hex
List
Table
Wide
```

## <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="52196-122">Verwenden von „Format-List“ für eine Listenansicht</span><span class="sxs-lookup"><span data-stu-id="52196-122">Using Format-List for a List View</span></span>

<span data-ttu-id="52196-123">Das Cmdlet **Format-List** zeigt ein Objekt in Form einer Auflistung an, wobei jede Eigenschaft in einer eigenen Zeile beschriftet und angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="52196-123">The **Format-List** cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

<span data-ttu-id="52196-124">Sie können Sie beliebig viele Eigenschaften angeben:</span><span class="sxs-lookup"><span data-stu-id="52196-124">You can specify as many properties as you want:</span></span>

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="52196-125">Abrufen von ausführliche Informationen durch Verwenden von „Format-List“ mit Platzhaltern</span><span class="sxs-lookup"><span data-stu-id="52196-125">Getting Detailed Information by Using Format-List with Wildcards</span></span>

<span data-ttu-id="52196-126">Das Cmdlet **Format-List** bietet Ihnen die Möglichkeit, einen Platzhalters als Wert für den **Property**-Parameter zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="52196-126">The **Format-List** cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="52196-127">Dies ermöglicht es Ihnen, ausführliche Informationen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="52196-127">This lets you display detailed information.</span></span> <span data-ttu-id="52196-128">Häufig enthalten Objekte mehr Informationen, als Sie benötigen. Dies ist der Grund, warum Windows PowerShell nicht standardmäßig alle Eigenschaftswerte anzeigt.</span><span class="sxs-lookup"><span data-stu-id="52196-128">Often, objects include more information than you need, which is why Windows PowerShell does not show all property values by default.</span></span> <span data-ttu-id="52196-129">Um alle Eigenschaften eines Objekts anzuzeigen, verwenden Sie den Befehl **Format-List -Property \&#42;**.</span><span class="sxs-lookup"><span data-stu-id="52196-129">To show all of properties of an object, use the **Format-List -Property \&#42;** command.</span></span> <span data-ttu-id="52196-130">Der folgende Befehl generiert mehr als 60 Zeilen an Ausgabe für einen einzelnen Prozess:</span><span class="sxs-lookup"><span data-stu-id="52196-130">The following command generates over 60 lines of output for a single process:</span></span>

```powershell
Get-Process -Name powershell | Format-List -Property *
```

<span data-ttu-id="52196-131">Obwohl der Befehl **Format-List** nützlich ist, Details anzuzeigen, ist eine einfachere tabellarische Ansicht oft nützlicher, wenn Sie einen Überblick über Ausgabe wünschen, die viele Elemente enthält.</span><span class="sxs-lookup"><span data-stu-id="52196-131">Although the **Format-List** command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

## <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="52196-132">Verwenden von „Format-Table“ für tabellarische Ausgabe</span><span class="sxs-lookup"><span data-stu-id="52196-132">Using Format-Table for Tabular Output</span></span>

<span data-ttu-id="52196-133">Wenn Sie die Ausgabe des Befehls **Get-Process** mit dem Cmdlet **Format-Table** ohne angegebene Eigenschaftsnamen formatieren, erhalten Sie genau dieselbe Ausgabe wie für den Fall, dass Sie keine Formatierung anwenden.</span><span class="sxs-lookup"><span data-stu-id="52196-133">If you use the **Format-Table** cmdlet with no property names specified to format the output of the **Get-Process** command, you get exactly the same output as you do without performing any formatting.</span></span> <span data-ttu-id="52196-134">Der Grund hierfür ist, dass Prozesse in der Regel in einem Tabellenformat angezeigt werden, wie dies für die meisten Windows PowerShell-Objekte zutrifft.</span><span class="sxs-lookup"><span data-stu-id="52196-134">The reason is that processes are usually displayed in a tabular format, as are most Windows PowerShell objects.</span></span>

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="52196-135">Verbessern der „Format-Table“-Ausgabe (AutoSize)</span><span class="sxs-lookup"><span data-stu-id="52196-135">Improving Format-Table Output (AutoSize)</span></span>

<span data-ttu-id="52196-136">Eine tabellarische Ansicht ist zwar zum Anzeigen vieler vergleichbarer Informationen nützlich, kann aber zu Interpretationsschwierigkeiten führen, wenn die Anzeige zu schmal für die Daten ist.</span><span class="sxs-lookup"><span data-stu-id="52196-136">Although a tabular view is useful for displaying a lot of comparable information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="52196-137">Wenn Sie beispielsweise versuchen, den Pfad, die ID, den Namen und das Unternehmen eines Prozesses anzuzeigen, erhalten Sie abgeschnittene Ausgabe für die Spalten mit dem Pfad und dem Unternehmen des Prozesses:</span><span class="sxs-lookup"><span data-stu-id="52196-137">For example, if you try to display process path, ID, name, and company, you get truncated output for the process path and the company column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

<span data-ttu-id="52196-138">Wenn Sie den **AutoSize**-Parameter angeben, wenn Sie den Befehl **Format-Table** ausführen, berechnet Windows PowerShell die Spaltenbreiten anhand der tatsächlichen Daten, die Sie anzeigen möchten.</span><span class="sxs-lookup"><span data-stu-id="52196-138">If you specify the **AutoSize** parameter when you run the **Format-Table** command, Windows PowerShell will calculate column widths based on the actual data you are going to display.</span></span> <span data-ttu-id="52196-139">Dadurch lässt sich die Spalte **Pfad** besser lesen, aber die Spalte für das Unternehmen bleibt abgeschnitten:</span><span class="sxs-lookup"><span data-stu-id="52196-139">This makes the **Path** column readable, but the company column remains truncated:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

<span data-ttu-id="52196-140">Im **Format-Table**Cmdlet werden möglicherweise weiterhin Daten abgeschnitten, aber dies erfolgt am Ende der Bildschirmausgabe.</span><span class="sxs-lookup"><span data-stu-id="52196-140">The **Format-Table** cmdlet might still truncate data, but it will only do so at the end of the screen.</span></span> <span data-ttu-id="52196-141">Jede Eigenschaft außer der letzten angezeigten Eigenschaft erhält so viel Breite, wie erforderlich ist, damit ihr längstes Datenelement richtig angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="52196-141">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span> <span data-ttu-id="52196-142">Sie können sehen, dass der Unternehmensname vollständig sichtbar ist, der Pfad aber abgeschnitten wird, wenn Sie die Positionen von **Path** und **Company** in der **Property**-Werteliste tauschen:</span><span class="sxs-lookup"><span data-stu-id="52196-142">You can see that company name is visible but path is truncated if you swap the locations of **Path** and **Company** in the **Property** value list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

<span data-ttu-id="52196-143">Für den Befehl **Format-Table** wird angenommen, dass eine Eigenschaft umso wichtiger ist, je näher sie sich am Anfang der Eigenschaftenliste befindet.</span><span class="sxs-lookup"><span data-stu-id="52196-143">The **Format-Table** command assumes that the nearer a property is to the beginning of the property list, the more important it is.</span></span> <span data-ttu-id="52196-144">Daher wird im Befehl versucht, die Eigenschaften, die dem Anfang am nächsten sind, vollständig anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="52196-144">So it attempts to display the properties nearest the beginning completely.</span></span> <span data-ttu-id="52196-145">Wenn der Befehl **Format-Table** nicht alle Eigenschaften anzeigen kann, entfernt er einige Spalten aus der Anzeige und gibt eine Warnung aus.</span><span class="sxs-lookup"><span data-stu-id="52196-145">If the **Format-Table** command cannot display all the properties, it will remove some columns from the display and provide a warning.</span></span> <span data-ttu-id="52196-146">Sie können dieses Verhalten sehen, wenn Sie **Name** zur letzten Eigenschaft in der Liste machen:</span><span class="sxs-lookup"><span data-stu-id="52196-146">You can see this behavior if you make **Name** the last property in the list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

<span data-ttu-id="52196-147">In dieser Ausgabe ist die ID-Spalte abgeschnitten, damit sie in die Auflistung passt, und die Spaltenüberschriften sind gestapelt.</span><span class="sxs-lookup"><span data-stu-id="52196-147">In the output above, the ID column is truncated to make it fit into the listing, and the column headings are stacked up.</span></span> <span data-ttu-id="52196-148">Eine automatische Größenänderung der Spalten erfolgt nicht immer so, wie Sie dies wünschen.</span><span class="sxs-lookup"><span data-stu-id="52196-148">Automatically resizing the columns does not always do what you want.</span></span>

### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="52196-149">Umbrechen von „Format-Table“-Ausgabe in Spalten (Wrap)</span><span class="sxs-lookup"><span data-stu-id="52196-149">Wrapping Format-Table Output in Columns (Wrap)</span></span>

<span data-ttu-id="52196-150">Sie können erzwingen, dass zu lange **Format-Table**-Daten innerhalb ihrer Anzeigespalte umbrochen werden, indem Sie den **Wrap**-Parameter verwenden.</span><span class="sxs-lookup"><span data-stu-id="52196-150">You can force lengthy **Format-Table** data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="52196-151">Das alleinige Verwenden des **Wrap**-Parameters bringt nicht notwendigerweise das von Ihnen erwartete Ergebnis, weil dann die Standardeinstellungen verwendet werden, wenn Sie nicht auch **AutoSize** angeben:</span><span class="sxs-lookup"><span data-stu-id="52196-151">Using the **Wrap** parameter alone will not necessarily do what you expect, since it uses default settings if you do not also specify **AutoSize**:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

<span data-ttu-id="52196-152">Ein Vorteil der Verwendung des **Wrap**-Parameters an sich besteht darin, dass er die Verarbeitung kaum verlangsamt.</span><span class="sxs-lookup"><span data-stu-id="52196-152">An advantage of using the **Wrap** parameter by itself is that it does not slow down processing very much.</span></span> <span data-ttu-id="52196-153">Wenn Sie eine rekursive Dateiauflistung eines umfangreichen Verzeichnissystems ausführen, kann es sehr lange dauern und viel Arbeitsspeicher erfordern, bis die ersten Ausgabeelemente angezeigt werden, wenn Sie **AutoSize** verwenden.</span><span class="sxs-lookup"><span data-stu-id="52196-153">If you perform a recursive file listing of a large directory system, it might take a very long time and use a lot of memory before displaying the first output items if you use **AutoSize**.</span></span>

<span data-ttu-id="52196-154">Wenn die Systemauslastung keine Rolle spielt, funktioniert **AutoSize** gut mit dem **Wrap**-Parameter.</span><span class="sxs-lookup"><span data-stu-id="52196-154">If you are not concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span> <span data-ttu-id="52196-155">Den ersten Spalten werden immer die Breiten zugeteilt, die für sie benötigt werden, um Elemente in einer Zeile anzuzeigen, genau so, als würden Sie **AutoSize** ohne den **Wrap**-Parameter angeben.</span><span class="sxs-lookup"><span data-stu-id="52196-155">The initial columns are always allotted as much width as they need to display items on one line, just as when you specify **AutoSize** without the **Wrap** parameter.</span></span> <span data-ttu-id="52196-156">Der einzige Unterschied ist, dass die letzte Spalte ggf. umbrochen wird:</span><span class="sxs-lookup"><span data-stu-id="52196-156">The only difference is that the final column will be wrapped if necessary:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

<span data-ttu-id="52196-157">Einige Spalten werden möglicherweise nicht angezeigt, wenn Sie die breitesten Spalten zuerst angeben. Daher ist es am sichersten, zunächst die schmalsten Datenelemente anzugeben.</span><span class="sxs-lookup"><span data-stu-id="52196-157">Some columns might not be displayed if you specify the widest columns first, so it is safest to specify the smallest data elements first.</span></span> <span data-ttu-id="52196-158">Im folgenden Beispiel ist das extrem breite „Path“-Element zuerst angegeben, und selbst mit Umbrechen geht die letzte **Name** Spalte verloren:</span><span class="sxs-lookup"><span data-stu-id="52196-158">In the following example, we specify the extremely wide path element first, and even with wrapping, we still lose the final **Name** column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

### <a name="organizing-table-output--groupby"></a><span data-ttu-id="52196-159">Ordnen von Tabellenausgabe (-GroupBy)</span><span class="sxs-lookup"><span data-stu-id="52196-159">Organizing Table Output (-GroupBy)</span></span>

<span data-ttu-id="52196-160">Eine weiterer nützlicher Parameter für das Steuern von tabellarischer Ausgabe ist **GroupBy**.</span><span class="sxs-lookup"><span data-stu-id="52196-160">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="52196-161">Es kann insbesondere schwierig sein, längere tabellarische Auflistungen zu vergleichen.</span><span class="sxs-lookup"><span data-stu-id="52196-161">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="52196-162">Mit dem **GroupBy**Parameter wird die Ausgabe anhand eines Eigenschaftswerts gruppiert.</span><span class="sxs-lookup"><span data-stu-id="52196-162">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="52196-163">Beispielsweise können Prozesse zur einfacheren Überprüfung nach dem Unternehmen gruppiert werden, wobei der Unternehmenswert aus der Eigenschaftenliste entfernt ist:</span><span class="sxs-lookup"><span data-stu-id="52196-163">For example, we can group processes by company for easier inspection, omitting the company value from the property listing:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```
