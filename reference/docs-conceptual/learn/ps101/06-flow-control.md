---
title: Flusssteuerung
description: PowerShell bietet Methoden zum Erstellen von Schleifen, zum Treffen von Entscheidungen und zur logischen Steuerung des Codeflusses in Skripts.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 4f0d7b7f5f3c12bb9475af5aed42b2d32cfbc14d
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84437991"
---
# <a name="chapter-6---flow-control"></a>Kapitel 6: Flusssteuerung

## <a name="scripting"></a>Skripterstellung

Wenn Sie nicht mehr nur noch PowerShell-Einzeiler, sondern ganze Skripts schreiben sollen, klingt dies erst einmal wesentlich komplizierter, als es tatsächlich ist. Ein Skript besteht aus denselben oder ähnlichen Befehlen, die Sie sonst interaktiv in der PowerShell-Konsole ausführen würden, außer dass diese jetzt als `.PS1`-Datei gespeichert werden. Es gibt einige Skriptkonstrukte, die Sie verwenden können, z. B. eine `foreach`-Schleife anstelle des Cmdlets `ForEach-Object`. Für Einsteiger können die Unterschiede verwirrend sein, besonders wenn Sie bedenken, dass `foreach` sowohl ein Skriptkonstrukt als auch ein Alias für das Cmdlet `ForEach-Object` ist.

## <a name="looping"></a>Schleifen

Eine der großartigen Eigenschaften von PowerShell ist, dass es, sobald Sie herausgefunden haben, wie Sie etwas mit einem Element machen, fast genauso einfach ist, dieselbe Aufgabe für Hunderte von Elementen auszuführen. Durchlaufen Sie die Elemente einfach in einer Schleife, indem Sie eine der zahlreichen verschiedenen Arten von Schleifen in PowerShell verwenden.

### <a name="foreach-object"></a>ForEach-Object

`ForEach-Object` ist ein Cmdlet zum Durchlaufen von Elementen in einer Pipeline, wie mit PowerShell-Einzeilern. `ForEach-Object` streamt die Objekte durch die Pipeline.

Obwohl der Parameter **Module** von `Get-Command` mehrere Werte akzeptiert, die Zeichenfolgen sind, akzeptiert er sie nur über die Pipelineeingabe mittels Eigenschaftsname oder über Parametereingaben. Wenn Sie im folgenden Szenario zwei Zeichenfolgen als Wert an `Get-Command` übergeben möchten, um sie mit dem Parameter **Module** zu verwenden, müssten Sie das Cmdlet `ForEach-Object` verwenden.

```powershell
'ActiveDirectory', 'SQLServer' |
   ForEach-Object {Get-Command -Module $_} |
     Group-Object -Property ModuleName -NoElement |
         Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  147 ActiveDirectory
   82 SqlServer
```

Im vorherigen Beispiel ist das aktuelle Objekt `$_`. Ab PowerShell-Version 3.0 kann anstelle von `$_` `$PSItem` verwendet werden. Ich bin aber der Meinung, dass die meisten erfahrenen PowerShell-Benutzer immer noch lieber `$_` verwenden, weil es abwärtskompatibel und weniger einzugeben ist.

Wenn Sie das Schlüsselwort `foreach` verwenden, müssen Sie zuerst alle Elemente im Arbeitsspeicher speichern, bevor Sie diese durchlaufen, was sich schwierig gestalten kann, wenn Sie nicht wissen, mit wie vielen Elementen Sie arbeiten.

```powershell
$ComputerName = 'DC01', 'WEB01'
foreach ($Computer in $ComputerName) {
  Get-ADComputer -Identity $Computer
}
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

Häufig ist eine Schleife wie `foreach` oder `ForEach-Object` erforderlich. Andernfalls erhalten Sie eine Fehlermeldung.

```powershell
Get-ADComputer -Identity 'DC01', 'WEB01'
```

```Output
Get-ADComputer : Cannot convert 'System.Object[]' to the type
'Microsoft.ActiveDirectory.Management.ADComputer' required by parameter 'Identity'.
Specified method is not supported.
At line:1 char:26
+ Get-ADComputer -Identity 'DC01', 'WEB01'
+                          ```````````````
    + CategoryInfo          : InvalidArgument: (:) [Get-ADComputer], ParameterBindingExc
   eption
    + FullyQualifiedErrorId : CannotConvertArgument,Microsoft.ActiveDirectory.Management
   .Commands.GetADComputer
```

In anderen Fällen können sie dieselben Ergebnisse erzielen und gleichzeitig die Schleife vollständig beseitigen. Sehen Sie in der Cmdlet-Hilfe nach, um Ihre Optionen herauszufinden.

```powershell
'DC01', 'WEB01' | Get-ADComputer
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

Wie Sie in den vorherigen Beispielen sehen können, akzeptiert der Parameter **Identity** für `Get-ADComputer` nur einen einzelnen Wert, wenn er über die Parametereingabe bereitgestellt wird, lässt aber mehrere Elemente zu, wenn die Eingabe über eine Pipelineeingabe bereitgestellt wird.

### <a name="for"></a>Für

Eine `for`-Schleife wird durchlaufen, während eine bestimmte Bedingung erfüllt (true) ist. Die `for`-Schleife verwende ich nicht häufig, aber sie hat ihre Berechtigung.

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
}
```

```Output
Sleeping for 1 seconds
Sleeping for 2 seconds
Sleeping for 3 seconds
Sleeping for 4 seconds
```

