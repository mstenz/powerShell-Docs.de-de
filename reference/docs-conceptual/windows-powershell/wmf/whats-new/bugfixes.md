---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Fehlerkorrekturen in WMF 5.1
ms.openlocfilehash: 8edf295eb6304dc04de2fa5d3792b1c2fc4b01f3
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809306"
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="3fca9-103">Fehlerkorrekturen in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="3fca9-103">Bug Fixes in WMF 5.1</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="3fca9-104">Behebung von Programmfehlern</span><span class="sxs-lookup"><span data-stu-id="3fca9-104">Bug fixes</span></span>

<span data-ttu-id="3fca9-105">Die folgenden auffälligen Fehler wurden in WMF 5.1 behoben:</span><span class="sxs-lookup"><span data-stu-id="3fca9-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-psmodulepath"></a><span data-ttu-id="3fca9-106">AutoErmittlung von Modulen berücksichtigt PSModulePath vollständig</span><span class="sxs-lookup"><span data-stu-id="3fca9-106">Module auto-discovery fully honors PSModulePath</span></span>

<span data-ttu-id="3fca9-107">Die AutoErmittlung von Modulen (d. h. das automatische Laden von Modulen ohne explizites Ausführen von „Import-Module“ beim Aufrufen eines Befehls) wurde in WMF 3 eingeführt.</span><span class="sxs-lookup"><span data-stu-id="3fca9-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span> <span data-ttu-id="3fca9-108">Nach der Einführung suchte PowerShell nach Befehlen in `$PSHome\Modules`, bevor `$env:PSModulePath` verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="3fca9-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="3fca9-109">In WMF 5.1 ändert sich dieses Verhalten so, dass `$env:PSModulePath` vollständig berücksichtigt wird.</span><span class="sxs-lookup"><span data-stu-id="3fca9-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span> <span data-ttu-id="3fca9-110">Dadurch kann ein vom Benutzer erstelltes Modul, das von PowerShell bereitgestellte Befehle definiert (z. B. `Get-ChildItem`), automatisch geladen werden und den integrierten Befehl ordnungsgemäß überschreiben.</span><span class="sxs-lookup"><span data-stu-id="3fca9-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="3fca9-111">Keine Hartcodierung mehr von „-Encoding Unicode“ bei der Umleitung von Dateien</span><span class="sxs-lookup"><span data-stu-id="3fca9-111">File redirection no longer hard-codes -Encoding Unicode</span></span>

<span data-ttu-id="3fca9-112">In allen früheren Versionen von PowerShell konnte die vom Dateiumleitungsoperator verwendete Dateicodierung nicht gesteuert werden.</span><span class="sxs-lookup"><span data-stu-id="3fca9-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator.</span></span>

<span data-ttu-id="3fca9-113">Ab WMF 5.1 können Sie jetzt die Dateicodierung der Umleitung durch Festlegen von `$PSDefaultParameterValues` ändern.</span><span class="sxs-lookup"><span data-stu-id="3fca9-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="3fca9-114">Korrektur einer Regression beim Zugriff auf Member von System.Reflection.TypeInfo</span><span class="sxs-lookup"><span data-stu-id="3fca9-114">Fixed a regression in accessing members of System.Reflection.TypeInfo</span></span>

<span data-ttu-id="3fca9-115">Durch eine in WMF 5.0 eingeführte Regression wurde der Zugriff auf Member von `System.Reflection.RuntimeType`, z. B. `[int].ImplementedInterfaces`, unterbrochen.</span><span class="sxs-lookup"><span data-stu-id="3fca9-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, for example, `[int].ImplementedInterfaces`.</span></span> <span data-ttu-id="3fca9-116">Dieser Fehler wurde in WMF 5.1 behoben.</span><span class="sxs-lookup"><span data-stu-id="3fca9-116">This bug has been fixed in WMF 5.1.</span></span>

### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="3fca9-117">Korrektur einiger Probleme mit COM-Objekten</span><span class="sxs-lookup"><span data-stu-id="3fca9-117">Fixed some issues with COM objects</span></span>

<span data-ttu-id="3fca9-118">In WMF 5.0 wurde ein neuer COM-Binder zum Aufrufen von Methoden für COM-Objekte und den Zugriff auf Eigenschaften von COM-Objekten eingeführt.</span><span class="sxs-lookup"><span data-stu-id="3fca9-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span> <span data-ttu-id="3fca9-119">Dieser neue Binder verbesserte die Leistung erheblich, verursachte jedoch auch einige Fehler, die in WMF 5.1 behoben wurden.</span><span class="sxs-lookup"><span data-stu-id="3fca9-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="3fca9-120">Argumentkonvertierungen erfolgten nicht immer ordnungsgemäß</span><span class="sxs-lookup"><span data-stu-id="3fca9-120">Argument conversions were not always performed correctly</span></span>

<span data-ttu-id="3fca9-121">Siehe folgendes Beispiel:</span><span class="sxs-lookup"><span data-stu-id="3fca9-121">In the following example:</span></span>

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="3fca9-122">Die **SendKeys**-Methode erwartet eine Zeichenfolge, aber PowerShell konvertierte „char“ nicht in „string“, wodurch die Konvertierung in der **IDispatch::Invoke**-Methode verzögert wurde. Diese Methode verwendet **VariantChangeType** zum Ausführen der Konvertierung.</span><span class="sxs-lookup"><span data-stu-id="3fca9-122">The **SendKeys** method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to **IDispatch::Invoke**, which uses **VariantChangeType** to do the conversion.</span></span> <span data-ttu-id="3fca9-123">In diesem Beispiel hat dies zum Senden der Schlüssel „1“, „7“ und „3 anstelle des erwarteten Schlüssels **Volume.Mute** geführt.</span><span class="sxs-lookup"><span data-stu-id="3fca9-123">In this example, this resulted in sending the keys '1', '7', and '3' instead of the expected **Volume.Mute** key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="3fca9-124">Die Verarbeitung aufzählbarer COM-Objekte erfolgte nicht immer ordnungsgemäß</span><span class="sxs-lookup"><span data-stu-id="3fca9-124">Enumerable COM objects not always handled correctly</span></span>

