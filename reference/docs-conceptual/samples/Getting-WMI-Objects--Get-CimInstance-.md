---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Abrufen von WMI-Objekten (Get CimInstance)
ms.openlocfilehash: 4ff47844fd367a49f554c7c05c491bdddf28eabc
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2020
ms.locfileid: "77002650"
---
# <a name="getting-wmi-objects-get-ciminstance"></a><span data-ttu-id="b6a54-103">Abrufen von WMI-Objekten (Get-CimInstance)</span><span class="sxs-lookup"><span data-stu-id="b6a54-103">Getting WMI Objects (Get-CimInstance)</span></span>

## <a name="getting-wmi-objects-get-ciminstance"></a><span data-ttu-id="b6a54-104">Abrufen von WMI-Objekten (Get-CimInstance)</span><span class="sxs-lookup"><span data-stu-id="b6a54-104">Getting WMI Objects (Get-CimInstance)</span></span>

<span data-ttu-id="b6a54-105">Windows-Verwaltungsinstrumentation (Windows Management Instrumentation, WMI) ist eine Kerntechnologie für die Windows-Systemadministration, denn sie macht eine Vielzahl von Informationen auf einheitliche Weise verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b6a54-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="b6a54-106">Dank der zahlreichen Möglichkeiten von WMI ist das PowerShell-Cmdlet `Get-CimInstance` zum Zugriff auf WMI-Objekte eines der nützlichsten Cmdlets für die eigentliche Arbeit.</span><span class="sxs-lookup"><span data-stu-id="b6a54-106">Because of how much WMI makes possible, the PowerShell cmdlet for accessing WMI objects, `Get-CimInstance`, is one of the most useful for doing real work.</span></span> <span data-ttu-id="b6a54-107">Es wird zunächst erläutert, wie mit CIM-Cmdlets auf WMI-Objekte zugegriffen werden kann, und dann wird erläutert, wie WMI-Objekte zum Ausführen bestimmter Aufgaben verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="b6a54-107">We are going to discuss how to use the CimCmdlets to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="b6a54-108">Auflisten von WMI-Klassen</span><span class="sxs-lookup"><span data-stu-id="b6a54-108">Listing WMI Classes</span></span>

<span data-ttu-id="b6a54-109">Das erste Problem, das die meisten WMI-Benutzer haben, besteht im Herausfinden, was mit WMI erledigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="b6a54-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="b6a54-110">WMI-Klassen beschreiben die Ressourcen, die verwaltet werden können.</span><span class="sxs-lookup"><span data-stu-id="b6a54-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="b6a54-111">Es gibt Hunderte von WMI-Klassen, von denen einige Dutzende von Eigenschaften enthalten.</span><span class="sxs-lookup"><span data-stu-id="b6a54-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="b6a54-112">`Get-CimClass` löst dieses Problem, indem es WMI auswertbar macht.</span><span class="sxs-lookup"><span data-stu-id="b6a54-112">`Get-CimClass` addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="b6a54-113">Sie können eine Liste der WMI-Klassen, die auf dem lokalen Computer verfügbar sind, durch folgende Eingabe abrufen:</span><span class="sxs-lookup"><span data-stu-id="b6a54-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

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

<span data-ttu-id="b6a54-114">Sie können die gleichen Informationen von einem Remotecomputer abrufen, indem Sie den **ComputerName**-Parameter verwenden und für diesen einen Computernamen oder eine IP-Adresse angeben:</span><span class="sxs-lookup"><span data-stu-id="b6a54-114">You can retrieve the same information from a remote computer by using the **ComputerName** parameter, specifying a computer name or IP address:</span></span>

```powershell
Get-CimClass -Namespace root/CIMV2 -ComputerName 192.168.1.29
```

<span data-ttu-id="b6a54-115">Die Klassenauflistungen, die von Remotecomputern zurückgegeben werden, können je nach Betriebssystem, unter dem der jeweilige Computer ausgeführt wird, und den bestimmten WMI-Erweiterungen, die durch installierte Programme hinzugefügt wurden, unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="b6a54-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="b6a54-116">Bei Verwendung von CIM-Cmdlets zum Herstellen einer Verbindung mit einem Remotecomputer muss WMI auf dem Remotecomputer ausgeführt werden, und das von Ihnen verwendete Konto muss der Gruppe der lokalen Administratoren auf dem Remotecomputer angehören.</span><span class="sxs-lookup"><span data-stu-id="b6a54-116">When using CIM cmdlets to connect to a remote computer, the remote computer must be running WMI and the account you are using must be in the local administrators group on the remote computer.</span></span>
> <span data-ttu-id="b6a54-117">Es ist nicht erforderlich, dass PowerShell auf dem Remotesystem installiert ist.</span><span class="sxs-lookup"><span data-stu-id="b6a54-117">The remote system does not need to have PowerShell installed.</span></span> <span data-ttu-id="b6a54-118">Auf diese Weise können Sie Betriebssysteme verwalten, in denen PowerShell nicht ausgeführt wird, für die aber WMI verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="b6a54-118">This allows you to administer operating systems that are not running PowerShell, but do have WMI available.</span></span>

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="b6a54-119">Anzeigen von WMI-Klassendetails</span><span class="sxs-lookup"><span data-stu-id="b6a54-119">Displaying WMI Class Details</span></span>

