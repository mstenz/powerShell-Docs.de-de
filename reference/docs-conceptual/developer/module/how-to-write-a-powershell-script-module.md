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
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416260"
---
# <a name="how-to-write-a-powershell-script-module"></a>Schreiben eines PowerShell-Skriptmoduls

Ein Skript Modul ist ein beliebiges gültiges PowerShell-Skript, das in einer `.psm1` Erweiterung gespeichert wird. Diese Erweiterung ermöglicht es der PowerShell-Engine, Regeln und Modul-Cmdlets für Ihre Datei zu verwenden. Die meisten dieser Funktionen sind verfügbar, damit Sie Ihren Code auf anderen Systemen installieren und die Bereichs Definition verwalten können. Sie können auch eine Modul Manifest-Datei verwenden, in der komplexere Installationen und Lösungen beschrieben werden.

## <a name="writing-a-powershell-script-module"></a>Schreiben eines PowerShell-Skript Moduls

Um ein Skript Modul zu erstellen, speichern Sie ein gültiges PowerShell-Skript in einer `.psm1` Datei. Das Skript und das Verzeichnis, in dem es gespeichert ist, müssen denselben Namen verwenden. Beispielsweise wird ein Skript mit dem Namen `MyPsScript.psm1` in einem Verzeichnis mit dem Namen `MyPsScript`gespeichert.

Das Modul Verzeichnis muss sich in einem in `$env:PSModulePath`angegebenen Pfad befinden. Das Verzeichnis des Moduls kann alle Ressourcen enthalten, die zum Ausführen des Skripts erforderlich sind, sowie eine Modul Manifest-Datei, die die Funktionsweise des Moduls in PowerShell beschreibt.

## <a name="create-a-basic-powershell-module"></a>Erstellen eines einfachen PowerShell-Moduls

In den folgenden Schritten wird beschrieben, wie Sie ein PowerShell-Modul erstellen.

1. Speichern Sie ein PowerShell-Skript mit einer `.psm1`-Erweiterung. Verwenden Sie den gleichen Namen für das Skript und das Verzeichnis, in dem das Skript gespeichert ist.

   Das Speichern eines Skripts mit der `.psm1`-Erweiterung bedeutet, dass Sie die Module-Cmdlets, z. b. [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), verwenden können. Die Module-Cmdlets sind hauptsächlich vorhanden, damit Sie Ihren Code in die Systeme anderer Benutzer importieren und exportieren können. Die alternative Lösung besteht darin, den Code auf andere Systeme zu laden und dann in den aktiven Speicher zu stellen, der keine skalierbare Lösung ist. Weitere Informationen finden Sie Untergrund Legendes zu [einem Windows PowerShell-Modul](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables).
   Wenn Benutzer ihre `.psm1` Datei importieren, können standardmäßig alle Funktionen in Ihrem Skript aufgerufen werden, aber Variablen sind nicht verfügbar.

   Ein Beispiel für ein PowerShell-Skript mit dem Titel `Show-Calendar`finden Sie am Ende dieses Artikels.

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

2. Um den Benutzer Zugriff auf bestimmte Funktionen oder Variablen zu steuern, nennen Sie [Export-modulemember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) am Ende des Skripts.

   Der Beispielcode am Ende des Artikels verfügt nur über eine Funktion, die standardmäßig verfügbar gemacht wird. Es wird jedoch empfohlen, explizit die Funktionen aufzurufen, die Sie verfügbar machen möchten, wie im folgenden Code beschrieben:

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   Sie können einschränken, was mithilfe eines Modul Manifests importiert wurde. Weitere Informationen finden Sie unter [Importieren eines PowerShell-Moduls](./importing-a-powershell-module.md) und Gewusst [wie: Schreiben eines PowerShell-Modul Manifests](./how-to-write-a-powershell-module-manifest.md).

