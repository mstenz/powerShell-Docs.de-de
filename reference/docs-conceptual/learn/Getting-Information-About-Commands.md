---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Abrufen von Informationen zu Befehlen
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 7af83e3a0e776d96e580b442430357b4ea063a72
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057705"
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="f2649-103">Abrufen von Informationen zu Befehlen</span><span class="sxs-lookup"><span data-stu-id="f2649-103">Getting information about commands</span></span>

<span data-ttu-id="f2649-104">Das PowerShell-Cmdlet `Get-Command` zeigt Befehle an, die in Ihrer aktuellen Sitzung verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="f2649-104">The PowerShell `Get-Command` displays commands that are available in your current session.</span></span>
<span data-ttu-id="f2649-105">Wenn Sie das Cmdlet `Get-Command` ausführen, wird eine Ausgabe wie die folgende angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f2649-105">When you run the `Get-Command` cmdlet, you see something similar to the following output:</span></span>

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

<span data-ttu-id="f2649-106">Diese Ausgabe hat große Ähnlichkeit mit der Hilfe-Ausgabe von **Cmd.exe**: Sie umfasst eine tabellarische Zusammenfassung der internen Befehle.</span><span class="sxs-lookup"><span data-stu-id="f2649-106">This output looks a lot like the Help output of **cmd.exe**: a tabular summary of internal commands.</span></span> <span data-ttu-id="f2649-107">Im Auszug der oben gezeigten `Get-Command`-Befehlsausgabe weist jeder aufgeführte Befehl den Befehlstyp (CommandType) „Cmdlet“ auf.</span><span class="sxs-lookup"><span data-stu-id="f2649-107">In the excerpt of the `Get-Command` command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="f2649-108">Ein Cmdlet ist ein systeminterner PowerShell-Befehlstyp.</span><span class="sxs-lookup"><span data-stu-id="f2649-108">A cmdlet is PowerShell's intrinsic command type.</span></span> <span data-ttu-id="f2649-109">Dieser Typ entspricht in etwa Befehlen wie `dir` und `cd` in **cmd.exe** oder den integrierten Befehlen von Unix-Shells wie Bash.</span><span class="sxs-lookup"><span data-stu-id="f2649-109">This type corresponds roughly to commands like `dir` and `cd` in **cmd.exe** or the built-in commands of Unix shells like bash.</span></span>

<span data-ttu-id="f2649-110">Das Cmdlet `Get-Command` umfasst einen Parameter **Syntax**, der die Syntax jedes Cmdlets zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="f2649-110">The `Get-Command` cmdlet has a **Syntax** parameter that returns syntax of each cmdlet.</span></span> <span data-ttu-id="f2649-111">Das folgende Beispiel zeigt, wie Sie die Syntax für das Cmdlet `Get-Help` abrufen:</span><span class="sxs-lookup"><span data-stu-id="f2649-111">The following example shows how to get the syntax of the `Get-Help` cmdlet:</span></span>

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a><span data-ttu-id="f2649-112">Anzeigen verfügbarer Befehle nach Typ</span><span class="sxs-lookup"><span data-stu-id="f2649-112">Displaying available command by type</span></span>

<span data-ttu-id="f2649-113">Mit dem Befehl `Get-Command` werden nur die Cmdlets in der aktuellen Sitzung aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="f2649-113">The `Get-Command` command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="f2649-114">PowerShell unterstützt tatsächlich verschiedene weitere Befehlstypen:</span><span class="sxs-lookup"><span data-stu-id="f2649-114">PowerShell actually supports several other types of commands:</span></span>

- <span data-ttu-id="f2649-115">Aliase</span><span class="sxs-lookup"><span data-stu-id="f2649-115">Aliases</span></span>
- <span data-ttu-id="f2649-116">Funktionen</span><span class="sxs-lookup"><span data-stu-id="f2649-116">Functions</span></span>
- <span data-ttu-id="f2649-117">Scripts</span><span class="sxs-lookup"><span data-stu-id="f2649-117">Scripts</span></span>

<span data-ttu-id="f2649-118">Externe ausführbare Dateien oder Dateien mit einem registrierten Dateityphandler werden ebenfalls als Befehle klassifiziert.</span><span class="sxs-lookup"><span data-stu-id="f2649-118">External executable files, or files that have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="f2649-119">Um alle Befehle in der Sitzung aufzurufen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="f2649-119">To get all commands in the session, type:</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="f2649-120">Diese Liste schließt externe Dateien in Ihrem Suchpfad ein, deshalb kann sie Tausende von Elementen enthalten.</span><span class="sxs-lookup"><span data-stu-id="f2649-120">This list includes external commands in your search path so it can contain thousands of items.</span></span>
<span data-ttu-id="f2649-121">Es ist sinnvoller, einen reduzierten Satz von Befehlen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f2649-121">It is more useful to look at a reduced set of commands.</span></span>

> [!NOTE]
> <span data-ttu-id="f2649-122">Das Sternchen (\*) wird zum Abgleich mit Platzhalterzeichen in PowerShell-Befehlsargumenten verwendet.</span><span class="sxs-lookup"><span data-stu-id="f2649-122">The asterisk (\*) is used for wildcard matching in PowerShell command arguments.</span></span> <span data-ttu-id="f2649-123">\* bedeutet „Abgleichen mit einem oder mehreren beliebigen Zeichen“.</span><span class="sxs-lookup"><span data-stu-id="f2649-123">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="f2649-124">Beispielsweise können Sie `Get-Command a*` eingeben, um nach allen Befehlen zu suchen, die mit dem Buchstaben „a“ beginnen.</span><span class="sxs-lookup"><span data-stu-id="f2649-124">You can type `Get-Command a*` to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="f2649-125">Anders als beim Platzhalterabgleich in **cmd.exe** führt das PowerShell-Platzhalterzeichen auch einen Abgleich mit einem Punkt durch.</span><span class="sxs-lookup"><span data-stu-id="f2649-125">Unlike wildcard matching in **cmd.exe**, PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="f2649-126">Verwenden Sie den **CommandType**-Parameter von `Get-Command`, um die nativen Befehle anderer Typen</span><span class="sxs-lookup"><span data-stu-id="f2649-126">Use the **CommandType** parameter of `Get-Command` to get native commands of other types.</span></span>
<span data-ttu-id="f2649-127">abzurufen.</span><span class="sxs-lookup"><span data-stu-id="f2649-127">cmdlet.</span></span>

<span data-ttu-id="f2649-128">Geben Sie Folgendes ein, um Befehlsaliase abzurufen, bei denen es sich um die zugewiesenen Spitznamen von Befehlen handelt:</span><span class="sxs-lookup"><span data-stu-id="f2649-128">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```powershell
Get-Command -CommandType Alias
```

<span data-ttu-id="f2649-129">Um die Funktionen in der aktuellen Sitzung abzurufen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="f2649-129">To get the functions in the current session, type:</span></span>

```powershell
Get-Command -CommandType Function
```

<span data-ttu-id="f2649-130">Um Skripts im Suchpfad von PowerShell anzuzeigen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="f2649-130">To display scripts in PowerShell's search path, type:</span></span>

```powershell
Get-Command -CommandType Script
```