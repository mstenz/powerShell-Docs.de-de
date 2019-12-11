---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Arbeiten mit Registrierungseinträge
ms.openlocfilehash: c1fd6f57f13240eb2039f2d5756796678800aee0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030721"
---
# <a name="working-with-registry-entries"></a>Arbeiten mit Registrierungseinträge

Da Registrierungseinträge Eigenschaften von Schlüsseln sind und daher nicht direkt gesucht werden können, muss für die Arbeit mit diesen ein etwas anderer Ansatz gewählt werden.

## <a name="listing-registry-entries"></a>Auflisten von Registrierungseinträgen

Es gibt viele verschiedene Möglichkeiten zum Untersuchen von Registrierungseinträgen. Am einfachsten ist es, die Eigenschaftennamen mit einem Schlüssel zu verknüpfen. Wenn Sie beispielsweise die Namen der Einträge im Registrierungsschlüssel `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion` anzeigen möchten, verwenden Sie `Get-Item`. Registrierungsschlüssel verfügen über eine Eigenschaft mit dem generischen Namen „Property“, die eine Liste der Registrierungseinträge im Schlüssel ist.
Der folgende Befehl wählt die Eigenschaft „Property“ aus und erweitert die Elemente so, dass sie in einer Liste angezeigt werden:

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

Wenn Sie die Registrierungseinträge in einer besser lesbaren Form anzeigen möchten, verwenden Sie `Get-ItemProperty`:

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

Die Windows PowerShell-bezogenen Eigenschaften für den Schüssel verfügen alle über das Präfix „PS“, z.B. **PSPath**, **PSParentPath**, **PSChildName** und **PSProvider**.

Sie können die Notation `*.*` zum Verweisen auf den aktuellen Speicherort verwenden. Sie können `Set-Location` verwenden, um zuerst in den Registrierungscontainer **CurrentVersion** zu wechseln:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Alternativ dazu können Sie das integrierte HKLM PSDrive mit `Set-Location` verwenden:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Anschließend können Sie die Notation `*.*` für den aktuellen Speicherort verwenden, um die Eigenschaften aufzulisten, ohne einen vollständigen Pfad anzugeben:

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

Die Pfaderweiterung funktioniert genauso wie innerhalb des Dateisystems. Sie können daher von diesem Speicherort die Auflistung **ItemProperty** für `HKLM:\SOFTWARE\Microsoft\Windows\Help` abrufen, indem Sie `Get-ItemProperty -Path ..\Help` verwenden.

## <a name="getting-a-single-registry-entry"></a>Abrufen eines einzelnen Registrierungseintrags