3. Wenn Sie über Module verfügen, die ihr eigenes Modul laden muss, können Sie `Import-Module`am Anfang des Moduls verwenden.

   Mit dem-Cmdlet "`Import-Module`" wird ein Ziel Modul auf ein System importiert, und es kann zu einem späteren Zeitpunkt in der Prozedur verwendet werden, um ein eigenes Modul zu installieren. Im Beispielcode am Ende dieses Artikels werden keine Import Module verwendet. Wenn dies der Fall ist, werden Sie am Anfang der Datei aufgelistet, wie im folgenden Code gezeigt:

   ```powershell
   Import-Module GenericModule
   ```

4. Um das Modul im PowerShell-Hilfesystem zu beschreiben, können Sie in der Datei entweder Standard Hilfe Kommentare verwenden oder eine zusätzliche Hilfedatei erstellen.

   Das Codebeispiel am Ende dieses Artikels enthält die Hilfe Informationen in den Kommentaren. Sie können auch erweiterte XML-Dateien schreiben, die zusätzlichen Hilfe Inhalt enthalten. Weitere Informationen finden Sie unter [Schreiben der Hilfe für Windows PowerShell-Module](./writing-help-for-windows-powershell-modules.md).

5. Wenn Sie über zusätzliche Module, XML-Dateien oder andere Inhalte verfügen, die Sie mit Ihrem Modul verpacken möchten, können Sie ein Modul Manifest verwenden.

   Ein Modul Manifest ist eine Datei, die die Namen anderer Module, Verzeichnis Layouts, Versionsnummern, Autoren Daten und andere Informationen enthält. PowerShell verwendet die Modul Manifest-Datei, um die Projekt Mappe zu organisieren und bereitzustellen. Weitere Informationen finden Sie unter Gewusst [wie: Schreiben eines PowerShell-Modul Manifests](./how-to-write-a-powershell-module-manifest.md).

6. Um das Modul zu installieren und auszuführen, speichern Sie das Modul in einem der entsprechenden PowerShell-Pfade, und verwenden Sie `Import-Module`.

   Die Pfade, in denen Sie das Modul installieren können, befinden sich in der `$env:PSModulePath` globalen Variablen. Beispielsweise wäre ein allgemeiner Pfad zum Speichern eines Moduls auf einem System `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>`. Stellen Sie sicher, dass Sie ein Verzeichnis für Ihr Modul erstellen, das denselben Namen wie das Skript Modul verwendet, selbst wenn es sich nur um eine einzige `.psm1` Datei handelt. Wenn Sie das Modul nicht in einem dieser Pfade gespeichert haben, müssen Sie den Speicherort des Moduls im `Import-Module` Befehl angeben. Andernfalls könnte PowerShell das Modul nicht finden.

   Ab PowerShell 3,0 müssen Sie das Modul nicht explizit importieren, wenn Sie das Modul in einem der PowerShell-Modul Pfade abgelegt haben. Das Modul wird automatisch geladen, wenn ein Benutzer die Funktion aufruft. Weitere Informationen zum Modulpfad finden Sie unter [Importieren eines PowerShell-Moduls](./importing-a-powershell-module.md) und [Ändern des psmodulepath-Installations Pfads](./modifying-the-psmodulepath-installation-path.md).

7. Wenn Sie ein Modul aus dem aktiven Dienst in der aktuellen PowerShell-Sitzung entfernen möchten, verwenden Sie " [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)".

   > [!NOTE]
   > `Remove-Module` entfernt ein Modul aus der aktuellen PowerShell-Sitzung, deinstalliert das Modul jedoch nicht oder löscht die Datei des Moduls.

## <a name="show-calendar-code-example"></a>Codebeispiel für Anzeige Kalender

Das folgende Beispiel ist ein Skript Modul, das eine einzelne Funktion mit dem Namen `Show-Calendar`enthält. Diese Funktion zeigt eine visuelle Darstellung eines Kalenders an. Das Beispiel enthält die PowerShell-Hilfe Zeichenfolgen für die Syntax, die Beschreibung, die Parameterwerte und den Code. Wenn das Modul importiert wird, stellt der `Export-ModuleMember`-Befehl sicher, dass die `Show-Calendar`-Funktion als Modulmember exportiert wird.

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
