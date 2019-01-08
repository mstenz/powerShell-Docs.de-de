---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Sortieren von Objekten
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 06aa15d89888f1ecbe60b8e1dfb4efebb1d73673
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401187"
---
# <a name="sorting-objects"></a>Sortieren von Objekten

Wir können die angezeigte Daten zu erleichtern geordnet Organisieren der `Sort-Object` Cmdlet. `Sort-Object` erhält den Namen der eine oder mehrere Eigenschaften sortiert werden soll, und Daten, die nach den Werten dieser Eigenschaften sortiert zurückgegeben.

## <a name="basic-sorting"></a>Grundlegende Sortierung

Betrachten Sie das Problem der Auflistung, Unterverzeichnisse und Dateien im aktuellen Verzeichnis.
Wenn Sie möchten nach zu sortieren **"LastWriteTime"** und dann nach **Namen**, können wir durch Eingabe:

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

Sie können die Objekte auch in umgekehrter Reihenfolge sortieren, durch Angabe der **absteigend** switch-Parameter.

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

Sie können verschiedene Eigenschaften in unterschiedlicher Reihenfolge sortieren, mithilfe von Hashtabellen in einem Array.
Jeder Hashtabelle verwendet einen **Ausdruck** -Taste, um den Eigenschaftennamen als Zeichenfolge angeben und ein **aufsteigend** oder **absteigend** -Taste, um die Sortierreihenfolge von anzugeben `$true` oder `$false`.
Die **Ausdruck** Schlüssel ist erforderlich.
Die **aufsteigend** oder **absteigend** Schlüssel ist optional.

Im folgenden Beispiel werden Objekte in absteigender **"LastWriteTime"** Reihenfolge und aufsteigender **Namen** Reihenfolge.

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

Sie können auch einen Skriptblock festlegen, um die **Ausdruck** Schlüssel.
Bei der Ausführung der `Sort-Object` -Cmdlet, das "scriptblock" ausgeführt wird und das Ergebnis wird für die Sortierung verwendet.

Im folgenden Beispiel werden Objekte in absteigender Reihenfolge nach der Zeitspanne zwischen dem **CreationTime** und **"LastWriteTime"**.

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

Sie können Auslassen der **Eigenschaft** Parameternamen wie folgt:

```powershell
Sort-Object LastWriteTime, Name
```

Außerdem sehen Sie sich `Sort-Object` über den integrierten Alias `sort`:

```powershell
sort LastWriteTime, Name
```

Die Schlüssel in den Hashtabellen für die Sortierung können abgekürzt werden, wie folgt:

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

In diesem Beispiel die **e** steht für **Ausdruck**, **d** steht für **absteigend**, und die **eine** steht für **aufsteigend**.

Um die Lesbarkeit zu verbessern, können Sie die Hashtabellen in eine separate Variable platzieren:

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```