<span data-ttu-id="b6a54-120">Wenn Sie den Namen einer WMI-Klasse bereits kennen, können Sie ihn verwenden, um Informationen sofort abzurufen.</span><span class="sxs-lookup"><span data-stu-id="b6a54-120">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="b6a54-121">Eine der WMI-Klassen, die häufig verwendet werden, um Informationen zu einem Computer abzurufen, ist z.B. **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="b6a54-121">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem
```

```Output
SystemDirectory     Organization BuildNumber RegisteredUser SerialNumber            Version
---------------     ------------ ----------- -------------- ------------            -------
C:\WINDOWS\system32 Microsoft    18362       USER1          00330-80000-00000-AA175 10.0.18362
```

<span data-ttu-id="b6a54-122">Obwohl hier alle Parameter gezeigt sind, kann der Befehl auf kompaktere Weise formuliert werden.</span><span class="sxs-lookup"><span data-stu-id="b6a54-122">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span>
<span data-ttu-id="b6a54-123">Der **ComputerName**-Parameter ist beim Verbinden mit dem lokalen System nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b6a54-123">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="b6a54-124">Er ist aufgeführt, um den allgemeinsten Fall zu veranschaulichen und Sie an den Parameter zu erinnern.</span><span class="sxs-lookup"><span data-stu-id="b6a54-124">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="b6a54-125">Als **Namespace** wird standardmäßig `root/CIMV2` verwendet, sodass auch dieser Parameter fehlen kann.</span><span class="sxs-lookup"><span data-stu-id="b6a54-125">The **Namespace** defaults to `root/CIMV2`, and can be omitted as well.</span></span> <span data-ttu-id="b6a54-126">Grundsätzlich gilt, dass es bei den meisten Cmdlets zulässig ist, die Namen von allgemeinen Parametern wegzulassen.</span><span class="sxs-lookup"><span data-stu-id="b6a54-126">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="b6a54-127">Wird bei `Get-CimInstance` kein Name für den ersten Parameter angegeben, geht PowerShell davon aus, dass es sich um den **Class**-Parameter handelt.</span><span class="sxs-lookup"><span data-stu-id="b6a54-127">With `Get-CimInstance`, if no name is specified for the first parameter, PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="b6a54-128">Dies bedeutet, dass der letzte Befehl mit folgender Eingabe ausgeführt werden kann:</span><span class="sxs-lookup"><span data-stu-id="b6a54-128">This means the last command could have been issued by typing:</span></span>

```powershell
Get-CimInstance Win32_OperatingSystem
```

<span data-ttu-id="b6a54-129">Die **Win32_OperatingSystem**-Klasse hat viel mehr Eigenschaften als hier aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="b6a54-129">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="b6a54-130">Sie können „Get-Member“ verwenden, um alle Eigenschaften anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b6a54-130">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="b6a54-131">Die Eigenschaften einer WMI-Klasse sind automatisch wie andere Objekteigenschaften verfügbar:</span><span class="sxs-lookup"><span data-stu-id="b6a54-131">The properties of a WMI class are automatically available like other object properties:</span></span>

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="b6a54-132">Anzeigen von Nicht-Standardeigenschaften mit „Format“-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="b6a54-132">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="b6a54-133">Wenn Sie Informationen anzeigen möchten, die in der **Win32_OperatingSystem**-Klasse enthalten sind, aber nicht standardmäßig angezeigt werden, verwenden Sie die **Format**-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b6a54-133">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="b6a54-134">Wenn Sie beispielsweise die verfügbaren Arbeitsspeicherdaten anzeigen möchten, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="b6a54-134">For example, if you want to display available memory data, type:</span></span>

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
> <span data-ttu-id="b6a54-135">Platzhalter können für Eigenschaftsnamen in `Format-Table` verwendet werden. Das letzte Pipelineelement kann daher auf `Format-Table -Property Total*Memory*, Free*` reduziert werden.</span><span class="sxs-lookup"><span data-stu-id="b6a54-135">Wildcards work with property names in `Format-Table`, so the final pipeline element can be reduced to `Format-Table -Property Total*Memory*, Free*`</span></span>

<span data-ttu-id="b6a54-136">Die Arbeitsspeicherdaten lassen sich möglicherweise besser lesen, wenn Sie sie durch die folgende Eingabe als Liste formatieren:</span><span class="sxs-lookup"><span data-stu-id="b6a54-136">The memory data might be more readable if you format it as a list by typing:</span></span>

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
