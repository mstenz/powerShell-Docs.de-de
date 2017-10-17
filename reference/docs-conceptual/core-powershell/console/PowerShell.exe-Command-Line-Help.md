---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Befehlszeilenhilfe für „PowerShell.exe“"
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: c2583dac14f32db414f0a4377b1694ab7fa7523b
ms.sourcegitcommit: cd66d4f49ea762a31887af2c72d087b219ddbe10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2017
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="4ea85-103">Befehlszeilenhilfe für „PowerShell.exe“</span><span class="sxs-lookup"><span data-stu-id="4ea85-103">PowerShell.exe Command-Line Help</span></span>
<span data-ttu-id="4ea85-104">Startet eine Windows PowerShell-Sitzung.</span><span class="sxs-lookup"><span data-stu-id="4ea85-104">Starts a Windows PowerShell session.</span></span> <span data-ttu-id="4ea85-105">Sie können mithilfe von „PowerShell.exe“ eine Windows PowerShell-Sitzung über die Befehlszeile eines anderen Tools wie z. B. „Cmd.exe“ starten oder mit diesem Befehl über die Windows PowerShell-Befehlszeile eine neue Sitzung starten.</span><span class="sxs-lookup"><span data-stu-id="4ea85-105">You can use PowerShell.exe to start a Windows PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the Windows PowerShell command line to start a new session.</span></span> <span data-ttu-id="4ea85-106">Verwenden Sie die Parameter, um die Sitzung anzupassen.</span><span class="sxs-lookup"><span data-stu-id="4ea85-106">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="4ea85-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="4ea85-107">Syntax</span></span>

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
       [-PSConsoleFile <FilePath> | -Version <Windows PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]
        

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="4ea85-108">Parameter</span><span class="sxs-lookup"><span data-stu-id="4ea85-108">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="4ea85-109">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="4ea85-109">-EncodedCommand <Base64EncodedCommand></span></span>
<span data-ttu-id="4ea85-110">Akzeptiert eine „base-64“-codierte Zeichenfolgenversion eines Befehls.</span><span class="sxs-lookup"><span data-stu-id="4ea85-110">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="4ea85-111">Verwenden Sie diesen Parameter, um Befehle an Windows PowerShell zu übermitteln, die komplexe Anführungszeichen oder geschweifte Klammern erfordern.</span><span class="sxs-lookup"><span data-stu-id="4ea85-111">Use this parameter to submit commands to Windows PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="4ea85-112">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="4ea85-112">-ExecutionPolicy <ExecutionPolicy></span></span>
<span data-ttu-id="4ea85-113">Legt die Standardausführungsrichtlinie für die aktuelle Sitzung fest und speichert sie in der Umgebungsvariablen „$env:PSExecutionPolicyPreference“.</span><span class="sxs-lookup"><span data-stu-id="4ea85-113">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="4ea85-114">Dieser Parameter ändert nicht die Windows PowerShell-Ausführungsrichtlinie, die in der Registrierung festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="4ea85-114">This parameter does not change the Windows PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="4ea85-115">Weitere Informationen zu Windows PowerShell-Ausführungsrichtlinien (einschließlich einer Liste gültiger Werte) finden Sie unter „about_Execution_Policies“ (http://go.microsoft.com/fwlink/?LinkID=135170).</span><span class="sxs-lookup"><span data-stu-id="4ea85-115">For information about Windows PowerShell execution policies, including a list of valid values, see about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="4ea85-116">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="4ea85-116">-File <FilePath> \[<Parameters>]</span></span>
<span data-ttu-id="4ea85-117">Führt das angegebene Skript im lokalen Bereich aus, sodass die Funktionen und Variablen, die das Skript erstellt, in der aktuellen Sitzung verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="4ea85-117">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="4ea85-118">Geben Sie den Pfad der Skriptdatei und Parameter an.</span><span class="sxs-lookup"><span data-stu-id="4ea85-118">Enter the script file path and any parameters.</span></span> <span data-ttu-id="4ea85-119">**File** muss der letzte Parameter im Befehl sein, da alle Zeichen, die nach dem **File**-Parameter eingegeben werden, als Pfad der Skriptdatei gefolgt von den Skriptparametern und ihren Werten interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="4ea85-119">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="4ea85-120">Sie können in den Wert des **File**-Parameters die Parameter eines Skripts und Parameterwerte einschließen.</span><span class="sxs-lookup"><span data-stu-id="4ea85-120">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="4ea85-121">Beispiel: `-File .\Get-Script.ps1 -Domain Central` Beachten Sie, dass Parameter, die an das Skript übergeben werden, als Zeichenfolgenliterale übergeben werden (nach der Interpretation durch die aktuelle Shell).</span><span class="sxs-lookup"><span data-stu-id="4ea85-121">For example: `-File .\Get-Script.ps1 -Domain Central` Note that parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span>
<span data-ttu-id="4ea85-122">Wenn Sie beispielsweise in „cmd.exe“ sind und den Wert einer Umgebungsvariable übergeben möchten, verwenden Sie die Syntax `powershell -File .\test.ps1 -Sample %windir%` von „cmd.exe“. Wenn Sie die PowerShell-Syntax verwenden, würde Ihr Skript in diesem Beispiel das Zeichenfolgenliteral „$env:windir“ erhalten und nicht den Wert der Umgebungsvariable: `powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="4ea85-122">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` If you were to use PowerShell syntax, then in this example your script would receive the literal "$env:windir" and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

<span data-ttu-id="4ea85-123">Die Switch-Parameter eines Skripts werden in der Regel entweder einbezogen oder ausgelassen.</span><span class="sxs-lookup"><span data-stu-id="4ea85-123">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="4ea85-124">Der folgende Befehl verwendet beispielsweise den **All**-Parameter der Skriptdatei „Get-Script.ps1“: `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="4ea85-124">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="4ea85-125">\--InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="4ea85-125">\-InputFormat {Text | XML}</span></span>
<span data-ttu-id="4ea85-126">Beschreibt das Format der Daten, die an Windows PowerShell übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="4ea85-126">Describes the format of data sent to Windows PowerShell.</span></span> <span data-ttu-id="4ea85-127">Gültige Werte sind "Text" (Textzeichenfolgen) oder "XML" (serialisiertes CLIXML-Format).</span><span class="sxs-lookup"><span data-stu-id="4ea85-127">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="4ea85-128">-Mta</span><span class="sxs-lookup"><span data-stu-id="4ea85-128">-Mta</span></span>
<span data-ttu-id="4ea85-129">Startet Windows PowerShell mit einem Multithread-Apartment.</span><span class="sxs-lookup"><span data-stu-id="4ea85-129">Starts Windows PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="4ea85-130">Dieser Parameter wird in Windows PowerShell 3.0 eingeführt.</span><span class="sxs-lookup"><span data-stu-id="4ea85-130">This parameter is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="4ea85-131">In Windows PowerShell 3.0 ist Singlethread-Apartment (STA) die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="4ea85-131">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="4ea85-132">In Windows PowerShell 2.0 ist Multithread-Apartment (MTA) die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="4ea85-132">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="4ea85-133">-NoExit</span><span class="sxs-lookup"><span data-stu-id="4ea85-133">-NoExit</span></span>
<span data-ttu-id="4ea85-134">Nach dem Ausführen der Startbefehle erfolgt kein Beenden.</span><span class="sxs-lookup"><span data-stu-id="4ea85-134">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="4ea85-135">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="4ea85-135">-NoLogo</span></span>
<span data-ttu-id="4ea85-136">Blendet die Copyrightinformationen beim Start aus.</span><span class="sxs-lookup"><span data-stu-id="4ea85-136">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="4ea85-137">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="4ea85-137">-NonInteractive</span></span>
<span data-ttu-id="4ea85-138">Zeigt dem Benutzer keine interaktive Eingabeaufforderung.</span><span class="sxs-lookup"><span data-stu-id="4ea85-138">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="4ea85-139">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="4ea85-139">-NoProfile</span></span>
<span data-ttu-id="4ea85-140">Das Windows PowerShell-Profil wird nicht geladen.</span><span class="sxs-lookup"><span data-stu-id="4ea85-140">Does not load the Windows PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="4ea85-141">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="4ea85-141">-OutputFormat {Text | XML}</span></span>
<span data-ttu-id="4ea85-142">Bestimmt, wie die Ausgabe von Windows PowerShell formatiert ist.</span><span class="sxs-lookup"><span data-stu-id="4ea85-142">Determines how output from Windows PowerShell is formatted.</span></span> <span data-ttu-id="4ea85-143">Gültige Werte sind "Text" (Textzeichenfolgen) oder "XML" (serialisiertes CLIXML-Format).</span><span class="sxs-lookup"><span data-stu-id="4ea85-143">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="4ea85-144">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="4ea85-144">-PSConsoleFile <FilePath></span></span>
<span data-ttu-id="4ea85-145">Lädt die angegebene Windows PowerShell-Konsolendatei.</span><span class="sxs-lookup"><span data-stu-id="4ea85-145">Loads the specified Windows PowerShell console file.</span></span> <span data-ttu-id="4ea85-146">Geben Sie den Pfad und Namen der Konsolendatei ein.</span><span class="sxs-lookup"><span data-stu-id="4ea85-146">Enter the path and name of the console file.</span></span> <span data-ttu-id="4ea85-147">Verwenden Sie zum Erstellen einer Konsolendatei das Cmdlet [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4ea85-147">To create a console file, use the [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet in Windows PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="4ea85-148">-Sta</span><span class="sxs-lookup"><span data-stu-id="4ea85-148">-Sta</span></span>
<span data-ttu-id="4ea85-149">Startet Windows PowerShell mit einem Singlethread-Apartment.</span><span class="sxs-lookup"><span data-stu-id="4ea85-149">Starts Windows PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="4ea85-150">In Windows PowerShell 3.0 ist Singlethread-Apartment (STA) die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="4ea85-150">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="4ea85-151">In Windows PowerShell 2.0 ist Multithread-Apartment (MTA) die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="4ea85-151">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-windows-powershell-version"></a><span data-ttu-id="4ea85-152">-Version <Windows PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="4ea85-152">-Version <Windows PowerShell Version></span></span>
<span data-ttu-id="4ea85-153">Startet die angegebene Version von Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4ea85-153">Starts the specified version of Windows PowerShell.</span></span> <span data-ttu-id="4ea85-154">Die Version, die Sie angeben, muss auf dem System installiert sein.</span><span class="sxs-lookup"><span data-stu-id="4ea85-154">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="4ea85-155">Falls Windows PowerShell 3.0 auf dem Computer installiert ist, sind „3.0“ und „2.0“ gültige Werte.</span><span class="sxs-lookup"><span data-stu-id="4ea85-155">If Windows PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="4ea85-156">Der Standardwert ist „3.0“.</span><span class="sxs-lookup"><span data-stu-id="4ea85-156">The default value is "3.0".</span></span>

<span data-ttu-id="4ea85-157">Falls Windows PowerShell 3.0 nicht installiert ist, ist „2.0“ der einzige gültige Wert.</span><span class="sxs-lookup"><span data-stu-id="4ea85-157">If Windows PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="4ea85-158">Andere Werte werden ignoriert.</span><span class="sxs-lookup"><span data-stu-id="4ea85-158">Other values are ignored.</span></span>

<span data-ttu-id="4ea85-159">Weitere Informationen finden Sie unter „Installieren von Windows PowerShell“ in [Erste Schritte mit Windows PowerShell [ALTES MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span><span class="sxs-lookup"><span data-stu-id="4ea85-159">For more information, see "Installing Windows PowerShell" in the [Getting Started with Windows PowerShell [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="4ea85-160">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="4ea85-160">-WindowStyle <Window style></span></span>
<span data-ttu-id="4ea85-161">Legt den Fensterstil für die Sitzung fest.</span><span class="sxs-lookup"><span data-stu-id="4ea85-161">Sets the window style for the session.</span></span> <span data-ttu-id="4ea85-162">Gültige Werte sind „Normal“, „Minimized“, „Maximized“ und „Hidden“.</span><span class="sxs-lookup"><span data-stu-id="4ea85-162">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="4ea85-163">-Command</span><span class="sxs-lookup"><span data-stu-id="4ea85-163">-Command</span></span>
<span data-ttu-id="4ea85-164">Führt die angegebenen Befehle (samt Parametern) so aus, als wären über die Windows PowerShell-Befehlszeile eingegeben worden, und wird dann beendet, es sei denn, der „NoExit“-Parameter wird angegeben.</span><span class="sxs-lookup"><span data-stu-id="4ea85-164">Executes the specified commands (and any parameters) as though they were typed at the Windows PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>
<span data-ttu-id="4ea85-165">Im Wesentlichen wird sämtlicher Text nach `-Command` als eine einzige Befehlszeile an PowerShell gesendet (dies unterscheidet sich davon, wie `-File` das Senden von Parametern an ein Skript behandelt).</span><span class="sxs-lookup"><span data-stu-id="4ea85-165">Essentially, any text after `-Command` is sent as a single command line to PowerShell (this is different from how `-File` handles parameters sent to a script).</span></span>

<span data-ttu-id="4ea85-166">Der Wert von „Command“ kann „-“, eine Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="4ea85-166">The value of Command can be "-", a string.</span></span> <span data-ttu-id="4ea85-167">oder ein Skriptblock sein.</span><span class="sxs-lookup"><span data-stu-id="4ea85-167">or a script block.</span></span> <span data-ttu-id="4ea85-168">Wenn der Wert des Befehls „-“ ist, wird der Befehlstext aus der Standardeingabe gelesen.</span><span class="sxs-lookup"><span data-stu-id="4ea85-168">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="4ea85-169">Skriptblöcke müssen in geschweifte Klammern ({}) gesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="4ea85-169">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="4ea85-170">Sie können einen Skriptblock nur angeben, wenn „PowerShell.exe“ in Windows PowerShell ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="4ea85-170">You can specify a script block only when running PowerShell.exe in Windows PowerShell.</span></span> <span data-ttu-id="4ea85-171">Die Ergebnisse des Skripts werden an die übergeordnete Shell als deserialisierte XML-Objekte und nicht als Live-Objekte zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="4ea85-171">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="4ea85-172">Wenn der Wert von „Command“ eine Zeichenfolge ist, muss **Command** der letzte Parameter im Befehl sein, da alle Zeichen, die nach dem Befehl eingegeben werden, als die Befehlsargumente interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="4ea85-172">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="4ea85-173">Um eine Zeichenfolge zu schreiben, die einen Windows PowerShell-Befehl ausführt, verwenden Sie das Format:</span><span class="sxs-lookup"><span data-stu-id="4ea85-173">To write a string that runs a Windows PowerShell command, use the format:</span></span>

```
"& {<command>}"
```

<span data-ttu-id="4ea85-174">wobei die Anführungszeichen eine Zeichenfolge angeben und der Aufrufoperator (&) bewirkt, dass der Befehl ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="4ea85-174">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="4ea85-175">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="4ea85-175">-Help, -?, /?</span></span>
<span data-ttu-id="4ea85-176">Zeigt diese Meldung.</span><span class="sxs-lookup"><span data-stu-id="4ea85-176">Shows this message.</span></span> <span data-ttu-id="4ea85-177">Wenn Sie einen „PowerShell.exe“-Befehl in Windows PowerShell eingeben, setzen Sie vor die Befehlsparameter einen Bindestrich (-) und keinen Schrägstrich (/).</span><span class="sxs-lookup"><span data-stu-id="4ea85-177">If you are typing a PowerShell.exe command in Windows PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="4ea85-178">In „Cmd.exe“ können Sie entweder einen Binde- oder Schrägstrich verwenden.</span><span class="sxs-lookup"><span data-stu-id="4ea85-178">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="4ea85-179">Hinweis zur Fehlerbehebung: In Windows PowerShell 2.0 misslingt das Starten einiger Programme in der Windows PowerShell-Konsole mit dem folgenden „LastExitCode“: 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="4ea85-179">Troubleshooting Note: In Windows PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="4ea85-180">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="4ea85-180">EXAMPLES</span></span>

```
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a Powerhell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate wayh to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```