<span data-ttu-id="3fca9-125">PowerShell zählt normalerweise die meisten aufzählbaren Objekte auf. Doch eine in WMF 5.0 eingeführte Regression verhinderte die Aufzählung von COM-Objekten, die „IEnumerable“ implementieren.</span><span class="sxs-lookup"><span data-stu-id="3fca9-125">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span> <span data-ttu-id="3fca9-126">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="3fca9-126">For example:</span></span>

```powershell
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

<span data-ttu-id="3fca9-127">Im obigen Beispiel schreibt WMF 5.0 fälschlicherweise **Scripting.Dictionary** in die Pipeline, anstatt die Schlüssel-Wert-Paare aufzuzählen.</span><span class="sxs-lookup"><span data-stu-id="3fca9-127">In the above example, WMF 5.0 incorrectly wrote the **Scripting.Dictionary** to the pipeline instead of enumerating the key/value pairs.</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="3fca9-128">[ordered] war innerhalb von Klassen nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="3fca9-128">[ordered] was not allowed inside classes</span></span>

<span data-ttu-id="3fca9-129">In WMF 5.0 wurden Klassen mit einer in Klassen verwendeten Überprüfung von Typliteralen eingeführt.</span><span class="sxs-lookup"><span data-stu-id="3fca9-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span> <span data-ttu-id="3fca9-130">`[ordered]` sieht wie ein Typliteral aus, ist jedoch kein echter .NET-Typ.</span><span class="sxs-lookup"><span data-stu-id="3fca9-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span> <span data-ttu-id="3fca9-131">WMF 5.0 meldete fälschlicherweise einen Fehler für `[ordered]` innerhalb einer Klasse:</span><span class="sxs-lookup"><span data-stu-id="3fca9-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```

### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="3fca9-132">Hilfe zu Themen mit mehreren Versionen funktioniert nicht</span><span class="sxs-lookup"><span data-stu-id="3fca9-132">Help on About topics with multiple versions does not work</span></span>

<span data-ttu-id="3fca9-133">Wenn Sie vor WMF 5.1 über mehrere Versionen eines installierten Modus verfügt haben und es für alle nur ein Hilfethema gab, z. B. „about_PSReadline“, gab `help about_PSReadline` mehrere Themen zurück, ohne dass es eine erkennbare Möglichkeit gab, die tatsächliche Hilfe anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3fca9-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="3fca9-134">In WMF 5.1 wurde dieser Fehler behoben, sodass nur die Hilfe für die neueste Version des Themas zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="3fca9-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="3fca9-135">`Get-Help` bietet keine Möglichkeit anzugeben, für welche Version Sie Hilfe wünschen.</span><span class="sxs-lookup"><span data-stu-id="3fca9-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span> <span data-ttu-id="3fca9-136">Die Problemumgebung besteht darin, zum Verzeichnis „Modules“ zu navigieren und die Hilfe direkt mit einem Tool wie Ihrem bevorzugten Editor anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3fca9-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span>

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="3fca9-137">„powershell.exe“ wird beim Lesen aus STDIN beendet</span><span class="sxs-lookup"><span data-stu-id="3fca9-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="3fca9-138">Kunden verwenden `powershell -command -` aus nativen Apps heraus zum Ausführen von PowerShell; die Übergabe im Skript über STDIN ist leider aufgrund anderer Änderungen am Konsolenhost fehlerhaft.</span><span class="sxs-lookup"><span data-stu-id="3fca9-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken by other changes in the console host.</span></span>

<span data-ttu-id="3fca9-139">Dies wurde für Version 5.1 im Windows 10 Anniversary Update behoben.</span><span class="sxs-lookup"><span data-stu-id="3fca9-139">This is fixed for version 5.1 in the Windows 10 Anniversary Update.</span></span>

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="3fca9-140">„powerShell.exe“ führt beim Start zu einer Spitze in der CPU-Auslastung</span><span class="sxs-lookup"><span data-stu-id="3fca9-140">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="3fca9-141">PowerShell überprüft mithilfe einer WMI-Abfrage, ob der Start über die Gruppenrichtlinie erfolgt ist, um Verzögerung bei der Anmeldung zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="3fca9-141">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span> <span data-ttu-id="3fca9-142">Am Ende der WMI-Abfrage wird „tzres.mui.dll“ in jeden Prozess auf dem System hinzugefügt, da die Klasse **WMI-Win32_Process** versucht, lokale Zeitzoneninformationen abzurufen.</span><span class="sxs-lookup"><span data-stu-id="3fca9-142">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI **Win32_Process** class attempts to retrieve local timezone information.</span></span> <span data-ttu-id="3fca9-143">Dies führt zu einer großen CPU-Spitze in **wmiprvse** (dem WMI-Anbieterhost).</span><span class="sxs-lookup"><span data-stu-id="3fca9-143">This results in a large CPU spike in **wmiprvse** (the WMI provider host).</span></span> <span data-ttu-id="3fca9-144">Lösung: Verwenden Sie Win32-API-Aufrufe anstelle von WMI, um die gleichen Informationen abzurufen.</span><span class="sxs-lookup"><span data-stu-id="3fca9-144">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>
