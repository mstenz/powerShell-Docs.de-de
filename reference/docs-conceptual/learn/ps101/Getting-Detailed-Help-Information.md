---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Abrufen von ausführlichen Hilfeinformationen
ms.openlocfilehash: e722eb8a0ca13e3d2de864314775a0a9fa578390
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808496"
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="134e0-103">Abrufen ausführlicher Hilfeinformationen</span><span class="sxs-lookup"><span data-stu-id="134e0-103">Getting detailed help information</span></span>

<span data-ttu-id="134e0-104">PowerShell umfasst ausführliche Hilfeartikel, in denen die Konzepte von PowerShell und die PowerShell-Sprache erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="134e0-104">PowerShell includes detailed Help articles that explain PowerShell concepts and the PowerShell language.</span></span> <span data-ttu-id="134e0-105">Außerdem gibt es Hilfeartikel für jedes Cmdlet und jeden Anbieter sowie für viele Funktionen und Skripts.</span><span class="sxs-lookup"><span data-stu-id="134e0-105">There are also Help articles for each cmdlet and provider and for many functions and scripts.</span></span>

<span data-ttu-id="134e0-106">Sie können diese Hilfeartikel über die Eingabeaufforderung anzeigen. Sie können aber auch die zuletzt aktualisierten Versionen dieser Artikel in der [PowerShell](/powershell/scripting/overview)-Dokumentation online anzeigen.</span><span class="sxs-lookup"><span data-stu-id="134e0-106">You can display these Help articles at the command prompt or view the most recently updated versions of these articles in the [PowerShell](/powershell/scripting/overview) documentation online.</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="134e0-107">Abrufen von Hilfe für Cmdlets</span><span class="sxs-lookup"><span data-stu-id="134e0-107">Getting help for cmdlets</span></span>

