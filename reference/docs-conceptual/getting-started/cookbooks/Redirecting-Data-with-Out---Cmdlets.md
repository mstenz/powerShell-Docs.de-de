---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Umleiten von Daten mit Out-Cmdlets
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: e570ca1c2c665a4a5d23abb50d4102a012b160e9
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2017
---
# <a name="redirecting-data-with-out--cmdlets"></a><span data-ttu-id="6b615-103">Umleiten von Daten mit Out-*-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="6b615-103">Redirecting Data with Out-* Cmdlets</span></span>
<span data-ttu-id="6b615-104">Windows PowerShell stellt mehrere Cmdlets bereit, mit denen Sie die Datenausgabe direkt steuern können.</span><span class="sxs-lookup"><span data-stu-id="6b615-104">Windows PowerShell provides several cmdlets that let you control data output directly.</span></span> <span data-ttu-id="6b615-105">Diese Cmdlets haben zwei wichtige Merkmale gemeinsam.</span><span class="sxs-lookup"><span data-stu-id="6b615-105">These cmdlets share two important characteristics.</span></span>

<span data-ttu-id="6b615-106">Zum Ersten transformieren sie Daten grundsätzlich in eine Form von Text.</span><span class="sxs-lookup"><span data-stu-id="6b615-106">First, they generally transform data to some form of text.</span></span> <span data-ttu-id="6b615-107">Dies geschieht, weil die Cmdlets Daten an Systemkomponenten ausgegeben, die Texteingabe erfordern.</span><span class="sxs-lookup"><span data-stu-id="6b615-107">They do this because they output the data to system components that require text input.</span></span> <span data-ttu-id="6b615-108">Das heißt, sie müssen die Objekte als Text darstellen.</span><span class="sxs-lookup"><span data-stu-id="6b615-108">This means they need to represent the objects as text.</span></span> <span data-ttu-id="6b615-109">Daher wird der Text so formatiert, wie Sie ihn im Windows PowerShell-Konsolenfenster sehen.</span><span class="sxs-lookup"><span data-stu-id="6b615-109">Therefore, the text is formatted as you see it in the Windows PowerShell console window.</span></span>

<span data-ttu-id="6b615-110">Zum Zweiten wird für diese Cmdlets das Windows PowerShell-Verb **Out** verwendet, weil sie Informationen aus Windows PowerShell heraus an ein anderes Element senden.</span><span class="sxs-lookup"><span data-stu-id="6b615-110">Second, these cmdlets use the Windows PowerShell verb **Out** because they send information out from Windows PowerShell to somewhere else.</span></span> <span data-ttu-id="6b615-111">Das Cmdlet **Out-Host** ist keine Ausnahme: Die Hostfensteranzeige befindet sich außerhalb der Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6b615-111">The **Out-Host** cmdlet is no exception: the host window display is outside of Windows PowerShell.</span></span> <span data-ttu-id="6b615-112">Dies ist wichtig, denn Daten, die aus Windows PowerShell gesendet werden, werden tatsächlich entfernt.</span><span class="sxs-lookup"><span data-stu-id="6b615-112">This is important because when data is sent out of Windows PowerShell, it is actually removed.</span></span> <span data-ttu-id="6b615-113">Sie können dies sehen, wenn Sie eine Pipeline erstellen, über die die Daten an das Hostfenster ausgelagert werden, und dann versuchen, die Daten als Liste zu formatieren, wie hier gezeigt:</span><span class="sxs-lookup"><span data-stu-id="6b615-113">You can see this if you try to create a pipeline that pages data to the host window, and then attempt to format it as a list, as shown here:</span></span>

```
PS> Get-Process | Out-Host -Paging | Format-List
```

<span data-ttu-id="6b615-114">Sie erwarten wahrscheinlich, dass der Befehl Seiten mit Prozessinformationen im Listenformat anzeigt.</span><span class="sxs-lookup"><span data-stu-id="6b615-114">You might expect the command to display pages of process information in list format.</span></span> <span data-ttu-id="6b615-115">Stattdessen werden die Daten in der standardmäßigen tabellarischen Liste angezeigt:</span><span class="sxs-lookup"><span data-stu-id="6b615-115">Instead, it displays the default tabular list:</span></span>

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="6b615-116">Das Cmdlet **Out-Host** sendet die Daten direkt an die Konsole, sodass der Befehl **Format-List** nichts empfängt, was formatiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="6b615-116">The **Out-Host** cmdlet sends the data directly to the console, so the **Format-List** command never receives anything to format.</span></span>

