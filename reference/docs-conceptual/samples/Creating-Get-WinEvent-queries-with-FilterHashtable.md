---
ms.date: 3/18/2019
title: Erstellen von Get-WinEvent-Abfragen mit FilterHashtable
ms.openlocfilehash: 28ba3c99a297944003a28eaba7de34b77d9df536
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293281"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a><span data-ttu-id="d540a-102">Erstellen von Get-WinEvent-Abfragen mit FilterHashtable</span><span class="sxs-lookup"><span data-stu-id="d540a-102">Creating Get-WinEvent queries with FilterHashtable</span></span>

<span data-ttu-id="d540a-103">Den **Scripting Guy**-Original-Blogbeitrag vom 3. Juni 2014 können Sie unter [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/) (Verwenden von FilterHashTable zum Filtern des Ereignisprotokolls mit PowerShell) lesen.</span><span class="sxs-lookup"><span data-stu-id="d540a-103">To read the original June 3, 2014 **Scripting Guy** blog post, see [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span></span>

<span data-ttu-id="d540a-104">Dieser Artikel ist ein Auszug des ursprünglichen Blogbeitrags und erläutert die Verwendung des **FilterHashtable**-Parameters des `Get-WinEvent`-Cmdlets zum Filtern von Ereignisprotokollen.</span><span class="sxs-lookup"><span data-stu-id="d540a-104">This article is an excerpt of the original blog post and explains how to use the `Get-WinEvent` cmdlet's **FilterHashtable** parameter to filter event logs.</span></span> <span data-ttu-id="d540a-105">Das PowerShell `Get-WinEvent`-Cmdlet bietet ein leistungsstarkes Verfahren zum Filtern von Windows-Ereignis- und Diagnoseprotokollen.</span><span class="sxs-lookup"><span data-stu-id="d540a-105">PowerShell's `Get-WinEvent` cmdlet is a powerful method to filter Windows event and diagnostic logs.</span></span> <span data-ttu-id="d540a-106">Die Leistung wird besser, wenn eine `Get-WinEvent`-Abfrage den **FilterHashtable**-Parameter nutzt.</span><span class="sxs-lookup"><span data-stu-id="d540a-106">Performance improves when a `Get-WinEvent` query uses the **FilterHashtable** parameter.</span></span>

<span data-ttu-id="d540a-107">Bei der Arbeit mit großen Ereignisprotokollen ist es nicht effizient, Objekte die Pipeline hinab an einen `Where-Object`-Befehl zu senden.</span><span class="sxs-lookup"><span data-stu-id="d540a-107">When you work with large event logs, it's not efficient to send objects down the pipeline to a `Where-Object` command.</span></span> <span data-ttu-id="d540a-108">Vor PowerShell 6 war das `Get-EventLog`-Cmdlet eine weitere Option, Protokolldaten abzurufen.</span><span class="sxs-lookup"><span data-stu-id="d540a-108">Prior to PowerShell 6, the `Get-EventLog` cmdlet was another option to get log data.</span></span> <span data-ttu-id="d540a-109">Beispielsweise sind die folgenden Befehle zum Filtern der **Microsoft-Windows-Defrag**-Protokolle ineffizient:</span><span class="sxs-lookup"><span data-stu-id="d540a-109">For example, the following commands are inefficient to filter the **Microsoft-Windows-Defrag** logs:</span></span>

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

<span data-ttu-id="d540a-110">Der folgende Befehl verwendet eine Hashtabelle, die die Leistung steigert:</span><span class="sxs-lookup"><span data-stu-id="d540a-110">The following command uses a hash table that improves the performance:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a><span data-ttu-id="d540a-111">Blogbeiträge zur Enumeration</span><span class="sxs-lookup"><span data-stu-id="d540a-111">Blog posts about enumeration</span></span>

<span data-ttu-id="d540a-112">Dieser Artikel enthält Informationen zur Verwendung von Enumerationswerten in einer Hashtabelle.</span><span class="sxs-lookup"><span data-stu-id="d540a-112">This article presents information about how to use enumerated values in a hash table.</span></span> <span data-ttu-id="d540a-113">Weitere Informationen über Enumeration finden Sie in diesen **Scripting Guy**-Blogbeiträgen.</span><span class="sxs-lookup"><span data-stu-id="d540a-113">For more information about enumeration, read these **Scripting Guy** blog posts.</span></span> <span data-ttu-id="d540a-114">Um eine Funktion zu erstellen, die die Enumerationswerte zurückgibt, lesen Sie [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values) (Enumerationen und Werte).</span><span class="sxs-lookup"><span data-stu-id="d540a-114">To create a function that returns the enumerated values, see [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span></span>
<span data-ttu-id="d540a-115">Weitere Informationen finden Sie in der [Scripting Guy-Reihe von Blogbeiträgen zur Enumeration](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span><span class="sxs-lookup"><span data-stu-id="d540a-115">For more information, see the [Scripting Guy series of blog posts about enumeration](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span></span>

## <a name="hash-table-keyvalue-pairs"></a><span data-ttu-id="d540a-116">Hashtabellen-Schlüssel/Wert-Paare</span><span class="sxs-lookup"><span data-stu-id="d540a-116">Hash table key/value pairs</span></span>

<span data-ttu-id="d540a-117">Um effiziente Abfragen zu erstellen, verwenden Sie das `Get-WinEvent`-Cmdlet mit dem **FilterHashtable**-Parameter.</span><span class="sxs-lookup"><span data-stu-id="d540a-117">To build efficient queries, use the `Get-WinEvent` cmdlet with the **FilterHashtable** parameter.</span></span>
<span data-ttu-id="d540a-118">**FilterHashtable** akzeptiert eine Hashtabelle als Filter, um bestimmte Informationen aus Windows-Ereignisprotokollen abzurufen.</span><span class="sxs-lookup"><span data-stu-id="d540a-118">**FilterHashtable** accepts a hash table as a filter to get specific information from Windows event logs.</span></span> <span data-ttu-id="d540a-119">Eine Hashtabelle verwendet **Schlüssel/Wert-Paare**.</span><span class="sxs-lookup"><span data-stu-id="d540a-119">A hash table uses **key/value** pairs.</span></span> <span data-ttu-id="d540a-120">Weitere Informationen zu Hashtabellen finden Sie unter [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables) (Informationen zu Hashtabellen).</span><span class="sxs-lookup"><span data-stu-id="d540a-120">For more information about hash tables, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="d540a-121">Wenn sich die **Schlüssel/Wert**-Paare in der gleichen Zeile befinden, müssen sie durch ein Semikolon getrennt werden.</span><span class="sxs-lookup"><span data-stu-id="d540a-121">If the **key/value** pairs are on the same line, they must be separated by a semicolon.</span></span> <span data-ttu-id="d540a-122">Wenn sich jedes **Schlüssel/Wert**-Paar in einer separaten Zeile befindet, ist kein Semikolon erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d540a-122">If each **key/value** pair is on a separate line, the semicolon isn't needed.</span></span> <span data-ttu-id="d540a-123">Beispielsweise werden in diesem Artikel **Schlüssel/Wert**-Paare in separaten Zeilen angeordnet und keine Semikola verwendet.</span><span class="sxs-lookup"><span data-stu-id="d540a-123">For example, this article places **key/value** pairs on separate lines and doesn't use semicolons.</span></span>

<span data-ttu-id="d540a-124">Dieses Beispiel nutzt mehrere der **Schlüssel/Wert**-Paare des **FilterHashtable**-Parameters.</span><span class="sxs-lookup"><span data-stu-id="d540a-124">This sample uses several of the **FilterHashtable** parameter's **key/value** pairs.</span></span> <span data-ttu-id="d540a-125">Die vollständige Abfrage beinhaltet **LogName**, **ProviderName**, **Keywords**, **ID** und **Level**.</span><span class="sxs-lookup"><span data-stu-id="d540a-125">The completed query includes **LogName**, **ProviderName**, **Keywords**, **ID**, and **Level**.</span></span>

<span data-ttu-id="d540a-126">Die akzeptierten **Schlüssel/Wert**-Paare sind in der folgenden Tabelle dargestellt und in der Dokumentation für den [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable**-Parameter enthalten.</span><span class="sxs-lookup"><span data-stu-id="d540a-126">The accepted **key/value** pairs are shown in the following table and are included in the documentation for the [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parameter.</span></span>

<span data-ttu-id="d540a-127">In der folgenden Tabelle sind die Schlüsselnamen und Datentypen aufgelistet und ob für einen Datenwert Platzhalterzeichen akzeptiert werden.</span><span class="sxs-lookup"><span data-stu-id="d540a-127">The following table displays the key names, data types, and whether wildcard characters are accepted for a data value.</span></span>

| <span data-ttu-id="d540a-128">Schlüsselname</span><span class="sxs-lookup"><span data-stu-id="d540a-128">Key name</span></span>     | <span data-ttu-id="d540a-129">Wertdatentyp</span><span class="sxs-lookup"><span data-stu-id="d540a-129">Value data type</span></span>    | <span data-ttu-id="d540a-130">Platzhalterzeichen akzeptiert?</span><span class="sxs-lookup"><span data-stu-id="d540a-130">Accepts wildcard characters?</span></span> |
|------------- | ------------------ | ---------------------------- |
| <span data-ttu-id="d540a-131">LogName</span><span class="sxs-lookup"><span data-stu-id="d540a-131">LogName</span></span>      | `<String[]>`       | <span data-ttu-id="d540a-132">Ja</span><span class="sxs-lookup"><span data-stu-id="d540a-132">Yes</span></span> |
| <span data-ttu-id="d540a-133">ProviderName</span><span class="sxs-lookup"><span data-stu-id="d540a-133">ProviderName</span></span> | `<String[]>`       | <span data-ttu-id="d540a-134">Ja</span><span class="sxs-lookup"><span data-stu-id="d540a-134">Yes</span></span> |
| <span data-ttu-id="d540a-135">Pfad</span><span class="sxs-lookup"><span data-stu-id="d540a-135">Path</span></span>         | `<String[]>`       | <span data-ttu-id="d540a-136">Nein</span><span class="sxs-lookup"><span data-stu-id="d540a-136">No</span></span>  |
| <span data-ttu-id="d540a-137">Keywords</span><span class="sxs-lookup"><span data-stu-id="d540a-137">Keywords</span></span>     | `<Long[]>`         | <span data-ttu-id="d540a-138">Nein</span><span class="sxs-lookup"><span data-stu-id="d540a-138">No</span></span>  |
| <span data-ttu-id="d540a-139">ID</span><span class="sxs-lookup"><span data-stu-id="d540a-139">ID</span></span>           | `<Int32[]>`        | <span data-ttu-id="d540a-140">Nein</span><span class="sxs-lookup"><span data-stu-id="d540a-140">No</span></span>  |
| <span data-ttu-id="d540a-141">Ebene</span><span class="sxs-lookup"><span data-stu-id="d540a-141">Level</span></span>        | `<Int32[]>`        | <span data-ttu-id="d540a-142">Nein</span><span class="sxs-lookup"><span data-stu-id="d540a-142">No</span></span>  |
| <span data-ttu-id="d540a-143">StartTime</span><span class="sxs-lookup"><span data-stu-id="d540a-143">StartTime</span></span>    | `<DateTime>`       | <span data-ttu-id="d540a-144">Nein</span><span class="sxs-lookup"><span data-stu-id="d540a-144">No</span></span>  |
| <span data-ttu-id="d540a-145">EndTime</span><span class="sxs-lookup"><span data-stu-id="d540a-145">EndTime</span></span>      | `<DateTime>`       | <span data-ttu-id="d540a-146">Nein</span><span class="sxs-lookup"><span data-stu-id="d540a-146">No</span></span>  |
| <span data-ttu-id="d540a-147">UserID</span><span class="sxs-lookup"><span data-stu-id="d540a-147">UserID</span></span>       | `<SID>`            | <span data-ttu-id="d540a-148">Nein</span><span class="sxs-lookup"><span data-stu-id="d540a-148">No</span></span>  |
| <span data-ttu-id="d540a-149">Daten</span><span class="sxs-lookup"><span data-stu-id="d540a-149">Data</span></span>         | `<String[]>`       | <span data-ttu-id="d540a-150">Nein</span><span class="sxs-lookup"><span data-stu-id="d540a-150">No</span></span>  |
| *            | `<String[]>`       | <span data-ttu-id="d540a-151">Nein</span><span class="sxs-lookup"><span data-stu-id="d540a-151">No</span></span>  |

## <a name="building-a-query-with-a-hash-table"></a><span data-ttu-id="d540a-152">Erstellen einer Abfrage mit einer Hashtabelle</span><span class="sxs-lookup"><span data-stu-id="d540a-152">Building a query with a hash table</span></span>

<span data-ttu-id="d540a-153">Um die Ergebnisse zu überprüfen und Probleme zu behandeln, ist es sinnvoll, die Hashtabelle aus jeweils einzelnen **Schlüssel/Wert**-Paaren aufzubauen.</span><span class="sxs-lookup"><span data-stu-id="d540a-153">To verify results and troubleshoot problems, it helps to build the hash table one **key/value** pair at a time.</span></span> <span data-ttu-id="d540a-154">Die Abfrage ruft Daten aus dem **Anwendungsprotokoll** ab.</span><span class="sxs-lookup"><span data-stu-id="d540a-154">The query gets data from the **Application** log.</span></span> <span data-ttu-id="d540a-155">Die Hashtabelle ist gleichbedeutend mit `Get-WinEvent –LogName Application`.</span><span class="sxs-lookup"><span data-stu-id="d540a-155">The hash table is equivalent to `Get-WinEvent –LogName Application`.</span></span>

<span data-ttu-id="d540a-156">Erstellen Sie zunächst die `Get-WinEvent`-Abfrage.</span><span class="sxs-lookup"><span data-stu-id="d540a-156">To begin, create the `Get-WinEvent` query.</span></span> <span data-ttu-id="d540a-157">Verwenden Sie das **Schlüssel/Wert**-Paar des **FilterHashtable**-Parameters mit dem Schlüssel **LogName** und dem Wert **Application**.</span><span class="sxs-lookup"><span data-stu-id="d540a-157">Use the **FilterHashtable** parameter's **key/value** pair with the key, **LogName**, and the value, **Application**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

<span data-ttu-id="d540a-158">Setzen Sie den Aufbau der Hashtabelle mit dem Schlüssel **ProviderName** fort.</span><span class="sxs-lookup"><span data-stu-id="d540a-158">Continue to build the hash table with the **ProviderName** key.</span></span> <span data-ttu-id="d540a-159">Der **ProviderName** ist der Name, der im Feld **Source** in der **Windows-Ereignisanzeige** angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d540a-159">The **ProviderName** is the name that appears in the **Source** field in the **Windows Event Viewer**.</span></span> <span data-ttu-id="d540a-160">Beispielsweise **.NET Runtime** im folgenden Screenshot:</span><span class="sxs-lookup"><span data-stu-id="d540a-160">For example, **.NET Runtime** in the following screenshot:</span></span>

![Abbildung der Quellen der Windows-Ereignisanzeige.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

<span data-ttu-id="d540a-162">Aktualisieren Sie die Hashtabelle, und schließen Sie das **Schlüssel/Wert**-Paar mit dem Schlüssel **ProviderName** und dem Wert **.NET Runtime** ein.</span><span class="sxs-lookup"><span data-stu-id="d540a-162">Update the hash table and include the **key/value** pair with the key, \*\*ProviderName, and the value, **.NET Runtime**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

<span data-ttu-id="d540a-163">Wenn Ihre Abfrage Daten aus archivierten Ereignisprotokollen abrufen muss, verwenden Sie den Schlüssel **Path**.</span><span class="sxs-lookup"><span data-stu-id="d540a-163">If your query needs to get data from archived event logs, use the **Path** key.</span></span> <span data-ttu-id="d540a-164">Der Wert von **Path** gibt den vollständigen Pfad zur Protokolldatei an.</span><span class="sxs-lookup"><span data-stu-id="d540a-164">The **Path** value specifies the full path to the log file.</span></span> <span data-ttu-id="d540a-165">Weitere Informationen finden Sie im **Scripting Guy**-Blogbeitrag [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors) (Verwenden von PowerShell zum Analysieren von gespeicherten Ereignisprotokollen auf Fehler).</span><span class="sxs-lookup"><span data-stu-id="d540a-165">For more information, see the **Scripting Guy** blog post, [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span></span>

## <a name="using-enumerated-values-in-a-hash-table"></a><span data-ttu-id="d540a-166">Verwenden von Enumerationswerten in einer Hashtabelle</span><span class="sxs-lookup"><span data-stu-id="d540a-166">Using enumerated values in a hash table</span></span>

<span data-ttu-id="d540a-167">**Keywords** ist der nächste Schlüssel in der Hashtabelle.</span><span class="sxs-lookup"><span data-stu-id="d540a-167">**Keywords** is the next key in the hash table.</span></span> <span data-ttu-id="d540a-168">Der Datentyp **Keywords** ist ein Array vom Werttyp `[long]`, der eine große Zahl enthält.</span><span class="sxs-lookup"><span data-stu-id="d540a-168">The **Keywords** data type is an array of the `[long]` value type that holds a large number.</span></span> <span data-ttu-id="d540a-169">Verwenden Sie den folgenden Befehl, um den Maximalwert von `[long]` zu ermitteln:</span><span class="sxs-lookup"><span data-stu-id="d540a-169">Use the following command to find the maximum value of `[long]`:</span></span>

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

<span data-ttu-id="d540a-170">Für den Schlüssel **Keywords** verwendet PowerShell eine Zahl, nicht eine Zeichenfolge, wie etwa **Security**.</span><span class="sxs-lookup"><span data-stu-id="d540a-170">For the **Keywords** key, PowerShell uses a number, not a string such as **Security**.</span></span> <span data-ttu-id="d540a-171">In der **Windows-Ereignisanzeige** werden die **Schlüsselwörter** als Zeichenfolgen dargestellt, sie sind jedoch Enumerationswerte.</span><span class="sxs-lookup"><span data-stu-id="d540a-171">**Windows Event Viewer** displays the **Keywords** as strings, but they are enumerated values.</span></span> <span data-ttu-id="d540a-172">Wenn Sie in der Hashtabelle den Schlüssel **Keywords** zusammen mit einem Zeichenfolgenwert verwenden, wird eine Fehlermeldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d540a-172">In the hash table, if you use the **Keywords** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="d540a-173">Öffnen Sie die **Windows-Ereignisanzeige**, und klicken Sie im Bereich **Aktionen** auf **Aktuelles Protokoll filtern**.</span><span class="sxs-lookup"><span data-stu-id="d540a-173">Open the **Windows Event Viewer** and from the **Actions** pane, click on **Filter current log**.</span></span>
<span data-ttu-id="d540a-174">Im Dropdownmenü **Schlüsselwörter** werden die verfügbaren Schlüsselwörter angezeigt, wie im folgenden Screenshot zu sehen:</span><span class="sxs-lookup"><span data-stu-id="d540a-174">The **Keywords** drop-down menu displays the available keywords, as shown in the following screenshot:</span></span>

![Abbildung der Schlüsselwörter der Windows-Ereignisanzeige.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

<span data-ttu-id="d540a-176">Verwenden Sie den folgenden Befehl, um die `StandardEventKeywords`-Eigenschaftsnamen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d540a-176">Use the following command to display the `StandardEventKeywords` property names.</span></span>

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

<span data-ttu-id="d540a-177">Die aufgezählten Werte sind im **.NET Framework** dokumentiert.</span><span class="sxs-lookup"><span data-stu-id="d540a-177">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="d540a-178">Weitere Informationen finden Sie unter [StandardEventKeywords Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="d540a-178">For more information, see [StandardEventKeywords Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="d540a-179">Die Namen und Enumerationswerte der **Schlüsselwörter** sind wie folgt:</span><span class="sxs-lookup"><span data-stu-id="d540a-179">The **Keywords** names and enumerated values are as follows:</span></span>

| <span data-ttu-id="d540a-180">Name</span><span class="sxs-lookup"><span data-stu-id="d540a-180">Name</span></span>             |  <span data-ttu-id="d540a-181">Wert</span><span class="sxs-lookup"><span data-stu-id="d540a-181">Value</span></span>            |
| ---------------- | ------------------|
| <span data-ttu-id="d540a-182">AuditFailure</span><span class="sxs-lookup"><span data-stu-id="d540a-182">AuditFailure</span></span>     | <span data-ttu-id="d540a-183">4503599627370496</span><span class="sxs-lookup"><span data-stu-id="d540a-183">4503599627370496</span></span>  |
| <span data-ttu-id="d540a-184">AuditSuccess</span><span class="sxs-lookup"><span data-stu-id="d540a-184">AuditSuccess</span></span>     | <span data-ttu-id="d540a-185">9007199254740992</span><span class="sxs-lookup"><span data-stu-id="d540a-185">9007199254740992</span></span>  |
| <span data-ttu-id="d540a-186">CorrelationHint2</span><span class="sxs-lookup"><span data-stu-id="d540a-186">CorrelationHint2</span></span> | <span data-ttu-id="d540a-187">18014398509481984</span><span class="sxs-lookup"><span data-stu-id="d540a-187">18014398509481984</span></span> |
| <span data-ttu-id="d540a-188">EventLogClassic</span><span class="sxs-lookup"><span data-stu-id="d540a-188">EventLogClassic</span></span>  | <span data-ttu-id="d540a-189">36028797018963968</span><span class="sxs-lookup"><span data-stu-id="d540a-189">36028797018963968</span></span> |
| <span data-ttu-id="d540a-190">Sqm</span><span class="sxs-lookup"><span data-stu-id="d540a-190">Sqm</span></span>              | <span data-ttu-id="d540a-191">2251799813685248</span><span class="sxs-lookup"><span data-stu-id="d540a-191">2251799813685248</span></span>  |
| <span data-ttu-id="d540a-192">WdiDiagnostic</span><span class="sxs-lookup"><span data-stu-id="d540a-192">WdiDiagnostic</span></span>    | <span data-ttu-id="d540a-193">1125899906842624</span><span class="sxs-lookup"><span data-stu-id="d540a-193">1125899906842624</span></span>  |
| <span data-ttu-id="d540a-194">WdiContext</span><span class="sxs-lookup"><span data-stu-id="d540a-194">WdiContext</span></span>       | <span data-ttu-id="d540a-195">562949953421312</span><span class="sxs-lookup"><span data-stu-id="d540a-195">562949953421312</span></span>   |
| <span data-ttu-id="d540a-196">ResponseTime</span><span class="sxs-lookup"><span data-stu-id="d540a-196">ResponseTime</span></span>     | <span data-ttu-id="d540a-197">281474976710656</span><span class="sxs-lookup"><span data-stu-id="d540a-197">281474976710656</span></span>   |
| <span data-ttu-id="d540a-198">Keine</span><span class="sxs-lookup"><span data-stu-id="d540a-198">None</span></span>             | <span data-ttu-id="d540a-199">0</span><span class="sxs-lookup"><span data-stu-id="d540a-199">0</span></span>                 |

<span data-ttu-id="d540a-200">Aktualisieren Sie die Hashtabelle, und schließen Sie das **Schlüssel/Wert**-Paar mit dem Schlüssel **Keywords**und dem **EventLogClassic**-Aufzählungswert **36028797018963968** ein.</span><span class="sxs-lookup"><span data-stu-id="d540a-200">Update the hash table and include the **key/value** pair with the key, **Keywords**, and the **EventLogClassic** enumeration value, **36028797018963968**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a><span data-ttu-id="d540a-201">Statischer Eigenschaftswert der Keywords-Eigenschaft (optional)</span><span class="sxs-lookup"><span data-stu-id="d540a-201">Keywords static property value (optional)</span></span>

<span data-ttu-id="d540a-202">Der Schlüssel **Keywords** ist aufgezählt, Sie können in der Hashtabellenabfrage aber einen statischen Eigenschaftsnamen verwenden.</span><span class="sxs-lookup"><span data-stu-id="d540a-202">The **Keywords** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="d540a-203">Anstatt die zurückgegebene Zeichenfolge zu verwenden, muss der Eigenschaftsname mit der Eigenschaft **Value__** in einen Wert konvertiert werden.</span><span class="sxs-lookup"><span data-stu-id="d540a-203">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="d540a-204">Beispielsweise verwendet das folgende Skript die Eigenschaft **Value__**.</span><span class="sxs-lookup"><span data-stu-id="d540a-204">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a><span data-ttu-id="d540a-205">Filtern nach Ereignis-ID</span><span class="sxs-lookup"><span data-stu-id="d540a-205">Filtering by Event Id</span></span>

<span data-ttu-id="d540a-206">Um spezifischere Daten zu erhalten, werden die Ergebnisse der Abfrage nach der **Ereignis-ID** gefiltert. Auf die **Ereignis-ID** wird in der Hashtabelle in Form des Schlüssels **ID** Bezug genommen, und der Wert ist eine spezifische **Ereignis-ID**. In der **Windows-Ereignisanzeige** wird die **Ereignis-ID** angezeigt. In diesem Beispiel wird die **Ereignis-ID 1023** verwendet.</span><span class="sxs-lookup"><span data-stu-id="d540a-206">To get more specific data, the query's results are filtered by **Event Id**. The **Event Id** is referenced in the hash table as the key **ID** and the value is a specific **Event Id**. The **Windows Event Viewer** displays the **Event Id**. This example uses **Event Id 1023**.</span></span>

<span data-ttu-id="d540a-207">Aktualisieren Sie die Hashtabelle, und schließen Sie das **Schlüssel/Wert**-Paar mit dem Schlüssel **ID** und dem Wert **1023** ein.</span><span class="sxs-lookup"><span data-stu-id="d540a-207">Update the hash table and include the **key/value** pair with the key, **ID** and the value, **1023**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a><span data-ttu-id="d540a-208">Filtern nach Ebene</span><span class="sxs-lookup"><span data-stu-id="d540a-208">Filtering by Level</span></span>

<span data-ttu-id="d540a-209">Um die Ergebnisse weiter einzugrenzen und nur Ereignisse aufzunehmen, die Fehler darstellen, verwenden Sie den Schlüssel **Level**.</span><span class="sxs-lookup"><span data-stu-id="d540a-209">To further refine the results and include only events that are errors, use the **Level** key.</span></span>
<span data-ttu-id="d540a-210">In der **Windows-Ereignisanzeige** wird der **Level** als Zeichenfolgenwert dargestellt, es handelt sich jedoch um Enumerationswerte.</span><span class="sxs-lookup"><span data-stu-id="d540a-210">**Windows Event Viewer** displays the **Level** as string values, but they are enumerated values.</span></span> <span data-ttu-id="d540a-211">Wenn Sie in der Hashtabelle den Schlüssel **Level** zusammen mit einem Zeichenfolgenwert verwenden, wird eine Fehlermeldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d540a-211">In the hash table, if you use the **Level** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="d540a-212">**Level** weist Werte wie **Error**, **Warning** oder **Informational** auf.</span><span class="sxs-lookup"><span data-stu-id="d540a-212">**Level** has values such as **Error**, **Warning**, or **Informational**.</span></span> <span data-ttu-id="d540a-213">Verwenden Sie den folgenden Befehl, um die Eigenschaftsnamen für `StandardEventLevel` anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d540a-213">Use the following command to display the `StandardEventLevel` property names.</span></span>

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

<span data-ttu-id="d540a-214">Die aufgezählten Werte sind im **.NET Framework** dokumentiert.</span><span class="sxs-lookup"><span data-stu-id="d540a-214">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="d540a-215">Weitere Informationen finden Sie unter [StandardEventLevel Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="d540a-215">For more information, see [StandardEventLevel Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="d540a-216">Die Namen und Enumerationswerte von **Level** sind wie folgt:</span><span class="sxs-lookup"><span data-stu-id="d540a-216">The **Level** key's names and enumerated values are as follows:</span></span>

| <span data-ttu-id="d540a-217">Name</span><span class="sxs-lookup"><span data-stu-id="d540a-217">Name</span></span>           | <span data-ttu-id="d540a-218">Wert</span><span class="sxs-lookup"><span data-stu-id="d540a-218">Value</span></span> |
| -------------- | ----- |
| <span data-ttu-id="d540a-219">Ausführlich</span><span class="sxs-lookup"><span data-stu-id="d540a-219">Verbose</span></span>        |   <span data-ttu-id="d540a-220">5</span><span class="sxs-lookup"><span data-stu-id="d540a-220">5</span></span>   |
| <span data-ttu-id="d540a-221">Informational</span><span class="sxs-lookup"><span data-stu-id="d540a-221">Informational</span></span>  |   <span data-ttu-id="d540a-222">4</span><span class="sxs-lookup"><span data-stu-id="d540a-222">4</span></span>   |
| <span data-ttu-id="d540a-223">Warning</span><span class="sxs-lookup"><span data-stu-id="d540a-223">Warning</span></span>        |   <span data-ttu-id="d540a-224">3</span><span class="sxs-lookup"><span data-stu-id="d540a-224">3</span></span>   |
| <span data-ttu-id="d540a-225">Fehler</span><span class="sxs-lookup"><span data-stu-id="d540a-225">Error</span></span>          |   <span data-ttu-id="d540a-226">2</span><span class="sxs-lookup"><span data-stu-id="d540a-226">2</span></span>   |
| <span data-ttu-id="d540a-227">Kritisch</span><span class="sxs-lookup"><span data-stu-id="d540a-227">Critical</span></span>       |   <span data-ttu-id="d540a-228">1</span><span class="sxs-lookup"><span data-stu-id="d540a-228">1</span></span>   |
| <span data-ttu-id="d540a-229">LogAlways</span><span class="sxs-lookup"><span data-stu-id="d540a-229">LogAlways</span></span>      |   <span data-ttu-id="d540a-230">0</span><span class="sxs-lookup"><span data-stu-id="d540a-230">0</span></span>   |

<span data-ttu-id="d540a-231">Die Hash-Tabelle für die vollständige Abfrage enthält den Schlüssel **Level** und den Wert **2**.</span><span class="sxs-lookup"><span data-stu-id="d540a-231">The hash table for the completed query includes the key, **Level**, and the value, **2**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a><span data-ttu-id="d540a-232">Statische Level-Eigenschaft in der Enumeration (optional)</span><span class="sxs-lookup"><span data-stu-id="d540a-232">Level static property in enumeration (optional)</span></span>

<span data-ttu-id="d540a-233">Der Schlüssel **Level** ist aufgezählt, Sie können in der Hashtabellenabfrage aber einen statischen Eigenschaftsnamen verwenden.</span><span class="sxs-lookup"><span data-stu-id="d540a-233">The **Level** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="d540a-234">Anstatt die zurückgegebene Zeichenfolge zu verwenden, muss der Eigenschaftsname mit der Eigenschaft **Value__** in einen Wert konvertiert werden.</span><span class="sxs-lookup"><span data-stu-id="d540a-234">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="d540a-235">Beispielsweise verwendet das folgende Skript die Eigenschaft **Value__**.</span><span class="sxs-lookup"><span data-stu-id="d540a-235">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```