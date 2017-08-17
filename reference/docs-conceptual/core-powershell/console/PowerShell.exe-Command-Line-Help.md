---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Befehlszeilenhilfe für „PowerShell.exe“"
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 4a14223dd024d967810a90dec10e416e4e35d6a2
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2017
---
# <a name="powershellexe-command-line-help"></a>Befehlszeilenhilfe für „PowerShell.exe“
Startet eine Windows PowerShell-Sitzung. Sie können mithilfe von „PowerShell.exe“ eine Windows PowerShell-Sitzung über die Befehlszeile eines anderen Tools wie z. B. „Cmd.exe“ starten oder mit diesem Befehl über die Windows PowerShell-Befehlszeile eine neue Sitzung starten. Verwenden Sie die Parameter, um die Sitzung anzupassen.

## <a name="syntax"></a>Syntax

```
PowerShell[.exe]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
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
       [-File <FilePath> [<Args>]]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a>Parameter

### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand <Base64EncodedCommand>
Akzeptiert eine „base-64“-codierte Zeichenfolgenversion eines Befehls. Verwenden Sie diesen Parameter, um Befehle an Windows PowerShell zu übermitteln, die komplexe Anführungszeichen oder geschweifte Klammern erfordern.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>
Legt die Standardausführungsrichtlinie für die aktuelle Sitzung fest und speichert sie in der Umgebungsvariablen „$env:PSExecutionPolicyPreference“. Dieser Parameter ändert nicht die Windows PowerShell-Ausführungsrichtlinie, die in der Registrierung festgelegt ist. Weitere Informationen zu Windows PowerShell-Ausführungsrichtlinien (einschließlich einer Liste gültiger Werte) finden Sie unter „about_Execution_Policies“ (http://go.microsoft.com/fwlink/?LinkID=135170).

### <a name="-file-filepath-parameters"></a>-File <FilePath> \[<Parameters>]
Führt das angegebene Skript im lokalen Bereich aus, sodass die Funktionen und Variablen, die das Skript erstellt, in der aktuellen Sitzung verfügbar sind. Geben Sie den Pfad der Skriptdatei und Parameter an. **File** muss der letzte Parameter im Befehl sein, da alle Zeichen, die nach dem **File**-Parameter eingegeben werden, als Pfad der Skriptdatei gefolgt von den Skriptparametern und ihren Werten interpretiert werden.

Sie können in den Wert des **File**-Parameters die Parameter eines Skripts und Parameterwerte einschließen. Beispiel: `-File .\Get-Script.ps1 -Domain Central` Beachten Sie, dass Parameter, die an das Skript übergeben werden, als Zeichenfolgenliterale übergeben werden (nach der Interpretation durch die aktuelle Shell).
Wenn Sie beispielsweise in „cmd.exe“ sind und den Wert einer Umgebungsvariable übergeben möchten, verwenden Sie die Syntax `powershell -File .\test.ps1 -Sample %windir%` von „cmd.exe“. Wenn Sie die PowerShell-Syntax verwenden, würde Ihr Skript in diesem Beispiel das Zeichenfolgenliteral „$env:windir“ erhalten und nicht den Wert der Umgebungsvariable: `powershell -File .\test.ps1 -Sample $env:windir`

Die Switch-Parameter eines Skripts werden in der Regel entweder einbezogen oder ausgelassen. Der folgende Befehl verwendet beispielsweise den **All**-Parameter der Skriptdatei „Get-Script.ps1“: `-File .\Get-Script.ps1 -All`

### <a name="-inputformat-text--xml"></a>\--InputFormat {Text | XML}
Beschreibt das Format der Daten, die an Windows PowerShell übermittelt werden. Gültige Werte sind "Text" (Textzeichenfolgen) oder "XML" (serialisiertes CLIXML-Format).

### <a name="-mta"></a>-Mta
Startet Windows PowerShell mit einem Multithread-Apartment. Dieser Parameter wird in Windows PowerShell 3.0 eingeführt. In Windows PowerShell 3.0 ist Singlethread-Apartment (STA) die Standardeinstellung. In Windows PowerShell 2.0 ist Multithread-Apartment (MTA) die Standardeinstellung.

### <a name="-noexit"></a>-NoExit
Nach dem Ausführen der Startbefehle erfolgt kein Beenden.

### <a name="-nologo"></a>-NoLogo
Blendet die Copyrightinformationen beim Start aus.

### <a name="-noninteractive"></a>-NonInteractive
Zeigt dem Benutzer keine interaktive Eingabeaufforderung.

### <a name="-noprofile"></a>-NoProfile
Das Windows PowerShell-Profil wird nicht geladen.

### <a name="-outputformat-text--xml"></a>-OutputFormat {Text | XML}
Bestimmt, wie die Ausgabe von Windows PowerShell formatiert ist. Gültige Werte sind "Text" (Textzeichenfolgen) oder "XML" (serialisiertes CLIXML-Format).

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>
Lädt die angegebene Windows PowerShell-Konsolendatei. Geben Sie den Pfad und Namen der Konsolendatei ein. Verwenden Sie zum Erstellen einer Konsolendatei das Cmdlet [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) in Windows PowerShell.

### <a name="-sta"></a>-Sta
Startet Windows PowerShell mit einem Singlethread-Apartment. In Windows PowerShell 3.0 ist Singlethread-Apartment (STA) die Standardeinstellung. In Windows PowerShell 2.0 ist Multithread-Apartment (MTA) die Standardeinstellung.

### <a name="-version-windows-powershell-version"></a>-Version <Windows PowerShell Version>
Startet die angegebene Version von Windows PowerShell. Die Version, die Sie angeben, muss auf dem System installiert sein. Falls Windows PowerShell 3.0 auf dem Computer installiert ist, sind „3.0“ und „2.0“ gültige Werte. Der Standardwert ist „3.0“.

Falls Windows PowerShell 3.0 nicht installiert ist, ist „2.0“ der einzige gültige Wert. Andere Werte werden ignoriert.

Weitere Informationen finden Sie unter „Installieren von Windows PowerShell“ in [Erste Schritte mit Windows PowerShell [ALTES MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>
Legt den Fensterstil für die Sitzung fest. Gültige Werte sind „Normal“, „Minimized“, „Maximized“ und „Hidden“.

### <a name="-command"></a>-Command
Führt die angegebenen Befehle (samt Parametern) so aus, als wären über die Windows PowerShell-Befehlszeile eingegeben worden, und wird dann beendet, es sei denn, der „NoExit“-Parameter wird angegeben.
Im Wesentlichen wird sämtlicher Text nach `-Command` als eine einzige Befehlszeile an PowerShell gesendet (dies unterscheidet sich davon, wie `-File` das Senden von Parametern an ein Skript behandelt).

Der Wert von „Command“ kann „-“, eine Zeichenfolge oder ein Skriptblock sein. Wenn der Wert des Befehls „-“ ist, wird der Befehlstext aus der Standardeingabe gelesen.

Skriptblöcke müssen in geschweifte Klammern ({}) gesetzt werden. Sie können einen Skriptblock nur angeben, wenn „PowerShell.exe“ in Windows PowerShell ausgeführt wird. Die Ergebnisse des Skripts werden an die übergeordnete Shell als deserialisierte XML-Objekte und nicht als Live-Objekte zurückgegeben.

Wenn der Wert von „Command“ eine Zeichenfolge ist, muss **Command** der letzte Parameter im Befehl sein, da alle Zeichen, die nach dem Befehl eingegeben werden, als die Befehlsargumente interpretiert werden.

Um eine Zeichenfolge zu schreiben, die einen Windows PowerShell-Befehl ausführt, verwenden Sie das Format:

```
"& {<command>}"
```

wobei die Anführungszeichen eine Zeichenfolge angeben und der Aufrufoperator (&) bewirkt, dass der Befehl ausgeführt wird.

### <a name="-help---"></a>-Help, -?, /?
Zeigt diese Meldung. Wenn Sie einen „PowerShell.exe“-Befehl in Windows PowerShell eingeben, setzen Sie vor die Befehlsparameter einen Bindestrich (-) und keinen Schrägstrich (/). In „Cmd.exe“ können Sie entweder einen Binde- oder Schrägstrich verwenden.

> [!NOTE]
> Hinweis zur Fehlerbehebung: In Windows PowerShell 2.0 misslingt das Starten einiger Programme in der Windows PowerShell-Konsole mit dem folgenden „LastExitCode“: 0xc0000142.

## <a name="examples"></a>BEISPIELE

```
PowerShell -PSConsoleFile sqlsnapin.psc1

PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

PowerShell -Command "Get-EventLog -LogName security"

# in an existing PowerShell session that understands the curly braces mean a script block
PowerShell -Command {Get-EventLog -LogName security}

PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```

