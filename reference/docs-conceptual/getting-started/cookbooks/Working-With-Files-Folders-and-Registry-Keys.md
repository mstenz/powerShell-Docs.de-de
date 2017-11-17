---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Arbeiten mit Dateien, Ordnern und Registrierungsschlüsseln"
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: 22a2390686659033bfd8b02a151b3397cfd46a22
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2017
---
# <a name="working-with-files-folders-and-registry-keys"></a><span data-ttu-id="8a599-103">Arbeiten mit Dateien, Ordnern und Registrierungsschlüsseln</span><span class="sxs-lookup"><span data-stu-id="8a599-103">Working With Files, Folders and Registry Keys</span></span>
<span data-ttu-id="8a599-104">Windows PowerShell verwendet das Nomen **Item** zum Verweisen auf Elemente in einem Windows PowerShell-Laufwerk.</span><span class="sxs-lookup"><span data-stu-id="8a599-104">Windows PowerShell uses the noun **Item** to refer to items found on a Windows PowerShell drive.</span></span> <span data-ttu-id="8a599-105">Im Zusammenhang mit dem Windows PowerShell FileSystem-Anbieter kann ein **Item** eine Datei, ein Ordner oder das Windows PowerShell-Laufwerk sein.</span><span class="sxs-lookup"><span data-stu-id="8a599-105">When dealing with the Windows PowerShell FileSystem provider, an **Item** might be a file, a folder, or the Windows PowerShell drive.</span></span> <span data-ttu-id="8a599-106">Das Auflisten dieser Elemente und die Arbeiten damit ist in den meisten Verwaltungseinstellungen eine wichtige grundlegende Aufgabe. Daher sollen diese Aufgaben ausführlich erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="8a599-106">Listing and working with these items is a critical basic task in most administrative settings, so we want to discuss these tasks in detail.</span></span>

### <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a><span data-ttu-id="8a599-107">Auflisten von Dateien, Ordnern und Registrierungsschlüsseln (Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="8a599-107">Enumerating Files, Folders, and Registry Keys (Get-ChildItem)</span></span>
<span data-ttu-id="8a599-108">Da das Abrufen einer Sammlung von Elementen von einem bestimmten Standort eine sehr häufig vorkommende Aufgabe ist, wurde das Cmdlet **Get-ChildItem** speziell dazu entwickelt, alle in einem Container, z.B. einem Ordner, gefundenen Elemente zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="8a599-108">Since getting a collection of items from a particular location is such a common task, the **Get-ChildItem** cmdlet is designed specifically to return all items found within a container such as a folder.</span></span>

<span data-ttu-id="8a599-109">Wenn Sie alle Dateien und Ordner zurückgeben möchten, die direkt im Ordner „C:\\Windows“ enthalten sind, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="8a599-109">If you want to return all files and folders that are contained directly within the folder C:\\Windows, type:</span></span>

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

<span data-ttu-id="8a599-110">Die Auflistung gleicht dem, was Sie sehen, wenn Sie den Befehl **dir** in **Cmd.exe** oder den Befehl **ls** in einer UNIX-Befehlsshell eingeben.</span><span class="sxs-lookup"><span data-stu-id="8a599-110">The listing looks similar to what you would see when you enter the **dir** command in **Cmd.exe**, or the **ls** command in a UNIX command shell.</span></span>

<span data-ttu-id="8a599-111">Sie können unter Verwendung der Parameter des Cmdlets **Get-ChildItem** sehr komplexe Auflistungen erstellen.</span><span class="sxs-lookup"><span data-stu-id="8a599-111">You can perform very complex listings by using parameters of the **Get-ChildItem** cmdlet.</span></span> <span data-ttu-id="8a599-112">Wir werden als Nächstes einige Szenarien näher betrachten.</span><span class="sxs-lookup"><span data-stu-id="8a599-112">We will look at a few scenarios next.</span></span> <span data-ttu-id="8a599-113">Sie können die Syntax des Cmdlets **Get-ChildItem** anzeigen, indem Sie Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="8a599-113">You can see the syntax the **Get-ChildItem** cmdlet by typing:</span></span>

```
PS> Get-Command -Name Get-ChildItem -Syntax
```

