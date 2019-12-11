---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Verwalten des aktuellen Speicherorts
ms.openlocfilehash: 42ab56759dec882d140f813c8614e578957722b3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030206"
---
# <a name="managing-current-location"></a>Verwalten des aktuellen Speicherorts

Wenn Sie in Verzeichnissystemen im Datei-Explorer navigieren, haben Sie in der Regel einen bestimmten Arbeitsspeicherort, nämlich den aktuell geöffneten Ordner. Elemente im aktuellen Ordner können problemlos verarbeitet werden, indem auf sie geklickt wird. In Befehlszeilenschnittstellen wie z.B. „Cmd.exe“ gilt: Wenn Sie sich im selben Ordner wie eine bestimmte Datei befinden, können Sie darauf zugreifen, indem Sie einen relativ kurzen Namen angeben. Es ist nicht erforderlich, dass Sie den vollständigen Pfad zu der Datei angeben. Das aktuelle Verzeichnis wird als Arbeitsverzeichnis bezeichnet.

In Windows PowerShell wird das Substantiv **Location** verwendet, um auf das Arbeitsverzeichnis zu verweisen, und es sind einige Cmdlets implementiert, mit denen der Speicherort überprüft und geändert werden kann.

## <a name="getting-your-current-location-get-location"></a>Abrufen Ihres aktuellen Speicherorts (Get-Location)

Um den Pfad zu Ihrem aktuellen Verzeichnis zu ermitteln, geben Sie den Befehl **Get-Location** ein:

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Das Cdmlet „Get-Location“ ähnelt dem Befehl **pwd** in der BASH-Shell. Das Cdmlet „Set-Location“ ähnelt dem Befehl **cd** in „Cmd.exe“.

## <a name="setting-your-current-location-set-location"></a>Festlegen Ihres aktuellen Speicherorts (Set-Location)

Der Befehl **Get-Location** wird mit dem Befehl **Set-Location** verwendet. Der Befehl **Set-Location** ermöglicht es Ihnen, das aktuelle Verzeichnis anzugeben.

```powershell
Set-Location -Path C:\Windows
```

Nachdem Sie den Befehl eingegeben haben, erhalten Sie kein direktes Feedback zu den Auswirkungen des Befehls. Die meisten Windows PowerShell-Befehle, die eine Aktion ausführen, erzeugen nur wenig oder keine Ausgabe, da die Ausgabe nicht immer hilfreich ist. Um sich zu vergewissern, dass das Verzeichnis nach der Eingabe des Befehls **Set-Location** erfolgreich geändert wurde, fügen Sie den Parameter **-PassThru** ein, wenn Sie den Befehl **Set-Location** eingeben:

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

Der Parameter **-PassThru** kann mit vielen „Set“-Befehlen in Windows PowerShell verwendet werden, um Informationen über das Ergebnis in Fällen zurückzugeben, in denen keine Standardausgabe vorhanden ist.

Sie können Pfade, die relativ zu Ihrem aktuellen Speicherort sind, auf die gleiche Weise angeben, wie Sie dies in den meisten UNIX- und Windows-Befehlsshells tun würden. In der Standardschreibweise für relative Pfade stellt ein Punkt ( **.** ) Ihren aktuellen Ordner dar, und zwei Punkte ( **..** ) stellen das übergeordnete Verzeichnis Ihres aktuellen Speicherorts dar.

Wenn Sie sich beispielsweise im Ordner **C:\\Windows** befinden, stellt ein Punkt ( **.** ) **C:\\Windows** dar, während zwei Punkte ( **..** ) **C:** darstellen. Sie können aus Ihrem aktuellen Speicherort in das Stammverzeichnis des Laufwerks C: wechseln, indem Sie Folgendes eingeben:

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

Dieselbe Vorgehensweise funktioniert für Windows PowerShell-Laufwerke, die keine Dateisystemlaufwerke sind, etwa **HKLM:** . Sie können Ihren Speicherort auf den Schlüssel „HKLM\\Software“ in der Registrierung festlegen, indem Sie Folgendes eingeben:

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

