---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Erfassen von Informationen über Computer
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: d837684108656e17ebf26189bd4841c5de01051c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058334"
---
# <a name="collecting-information-about-computers"></a>Erfassen von Informationen über Computer

Cmdlets des Moduls **CimCmdlets** sind die wichtigsten Cmdlets für einfache Tasks zur Systemverwaltung.
Alle kritischen Subsystemeinstellungen werden über WMI verfügbar gemacht.
Darüber hinaus behandelt WMI Daten als Objekte, die zu Sammlungen eines oder mehrerer Elemente gehören.
Da Windows PowerShell ebenfalls mit Objekten arbeitet und über eine Pipeline verfügt, mit der Sie einzelne oder mehrere Objekte auf die gleiche Weise behandeln können, ermöglicht der generische WMI-Zugriff Ihnen, einige erweiterte Aufgaben mit sehr geringem Aufwand auszuführen.

In den folgenden Beispielen wird gezeigt, wie Sie mit `Get-CimInstance` spezifische Informationen für einen beliebigen Computer sammeln.
Sie geben den Parameter **ComputerName** mit dem Punkt (**.**) als Wert an, der den lokalen Computer darstellt.
Sie können einen Namen oder eine IP-Adresse eines beliebigen Computers angeben, den Sie über WMI erreichen können.
Zum Abrufen von Informationen über den lokalen Computer können Sie den Parameter **ComputerName** weglassen.

## <a name="listing-desktop-settings"></a>Auflisten von Desktopeinstellungen

Wir beginnen mit einem Befehl, der Informationen über die Desktops auf dem lokalen Computer erfasst.

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

Dadurch werden Informationen über alle Desktops zurückgegeben, ganz gleich, ob sie verwendet werden oder nicht.

> [!NOTE]
> Einige WMI-Klassen geben sehr detaillierte Informationen zurück, die häufig Metadaten über die WMI-Klasse enthalten.
Da die meisten dieser Metadateneigenschaften über Namen verfügen, die mit **Cim** beginnen, können Sie die Eigenschaften mit `Select-Object` filtern.
Geben Sie dem Parameter **-ExcludeProperty** mit „Cim*“ als Wert an.
Beispiel:

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Um die Metadaten zu filtern, verwenden Sie einen Pipelineoperator (|), um die Ergebnisse des Befehls `Get-CimInstance` an `Select-Object -ExcludeProperty "CIM*"` zu senden.

## <a name="listing-bios-information"></a>Auflisten von BIOS-Informationen

Die WMI-Klasse **Win32_BIOS** gibt kompakte und vollständige Informationen zum System-BIOS auf dem lokalen Computer zurück:

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

## <a name="listing-processor-information"></a>Auflisten von Prozessorinformationen

Sie können allgemeine Prozessorinformationen mithilfe der WMI-Klasse **Win32_Processor** abrufen. Allerdings möchten Sie die Daten wahrscheinlich filtern:

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Wenn Sie eine Zeichenfolge mit einer allgemeinen Beschreibung der Prozessorfamilie erhalten möchten, lassen Sie die **SystemType**-Eigenschaft zurückgeben:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a>Auflisten von Informationen zum Computerhersteller und -modell

Informationen zum Computermodell sind auch über **Win32_ComputerSystem** verfügbar.
Zum Bereitstellen von OEM-Daten ist keine Filterung der angezeigten Standardausgabe erforderlich:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

Die Ausgabe von Befehlen, die Informationen direkt von bestimmter Hardware zurückgeben, kann nur so gut sein, wie die vorhandenen Daten.
Einige Informationen wurden von den Hardwareherstellern nicht ordnungsgemäß konfiguriert und sind daher möglicherweise nicht verfügbar.

## <a name="listing-installed-hotfixes"></a>Auflisten installierter Hotfixes

Mit **Win32_QuickFixEngineering** können Sie alle installierten Hotfixes auflisten:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

Diese Klasse gibt eine Liste von Hotfixes zurück, die wie folgt aussieht:

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