<span data-ttu-id="8a599-114">Diese Parameter können gemischt und angepasst werden, um eine stark angepasste Ausgabe zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="8a599-114">These parameters can be mixed and matched to get highly customized output.</span></span>

#### <a name="listing-all-contained-items--recurse"></a><span data-ttu-id="8a599-115">Auflisten aller enthaltenen Elemente (-Recurse)</span><span class="sxs-lookup"><span data-stu-id="8a599-115">Listing all Contained Items (-Recurse)</span></span>
<span data-ttu-id="8a599-116">Um sowohl die Elemente in einem Windows-Ordner als auch alle in dessen Unterordnern enthaltenen Elemente anzuzeigen, verwenden Sie den Parameter **Recurse** von **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="8a599-116">To see both the items inside a Windows folder and any items that are contained within the subfolders, use the **Recurse** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="8a599-117">Die Auflistung zeigt alles, was im Windows-Ordner enthalten ist, und alle Elemente in seinen Unterordnern an.</span><span class="sxs-lookup"><span data-stu-id="8a599-117">The listing displays everything within the Windows folder and the items in its subfolders.</span></span> <span data-ttu-id="8a599-118">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="8a599-118">For example:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

#### <a name="filtering-items-by-name--name"></a><span data-ttu-id="8a599-119">Filtern von Elementen anhand des Namens (-Name)</span><span class="sxs-lookup"><span data-stu-id="8a599-119">Filtering Items by Name (-Name)</span></span>
<span data-ttu-id="8a599-120">Um nur die Elementnamen anzuzeigen, verwenden Sie den Parameter **Name** von **Get-Childitem**:</span><span class="sxs-lookup"><span data-stu-id="8a599-120">To display only the names of items, use the **Name** parameter of **Get-Childitem**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

#### <a name="forcibly-listing-hidden-items--force"></a><span data-ttu-id="8a599-121">Erzwungenes Auflisten von ausgeblendeten Elementen (-Force)</span><span class="sxs-lookup"><span data-stu-id="8a599-121">Forcibly Listing Hidden Items (-Force)</span></span>
<span data-ttu-id="8a599-122">Elemente, die normalerweise im Datei-Explorer oder in „Cmd.exe“ nicht sichtbar sind, werden in der Ausgabe des Befehls **Get-ChildItem** nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8a599-122">Items that are normally invisible in File Explorer or Cmd.exe are not displayed in the output of a **Get-ChildItem** command.</span></span> <span data-ttu-id="8a599-123">Um ausgeblendete Elemente anzuzeigen, verwenden Sie den Parameter **Force** von **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="8a599-123">To display hidden items, use the **Force** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="8a599-124">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="8a599-124">For example:</span></span>

```
Get-ChildItem -Path C:\Windows -Force
```

<span data-ttu-id="8a599-125">Dieser Parameter heißt „Force“ (Zwingen), weil Sie mit ihm erzwingen können, dass das normale Verhalten des Befehls **Get-ChildItem** außer Kraft gesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="8a599-125">This parameter is named Force because you can forcibly override the normal behavior of the **Get-ChildItem** command.</span></span> <span data-ttu-id="8a599-126">„Force“ ist ein weit verbreiteter Parameter, der eine Aktion erzwingt, die ein Cmdlet normalerweise nicht ausführen würde. Allerdings wird keine Aktion ausgeführt, die die Sicherheit des Systems gefährden würde.</span><span class="sxs-lookup"><span data-stu-id="8a599-126">Force is a widely used parameter that forces an action that a cmdlet would not normally perform, although it will not perform any action that compromises the security of the system.</span></span>

#### <a name="matching-item-names-with-wildcards"></a><span data-ttu-id="8a599-127">Abgleichen von Elementnamen mit Platzhaltern</span><span class="sxs-lookup"><span data-stu-id="8a599-127">Matching Item Names with Wildcards</span></span>
<span data-ttu-id="8a599-128">Der Befehl **Get-ChildItem** akzeptiert Platzhalter im Pfad der aufzulistenden Elemente.</span><span class="sxs-lookup"><span data-stu-id="8a599-128">**The Get-ChildItem** command accepts wildcards in the path of the items to list.</span></span>

