---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Verwenden von Variablen, um Objekte zu speichern
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 9a95d421fa2686608a565987c16fecc41c3c6d20
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2017
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="9c527-103">Verwenden von Variablen, um Objekte zu speichern</span><span class="sxs-lookup"><span data-stu-id="9c527-103">Using Variables to Store Objects</span></span>
<span data-ttu-id="9c527-104">PowerShell arbeitet mit Objekten.</span><span class="sxs-lookup"><span data-stu-id="9c527-104">PowerShell works with objects.</span></span> <span data-ttu-id="9c527-105">In PowerShell können Sie Variablen – eigentlich benannte Objekte – erstellen, um Ausgabe zur späteren Verwendung beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="9c527-105">PowerShell lets you create variables, essentially named objects, to preserve output for later use.</span></span> <span data-ttu-id="9c527-106">Wenn Sie mit dem Verwenden von Variablen in anderen Shells vertraut sind, sollten Sie daran denken, dass PowerShell-Variablen keine Texte, sondern Objekte sind.</span><span class="sxs-lookup"><span data-stu-id="9c527-106">If you are used to working with variables in other shells remember that PowerShell variables are objects, not text.</span></span>

<span data-ttu-id="9c527-107">Variablen werden immer mit dem Anfangszeichen $ angegeben und können jedes alphanumerische Zeichen und den Unterstrich in ihren Namen enthalten.</span><span class="sxs-lookup"><span data-stu-id="9c527-107">Variables are always specified with the initial character $, and can include any alphanumeric characters or the underscore in their names.</span></span>

### <a name="creating-a-variable"></a><span data-ttu-id="9c527-108">Erstellen einer Variablen</span><span class="sxs-lookup"><span data-stu-id="9c527-108">Creating a Variable</span></span>
<span data-ttu-id="9c527-109">Sie können eine Variablen erstellen, indem Sie einen zulässigen Variablennamen eingeben:</span><span class="sxs-lookup"><span data-stu-id="9c527-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="9c527-110">Dies gibt kein Ergebnis zurück, weil **$loc** keinen Wert hat.</span><span class="sxs-lookup"><span data-stu-id="9c527-110">This returns no result because **$loc** does not have a value.</span></span> <span data-ttu-id="9c527-111">Sie können im selben Schritt eine Variable erstellen und ihr einen Wert zuweisen.</span><span class="sxs-lookup"><span data-stu-id="9c527-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="9c527-112">PowerShell erstellt die Variable nur, wenn sie nicht vorhanden ist. Andernfalls weist Windows PowerShell der vorhandenen Variablen den angegebenen Wert zu.</span><span class="sxs-lookup"><span data-stu-id="9c527-112">PowerShell only creates the variable if it does not exist; otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="9c527-113">Um Ihren aktuellen Speicherort in der Variablen **$loc** zu speichern, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="9c527-113">To store your current location in the variable **$loc**, type:</span></span>

```
$loc = Get-Location
```

<span data-ttu-id="9c527-114">Es wird keine Ausgabe angezeigt, wenn Sie diesen Befehl eingeben, weil die Ausgabe an „$loc“ gesendet wird</span><span class="sxs-lookup"><span data-stu-id="9c527-114">There is no output displayed when you type this command because the output is sent to $loc.</span></span> <span data-ttu-id="9c527-115">In PowerShell ist angezeigte Ausgabe ein Nebeneffekt der Tatsache, dass Daten, die nicht anderweitig weitergeleitet werden, immer an den Bildschirm gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="9c527-115">In PowerShell, displayed output is a side effect of the fact that data, which is not otherwise directed, always gets sent to the screen.</span></span> <span data-ttu-id="9c527-116">Durch Eingeben von „$loc“ wird Ihr aktueller Speicherort angezeigt:</span><span class="sxs-lookup"><span data-stu-id="9c527-116">Typing $loc will show your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="9c527-117">Sie können **Get-Member** verwenden, um Informationen über die Inhalte der Variablen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="9c527-117">You can use **Get-Member** to display information about the contents of variables.</span></span> <span data-ttu-id="9c527-118">Wenn Sie „$loc“ in einer Pipeline an „Get-Member“ übergeben, sehen Sie, dass die Variable ein **PathInfo**-Objekt ist, genau wie die Ausgabe von „Get-Location“:</span><span class="sxs-lookup"><span data-stu-id="9c527-118">Piping $loc to Get-Member will show you that it is a **PathInfo** object, just like the output from Get-Location:</span></span>

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a><span data-ttu-id="9c527-119">Verwalten von Variablen</span><span class="sxs-lookup"><span data-stu-id="9c527-119">Manipulating Variables</span></span>
<span data-ttu-id="9c527-120">PowerShell stellt mehrere Befehle bereit, mit denen Variablen verwaltet werden können.</span><span class="sxs-lookup"><span data-stu-id="9c527-120">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="9c527-121">Eine vollständige Liste in einem lesbaren Format erhalten Sie, wenn Sie Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="9c527-121">You can see a complete listing in a readable form by typing:</span></span>

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="9c527-122">Zusätzlich zu den Variablen, die Sie in Ihrer aktuellen PowerShell-Sitzung erstellen, gibt es mehrere systemdefinierte Variablen.</span><span class="sxs-lookup"><span data-stu-id="9c527-122">In addition to the variables you create in your current PowerShell session, there are several system-defined variables.</span></span> <span data-ttu-id="9c527-123">Mit dem Cmdlet **Remove-Variable** können Sie alle Variablen löschen, die nicht von PowerShell kontrolliert werden.</span><span class="sxs-lookup"><span data-stu-id="9c527-123">You can use the **Remove-Variable** cmdlet to clear out all of the variables which are not controlled by PowerShell.</span></span> <span data-ttu-id="9c527-124">Geben Sie den folgenden Befehl ein, um alle Variablen zu löschen:</span><span class="sxs-lookup"><span data-stu-id="9c527-124">Type the following command to clear all variables:</span></span>

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="9c527-125">Daraufhin wird die nachstehende Bestätigungsaufforderung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9c527-125">This will produce the confirmation prompt you see below.</span></span>

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