Wenn Sie eine kompaktere Ausgabe erhalten möchten, können Sie bestimmte Eigenschaften ausschließen.
Sie können zwar den `Get-CimInstance`Property **-Parameter von**  verwenden, um nur die **HotFixID** auszuwählen. Dennoch werden weitere Informationen zurückgegeben, da standardmäßig alle Metadaten angezeigt werden:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixID
```

```output
PSShowComputerName    : True
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4048951
InstalledBy           :
ServicePackInEffect   :
PSComputerName        : .
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

Die zusätzlichen Daten werden zurückgegeben, weil der „Property“-Parameter in `Get-CimInstance` die von WMI-Klasseninstanzen zurückgegebenen Eigenschaften, nicht aber das an die Windows PowerShell zurückgegebene Objekt einschränkt.
Um die Ausgabe zu verringern, verwenden Sie `Select-Object`:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a>Auflisten von Informationen zur Betriebssystemversion

Die Klasseneigenschaften **Win32_OperatingSystem** umfassen Informationen zur Version und zum Service Pack.
Sie können mit **Win32_OperatingSystem** explizit nur diese Eigenschaften auswählen, um eine Zusammenfassung von Versionsinformationen abzurufen:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

Sie können mit dem **Property**-Parameter von `Select-Object` auch Platzhalterzeichen verwenden.
Da alle Eigenschaften, die entweder mit **Build** oder **Service Pack** beginnen, hier wichtig sind, können wir das Beispiel auf das folgende Format kürzen:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*
```

```output
BuildNumber             : 16299
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

## <a name="listing-local-users-and-owner"></a>Auflisten der lokalen Benutzer und des Besitzers

Allgemeine lokale Benutzerinformationen (z.B. Anzahl lizenzierter Benutzer, aktuelle Anzahl von Benutzern und Besitzername) können Sie mit einer Auswahl von **Win32_OperatingSystem**-Klasseneigenschaften suchen.
Sie können die anzuzeigenden Eigenschaften wie folgt explizit auswählen:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Eine kompaktere Version mit Platzhaltern ist:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a>Abrufen des verfügbaren Speicherplatzes

Um den Speicherplatz und den freien Speicherplatz auf lokalen Laufwerken anzuzeigen, können Sie die WMI-Klasse „Win32_LogicalDisk“ verwenden.
Sie brauchen nur Instanzen mit einem „DriveType“-Wert von „3“ anzuzeigen. Dieser Wert wird von WMI für Festplatten mit fester Größe verwendet.

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .

Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum

Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

## <a name="getting-logon-session-information"></a>Abrufen von Informationen zur Anmeldesitzung

Allgemeine Informationen zu Benutzern zugeordneten Anmeldesitzungen können Sie über die WMI-Klasse **Win32_LogonSession** abrufen:

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

## <a name="getting-the-user-logged-on-to-a-computer"></a>Abrufen des auf einem Computer angemeldeten Benutzers

Mit „Win32_ComputerSystem“ können Sie den auf einem bestimmten Computer angemeldeten Benutzers anzeigen.
Dieser Befehl gibt nur den auf dem Systemdesktop angemeldeten Benutzer zurück:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

## <a name="getting-local-time-from-a-computer"></a>Abrufen der lokalen Uhrzeit eines Computers

Sie können die aktuelle lokale Zeit auf einem bestimmten Computer mit der Klasse **WMI-Win32_LocalTime** abrufen.

```powershell
Get-CimInstance -ClassName Win32_LocalTime -ComputerName .

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2017
PSComputerName : .
```

## <a name="displaying-service-status"></a>Anzeigen des Dienststatus

Zum Anzeigen des Status aller Dienste auf einem bestimmten Computer können Sie das Cmdlet `Get-Service` verwenden.
Für Remotesysteme können Sie die Klasse **WMI-Win32_Service** verwenden.
Wenn Sie die Ergebnisse außerdem mit `Select-Object` nach **Status**, **Name** und **DisplayName** filtern, ist das Ausgabeformat fast identisch mit dem von `Get-Service`:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Um für die wenigen Dienste mit extrem langen Namen die Anzeige der vollständigen Namen zu ermöglichen, können Sie `Format-Table` mit den Parametern **AutoSize** und **Wrap** verwenden. Dadurch wird die Spaltenbreite optimiert und ermöglicht, dass lange Namen umgebrochen und nicht abgeschnitten werden:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