<span data-ttu-id="8a599-129">Da das Abgleichen von Platzhaltern vom Windows PowerShell-Modul durchgeführt wird, verwenden alle Cmdlets, die Platzhalter akzeptieren, die gleiche Notation und das gleiche Abgleichverhalten.</span><span class="sxs-lookup"><span data-stu-id="8a599-129">Because wildcard matching is handled by the Windows PowerShell engine, all cmdlets that accepts wildcards use the same notation and have the same matching behavior.</span></span> <span data-ttu-id="8a599-130">Die Windows PowerShell-Notation für Platzhalter enthält Folgendes:</span><span class="sxs-lookup"><span data-stu-id="8a599-130">The Windows PowerShell wildcard notation includes:</span></span>

- <span data-ttu-id="8a599-131">Sternchen (\*) steht für null oder mehr beliebige Zeichen.</span><span class="sxs-lookup"><span data-stu-id="8a599-131">Asterisk (\*)matches zero or more occurrences of any character.</span></span>

- <span data-ttu-id="8a599-132">Fragezeichen (?) steht für genau ein Zeichen.</span><span class="sxs-lookup"><span data-stu-id="8a599-132">Question mark (?) matches exactly one character.</span></span>

- <span data-ttu-id="8a599-133">Die linke eckige Klammer (\[) und die rechte eckige Klammer (]) umgeben eine Gruppe von Zeichen, die für den Abgleich verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="8a599-133">Left bracket (\[) character and right bracket (]) character surround a set of characters to be matched.</span></span>

<span data-ttu-id="8a599-134">Hier sind einige Beispiele für die Funktionsweise der Platzhalterspezifikation.</span><span class="sxs-lookup"><span data-stu-id="8a599-134">Here are some examples of how wildcard specification works.</span></span>

<span data-ttu-id="8a599-135">Um im Windows-Verzeichnis alle Dateien mit dem Suffix **.log** und genau fünf Zeichen im Basisnamen zu suchen, geben Sie den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="8a599-135">To find all files in the Windows directory with the suffix **.log** and exactly five characters in the base name, enter the following command:</span></span>