Im vorherigen Beispiel wird die Schleife viermal durchlaufen, beginnend mit der Zahl 1, und wird fortgesetzt, solange die Zählervariable `$i` kleiner als 5 ist. Sie setzt für insgesamt 10 Sekunden aus.

### <a name="do"></a>Sie sollten

Es gibt zwei verschiedene `do`-Schleifen in PowerShell. `Do Until` wird ausgeführt, während die angegebene Bedingung nicht erfüllt (false) ist.

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  }
  elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
until ($guess -eq $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
```

Das vorherige Beispiel ist ein Zahlenspiel, das solange fortgesetzt wird, bis der von Ihnen geschätzte Wert mit der Zahl übereinstimmt, die das Cmdlet `Get-Random` generiert hat.

`Do While` ist genau das Gegenteil. Sie wird ausgeführt, solange die angegebene Bedingung als „true“ ausgewertet wird.

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  } elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
while ($guess -ne $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
Too low!
What's your guess?: 4
```

Dieselben Ergebnisse werden mit einer `Do While`-Schleife erzielt, indem die Testbedingung in „ungleich“ umgekehrt wird.

`Do`-Schleifen werden immer mindestens einmal ausgeführt, weil die Bedingung am Ende der Schleife ausgewertet wird.

### <a name="while"></a>While

Ähnlich wie bei der `Do While`-Schleife, wird eine `While`-Schleife ausgeführt, solange die angegebene Bedingung erfüllt (true) ist. Der Unterschied besteht jedoch darin, dass eine `While`-Schleife die Bedingung am Anfang der Schleife auswertet, bevor überhaupt Code ausgeführt wird. Somit wird sie gar nicht ausgeführt, wenn die Bedingung als „false“ ausgewertet wird.

```powershell
$date = Get-Date -Date 'November 22'
while ($date.DayOfWeek -ne 'Thursday') {
  $date = $date.AddDays(1)
}
Write-Output $date
```

```Output
Thursday, November 23, 2017 12:00:00 AM
```

Im vorherigen Beispiel wird berechnet, an welchem Tag in den USA „Thanksgiving“ (Erntedankfest) ist. Dies ist immer am vierten Donnerstag im November. Die Schleife beginnt also mit dem 22. Tag im November und fügt einen Tag hinzu, solange der Wochentag nicht gleich Donnerstag ist. Wenn der 22. ein Donnerstag ist, wird die Schleife überhaupt nicht ausgeführt.

## <a name="break-continue-and-return"></a>Break, Continue und Return

`Break` dient dem Unterbrechen einer Schleife. Es wird auch häufig mit der `switch`-Anweisung verwendet.

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
  break
}
```

```Output
Sleeping for 1 seconds
```

Die im vorherigen Beispiel gezeigte `break`-Anweisung bewirkt, dass die Schleife bei der ersten Iterationen beendet wird.

„Continue“ ist so konzipiert, dass zur nächsten Iteration einer Schleife gesprungen wird.

```powershell
while ($i -lt 5) {
  $i += 1
  if ($i -eq 3) {
    continue
  }
  Write-Output $i
}
```

```Output
1
2
4
5
```

Das vorherige Beispiel gibt die Zahlen 1, 2, 4 und 5 aus. Es überspringt die Zahl 3 und fährt mit der nächsten Iteration der Schleife fort. Ähnlich wie bei `break`, unterbricht `continue` die Schleife, wenn auch nur für die aktuelle Iteration. Die Ausführung wird mit der nächsten Iteration fortgesetzt, anstatt die Schleife zu unterbrechen und zu beenden.

„Return“ ist so konzipiert, dass der vorhandene Bereich verlassen wird.

```powershell
$number = 1..10
foreach ($n in $number) {
  if ($n -ge 4) {
    Return $n
  }
}
```

```Output
4
```

Beachten Sie, dass im vorherigen Beispiel „return“ das erste Ergebnis ausgibt und dann die Schleife beendet. Eine gründlichere Erklärung der result-Anweisung finden Sie in einem meiner Blogartikel: [„Das PowerShell-Schlüsselwort ‚return‘“][].

## <a name="summary"></a>Zusammenfassung

In diesem Kapitel haben Sie die verschiedenen Arten von Schleifen kennengelernt, die in PowerShell vorhanden sind.

## <a name="review"></a>Überprüfung

1. Worin besteht der Unterschied zwischen dem `ForEach-Object`-Cmdlet und dem foreach-Skriptkonstrukt?
1. Worin besteht der primäre Vorteil bei der Verwendung einer While-Schleife anstelle einer „Do While“- oder „Do Until“-Schleife?
1. Worin unterscheiden sich break- und continue-Anweisungen?

## <a name="recommended-reading"></a>Empfohlene Lektüre

- [ForEach-Object][]
- [about_ForEach][]
- [about_For][]
- [about_Do][]
- [about_While][]
- [about_Break][]
- [about_Continue][]
- [about_Return][]

<!-- link references -->
[ForEach-Object]: /powershell/module/microsoft.powershell.core/foreach-object
[about_ForEach]: /powershell/module/microsoft.powershell.core/about/about_foreach
[about_For]: /powershell/module/microsoft.powershell.core/about/about_for
[about_Do]: /powershell/module/microsoft.powershell.core/about/about_do
[about_While]: /powershell/module/microsoft.powershell.core/about/about_while
[about_Break]: /powershell/module/microsoft.powershell.core/about/about_break
[about_Continue]: /powershell/module/microsoft.powershell.core/about/about_continue
[about_Return]: /powershell/module/microsoft.powershell.core/about/about_return
[„Das PowerShell-Schlüsselwort ‚return‘“]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/
