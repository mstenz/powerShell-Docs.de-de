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

Parameter, die an das Skript übergeben werden, werden als Zeichenfolgenliterale übergeben (nach der Interpretation durch die aktuelle Shell). Wenn Sie in cmd.exe und Wert einer Umgebungsvariable übergeben möchten, würden Sie z. B. der cmd.exe-Syntax verwenden: `powershell.exe -File .\test.ps1 -TestParam %windir%`

Im Gegensatz dazu ausführen `powershell.exe -File .\test.ps1 -TestParam $env:windir` in cmd.exe führt das Skript mit dem Empfang der literalen Zeichenfolge `$env:windir` , da es keine spezielle Bedeutung für die aktuelle cmd.exe-Shell hat.
Die `$env:windir` Stil der Referenz zu Umgebungsvariablen _können_ in verwendet werden. eine `-Command` Parameter, da es ihn als PowerShell-Code interpretiert wird.

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
PowerShell nach der Ausführung wird beendet, es sei denn, die **NoExit** Parameter angegeben ist.
Sämtlicher Text nach `-Command` wird als eine einzige Befehlszeile an PowerShell gesendet.
Dies ist ein Unterschied zum Verhalten von `-File` bei der Verarbeitung von an ein Skript gesendete Parameter.

Der Wert des `-Command` kann "-", eine Zeichenfolge oder ein Skriptblock.
Die Ergebnisse des Befehls werden an die übergeordnete Shell als deserialisierte XML-Objekte, nicht als live-Objekte zurückgegeben.

Wenn der Wert des `-Command` ist "-", wird der Befehlstext aus der Standardeingabe gelesen.

Wenn der Wert des `-Command` ist eine Zeichenfolge, **Befehl** _müssen_ der letzte Parameter angegeben werden, da alle Zeichen eingegeben werden, nachdem der Befehl als die Befehlsargumente interpretiert werden.

Die **Befehl** Parameter akzeptiert nur einen Skriptblock für die Ausführung, wenn sie den übergebenen Wert erkennen kann `-Command` als Typ "scriptblock".
Dies ist _nur_ möglich, die bei der Ausführung des PowerShell.exe von einem anderen PowerShell-Host.
Der Typ kann in eine vorhandene Variable aus einem Ausdruck zurückgegebenen oder analysiert, indem Sie das PowerShell enthalten sein, "scriptblock" zu hosten, als literal Skriptblock in geschweiften Klammern `{}`, bevor an PowerShell.exe übergeben wird.

In cmd.exe, es gibt keine als Skriptblock (oder "scriptblock" Typ), also den übergebenen Wert **Befehl** wird _immer_ eine Zeichenfolge sein.
Sie können einen Skriptblock innerhalb der Zeichenfolge schreiben, aber ausgeführt wird es verhält sich genau als ob Sie sie in einer typischen PowerShell-Eingabeaufforderung eingegeben, Drucken des Inhalts des Skripts wieder für Sie blockiert.

Eine Zeichenfolge übergeben, um `-Command` weiterhin so ausgeführt, als PowerShell, sodass die geschweiften Klammern für Skript-Block häufig nicht erforderlich in erster Linie sind bei Ausführung von cmd.exe.
Zum Ausführen eines Inline-Skriptblock, der definiert, die in eine Zeichenfolge, die [Aufrufoperator](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` kann verwendet werden:

```console
"& {<command>}"
```

### <a name="-help---"></a>-Help, -?, /?

Zeigt die Syntax von „powershell.exe“. Wenn Sie einen „PowerShell.exe“-Befehl in PowerShell eingeben, setzen Sie vor die Befehlsparameter einen Bindestrich (-) und keinen Schrägstrich (/). In „Cmd.exe“ können Sie entweder einen Binde- oder Schrägstrich verwenden.

> [!NOTE]
> Hinweis zur Fehlerbehebung: In PowerShell 2.0 misslingt das Starten einiger Programme in der Windows PowerShell-Konsole mit dem folgenden „LastExitCode“: 0xc0000142.

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