```
PS> Get-ChildItem -Path C:\Windows\?????.log
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

<span data-ttu-id="8a599-136">Um im Windows-Verzeichnis alle Dateien zu suchen, die mit dem Buchstaben **x** beginnen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="8a599-136">To find all files that begin with the letter **x** in the Windows directory, type:</span></span>

```
Get-ChildItem -Path C:\Windows\x*
```

<span data-ttu-id="8a599-137">Um alle Dateien zu suchen, deren Name mit **x** oder **z** beginnt, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="8a599-137">To find all files whose names begin with **x** or **z**, type:</span></span>

```
Get-ChildItem -Path C:\Windows\[xz]*
```

#### <a name="excluding-items--exclude"></a><span data-ttu-id="8a599-138">Ausschließen von Elementen (-Exclude)</span><span class="sxs-lookup"><span data-stu-id="8a599-138">Excluding Items (-Exclude)</span></span>
<span data-ttu-id="8a599-139">Sie können bestimmte Elemente durch Verwenden des Parameters **Exclude** von „Get-ChildItem“ ausschließen.</span><span class="sxs-lookup"><span data-stu-id="8a599-139">You can exclude specific items by using the **Exclude** parameter of Get-ChildItem.</span></span> <span data-ttu-id="8a599-140">Auf diese Weise können Sie eine komplexe Filterung in einer einzigen Anweisung durchführen.</span><span class="sxs-lookup"><span data-stu-id="8a599-140">This lets you perform complex filtering in a single statement.</span></span>

<span data-ttu-id="8a599-141">Angenommen, Sie möchten die Windows Time Service-DLL im Ordner „System32“ suchen, und Sie können sich nur daran erinnern, dass der Name der DLL mit „W“ anfängt und „32“ darin enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="8a599-141">For example, suppose you are trying to find the Windows Time Service DLL in the System32 folder, and all you can remember about the DLL name is that it begins with "W" and has "32" in it.</span></span>

<span data-ttu-id="8a599-142">Mit einem Ausdruck wie **w\&#42;32\&#42;.dll** finden Sie alle DLLs, die die Bedingung erfüllen, aber es können auch die Kompatibilitäts-DLLs für Windows 95 und 16-Bit-Windows zurückgegeben werden, die „95“ oder „16“ im Namen enthalten.</span><span class="sxs-lookup"><span data-stu-id="8a599-142">An expression like **w\&#42;32\&#42;.dll** will find all DLLs that satisfy the conditions, but it may also return the Windows 95 and 16-bit Windows compatibility DLLs that include "95" or "16" in their names.</span></span> <span data-ttu-id="8a599-143">Sie können Dateien ausschließen, die diese Zahlen in ihren Namen enthalten, indem Sie den Parameter **Exclude** mit dem Muster **\&#42;\[9516]\&#42;** verwenden:</span><span class="sxs-lookup"><span data-stu-id="8a599-143">You can omit files that have any of these numbers in their names by using the **Exclude** parameter with the pattern **\&#42;\[9516]\&#42;**:</span></span>

<pre>PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*
Directory: Microsoft.PowerShell.Core\FileSystem::C:\WINDOWS\System32
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     174592 w32time.dll
-a---        2004-08-04   8:00 AM      22016 w32topl.dll
-a---        2004-08-04   8:00 AM     101888 win32spl.dll
-a---        2004-08-04   8:00 AM     172032 wldap32.dll
-a---        2004-08-04   8:00 AM     264192 wow32.dll
-a---        2004-08-04   8:00 AM      82944 ws2_32.dll
-a---        2004-08-04   8:00 AM      42496 wsnmp32.dll
-a---        2004-08-04   8:00 AM      22528 wsock32.dll
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll</pre>

#### <a name="mixing-get-childitem-parameters"></a><span data-ttu-id="8a599-144">Kombinieren von Get-ChildItem-Parametern</span><span class="sxs-lookup"><span data-stu-id="8a599-144">Mixing Get-ChildItem Parameters</span></span>
<span data-ttu-id="8a599-145">Sie können verschiedene Parameter des Cmdlets **Get-ChildItem** im gleichen Befehl verwenden.</span><span class="sxs-lookup"><span data-stu-id="8a599-145">You can use several of the parameters of the **Get-ChildItem** cmdlet in the same command.</span></span> <span data-ttu-id="8a599-146">Bevor Sie Parameter kombinieren, sollten Sie sicher sein, dass Sie das Abgleichen mit Platzhalterzeichen verstanden haben.</span><span class="sxs-lookup"><span data-stu-id="8a599-146">Before you mix parameters, be sure that you understand wildcard matching.</span></span> <span data-ttu-id="8a599-147">Beispielsweise gibt der folgende Befehl keine Ergebnisse zurück:</span><span class="sxs-lookup"><span data-stu-id="8a599-147">For example, the following command returns no results:</span></span>

```
PS> Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

<span data-ttu-id="8a599-148">Es werden keine Ergebnisse zurückgegeben, obwohl es im Windows-Ordner zwei DLLs gibt, die mit dem Buchstaben „z“ beginnen.</span><span class="sxs-lookup"><span data-stu-id="8a599-148">There are no results, even though there are two DLLs that begin with the letter "z" in the Windows folder.</span></span>

<span data-ttu-id="8a599-149">Es wurden keine Ergebnisse zurückgegeben, weil das Platzhalterzeichen als Teil des Pfads angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="8a599-149">No results were returned because we specified the wildcard as part of the path.</span></span> <span data-ttu-id="8a599-150">Obwohl der Befehl rekursiv war, hat das Cmdlet **Get-ChildItem** die Elemente auf die Elemente im Windows-Ordner beschränkt, deren Namen mit „.dll“ enden.</span><span class="sxs-lookup"><span data-stu-id="8a599-150">Even though the command was recursive, the **Get-ChildItem** cmdlet restricted the items to those that are in the Windows folder with names ending with ".dll".</span></span>

<span data-ttu-id="8a599-151">Um eine rekursive Suche nach Dateien anzugeben, deren Namen einem bestimmten Muster entsprechen, verwenden Sie den Parameter **-Include**.</span><span class="sxs-lookup"><span data-stu-id="8a599-151">To specify a recursive search for files whose names match a special pattern, use the **-Include** parameter.</span></span>

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```

