---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Arbeiten mit Dateien und Ordnern
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: 393e886a4945222198d9b81019250c5d5b905ad3
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293217"
---
# <a name="working-with-files-and-folders"></a>Arbeiten mit Dateien und Ordnern

Das Navigieren auf Windows PowerShell-Laufwerken und das Bearbeiten der darauf gespeicherten Elemente gleicht dem Bearbeiten von Dateien und Ordnern auf physischen Windows-Festplattenlaufwerken. In diesem Abschnitt werden bestimmte Aufgaben im Zusammenhang mit der Bearbeitung von Dateien und Ordnern mithilfe von PowerShell erörtert.

## <a name="listing-all-the-files-and-folders-within-a-folder"></a>Auflisten aller Dateien und Ordner in einem Ordner

Mit **Get-ChildItem** können Sie alle Elemente abrufen, die sich unmittelbar in einem Ordner befinden. Fügen Sie den optionalen Parameter **Force** hinzu, um ausgeblendete oder Systemelemente anzuzeigen. Dieser Befehl zeigt z. B. den unmittelbaren Inhalt der Windows PowerShell-Laufwerks C: an (dieses entspricht dem physischen Windows-Laufwerk C:):

```powershell
Get-ChildItem -Path C:\ -Force
```

Der Befehl listet nur die Elemente auf, die sich unmittelbar in dem Ordner befinden, ähnlich dem „Cmd.exe“-Befehl **DIR** oder **ls** in einer UNIX-Shell. Um enthaltene Elemente anzuzeigen, müssen Sie außerdem den Parameter **-Recurse** angeben. (Es kann sehr lange dauern, bis dieser Vorgang abgeschlossen ist.) So listen Sie alle Dateien auf Laufwerk C: auf:

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

Um mit **Get-ChildItem** Elemente zu filtern, verwenden Sie die Parameter **Path**, **Filter**, **Include** und **Exclude**, die allerdings nur auf Namen basieren. Zum Durchführen komplexer Filterung basierend auf anderen Eigenschaften verwenden Sie **Where-Object**.

Der folgende Befehl sucht alle ausführbaren Dateien im Ordner „Programme“, die nach dem 1. Oktober 2005 zuletzt geändert wurden und weder kleiner als 1 MB noch größer als 10 MB sind:

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a>Kopieren von Dateien und Ordner

Das Kopieren erfolgt mit **Copy-Item**. Der folgende Befehl sichert C:\\boot.ini nach C:\\boot.bak:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

Wenn die Zieldatei bereits vorhanden ist, schlägt der Kopierversuch fehl. Zum Überschreiben eines vorhandenen Ziels verwenden Sie den Parameter **Force**:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

Dieser Befehl funktioniert auch, wenn das Ziel schreibgeschützt ist.

Das Kopieren von Ordnern funktioniert auf dieselbe Weise. Dieser Befehl kopiert den Ordner „C:\\temp\\test1“ rekursiv nach „C:\\temp\\DeleteMe“:

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

Sie können auch eine Auswahl von Elementen kopieren. Der folgende Befehl kopiert alle TXT-Dateien, die an beliebiger Stelle in „c:\\data“ enthalten sind, nach „c:\\temp\\text“:

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

Sie können auch weiterhin andere Tools verwenden, um Dateisystemkopien auszuführen. XCOPY-, ROBOCOPY- und COM-Objekte, z. B. **Scripting.FileSystemObject,** können in Windows PowerShell verwendet werden. Sie können z.B. die Windows Script Host-Klasse **Scripting.FileSystem COM** verwenden, um „C:\\boot.ini“ nach „C:\\boot.bak“ zu sichern:

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a>Erstellen von Dateien und Ordnern

Das Erstellen neuer Elemente funktioniert auf allen Windows PowerShell-Anbietern gleich. Wenn ein Windows PowerShell-Anbieter über mehrere Elementtypen verfügt – der Dateisystem Windows PowerShell-Anbieter z. B. unterscheidet zwischen Verzeichnissen und Dateien – müssen Sie den Elementtyp angeben.

Dieser Befehl erstellt einen neuen Ordner „C:\\temp\\New Folder“:

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

Dieser Befehl erstellt eine neue leere Datei „C:\\temp\\New Folder\\file.txt“.

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a>Entfernen aller Dateien und Ordner in einem Ordner

Mit **Remove-Item** können Sie enthaltene Elemente entfernen. Wenn ein Element weitere Elemente enthält, werden Sie jedoch aufgefordert, das Entfernen zu bestätigen. Wenn Sie z.B. versuchen, den Ordner „C:\\temp\\DeleteMe“, der weitere Elemente enthält, zu löschen, fordert Windows PowerShell Sie vor dem Löschen des Ordners zur Bestätigung auf:

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Wenn Sie nicht für jedes enthaltene Element aufgefordert werden möchten, geben Sie den Parameter **Recurse** an:

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a>Zuordnen eines lokalen Ordners als ein zugreifbares Windows-Laufwerk

Sie können mithilfe des Befehls **subst** auch einen lokalen Ordner zuordnen. Der folgende Befehl erstellt ein lokales geroutetes Laufwerk P: im lokalen Verzeichnis „Programme“:

```powershell
subst p: $env:programfiles
```

Wie bei Netzlaufwerken sind in Windows PowerShell mit **subst** zugeordnete Laufwerke für die Windows PowerShell-Shell sofort sichtbar.

## <a name="reading-a-text-file-into-an-array"></a>Einlesen einer Textdatei in ein Array

Eine der häufigeren Speicherformate für Textdaten ist eine Datei mit separaten Zeilen, die als einzelne Datenelemente behandelt werden. Das Cmdlet **Get-Content** kann zum Lesen einer vollständigen Datei in einem Schritt verwendet werden, wie hier gezeigt:

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional
with Data Execution Prevention" /noexecute=optin /fastdetect
```

**Get-Content** behandelt die aus der Datei gelesenen Daten bereits als Array, mit je einem Element Dateiinhalt pro Zeile. Sie können dies anhand der Länge (**Length**) des zurückgegebenen Inhalts überprüfen:

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

Dieser Befehl ist besonders hilfreich zum Abrufen von Listen mit Informationen direkt in Windows PowerShell. Beispielsweise können Sie eine Liste von Computernamen oder IP-Adressen in einer Datei namens „C:\\temp\\domainMembers.txt“ speichern, wobei in jede Zeile der Datei je ein Name geschrieben wird. Mit **Get-Content** können Sie Dateiinhalte abrufen und in die Variable **$Computers** übernehmen:

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

**$Computers** ist jetzt ein Array mit einem Computernamen in jedem Element.
