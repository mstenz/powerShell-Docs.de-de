---
title: Schreiben eines PowerShell-Skript Moduls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: b2a929a1724f77f0516ad24cfd90f6d6053ed19e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360689"
---
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="2bd38-102">Schreiben eines PowerShell-Skriptmoduls</span><span class="sxs-lookup"><span data-stu-id="2bd38-102">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="2bd38-103">Ein Skript Modul ist im Grunde ein beliebiges gültiges PowerShell-Skript, das in einer Erweiterung. psm1 gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="2bd38-103">A script module is essentially any valid PowerShell script saved in a .psm1 extension.</span></span> <span data-ttu-id="2bd38-104">Mit dieser Erweiterung kann die PowerShell-Engine eine Reihe von Regeln und Cmdlets für Ihre Datei verwenden.</span><span class="sxs-lookup"><span data-stu-id="2bd38-104">This extension allows the PowerShell engine to use a number of rules and cmdlets on your file.</span></span> <span data-ttu-id="2bd38-105">Die meisten dieser Funktionen sind verfügbar, damit Sie Ihren Code auf anderen Systemen installieren und die Bereichs Definition verwalten können.</span><span class="sxs-lookup"><span data-stu-id="2bd38-105">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="2bd38-106">Sie können auch eine Modul Manifest-Datei verwenden, die noch komplexere Installationen und Lösungen beschreiben kann.</span><span class="sxs-lookup"><span data-stu-id="2bd38-106">You can also use a module manifest file, which can describe even more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="2bd38-107">Schreiben eines PowerShell-Skript Moduls</span><span class="sxs-lookup"><span data-stu-id="2bd38-107">Writing a PowerShell Script Module</span></span>

<span data-ttu-id="2bd38-108">Sie erstellen ein Skript Modul, indem Sie ein gültiges PowerShell-Skript in einer psm1-Datei speichern und diese Datei dann in einem Verzeichnis speichern, in dem PowerShell Sie finden kann.</span><span class="sxs-lookup"><span data-stu-id="2bd38-108">You create a script module by saving a valid PowerShell script to a .psm1 file, and then saving that file in a directory located where PowerShell can find it.</span></span> <span data-ttu-id="2bd38-109">In diesem Ordner können Sie auch alle Ressourcen platzieren, die Sie zum Ausführen des Skripts benötigen, sowie eine Manifest-Datei, die die Funktionsweise des Moduls in PowerShell beschreibt.</span><span class="sxs-lookup"><span data-stu-id="2bd38-109">In that folder you can also place any resources you need to run your script, as well as a manifest file that describes to PowerShell how your module works.</span></span>

#### <a name="to-create-a-basic-powershell-module"></a><span data-ttu-id="2bd38-110">So erstellen Sie ein einfaches PowerShell-Modul</span><span class="sxs-lookup"><span data-stu-id="2bd38-110">To create a basic PowerShell Module</span></span>

