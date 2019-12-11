---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Verwenden von Variablen, um Objekte zu speichern
ms.openlocfilehash: 2d20d84e48d3f68cab5c1ffa05d689b46415ebc8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030374"
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="ea995-103">Verwenden von Variablen zum Speichern von Objekten</span><span class="sxs-lookup"><span data-stu-id="ea995-103">Using variables to store objects</span></span>

<span data-ttu-id="ea995-104">PowerShell arbeitet mit Objekten.</span><span class="sxs-lookup"><span data-stu-id="ea995-104">PowerShell works with objects.</span></span> <span data-ttu-id="ea995-105">PowerShell ermöglicht es Ihnen, benannte Objekt zu erstellen, sogenannte Variablen.</span><span class="sxs-lookup"><span data-stu-id="ea995-105">PowerShell lets you create named objects known as variables.</span></span>
<span data-ttu-id="ea995-106">Variablennamen können Unterstriche und beliebige andere alphanumerische Zeichen enthalten.</span><span class="sxs-lookup"><span data-stu-id="ea995-106">Variable names can include the underscore character and any alphanumeric characters.</span></span> <span data-ttu-id="ea995-107">Bei Verwendung in PowerShell wird eine Variable immer mit dem Zeichen \$, gefolgt von einem Variablennamen angegeben.</span><span class="sxs-lookup"><span data-stu-id="ea995-107">When used in PowerShell, a variable is always specified using the \$ character followed by variable name.</span></span>

## <a name="creating-a-variable"></a><span data-ttu-id="ea995-108">Erstellen einer Variablen</span><span class="sxs-lookup"><span data-stu-id="ea995-108">Creating a variable</span></span>

<span data-ttu-id="ea995-109">Sie können eine Variablen erstellen, indem Sie einen zulässigen Variablennamen eingeben:</span><span class="sxs-lookup"><span data-stu-id="ea995-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="ea995-110">Dieses Beispiel gibt kein Ergebnis zurück, weil `$loc` keinen Wert umfasst.</span><span class="sxs-lookup"><span data-stu-id="ea995-110">This example returns no result because `$loc` doesn't have a value.</span></span> <span data-ttu-id="ea995-111">Sie können im selben Schritt eine Variable erstellen und ihr einen Wert zuweisen.</span><span class="sxs-lookup"><span data-stu-id="ea995-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="ea995-112">PowerShell kann die Variable nur erstellen, wenn sie nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="ea995-112">PowerShell only creates the variable if it doesn't exist.</span></span>
<span data-ttu-id="ea995-113">Andernfalls wird der angegebene Wert der vorhandenen Variablen zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="ea995-113">Otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="ea995-114">Im folgenden Beispiel wird der aktuelle Standort in der Variablen `$loc` gespeichert:</span><span class="sxs-lookup"><span data-stu-id="ea995-114">The following example stores the current location in the variable `$loc`:</span></span>

```powershell
$loc = Get-Location
```

<span data-ttu-id="ea995-115">PowerShell zeigt keine Ausgabe an, wenn Sie diesen Befehl eingeben.</span><span class="sxs-lookup"><span data-stu-id="ea995-115">PowerShell displays no output when you type this command.</span></span> <span data-ttu-id="ea995-116">PowerShell sendet die Ausgabe von „Get-Location“ an `$loc`.</span><span class="sxs-lookup"><span data-stu-id="ea995-116">PowerShell sends the output of 'Get-Location' to `$loc`.</span></span> <span data-ttu-id="ea995-117">In PowerShell werden Daten, die nicht zugewiesen oder umgeleitet werden, an den Bildschirm gesendet.</span><span class="sxs-lookup"><span data-stu-id="ea995-117">In PowerShell, data that isn't assigned or redirected is sent to the screen.</span></span> <span data-ttu-id="ea995-118">Durch Eingabe von `$loc` wird Ihnen der aktuelle Standort angezeigt:</span><span class="sxs-lookup"><span data-stu-id="ea995-118">Typing `$loc` shows your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="ea995-119">Sie können `Get-Member` verwenden, um Informationen über die Inhalte der Variablen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="ea995-119">You can use `Get-Member` to display information about the contents of variables.</span></span> <span data-ttu-id="ea995-120">`Get-Member` zeigt Ihnen, dass es sich bei `$loc` um ein **PathInfo**-Objekt handelt, ebenso wie die Ausgabe von `Get-Location`:</span><span class="sxs-lookup"><span data-stu-id="ea995-120">`Get-Member` shows you that `$loc` is a **PathInfo** object, just like the output from `Get-Location`:</span></span>

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

## <a name="manipulating-variables"></a><span data-ttu-id="ea995-121">Bearbeiten von Variablen</span><span class="sxs-lookup"><span data-stu-id="ea995-121">Manipulating variables</span></span>

