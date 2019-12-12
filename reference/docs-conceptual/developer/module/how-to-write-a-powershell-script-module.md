---
title: Schreiben eines PowerShell-Skript Moduls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: 7742eedd67283535b9e5898adc74d0d48faf68fe
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416260"
---
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="4488c-102">Schreiben eines PowerShell-Skriptmoduls</span><span class="sxs-lookup"><span data-stu-id="4488c-102">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="4488c-103">Ein Skript Modul ist ein beliebiges gültiges PowerShell-Skript, das in einer `.psm1` Erweiterung gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="4488c-103">A script module is any valid PowerShell script saved in a `.psm1` extension.</span></span> <span data-ttu-id="4488c-104">Diese Erweiterung ermöglicht es der PowerShell-Engine, Regeln und Modul-Cmdlets für Ihre Datei zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="4488c-104">This extension allows the PowerShell engine to use rules and module cmdlets on your file.</span></span> <span data-ttu-id="4488c-105">Die meisten dieser Funktionen sind verfügbar, damit Sie Ihren Code auf anderen Systemen installieren und die Bereichs Definition verwalten können.</span><span class="sxs-lookup"><span data-stu-id="4488c-105">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="4488c-106">Sie können auch eine Modul Manifest-Datei verwenden, in der komplexere Installationen und Lösungen beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="4488c-106">You can also use a module manifest file, which describes more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="4488c-107">Schreiben eines PowerShell-Skript Moduls</span><span class="sxs-lookup"><span data-stu-id="4488c-107">Writing a PowerShell script module</span></span>

<span data-ttu-id="4488c-108">Um ein Skript Modul zu erstellen, speichern Sie ein gültiges PowerShell-Skript in einer `.psm1` Datei.</span><span class="sxs-lookup"><span data-stu-id="4488c-108">To create a script module, save a valid PowerShell script to a `.psm1` file.</span></span> <span data-ttu-id="4488c-109">Das Skript und das Verzeichnis, in dem es gespeichert ist, müssen denselben Namen verwenden.</span><span class="sxs-lookup"><span data-stu-id="4488c-109">The script and the directory where it's stored must use the same name.</span></span> <span data-ttu-id="4488c-110">Beispielsweise wird ein Skript mit dem Namen `MyPsScript.psm1` in einem Verzeichnis mit dem Namen `MyPsScript`gespeichert.</span><span class="sxs-lookup"><span data-stu-id="4488c-110">For example, a script named `MyPsScript.psm1` is stored in a directory named `MyPsScript`.</span></span>

<span data-ttu-id="4488c-111">Das Modul Verzeichnis muss sich in einem in `$env:PSModulePath`angegebenen Pfad befinden.</span><span class="sxs-lookup"><span data-stu-id="4488c-111">The module's directory needs to be in a path specified in `$env:PSModulePath`.</span></span> <span data-ttu-id="4488c-112">Das Verzeichnis des Moduls kann alle Ressourcen enthalten, die zum Ausführen des Skripts erforderlich sind, sowie eine Modul Manifest-Datei, die die Funktionsweise des Moduls in PowerShell beschreibt.</span><span class="sxs-lookup"><span data-stu-id="4488c-112">The module's directory can contain any resources that are needed to run the script, and a module manifest file that describes to PowerShell how your module works.</span></span>

## <a name="create-a-basic-powershell-module"></a><span data-ttu-id="4488c-113">Erstellen eines einfachen PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="4488c-113">Create a basic PowerShell module</span></span>

<span data-ttu-id="4488c-114">In den folgenden Schritten wird beschrieben, wie Sie ein PowerShell-Modul erstellen.</span><span class="sxs-lookup"><span data-stu-id="4488c-114">The following steps describe how to create a PowerShell module.</span></span>