1. <span data-ttu-id="2bd38-111">Erstellen Sie ein vorhandenes PowerShell-Skript, und speichern Sie das Skript mit der Erweiterung. psm1.</span><span class="sxs-lookup"><span data-stu-id="2bd38-111">Take an existing PowerShell script, and save the script with a .psm1 extension.</span></span>

   <span data-ttu-id="2bd38-112">Das Speichern eines Skripts mit der Erweiterung. psm1 bedeutet, dass Sie die Module-Cmdlets (z. b. [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)) darauf anwenden können.</span><span class="sxs-lookup"><span data-stu-id="2bd38-112">Saving a script with the .psm1 extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), on it.</span></span> <span data-ttu-id="2bd38-113">Diese Cmdlets sind hauptsächlich vorhanden, damit Sie Ihren Code problemlos auf die Systeme anderer Benutzer importieren und exportieren können.</span><span class="sxs-lookup"><span data-stu-id="2bd38-113">These cmdlets exist primarily so that you can easily import and export your code onto other user's systems.</span></span> <span data-ttu-id="2bd38-114">(Die alternative Lösung besteht darin, den Code auf anderen Systemen zu laden und dann in den aktiven Speicher zu stellen, was keine besonders skalierbare Lösung ist.) Weitere Informationen finden Sie im Abschnitt **Module-Cmdlets und Variablen** in [Windows PowerShell-Modulen](./understanding-a-windows-powershell-module.md) . Beachten Sie, dass standardmäßig alle Funktionen in Ihrem Skript für Benutzer zugänglich sind, die ihre psm1-Datei importieren, die Eigenschaften jedoch nicht.</span><span class="sxs-lookup"><span data-stu-id="2bd38-114">(The alternate solution would be to load up your code on other systems and then dot-source it into active memory, which isn't a particularly scalable solution.) For more information see the **Module Cmdlets and Variables** section in [Windows PowerShell Modules](./understanding-a-windows-powershell-module.md) Note that, by default, all functions in your script are accessible to users who import your .psm1 file, but properties are not.</span></span>

   <span data-ttu-id="2bd38-115">Ein PowerShell-Beispielskript mit dem Titel "`Show-Calendar`" ist am Ende dieses Themas verfügbar.</span><span class="sxs-lookup"><span data-stu-id="2bd38-115">An example PowerShell script, entitled `Show-Calendar`, is available at the end of this topic.</span></span>

   ```powershell
   function Show-Calendar {
   param(
       [DateTime] $start = [DateTime]::Today,
       [DateTime] $end = $start,
       $firstDayOfWeek,
       [int[]] $highlightDay,
       [string[]] $highlightDate = [DateTime]::Today.ToString()
       )

       #actual code for the function goes here see the end of the topic for the complete code sample
   }
   ```

