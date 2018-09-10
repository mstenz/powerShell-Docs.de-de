---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Verwenden von Variablen zum Speichern von Objekten
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: f4254199facb914c68a487b281b30070c35550a1
ms.sourcegitcommit: c170a1608d20d3c925d79c35fa208f650d014146
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2018
ms.locfileid: "43353217"
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="e800c-103">Verwenden von Variablen zum Speichern von Objekten</span><span class="sxs-lookup"><span data-stu-id="e800c-103">Using variables to store objects</span></span>

<span data-ttu-id="e800c-104">PowerShell arbeitet mit Objekten.</span><span class="sxs-lookup"><span data-stu-id="e800c-104">PowerShell works with objects.</span></span> <span data-ttu-id="e800c-105">PowerShell ermöglicht es Ihnen, benannte Objekt zu erstellen, sogenannte Variablen.</span><span class="sxs-lookup"><span data-stu-id="e800c-105">PowerShell lets you create named objects known as variables.</span></span>
<span data-ttu-id="e800c-106">Variablennamen können Unterstriche und beliebige andere alphanumerische Zeichen enthalten.</span><span class="sxs-lookup"><span data-stu-id="e800c-106">Variables names can include the underscore character can any alphanumeric characters.</span></span> <span data-ttu-id="e800c-107">Bei Verwendung in PowerShell wird eine Variable immer mit dem Zeichen \$, gefolgt von einem Variablennamen angegeben.</span><span class="sxs-lookup"><span data-stu-id="e800c-107">When used in PowerShell, a variable is always specified using the \$ character followed by variable name.</span></span>

## <a name="creating-a-variable"></a><span data-ttu-id="e800c-108">Erstellen einer Variablen</span><span class="sxs-lookup"><span data-stu-id="e800c-108">Creating a variable</span></span>

<span data-ttu-id="e800c-109">Sie können eine Variablen erstellen, indem Sie einen zulässigen Variablennamen eingeben:</span><span class="sxs-lookup"><span data-stu-id="e800c-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="e800c-110">Dieses Beispiel gibt kein Ergebnis zurück, weil `$loc` keinen Wert umfasst.</span><span class="sxs-lookup"><span data-stu-id="e800c-110">This example returns no result because `$loc` doesn't have a value.</span></span> <span data-ttu-id="e800c-111">Sie können im selben Schritt eine Variable erstellen und ihr einen Wert zuweisen.</span><span class="sxs-lookup"><span data-stu-id="e800c-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="e800c-112">PowerShell kann die Variable nur erstellen, wenn sie nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="e800c-112">PowerShell only creates the variable if it doesn't exist.</span></span>
<span data-ttu-id="e800c-113">Andernfalls wird der angegebene Wert der vorhandenen Variablen zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="e800c-113">Otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="e800c-114">Im folgenden Beispiel wird der aktuelle Standort in der Variablen `$loc` gespeichert:</span><span class="sxs-lookup"><span data-stu-id="e800c-114">The following example stores the current location in the variable `$loc`:</span></span>

```powershell
$loc = Get-Location
```

<span data-ttu-id="e800c-115">PowerShell zeigt keine Ausgabe an, wenn Sie diesen Befehl eingeben.</span><span class="sxs-lookup"><span data-stu-id="e800c-115">PowerShell displays no output when you type this command.</span></span> <span data-ttu-id="e800c-116">PowerShell sendet die Ausgabe von „Get-Location“ an `$loc`.</span><span class="sxs-lookup"><span data-stu-id="e800c-116">PowerShell sends the output of 'Get-Location' to `$loc`.</span></span> <span data-ttu-id="e800c-117">In PowerShell werden Daten, die nicht zugewiesen oder umgeleitet werden, an den Bildschirm gesendet.</span><span class="sxs-lookup"><span data-stu-id="e800c-117">In PowerShell, data that isn't assigned or redirected is sent to the screen.</span></span> <span data-ttu-id="e800c-118">Durch Eingabe von `$loc` wird Ihnen der aktuelle Standort angezeigt:</span><span class="sxs-lookup"><span data-stu-id="e800c-118">Typing `$loc` shows your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="e800c-119">Sie können `Get-Member` verwenden, um Informationen über die Inhalte der Variablen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e800c-119">You can use `Get-Member` to display information about the contents of variables.</span></span> <span data-ttu-id="e800c-120">`Get-Member` zeigt Ihnen, dass es sich bei `$loc` um ein **PathInfo**-Objekt handelt, ebenso wie die Ausgabe von `Get-Location`:</span><span class="sxs-lookup"><span data-stu-id="e800c-120">`Get-Member` shows you that `$loc` is a **PathInfo** object, just like the output from `Get-Location`:</span></span>

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a><span data-ttu-id="e800c-121">Bearbeiten von Variablen</span><span class="sxs-lookup"><span data-stu-id="e800c-121">Manipulating variables</span></span>