<span data-ttu-id="ea995-122">PowerShell stellt mehrere Befehle bereit, mit denen Variablen verwaltet werden können.</span><span class="sxs-lookup"><span data-stu-id="ea995-122">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="ea995-123">Eine vollständige Liste in einem lesbaren Format erhalten Sie, wenn Sie Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="ea995-123">You can see a complete listing in a readable form by typing:</span></span>

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="ea995-124">PowerShell erstellt außerdem verschiedene systemdefinierte Variablen.</span><span class="sxs-lookup"><span data-stu-id="ea995-124">PowerShell also creates several system-defined variables.</span></span> <span data-ttu-id="ea995-125">Mit dem Cmdlet `Remove-Variable` können Sie Variablen aus der aktuellen Sitzung löschen, die nicht von PowerShell kontrolliert werden.</span><span class="sxs-lookup"><span data-stu-id="ea995-125">You can use the `Remove-Variable` cmdlet to remove variables, which are not controlled by PowerShell, from the current session.</span></span> <span data-ttu-id="ea995-126">Geben Sie den folgenden Befehl ein, um alle Variablen zu löschen:</span><span class="sxs-lookup"><span data-stu-id="ea995-126">Type the following command to clear all variables:</span></span>

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="ea995-127">Nach dem Ausführen des vorstehenden Befehls zeigt das Cmdlet `Get-Variable` die PowerShell-Systemvariablen an.</span><span class="sxs-lookup"><span data-stu-id="ea995-127">After running the previous command, the `Get-Variable` cmdlet shows the PowerShell system variables.</span></span>

<span data-ttu-id="ea995-128">PowerShell erstellt außerdem ein Laufwerk „variable“.</span><span class="sxs-lookup"><span data-stu-id="ea995-128">PowerShell also creates a variable drive.</span></span> <span data-ttu-id="ea995-129">Verwenden Sie das folgende Beispiel, um alle PowerShell-Variablen mit dem Laufwerk „variable“ anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="ea995-129">Use the following example to display all PowerShell variables using the variable drive:</span></span>

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a><span data-ttu-id="ea995-130">Verwenden von Cmd.exe-Variablen</span><span class="sxs-lookup"><span data-stu-id="ea995-130">Using cmd.exe variables</span></span>

<span data-ttu-id="ea995-131">PowerShell kann die gleichen Umgebungsvariablen verwenden, die jedem Windows-Prozess zur Verfügung stehen, **cmd.exe** eingeschlossen.</span><span class="sxs-lookup"><span data-stu-id="ea995-131">PowerShell can use the same environment variables available to any Windows process, including **cmd.exe**.</span></span> <span data-ttu-id="ea995-132">Diese Variablen werden über ein Laufwerk namens `env:` verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="ea995-132">These variables are exposed through a drive named `env:`.</span></span> <span data-ttu-id="ea995-133">Sie können diese Variablen anzeigen, indem Sie den folgenden Befehl eingeben:</span><span class="sxs-lookup"><span data-stu-id="ea995-133">You can view these variables by typing the following command:</span></span>

```powershell
Get-ChildItem env:
```

<span data-ttu-id="ea995-134">Die standardmäßigen `*-Variable`-Cmdlets sind nicht auf die Arbeit mit Umgebungsvariablen ausgelegt.</span><span class="sxs-lookup"><span data-stu-id="ea995-134">The standard `*-Variable` cmdlets aren't designed to work with environment variables.</span></span> <span data-ttu-id="ea995-135">Auf Umgebungsvariablen wird über das Laufwerkpräfix `env:` zugegriffen.</span><span class="sxs-lookup"><span data-stu-id="ea995-135">Environment variables are accessed using the `env:` drive prefix.</span></span> <span data-ttu-id="ea995-136">Beispielsweise enthält die Variable **%SystemRoot%** in **cmd.exe** den Stammverzeichnisnamen des Betriebssystems.</span><span class="sxs-lookup"><span data-stu-id="ea995-136">For example, the **%SystemRoot%** variable in **cmd.exe** contains the operating system's root directory name.</span></span> <span data-ttu-id="ea995-137">In PowerShell verwenden Sie `$env:SystemRoot`, um auf denselben Wert zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="ea995-137">In PowerShell, you use `$env:SystemRoot` to access the same value.</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="ea995-138">Sie können auch Umgebungsvariablen in PowerShell erstellen und ändern.</span><span class="sxs-lookup"><span data-stu-id="ea995-138">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="ea995-139">Umgebungsvariablen in PowerShell unterliegen denselben Regeln für Umgebungsvariablen, die an beliebiger anderer Stelle im Betriebssystem verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ea995-139">Environment variables in PowerShell follow the same rules for environment variables used elsewhere in the operating system.</span></span> <span data-ttu-id="ea995-140">Durch das folgende Beispiel wird eine neue Umgebungsvariable erstellt:</span><span class="sxs-lookup"><span data-stu-id="ea995-140">The following example creates a new environment variable:</span></span>

```powershell
$env:LIB_PATH='/usr/local/lib'
```

<span data-ttu-id="ea995-141">Wenngleich dies nicht erforderlich ist, ist es gängige Praxis, für Namen von Umgebungsvariablen ausschließlich Großbuchstaben zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ea995-141">Though not required, it's common for environment variable names to use all uppercase letters.</span></span>