1. <span data-ttu-id="4488c-115">Speichern Sie ein PowerShell-Skript mit einer `.psm1`-Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="4488c-115">Save a PowerShell script with a `.psm1` extension.</span></span> <span data-ttu-id="4488c-116">Verwenden Sie den gleichen Namen für das Skript und das Verzeichnis, in dem das Skript gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="4488c-116">Use the same name for the script and the directory where the script is saved.</span></span>

   <span data-ttu-id="4488c-117">Das Speichern eines Skripts mit der `.psm1`-Erweiterung bedeutet, dass Sie die Module-Cmdlets, z. b. [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), verwenden können.</span><span class="sxs-lookup"><span data-stu-id="4488c-117">Saving a script with the `.psm1` extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span> <span data-ttu-id="4488c-118">Die Module-Cmdlets sind hauptsächlich vorhanden, damit Sie Ihren Code in die Systeme anderer Benutzer importieren und exportieren können.</span><span class="sxs-lookup"><span data-stu-id="4488c-118">The module cmdlets exist primarily so that you can import and export your code onto other user's systems.</span></span> <span data-ttu-id="4488c-119">Die alternative Lösung besteht darin, den Code auf andere Systeme zu laden und dann in den aktiven Speicher zu stellen, der keine skalierbare Lösung ist.</span><span class="sxs-lookup"><span data-stu-id="4488c-119">The alternate solution would be to load your code on other systems and then dot-source it into active memory, which isn't a scalable solution.</span></span> <span data-ttu-id="4488c-120">Weitere Informationen finden Sie Untergrund Legendes zu [einem Windows PowerShell-Modul](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables).</span><span class="sxs-lookup"><span data-stu-id="4488c-120">For more information, see [Understanding a Windows PowerShell Module](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables).</span></span>
   <span data-ttu-id="4488c-121">Wenn Benutzer ihre `.psm1` Datei importieren, können standardmäßig alle Funktionen in Ihrem Skript aufgerufen werden, aber Variablen sind nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="4488c-121">By default, when users import your `.psm1` file, all functions in your script are accessible, but variables aren't.</span></span>

   <span data-ttu-id="4488c-122">Ein Beispiel für ein PowerShell-Skript mit dem Titel `Show-Calendar`finden Sie am Ende dieses Artikels.</span><span class="sxs-lookup"><span data-stu-id="4488c-122">An example PowerShell script, entitled `Show-Calendar`, is available at the end of this article.</span></span>

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

