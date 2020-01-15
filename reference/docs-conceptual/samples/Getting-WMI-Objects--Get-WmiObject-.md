---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Abrufen von WMI-Objekten (Get-WmiObject)
ms.openlocfilehash: 23fd8cf596a8be7e36651ac3f9c79ca97240e647
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737218"
---
# <a name="getting-wmi-objects-get-wmiobject"></a>Abrufen von WMI-Objekten (Get-WmiObject)

## <a name="getting-wmi-objects-get-wmiobject"></a>Abrufen von WMI-Objekten (Get-WmiObject)

Windows-Verwaltungsinstrumentation (Windows Management Instrumentation, WMI) ist eine Kerntechnologie für die Windows-Systemadministration, denn sie macht eine Vielzahl von Informationen auf einheitliche Weise verfügbar. Dank der zahlreichen Möglichkeiten von WMI ist das PowerShell-Cmdlet `Get-CimInstance` zum Zugriff auf WMI-Objekte eines der nützlichsten Cmdlets für die eigentliche Arbeit. Es wird zunächst erläutert, wie mit CIM-Cmdlets auf WMI-Objekte zugegriffen werden kann, und dann wird erläutert, wie WMI-Objekte zum Ausführen bestimmter Aufgaben verwendet werden können.

### <a name="listing-wmi-classes"></a>Auflisten von WMI-Klassen

Das erste Problem, das die meisten WMI-Benutzer haben, besteht im Herausfinden, was mit WMI erledigt werden kann. WMI-Klassen beschreiben die Ressourcen, die verwaltet werden können. Es gibt Hunderte von WMI-Klassen, von denen einige Dutzende von Eigenschaften enthalten.

`Get-CimClass` löst dieses Problem, indem es WMI auswertbar macht. Sie können eine Liste der WMI-Klassen, die auf dem lokalen Computer verfügbar sind, durch folgende Eingabe abrufen:

```powershell
Get-CimClass -Namespace root/CIMV2 |
  Where-Object CimClassName -like Win32* |
    Select-Object CimClassName
```

```Output
CimClassName
------------
Win32_DeviceChangeEvent
Win32_SystemConfigurationChangeEvent
Win32_VolumeChangeEvent
Win32_SystemTrace
Win32_ProcessTrace
Win32_ProcessStartTrace
Win32_ProcessStopTrace
Win32_ThreadTrace
Win32_ThreadStartTrace
Win32_ThreadStopTrace
...
```

Sie können die gleichen Informationen von einem Remotecomputer abrufen, indem Sie den **ComputerName**-Parameter verwenden und für diesen einen Computernamen oder eine IP-Adresse angeben:

```powershell
Get-CimClass -Namespace root/CIMV2 -ComputerName 192.168.1.29
```

Die Klassenauflistungen, die von Remotecomputern zurückgegeben werden, können je nach Betriebssystem, unter dem der jeweilige Computer ausgeführt wird, und den bestimmten WMI-Erweiterungen, die durch installierte Programme hinzugefügt wurden, unterschiedlich sein.

> [!NOTE]
> Bei Verwendung von CIM-Cmdlets zum Herstellen einer Verbindung mit einem Remotecomputer muss WMI auf dem Remotecomputer ausgeführt werden, und das von Ihnen verwendete Konto muss der Gruppe der lokalen Administratoren auf dem Remotecomputer angehören.
> Es ist nicht erforderlich, dass PowerShell auf dem Remotesystem installiert ist. Auf diese Weise können Sie Betriebssysteme verwalten, in denen PowerShell nicht ausgeführt wird, für die aber WMI verfügbar ist.

### <a name="displaying-wmi-class-details"></a>Anzeigen von WMI-Klassendetails

Wenn Sie den Namen einer WMI-Klasse bereits kennen, können Sie ihn verwenden, um Informationen sofort abzurufen. Eine der WMI-Klassen, die häufig verwendet werden, um Informationen zu einem Computer abzurufen, ist z.B. **Win32_OperatingSystem**.

```powershell
Get-CimInstance -Class Win32_OperatingSystem
```

