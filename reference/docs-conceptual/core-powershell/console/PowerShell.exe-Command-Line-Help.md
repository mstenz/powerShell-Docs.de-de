---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Befehlszeilenhilfe für „PowerShell.exe“
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: 03c7672ee72698fe88a73e99702ceaadf87e702f
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51691829"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="27404-103">Befehlszeilenhilfe für „PowerShell.exe“</span><span class="sxs-lookup"><span data-stu-id="27404-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="27404-104">Sie können mithilfe von „PowerShell.exe“ eine PowerShell-Sitzung über die Befehlszeile eines anderen Tools wie z. B. „Cmd.exe“ starten oder mit diesem Befehl über die PowerShell-Befehlszeile eine neue Sitzung starten.</span><span class="sxs-lookup"><span data-stu-id="27404-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="27404-105">Verwenden Sie die Parameter, um die Sitzung anzupassen.</span><span class="sxs-lookup"><span data-stu-id="27404-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="27404-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="27404-106">Syntax</span></span>

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}]
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive]
       [-NoProfile]
       [-OutputFormat {Text | XML}]
       [-PSConsoleFile <FilePath> | -Version <PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="27404-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="27404-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="27404-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="27404-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="27404-109">Akzeptiert eine „base-64“-codierte Zeichenfolgenversion eines Befehls.</span><span class="sxs-lookup"><span data-stu-id="27404-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="27404-110">Verwenden Sie diesen Parameter, um Befehle an PowerShell zu übermitteln, die komplexe Anführungszeichen oder geschweifte Klammern erfordern.</span><span class="sxs-lookup"><span data-stu-id="27404-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="27404-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="27404-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="27404-112">Legt die Standardausführungsrichtlinie für die aktuelle Sitzung fest und speichert sie in der Umgebungsvariablen „$env:PSExecutionPolicyPreference“.</span><span class="sxs-lookup"><span data-stu-id="27404-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="27404-113">Dieser Parameter ändert die PowerShell-Ausführungsrichtlinie nicht, die in der Registrierung festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="27404-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="27404-114">Weitere Informationen zu PowerShell-Ausführungsrichtlinien (einschließlich einer Liste gültiger Werte) finden Sie unter [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="27404-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="27404-115">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="27404-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="27404-116">Führt das angegebene Skript im lokalen Bereich aus, sodass die Funktionen und Variablen, die das Skript erstellt, in der aktuellen Sitzung verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="27404-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="27404-117">Geben Sie den Pfad der Skriptdatei und Parameter an.</span><span class="sxs-lookup"><span data-stu-id="27404-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="27404-118">**File** muss der letzte Parameter im Befehl sein.</span><span class="sxs-lookup"><span data-stu-id="27404-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="27404-119">Alle Werte, die nach dem **-File**-Parameter eingegeben werden, werden als Skriptdateipfad und als an das Skript übergebene Parameter interpretiert.</span><span class="sxs-lookup"><span data-stu-id="27404-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="27404-120">Parameter, die an das Skript übergeben werden, werden als Zeichenfolgenliterale übergeben (nach der Interpretation durch die aktuelle Shell).</span><span class="sxs-lookup"><span data-stu-id="27404-120">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="27404-121">Wenn Sie in cmd.exe und Wert einer Umgebungsvariable übergeben möchten, würden Sie z. B. der cmd.exe-Syntax verwenden: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="27404-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="27404-122">Im Gegensatz dazu ausführen `powershell.exe -File .\test.ps1 -TestParam $env:windir` in cmd.exe führt das Skript mit dem Empfang der literalen Zeichenfolge `$env:windir` , da es keine spezielle Bedeutung für die aktuelle cmd.exe-Shell hat.</span><span class="sxs-lookup"><span data-stu-id="27404-122">In contrast, running `powershell.exe -File .\test.ps1 -TestParam $env:windir` in cmd.exe results in the script receiving the literal string `$env:windir` because it has no special meaning to the current cmd.exe shell.</span></span>
<span data-ttu-id="27404-123">Die `$env:windir` Stil der Referenz zu Umgebungsvariablen _können_ in verwendet werden. eine `-Command` Parameter, da es ihn als PowerShell-Code interpretiert wird.</span><span class="sxs-lookup"><span data-stu-id="27404-123">The `$env:windir` style of environment variable reference _can_ be used inside a `-Command` parameter, since there it will be interpreted as PowerShell code.</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="27404-124">\--InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="27404-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="27404-125">Beschreibt das Format der Daten, die an PowerShell übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="27404-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="27404-126">Gültige Werte sind "Text" (Textzeichenfolgen) oder "XML" (serialisiertes CLIXML-Format).</span><span class="sxs-lookup"><span data-stu-id="27404-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="27404-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="27404-127">-Mta</span></span>

<span data-ttu-id="27404-128">Startet PowerShell mit einem Multithread-Apartment.</span><span class="sxs-lookup"><span data-stu-id="27404-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="27404-129">Dieser Parameter wird in Windows PowerShell 3.0 eingeführt.</span><span class="sxs-lookup"><span data-stu-id="27404-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="27404-130">In PowerShell 3.0 ist Singlethread-Apartment (STA) die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="27404-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="27404-131">In PowerShell 2.0 stellt Multithread-Apartment (MTA) die Standardeinstellung dar.</span><span class="sxs-lookup"><span data-stu-id="27404-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="27404-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="27404-132">-NoExit</span></span>

<span data-ttu-id="27404-133">Nach dem Ausführen der Startbefehle erfolgt kein Beenden.</span><span class="sxs-lookup"><span data-stu-id="27404-133">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="27404-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="27404-134">-NoLogo</span></span>

<span data-ttu-id="27404-135">Blendet die Copyrightinformationen beim Start aus.</span><span class="sxs-lookup"><span data-stu-id="27404-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="27404-136">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="27404-136">-NonInteractive</span></span>

<span data-ttu-id="27404-137">Zeigt dem Benutzer keine interaktive Eingabeaufforderung.</span><span class="sxs-lookup"><span data-stu-id="27404-137">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="27404-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="27404-138">-NoProfile</span></span>

<span data-ttu-id="27404-139">Das PowerShell-Profil wird nicht geladen.</span><span class="sxs-lookup"><span data-stu-id="27404-139">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="27404-140">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="27404-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="27404-141">Bestimmt, wie die Ausgabe von PowerShell formatiert ist.</span><span class="sxs-lookup"><span data-stu-id="27404-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="27404-142">Gültige Werte sind "Text" (Textzeichenfolgen) oder "XML" (serialisiertes CLIXML-Format).</span><span class="sxs-lookup"><span data-stu-id="27404-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="27404-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="27404-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="27404-144">Lädt die angegebene PowerShell-Konsolendatei.</span><span class="sxs-lookup"><span data-stu-id="27404-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="27404-145">Geben Sie den Pfad und Namen der Konsolendatei ein.</span><span class="sxs-lookup"><span data-stu-id="27404-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="27404-146">Verwenden Sie zum Erstellen einer Konsolendatei das Cmdlet [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="27404-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="27404-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="27404-147">-Sta</span></span>

<span data-ttu-id="27404-148">Startet PowerShell mit einem Singlethread-Apartment.</span><span class="sxs-lookup"><span data-stu-id="27404-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="27404-149">In PowerShell 3.0 ist Singlethread-Apartment (STA) die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="27404-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="27404-150">In PowerShell 2.0 stellt Multithread-Apartment (MTA) die Standardeinstellung dar.</span><span class="sxs-lookup"><span data-stu-id="27404-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="27404-151">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="27404-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="27404-152">Startet die angegebene Version von PowerShell.</span><span class="sxs-lookup"><span data-stu-id="27404-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="27404-153">Die Version, die Sie angeben, muss auf dem System installiert sein.</span><span class="sxs-lookup"><span data-stu-id="27404-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="27404-154">Falls PowerShell 3.0 auf dem Computer installiert ist, sind „2.0“ und „3.0“ gültige Werte.</span><span class="sxs-lookup"><span data-stu-id="27404-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="27404-155">Der Standardwert ist „3.0“.</span><span class="sxs-lookup"><span data-stu-id="27404-155">The default value is "3.0".</span></span>

<span data-ttu-id="27404-156">Falls PowerShell 3.0 nicht installiert ist, ist „2.0“ der einzige gültige Wert.</span><span class="sxs-lookup"><span data-stu-id="27404-156">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="27404-157">Andere Werte werden ignoriert.</span><span class="sxs-lookup"><span data-stu-id="27404-157">Other values are ignored.</span></span>

<span data-ttu-id="27404-158">Weitere Informationen finden Sie unter [Installieren von Windows PowerShell](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="27404-158">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="27404-159">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="27404-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="27404-160">Legt den Fensterstil für die Sitzung fest.</span><span class="sxs-lookup"><span data-stu-id="27404-160">Sets the window style for the session.</span></span> <span data-ttu-id="27404-161">Gültige Werte sind „Normal“, „Minimized“, „Maximized“ und „Hidden“.</span><span class="sxs-lookup"><span data-stu-id="27404-161">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="27404-162">-Command</span><span class="sxs-lookup"><span data-stu-id="27404-162">-Command</span></span>

<span data-ttu-id="27404-163">Führt die angegebenen Befehle (mit den Parametern) so aus, als wären sie über die PowerShell-Befehlszeile eingegeben worden.</span><span class="sxs-lookup"><span data-stu-id="27404-163">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span>
<span data-ttu-id="27404-164">PowerShell nach der Ausführung wird beendet, es sei denn, die **NoExit** Parameter angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="27404-164">After execution, PowerShell exits unless the **NoExit** parameter is specified.</span></span>
<span data-ttu-id="27404-165">Sämtlicher Text nach `-Command` wird als eine einzige Befehlszeile an PowerShell gesendet.</span><span class="sxs-lookup"><span data-stu-id="27404-165">Any text after `-Command` is sent as a single command line to PowerShell.</span></span>
<span data-ttu-id="27404-166">Dies ist ein Unterschied zum Verhalten von `-File` bei der Verarbeitung von an ein Skript gesendete Parameter.</span><span class="sxs-lookup"><span data-stu-id="27404-166">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="27404-167">Der Wert des `-Command` kann "-", eine Zeichenfolge oder ein Skriptblock.</span><span class="sxs-lookup"><span data-stu-id="27404-167">The value of `-Command` can be "-", a string, or a script block.</span></span>
<span data-ttu-id="27404-168">Die Ergebnisse des Befehls werden an die übergeordnete Shell als deserialisierte XML-Objekte, nicht als live-Objekte zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="27404-168">The results of the command are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="27404-169">Wenn der Wert des `-Command` ist "-", wird der Befehlstext aus der Standardeingabe gelesen.</span><span class="sxs-lookup"><span data-stu-id="27404-169">If the value of `-Command` is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="27404-170">Wenn der Wert des `-Command` ist eine Zeichenfolge, **Befehl** _müssen_ der letzte Parameter angegeben werden, da alle Zeichen eingegeben werden, nachdem der Befehl als die Befehlsargumente interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="27404-170">When the value of `-Command` is a string, **Command** _must_ be the last parameter specified because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="27404-171">Die **Befehl** Parameter akzeptiert nur einen Skriptblock für die Ausführung, wenn sie den übergebenen Wert erkennen kann `-Command` als Typ "scriptblock".</span><span class="sxs-lookup"><span data-stu-id="27404-171">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to `-Command` as a ScriptBlock type.</span></span>
<span data-ttu-id="27404-172">Dies ist _nur_ möglich, die bei der Ausführung des PowerShell.exe von einem anderen PowerShell-Host.</span><span class="sxs-lookup"><span data-stu-id="27404-172">This is _only_ possible when running PowerShell.exe from another PowerShell host.</span></span>
<span data-ttu-id="27404-173">Der Typ kann in eine vorhandene Variable aus einem Ausdruck zurückgegebenen oder analysiert, indem Sie das PowerShell enthalten sein, "scriptblock" zu hosten, als literal Skriptblock in geschweiften Klammern `{}`, bevor an PowerShell.exe übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="27404-173">The ScriptBlock type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces `{}`, before being passed to PowerShell.exe.</span></span>

<span data-ttu-id="27404-174">In cmd.exe, es gibt keine als Skriptblock (oder "scriptblock" Typ), also den übergebenen Wert **Befehl** wird _immer_ eine Zeichenfolge sein.</span><span class="sxs-lookup"><span data-stu-id="27404-174">In cmd.exe, there is no such thing as a script block (or ScriptBlock type), so the value passed to **Command** will _always_ be a string.</span></span>
<span data-ttu-id="27404-175">Sie können einen Skriptblock innerhalb der Zeichenfolge schreiben, aber ausgeführt wird es verhält sich genau als ob Sie sie in einer typischen PowerShell-Eingabeaufforderung eingegeben, Drucken des Inhalts des Skripts wieder für Sie blockiert.</span><span class="sxs-lookup"><span data-stu-id="27404-175">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="27404-176">Eine Zeichenfolge übergeben, um `-Command` weiterhin so ausgeführt, als PowerShell, sodass die geschweiften Klammern für Skript-Block häufig nicht erforderlich in erster Linie sind bei Ausführung von cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="27404-176">A string passed to `-Command` will still be executed as PowerShell, so the script block curly braces are often not required in the first place when running from cmd.exe.</span></span>
<span data-ttu-id="27404-177">Zum Ausführen eines Inline-Skriptblock, der definiert, die in eine Zeichenfolge, die [Aufrufoperator](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` kann verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="27404-177">To execute an inline script block defined inside a string, the [call operator](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` can be used:</span></span>

```console
"& {<command>}"
```

### <a name="-help---"></a><span data-ttu-id="27404-178">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="27404-178">-Help, -?, /?</span></span>

<span data-ttu-id="27404-179">Zeigt die Syntax von „powershell.exe“.</span><span class="sxs-lookup"><span data-stu-id="27404-179">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="27404-180">Wenn Sie einen „PowerShell.exe“-Befehl in PowerShell eingeben, setzen Sie vor die Befehlsparameter einen Bindestrich (-) und keinen Schrägstrich (/).</span><span class="sxs-lookup"><span data-stu-id="27404-180">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="27404-181">In „Cmd.exe“ können Sie entweder einen Binde- oder Schrägstrich verwenden.</span><span class="sxs-lookup"><span data-stu-id="27404-181">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="27404-182">Hinweis zur Fehlerbehebung: In PowerShell 2.0 misslingt das Starten einiger Programme in der Windows PowerShell-Konsole mit dem folgenden „LastExitCode“: 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="27404-182">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="27404-183">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="27404-183">EXAMPLES</span></span>

```powershell
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a PowerShell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate way to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```