2. <span data-ttu-id="4488c-123">Um den Benutzer Zugriff auf bestimmte Funktionen oder Variablen zu steuern, nennen Sie [Export-modulemember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) am Ende des Skripts.</span><span class="sxs-lookup"><span data-stu-id="4488c-123">To control user access to certain functions or variables, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="4488c-124">Der Beispielcode am Ende des Artikels verfügt nur über eine Funktion, die standardmäßig verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="4488c-124">The example code at the bottom of the article has only one function, which by default would be exposed.</span></span> <span data-ttu-id="4488c-125">Es wird jedoch empfohlen, explizit die Funktionen aufzurufen, die Sie verfügbar machen möchten, wie im folgenden Code beschrieben:</span><span class="sxs-lookup"><span data-stu-id="4488c-125">However, it's recommended you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="4488c-126">Sie können einschränken, was mithilfe eines Modul Manifests importiert wurde.</span><span class="sxs-lookup"><span data-stu-id="4488c-126">You can restrict what's imported using a module manifest.</span></span> <span data-ttu-id="4488c-127">Weitere Informationen finden Sie unter [Importieren eines PowerShell-Moduls](./importing-a-powershell-module.md) und Gewusst [wie: Schreiben eines PowerShell-Modul Manifests](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="4488c-127">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="4488c-128">Wenn Sie über Module verfügen, die ihr eigenes Modul laden muss, können Sie `Import-Module`am Anfang des Moduls verwenden.</span><span class="sxs-lookup"><span data-stu-id="4488c-128">If you have modules that your own module needs to load, you can use `Import-Module`, at the top of your module.</span></span>

   <span data-ttu-id="4488c-129">Mit dem-Cmdlet "`Import-Module`" wird ein Ziel Modul auf ein System importiert, und es kann zu einem späteren Zeitpunkt in der Prozedur verwendet werden, um ein eigenes Modul zu installieren.</span><span class="sxs-lookup"><span data-stu-id="4488c-129">The `Import-Module` cmdlet imports a targeted module onto a system, and can be used at a later point in the procedure to install your own module.</span></span> <span data-ttu-id="4488c-130">Im Beispielcode am Ende dieses Artikels werden keine Import Module verwendet.</span><span class="sxs-lookup"><span data-stu-id="4488c-130">The sample code at the bottom of this article doesn't use any import modules.</span></span> <span data-ttu-id="4488c-131">Wenn dies der Fall ist, werden Sie am Anfang der Datei aufgelistet, wie im folgenden Code gezeigt:</span><span class="sxs-lookup"><span data-stu-id="4488c-131">But if it did, they would be listed at the top of the file, as shown in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="4488c-132">Um das Modul im PowerShell-Hilfesystem zu beschreiben, können Sie in der Datei entweder Standard Hilfe Kommentare verwenden oder eine zusätzliche Hilfedatei erstellen.</span><span class="sxs-lookup"><span data-stu-id="4488c-132">To describe your module to the PowerShell Help system, you can either use standard help comments inside the file, or create an additional Help file.</span></span>

   <span data-ttu-id="4488c-133">Das Codebeispiel am Ende dieses Artikels enthält die Hilfe Informationen in den Kommentaren.</span><span class="sxs-lookup"><span data-stu-id="4488c-133">The code sample at the bottom of this article includes the help information in the comments.</span></span> <span data-ttu-id="4488c-134">Sie können auch erweiterte XML-Dateien schreiben, die zusätzlichen Hilfe Inhalt enthalten.</span><span class="sxs-lookup"><span data-stu-id="4488c-134">You could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="4488c-135">Weitere Informationen finden Sie unter [Schreiben der Hilfe für Windows PowerShell-Module](./writing-help-for-windows-powershell-modules.md).</span><span class="sxs-lookup"><span data-stu-id="4488c-135">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="4488c-136">Wenn Sie über zusätzliche Module, XML-Dateien oder andere Inhalte verfügen, die Sie mit Ihrem Modul verpacken möchten, können Sie ein Modul Manifest verwenden.</span><span class="sxs-lookup"><span data-stu-id="4488c-136">If you have additional modules, XML files, or other content you want to package with your module, you can use a module manifest.</span></span>

   <span data-ttu-id="4488c-137">Ein Modul Manifest ist eine Datei, die die Namen anderer Module, Verzeichnis Layouts, Versionsnummern, Autoren Daten und andere Informationen enthält.</span><span class="sxs-lookup"><span data-stu-id="4488c-137">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="4488c-138">PowerShell verwendet die Modul Manifest-Datei, um die Projekt Mappe zu organisieren und bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="4488c-138">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="4488c-139">Weitere Informationen finden Sie unter Gewusst [wie: Schreiben eines PowerShell-Modul Manifests](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="4488c-139">For more information, see [How to write a PowerShell module manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="4488c-140">Um das Modul zu installieren und auszuführen, speichern Sie das Modul in einem der entsprechenden PowerShell-Pfade, und verwenden Sie `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="4488c-140">To install and run your module, save the module to one of the appropriate PowerShell paths, and use `Import-Module`.</span></span>

   <span data-ttu-id="4488c-141">Die Pfade, in denen Sie das Modul installieren können, befinden sich in der `$env:PSModulePath` globalen Variablen.</span><span class="sxs-lookup"><span data-stu-id="4488c-141">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="4488c-142">Beispielsweise wäre ein allgemeiner Pfad zum Speichern eines Moduls auf einem System `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="4488c-142">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="4488c-143">Stellen Sie sicher, dass Sie ein Verzeichnis für Ihr Modul erstellen, das denselben Namen wie das Skript Modul verwendet, selbst wenn es sich nur um eine einzige `.psm1` Datei handelt.</span><span class="sxs-lookup"><span data-stu-id="4488c-143">Be sure to create a directory for your module that uses the same name as the script module, even if it's only a single `.psm1` file.</span></span> <span data-ttu-id="4488c-144">Wenn Sie das Modul nicht in einem dieser Pfade gespeichert haben, müssen Sie den Speicherort des Moduls im `Import-Module` Befehl angeben.</span><span class="sxs-lookup"><span data-stu-id="4488c-144">If you didn't save your module to one of these paths, you would have to specify the module's location in the `Import-Module` command.</span></span> <span data-ttu-id="4488c-145">Andernfalls könnte PowerShell das Modul nicht finden.</span><span class="sxs-lookup"><span data-stu-id="4488c-145">Otherwise, PowerShell wouldn't be able to find the module.</span></span>

   <span data-ttu-id="4488c-146">Ab PowerShell 3,0 müssen Sie das Modul nicht explizit importieren, wenn Sie das Modul in einem der PowerShell-Modul Pfade abgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="4488c-146">Starting with PowerShell 3.0, if you've placed your module in one of the PowerShell module paths, you don't need to explicitly import it.</span></span> <span data-ttu-id="4488c-147">Das Modul wird automatisch geladen, wenn ein Benutzer die Funktion aufruft.</span><span class="sxs-lookup"><span data-stu-id="4488c-147">Your module is automatically loaded when a user calls your function.</span></span> <span data-ttu-id="4488c-148">Weitere Informationen zum Modulpfad finden Sie unter [Importieren eines PowerShell-Moduls](./importing-a-powershell-module.md) und [Ändern des psmodulepath-Installations Pfads](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="4488c-148">For more information about the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [Modifying the PSModulePath Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="4488c-149">Wenn Sie ein Modul aus dem aktiven Dienst in der aktuellen PowerShell-Sitzung entfernen möchten, verwenden Sie " [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)".</span><span class="sxs-lookup"><span data-stu-id="4488c-149">To remove a module from active service in the current PowerShell session, use [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

   > [!NOTE]
   > <span data-ttu-id="4488c-150">`Remove-Module` entfernt ein Modul aus der aktuellen PowerShell-Sitzung, deinstalliert das Modul jedoch nicht oder löscht die Datei des Moduls.</span><span class="sxs-lookup"><span data-stu-id="4488c-150">`Remove-Module` removes a module from the current PowerShell session, but doesn't uninstall the module or delete the module's files.</span></span>

## <a name="show-calendar-code-example"></a><span data-ttu-id="4488c-151">Codebeispiel für Anzeige Kalender</span><span class="sxs-lookup"><span data-stu-id="4488c-151">Show-Calendar code example</span></span>

<span data-ttu-id="4488c-152">Das folgende Beispiel ist ein Skript Modul, das eine einzelne Funktion mit dem Namen `Show-Calendar`enthält.</span><span class="sxs-lookup"><span data-stu-id="4488c-152">The following example is a script module that contains a single function named `Show-Calendar`.</span></span> <span data-ttu-id="4488c-153">Diese Funktion zeigt eine visuelle Darstellung eines Kalenders an.</span><span class="sxs-lookup"><span data-stu-id="4488c-153">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="4488c-154">Das Beispiel enthält die PowerShell-Hilfe Zeichenfolgen für die Syntax, die Beschreibung, die Parameterwerte und den Code.</span><span class="sxs-lookup"><span data-stu-id="4488c-154">The sample contains the PowerShell Help strings for the synopsis, description, parameter values, and code.</span></span> <span data-ttu-id="4488c-155">Wenn das Modul importiert wird, stellt der `Export-ModuleMember`-Befehl sicher, dass die `Show-Calendar`-Funktion als Modulmember exportiert wird.</span><span class="sxs-lookup"><span data-stu-id="4488c-155">When the module is imported, the `Export-ModuleMember` command ensures that the `Show-Calendar` function is exported as a module member.</span></span>

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