```Output
SystemDirectory     Organization BuildNumber RegisteredUser SerialNumber            Version
---------------     ------------ ----------- -------------- ------------            -------
C:\WINDOWS\system32 Microsoft    18362       USER1          00330-80000-00000-AA175 10.0.18362
```

Obwohl hier alle Parameter gezeigt sind, kann der Befehl auf kompaktere Weise formuliert werden.
Der **ComputerName**-Parameter ist beim Verbinden mit dem lokalen System nicht erforderlich. Er ist aufgeführt, um den allgemeinsten Fall zu veranschaulichen und Sie an den Parameter zu erinnern. Als **Namespace** wird standardmäßig `root/CIMV2` verwendet, sodass auch dieser Parameter fehlen kann. Grundsätzlich gilt, dass es bei den meisten Cmdlets zulässig ist, die Namen von allgemeinen Parametern wegzulassen. Wird bei `Get-CimInstance` kein Name für den ersten Parameter angegeben, geht PowerShell davon aus, dass es sich um den **Class**-Parameter handelt. Dies bedeutet, dass der letzte Befehl mit folgender Eingabe ausgeführt werden kann:

```powershell
Get-WmiObject Win32_OperatingSystem
```

Die **Win32_OperatingSystem**-Klasse hat viel mehr Eigenschaften als hier aufgeführt sind. Sie können „Get-Member“ verwenden, um alle Eigenschaften anzuzeigen. Die Eigenschaften einer WMI-Klasse sind automatisch wie andere Objekteigenschaften verfügbar:

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Get-Member -MemberType Property
```

```Output
   TypeName: Microsoft.Management.Infrastructure.CimInstance#root/cimv2/Win32_OperatingSystem
Name                                      MemberType Definition
----                                      ---------- ----------
BootDevice                                Property   string BootDevice {get;}
BuildNumber                               Property   string BuildNumber {get;}
BuildType                                 Property   string BuildType {get;}
Caption                                   Property   string Caption {get;}
CodeSet                                   Property   string CodeSet {get;}
CountryCode                               Property   string CountryCode {get;}
CreationClassName                         Property   string CreationClassName {get;}
CSCreationClassName                       Property   string CSCreationClassName {get;}
CSDVersion                                Property   string CSDVersion {get;}
CSName                                    Property   string CSName {get;}
CurrentTimeZone                           Property   short CurrentTimeZone {get;}
DataExecutionPrevention_32BitApplications Property   bool DataExecutionPrevention_32BitApplications {get;}
DataExecutionPrevention_Available         Property   bool DataExecutionPrevention_Available {get;}
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Anzeigen von Nicht-Standardeigenschaften mit „Format“-Cmdlets

Wenn Sie Informationen anzeigen möchten, die in der **Win32_OperatingSystem**-Klasse enthalten sind, aber nicht standardmäßig angezeigt werden, verwenden Sie die **Format**-Cmdlets. Wenn Sie beispielsweise die verfügbaren Arbeitsspeicherdaten anzeigen möchten, geben Sie Folgendes ein:

```powershell
Get-CimInstance -Class Win32_OperatingSystem |
  Format-Table -Property TotalVirtualMemorySize, TotalVisibleMemorySize,
    FreePhysicalMemory, FreeVirtualMemory, FreeSpaceInPagingFiles
```

```Output
TotalVirtualMemorySize TotalVisibleMemorySize FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------------- ------------------ ----------------- ----------------------
              33449088               16671872            6451868          18424496               16285032
```

> [!NOTE]
> Platzhalter können für Eigenschaftsnamen in `Format-Table` verwendet werden. Das letzte Pipelineelement kann daher auf `Format-Table -Property Total*Memory*, Free*` reduziert werden.

Die Arbeitsspeicherdaten lassen sich möglicherweise besser lesen, wenn Sie sie durch die folgende Eingabe als Liste formatieren:

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Format-List Total*Memory*, Free*
```

```Output
TotalVirtualMemorySize : 33449088
TotalVisibleMemorySize : 16671872
FreePhysicalMemory     : 6524456
FreeSpaceInPagingFiles : 16285808
FreeVirtualMemory      : 18393668
Name                   : Microsoft Windows 10 Pro|C:\WINDOWS|\Device\Harddisk0\Partition2
```
