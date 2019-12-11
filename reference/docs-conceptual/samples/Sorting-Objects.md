---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Sortieren von Objekten
ms.openlocfilehash: ed78e7e333f3468781c9cd96df2194fbdfebe753
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030770"
---
# <a name="sorting-objects"></a>Sortieren von Objekten

Sie können angezeigte Daten mithilfe des Cmdlets `Sort-Object` ordnen, damit sie sich einfacher überprüfen lassen. `Sort-Object` erhält den Namen von mindestens einer Eigenschaft, nach der sortiert werden soll, und gibt Daten zurück, die nach den Werten dieser Eigenschaften sortiert sind.

## <a name="basic-sorting"></a>Grundlegende Sortierung

Angenommen, Unterverzeichnisse und Dateien sollen im aktuellen Verzeichnis aufgelistet werden.
Wenn wir nach **LastWriteTime** und dann nach **Name** sortieren möchten, können wir dies durch die folgende Eingabe erreichen:

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
11/6/2017 10:10:11 AM  .localization-config
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:15 AM  tests
6/6/2018 7:58:59 PM    CONTRIBUTING.md
6/6/2018 7:58:59 PM    README.md
...
```

Sie können die Objekte auch in umgekehrter Reihenfolge sortieren, indem Sie den **Descending**-Umschaltparameter angeben.

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name -Descending |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  reference
12/1/2018 10:13:50 PM  dsc
...
6/6/2018 7:58:59 PM    README.md
6/6/2018 7:58:59 PM    CONTRIBUTING.md
11/6/2017 10:10:15 AM  tests
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  .localization-config
```

## <a name="using-hash-tables"></a>Verwenden von Hashtabellen

Sie können verschiedene Eigenschaften in verschiedenen Reihenfolgen sortieren, indem Sie Hashtabellen in einem Array verwenden.
Jede Hashtabelle verwendet einen **Expression**-Schlüssel, um den Namen der Eigenschaft als Zeichenfolge anzugeben, und einen **Ascending**- oder **Descending**-Schlüssel, um die Sortierreihenfolge durch `$true` oder `$false` anzugeben.
Der **Expression**-Schlüssel ist erforderlich.
Die **Ascending**- oder **Descending**-Schlüssel sind optional.

Das folgende Beispiel sortiert Objekte in absteigender **LastWriteTime**- und aufsteigender **Name**-Reihenfolge.

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = 'LastWriteTime'; Descending = $true }, @{ Expression = 'Name'; Ascending = $true } |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  dsc
12/1/2018 10:13:50 PM  reference
11/29/2018 6:56:01 PM  .openpublishing.redirection.json
11/29/2018 6:56:01 PM  gallery
11/24/2018 10:33:22 AM developer
11/20/2018 7:22:19 PM  .markdownlint.json
...
```

Sie können auch einen Skriptblock auf den **Expression**-Schlüssel festlegen.
Wenn Sie das Cmdlet `Sort-Object` ausführen, wird der Skriptblock ausgeführt und das Ergebnis für die Sortierung verwendet.

Das folgende Beispiel sortiert Objekte in absteigender Reihenfolge nach der Zeitspanne zwischen **CreationTime** und **LastWriteTime**.

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = { $_.LastWriteTime - $_.CreationTime }; Descending = $true } |
  Format-Table -Property LastWriteTime, CreationTime
```

```output
LastWriteTime          CreationTime
-------------          ------------
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:15 AM
11/3/2018 9:58:17 AM   11/6/2017 10:10:11 AM
10/26/2018 4:50:21 PM  11/6/2017 10:10:11 AM
11/17/2018 1:10:57 PM  11/29/2017 5:48:30 PM
11/12/2018 6:29:53 PM  12/7/2017 7:57:07 PM
...
```

## <a name="tips"></a>Tipps

Sie können den **Property**-Parameternamen wie folgt auslassen:

```powershell
Sort-Object LastWriteTime, Name
```

Außerdem können Sie sich auch auf `Sort-Object` über den integrierten Alias `sort` beziehen:

```powershell
sort LastWriteTime, Name
```

Die Schlüssel in den Hashtabellen für die Sortierung können wie folgt abgekürzt werden:

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

In diesem Beispiel steht das **e** für **Expression**, das **d** für **Descending** und das **a** für **Ascending**.

Um die Lesbarkeit zu verbessern, können Sie die Hashtabellen in einer separaten Variablen platzieren:

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```