Wenn Sie einen bestimmten Eintrag in einem Registrierungsschlüssel abrufen möchten, stehen verschiedene Möglichkeiten zur Verfügung. In diesem Beispiel wird der Wert von **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion` gesucht.

Verwenden Sie mit `Get-ItemProperty` den Parameter **Path**, um den Namen des Schlüssels anzugeben, und den Parameter **Name**, um den Namen des Eintrags **DevicePath** anzugeben.

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

Dieser Befehl gibt die standardmäßigen Windows PowerShell-Eigenschaften sowie die Eigenschaft **DevicePath** aus.

> [!NOTE]
> Obwohl `Get-ItemProperty` die Parameter **Filter**, **Include** und **Exclude** aufweist, können sie nicht zum Filtern nach dem Namen der Eigenschaft verwendet werden. Diese Parameter verweisen auf Registrierungsschlüssel, die Elementpfade und keine Registrierungseinträge sind. Registrierungseinträge sind Elementeigenschaften.

Eine weitere Option ist die Verwendung des Befehlszeilentools „Reg.exe“. Um Hilfe zu „reg.exe“ zu erhalten, geben Sie an einer Eingabeaufforderung `reg.exe /?` ein. Mithilfe von „reg.exe“ finden Sie den Eintrag „DevicePath“, wie im folgenden Befehl gezeigt:

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

(Sie können das COM-Objekt **WshShell** auch zum Suchen bestimmter Registrierungseinträge verwenden, obwohl diese Methode mit großen Binärdaten oder mit Registrierungseintragsnamen, die Zeichen wie „\\“ enthalten, nicht funktioniert.) Fügen Sie den Namen der Eigenschaft mit einem \\-Trennzeichen zum Elementpfad hinzu:

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

## <a name="setting-a-single-registry-entry"></a>Festlegen eines einzelnen Registrierungseintrags

Wenn Sie einen bestimmten Eintrag in einem Registrierungsschlüssel ändern möchten, stehen Ihnen verschiedene Möglichkeiten zur Verfügung. In diesem Beispiel wird der Eintrag **Path** unter `HKEY_CURRENT_USER\Environment` geändert. Der Eintrag **Path** gibt an, wo ausführbare Dateien zu finden sind.

1. Rufen Sie den aktuellen Wert des Eintrags **Path** mit `Get-ItemProperty` ab.
2. Fügen Sie den neuen Wert hinzu, und trennen Sie ihn mit `;`.
3. Verwenden Sie `Set-ItemProperty` mit dem angegebenen Schlüssel, Eintragsnamen und Wert, um den Registrierungseintrag zu ändern.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> Obwohl `Set-ItemProperty` die Parameter **Filter**, **Include** und **Exclude** aufweist, können sie nicht zum Filtern nach dem Namen der Eigenschaft verwendet werden. Diese Parameter verweisen auf Registrierungsschlüssel (das sind Elementpfade und keine Registrierungseinträge), die Elementeigenschaften sind.

Eine weitere Option ist die Verwendung des Befehlszeilentools „Reg.exe“. Um Hilfe zu „reg.exe“ zu erhalten, geben Sie **reg.exe /?** an einer Eingabeaufforderung ein.
an einer Eingabeaufforderung.

Im folgenden Beispiel wird der Eintrag **Path** geändert, indem der im vorstehenden Beispiel hinzugefügte Pfad entfernt wird.
`reg query` wird weiterhin zum Abrufen des aktuellen Werts verwendet, um zu vermeiden, dass die aus `Get-ItemProperty` zurückgegebene Zeichenfolge analysiert werden muss. Mit den Methoden **SubString** und **LastIndexOf** wird der letzte Pfad abgerufen, der dem Eintrag **Path** hinzugefügt wurde.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

## <a name="creating-new-registry-entries"></a>Erstellen neuer Registrierungseinträge

Verwenden Sie `New-ItemProperty` mit dem Pfad zum Schüssel, dem Eintragsnamen und dem Wert des Eintrags, um einen neuen Eintrag namens „PowerShellPath“ zum Schlüssel **CurrentVersion** hinzuzufügen. In diesem Beispiel wird der Wert der Windows PowerShell-Variablen `$PSHome` verwendet, in der der Pfad zum Installationsverzeichnis für Windows PowerShell gespeichert wird.

Sie können dem Schlüssel mit Hilfe des folgenden Befehls den neuen Eintrag hinzufügen, und der Befehl gibt auch Informationen zu dem neuen Eintrag zurück:

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

**PropertyType** muss der Namen eines **Microsoft.Win32.RegistryValueKind**-Aufzählungselements aus der folgenden Tabelle sein:

|PropertyType-Wert|Bedeutung|
|----------------------|-----------|
|Binär|Binärdaten|
|DWord|Eine Zahl, die eine gültige UInt32 ist|
|ExpandString|Eine Zeichenfolge, die Umgebungsvariablen enthalten kann, die dynamisch erweitert werden|
|MultiString|Eine mehrzeilige Zeichenfolge|
|Zeichenfolge|Ein beliebiger Zeichenfolgenwert|
|QWord|8 Byte Binärdaten|

> [!NOTE]
> Sie können einen Registrierungseintrag zu mehreren Speicherorten hinzufügen, indem Sie ein Array von Werten für den Parameter **Path** angeben:

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Sie können auch einen bereits vorhandenen Registrierungseintragswert überschreiben, indem Sie den Parameter **Force** an einen beliebigen `New-ItemProperty`-Befehl anfügen.

## <a name="renaming-registry-entries"></a>Umbenennen von Registrierungseinträgen

Verwenden Sie `Rename-ItemProperty`, um den Eintrag **PowerShellPath** in „PSHome“ umzubenennen:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Um den umbenannten Wert anzuzeigen, fügen Sie dem Befehl den Parameter **PassThru** hinzu.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

## <a name="deleting-registry-entries"></a>Löschen von Registrierungseinträgen

Verwenden Sie `Remove-ItemProperty`, um die Registrierungseinträge „PSHome“ und „PowerShellPath“ zu löschen:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
