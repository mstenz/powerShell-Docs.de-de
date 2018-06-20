---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Befehlszeilenhilfe für „PowerShell.exe“
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 60b6a7e310821a4092b0972b7abbdae0e2d5f738
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952578"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="2418a-103">Befehlszeilenhilfe für „PowerShell.exe“</span><span class="sxs-lookup"><span data-stu-id="2418a-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="2418a-104">Sie können mithilfe von „PowerShell.exe“ eine PowerShell-Sitzung über die Befehlszeile eines anderen Tools wie z. B. „Cmd.exe“ starten oder mit diesem Befehl über die PowerShell-Befehlszeile eine neue Sitzung starten.</span><span class="sxs-lookup"><span data-stu-id="2418a-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="2418a-105">Verwenden Sie die Parameter, um die Sitzung anzupassen.</span><span class="sxs-lookup"><span data-stu-id="2418a-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="2418a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2418a-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="2418a-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="2418a-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="2418a-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="2418a-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="2418a-109">Akzeptiert eine „base-64“-codierte Zeichenfolgenversion eines Befehls.</span><span class="sxs-lookup"><span data-stu-id="2418a-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="2418a-110">Verwenden Sie diesen Parameter, um Befehle an PowerShell zu übermitteln, die komplexe Anführungszeichen oder geschweifte Klammern erfordern.</span><span class="sxs-lookup"><span data-stu-id="2418a-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="2418a-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="2418a-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="2418a-112">Legt die Standardausführungsrichtlinie für die aktuelle Sitzung fest und speichert sie in der Umgebungsvariablen „$env:PSExecutionPolicyPreference“.</span><span class="sxs-lookup"><span data-stu-id="2418a-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="2418a-113">Dieser Parameter ändert nicht die PowerShell-Ausführungsrichtlinie, die in der Registrierung festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="2418a-113">This parameter does not change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="2418a-114">Weitere Informationen zu PowerShell-Ausführungsrichtlinien (einschließlich einer Liste gültiger Werte) finden Sie unter [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="2418a-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="2418a-115">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="2418a-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="2418a-116">Führt das angegebene Skript im lokalen Bereich aus, sodass die Funktionen und Variablen, die das Skript erstellt, in der aktuellen Sitzung verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="2418a-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="2418a-117">Geben Sie den Pfad der Skriptdatei und Parameter an.</span><span class="sxs-lookup"><span data-stu-id="2418a-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="2418a-118">**File** muss der letzte Parameter im Befehl sein, da alle Zeichen, die nach dem **File**-Parameter eingegeben werden, als Pfad der Skriptdatei gefolgt von den Skriptparametern und ihren Werten interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="2418a-118">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="2418a-119">Sie können in den Wert des **File**-Parameters die Parameter eines Skripts und Parameterwerte einschließen.</span><span class="sxs-lookup"><span data-stu-id="2418a-119">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="2418a-120">Beispiel: `-File .\Get-Script.ps1 -Domain Central` Beachten Sie, dass Parameter, die an das Skript übergeben werden, als Zeichenfolgenliterale übergeben werden (nach der Interpretation durch die aktuelle Shell).</span><span class="sxs-lookup"><span data-stu-id="2418a-120">For example: `-File .\Get-Script.ps1 -Domain Central` Note that parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span>
<span data-ttu-id="2418a-121">Wenn Sie beispielsweise in „cmd.exe“ sind und den Wert einer Umgebungsvariable übergeben möchten, verwenden Sie die Syntax `powershell -File .\test.ps1 -Sample %windir%` von „cmd.exe“. Wenn Sie die PowerShell-Syntax verwenden, würde Ihr Skript in diesem Beispiel das Zeichenfolgenliteral „$env:windir“ erhalten und nicht den Wert der Umgebungsvariable: `powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="2418a-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` If you were to use PowerShell syntax, then in this example your script would receive the literal "$env:windir" and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

<span data-ttu-id="2418a-122">Die Switch-Parameter eines Skripts werden in der Regel entweder einbezogen oder ausgelassen.</span><span class="sxs-lookup"><span data-stu-id="2418a-122">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="2418a-123">Der folgende Befehl verwendet beispielsweise den **All**-Parameter der Skriptdatei „Get-Script.ps1“: `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="2418a-123">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="2418a-124">\--InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="2418a-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="2418a-125">Beschreibt das Format der Daten, die an PowerShell übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="2418a-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="2418a-126">Gültige Werte sind "Text" (Textzeichenfolgen) oder "XML" (serialisiertes CLIXML-Format).</span><span class="sxs-lookup"><span data-stu-id="2418a-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="2418a-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="2418a-127">-Mta</span></span>

<span data-ttu-id="2418a-128">Startet PowerShell mit einem Multithread-Apartment.</span><span class="sxs-lookup"><span data-stu-id="2418a-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="2418a-129">Dieser Parameter wird in Windows PowerShell 3.0 eingeführt.</span><span class="sxs-lookup"><span data-stu-id="2418a-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="2418a-130">In PowerShell 3.0 ist Singlethread-Apartment (STA) die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="2418a-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="2418a-131">In PowerShell 2.0 stellt Multithread-Apartment (MTA) die Standardeinstellung dar.</span><span class="sxs-lookup"><span data-stu-id="2418a-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="2418a-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="2418a-132">-NoExit</span></span>

<span data-ttu-id="2418a-133">Nach dem Ausführen der Startbefehle erfolgt kein Beenden.</span><span class="sxs-lookup"><span data-stu-id="2418a-133">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="2418a-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="2418a-134">-NoLogo</span></span>

<span data-ttu-id="2418a-135">Blendet die Copyrightinformationen beim Start aus.</span><span class="sxs-lookup"><span data-stu-id="2418a-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="2418a-136">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="2418a-136">-NonInteractive</span></span>

<span data-ttu-id="2418a-137">Zeigt dem Benutzer keine interaktive Eingabeaufforderung.</span><span class="sxs-lookup"><span data-stu-id="2418a-137">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="2418a-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="2418a-138">-NoProfile</span></span>

<span data-ttu-id="2418a-139">Das PowerShell-Profil wird nicht geladen.</span><span class="sxs-lookup"><span data-stu-id="2418a-139">Does not load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="2418a-140">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="2418a-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="2418a-141">Bestimmt, wie die Ausgabe von PowerShell formatiert ist.</span><span class="sxs-lookup"><span data-stu-id="2418a-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="2418a-142">Gültige Werte sind "Text" (Textzeichenfolgen) oder "XML" (serialisiertes CLIXML-Format).</span><span class="sxs-lookup"><span data-stu-id="2418a-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="2418a-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="2418a-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="2418a-144">Lädt die angegebene PowerShell-Konsolendatei.</span><span class="sxs-lookup"><span data-stu-id="2418a-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="2418a-145">Geben Sie den Pfad und Namen der Konsolendatei ein.</span><span class="sxs-lookup"><span data-stu-id="2418a-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="2418a-146">Verwenden Sie zum Erstellen einer Konsolendatei das Cmdlet [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2418a-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="2418a-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="2418a-147">-Sta</span></span>

<span data-ttu-id="2418a-148">Startet PowerShell mit einem Singlethread-Apartment.</span><span class="sxs-lookup"><span data-stu-id="2418a-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="2418a-149">In PowerShell 3.0 ist Singlethread-Apartment (STA) die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="2418a-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="2418a-150">In PowerShell 2.0 stellt Multithread-Apartment (MTA) die Standardeinstellung dar.</span><span class="sxs-lookup"><span data-stu-id="2418a-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="2418a-151">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="2418a-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="2418a-152">Startet die angegebene Version von PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2418a-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="2418a-153">Die Version, die Sie angeben, muss auf dem System installiert sein.</span><span class="sxs-lookup"><span data-stu-id="2418a-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="2418a-154">Falls PowerShell 3.0 auf dem Computer installiert ist, sind „2.0“ und „3.0“ gültige Werte.</span><span class="sxs-lookup"><span data-stu-id="2418a-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="2418a-155">Der Standardwert ist „3.0“.</span><span class="sxs-lookup"><span data-stu-id="2418a-155">The default value is "3.0".</span></span>

<span data-ttu-id="2418a-156">Falls PowerShell 3.0 nicht installiert ist, ist „2.0“ der einzige gültige Wert.</span><span class="sxs-lookup"><span data-stu-id="2418a-156">If PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="2418a-157">Andere Werte werden ignoriert.</span><span class="sxs-lookup"><span data-stu-id="2418a-157">Other values are ignored.</span></span>

<span data-ttu-id="2418a-158">Weitere Informationen finden Sie unter [Installieren von Windows PowerShell](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="2418a-158">For more information, see "[Installing Windows PowerShell](../../setup/installing-windows-powershell.md)".</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="2418a-159">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="2418a-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="2418a-160">Legt den Fensterstil für die Sitzung fest.</span><span class="sxs-lookup"><span data-stu-id="2418a-160">Sets the window style for the session.</span></span> <span data-ttu-id="2418a-161">Gültige Werte sind „Normal“, „Minimized“, „Maximized“ und „Hidden“.</span><span class="sxs-lookup"><span data-stu-id="2418a-161">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="2418a-162">-Command</span><span class="sxs-lookup"><span data-stu-id="2418a-162">-Command</span></span>

<span data-ttu-id="2418a-163">Führt die angegebenen Befehle (samt Parametern) so aus, als wären sie über die PowerShell-Befehlszeile eingegeben worden, und wird dann beendet, es sei denn, der „NoExit“-Parameter wird angegeben.</span><span class="sxs-lookup"><span data-stu-id="2418a-163">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>
<span data-ttu-id="2418a-164">Im Wesentlichen wird sämtlicher Text nach `-Command` als eine einzige Befehlszeile an PowerShell gesendet (dies unterscheidet sich davon, wie `-File` das Senden von Parametern an ein Skript behandelt).</span><span class="sxs-lookup"><span data-stu-id="2418a-164">Essentially, any text after `-Command` is sent as a single command line to PowerShell (this is different from how `-File` handles parameters sent to a script).</span></span>

<span data-ttu-id="2418a-165">Der Wert von „Command“ kann „-“, eine Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="2418a-165">The value of Command can be "-", a string.</span></span> <span data-ttu-id="2418a-166">oder ein Skriptblock sein.</span><span class="sxs-lookup"><span data-stu-id="2418a-166">or a script block.</span></span> <span data-ttu-id="2418a-167">Wenn der Wert des Befehls „-“ ist, wird der Befehlstext aus der Standardeingabe gelesen.</span><span class="sxs-lookup"><span data-stu-id="2418a-167">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="2418a-168">Skriptblöcke müssen in geschweifte Klammern ({}) gesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="2418a-168">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="2418a-169">Sie können einen Skriptblock nur angeben, wenn „PowerShell.exe“ in PowerShell ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2418a-169">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="2418a-170">Die Ergebnisse des Skripts werden an die übergeordnete Shell als deserialisierte XML-Objekte und nicht als Live-Objekte zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="2418a-170">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="2418a-171">Wenn der Wert von „Command“ eine Zeichenfolge ist, muss **Command** der letzte Parameter im Befehl sein, da alle Zeichen, die nach dem Befehl eingegeben werden, als die Befehlsargumente interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="2418a-171">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="2418a-172">Um eine Zeichenfolge zu schreiben, die einen PowerShell-Befehl ausführt, verwenden Sie das Format:</span><span class="sxs-lookup"><span data-stu-id="2418a-172">To write a string that runs a PowerShell command, use the format:</span></span>

```powershell
"& {<command>}"
```

<span data-ttu-id="2418a-173">wobei die Anführungszeichen eine Zeichenfolge angeben und der Aufrufoperator (&) bewirkt, dass der Befehl ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2418a-173">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="2418a-174">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="2418a-174">-Help, -?, /?</span></span>

<span data-ttu-id="2418a-175">Zeigt diese Meldung.</span><span class="sxs-lookup"><span data-stu-id="2418a-175">Shows this message.</span></span> <span data-ttu-id="2418a-176">Wenn Sie einen „PowerShell.exe“-Befehl in PowerShell eingeben, setzen Sie vor die Befehlsparameter einen Bindestrich (-) und keinen Schrägstrich (/).</span><span class="sxs-lookup"><span data-stu-id="2418a-176">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="2418a-177">In „Cmd.exe“ können Sie entweder einen Binde- oder Schrägstrich verwenden.</span><span class="sxs-lookup"><span data-stu-id="2418a-177">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="2418a-178">Hinweis zur Fehlerbehebung: In PowerShell 2.0 misslingt das Starten einiger Programme in der Windows PowerShell-Konsole mit dem folgenden „LastExitCode“: 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="2418a-178">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="2418a-179">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="2418a-179">EXAMPLES</span></span>

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