---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Das ISEOptions-Objekt
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: 56bdd5999b46b6e29e762c2d9a2060cebe3a1299
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="b17d2-103">Das ISEOptions-Objekt</span><span class="sxs-lookup"><span data-stu-id="b17d2-103">The ISEOptions Object</span></span>
  <span data-ttu-id="b17d2-104">Das **ISEOptions**-Objekt stellt verschiedene Einstellungen für Windows PowerShell ISE dar.</span><span class="sxs-lookup"><span data-stu-id="b17d2-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="b17d2-105">Es ist eine Instanz der **Microsoft.PowerShell.Host.ISE.ISEOptions**-Klasse.</span><span class="sxs-lookup"><span data-stu-id="b17d2-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

 <span data-ttu-id="b17d2-106">Das **ISEOptions**-Objekt stellt die folgenden Methoden und Eigenschaften bereit.</span><span class="sxs-lookup"><span data-stu-id="b17d2-106">The **ISEOptions** object provides the following methods and properties.</span></span>

 <span data-ttu-id="b17d2-107">**Methoden**</span><span class="sxs-lookup"><span data-stu-id="b17d2-107">**Methods**</span></span>

-   [<span data-ttu-id="b17d2-108">RestoreDefaultConsoleTokenColors()</span><span class="sxs-lookup"><span data-stu-id="b17d2-108">RestoreDefaultConsoleTokenColors()</span></span>](#rdctc)

-   [<span data-ttu-id="b17d2-109">RestoreDefaults()</span><span class="sxs-lookup"><span data-stu-id="b17d2-109">RestoreDefaults()</span></span>](#rd)

-   [<span data-ttu-id="b17d2-110">RestoreDefaultTokenColors()</span><span class="sxs-lookup"><span data-stu-id="b17d2-110">RestoreDefaultTokenColors()</span></span>](#rdtc)

-   [<span data-ttu-id="b17d2-111">RestoreDefaultXmlTokenColors()</span><span class="sxs-lookup"><span data-stu-id="b17d2-111">RestoreDefaultXmlTokenColors()</span></span>](#rdxtc)

 <span data-ttu-id="b17d2-112">**Eigenschaften**</span><span class="sxs-lookup"><span data-stu-id="b17d2-112">**Properties**</span></span>

-   [<span data-ttu-id="b17d2-113">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="b17d2-113">AutoSaveMinuteInterval</span></span>](#asmi)

-   [<span data-ttu-id="b17d2-114">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-114">CommandPaneBackgroundColor</span></span>](#cpbc)

-   [<span data-ttu-id="b17d2-115">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="b17d2-115">CommandPaneUp</span></span>](#cpu)

-   [<span data-ttu-id="b17d2-116">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-116">ConsolePaneBackgroundColor</span></span>](#conpbc)

-   [<span data-ttu-id="b17d2-117">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-117">ConsolePaneForegroundColor</span></span>](#conpfc)

-   [<span data-ttu-id="b17d2-118">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-118">ConsolePaneTextBackgroundColor</span></span>](#conptbc)

-   [<span data-ttu-id="b17d2-119">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="b17d2-119">ConsoleTokenColors</span></span>](#contc)

-   [<span data-ttu-id="b17d2-120">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-120">DebugBackgroundColor</span></span>](#dbc)

-   [<span data-ttu-id="b17d2-121">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-121">DebugForegroundColor</span></span>](#dfc)

-   [<span data-ttu-id="b17d2-122">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="b17d2-122">DefaultOptions</span></span>](#do)

-   [<span data-ttu-id="b17d2-123">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-123">ErrorBackgroundColor</span></span>](#ebc)

-   [<span data-ttu-id="b17d2-124">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-124">ErrorForegroundColor</span></span>](#efc)

-   [<span data-ttu-id="b17d2-125">FontName</span><span class="sxs-lookup"><span data-stu-id="b17d2-125">FontName</span></span>](#fn)

-   [<span data-ttu-id="b17d2-126">FontSize</span><span class="sxs-lookup"><span data-stu-id="b17d2-126">FontSize</span></span>](#fs)

-   [<span data-ttu-id="b17d2-127">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="b17d2-127">IntellisenseTimeoutInSeconds</span></span>](#itis)

-   [<span data-ttu-id="b17d2-128">MruCount</span><span class="sxs-lookup"><span data-stu-id="b17d2-128">MruCount</span></span>](#mc)

-   [<span data-ttu-id="b17d2-129">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-129">OutputPaneBackgroundColor</span></span>](#opbc)

-   [<span data-ttu-id="b17d2-130">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-130">OutputPaneTextForegroundColor</span></span>](#optfc)

-   [<span data-ttu-id="b17d2-131">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-131">OutputPaneTextBackgroundColor</span></span>](#optbc)

-   [<span data-ttu-id="b17d2-132">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-132">ScriptPaneBackgroundColor</span></span>](#spbc)

-   [<span data-ttu-id="b17d2-133">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-133">ScriptPaneForegroundColor</span></span>](#spfc)

-   [<span data-ttu-id="b17d2-134">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="b17d2-134">SelectedScriptPaneState</span></span>](#ssps)

-   [<span data-ttu-id="b17d2-135">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="b17d2-135">ShowDefaultSnippets</span></span>](#sds)

-   [<span data-ttu-id="b17d2-136">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="b17d2-136">ShowIntellisenseInConsolePane</span></span>](#siicp)

-   [<span data-ttu-id="b17d2-137">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="b17d2-137">ShowIntellisenseInScriptPane</span></span>](#siisp)

-   [<span data-ttu-id="b17d2-138">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="b17d2-138">ShowLineNumbers</span></span>](#sln)

-   [<span data-ttu-id="b17d2-139">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="b17d2-139">ShowOutlining</span></span>](#so)

-   [<span data-ttu-id="b17d2-140">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="b17d2-140">ShowToolBar</span></span>](#stb)

-   [<span data-ttu-id="b17d2-141">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="b17d2-141">ShowWarningBeforeSavingOnRun</span></span>](#swbsor)

-   [<span data-ttu-id="b17d2-142">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="b17d2-142">ShowWarningForDuplicateFiles</span></span>](#swfdf)

-   [<span data-ttu-id="b17d2-143">TokenColors</span><span class="sxs-lookup"><span data-stu-id="b17d2-143">TokenColors</span></span>](#tc)

-   [<span data-ttu-id="b17d2-144">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="b17d2-144">UseEnterToSelectInConsolePaneIntellisense</span></span>](#uetsicpi)

-   [<span data-ttu-id="b17d2-145">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="b17d2-145">UseEnterToSelectInScriptPaneIntellisense</span></span>](#uetsispi)

-   [<span data-ttu-id="b17d2-146">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="b17d2-146">UseLocalHelp</span></span>](#ulh)

-   [<span data-ttu-id="b17d2-147">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-147">VerboseBackgroundColor</span></span>](#vbc)

-   [<span data-ttu-id="b17d2-148">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-148">VerboseForegroundColor</span></span>](#vfc)

-   [<span data-ttu-id="b17d2-149">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-149">WarningBackgroundColor</span></span>](#wbc)

-   [<span data-ttu-id="b17d2-150">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-150">WarningForegroundColor</span></span>](#wfc)

-   [<span data-ttu-id="b17d2-151">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="b17d2-151">XmlTokenColors</span></span>](#xtc)

-   [<span data-ttu-id="b17d2-152">Zoom</span><span class="sxs-lookup"><span data-stu-id="b17d2-152">Zoom</span></span>](#z)

## <a name="methods"></a><span data-ttu-id="b17d2-153">Methoden</span><span class="sxs-lookup"><span data-stu-id="b17d2-153">Methods</span></span>

###  <span data-ttu-id="b17d2-154"><a name="rdctc"></a> RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="b17d2-154"><a name="rdctc"></a> RestoreDefaultConsoleTokenColors\(\)</span></span>
  <span data-ttu-id="b17d2-155">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-155">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b17d2-156">Stellt die Standardwerte für die Tokenfarben im Konsolenbereich wieder her.</span><span class="sxs-lookup"><span data-stu-id="b17d2-156">Restores the default values of the token colors in the Console pane.</span></span>

```
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = "red"
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

###  <span data-ttu-id="b17d2-157"><a name="rd"></a> RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="b17d2-157"><a name="rd"></a> RestoreDefaults\(\)</span></span>
  <span data-ttu-id="b17d2-158">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b17d2-159">Stellt die Standardwerte aller Optionseinstellungen im Konsolenbereich wieder her.</span><span class="sxs-lookup"><span data-stu-id="b17d2-159">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="b17d2-160">Außerdem wird das Verhalten von verschiedenen Warnmeldungen zurückgesetzt, in denen das Standardkontrollkästchen angezeigt wird, mit dem das erneute Anzeigen der Nachricht verhindert werden kann.</span><span class="sxs-lookup"><span data-stu-id="b17d2-160">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = "orange"
$psISE.Options.RestoreDefaults()
```

###  <span data-ttu-id="b17d2-161"><a name="rdtc"></a> RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="b17d2-161"><a name="rdtc"></a> RestoreDefaultTokenColors\(\)</span></span>
  <span data-ttu-id="b17d2-162">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b17d2-163">Stellt die Standardwerte für die Tokenfarben im Skriptbereich wieder her.</span><span class="sxs-lookup"><span data-stu-id="b17d2-163">Restores the default values of the token colors in the Script pane.</span></span>

```
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultTokenColors()
```

###  <span data-ttu-id="b17d2-164"><a name="rdxtc"></a> RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="b17d2-164"><a name="rdxtc"></a> RestoreDefaultXmlTokenColors\(\)</span></span>
  <span data-ttu-id="b17d2-165">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-165">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b17d2-166">Stellt die Standardwerte für die Tokenfarben für XML-Elemente wieder her, die in Windows PowerShell ISE angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b17d2-166">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="b17d2-167">Siehe auch [XmlTokenColors](#xtc).</span><span class="sxs-lookup"><span data-stu-id="b17d2-167">Also see [XmlTokenColors](#xtc).</span></span>

```
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="b17d2-168">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="b17d2-168">Properties</span></span>

###  <span data-ttu-id="b17d2-169"><a name="asmi"></a> AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="b17d2-169"><a name="asmi"></a> AutoSaveMinuteInterval</span></span>
  <span data-ttu-id="b17d2-170">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-170">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b17d2-171">Gibt die Anzahl der Minuten zwischen automatischen Speichervorgängen Ihrer Dateien durch Windows PowerShell ISE an.</span><span class="sxs-lookup"><span data-stu-id="b17d2-171">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="b17d2-172">Der Standardwert beträgt 2 Minuten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-172">The default value is 2 minutes.</span></span> <span data-ttu-id="b17d2-173">Der Wert ist eine ganze Zahl.</span><span class="sxs-lookup"><span data-stu-id="b17d2-173">The value is an integer.</span></span>

```
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

###  <span data-ttu-id="b17d2-174"><a name="cpbc"></a> CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-174"><a name="cpbc"></a> CommandPaneBackgroundColor</span></span>
  <span data-ttu-id="b17d2-175">Dieses Feature ist in Windows PowerShell ISE 2.0 enthalten, wurde in höheren Versionen von ISE aber entfernt oder umbenannt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-175">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="b17d2-176">Informationen zu höheren Versionen finden Sie unter [ConsolePaneBackgroundColor](#conpbc).</span><span class="sxs-lookup"><span data-stu-id="b17d2-176">For later versions, see [ConsolePaneBackgroundColor](#conpbc).</span></span>

 <span data-ttu-id="b17d2-177">Gibt die Hintergrundfarbe für den Befehlsbereich an.</span><span class="sxs-lookup"><span data-stu-id="b17d2-177">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="b17d2-178">Dies ist eine Instanz der **System.Windows.Media.Color**-Klasse.</span><span class="sxs-lookup"><span data-stu-id="b17d2-178">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = "orange"
```

###  <span data-ttu-id="b17d2-179"><a name="cpu"></a> CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="b17d2-179"><a name="cpu"></a> CommandPaneUp</span></span>
  <span data-ttu-id="b17d2-180">Dieses Feature ist in Windows PowerShell ISE 2.0 enthalten, wurde in höheren Versionen von ISE aber entfernt oder umbenannt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-180">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

 <span data-ttu-id="b17d2-181">Gibt an, ob sich der Befehlsbereich oberhalb des Ausgabebereichs befindet.</span><span class="sxs-lookup"><span data-stu-id="b17d2-181">Specifies whether the Command pane is located above the Output pane.</span></span>

```
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true

```

###  <span data-ttu-id="b17d2-182"><a name="conpbc"></a> ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-182"><a name="conpbc"></a> ConsolePaneBackgroundColor</span></span>
  <span data-ttu-id="b17d2-183">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-183">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b17d2-184">Gibt die Hintergrundfarbe für den Konsolenbereich an.</span><span class="sxs-lookup"><span data-stu-id="b17d2-184">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="b17d2-185">Dies ist eine Instanz der **System.Windows.Media.Color**-Klasse.</span><span class="sxs-lookup"><span data-stu-id="b17d2-185">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = "red"
```

###  <span data-ttu-id="b17d2-186"><a name="conpfc"></a> ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-186"><a name="conpfc"></a> ConsolePaneForegroundColor</span></span>
  <span data-ttu-id="b17d2-187">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b17d2-188">Gibt die Vordergrundfarbe des Texts im Konsolenbereich an.</span><span class="sxs-lookup"><span data-stu-id="b17d2-188">Specifies the foreground color of the text in the Console pane.</span></span>

```
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = "yellow"

```

###  <span data-ttu-id="b17d2-189"><a name="conptbc"></a> ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-189"><a name="conptbc"></a> ConsolePaneTextBackgroundColor</span></span>
  <span data-ttu-id="b17d2-190">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-190">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b17d2-191">Gibt die Hintergrundfarbe des Texts im Konsolenbereich an.</span><span class="sxs-lookup"><span data-stu-id="b17d2-191">Specifies the background color of the text in the Console pane.</span></span>

```
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = "pink"
```

###  <span data-ttu-id="b17d2-192"><a name="contc"></a> ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="b17d2-192"><a name="contc"></a> ConsoleTokenColors</span></span>
  <span data-ttu-id="b17d2-193">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-193">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b17d2-194">Gibt die Farben der IntelliSense-Token im Windows PowerShell ISE-Konsolenbereich an.</span><span class="sxs-lookup"><span data-stu-id="b17d2-194">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="b17d2-195">Diese Eigenschaft ist ein Wörterbuchobjekt, das Name-Wert-Paare von Tokentypen und Farben für den Konsolenbereich enthält.</span><span class="sxs-lookup"><span data-stu-id="b17d2-195">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="b17d2-196">Informationen zum Ändern der Farben der IntelliSense-Token im Skriptbereich finden Sie unter [TokenColors](#tc).</span><span class="sxs-lookup"><span data-stu-id="b17d2-196">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tc).</span></span> <span data-ttu-id="b17d2-197">Informationen zum Zurücksetzen der Farben auf die Standardwerte finden Sie unter [RestoreDefaultConsoleTokenColors()](#rdctc).</span><span class="sxs-lookup"><span data-stu-id="b17d2-197">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors()](#rdctc).</span></span> <span data-ttu-id="b17d2-198">Tokenfarben können für folgende Elemente festgelegt werden: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="b17d2-198">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = "magenta"

```

###  <span data-ttu-id="b17d2-199"><a name="dbc"></a> DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-199"><a name="dbc"></a> DebugBackgroundColor</span></span>
  <span data-ttu-id="b17d2-200">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-200">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b17d2-201">Gibt die Hintergrundfarbe für den Debugtext an, der im Konsolenbereich angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b17d2-201">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="b17d2-202">Dies ist eine Instanz der **System.Windows.Media.Color**-Klasse.</span><span class="sxs-lookup"><span data-stu-id="b17d2-202">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="b17d2-203"><a name="dfc"></a> DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-203"><a name="dfc"></a> DebugForegroundColor</span></span>
  <span data-ttu-id="b17d2-204">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-204">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b17d2-205">Gibt die Vordergrundfarbe für den Debugtext an, der im Konsolenbereich angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b17d2-205">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="b17d2-206">Dies ist eine Instanz der **System.Windows.Media.Color**-Klasse.</span><span class="sxs-lookup"><span data-stu-id="b17d2-206">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor ="yellow"
```

###  <span data-ttu-id="b17d2-207"><a name="do"></a> DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="b17d2-207"><a name="do"></a> DefaultOptions</span></span>
  <span data-ttu-id="b17d2-208">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-208">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b17d2-209">Eine Sammlung von Eigenschaften, mit denen die Standardwerte angegeben werden, die bei Verwendung der Reset-Methoden verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b17d2-209">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

```
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions

SelectedScriptPaneState                   : Top
ShowDefaultSnippets                       : True
ShowToolBar                               : True
ShowOutlining                             : True
ShowLineNumbers                           : True
TokenColors                               : {[Attribute, #FF00BFFF], [Command, #FF0000FF], [CommandArgument, #FF8A2BE2], [CommandParameter, #FF000080]...}
ConsoleTokenColors                        : {[Attribute, #FFB0C4DE], [Command, #FFE0FFFF], [CommandArgument, #FFEE82EE], [CommandParameter, #FFFFE4B5]...}
XmlTokenColors                            : {[Comment, #FF006400], [CommentDelimiter, #FF008000], [ElementName, #FF8B0000], [MarkupExtension, #FFFF8C00]...}
DefaultOptions                            : Microsoft.PowerShell.Host.ISE.ISEOptions
FontSize                                  : 9
Zoom                                      : 100
FontName                                  : Lucida Console
ErrorForegroundColor                      : #FFFF0000
ErrorBackgroundColor                      : #00FFFFFF
WarningForegroundColor                    : #FFFF8C00
WarningBackgroundColor                    : #00FFFFFF
VerboseForegroundColor                    : #FF00FFFF
VerboseBackgroundColor                    : #00FFFFFF
DebugForegroundColor                      : #FF00FFFF
DebugBackgroundColor                      : #00FFFFFF
ConsolePaneBackgroundColor                : #FF012456
ConsolePaneTextBackgroundColor            : #FF012456
ConsolePaneForegroundColor                : #FFF5F5F5
ScriptPaneBackgroundColor                 : #FFFFFFFF
ScriptPaneForegroundColor                 : #FF000000
ShowWarningForDuplicateFiles              : True
ShowWarningBeforeSavingOnRun              : True
UseLocalHelp                              : True
AutoSaveMinuteInterval                    : 2
MruCount                                  : 10
ShowIntellisenseInConsolePane             : True
ShowIntellisenseInScriptPane              : True
UseEnterToSelectInConsolePaneIntellisense : True
UseEnterToSelectInScriptPaneIntellisense  : True
IntellisenseTimeoutInSeconds              : 3

```

###  <span data-ttu-id="b17d2-210"><a name="ebc"></a> ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-210"><a name="ebc"></a> ErrorBackgroundColor</span></span>
  <span data-ttu-id="b17d2-211">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-211">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b17d2-212">Gibt die Hintergrundfarbe für den Fehlertext an, der im Konsolenbereich angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b17d2-212">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="b17d2-213">Dies ist eine Instanz der **System.Windows.Media.Color**-Klasse.</span><span class="sxs-lookup"><span data-stu-id="b17d2-213">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor="black"
```

###  <span data-ttu-id="b17d2-214"><a name="efc"></a> ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-214"><a name="efc"></a> ErrorForegroundColor</span></span>
  <span data-ttu-id="b17d2-215">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-215">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b17d2-216">Gibt die Vordergrundfarbe für den Fehlertext an, der im Konsolenbereich angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b17d2-216">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="b17d2-217">Dies ist eine Instanz der **System.Windows.Media.Color**-Klasse.</span><span class="sxs-lookup"><span data-stu-id="b17d2-217">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor ="green"
```

###  <span data-ttu-id="b17d2-218"><a name="fn"></a> FontName</span><span class="sxs-lookup"><span data-stu-id="b17d2-218"><a name="fn"></a> FontName</span></span>
  <span data-ttu-id="b17d2-219">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-219">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b17d2-220">Gibt den Namen der Schriftart an, die derzeit im Skriptbereich und im Konsolenbereich verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b17d2-220">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```
# Changes the font used in both panes.
$psISE.Options.FontName = "courier new"
```

###  <span data-ttu-id="b17d2-221"><a name="fs"></a> FontSize</span><span class="sxs-lookup"><span data-stu-id="b17d2-221"><a name="fs"></a> FontSize</span></span>
  <span data-ttu-id="b17d2-222">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-222">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b17d2-223">Gibt den Schriftgrad als ganze Zahl an.</span><span class="sxs-lookup"><span data-stu-id="b17d2-223">Specifies the font size as an integer.</span></span> <span data-ttu-id="b17d2-224">Dieser wird im Skriptbereich, Befehlsbereich und Ausgabebereich verwendet.</span><span class="sxs-lookup"><span data-stu-id="b17d2-224">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="b17d2-225">Der gültige Wertebereich liegt zwischen 8 und 32.</span><span class="sxs-lookup"><span data-stu-id="b17d2-225">The valid range of values is 8 through 32.</span></span>

```
# Changes the font size in all panes.
$psISE.Options.FontSize = 20

```

###  <span data-ttu-id="b17d2-226"><a name="itis"></a> IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="b17d2-226"><a name="itis"></a> IntellisenseTimeoutInSeconds</span></span>
  <span data-ttu-id="b17d2-227">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-227">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b17d2-228">Gibt in Sekunden an, wie lange IntelliSense versucht, den gerade eingegebenen Text aufzulösen.</span><span class="sxs-lookup"><span data-stu-id="b17d2-228">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="b17d2-229">Nach dieser Anzahl von Sekunden tritt in IntelliSense eine Zeitüberschreitung auf, und Sie können mit der Eingabe fortfahren.</span><span class="sxs-lookup"><span data-stu-id="b17d2-229">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="b17d2-230">Der Standardwert sind 3 Sekunden.</span><span class="sxs-lookup"><span data-stu-id="b17d2-230">The default value is 3 seconds.</span></span> <span data-ttu-id="b17d2-231">Der Wert ist eine ganze Zahl.</span><span class="sxs-lookup"><span data-stu-id="b17d2-231">The value is an integer.</span></span>

```
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

###  <span data-ttu-id="b17d2-232"><a name="mc"></a> MruCount</span><span class="sxs-lookup"><span data-stu-id="b17d2-232"><a name="mc"></a> MruCount</span></span>
  <span data-ttu-id="b17d2-233">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-233">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b17d2-234">Gibt die Anzahl der zuletzt geöffneten Dateien an, die Windows PowerShell ISE nachverfolgt und am unteren Rand des Menüs **Datei öffnen** anzeigt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-234">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="b17d2-235">Der Standardwert ist 10.</span><span class="sxs-lookup"><span data-stu-id="b17d2-235">The default value is 10.</span></span> <span data-ttu-id="b17d2-236">Der Wert ist eine ganze Zahl.</span><span class="sxs-lookup"><span data-stu-id="b17d2-236">The value is an integer.</span></span>

```
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

###  <span data-ttu-id="b17d2-237"><a name="opbc"></a> OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-237"><a name="opbc"></a> OutputPaneBackgroundColor</span></span>
  <span data-ttu-id="b17d2-238">Dieses Feature ist in Windows PowerShell ISE 2.0 enthalten, wurde in höheren Versionen von ISE aber entfernt oder umbenannt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-238">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="b17d2-239">Informationen zu höheren Versionen finden Sie unter [ConsolePaneBackgroundColor](#conpbc).</span><span class="sxs-lookup"><span data-stu-id="b17d2-239">For later versions, see [ConsolePaneBackgroundColor](#conpbc).</span></span>

 <span data-ttu-id="b17d2-240">Die Lese-/Schreibeigenschaft, die die Hintergrundfarbe für den Ausgabebereich selbst abruft oder festlegt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-240">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="b17d2-241">Dies ist eine Instanz der **System.Windows.Media.Color**-Klasse.</span><span class="sxs-lookup"><span data-stu-id="b17d2-241">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = "gold"

```

###  <span data-ttu-id="b17d2-242"><a name="optfc"></a> OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-242"><a name="optfc"></a> OutputPaneTextForegroundColor</span></span>
  <span data-ttu-id="b17d2-243">Dieses Feature ist in Windows PowerShell ISE 2.0 enthalten, wurde in höheren Versionen von ISE aber entfernt oder umbenannt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-243">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="b17d2-244">Informationen zu höheren Versionen finden Sie unter [ConsolePaneForegroundColor](#conpfc).</span><span class="sxs-lookup"><span data-stu-id="b17d2-244">For later versions, see [ConsolePaneForegroundColor](#conpfc).</span></span>

 <span data-ttu-id="b17d2-245">Die Lese-/Schreibeigenschaft, mit der die Vordergrundfarbe des Texts im Ausgabereich in Windows PowerShell ISE 2.0 geändert wird.</span><span class="sxs-lookup"><span data-stu-id="b17d2-245">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = "blue"

```

###  <span data-ttu-id="b17d2-246"><a name="optbc"></a> OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-246"><a name="optbc"></a> OutputPaneTextBackgroundColor</span></span>
  <span data-ttu-id="b17d2-247">Dieses Feature ist in Windows PowerShell ISE 2.0 enthalten, wurde in höheren Versionen von ISE aber entfernt oder umbenannt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-247">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="b17d2-248">Informationen zu höheren Versionen finden Sie unter [ConsolePaneTextBackgroundColor](#conptbc).</span><span class="sxs-lookup"><span data-stu-id="b17d2-248">For later versions, see [ConsolePaneTextBackgroundColor](#conptbc).</span></span>

 <span data-ttu-id="b17d2-249">Die Lese-/Schreibeigenschaft, mit der die Hintergrundfarbe des Texts im Ausgabereich geändert wird.</span><span class="sxs-lookup"><span data-stu-id="b17d2-249">The read/write property that changes the background color of the text in the Output pane.</span></span>

```
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = "pink"
```

###  <span data-ttu-id="b17d2-250"><a name="spbc"></a> ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-250"><a name="spbc"></a> ScriptPaneBackgroundColor</span></span>
  <span data-ttu-id="b17d2-251">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-251">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b17d2-252">Die Lese-/Schreibeigenschaft, mit der die Hintergrundfarbe für Dateien abgerufen oder festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="b17d2-252">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="b17d2-253">Dies ist eine Instanz der **System.Windows.Media.Color**-Klasse.</span><span class="sxs-lookup"><span data-stu-id="b17d2-253">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```

# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = ”yellow”

```

###  <span data-ttu-id="b17d2-254"><a name="spfc"></a> ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-254"><a name="spfc"></a> ScriptPaneForegroundColor</span></span>
  <span data-ttu-id="b17d2-255">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-255">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b17d2-256">Die Lese-/Schreibeigenschaft, mit der die Vordergrundfarbe für Nicht-Skriptdateien im Skriptbereich abgerufen oder festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="b17d2-256">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="b17d2-257">Verwenden Sie zum Festlegen der Vordergrundfarbe für Skriptdateien die [TokenColors](The-ISEOptions-Object.md#tc)-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="b17d2-257">To set the foreground color for script files, use the [TokenColors](The-ISEOptions-Object.md#tc) property.</span></span>

```
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = "green"

```

###  <span data-ttu-id="b17d2-258"><a name="ssps"></a> SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="b17d2-258"><a name="ssps"></a> SelectedScriptPaneState</span></span>
  <span data-ttu-id="b17d2-259">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-259">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b17d2-260">Die Lese-/Schreibeigenschaft, die die Position des Skriptbereichs in der Anzeige abruft oder festlegt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-260">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="b17d2-261">Die Zeichenfolge kann „Maximized“, „Top“ oder „Right“ lauten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-261">The string can be either "Maximized", "Top", or "Right".</span></span>

```
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = "Top"
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = "Right"
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = "Maximized"

```

###  <span data-ttu-id="b17d2-262"><a name="sds"></a> ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="b17d2-262"><a name="sds"></a> ShowDefaultSnippets</span></span>
  <span data-ttu-id="b17d2-263">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b17d2-264">Gibt an, ob die **STRG+J**-Codeausschnittliste den in Windows PowerShell enthaltenen Startersatz umfasst.</span><span class="sxs-lookup"><span data-stu-id="b17d2-264">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="b17d2-265">Bei **$false** werden nur benutzerdefinierte Codeausschnitte in der **STRG+J**-Liste angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-265">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="b17d2-266">Der Standardwert ist **$true**.</span><span class="sxs-lookup"><span data-stu-id="b17d2-266">The default value is **$true**.</span></span>

```
# Hide the default snippets from the CTRL+J list.
$psISe.Options.ShowDefaultSnippets = $false
```

###  <span data-ttu-id="b17d2-267"><a name="siicp"></a> ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="b17d2-267"><a name="siicp"></a> ShowIntellisenseInConsolePane</span></span>
  <span data-ttu-id="b17d2-268">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-268">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b17d2-269">Gibt an, ob IntelliSense Syntax-, Parameter- und Wertvorschläge im Konsolenbereich anzeigt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-269">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="b17d2-270">Der Standardwert ist **$true**.</span><span class="sxs-lookup"><span data-stu-id="b17d2-270">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the console pane.
$psISe.Options.ShowIntellisenseInConsolePane = $false
```

###  <span data-ttu-id="b17d2-271"><a name="siisp"></a> ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="b17d2-271"><a name="siisp"></a> ShowIntellisenseInScriptPane</span></span>
  <span data-ttu-id="b17d2-272">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-272">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b17d2-273">Gibt an, ob IntelliSense Syntax-, Parameter- und Wertvorschläge im Skriptbereich anzeigt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-273">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="b17d2-274">Der Standardwert ist **$true**.</span><span class="sxs-lookup"><span data-stu-id="b17d2-274">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the Script pane.
$psISe.Options.ShowIntellisenseInScriptPane = $false
```

###  <span data-ttu-id="b17d2-275"><a name="sln"></a> ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="b17d2-275"><a name="sln"></a> ShowLineNumbers</span></span>
  <span data-ttu-id="b17d2-276">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-276">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b17d2-277">Gibt an, ob im Skriptbereich Zeilennummern am linken Rand angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b17d2-277">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="b17d2-278">Der Standardwert ist **$true**.</span><span class="sxs-lookup"><span data-stu-id="b17d2-278">The default value is **$true**.</span></span>

```
# Turn off line numbers in the Script pane.
$psISe.Options.ShowLineNumbers = $false
```

###  <span data-ttu-id="b17d2-279"><a name="so"></a> ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="b17d2-279"><a name="so"></a> ShowOutlining</span></span>
  <span data-ttu-id="b17d2-280">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-280">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b17d2-281">Gibt an, ob im Skriptbereich erweiterbare und reduzierbare Klammern neben Codeabschnitten am linken Rand angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b17d2-281">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="b17d2-282">Wenn sie angezeigt werden, können Sie auf das Minuszeichen \(-\) neben einem Textblock klicken, um ihn zuzuklappen, oder auf das Pluszeichen \(+\), um einen Textblock auszuklappen.</span><span class="sxs-lookup"><span data-stu-id="b17d2-282">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="b17d2-283">Der Standardwert ist **$true**.</span><span class="sxs-lookup"><span data-stu-id="b17d2-283">The default value is **$true**.</span></span>

```
# Turn off outlining in the Script pane.
$psISe.Options.ShowOutlining = $false
```

###  <span data-ttu-id="b17d2-284"><a name="stb"></a> ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="b17d2-284"><a name="stb"></a> ShowToolBar</span></span>
  <span data-ttu-id="b17d2-285">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b17d2-286">Gibt an, ob die ISE-Symbolleiste am oberen Rand des Windows PowerShell ISE-Fensters angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b17d2-286">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="b17d2-287">Der Standardwert ist **$true**.</span><span class="sxs-lookup"><span data-stu-id="b17d2-287">The default value is **$true**.</span></span>

```
# Show the toolbar.
$psISe.Options.ShowToolBar = $true
```

###  <span data-ttu-id="b17d2-288"><a name="swbsor"></a> ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="b17d2-288"><a name="swbsor"></a> ShowWarningBeforeSavingOnRun</span></span>
  <span data-ttu-id="b17d2-289">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-289">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b17d2-290">Gibt an, ob eine Warnung angezeigt wird, wenn ein Skript vor dem Ausführen automatisch gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="b17d2-290">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="b17d2-291">Der Standardwert ist **$true**.</span><span class="sxs-lookup"><span data-stu-id="b17d2-291">The default value is **$true**.</span></span>

```
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun=$true

```

###  <span data-ttu-id="b17d2-292"><a name="swfdf"></a> ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="b17d2-292"><a name="swfdf"></a> ShowWarningForDuplicateFiles</span></span>
  <span data-ttu-id="b17d2-293">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-293">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b17d2-294">Gibt an, ob eine Warnung angezeigt wird, wenn die gleiche Datei auf mehreren PowerShell-Registerkarten geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="b17d2-294">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="b17d2-295">Wenn dies auf **$true** festgelegt ist und eine Datei auf mehreren Registerkarten angezeigt werden soll, wird die folgende Meldung angezeigt: „Eine Kopie dieser Datei ist in einer anderen PowerShell-Registerkarte geöffnet.</span><span class="sxs-lookup"><span data-stu-id="b17d2-295">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab.</span></span> <span data-ttu-id="b17d2-296">Änderungen an dieser Datei betreffen alle geöffneten Kopien.“</span><span class="sxs-lookup"><span data-stu-id="b17d2-296">Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="b17d2-297">Der Standardwert ist **$true**.</span><span class="sxs-lookup"><span data-stu-id="b17d2-297">The default value is **$true**.</span></span>

```
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true

```

###  <span data-ttu-id="b17d2-298"><a name="tc"></a> TokenColors</span><span class="sxs-lookup"><span data-stu-id="b17d2-298"><a name="tc"></a> TokenColors</span></span>
  <span data-ttu-id="b17d2-299">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-299">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b17d2-300">Gibt die Farben der IntelliSense-Token im Windows PowerShell ISE-Skriptbereich an.</span><span class="sxs-lookup"><span data-stu-id="b17d2-300">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="b17d2-301">Diese Eigenschaft ist ein Wörterbuchobjekt, das Name-Wert-Paare von Tokentypen und Farben für den Skriptbereich enthält.</span><span class="sxs-lookup"><span data-stu-id="b17d2-301">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="b17d2-302">Informationen zum Ändern der Farben der IntelliSense-Token im Konsolenbereich finden Sie unter [ConsoleTokenColors](#contc).</span><span class="sxs-lookup"><span data-stu-id="b17d2-302">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#contc).</span></span> <span data-ttu-id="b17d2-303">Informationen zum Zurücksetzen der Farben auf die Standardwerte finden Sie unter [RestoreDefaultTokenColors()](#rdtc).</span><span class="sxs-lookup"><span data-stu-id="b17d2-303">To reset the colors to the default values, see [RestoreDefaultTokenColors()](#rdtc).</span></span> <span data-ttu-id="b17d2-304">Tokenfarben können für folgende Elemente festgelegt werden: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="b17d2-304">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"

```

###  <span data-ttu-id="b17d2-305"><a name="uetsicpi"></a> UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="b17d2-305"><a name="uetsicpi"></a> UseEnterToSelectInConsolePaneIntellisense</span></span>
  <span data-ttu-id="b17d2-306">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-306">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b17d2-307">Gibt an, ob Sie mit der Eingabetaste eine von IntelliSense bereitgestellte Option im Konsolenbereich auswählen können.</span><span class="sxs-lookup"><span data-stu-id="b17d2-307">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="b17d2-308">Der Standardwert ist **$true**.</span><span class="sxs-lookup"><span data-stu-id="b17d2-308">The default value is **$true**.</span></span>

```
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$false

```

###  <span data-ttu-id="b17d2-309"><a name="uetsispi"></a> UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="b17d2-309"><a name="uetsispi"></a> UseEnterToSelectInScriptPaneIntellisense</span></span>
  <span data-ttu-id="b17d2-310">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-310">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b17d2-311">Gibt an, ob Sie mit der Eingabetaste eine von IntelliSense bereitgestellte Option im Skriptbereich auswählen können.</span><span class="sxs-lookup"><span data-stu-id="b17d2-311">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="b17d2-312">Der Standardwert ist **$true**.</span><span class="sxs-lookup"><span data-stu-id="b17d2-312">The default value is **$true**.</span></span>

```
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$true

```

###  <span data-ttu-id="b17d2-313"><a name="ulh"></a> UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="b17d2-313"><a name="ulh"></a> UseLocalHelp</span></span>
  <span data-ttu-id="b17d2-314">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-314">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b17d2-315">Gibt an, ob die lokal installierte Hilfe oder die Onlinehilfe der TechNet-Bibliothek angezeigt wird, wenn der Cursor auf einem Schlüsselwort positioniert ist und Sie F1 drücken.</span><span class="sxs-lookup"><span data-stu-id="b17d2-315">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="b17d2-316">Wenn dies auf **$true** festgelegt ist, werden in einem Popupfenster Inhalte aus der lokal installierten Hilfe angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-316">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="b17d2-317">Sie können die Hilfedateien mit dem Befehl `Update-Help` installieren.</span><span class="sxs-lookup"><span data-stu-id="b17d2-317">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="b17d2-318">Wenn dies auf **$false** festgelegt ist, wird eine Seite in der TechNet-Bibliothek im Browser geöffnet.</span><span class="sxs-lookup"><span data-stu-id="b17d2-318">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp=$false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp=$true

```

###  <span data-ttu-id="b17d2-319"><a name="vbc"></a> VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-319"><a name="vbc"></a> VerboseBackgroundColor</span></span>
  <span data-ttu-id="b17d2-320">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-320">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b17d2-321">Gibt die Hintergrundfarbe für ausführlichen Text an, der im Konsolenbereich angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b17d2-321">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="b17d2-322">Dies ist ein **System.Windows.Media.Color**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-322">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="b17d2-323"><a name="vfc"></a> VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-323"><a name="vfc"></a> VerboseForegroundColor</span></span>
  <span data-ttu-id="b17d2-324">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-324">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b17d2-325">Gibt die Vordergrundfarbe für ausführlichen Text an, der im Konsolenbereich angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b17d2-325">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="b17d2-326">Dies ist ein **System.Windows.Media.Color**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-326">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor =”yellow”
```

###  <span data-ttu-id="b17d2-327"><a name="wbc"></a> WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-327"><a name="wbc"></a> WarningBackgroundColor</span></span>
  <span data-ttu-id="b17d2-328">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-328">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b17d2-329">Gibt die Hintergrundfarbe für Warntext an, der im Konsolenbereich angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b17d2-329">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="b17d2-330">Dies ist ein **System.Windows.Media.Color**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-330">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="b17d2-331"><a name="wfc"></a> WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b17d2-331"><a name="wfc"></a> WarningForegroundColor</span></span>
  <span data-ttu-id="b17d2-332">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-332">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="b17d2-333">Gibt die Vordergrundfarbe für Warntext an, der im Ausgabebereich angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b17d2-333">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="b17d2-334">Dies ist ein **System.Windows.Media.Color**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-334">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor =”yellow”
```

###  <span data-ttu-id="b17d2-335"><a name="xtc"></a> XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="b17d2-335"><a name="xtc"></a> XmlTokenColors</span></span>
  <span data-ttu-id="b17d2-336">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-336">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b17d2-337">Gibt ein Wörterbuchobjekt an, das Name-Wert-Paare von Tokentypen und Farben für XML-Inhalte enthält, die in Windows PowerShell ISE angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b17d2-337">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="b17d2-338">Tokenfarben können für folgende Elemente festgelegt werden: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="b17d2-338">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="b17d2-339">Siehe auch [RestoreDefaultXmlTokenColors()](#rdxtc).</span><span class="sxs-lookup"><span data-stu-id="b17d2-339">Also see [RestoreDefaultXmlTokenColors()](#rdxtc).</span></span>

```
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = "green"
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = "magenta"

```

###  <span data-ttu-id="b17d2-340"><a name="z"></a> Zoom</span><span class="sxs-lookup"><span data-stu-id="b17d2-340"><a name="z"></a> Zoom</span></span>
  <span data-ttu-id="b17d2-341">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="b17d2-341">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="b17d2-342">Gibt die relative Größe des Texts im Konsolenbereich und Skriptbereich an.</span><span class="sxs-lookup"><span data-stu-id="b17d2-342">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="b17d2-343">Der Standardwert ist 100.</span><span class="sxs-lookup"><span data-stu-id="b17d2-343">The default value is 100.</span></span> <span data-ttu-id="b17d2-344">Bei kleineren Werten wird der Text in Windows PowerShell ISE kleiner angezeigt, bei größeren Werten wird er größer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b17d2-344">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="b17d2-345">Der Wert ist eine ganze Zahl zwischen 20 und 400.</span><span class="sxs-lookup"><span data-stu-id="b17d2-345">The value is an integer that ranges from 20 to 400.</span></span>

```
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="b17d2-346">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b17d2-346">See Also</span></span>
- [<span data-ttu-id="b17d2-347">Das Windows PowerShell ISE-Skriptobjektmodell</span><span class="sxs-lookup"><span data-stu-id="b17d2-347">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="b17d2-348">Referenz zum Windows PowerShell ISE-Objektmodell</span><span class="sxs-lookup"><span data-stu-id="b17d2-348">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

