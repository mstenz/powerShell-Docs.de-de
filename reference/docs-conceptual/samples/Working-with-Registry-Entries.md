---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Arbeiten mit Registrierungseinträge
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 8483b6f98739697b24a13055dfffbc7b5bacc2cc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678674"
---
# <a name="working-with-registry-entries"></a>Arbeiten mit Registrierungseinträge

Da Registrierungseinträge Eigenschaften von Schlüsseln sind und daher nicht direkt gesucht werden können, muss für die Arbeit mit diesen ein etwas anderer Ansatz gewählt werden.

### <a name="listing-registry-entries"></a>Auflisten von Registrierungseinträgen

Es gibt viele verschiedene Möglichkeiten zum Untersuchen von Registrierungseinträgen. Am einfachsten ist es, die Eigenschaftennamen mit einem Schlüssel zu verknüpfen. Um beispielsweise den Namen der Einträge im Registrierungsschlüssel finden Sie unter `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, verwenden Sie `Get-Item`. Registrierungsschlüssel verfügen über eine Eigenschaft mit dem generischen Namen „Property“, die eine Liste der Registrierungseinträge im Schlüssel ist.
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

Um die Registrierungseinträge in einer besser lesbaren Form anzuzeigen, verwenden `Get-ItemProperty`:

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

Sie können die Notation „`*.*`.“ zum Verweisen auf den aktuellen Speicherort verwenden. Sie können `Set-Location` so ändern Sie in der **"CurrentVersion"** registrierungscontainer erste:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Alternativ können Sie das integrierte HKLM PSDrive mit `Set-Location`:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Anschließend können Sie die Notation „`*.*`.“ für den aktuellen Speicherort verwenden, um die Eigenschaften aufzulisten, ohne einen vollständigen Pfad anzugeben:

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

Pfaderweiterung funktioniert genauso wie innerhalb des Dateisystems, damit von diesem Speicherort sollte man die **ItemProperty** für `HKLM:\SOFTWARE\Microsoft\Windows\Help` mit `Get-ItemProperty -Path ..\Help`.

### <a name="getting-a-single-registry-entry"></a>Abrufen eines einzelnen Registrierungseintrags

Wenn Sie einen bestimmten Eintrag in einem Registrierungsschlüssel abrufen möchten, stehen verschiedene Möglichkeiten zur Verfügung. In diesem Beispiel wird der Wert von **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.

Mithilfe von `Get-ItemProperty`, verwenden Sie die **Pfad** Parameter, um den Namen des Schlüssels anzugeben und die **Name** Parameter, um den Namen des der **DevicePath** Eintrag.

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
> Obwohl `Get-ItemProperty` hat **Filter**, **Include**, und **ausschließen** Parameter nach Namen Filtern nicht verwendet werden. Diese Parameter verweisen auf Registrierungsschlüssel, die sind elementpfade und keine Registrierungseinträge. Einträge in der Registrierung die Elementeigenschaften sind.

Eine weitere Option ist die Verwendung des Befehlszeilentools „Reg.exe“. Geben Sie für Hilfe mit reg.exe `reg.exe /?` an einer Eingabeaufforderung. Mithilfe von „reg.exe“ finden Sie den Eintrag „DevicePath“, wie im folgenden Befehl gezeigt:

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

Sie können das Objekt **WshShell COM** auch zum Suchen bestimmter Registrierungseinträge verwenden, obwohl diese Methode mit großen Binärdaten oder mit Registrierungseintragsnamen, die Zeichen wie „\\“ enthalten, nicht funktioniert. Fügen Sie den Namen der Eigenschaft mit einem \\-Trennzeichen zum Elementpfad hinzu:

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

### <a name="setting-a-single-registry-entry"></a>Festlegen eines einzelnen Registrierungseintrags

Wenn Sie einen bestimmten Eintrag in einem Registrierungsschlüssel ändern möchten, können Sie eine der mehrere mögliche Ansätze kennen. In diesem Beispiel ändert die **Pfad** Eintrag unter `HKEY_CURRENT_USER\Environment`. Die **Pfad** Eintrag gibt an, wo Sie ausführbare Dateien zu finden.

1. Abrufen des aktuellen Werts der **Pfad** Eintrag mit `Get-ItemProperty`.
2. Fügen Sie den neuen Wert, trennen sie mit einem `;`.
3. Verwendung `Set-ItemProperty` mit dem angegebenen Schlüssel, den Eintragsnamen und den Wert so ändern Sie den Registrierungseintrag.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> Obwohl `Set-ItemProperty` hat **Filter**, **Include**, und **ausschließen** Parameter nach Namen Filtern nicht verwendet werden. Diese Parameter verweisen auf Registrierungsschlüssel (das sind Elementpfade und keine Registrierungseinträge), die Elementeigenschaften sind.

Eine weitere Option ist die Verwendung des Befehlszeilentools „Reg.exe“. Um Hilfe zu „reg.exe“ zu erhalten, geben Sie **reg.exe /?** an einer Eingabeaufforderung ein.
an einer Eingabeaufforderung.

Im folgenden Beispiel wird geändert der **Pfad** Eintrag durch das Entfernen des Pfads, der im obigen Beispiel hinzugefügt.
`Get-ItemProperty` Dient zum Abrufen des aktuellen Werts um zu vermeiden, dass die Zeichenfolge, die von zurückgegeben analysiert weiterhin `reg query`. Die **Teilzeichenfolge** und **LastIndexOf** Methoden zum Abrufen des letzten Pfads hinzugefügt, die **Pfad** Eintrag.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

### <a name="creating-new-registry-entries"></a>Erstellen neuer Registrierungseinträge

Einen neuen Eintrag namens "PowerShellPath" zum Hinzufügen der **"CurrentVersion"** verwenden `New-ItemProperty` durch den Pfad zu den Schlüssel, dem Eintragsnamen und dem Wert des Eintrags. In diesem Beispiel dauert es, den Wert der Windows PowerShell-Variablen `$PSHome`, die den Pfad zum Installationsverzeichnis für Windows PowerShell speichert.

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

Sie können auch einen bereits vorhandenen registrierungseintragswert überschreiben, durch das Hinzufügen der **Force** Parameter an eine `New-ItemProperty` Befehl.

### <a name="renaming-registry-entries"></a>Umbenennen von Registrierungseinträgen

So benennen Sie um die **"powershellpath"** Eintrag in "PSHome", verwenden `Rename-ItemProperty`:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Um den umbenannten Wert anzuzeigen, fügen Sie dem Befehl den Parameter **PassThru** hinzu.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a>Löschen von Registrierungseinträgen

Um sowohl die "pshome" und "powershellpath" Registrierungseinträge zu löschen, verwenden `Remove-ItemProperty`:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
