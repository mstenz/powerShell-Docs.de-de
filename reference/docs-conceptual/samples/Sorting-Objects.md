---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Sortieren von Objekten
ms.openlocfilehash: ed78e7e333f3468781c9cd96df2194fbdfebe753
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030770"
---
# <a name="sorting-objects"></a><span data-ttu-id="24a63-103">Sortieren von Objekten</span><span class="sxs-lookup"><span data-stu-id="24a63-103">Sorting Objects</span></span>

<span data-ttu-id="24a63-104">Sie können angezeigte Daten mithilfe des Cmdlets `Sort-Object` ordnen, damit sie sich einfacher überprüfen lassen.</span><span class="sxs-lookup"><span data-stu-id="24a63-104">We can organize displayed data to make it easier to scan by using the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="24a63-105">`Sort-Object` erhält den Namen von mindestens einer Eigenschaft, nach der sortiert werden soll, und gibt Daten zurück, die nach den Werten dieser Eigenschaften sortiert sind.</span><span class="sxs-lookup"><span data-stu-id="24a63-105">`Sort-Object` takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

## <a name="basic-sorting"></a><span data-ttu-id="24a63-106">Grundlegende Sortierung</span><span class="sxs-lookup"><span data-stu-id="24a63-106">Basic sorting</span></span>

<span data-ttu-id="24a63-107">Angenommen, Unterverzeichnisse und Dateien sollen im aktuellen Verzeichnis aufgelistet werden.</span><span class="sxs-lookup"><span data-stu-id="24a63-107">Consider the problem of listing subdirectories and files in the current directory.</span></span>
<span data-ttu-id="24a63-108">Wenn wir nach **LastWriteTime** und dann nach **Name** sortieren möchten, können wir dies durch die folgende Eingabe erreichen:</span><span class="sxs-lookup"><span data-stu-id="24a63-108">If we want to sort by **LastWriteTime** and then by **Name**, we can do it by typing:</span></span>

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

<span data-ttu-id="24a63-109">Sie können die Objekte auch in umgekehrter Reihenfolge sortieren, indem Sie den **Descending**-Umschaltparameter angeben.</span><span class="sxs-lookup"><span data-stu-id="24a63-109">You can also sort the objects in reverse order by specifying the **Descending** switch parameter.</span></span>

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

## <a name="using-hash-tables"></a><span data-ttu-id="24a63-110">Verwenden von Hashtabellen</span><span class="sxs-lookup"><span data-stu-id="24a63-110">Using hash tables</span></span>

<span data-ttu-id="24a63-111">Sie können verschiedene Eigenschaften in verschiedenen Reihenfolgen sortieren, indem Sie Hashtabellen in einem Array verwenden.</span><span class="sxs-lookup"><span data-stu-id="24a63-111">You can sort different properties in different orders by using hash tables in an array.</span></span>
<span data-ttu-id="24a63-112">Jede Hashtabelle verwendet einen **Expression**-Schlüssel, um den Namen der Eigenschaft als Zeichenfolge anzugeben, und einen **Ascending**- oder **Descending**-Schlüssel, um die Sortierreihenfolge durch `$true` oder `$false` anzugeben.</span><span class="sxs-lookup"><span data-stu-id="24a63-112">Each hash table uses an **Expression** key to specify the property name as string and an **Ascending** or **Descending** key to specify the sort order by `$true` or `$false`.</span></span>
<span data-ttu-id="24a63-113">Der **Expression**-Schlüssel ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="24a63-113">The **Expression** key is mandatory.</span></span>
<span data-ttu-id="24a63-114">Die **Ascending**- oder **Descending**-Schlüssel sind optional.</span><span class="sxs-lookup"><span data-stu-id="24a63-114">The **Ascending** or **Descending** key is optional.</span></span>

<span data-ttu-id="24a63-115">Das folgende Beispiel sortiert Objekte in absteigender **LastWriteTime**- und aufsteigender **Name**-Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="24a63-115">The following example sorts objects in descending **LastWriteTime** order and ascending **Name** order.</span></span>

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

<span data-ttu-id="24a63-116">Sie können auch einen Skriptblock auf den **Expression**-Schlüssel festlegen.</span><span class="sxs-lookup"><span data-stu-id="24a63-116">You can also set a scriptblock to the **Expression** key.</span></span>
<span data-ttu-id="24a63-117">Wenn Sie das Cmdlet `Sort-Object` ausführen, wird der Skriptblock ausgeführt und das Ergebnis für die Sortierung verwendet.</span><span class="sxs-lookup"><span data-stu-id="24a63-117">When running the `Sort-Object` cmdlet, the scriptblock is executed and the result is used for sorting.</span></span>

<span data-ttu-id="24a63-118">Das folgende Beispiel sortiert Objekte in absteigender Reihenfolge nach der Zeitspanne zwischen **CreationTime** und **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="24a63-118">The following example sorts objects in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

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

## <a name="tips"></a><span data-ttu-id="24a63-119">Tipps</span><span class="sxs-lookup"><span data-stu-id="24a63-119">Tips</span></span>

<span data-ttu-id="24a63-120">Sie können den **Property**-Parameternamen wie folgt auslassen:</span><span class="sxs-lookup"><span data-stu-id="24a63-120">You can omit the **Property** parameter name as following:</span></span>

```powershell
Sort-Object LastWriteTime, Name
```

<span data-ttu-id="24a63-121">Außerdem können Sie sich auch auf `Sort-Object` über den integrierten Alias `sort` beziehen:</span><span class="sxs-lookup"><span data-stu-id="24a63-121">Besides, you can refer to `Sort-Object` by its built-in alias, `sort`:</span></span>

```powershell
sort LastWriteTime, Name
```

<span data-ttu-id="24a63-122">Die Schlüssel in den Hashtabellen für die Sortierung können wie folgt abgekürzt werden:</span><span class="sxs-lookup"><span data-stu-id="24a63-122">The keys in the hash tables for sorting can be abbreviated as following:</span></span>

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

<span data-ttu-id="24a63-123">In diesem Beispiel steht das **e** für **Expression**, das **d** für **Descending** und das **a** für **Ascending**.</span><span class="sxs-lookup"><span data-stu-id="24a63-123">In this example, the **e** stands for **Expression**, the **d** stands for **Descending**, and the **a** stands for **Ascending**.</span></span>

<span data-ttu-id="24a63-124">Um die Lesbarkeit zu verbessern, können Sie die Hashtabellen in einer separaten Variablen platzieren:</span><span class="sxs-lookup"><span data-stu-id="24a63-124">To improve readability, you can place the hash tables into a separate variable:</span></span>

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```