Anschließend können Sie das Verzeichnis in das übergeordnete Verzeichnis ändern, das das Stammverzeichnis des Windows PowerShell-Laufwerks HKLM: ist, indem Sie einen relativen Pfad angeben:

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

Sie können „Set-Location“ eingeben oder einen der integrierten Windows PowerShell-Aliase für „Set-Location“ verwenden („cd“, „chdir“, „sl“). Beispiel:

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

## <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a>Speichern und Abrufen von zuletzt verwendeten Speicherorten („Push-Location“ und „Pop-Location“)

Wenn Sie Speicherorte wechseln, ist es sinnvoll, zu verfolgen, wo Sie waren, und in der Lage zu sein, zu Ihrem vorherigen Speicherort zurückzukehren. Das Cmdlet **Push-Location** in Windows PowerShell erstellt einen geordneten Verlauf (einen „Stapel“) der Verzeichnispfade, in denen Sie waren, und Sie können mithilfe des komplementären Cmdlets **Pop-Location** durch den Verlauf der Verzeichnispfade zurückgehen.

Beispielsweise startet Windows PowerShell üblicherweise im Basisverzeichnis des Benutzers.

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Das Wort *Stapel* hat in vielen Programmiereinstellungen eine besondere Bedeutung, so auch in NET Framework. Wie bei einem physischen Stapel von Elementen ist das letzte Elemente, das Sie auf dem Stapel ablegen, das erste Element, das Sie von dem Stapel herunternehmen können. Das Hinzufügen eines Elements zu einem Stapel wird gelegentlich als „Element mit Push auf dem Stapel ablegen“ bezeichnet. Das Herunternehmen eines Elements vom Stapel wird gelegentlich als „Element mit Pop aus dem Stapel entfernen“ bezeichnet.

Um den aktuellen Speicherort auf dem Stapel abzulegen und dann zum Ordner „Local Settings“ zu wechseln, geben Sie Folgendes ein:

```powershell
Push-Location -Path "Local Settings"
```

Sie können dann das Verzeichnis „Local Settings“ auf dem Stapel ablegen und zum Ordner „Temp“ wechseln, indem Sie Folgendes eingeben:

```powershell
Push-Location -Path Temp
```

Sie können sich vergewissern, dass Sie die Verzeichnisse geändert haben, indem Sie den Befehl **Get-Location** eingeben:

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

Sie können dann zurück zum zuletzt besuchten Verzeichnis wechseln, indem Sie den Befehl **Pop-Location** eingeben, und die Änderung überprüfen, indem Sie den Befehl **Get-Location** eingeben:

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

Wie beim Cdmlet **Set-Location** können Sie den Parameter **-PassThru** bei der Eingabe des Cdmlets **Pop-Location** einfügen, damit das Verzeichnis angezeigt wird, das Sie eingegeben haben:

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

Sie können die „Location“-Cdmlets auch mit Netzwerkpfaden verwenden. Wenn Sie einen Server namens „FS01“ mit einer Freigabe namens „Public“ haben, können Sie den Speicherort ändern, indem Sie Folgendes eingeben:

```powershell
Set-Location \\FS01\Public
```

oder

```powershell
Push-Location \\FS01\Public
```

Sie können die Befehle **Push-Location** und **Set-Location** verwenden, um den Speicherort in jedes verfügbare Laufwerk zu ändern. Wenn Sie z.B. ein lokales CD-ROM-Laufwerk mit dem Laufwerksbuchstaben D haben, das eine Daten-CD enthält, können Sie den Speicherort in das CD-Laufwerk ändern, indem Sie den Befehl **Set-Location D:** eingeben.

Ist das Laufwerk leer, wird die folgende Fehlermeldung angezeigt:

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

Wenn Sie eine Befehlszeilenschnittstelle verwenden, ist es nicht praktisch, den Datei-Explorer zu verwenden, um die verfügbaren physischen Laufwerken zu prüfen. Der Datei-Explorer zeigt darüber hinaus nicht alle Windows PowerShell-Laufwerke an. Windows PowerShell stellt eine Reihe von Befehlen zum Handhaben von Windows PowerShell-Laufwerken bereit, die im nächsten Abschnitt vorgestellt werden.
