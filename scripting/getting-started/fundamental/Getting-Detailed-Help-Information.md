---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Abrufen von ausführlichen Hilfeinformationen"
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: 3260b5ec0a91749d3b7b126412137aa9d603ef0e
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="2ac46-103">Abrufen von ausführlichen Hilfeinformationen</span><span class="sxs-lookup"><span data-stu-id="2ac46-103">Getting Detailed Help Information</span></span>
<span data-ttu-id="2ac46-104">Windows PowerShell umfasst ausführliche Hilfethemen, in denen die Konzepte von Windows PowerShell und die Windows PowerShell-Sprache erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="2ac46-104">Windows PowerShell includes detailed Help topics that explain Windows PowerShell concepts and the Windows PowerShell language.</span></span> <span data-ttu-id="2ac46-105">Außerdem gibt es Hilfethemen für jedes Cmdlet und jeden Anbieter sowie Hilfethemen für viele Funktionen und Skripts.</span><span class="sxs-lookup"><span data-stu-id="2ac46-105">There are also Help topics for each cmdlet and provider and Help topics for many functions and scripts.</span></span>

<span data-ttu-id="2ac46-106">Sie können diese Hilfethemen über die Eingabeaufforderung anzeigen, oder Sie können die zuletzt aktualisierten Versionen dieser Themen in der Microsoft TechNet Library anzeigen.</span><span class="sxs-lookup"><span data-stu-id="2ac46-106">You can display these Help topics at the command prompt or view the most recently updated versions of these topics in the Microsoft TechNet Library.</span></span> <span data-ttu-id="2ac46-107">Viele Programme, von denen Windows PowerShell gehostet wird, z.B. Windows PowerShell Integrated Scripting Environment, stellen zusätzliche Hilfefunktionen bereit, etwa kontextbezogene Hilfe und kompilierte Hilfedateien (CHM).</span><span class="sxs-lookup"><span data-stu-id="2ac46-107">Many programs that host Windows PowerShell, such as Windows PowerShell Integrated Scripting Environment, provide additional Help features, such as context-sensitive Help and compiled Help file (.chm).</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="2ac46-108">Abrufen von Hilfe für Cmdlets</span><span class="sxs-lookup"><span data-stu-id="2ac46-108">Getting Help for Cmdlets</span></span>
<span data-ttu-id="2ac46-109">Wenn Sie Hilfe zu Windows PowerShell-Cmdlets abrufen möchten, verwenden Sie das Cmdlet [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2).</span><span class="sxs-lookup"><span data-stu-id="2ac46-109">To get Help about Windows PowerShell cmdlets, use the [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet.</span></span> <span data-ttu-id="2ac46-110">Geben Sie beispielsweise Folgendes ein, um Hilfe für das Cmdlet [Get-ChildItem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) abzurufen:</span><span class="sxs-lookup"><span data-stu-id="2ac46-110">For example, to get Help for the [Get-ChildItem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, type:</span></span>

```
get-help get-childitem
```

<span data-ttu-id="2ac46-111">oder</span><span class="sxs-lookup"><span data-stu-id="2ac46-111">or</span></span>

```
get-childitem -?
```

<span data-ttu-id="2ac46-112">Sie können sogar Hilfe zu dem Cmdlet „Get-Help“ abrufen.</span><span class="sxs-lookup"><span data-stu-id="2ac46-112">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="2ac46-113">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="2ac46-113">For example:</span></span>

```
get-help get-help
```

<span data-ttu-id="2ac46-114">Um eine Liste aller Cmdlet-Hilfethemen in der Sitzung abzurufen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="2ac46-114">To get a list of all the cmdlet Help topics in your session, type:</span></span>

```
get-help -category cmdlet
```

<span data-ttu-id="2ac46-115">Wenn Sie nur jeweils eine Seite jedes Hilfethemas anzeigen möchten, verwenden Sie die Funktion **help** oder deren Alias **man**.</span><span class="sxs-lookup"><span data-stu-id="2ac46-115">To display one page of each Help topic at a time, use the **help** function or its alias **man**.</span></span> <span data-ttu-id="2ac46-116">Wenn Sie beispielsweise Hilfe für das Cmdlet „Get-ChildItem“ anzeigen möchten, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="2ac46-116">For example, to display Help for the Get-ChildItem cmdlet, type</span></span>

```
man get-childitem
```

<span data-ttu-id="2ac46-117">oder</span><span class="sxs-lookup"><span data-stu-id="2ac46-117">or</span></span>

```
help get-childitem
```

<span data-ttu-id="2ac46-118">Um detaillierte Informationen zu einem Cmdlet, zu einer Funktion oder zu einem Skript samt Beschreibungen der jeweiligen Parameter sowie Beispielen für deren Verwendung anzuzeigen, verwenden Sie den *Detailed*-Parameter des Cmdlets „Get-Help“.</span><span class="sxs-lookup"><span data-stu-id="2ac46-118">To display detailed information about a cmdlet, function, or script, including descriptions of its parameters and examples of its use, use the *Detailed* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="2ac46-119">Geben Sie beispielsweise Folgendes ein, um ausführliche Informationen zum Cmdlet „Get-ChildItem“ abzurufen:</span><span class="sxs-lookup"><span data-stu-id="2ac46-119">For example, to get detailed information about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -detailed
```

<span data-ttu-id="2ac46-120">Wenn Sie den gesamten Inhalt eines Hilfethemas anzeigen möchten, verwenden Sie den *Full*-Parameter des Cmdlets „Get-Help“.</span><span class="sxs-lookup"><span data-stu-id="2ac46-120">To display all content in the Help topic, use the *Full* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="2ac46-121">Soll beispielsweise der gesamte Inhalt des Hilfethemas für das Cmdlet „Get-ChildItem“ angezeigt werden, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="2ac46-121">For example, to display all content in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -full
```

<span data-ttu-id="2ac46-122">Um ausführliche Hilfe zu den Parametern eines Cmdlets abzurufen, verwenden Sie den *Parameter*-Parameter des Cmdlets „Get-Help“.</span><span class="sxs-lookup"><span data-stu-id="2ac46-122">To get detailed Help about the parameters of a cmdlet, use the *Parameter* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="2ac46-123">Soll beispielsweise die ausführliche Hilfe zu allen Parametern des Cmdlets „Get-ChildItem“ abgerufen werden, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="2ac46-123">For example, to get detailed Help for all of the parameters of the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -parameter *
```

<span data-ttu-id="2ac46-124">Um nur die Beispiele anzuzeigen, die es in einem Hilfethema gibt, verwenden Sie den *Example*-Parameter von „Get-Help“.</span><span class="sxs-lookup"><span data-stu-id="2ac46-124">To display only the examples in a Help topic, use the *Example* parameter of the Get-Help.</span></span> <span data-ttu-id="2ac46-125">Sollen beispielsweise nur die Beispiele im Hilfethema für das Cmdlet „Get-ChildItem“ angezeigt werden, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="2ac46-125">For example, to display only the examples in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -examples
```

<span data-ttu-id="2ac46-126">Informationen dazu, wie Sie Hilfethemen für die Cmdlets schreiben, die Sie erstellen, finden Sie im Thema „How to Write Cmdlet Help“ in MSDN.</span><span class="sxs-lookup"><span data-stu-id="2ac46-126">For information about how to write Help topics for the cmdlets that you write, see the "How to Write Cmdlet Help" topic in MSDN.</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="2ac46-127">Abrufen von konzeptioneller Hilfe</span><span class="sxs-lookup"><span data-stu-id="2ac46-127">Getting Conceptual Help</span></span>
<span data-ttu-id="2ac46-128">Das Cmdlet „Get-Help“ zeigt auch Informationen zu konzeptionellen Themen in Windows PowerShell an, einschließlich Themen zur Windows PowerShell-Sprache.</span><span class="sxs-lookup"><span data-stu-id="2ac46-128">The Get-Help cmdlet also displays information about conceptual topics in Windows PowerShell, including topics about the Windows PowerShell language.</span></span> <span data-ttu-id="2ac46-129">Konzeptionelle Hilfethemen beginnen mit dem Präfix „about_“, z.B. „about_line_editing“.</span><span class="sxs-lookup"><span data-stu-id="2ac46-129">Conceptual Help topics begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="2ac46-130">(Der Name eines konzeptionellen Themas muss in Englisch eingegeben werden, auch in nicht englischsprachigen Versionen von Windows PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="2ac46-130">(The name of the conceptual topic must be entered in English even on non-English versions of Windows PowerShell.)</span></span>

<span data-ttu-id="2ac46-131">Um eine Liste der konzeptionellen Themen anzuzeigen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="2ac46-131">To display a list of conceptual topics, type:</span></span>

```
get-help about_*
```

<span data-ttu-id="2ac46-132">Um ein bestimmtes Hilfethema anzuzeigen, geben Sie den Namen des Themas ein, zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="2ac46-132">To display a particular Help topic, type the topic name, for example:</span></span>

```
get-help about_command_syntax
```

<span data-ttu-id="2ac46-133">Die Parameter von „Get-Help“, etwa *Detailed*, *Parameter* und *Examples*, wirken sich nicht auf die Anzeige von konzeptionellen Hilfethemen aus.</span><span class="sxs-lookup"><span data-stu-id="2ac46-133">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of conceptual Help topics.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="2ac46-134">Abrufen von Hilfe zu Anbietern</span><span class="sxs-lookup"><span data-stu-id="2ac46-134">Getting Help About Providers</span></span>
<span data-ttu-id="2ac46-135">Das Cmdlet „Get-Help“ zeigt Informationen zu Windows PowerShell-Anbietern an.</span><span class="sxs-lookup"><span data-stu-id="2ac46-135">The Get-Help cmdlet displays information about Windows PowerShell providers.</span></span> <span data-ttu-id="2ac46-136">Um Hilfe zu einem Anbieter (Provider) zu abzurufen, geben Sie „Get-Help“ gefolgt vom Anbieternamen ein.</span><span class="sxs-lookup"><span data-stu-id="2ac46-136">To get Help for a provider, type "Get-Help" followed by the provider name.</span></span> <span data-ttu-id="2ac46-137">Wenn Sie z. B. Hilfe zum Registrierungsanbieter abrufen möchten, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="2ac46-137">For example, to get Help for the Registry provider, type:</span></span>

```
get-help registry
```

<span data-ttu-id="2ac46-138">Um eine Liste aller Anbieter-Hilfethemen in der Sitzung abzurufen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="2ac46-138">To get a list of all the provider Help topics in your session, type</span></span>

```
get-help -category provider
```

<span data-ttu-id="2ac46-139">Die Parameter von „Get-Help“, etwa *Detailed*, *Parameter* und *Examples*, wirken sich nicht auf die Anzeige von Anbieter-Hilfethemen aus.</span><span class="sxs-lookup"><span data-stu-id="2ac46-139">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of provider Help topics.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="2ac46-140">Abrufen von Hilfe zu Skripts und Funktionen</span><span class="sxs-lookup"><span data-stu-id="2ac46-140">Getting Help About Scripts and Functions</span></span>
<span data-ttu-id="2ac46-141">Viele Skripts und Funktionen in Windows PowerShell haben Hilfethemen.</span><span class="sxs-lookup"><span data-stu-id="2ac46-141">Many scripts and functions in Windows PowerShell have Help topics.</span></span> <span data-ttu-id="2ac46-142">Verwenden Sie das Cmdlet „Get-Help“, um die Hilfethemen für Skripts und Funktionen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="2ac46-142">Use the Get-Help cmdlet to display the Help topics for scripts and functions.</span></span>

<span data-ttu-id="2ac46-143">Wenn Sie die Hilfe für eine Funktion anzeigen möchten, geben Sie „get-help“ und dahinter den Namen der Funktion ein.</span><span class="sxs-lookup"><span data-stu-id="2ac46-143">To display the Help for a function, type "get-help" followed by the function name.</span></span> <span data-ttu-id="2ac46-144">Soll beispielsweise Hilfe für die Funktion „Disable-PSRemoting“ abgerufen werden, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="2ac46-144">For example, to get Help for the Disable-PSRemoting function, type:</span></span>

```
get-help disable-psremoting
```

<span data-ttu-id="2ac46-145">Um die Hilfe für ein Skript anzuzeigen, geben Sie den vollqualifizierten Pfad zur Skriptdatei ein.</span><span class="sxs-lookup"><span data-stu-id="2ac46-145">To display the Help for a script, type the fully qualified path to the script file.</span></span> <span data-ttu-id="2ac46-146">Befindet sich das Skript in einem Pfad, der in der Umgebungsvariablen „Path“ aufgelistet ist, müssen Sie den Pfad nicht im Befehl angeben.</span><span class="sxs-lookup"><span data-stu-id="2ac46-146">If the script is in a path that is listed in the Path environment variable, you can omit the path from the command.</span></span>

<span data-ttu-id="2ac46-147">Wenn Sie beispielsweise ein Skript namens „TestScript.ps1“ in Ihrem Verzeichnis „C:\\PS-Test“ haben, geben Sie Folgendes ein, um das Hilfethema für das Skript anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="2ac46-147">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help topic for the script, type:</span></span>

```
get-help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="2ac46-148">Die Parameter, die für die Anzeige von Cmdlet-Hilfe konzipiert wurden, etwa *Detailed*, *Full*, *Examples* und *Parameter*, funktionieren auch für Hilfe zu Skripts und Funktionen.</span><span class="sxs-lookup"><span data-stu-id="2ac46-148">The parameters that were designed for displaying cmdlet Help, such as *Detailed*, *Full*, *Examples*, and *Parameter*, work for script Help and function Help, too.</span></span> <span data-ttu-id="2ac46-149">Wenn Sie die gesamte Hilfe anzeigen, indem Sie „get-help \*“ eingeben, wird die Hilfe zu Funktionen und Skripts aber nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2ac46-149">However, when you display all Help, by typing "get-help \*", Help for functions and scripts does not appear.</span></span>

<span data-ttu-id="2ac46-150">Informationen über das Schreiben von Hilfethemen für Ihre Funktionen und Skripts finden Sie unter [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af) und [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span><span class="sxs-lookup"><span data-stu-id="2ac46-150">For information about writing Help topics for your functions and scripts, see [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af), and [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span></span>

## <a name="getting-help-online"></a><span data-ttu-id="2ac46-151">Abrufen von Hilfe aus dem Internet</span><span class="sxs-lookup"><span data-stu-id="2ac46-151">Getting Help Online</span></span>
<span data-ttu-id="2ac46-152">Wenn Sie eine Verbindung mit dem Internet haben, ist eine der besten Möglichkeiten zum Abrufen von Hilfe, die Hilfethemen online anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="2ac46-152">If you are connected to the Internet, one of the best ways to get Help is to view the Help topics online.</span></span> <span data-ttu-id="2ac46-153">Da online verfügbare Themen einfach zu aktualisieren sind, stellen sie wahrscheinlich die aktuellsten Inhalte bereit.</span><span class="sxs-lookup"><span data-stu-id="2ac46-153">Because online topics are easy to update, they are likely to provide the most current content.</span></span>

<span data-ttu-id="2ac46-154">Um Hilfe aus dem Internet abzurufen, verwenden Sie den *Online*-Parameter des Cmdlets „Get-Help“.</span><span class="sxs-lookup"><span data-stu-id="2ac46-154">To get Help online, try the *Online* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="2ac46-155">Der *Online*-Parameter des Cmdlets „Get-Help“ funktioniert nur für Hilfe zu Cmdlets, Funktionen und Skripts.</span><span class="sxs-lookup"><span data-stu-id="2ac46-155">The *Online* parameter of the Get-Help cmdlet works only for cmdlet Help, function Help, and script Help.</span></span> <span data-ttu-id="2ac46-156">Der *Online*-Parameter kann nicht mit konzeptionellen Themen (About) oder Anbieter-Hilfethemen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2ac46-156">You cannot use the *Online* parameter with conceptual (About) topics or provider Help topics.</span></span> <span data-ttu-id="2ac46-157">Außerdem funktioniert dieser Parameter, da er optional ist, nicht für alle Hilfethemen zu Cmdlets, Funktionen oder Skripts.</span><span class="sxs-lookup"><span data-stu-id="2ac46-157">Also, because this feature is optional, it does not work for every cmdlet, function, or script Help topic.</span></span>

<span data-ttu-id="2ac46-158">Allerdings sind alle Hilfethemen, die zu Windows PowerShell gehören, einschließlich Anbieter-Hilfe und konzeptioneller Hilfethemen (About), online im [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116)-Abschnitt der Microsoft TechNet-Bibliothek verfügbar.</span><span class="sxs-lookup"><span data-stu-id="2ac46-158">However, all the Help topics that come with Windows PowerShell, including provider Help and conceptual (About) Help topics, are available online in the [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) section of the Microsoft TechNet Library.</span></span>

<span data-ttu-id="2ac46-159">Wenn Sie den *Online*-Parameter des Cmdlets „Get-Help“ verwenden möchten, verwenden Sie das folgende Befehlsformat.</span><span class="sxs-lookup"><span data-stu-id="2ac46-159">To use the *Online* parameter of the Get-Help cmdlet, use the following command format.</span></span>

```
get-help <command-name> -online
```

<span data-ttu-id="2ac46-160">Möchten Sie beispielsweise die Onlineversion des Hilfethemas zum Cmdlet „Get-ChildItem“ abrufen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="2ac46-160">For example, to get the online version of the Help topic about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -online
```

<span data-ttu-id="2ac46-161">Ist eine Onlineversion des Hilfethemas verfügbar, wird sie in Ihrem Standardbrowser geöffnet.</span><span class="sxs-lookup"><span data-stu-id="2ac46-161">If an online version of the Help topic is available, it will open in your default browser.</span></span>

<span data-ttu-id="2ac46-162">Wird Onlinehilfe für ein Hilfethema unterstützt, können Sie auch die Internetadresse (URL) des Hilfethemas anzeigen.</span><span class="sxs-lookup"><span data-stu-id="2ac46-162">If online Help is supported for a Help topic, you can also view the Internet address (URL) of the Help topic.</span></span> <span data-ttu-id="2ac46-163">Die Internetadresse wird im Abschnitt „Verwandte Links“ eines Hilfethemas angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2ac46-163">The Internet address appears in the Related Links section of a Help topic.</span></span>

<span data-ttu-id="2ac46-164">Wenn Sie beispielsweise die URL für die Onlineversion des Cmdlets „Add-Computer“ anzeigen möchten, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="2ac46-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```
get-help add-computer
```

<span data-ttu-id="2ac46-165">Die erste Zeile des Abschnitts „Verwandte Links“ des Themas ist nachstehend dargestellt.</span><span class="sxs-lookup"><span data-stu-id="2ac46-165">The first line in the Related Links section of the topic is shown below.</span></span>

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

<span data-ttu-id="2ac46-166">Informationen dazu, wie Sie die Onlineunterstützung für Ihre Hilfethemen bereitstellen, finden Sie unter [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf) sowie unter „How to Write Cmdlet Help“ ([http://go.microsoft.com/fwlink/?LinkID=123415](http://go.microsoft.com/fwlink/?LinkID=123415)) in der MSDN-Bibliothek (Microsoft Developer Network).</span><span class="sxs-lookup"><span data-stu-id="2ac46-166">For information about how to provide online support for your Help topics, see [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf), and see "How to Write Cmdlet Help" ([http://go.microsoft.com/fwlink/?LinkID=123415](http://go.microsoft.com/fwlink/?LinkID=123415)) in the MSDN (Microsoft Developer Network) library.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ac46-167">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2ac46-167">See Also</span></span>
- [<span data-ttu-id="2ac46-168">about_Functions [m2]</span><span class="sxs-lookup"><span data-stu-id="2ac46-168">about_Functions [m2]</span></span>](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)
- [<span data-ttu-id="2ac46-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="2ac46-169">about_Scripts</span></span>](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af)
- [<span data-ttu-id="2ac46-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="2ac46-170">about_Comment_Based_Help</span></span>](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- [<span data-ttu-id="2ac46-171">Get-Help [m2]</span><span class="sxs-lookup"><span data-stu-id="2ac46-171">Get-Help [m2]</span></span>](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)