<span data-ttu-id="6b615-117">Damit dieser Befehl die richtige Struktur hat, muss das Cmdlet **Out-Host** an das Ende der Pipeline gesetzt werden, wie unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="6b615-117">The correct way to structure this command is to put the **Out-Host** cmdlet at the end of the pipeline as shown below.</span></span> <span data-ttu-id="6b615-118">Dies bewirkt, dass die Prozessdaten in einer Liste formatiert werden, bevor sie ausgelagert und angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="6b615-118">This causes the process data to be formatted in a list before being paged and displayed.</span></span>

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="6b615-119">Dies gilt für alle **Out**-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="6b615-119">This applies to all of the **Out** cmdlets.</span></span> <span data-ttu-id="6b615-120">Ein **Out**-Cmdlet sollte immer am Ende einer Pipeline stehen.</span><span class="sxs-lookup"><span data-stu-id="6b615-120">An **Out** cmdlet should always appear at the end of the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="6b615-121">Alle **Out**-Cmdlets rendern Ausgabe als Text, wobei sie die Formatierung verwenden, die für das Konsolenfenster wirksam ist, einschließlich Längenbeschränkungen für Zeilen.</span><span class="sxs-lookup"><span data-stu-id="6b615-121">All the **Out** cmdlets render output as text, using the formatting in effect for the console window, including line length limits.</span></span>

#### <a name="paging-console-output-out-host"></a><span data-ttu-id="6b615-122">Auslagern von Konsolenausgabe (Out-Host)</span><span class="sxs-lookup"><span data-stu-id="6b615-122">Paging Console Output (Out-Host)</span></span>
<span data-ttu-id="6b615-123">Standardmäßig sendet Windows PowerShell Daten an das Hostfenster, und dies entspricht exakt der Funktionsweise des „Out-Host“-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="6b615-123">By default, Windows PowerShell sends data to the host window, which is exactly what the Out-Host cmdlet does.</span></span> <span data-ttu-id="6b615-124">Die vorrangige Verwendung für das „Out-Host“-Cmdlet ist das Auslagern von Daten, wie bereits erläutert.</span><span class="sxs-lookup"><span data-stu-id="6b615-124">The primary use for the Out-Host cmdlet is paging data as we discussed earlier.</span></span> <span data-ttu-id="6b615-125">Beispielsweise wird „Out-Host“ im folgenden Befehl dazu verwendet,die Ausgabe des „Get-Command“-Cmdlets auszulagern:</span><span class="sxs-lookup"><span data-stu-id="6b615-125">For example, the following command uses Out-Host to page the output of the Get-Command cmdlet:</span></span>

```
PS> Get-Command | Out-Host -Paging
```

<span data-ttu-id="6b615-126">Sie können auch die **more**-Funktion verwenden, um Daten auszulagern.</span><span class="sxs-lookup"><span data-stu-id="6b615-126">You can also use the **more** function to page data.</span></span> <span data-ttu-id="6b615-127">In Windows PowerShell ist **more** eine Funktion, die **Out-Host -Paging** aufruft.</span><span class="sxs-lookup"><span data-stu-id="6b615-127">In Windows PowerShell, **more** is a function that calls **Out-Host -Paging**.</span></span> <span data-ttu-id="6b615-128">Mit dem folgenden Befehl wird veranschaulicht, wie die **more**-Funktion verwendet wird, um die Ausgabe von „Get-Command“ auszulagern:</span><span class="sxs-lookup"><span data-stu-id="6b615-128">The following command demonstrates using the **more** function to page the output of Get-Command:</span></span>

```
PS> Get-Command | more
```

<span data-ttu-id="6b615-129">Wenn Sie einen oder mehrere Dateinamen als Argumente für die „more“-Funktion angeben, werden die Dateien von der Funktion gelesen, und die Funktion lagert die Inhalte der Dateien an den Host aus:</span><span class="sxs-lookup"><span data-stu-id="6b615-129">If you include one or more filenames as arguments to the more function, the function will read the specified files and page their contents to the host:</span></span>

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a><span data-ttu-id="6b615-130">Verwerfen von Ausgabe (Out-Null)</span><span class="sxs-lookup"><span data-stu-id="6b615-130">Discarding Output (Out-Null)</span></span>
<span data-ttu-id="6b615-131">Das **Out-Null**-Cmdlet verwirft sofort jegliche Eingabe, die es empfängt.</span><span class="sxs-lookup"><span data-stu-id="6b615-131">The **Out-Null** cmdlet is designed to immediately discard any input it receives.</span></span> <span data-ttu-id="6b615-132">Damit können Sie überflüssige Daten verwerfen, die Sie als Nebeneffekt des Ausführens eines Befehls erhalten.</span><span class="sxs-lookup"><span data-stu-id="6b615-132">This is useful for discarding unnecessary data that you get as a side-effect of running a command.</span></span> <span data-ttu-id="6b615-133">Wenn Sie den folgenden Befehl eingeben, erhalten Sie keinerlei Rückgabe von dem Befehl:</span><span class="sxs-lookup"><span data-stu-id="6b615-133">When type the following command, you do not get anything back from the command:</span></span>