<span data-ttu-id="9c527-126">Wenn Sie nun das Cmdlet **Get-Variable** ausführen, sehen Sie die verbliebenen PowerShell-Variablen.</span><span class="sxs-lookup"><span data-stu-id="9c527-126">If you then run the **Get-Variable** cmdlet, you will see the remaining PowerShell variables.</span></span> <span data-ttu-id="9c527-127">Da es auch ein PowerShell-Laufwerk für Variablen gibt, können Sie alle PowerShell-Variablen ebenfalls durch die folgende Eingabe anzeigen:</span><span class="sxs-lookup"><span data-stu-id="9c527-127">Since there is also a variable PowerShell drive, you can also display all PowerShell variables by typing:</span></span>

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a><span data-ttu-id="9c527-128">Verwenden von „Cmd.exe“-Variablen</span><span class="sxs-lookup"><span data-stu-id="9c527-128">Using Cmd.exe Variables</span></span>
<span data-ttu-id="9c527-129">PowerShell ist zwar nicht „Cmd.exe“, wird aber trotzdem in einer Befehlsshellumgebung ausgeführt und kann die Variablen verwenden, die in jeder Umgebung in Windows verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="9c527-129">Although PowerShell is not Cmd.exe, it runs in a command shell environment and can use the same variables available in any environment in Windows.</span></span> <span data-ttu-id="9c527-130">Diese Variablen werden über ein Laufwerk namens **env:** verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="9c527-130">These variables are exposed through a drive named **env**:.</span></span> <span data-ttu-id="9c527-131">Sie können diese Variablen anzeigen, indem Sie Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="9c527-131">You can view these variables by typing:</span></span>

```
Get-ChildItem env:
```

<span data-ttu-id="9c527-132">Obwohl die Standardcmdlets für Variablen nicht so konzipiert sind, dass sie mit **env:** funktionieren, können Sie sie weiterhin verwenden, indem Sie das Präfix **env:** angeben.</span><span class="sxs-lookup"><span data-stu-id="9c527-132">Although the standard variable cmdlets are not designed to work with **env:** variables, you can still use them by specifying the **env:** prefix.</span></span> <span data-ttu-id="9c527-133">Wenn Sie beispielsweise das Stammverzeichnis des Betriebssystems anzeigen möchten, können Sie die Befehlsshellvariable **%SystemRoot%** in PowerShell verwenden, indem Sie Folgende eingeben:</span><span class="sxs-lookup"><span data-stu-id="9c527-133">For example, to see the operating system root directory, you can use the command-shell **%SystemRoot%** variable from within PowerShell by typing:</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="9c527-134">Sie können auch Umgebungsvariablen in PowerShell erstellen und ändern.</span><span class="sxs-lookup"><span data-stu-id="9c527-134">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="9c527-135">Für Umgebungsvariablen, auf die über Windows PowerShell zugegriffen wird, gelten die normalen Regeln für Umgebungsvariablen wie an sonstigen Stellen in Windows.</span><span class="sxs-lookup"><span data-stu-id="9c527-135">Environment variables accessed from Windows PowerShell conform to the normal rules for environment variables elsewhere in Windows.</span></span>

