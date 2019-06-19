---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Abrufen von WMI-Objekten (Get-WmiObject)
ms.openlocfilehash: 93276ce12135342af2d6f238976e65e5d8bdde7a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030218"
---
# <a name="getting-wmi-objects-get-wmiobject"></a>Abrufen von WMI-Objekten (Get-WmiObject)

## <a name="getting-wmi-objects-get-wmiobject"></a>Abrufen von WMI-Objekten (Get-WmiObject)

Windows-Verwaltungsinstrumentation (Windows Management Instrumentation, WMI) ist eine Kerntechnologie für die Windows-Systemadministration, denn sie macht eine Vielzahl von Informationen auf einheitliche Weise verfügbar. Weil WMI so viel möglich macht, ist das Windows PowerShell-Cmdlet **Get-WmiObject** eines der nützlichsten Cmdlets für die tatsächliche Arbeit. Es wird zunächst erläutert, wie mit „Get-WmiObject WMI“ auf WMI-Objekte zugegriffen werden kann, und dann wird erläutert, wie WMI-Objekte zum Ausführen bestimmter Aufgaben verwendet werden können.

### <a name="listing-wmi-classes"></a>Auflisten von WMI-Klassen

Das erste Problem, das die meisten WMI-Benutzer haben, besteht im Herausfinden, was mit WMI erledigt werden kann. WMI-Klassen beschreiben die Ressourcen, die verwaltet werden können. Es gibt Hunderte von WMI-Klassen, von denen einige Dutzende von Eigenschaften enthalten.

**Get-WmiObject** löst dieses Problem, indem es WMI auswertbar macht. Sie können eine Liste der WMI-Klassen, die auf dem lokalen Computer verfügbar sind, durch folgende Eingabe abrufen:

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

Sie können die gleichen Informationen von einem Remotecomputer abrufen, indem Sie den „ComputerName“-Parameter verwenden und für diesen einen Computernamen oder eine IP-Adresse angeben:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

Die Klassenauflistungen, die von Remotecomputern zurückgegeben werden, können je nach Betriebssystem, unter dem der jeweilige Computer ausgeführt wird, und den bestimmten WMI-Erweiterungen, die durch installierte Programme hinzugefügt wurden, unterschiedlich sein.

> [!NOTE]
> Wird mit „Get-WmiObject“ eine Verbindung mit einem Remotecomputer hergestellt, muss WMI auf dem Remotecomputer ausgeführt werden, und das von Ihnen verwendete Konto muss, in der Standardkonfiguration, zur Gruppe der lokalen Administratoren auf dem Remotecomputer gehören. Es ist nicht erforderlich, dass Windows PowerShell auf dem Remotesystem installiert ist. Dadurch können Sie Betriebssysteme verwalten, in denen die Windows PowerShell nicht ausgeführt wird, für die aber WMI verfügbar ist.

Den Computernamen können Sie auch einfügen, wenn Sie eine Verbindung mit dem lokalen System herstellen. Für den Computernamen können Sie den Namen des lokalen Computers, dessen IP-Adresse (oder die Loopbackadresse „127.0.0.1“) oder den WMI-Stil „.“ verwenden. Wenn Sie Windows PowerShell auf einem Computer namens „Admin01“ mit der IP-Adresse „192.168.1.90“ ausführen, geben die folgenden Befehle die WMI-Klassenauflistung für diesen Computer zurück:

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

Für „Get-WmiObject“ wird standardmäßig der Namespace „root/cimv2“ verwendet. Wenn Sie einen anderen WMI-Namespace nutzen möchten, verwenden Sie den **Namespace**-Parameter, und geben Sie den entsprechenden Namespacepfad an:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a>Anzeigen von WMI-Klassendetails

Wenn Sie den Namen einer WMI-Klasse bereits kennen, können Sie ihn verwenden, um Informationen sofort abzurufen. Eine der WMI-Klassen, die häufig verwendet werden, um Informationen zu einem Computer abzurufen, ist z.B. **Win32_OperatingSystem**.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

Obwohl hier alle Parameter gezeigt sind, kann der Befehl auf kompaktere Weise formuliert werden. Der **ComputerName**-Parameter ist beim Verbinden mit dem lokalen System nicht erforderlich. Er ist aufgeführt, um den allgemeinsten Fall zu veranschaulichen und Sie an den Parameter zu erinnern. Als **Namespace** wird standardmäßig „root/cimv2“ verwendet, sodass auch dieser Parameter fehlen kann. Grundsätzlich gilt, dass es bei den meisten Cmdlets zulässig ist, die Namen von allgemeinen Parametern wegzulassen. Wird bei „Get-WmiObject“ kein Name für den ersten Parameter angegeben, geht Windows PowerShell davon aus, dass es sich um den **Class**-Parameter handelt. Dies bedeutet, dass der letzte Befehl mit folgender Eingabe ausgeführt werden kann:

```powershell
Get-WmiObject Win32_OperatingSystem
```

Die **Win32_OperatingSystem**-Klasse hat viel mehr Eigenschaften als hier aufgeführt sind. Sie können „Get-Member“ verwenden, um alle Eigenschaften anzuzeigen. Die Eigenschaften einer WMI-Klasse sind automatisch wie andere Objekteigenschaften verfügbar:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Get-Member -MemberType Property

   TypeName: System.Management.ManagementObject#root\cimv2\Win32_OperatingSyste
m

Name                                      MemberType Definition
----                                      ---------- ----------
__CLASS                                   Property   System.String __CLASS {...
...
BootDevice                                Property   System.String BootDevic...
BuildNumber                               Property   System.String BuildNumb...
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Anzeigen von Nicht-Standardeigenschaften mit „Format“-Cmdlets

Wenn Sie Informationen anzeigen möchten, die in der **Win32_OperatingSystem**-Klasse enthalten sind, aber nicht standardmäßig angezeigt werden, verwenden Sie die **Format**-Cmdlets. Wenn Sie beispielsweise die verfügbaren Arbeitsspeicherdaten anzeigen möchten, geben Sie Folgendes ein:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> Platzhalter können für Eigenschaftsnamen in **Format-Table** verwendet werden. Das letzte Pipelineelement kann daher auf `Format-Table -Property Total,Free` reduziert werden.

Die Arbeitsspeicherdaten lassen sich möglicherweise besser lesen, wenn Sie sie durch die folgende Eingabe als Liste formatieren:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