2. <span data-ttu-id="2bd38-116">Um den Benutzer Zugriff auf bestimmte Funktionen oder Eigenschaften zu steuern, nennen Sie [Export-modulemember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) am Ende des Skripts.</span><span class="sxs-lookup"><span data-stu-id="2bd38-116">To control user access to certain functions or properties, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="2bd38-117">Der Beispielcode unten auf der Seite verfügt nur über eine Funktion, die standardmäßig verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="2bd38-117">The example code at the bottom of the page has only one function, which by default would be exposed.</span></span> <span data-ttu-id="2bd38-118">Es wird jedoch empfohlen, explizit die Funktionen aufzurufen, die Sie verfügbar machen möchten, wie im folgenden Code beschrieben:</span><span class="sxs-lookup"><span data-stu-id="2bd38-118">However, it is recommended that you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="2bd38-119">Sie können auch einschränken, was mithilfe eines Modul Manifests importiert wird.</span><span class="sxs-lookup"><span data-stu-id="2bd38-119">You can also restrict what is imported using a module manifest.</span></span> <span data-ttu-id="2bd38-120">Weitere Informationen finden Sie unter [Importieren eines PowerShell-Moduls](./importing-a-powershell-module.md) und Gewusst [wie: Schreiben eines PowerShell-Modul Manifests](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="2bd38-120">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="2bd38-121">Wenn Sie über Module verfügen, die von Ihrem eigenen Modul geladen werden müssen, können Sie Sie mit einem `Import-Module`-aufzurufenden Befehl am oberen Rand Ihres eigenen Moduls verwenden.</span><span class="sxs-lookup"><span data-stu-id="2bd38-121">If you have modules that your own module needs to have loaded, you can use them with a call to `Import-Module`, at the top of your own module.</span></span>

   <span data-ttu-id="2bd38-122">`Import-Module` ist ein Cmdlet, das ein Ziel Modul auf ein System importiert.</span><span class="sxs-lookup"><span data-stu-id="2bd38-122">`Import-Module` is a cmdlet that imports a targeted module onto a system.</span></span> <span data-ttu-id="2bd38-123">Daher wird Sie auch zu einem späteren Zeitpunkt in der Prozedur verwendet, um auch ein eigenes Modul zu installieren.</span><span class="sxs-lookup"><span data-stu-id="2bd38-123">As such, it is also used at a later point in the procedure to install your own module as well.</span></span> <span data-ttu-id="2bd38-124">Im Beispielcode unten auf dieser Seite werden keine Import Module verwendet.</span><span class="sxs-lookup"><span data-stu-id="2bd38-124">The sample code at the bottom of this page does not use any import modules.</span></span> <span data-ttu-id="2bd38-125">Wenn dies der Fall ist, werden Sie jedoch am Anfang der Datei aufgelistet, wie im folgenden Code beschrieben:</span><span class="sxs-lookup"><span data-stu-id="2bd38-125">If it did, however, they would be listed at the top of the file, as described in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="2bd38-126">Um das Modul im PowerShell-Hilfesystem zu beschreiben, können Sie in der Datei entweder Standard Hilfe Kommentare verwenden oder eine zusätzliche Hilfedatei erstellen.</span><span class="sxs-lookup"><span data-stu-id="2bd38-126">To describe your module to the PowerShell Help system, you can either use standard help comments inside the file, or create an additional Help file.</span></span>

   <span data-ttu-id="2bd38-127">Das Codebeispiel am Ende dieses Themas enthält die Hilfe Informationen in den Kommentaren.</span><span class="sxs-lookup"><span data-stu-id="2bd38-127">The code sample at the bottom of this topic includes the help information in the comments.</span></span> <span data-ttu-id="2bd38-128">Sie können auch erweiterte XML-Dateien schreiben, die zusätzlichen Hilfe Inhalt enthalten.</span><span class="sxs-lookup"><span data-stu-id="2bd38-128">You could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="2bd38-129">Weitere Informationen finden Sie unter [Schreiben der Hilfe für Windows PowerShell-Module](./writing-help-for-windows-powershell-modules.md).</span><span class="sxs-lookup"><span data-stu-id="2bd38-129">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="2bd38-130">Wenn Sie über zusätzliche Module, XML-Dateien oder andere Inhalte verfügen, die Sie mit Ihrem Modul verpacken möchten, können Sie dies mit einem Modul Manifest tun.</span><span class="sxs-lookup"><span data-stu-id="2bd38-130">If you have additional modules, XML files, or other content you want to package up with your module, you can do so with a module manifest.</span></span>

   <span data-ttu-id="2bd38-131">Ein Modul Manifest ist eine Datei, die die Namen anderer Module, Verzeichnis Layouts, Versionsnummern, Autoren Daten und andere Informationen enthält.</span><span class="sxs-lookup"><span data-stu-id="2bd38-131">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="2bd38-132">PowerShell verwendet die Modul Manifest-Datei, um die Projekt Mappe zu organisieren und bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="2bd38-132">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="2bd38-133">Aufgrund der relativ einfachen Natur dieses Beispiels war eine Manifest-Datei jedoch nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="2bd38-133">However, due to the relatively simple nature of this example, a manifest file was not needed.</span></span> <span data-ttu-id="2bd38-134">Weitere Informationen finden Sie unter [Modul Manifeste](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="2bd38-134">For more information, see [Module Manifests](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="2bd38-135">Um das Modul zu installieren und auszuführen, speichern Sie das Modul in einem der entsprechenden PowerShell-Pfade, und führen Sie `Import-Module` aus.</span><span class="sxs-lookup"><span data-stu-id="2bd38-135">To install and run your module, save the module to one of the appropriate PowerShell paths, and make a call to `Import-Module`.</span></span>

   <span data-ttu-id="2bd38-136">Die Pfade, in denen Sie das Modul installieren können, befinden sich in der globalen Variable `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="2bd38-136">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="2bd38-137">Ein allgemeiner Pfad zum Speichern eines Moduls auf einem System wäre beispielsweise `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="2bd38-137">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="2bd38-138">Stellen Sie sicher, dass Sie einen Ordner erstellen, in dem das Modul vorhanden ist, selbst wenn es sich nur um eine psm1-Datei handelt.</span><span class="sxs-lookup"><span data-stu-id="2bd38-138">Be sure to create a folder for your module to exist in, even if it is only a single .psm1 file.</span></span> <span data-ttu-id="2bd38-139">Wenn Sie das Modul nicht in einem dieser Pfade gespeichert haben, müssen Sie den Speicherort des Moduls im `Import-Module`-aufrufswert übergeben.</span><span class="sxs-lookup"><span data-stu-id="2bd38-139">If you did not save your module to one of these paths, you would have to pass in the location of your module in the call to `Import-Module`.</span></span> <span data-ttu-id="2bd38-140">(Andernfalls ist PowerShell nicht in der Lage, Sie zu finden.) Ab PowerShell 3,0 müssen Sie das Modul nicht explizit importieren, wenn Sie es in einem der PowerShell-Modul Pfade abgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="2bd38-140">(Otherwise, PowerShell would not be able to find it.) Starting with PowerShell 3.0, if you have placed your module in one of the PowerShell module paths, you do not need to explicitly import it.</span></span> <span data-ttu-id="2bd38-141">Das Modul wird automatisch geladen, wenn ein Benutzer die Funktion aufruft.</span><span class="sxs-lookup"><span data-stu-id="2bd38-141">You module is automatically loaded when a user calls your function.</span></span>
   <span data-ttu-id="2bd38-142">Weitere Informationen zum Modulpfad finden Sie unter [Importieren eines PowerShell-Moduls und einer](./importing-a-powershell-module.md) [psmodulepath-Umgebungsvariablen](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="2bd38-142">For more information on the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [PSModulePath Environment Variable](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="2bd38-143">Wenn Sie ein Modul aus dem aktiven Dienst entfernen möchten, führen Sie den Befehl [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)aus.</span><span class="sxs-lookup"><span data-stu-id="2bd38-143">To remove a module from active service, make a call to [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

   <span data-ttu-id="2bd38-144">Beachten Sie, dass [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) das Modul aus dem aktiven Speicher entfernt. es löscht es nicht tatsächlich aus dem Speicherort, an dem Sie die Moduldateien gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="2bd38-144">Note that [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) removes your module from active memory - it does not actually delete it from where you saved the module files.</span></span>

### <a name="show-calendar-code-example"></a><span data-ttu-id="2bd38-145">Codebeispiel für Anzeige Kalender</span><span class="sxs-lookup"><span data-stu-id="2bd38-145">Show-Calendar code example</span></span>

<span data-ttu-id="2bd38-146">Das folgende Beispiel ist ein einfaches Skript Modul, das eine einzelne Funktion mit dem Namen "`Show-Calendar`" enthält.</span><span class="sxs-lookup"><span data-stu-id="2bd38-146">The following example is a simple script module that contains a single function named `Show-Calendar`.</span></span>
<span data-ttu-id="2bd38-147">Diese Funktion zeigt eine visuelle Darstellung eines Kalenders an.</span><span class="sxs-lookup"><span data-stu-id="2bd38-147">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="2bd38-148">Außerdem enthält das Beispiel die PowerShell-Hilfe Zeichenfolgen für Syntax, Beschreibung, Parameterwerte und Beispiel.</span><span class="sxs-lookup"><span data-stu-id="2bd38-148">In addition, the sample contains the PowerShell Help strings for the synopsis, description, parameter values, and example.</span></span> <span data-ttu-id="2bd38-149">Beachten Sie, dass die letzte Codezeile sicherstellt, dass die `Show-Calendar`-Funktion als Modulmember exportiert wird, wenn das Modul importiert wird.</span><span class="sxs-lookup"><span data-stu-id="2bd38-149">Note that the last line of code ensures that the `Show-Calendar` function is exported as a module member when the module is imported.</span></span>

```powershell
<#
 .Synopsis
  Displays a visual representation of a calendar.

 .Description
  Displays a visual representation of a calendar. This function supports multiple months
  and lets you highlight specific date ranges or days.

 .Parameter Start
  The first month to display.

 .Parameter End
  The last month to display.

 .Parameter FirstDayOfWeek
  The day of the month on which the week begins.

 .Parameter HighlightDay
  Specific days (numbered) to highlight. Used for date ranges like (25..31).
  Date ranges are specified by the Windows PowerShell range syntax. These dates are
  enclosed in square brackets.

 .Parameter HighlightDate
  Specific days (named) to highlight. These dates are surrounded by asterisks.

 .Example
   # Show a default display of this month.
   Show-Calendar

 .Example
   # Display a date range.
   Show-Calendar -Start "March, 2010" -End "May, 2010"

 .Example
   # Highlight a range of days.
   Show-Calendar -HighlightDay (1..10 + 22) -HighlightDate "December 25, 2008"
#>
function Show-Calendar {
param(
    [DateTime] $start = [DateTime]::Today,
    [DateTime] $end = $start,
    $firstDayOfWeek,
    [int[]] $highlightDay,
    [string[]] $highlightDate = [DateTime]::Today.ToString()
    )

## Determine the first day of the start and end months.
$start = New-Object DateTime $start.Year,$start.Month,1
$end = New-Object DateTime $end.Year,$end.Month,1

## Convert the highlighted dates into real dates.
[DateTime[]] $highlightDate = [DateTime[]] $highlightDate

## Retrieve the DateTimeFormat information so that the
## calendar can be manipulated.
$dateTimeFormat  = (Get-Culture).DateTimeFormat
if($firstDayOfWeek)
{
    $dateTimeFormat.FirstDayOfWeek = $firstDayOfWeek
}

$currentDay = $start

## Process the requested months.
while($start -le $end)
{
    ## Return to an earlier point in the function if the first day of the month
    ## is in the middle of the week.
    while($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek)
    {
        $currentDay = $currentDay.AddDays(-1)
    }

    ## Prepare to store information about this date range.
    $currentWeek = New-Object PsObject
    $dayNames = @()
    $weeks = @()

    ## Continue processing dates until the function reaches the end of the month.
    ## The function continues until the week is completed with
    ## days from the next month.
    while(($currentDay -lt $start.AddMonths(1)) -or
        ($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek))
    {
        ## Determine the day names to use to label the columns.
        $dayName = "{0:ddd}" -f $currentDay
        if($dayNames -notcontains $dayName)
        {
            $dayNames += $dayName
        }

        ## Pad the day number for display, highlighting if necessary.
        $displayDay = " {0,2} " -f $currentDay.Day

        ## Determine whether to highlight a specific date.
        if($highlightDate)
        {
            $compareDate = New-Object DateTime $currentDay.Year,
                $currentDay.Month,$currentDay.Day
            if($highlightDate -contains $compareDate)
            {
                $displayDay = "*" + ("{0,2}" -f $currentDay.Day) + "*"
            }
        }

        ## Otherwise, highlight as part of a date range.
        if($highlightDay -and ($highlightDay[0] -eq $currentDay.Day))
        {
            $displayDay = "[" + ("{0,2}" -f $currentDay.Day) + "]"
            $null,$highlightDay = $highlightDay
        }

        ## Add the day of the week and the day of the month as note properties.
        $currentWeek | Add-Member NoteProperty $dayName $displayDay

        ## Move to the next day of the month.
        $currentDay = $currentDay.AddDays(1)

        ## If the function reaches the next week, store the current week
        ## in the week list and continue.
        if($currentDay.DayOfWeek -eq $dateTimeFormat.FirstDayOfWeek)
        {
            $weeks += $currentWeek
            $currentWeek = New-Object PsObject
        }
    }

    ## Format the weeks as a table.
    $calendar = $weeks | Format-Table $dayNames -AutoSize | Out-String

    ## Add a centered header.
    $width = ($calendar.Split("`n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " `n" + $padding + $header + "`n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
