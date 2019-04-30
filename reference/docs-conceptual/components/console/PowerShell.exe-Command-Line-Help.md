---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Befehlszeilenhilfe für „PowerShell.exe“
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058512"
---
# <a name="powershellexe-command-line-help"></a>Befehlszeilenhilfe für „PowerShell.exe“

Sie können mithilfe von „PowerShell.exe“ eine PowerShell-Sitzung über die Befehlszeile eines anderen Tools wie z. B. „Cmd.exe“ starten oder mit diesem Befehl über die PowerShell-Befehlszeile eine neue Sitzung starten. Verwenden Sie die Parameter, um die Sitzung anzupassen.

## <a name="syntax"></a>Syntax

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

## <a name="parameters"></a>Parameter

### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand <Base64EncodedCommand>

Akzeptiert eine „base-64“-codierte Zeichenfolgenversion eines Befehls. Verwenden Sie diesen Parameter, um Befehle an PowerShell zu übermitteln, die komplexe Anführungszeichen oder geschweifte Klammern erfordern.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>

Legt die Standardausführungsrichtlinie für die aktuelle Sitzung fest und speichert sie in der Umgebungsvariablen „$env:PSExecutionPolicyPreference“. Dieser Parameter ändert die PowerShell-Ausführungsrichtlinie nicht, die in der Registrierung festgelegt ist. Weitere Informationen zu PowerShell-Ausführungsrichtlinien (einschließlich einer Liste gültiger Werte) finden Sie unter [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

### <a name="-file-filepath-parameters"></a>-File <FilePath> \[<Parameters>]

Führt das angegebene Skript im lokalen Bereich aus, sodass die Funktionen und Variablen, die das Skript erstellt, in der aktuellen Sitzung verfügbar sind. Geben Sie den Pfad der Skriptdatei und Parameter an. **File** muss der letzte Parameter im Befehl sein. Alle Werte, die nach dem **-File**-Parameter eingegeben werden, werden als Skriptdateipfad und als an das Skript übergebene Parameter interpretiert.

Parameter, die an das Skript übergeben werden, werden als Zeichenfolgenliterale übergeben (nach der Interpretation durch die aktuelle Shell). Wenn Sie beispielsweise aus „cmd.exe“ einen Wert für eine Umgebungsvariable übergeben möchten, verwenden Sie die cmd.exe-Syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`

Im Gegensatz dazu führt die Ausführung von `powershell.exe -File .\test.ps1 -TestParam $env:windir` in „cmd.exe“ dazu, dass das Skript die literale Zeichenfolge `$env:windir` erhält, da sie für die aktuelle cmd.exe-Shell keine besondere Bedeutung besitzt.
Die `$env:windir`-Syntax des Umgebungsvariablenverweises _kann_ innerhalb eines `-Command`-Parameters verwendet werden, da er dort als PowerShell-Code interpretiert wird.

### <a name="-inputformat-text--xml"></a>\--InputFormat {Text | XML}

Beschreibt das Format der Daten, die an PowerShell übermittelt werden. Gültige Werte sind "Text" (Textzeichenfolgen) oder "XML" (serialisiertes CLIXML-Format).

### <a name="-mta"></a>-Mta

Startet PowerShell mit einem Multithread-Apartment. Dieser Parameter wird in Windows PowerShell 3.0 eingeführt. In PowerShell 3.0 ist Singlethread-Apartment (STA) die Standardeinstellung. In PowerShell 2.0 stellt Multithread-Apartment (MTA) die Standardeinstellung dar.

### <a name="-noexit"></a>-NoExit

Nach dem Ausführen der Startbefehle erfolgt kein Beenden.

### <a name="-nologo"></a>-NoLogo

Blendet die Copyrightinformationen beim Start aus.

### <a name="-noninteractive"></a>-NonInteractive

Zeigt dem Benutzer keine interaktive Eingabeaufforderung.

### <a name="-noprofile"></a>-NoProfile

Das PowerShell-Profil wird nicht geladen.

### <a name="-outputformat-text--xml"></a>-OutputFormat {Text | XML}

Bestimmt, wie die Ausgabe von PowerShell formatiert ist. Gültige Werte sind "Text" (Textzeichenfolgen) oder "XML" (serialisiertes CLIXML-Format).

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>

Lädt die angegebene PowerShell-Konsolendatei. Geben Sie den Pfad und Namen der Konsolendatei ein. Verwenden Sie zum Erstellen einer Konsolendatei das Cmdlet [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) in PowerShell.

### <a name="-sta"></a>-Sta

Startet PowerShell mit einem Singlethread-Apartment. In PowerShell 3.0 ist Singlethread-Apartment (STA) die Standardeinstellung. In PowerShell 2.0 stellt Multithread-Apartment (MTA) die Standardeinstellung dar.

### <a name="-version-powershell-version"></a>-Version <PowerShell Version>

Startet die angegebene Version von PowerShell. Die Version, die Sie angeben, muss auf dem System installiert sein. Falls PowerShell 3.0 auf dem Computer installiert ist, sind „2.0“ und „3.0“ gültige Werte. Der Standardwert ist „3.0“.

Falls PowerShell 3.0 nicht installiert ist, ist „2.0“ der einzige gültige Wert. Andere Werte werden ignoriert.

Weitere Informationen finden Sie unter [Installieren von Windows PowerShell](../../setup/installing-windows-powershell.md).

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>

Legt den Fensterstil für die Sitzung fest. Gültige Werte sind „Normal“, „Minimized“, „Maximized“ und „Hidden“.

### <a name="-command"></a>-Command

Führt die angegebenen Befehle (mit den Parametern) so aus, als wären sie über die PowerShell-Befehlszeile eingegeben worden.
Nach der Ausführung wird PowerShell beendet, es sei denn, der **NoExit**-Parameter wird angegeben.
Sämtlicher Text nach `-Command` wird als eine einzige Befehlszeile an PowerShell gesendet.
Dies ist ein Unterschied zum Verhalten von `-File` bei der Verarbeitung von an ein Skript gesendete Parameter.

Der Wert von `-Command` kann „-“, eine Zeichenfolge oder ein Skriptblock sein.
Die Ergebnisse des Befehls werden an die übergeordnete Shell als deserialisierte XML-Objekte und nicht als Liveobjekte zurückgegeben.

Wenn der Wert von `-Command` „-“ ist, wird der Befehlstext aus der Standardeingabe gelesen.

Wenn der Wert von `-Command` eine Zeichenfolge ist, _muss_ **Command** der letzte angegebene Parameter sein, da alle Zeichen, die nach dem Befehl eingegeben werden, als Befehlsargumente interpretiert werden.

Der Parameter **Command** akzeptiert einen Skriptblock nur dann zur Ausführung, wenn er den an `-Command` übergebenen Wert als SkriptBlock-Typ erkennen kann.
Dies ist _nur_ möglich, wenn „PowerShell.exe“ von einem anderen PowerShell-Host ausgeführt wird.
Der Typ ScriptBlock kann in einer vorhandenen Variablen enthalten sein, von einem Ausdruck zurückgegeben oder vom PowerShell-Host als literaler Skriptblock analysiert werden, der in geschweifte Klammern `{}` eingeschlossen ist, bevor er an „PowerShell.exe“ übergeben wird.

In „cmd.exe“ gibt es keine Skriptblöcke (oder ScriptBlock-Typen), sodass der an **Command** übergebene Wert _immer_ eine Zeichenfolge ist.
Sie können einen Skriptblock innerhalb der Zeichenfolge schreiben, aber anstatt ausgeführt zu werden, verhält er sich genau so, als ob Sie ihn an einer typischen PowerShell-Eingabeaufforderung eingegeben hätten, wobei der Inhalt des Skriptblocks wieder an Sie ausgegeben wird.

Eine an `-Command` übergebene Zeichenfolge wird weiterhin als PowerShell ausgeführt, sodass die geschweiften Klammern des Skriptblocks beim der Ausführung aus „cmd.exe“ oft gar nicht erst erforderlich sind.
Zum Ausführen eines Inlineskriptblocks, der in einer Zeichenfolge definiert ist, kann der [Aufrufoperator](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` verwendet werden:

```console
"& {<command>}"
```

### <a name="-help---"></a>-Help, -?, /?

Zeigt die Syntax von „powershell.exe“. Wenn Sie einen „PowerShell.exe“-Befehl in PowerShell eingeben, setzen Sie vor die Befehlsparameter einen Bindestrich (-) und keinen Schrägstrich (/). In „Cmd.exe“ können Sie entweder einen Binde- oder Schrägstrich verwenden.

> [!NOTE]
> Hinweis zur Problembehandlung: In PowerShell 2.0 tritt beim Starten einiger Programme in der Windows PowerShell-Konsole ein Fehler mit dem folgenden LastExitCode auf: 0xc0000142.

## <a name="examples"></a>BEISPIELE

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
