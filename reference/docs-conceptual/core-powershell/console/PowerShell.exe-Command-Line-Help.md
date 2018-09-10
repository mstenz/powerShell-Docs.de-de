---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Befehlszeilenhilfe für „PowerShell.exe“
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: c7f35511e876e8e5189d8a2b949555603d43f731
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133160"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="42e68-103">Befehlszeilenhilfe für „PowerShell.exe“</span><span class="sxs-lookup"><span data-stu-id="42e68-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="42e68-104">Sie können mithilfe von „PowerShell.exe“ eine PowerShell-Sitzung über die Befehlszeile eines anderen Tools wie z. B. „Cmd.exe“ starten oder mit diesem Befehl über die PowerShell-Befehlszeile eine neue Sitzung starten.</span><span class="sxs-lookup"><span data-stu-id="42e68-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="42e68-105">Verwenden Sie die Parameter, um die Sitzung anzupassen.</span><span class="sxs-lookup"><span data-stu-id="42e68-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="42e68-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="42e68-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="42e68-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="42e68-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="42e68-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="42e68-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="42e68-109">Akzeptiert eine „base-64“-codierte Zeichenfolgenversion eines Befehls.</span><span class="sxs-lookup"><span data-stu-id="42e68-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="42e68-110">Verwenden Sie diesen Parameter, um Befehle an PowerShell zu übermitteln, die komplexe Anführungszeichen oder geschweifte Klammern erfordern.</span><span class="sxs-lookup"><span data-stu-id="42e68-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="42e68-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="42e68-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="42e68-112">Legt die Standardausführungsrichtlinie für die aktuelle Sitzung fest und speichert sie in der Umgebungsvariablen „$env:PSExecutionPolicyPreference“.</span><span class="sxs-lookup"><span data-stu-id="42e68-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="42e68-113">Dieser Parameter ändert die PowerShell-Ausführungsrichtlinie nicht, die in der Registrierung festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="42e68-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="42e68-114">Weitere Informationen zu PowerShell-Ausführungsrichtlinien (einschließlich einer Liste gültiger Werte) finden Sie unter [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="42e68-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="42e68-115">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="42e68-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="42e68-116">Führt das angegebene Skript im lokalen Bereich aus, sodass die Funktionen und Variablen, die das Skript erstellt, in der aktuellen Sitzung verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="42e68-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="42e68-117">Geben Sie den Pfad der Skriptdatei und Parameter an.</span><span class="sxs-lookup"><span data-stu-id="42e68-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="42e68-118">**File** muss der letzte Parameter im Befehl sein.</span><span class="sxs-lookup"><span data-stu-id="42e68-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="42e68-119">Alle Werte, die nach dem **-File**-Parameter eingegeben werden, werden als Skriptdateipfad und als an das Skript übergebene Parameter interpretiert.</span><span class="sxs-lookup"><span data-stu-id="42e68-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="42e68-120">Parameter, die an das Skript übergeben werden, werden als Zeichenfolgenliterale übergeben (nach der Interpretation durch die aktuelle Shell).</span><span class="sxs-lookup"><span data-stu-id="42e68-120">Parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span> <span data-ttu-id="42e68-121">Wenn Sie beispielsweise in „cmd.exe“ sind und den Wert einer Umgebungsvariablen übergeben möchten, verwenden Sie die Syntax `powershell -File .\test.ps1 -Sample %windir%` von „cmd.exe“. In diesem Beispiel empfängt Ihr Skript das Zeichenfolgenliteral `$env:windir` und nicht den Wert der Umgebungsvariablen: `powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="42e68-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` In this example, the script receives the literal string `$env:windir` and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="42e68-122">\--InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="42e68-122">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="42e68-123">Beschreibt das Format der Daten, die an PowerShell übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="42e68-123">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="42e68-124">Gültige Werte sind "Text" (Textzeichenfolgen) oder "XML" (serialisiertes CLIXML-Format).</span><span class="sxs-lookup"><span data-stu-id="42e68-124">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="42e68-125">-Mta</span><span class="sxs-lookup"><span data-stu-id="42e68-125">-Mta</span></span>

<span data-ttu-id="42e68-126">Startet PowerShell mit einem Multithread-Apartment.</span><span class="sxs-lookup"><span data-stu-id="42e68-126">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="42e68-127">Dieser Parameter wird in Windows PowerShell 3.0 eingeführt.</span><span class="sxs-lookup"><span data-stu-id="42e68-127">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="42e68-128">In PowerShell 3.0 ist Singlethread-Apartment (STA) die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="42e68-128">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="42e68-129">In PowerShell 2.0 stellt Multithread-Apartment (MTA) die Standardeinstellung dar.</span><span class="sxs-lookup"><span data-stu-id="42e68-129">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="42e68-130">-NoExit</span><span class="sxs-lookup"><span data-stu-id="42e68-130">-NoExit</span></span>

<span data-ttu-id="42e68-131">Nach dem Ausführen der Startbefehle erfolgt kein Beenden.</span><span class="sxs-lookup"><span data-stu-id="42e68-131">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="42e68-132">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="42e68-132">-NoLogo</span></span>

<span data-ttu-id="42e68-133">Blendet die Copyrightinformationen beim Start aus.</span><span class="sxs-lookup"><span data-stu-id="42e68-133">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="42e68-134">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="42e68-134">-NonInteractive</span></span>

<span data-ttu-id="42e68-135">Zeigt dem Benutzer keine interaktive Eingabeaufforderung.</span><span class="sxs-lookup"><span data-stu-id="42e68-135">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="42e68-136">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="42e68-136">-NoProfile</span></span>

<span data-ttu-id="42e68-137">Das PowerShell-Profil wird nicht geladen.</span><span class="sxs-lookup"><span data-stu-id="42e68-137">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="42e68-138">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="42e68-138">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="42e68-139">Bestimmt, wie die Ausgabe von PowerShell formatiert ist.</span><span class="sxs-lookup"><span data-stu-id="42e68-139">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="42e68-140">Gültige Werte sind "Text" (Textzeichenfolgen) oder "XML" (serialisiertes CLIXML-Format).</span><span class="sxs-lookup"><span data-stu-id="42e68-140">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="42e68-141">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="42e68-141">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="42e68-142">Lädt die angegebene PowerShell-Konsolendatei.</span><span class="sxs-lookup"><span data-stu-id="42e68-142">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="42e68-143">Geben Sie den Pfad und Namen der Konsolendatei ein.</span><span class="sxs-lookup"><span data-stu-id="42e68-143">Enter the path and name of the console file.</span></span> <span data-ttu-id="42e68-144">Verwenden Sie zum Erstellen einer Konsolendatei das Cmdlet [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="42e68-144">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="42e68-145">-Sta</span><span class="sxs-lookup"><span data-stu-id="42e68-145">-Sta</span></span>

<span data-ttu-id="42e68-146">Startet PowerShell mit einem Singlethread-Apartment.</span><span class="sxs-lookup"><span data-stu-id="42e68-146">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="42e68-147">In PowerShell 3.0 ist Singlethread-Apartment (STA) die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="42e68-147">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="42e68-148">In PowerShell 2.0 stellt Multithread-Apartment (MTA) die Standardeinstellung dar.</span><span class="sxs-lookup"><span data-stu-id="42e68-148">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="42e68-149">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="42e68-149">-Version <PowerShell Version></span></span>

<span data-ttu-id="42e68-150">Startet die angegebene Version von PowerShell.</span><span class="sxs-lookup"><span data-stu-id="42e68-150">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="42e68-151">Die Version, die Sie angeben, muss auf dem System installiert sein.</span><span class="sxs-lookup"><span data-stu-id="42e68-151">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="42e68-152">Falls PowerShell 3.0 auf dem Computer installiert ist, sind „2.0“ und „3.0“ gültige Werte.</span><span class="sxs-lookup"><span data-stu-id="42e68-152">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="42e68-153">Der Standardwert ist „3.0“.</span><span class="sxs-lookup"><span data-stu-id="42e68-153">The default value is "3.0".</span></span>

<span data-ttu-id="42e68-154">Falls PowerShell 3.0 nicht installiert ist, ist „2.0“ der einzige gültige Wert.</span><span class="sxs-lookup"><span data-stu-id="42e68-154">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="42e68-155">Andere Werte werden ignoriert.</span><span class="sxs-lookup"><span data-stu-id="42e68-155">Other values are ignored.</span></span>

<span data-ttu-id="42e68-156">Weitere Informationen finden Sie unter [Installieren von Windows PowerShell](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="42e68-156">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="42e68-157">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="42e68-157">-WindowStyle <Window style></span></span>

<span data-ttu-id="42e68-158">Legt den Fensterstil für die Sitzung fest.</span><span class="sxs-lookup"><span data-stu-id="42e68-158">Sets the window style for the session.</span></span> <span data-ttu-id="42e68-159">Gültige Werte sind „Normal“, „Minimized“, „Maximized“ und „Hidden“.</span><span class="sxs-lookup"><span data-stu-id="42e68-159">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="42e68-160">-Command</span><span class="sxs-lookup"><span data-stu-id="42e68-160">-Command</span></span>

<span data-ttu-id="42e68-161">Führt die angegebenen Befehle (mit den Parametern) so aus, als wären sie über die PowerShell-Befehlszeile eingegeben worden.</span><span class="sxs-lookup"><span data-stu-id="42e68-161">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span> <span data-ttu-id="42e68-162">Nach der Ausführung wird PowerShell beendet, es sei denn, der `-NoExit`-Parameter wurde angegeben.</span><span class="sxs-lookup"><span data-stu-id="42e68-162">After execution, PowerShell exits unless the `-NoExit` parameter is specified.</span></span>
<span data-ttu-id="42e68-163">Sämtlicher Text nach `-Command` wird als eine einzige Befehlszeile an PowerShell gesendet.</span><span class="sxs-lookup"><span data-stu-id="42e68-163">Any text after `-Command` is sent as a single command line to PowerShell.</span></span> <span data-ttu-id="42e68-164">Dies ist ein Unterschied zum Verhalten von `-File` bei der Verarbeitung von an ein Skript gesendete Parameter.</span><span class="sxs-lookup"><span data-stu-id="42e68-164">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="42e68-165">Der Wert von „Command“ kann „-“, eine Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="42e68-165">The value of Command can be "-", a string.</span></span> <span data-ttu-id="42e68-166">oder ein Skriptblock sein.</span><span class="sxs-lookup"><span data-stu-id="42e68-166">or a script block.</span></span> <span data-ttu-id="42e68-167">Wenn der Wert des Befehls „-“ ist, wird der Befehlstext aus der Standardeingabe gelesen.</span><span class="sxs-lookup"><span data-stu-id="42e68-167">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="42e68-168">Skriptblöcke müssen in geschweifte Klammern ({}) gesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="42e68-168">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="42e68-169">Sie können einen Skriptblock nur angeben, wenn „PowerShell.exe“ in PowerShell ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="42e68-169">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="42e68-170">Die Ergebnisse des Skripts werden an die übergeordnete Shell als deserialisierte XML-Objekte und nicht als Live-Objekte zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="42e68-170">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="42e68-171">Wenn der Wert von „Command“ eine Zeichenfolge ist, muss **Command** der letzte Parameter im Befehl sein, da alle Zeichen, die nach dem Befehl eingegeben werden, als die Befehlsargumente interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="42e68-171">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="42e68-172">Um eine Zeichenfolge zu schreiben, die einen PowerShell-Befehl ausführt, verwenden Sie das Format:</span><span class="sxs-lookup"><span data-stu-id="42e68-172">To write a string that runs a PowerShell command, use the format:</span></span>

```powershell
"& {<command>}"
```

<span data-ttu-id="42e68-173">Die Anführungszeichen geben eine Zeichenfolge an, und der Aufrufoperator (&) bewirkt, dass der Befehl ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="42e68-173">The quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="42e68-174">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="42e68-174">-Help, -?, /?</span></span>

<span data-ttu-id="42e68-175">Zeigt die Syntax von „powershell.exe“.</span><span class="sxs-lookup"><span data-stu-id="42e68-175">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="42e68-176">Wenn Sie einen „PowerShell.exe“-Befehl in PowerShell eingeben, setzen Sie vor die Befehlsparameter einen Bindestrich (-) und keinen Schrägstrich (/).</span><span class="sxs-lookup"><span data-stu-id="42e68-176">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="42e68-177">In „Cmd.exe“ können Sie entweder einen Binde- oder Schrägstrich verwenden.</span><span class="sxs-lookup"><span data-stu-id="42e68-177">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="42e68-178">Hinweis zur Fehlerbehebung: In PowerShell 2.0 misslingt das Starten einiger Programme in der Windows PowerShell-Konsole mit dem folgenden „LastExitCode“: 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="42e68-178">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="42e68-179">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="42e68-179">EXAMPLES</span></span>

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