```
PS> Get-Command | Out-Null
```

<span data-ttu-id="6b615-134">Das Cmdlet **Out-Null** verwirft keine Fehlerausgabe.</span><span class="sxs-lookup"><span data-stu-id="6b615-134">The **Out-Null** cmdlet does not discard error output.</span></span> <span data-ttu-id="6b615-135">Wenn Sie beispielsweise den folgenden Befehl eingeben, wird eine Meldung angezeigt, der zu entnehmen ist, dass Windows PowerShell „Is-NotACommand“ nicht erkennt:</span><span class="sxs-lookup"><span data-stu-id="6b615-135">For example, if you enter the following command, a message is displayed informing you that Windows PowerShell does not recognize 'Is-NotACommand':</span></span>

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a><span data-ttu-id="6b615-136">Drucken von Daten (Out-Printer)</span><span class="sxs-lookup"><span data-stu-id="6b615-136">Printing Data (Out-Printer)</span></span>
<span data-ttu-id="6b615-137">Sie können Daten drucken, indem Sie das Cmdlet **Out-Printer** verwenden.</span><span class="sxs-lookup"><span data-stu-id="6b615-137">You can print data by using the **Out-Printer** cmdlet.</span></span> <span data-ttu-id="6b615-138">Das Cmdlet **Out-Printer** verwendet den Standarddrucker, wenn Sie keinen Druckernamen angeben.</span><span class="sxs-lookup"><span data-stu-id="6b615-138">The **Out-Printer** cmdlet will use your default printer if you do not provide a printer name.</span></span> <span data-ttu-id="6b615-139">Sie können jeden Windows-basierten Drucker verwenden, indem Sie dessen Anzeigenamen angeben.</span><span class="sxs-lookup"><span data-stu-id="6b615-139">You can use any Windows-based printer by specifying its display name.</span></span> <span data-ttu-id="6b615-140">Es sind weder irgendeine Art von Druckeranschlusszuordnung noch sogar ein echter physischer Drucker erforderlich.</span><span class="sxs-lookup"><span data-stu-id="6b615-140">There is no need for any kind of printer port mapping or even a real physical printer.</span></span> <span data-ttu-id="6b615-141">Wenn Sie etwa die Bilderstellungstools für Microsoft Office-Dokumente installiert haben, können Sie die Daten in eine Bilddatei senden, indem Sie Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="6b615-141">For example, if you have the Microsoft Office document imaging tools installed, you can send the data to an image file by typing:</span></span>

```
PS> Get-Command Get-Command | Out-Printer -Name "Microsoft Office Document Image Writer"
```

#### <a name="saving-data-out-file"></a><span data-ttu-id="6b615-142">Speichern von Daten (Out-File)</span><span class="sxs-lookup"><span data-stu-id="6b615-142">Saving Data (Out-File)</span></span>
<span data-ttu-id="6b615-143">Mit dem Cmdlet **Out-File** können Sie Ausgabe in eine Datei statt an das Konsolenfenster senden.</span><span class="sxs-lookup"><span data-stu-id="6b615-143">You can send output to a file instead of the console window by using the **Out-File** cmdlet.</span></span> <span data-ttu-id="6b615-144">In der folgenden Befehlszeile wird die jeweilige Liste der Prozesse in die Datei **C:\\temp\\processlist.txt** gesendet:</span><span class="sxs-lookup"><span data-stu-id="6b615-144">The following command line sends a list of processes to the file **C:\\temp\\processlist.txt**:</span></span>