<span data-ttu-id="134e0-108">Wenn Sie Hilfe zu PowerShell-Cmdlets abrufen möchten, verwenden Sie das Cmdlet [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help).</span><span class="sxs-lookup"><span data-stu-id="134e0-108">To get Help about PowerShell cmdlets, use the [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span></span> <span data-ttu-id="134e0-109">Geben Sie beispielsweise Folgendes ein, um Hilfe für das Cmdlet `Get-ChildItem` abzurufen:</span><span class="sxs-lookup"><span data-stu-id="134e0-109">For example, to get Help for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="134e0-110">oder</span><span class="sxs-lookup"><span data-stu-id="134e0-110">or</span></span>

```powershell
Get-ChildItem -?
```

<span data-ttu-id="134e0-111">Sie können sogar Hilfe zu dem Cmdlet „Get-Help“ abrufen.</span><span class="sxs-lookup"><span data-stu-id="134e0-111">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="134e0-112">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="134e0-112">For example:</span></span>

```powershell
Get-Help Get-Help
```

<span data-ttu-id="134e0-113">Um eine Liste aller Cmdlet-Hilfeartikel in der Sitzung abzurufen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="134e0-113">To get a list of all the cmdlet Help articles in your session, type:</span></span>

```powershell
Get-Help -Category Cmdlet
```

<span data-ttu-id="134e0-114">Wenn Sie nur jeweils eine Seite jedes Hilfeartikels anzeigen möchten, verwenden Sie die Funktion `help` oder deren Alias `man`.</span><span class="sxs-lookup"><span data-stu-id="134e0-114">To display one page of each Help article at a time, use the `help` function or its alias `man`.</span></span>
<span data-ttu-id="134e0-115">Geben Sie beispielsweise Folgendes ein, um Hilfe für das Cmdlet `Get-ChildItem` anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="134e0-115">For example, to display Help for the `Get-ChildItem` cmdlet, type</span></span>

```powershell
man Get-ChildItem
```

<span data-ttu-id="134e0-116">oder</span><span class="sxs-lookup"><span data-stu-id="134e0-116">or</span></span>

```powershell
help Get-ChildItem
```

<span data-ttu-id="134e0-117">Um ausführliche Informationen anzuzeigen, verwenden Sie den Parameter **Detailed** des Cmdlets `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="134e0-117">To display detailed information, use the **Detailed** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="134e0-118">Geben Sie beispielsweise Folgendes ein, um ausführliche Informationen zum Cmdlet `Get-ChildItem` abzurufen:</span><span class="sxs-lookup"><span data-stu-id="134e0-118">For example, to get detailed information about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Detailed
```

<span data-ttu-id="134e0-119">Wenn Sie den gesamten Inhalt eines Hilfeartikels anzeigen möchten, verwenden Sie den Parameter **Full** des Cmdlets `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="134e0-119">To display all content in the Help article, use the **Full** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="134e0-120">Soll beispielsweise der gesamte Inhalt des Hilfeartikels für das Cmdlet `Get-ChildItem` angezeigt werden, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="134e0-120">For example, to display all content in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Full
```

<span data-ttu-id="134e0-121">Um ausführliche Hilfe zu den Parametern eines Cmdlets abzurufen, verwenden Sie den Parameter **Parameter** des Cmdlets `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="134e0-121">To get detailed Help about the parameters of a cmdlet, use the **Parameter** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="134e0-122">Soll beispielsweise die ausführliche Hilfe zu allen Parametern des Cmdlets `Get-ChildItem` abgerufen werden, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="134e0-122">For example, to get detailed Help for all of the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Parameter *
```

<span data-ttu-id="134e0-123">Um nur die Beispiele in einem Hilfeartikel anzuzeigen, verwenden Sie den Parameter **Examples** von `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="134e0-123">To display only the examples in a Help article, use the **Examples** parameter of the `Get-Help`.</span></span>
<span data-ttu-id="134e0-124">Sollen beispielsweise nur die Beispiele im Hilfeartikel für das Cmdlet `Get-ChildItem` angezeigt werden, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="134e0-124">For example, to display only the examples in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Examples
```

<span data-ttu-id="134e0-125">Informationen dazu, wie Sie Hilfeartikel für die Cmdlets schreiben, die Sie erstellen, finden Sie unter [How to Write Cmdlet Help (Schreiben von Hilfe zu Cmdlets)](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="134e0-125">For information about how to write Help articles for the cmdlets that you write, see [How to Write Cmdlet Help](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="134e0-126">Abrufen von konzeptioneller Hilfe</span><span class="sxs-lookup"><span data-stu-id="134e0-126">Getting conceptual help</span></span>

<span data-ttu-id="134e0-127">Das Cmdlet `Get-Help` zeigt auch Informationen zu konzeptionellen Artikeln in PowerShell an, darunter Artikel zur PowerShell-Sprache.</span><span class="sxs-lookup"><span data-stu-id="134e0-127">The `Get-Help` cmdlet also displays information about conceptual articles in PowerShell, including articles about the PowerShell language.</span></span> <span data-ttu-id="134e0-128">Konzeptionelle Hilfeartikel beginnen mit dem Präfix „about_“, z.B. „about_line_editing“.</span><span class="sxs-lookup"><span data-stu-id="134e0-128">Conceptual Help articles begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="134e0-129">(Der Name eines konzeptionellen Artikels muss in Englisch eingegeben werden, auch in nicht englischsprachigen Versionen von PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="134e0-129">(The name of the conceptual article must be entered in English even on non-English versions of PowerShell.)</span></span>

<span data-ttu-id="134e0-130">Um eine Liste der konzeptionellen Artikel anzuzeigen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="134e0-130">To display a list of conceptual articles, type:</span></span>

```powershell
Get-Help about_*
```

<span data-ttu-id="134e0-131">Um einen bestimmten Hilfeartikel anzuzeigen, geben Sie den Namen des Artikels ein, Beispiel:</span><span class="sxs-lookup"><span data-stu-id="134e0-131">To display a particular Help article, type the article name, for example:</span></span>

```powershell
Get-Help about_command_syntax
```

<span data-ttu-id="134e0-132">Die Parameter von `Get-Help`, etwa **Detailed**, **Parameter** und **Examples**, wirken sich nicht auf die Anzeige von konzeptionellen Hilfeartikeln aus.</span><span class="sxs-lookup"><span data-stu-id="134e0-132">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of conceptual Help articles.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="134e0-133">Abrufen von Hilfe zu Anbietern</span><span class="sxs-lookup"><span data-stu-id="134e0-133">Getting help about providers</span></span>

<span data-ttu-id="134e0-134">Das Cmdlet `Get-Help` zeigt Informationen zu PowerShell-Anbietern an.</span><span class="sxs-lookup"><span data-stu-id="134e0-134">The `Get-Help` cmdlet displays information about PowerShell providers.</span></span> <span data-ttu-id="134e0-135">Um Hilfe zu einem Anbieter abzurufen, geben Sie `Get-Help` gefolgt vom Anbieternamen ein.</span><span class="sxs-lookup"><span data-stu-id="134e0-135">To get Help for a provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="134e0-136">Wenn Sie z. B. Hilfe zum Registrierungsanbieter abrufen möchten, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="134e0-136">For example, to get Help for the Registry provider, type:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="134e0-137">Um eine Liste aller Hilfeartikel zu Anbietern in der Sitzung abzurufen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="134e0-137">To get a list of all the provider Help articles in your session, type</span></span>

```powershell
Get-Help -Category provider
```

<span data-ttu-id="134e0-138">Die Parameter von `Get-Help`, etwa **Detailed**, **Parameter** und **Examples**, wirken sich nicht auf die Anzeige von Hilfeartikeln zu Anbietern aus.</span><span class="sxs-lookup"><span data-stu-id="134e0-138">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of provider Help articles.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="134e0-139">Abrufen von Hilfe zu Skripts und Funktionen</span><span class="sxs-lookup"><span data-stu-id="134e0-139">Getting help about scripts and functions</span></span>

<span data-ttu-id="134e0-140">Viele Skripts und Funktionen in PowerShell haben Hilfeartikel.</span><span class="sxs-lookup"><span data-stu-id="134e0-140">Many scripts and functions in PowerShell have Help articles.</span></span> <span data-ttu-id="134e0-141">Verwenden Sie das Cmdlet `Get-Help`, um die Hilfeartikel für Skripts und Funktionen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="134e0-141">Use the `Get-Help` cmdlet to display the Help articles for scripts and functions.</span></span>

<span data-ttu-id="134e0-142">Wenn Sie die Hilfe für eine Funktion anzeigen möchten, geben Sie `Get-Help` und dahinter den Namen der Funktion ein.</span><span class="sxs-lookup"><span data-stu-id="134e0-142">To display the Help for a function, type `Get-Help` followed by the function name.</span></span> <span data-ttu-id="134e0-143">Geben Sie beispielsweise Folgendes ein, um Hilfe für die Funktion `Disable-PSRemoting` abzurufen:</span><span class="sxs-lookup"><span data-stu-id="134e0-143">For example, to get Help for the `Disable-PSRemoting` function, type:</span></span>

```powershell
Get-Help Disable-PSRemoting
```

<span data-ttu-id="134e0-144">Um die Hilfe für ein Skript anzuzeigen, geben Sie den Pfad zur Skriptdatei ein.</span><span class="sxs-lookup"><span data-stu-id="134e0-144">To display the Help for a script, type the path to the script file.</span></span> <span data-ttu-id="134e0-145">Wenn sich das Skript nicht in einem Pfad befindet, der in der Umgebungsvariablen „Path“ aufgelistet ist, müssen Sie den vollqualifizierten Pfad verwenden.</span><span class="sxs-lookup"><span data-stu-id="134e0-145">If the script is not in a path listed in the Path environment variable, you must use the fully qualified path.</span></span>

<span data-ttu-id="134e0-146">Wenn Sie beispielsweise ein Skript namens „TestScript.ps1“ in Ihrem Verzeichnis „C:\\PS-Test“ haben, geben Sie Folgendes ein, um den Hilfeartikel für das Skript anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="134e0-146">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help article for the script, type:</span></span>

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="134e0-147">Die Parameter, die für die Anzeige der Cmdlet-Hilfe vorgesehen sind, funktionieren auch für die Hilfe zu Skripts und Funktionen.</span><span class="sxs-lookup"><span data-stu-id="134e0-147">The parameters that are designed for displaying cmdlet Help work for script and function Help, too.</span></span> <span data-ttu-id="134e0-148">Die Hilfe zu Funktionen und Skripts wird allerdings nicht beim Ausführen von `Get-Help *` angezeigt.</span><span class="sxs-lookup"><span data-stu-id="134e0-148">However, help for functions and scripts is not shown when you run `Get-Help *`.</span></span>

<span data-ttu-id="134e0-149">Informationen zum Schreiben von Hilfeartikeln für Ihre Funktionen und Skripts finden Sie in den folgenden Artikeln:</span><span class="sxs-lookup"><span data-stu-id="134e0-149">For information about writing Help articles for your functions and scripts, see the following articles:</span></span>

- [<span data-ttu-id="134e0-150">about_Functions</span><span class="sxs-lookup"><span data-stu-id="134e0-150">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="134e0-151">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="134e0-151">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="134e0-152">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="134e0-152">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a><span data-ttu-id="134e0-153">Abrufen von Hilfe aus dem Internet</span><span class="sxs-lookup"><span data-stu-id="134e0-153">Getting help online</span></span>

<span data-ttu-id="134e0-154">Die Onlineanzeige der Hilfeartikel ist eine der besten Möglichkeiten, um Hilfe zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="134e0-154">Viewing the Help articles online is one of the best ways to get help.</span></span> <span data-ttu-id="134e0-155">Onlineartikel können leichter aktualisiert werden und bieten aktuelle Inhalte.</span><span class="sxs-lookup"><span data-stu-id="134e0-155">Online articles are easier to update and provide the most current content.</span></span>

<span data-ttu-id="134e0-156">Um Hilfe aus dem Internet abzurufen, verwenden Sie den Parameter **Online** des Cmdlets `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="134e0-156">To get Help online, use the **Online** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="134e0-157">Alle Hilfeartikel für PowerShell, einschließlich der Hilfeartikel zu Anbietern und konzeptioneller Hilfeartikel („about“), stehen online in der [PowerShell](/powershell/scripting/powershell-scripting)-Dokumentation zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="134e0-157">All the Help articles that come with PowerShell, including provider Help and conceptual (About) Help articles, are available online in the [PowerShell](/powershell/scripting/powershell-scripting) documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="134e0-158">Der Parameter **Online** kann nicht mit konzeptionellen (about_\*) Hilfeartikeln oder Hilfeartikeln zu Anbietern verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="134e0-158">You can't use the **Online** parameter with conceptual (about_\*) or provider Help articles.</span></span>
> <span data-ttu-id="134e0-159">Die Onlinehilfe ist optional, daher ist sie nicht für alle Cmdlets, Funktionen oder Skripts verfügbar.</span><span class="sxs-lookup"><span data-stu-id="134e0-159">Online help is optional, so it does not work for every cmdlet, function, or script.</span></span>

<span data-ttu-id="134e0-160">Möchten Sie beispielsweise die Onlineversion des Hilfeartikels zum Cmdlet `Get-ChildItem` abrufen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="134e0-160">For example, to get the online version of the Help article about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Online
```

<span data-ttu-id="134e0-161">PowerShell öffnet den Artikel in Ihrem Standardbrowser.</span><span class="sxs-lookup"><span data-stu-id="134e0-161">PowerShell opens the article in your default browser.</span></span> <span data-ttu-id="134e0-162">Wird Onlinehilfe für einen Hilfeartikel unterstützt, können Sie auch die URL des Hilfeartikels anzeigen.</span><span class="sxs-lookup"><span data-stu-id="134e0-162">If online Help is supported for a Help article, you can also view the URL of the Help article.</span></span> <span data-ttu-id="134e0-163">Die URL wird im Abschnitt „Verwandte Links“ eines Hilfeartikels angezeigt.</span><span class="sxs-lookup"><span data-stu-id="134e0-163">The URL appears in the Related Links section of a Help article.</span></span>

<span data-ttu-id="134e0-164">Wenn Sie beispielsweise die URL für die Onlineversion des Cmdlets „Add-Computer“ anzeigen möchten, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="134e0-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```powershell
Get-Help Add-Computer
```

<span data-ttu-id="134e0-165">Die erste Zeile des Abschnitts „Verwandte Links“ des Artikels ist nachstehend dargestellt.</span><span class="sxs-lookup"><span data-stu-id="134e0-165">The first line in the Related Links section of the article is shown below.</span></span>

```Output
Online version: https://go.microsoft.com/fwlink/?LinkId=821564
```

<span data-ttu-id="134e0-166">Informationen dazu, wie Sie Onlineunterstützung für Ihre Hilfeartikel bereitstellen, finden Sie unter [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span><span class="sxs-lookup"><span data-stu-id="134e0-166">For information about how to provide online support for your Help articles, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

## <a name="see-also"></a><span data-ttu-id="134e0-167">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="134e0-167">See also</span></span>

- [<span data-ttu-id="134e0-168">about_Functions</span><span class="sxs-lookup"><span data-stu-id="134e0-168">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="134e0-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="134e0-169">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="134e0-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="134e0-170">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [<span data-ttu-id="134e0-171">Get-Help</span><span class="sxs-lookup"><span data-stu-id="134e0-171">Get-Help</span></span>](/powershell/module/microsoft.powershell.core/get-help)