<span data-ttu-id="e800c-122">PowerShell stellt mehrere Befehle bereit, mit denen Variablen verwaltet werden können.</span><span class="sxs-lookup"><span data-stu-id="e800c-122">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="e800c-123">Eine vollständige Liste in einem lesbaren Format erhalten Sie, wenn Sie Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="e800c-123">You can see a complete listing in a readable form by typing:</span></span>

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="e800c-124">PowerShell erstellt außerdem verschiedene systemdefinierte Variablen.</span><span class="sxs-lookup"><span data-stu-id="e800c-124">PowerShell also creates several system-defined variables.</span></span> <span data-ttu-id="e800c-125">Mit dem Cmdlet `Remove-Variable` können Sie Variablen aus der aktuellen Sitzung löschen, die nicht von PowerShell kontrolliert werden.</span><span class="sxs-lookup"><span data-stu-id="e800c-125">You can use the `Remove-Variable` cmdlet to remove variables, which are not controlled by PowerShell, from the current session.</span></span> <span data-ttu-id="e800c-126">Geben Sie den folgenden Befehl ein, um alle Variablen zu löschen:</span><span class="sxs-lookup"><span data-stu-id="e800c-126">Type the following command to clear all variables:</span></span>

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="e800c-127">Nach dem Ausführen des vorstehenden Befehls zeigt das Cmdlet `Get-Variable` die PowerShell-Systemvariablen an.</span><span class="sxs-lookup"><span data-stu-id="e800c-127">After running the previous command, the `Get-Variable` cmdlet shows the PowerShell system variables.</span></span>

<span data-ttu-id="e800c-128">PowerShell erstellt außerdem ein Laufwerk „variable“.</span><span class="sxs-lookup"><span data-stu-id="e800c-128">PowerShell also creates a variable drive.</span></span> <span data-ttu-id="e800c-129">Verwenden Sie das folgende Beispiel, um alle PowerShell-Variablen mit dem Laufwerk „variable“ anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="e800c-129">Use the following example to display all PowerShell variables using the variable drive:</span></span>

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a><span data-ttu-id="e800c-130">Verwenden von Cmd.exe-Variablen</span><span class="sxs-lookup"><span data-stu-id="e800c-130">Using cmd.exe variables</span></span>

<span data-ttu-id="e800c-131">PowerShell kann die gleichen Umgebungsvariablen verwenden, die jedem Windows-Prozess zur Verfügung stehen, **cmd.exe** eingeschlossen.</span><span class="sxs-lookup"><span data-stu-id="e800c-131">PowerShell can use the same environment variables available to any Windows process, including **cmd.exe**.</span></span> <span data-ttu-id="e800c-132">Diese Variablen werden über ein Laufwerk namens `env:` verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="e800c-132">These variables are exposed through a drive named `env:`.</span></span> <span data-ttu-id="e800c-133">Sie können diese Variablen anzeigen, indem Sie den folgenden Befehl eingeben:</span><span class="sxs-lookup"><span data-stu-id="e800c-133">You can view these variables by typing the following command:</span></span>

```powershell
Get-ChildItem env:
```

<span data-ttu-id="e800c-134">Die standardmäßigen `*-Variable`-Cmdlets sind nicht auf die Arbeit mit Umgebungsvariablen ausgelegt.</span><span class="sxs-lookup"><span data-stu-id="e800c-134">The standard `*-Variable` cmdlets aren't designed to work with environment variables.</span></span> <span data-ttu-id="e800c-135">Auf Umgebungsvariablen wird über das Laufwerkpräfix `env:` zugegriffen.</span><span class="sxs-lookup"><span data-stu-id="e800c-135">Environment variables are accessed using the `env:` drive prefix.</span></span> <span data-ttu-id="e800c-136">Beispielsweise enthält die Variable **%SystemRoot%** in **cmd.exe** den Stammverzeichnisnamen des Betriebssystems.</span><span class="sxs-lookup"><span data-stu-id="e800c-136">For example, the **%SystemRoot%** variable in **cmd.exe** contains the operating system's root directory name.</span></span> <span data-ttu-id="e800c-137">In PowerShell verwenden Sie `$env:SystemRoot`, um auf denselben Wert zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="e800c-137">In PowerShell, you use `$env:SystemRoot` to access the same value.</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="e800c-138">Sie können auch Umgebungsvariablen in PowerShell erstellen und ändern.</span><span class="sxs-lookup"><span data-stu-id="e800c-138">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="e800c-139">Umgebungsvariablen in PowerShell unterliegen denselben Regeln für Umgebungsvariablen, die an beliebiger anderer Stelle im Betriebssystem verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e800c-139">Environment variables in PowerShell follow the same rules for environment variables used elsewhere in the operating system.</span></span> <span data-ttu-id="e800c-140">Durch das folgende Beispiel wird eine neue Umgebungsvariable erstellt:</span><span class="sxs-lookup"><span data-stu-id="e800c-140">The following example creates a new environment variable:</span></span>

```powershell
$env:LIB_PATH='/usr/local/lib'
```

<span data-ttu-id="e800c-141">Wenngleich dies nicht erforderlich ist, ist es gängige Praxis, für Namen von Umgebungsvariablen ausschließlich Großbuchstaben zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e800c-141">Though not required, is it common for environment variable names to use all uppercase letters.</span></span>