```
PS> Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

<span data-ttu-id="6b615-145">Die Ergebnisse, die das Cmdlet **Out-File** bringt, entsprechen möglicherweise nicht Ihrer Erwartung, wenn Sie an herkömmliche Ausgabeumleitung denken.</span><span class="sxs-lookup"><span data-stu-id="6b615-145">The results of using the **Out-File** cmdlet may not be what you expect if you are used to traditional output redirection.</span></span> <span data-ttu-id="6b615-146">Um dessen Verhalten zu verstehen, müssen Sie den Kontext berücksichtigen, in dem das Cmdlet **Out-File** ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="6b615-146">To understand its behavior, you must be aware of the context in which the **Out-File** cmdlet operates.</span></span>

<span data-ttu-id="6b615-147">Standardmäßig erstellt das Cmdlet **Out-File** eine Unicode-Datei.</span><span class="sxs-lookup"><span data-stu-id="6b615-147">By default, the **Out-File** cmdlet creates a Unicode file.</span></span> <span data-ttu-id="6b615-148">Dies ist langfristig die beste Standardeinstellung, bedeutet aber, dass die Tools, die ASCII-Dateien erwarten, mit dem Standardausgabeformat nicht ordnungsgemäß funktionieren.</span><span class="sxs-lookup"><span data-stu-id="6b615-148">This is the best default in the long run, but it means that tools that expect ASCII files will not work correctly with the default output format.</span></span> <span data-ttu-id="6b615-149">Sie können das Standardausgabeformat in ASCII ändern, indem Sie den **Encoding**-Parameter verwenden:</span><span class="sxs-lookup"><span data-stu-id="6b615-149">You can change the default output format to ASCII by using the **Encoding** parameter:</span></span>

```
PS> Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

<span data-ttu-id="6b615-150">**Out-File** formatiert Dateiinhalt so, dass er wie Konsolenausgabe aussieht.</span><span class="sxs-lookup"><span data-stu-id="6b615-150">**Out-file** formats file contents to look like console output.</span></span> <span data-ttu-id="6b615-151">Dies bewirkt, dass die Ausgabe abgeschnitten wird, so wie dies in den meisten Fällen in einem Konsolenfenster erfolgt.</span><span class="sxs-lookup"><span data-stu-id="6b615-151">This causes the output to be truncated just as it is in a console window in most circumstances.</span></span> <span data-ttu-id="6b615-152">Angenommen, Sie führen den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="6b615-152">For example, if you run the following command:</span></span>

```
PS> Get-Command | Out-File -FilePath c:\temp\output.txt
```

<span data-ttu-id="6b615-153">Die Ausgabe sieht folgendermaßen aus:</span><span class="sxs-lookup"><span data-stu-id="6b615-153">The output will look like this:</span></span>

```
CommandType     Name                            Definition                     
-----------     ----                            ----------                     
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

<span data-ttu-id="6b615-154">Wenn Sie Ausgabe erhalten möchten, die keine Zeilenumbrüche erzwingt, um die Bildschirmbreite einzuhalten, verwenden Sie den **Width**-Parameter, um die Breite anzugeben.</span><span class="sxs-lookup"><span data-stu-id="6b615-154">To get output that does not force line wraps to match the screen width, you can use the **Width** parameter to specify line width.</span></span> <span data-ttu-id="6b615-155">Weil **Width** ein 32-Bit-Ganzzahl-Parameter ist, beträgt sein größter Wert 2147483647.</span><span class="sxs-lookup"><span data-stu-id="6b615-155">Because **Width** is a 32-bit integer parameter, the maximum value it can have is 2147483647.</span></span> <span data-ttu-id="6b615-156">Geben Sie Folgendes ein, um die Zeilenbreite auf diesen größten Wert festzulegen:</span><span class="sxs-lookup"><span data-stu-id="6b615-156">Type the following to set the line width to this maximum value:</span></span>

```
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

<span data-ttu-id="6b615-157">Das Cmdlet **Out-File** lässt sich dann am besten verwenden, wenn Sie Ausgabe so speichern möchten, wie sie in der Konsole angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6b615-157">The **Out-File** cmdlet is most useful when you want to save output as it would have displayed on the console.</span></span> <span data-ttu-id="6b615-158">Für eine genauere Steuerung des Ausgabeformats benötigen Sie Tools mit erweiterter Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="6b615-158">For finer control over output format, you need more advanced tools.</span></span> <span data-ttu-id="6b615-159">Diese Tools sind zusammen mit einigen Details zur Objektverarbeitung Gegenstand des nächsten Kapitels.</span><span class="sxs-lookup"><span data-stu-id="6b615-159">We will look at those in the next chapter, along with some details about object manipulation.</span></span>

