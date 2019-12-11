---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Abrufen von WMI-Objekten (Get-WmiObject)
ms.openlocfilehash: 93276ce12135342af2d6f238976e65e5d8bdde7a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030218"
---
# <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="a1d3b-103">Abrufen von WMI-Objekten (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="a1d3b-103">Getting WMI Objects (Get-WmiObject)</span></span>

## <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="a1d3b-104">Abrufen von WMI-Objekten (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="a1d3b-104">Getting WMI Objects (Get-WmiObject)</span></span>

<span data-ttu-id="a1d3b-105">Windows-Verwaltungsinstrumentation (Windows Management Instrumentation, WMI) ist eine Kerntechnologie für die Windows-Systemadministration, denn sie macht eine Vielzahl von Informationen auf einheitliche Weise verfügbar.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="a1d3b-106">Weil WMI so viel möglich macht, ist das Windows PowerShell-Cmdlet **Get-WmiObject** eines der nützlichsten Cmdlets für die tatsächliche Arbeit.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-106">Because of how much WMI makes possible, the Windows PowerShell cmdlet for accessing WMI objects, **Get-WmiObject**, is one of the most useful for doing real work.</span></span> <span data-ttu-id="a1d3b-107">Es wird zunächst erläutert, wie mit „Get-WmiObject WMI“ auf WMI-Objekte zugegriffen werden kann, und dann wird erläutert, wie WMI-Objekte zum Ausführen bestimmter Aufgaben verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-107">We are going to discuss how to use Get-WmiObject to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="a1d3b-108">Auflisten von WMI-Klassen</span><span class="sxs-lookup"><span data-stu-id="a1d3b-108">Listing WMI Classes</span></span>

<span data-ttu-id="a1d3b-109">Das erste Problem, das die meisten WMI-Benutzer haben, besteht im Herausfinden, was mit WMI erledigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="a1d3b-110">WMI-Klassen beschreiben die Ressourcen, die verwaltet werden können.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="a1d3b-111">Es gibt Hunderte von WMI-Klassen, von denen einige Dutzende von Eigenschaften enthalten.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="a1d3b-112">**Get-WmiObject** löst dieses Problem, indem es WMI auswertbar macht.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-112">**Get-WmiObject** addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="a1d3b-113">Sie können eine Liste der WMI-Klassen, die auf dem lokalen Computer verfügbar sind, durch folgende Eingabe abrufen:</span><span class="sxs-lookup"><span data-stu-id="a1d3b-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

<span data-ttu-id="a1d3b-114">Sie können die gleichen Informationen von einem Remotecomputer abrufen, indem Sie den „ComputerName“-Parameter verwenden und für diesen einen Computernamen oder eine IP-Adresse angeben:</span><span class="sxs-lookup"><span data-stu-id="a1d3b-114">You can retrieve the same information from a remote computer by using the ComputerName parameter, specifying a computer name or IP address:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

<span data-ttu-id="a1d3b-115">Die Klassenauflistungen, die von Remotecomputern zurückgegeben werden, können je nach Betriebssystem, unter dem der jeweilige Computer ausgeführt wird, und den bestimmten WMI-Erweiterungen, die durch installierte Programme hinzugefügt wurden, unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="a1d3b-116">Wird mit „Get-WmiObject“ eine Verbindung mit einem Remotecomputer hergestellt, muss WMI auf dem Remotecomputer ausgeführt werden, und das von Ihnen verwendete Konto muss, in der Standardkonfiguration, zur Gruppe der lokalen Administratoren auf dem Remotecomputer gehören.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-116">When using Get-WmiObject to connect to a remote computer, the remote computer must be running WMI and, under the default configuration, the account you are using must be in the local administrators group on the remote computer.</span></span> <span data-ttu-id="a1d3b-117">Es ist nicht erforderlich, dass Windows PowerShell auf dem Remotesystem installiert ist.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-117">The remote system does not need to have Windows PowerShell installed.</span></span> <span data-ttu-id="a1d3b-118">Dadurch können Sie Betriebssysteme verwalten, in denen die Windows PowerShell nicht ausgeführt wird, für die aber WMI verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-118">This allows you to administer operating systems that are not running Windows PowerShell, but do have WMI available.</span></span>

<span data-ttu-id="a1d3b-119">Den Computernamen können Sie auch einfügen, wenn Sie eine Verbindung mit dem lokalen System herstellen.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-119">You can even include the ComputerName when connecting to the local system.</span></span> <span data-ttu-id="a1d3b-120">Für den Computernamen können Sie den Namen des lokalen Computers, dessen IP-Adresse (oder die Loopbackadresse „127.0.0.1“) oder den WMI-Stil „.“ verwenden.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-120">You can use the local computer's name, its IP address (or the loopback address 127.0.0.1), or the WMI-style '.' as the computer name.</span></span> <span data-ttu-id="a1d3b-121">Wenn Sie Windows PowerShell auf einem Computer namens „Admin01“ mit der IP-Adresse „192.168.1.90“ ausführen, geben die folgenden Befehle die WMI-Klassenauflistung für diesen Computer zurück:</span><span class="sxs-lookup"><span data-stu-id="a1d3b-121">If you are running Windows PowerShell on a computer named Admin01 with IP address 192.168.1.90, the following commands will all return the WMI class listing for that computer:</span></span>

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

<span data-ttu-id="a1d3b-122">Für „Get-WmiObject“ wird standardmäßig der Namespace „root/cimv2“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-122">Get-WmiObject uses the root/cimv2 namespace by default.</span></span> <span data-ttu-id="a1d3b-123">Wenn Sie einen anderen WMI-Namespace nutzen möchten, verwenden Sie den **Namespace**-Parameter, und geben Sie den entsprechenden Namespacepfad an:</span><span class="sxs-lookup"><span data-stu-id="a1d3b-123">If you want to specify another WMI namespace, use the **Namespace** parameter and specify the corresponding namespace path:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="a1d3b-124">Anzeigen von WMI-Klassendetails</span><span class="sxs-lookup"><span data-stu-id="a1d3b-124">Displaying WMI Class Details</span></span>

<span data-ttu-id="a1d3b-125">Wenn Sie den Namen einer WMI-Klasse bereits kennen, können Sie ihn verwenden, um Informationen sofort abzurufen.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-125">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="a1d3b-126">Eine der WMI-Klassen, die häufig verwendet werden, um Informationen zu einem Computer abzurufen, ist z.B. **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-126">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

<span data-ttu-id="a1d3b-127">Obwohl hier alle Parameter gezeigt sind, kann der Befehl auf kompaktere Weise formuliert werden.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-127">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span> <span data-ttu-id="a1d3b-128">Der **ComputerName**-Parameter ist beim Verbinden mit dem lokalen System nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-128">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="a1d3b-129">Er ist aufgeführt, um den allgemeinsten Fall zu veranschaulichen und Sie an den Parameter zu erinnern.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-129">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="a1d3b-130">Als **Namespace** wird standardmäßig „root/cimv2“ verwendet, sodass auch dieser Parameter fehlen kann.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-130">The **Namespace** defaults to root/cimv2, and can be omitted as well.</span></span> <span data-ttu-id="a1d3b-131">Grundsätzlich gilt, dass es bei den meisten Cmdlets zulässig ist, die Namen von allgemeinen Parametern wegzulassen.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-131">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="a1d3b-132">Wird bei „Get-WmiObject“ kein Name für den ersten Parameter angegeben, geht Windows PowerShell davon aus, dass es sich um den **Class**-Parameter handelt.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-132">With Get-WmiObject, if no name is specified for the first parameter, Windows PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="a1d3b-133">Dies bedeutet, dass der letzte Befehl mit folgender Eingabe ausgeführt werden kann:</span><span class="sxs-lookup"><span data-stu-id="a1d3b-133">This means the last command could have been issued by typing:</span></span>

```powershell
Get-WmiObject Win32_OperatingSystem
```

<span data-ttu-id="a1d3b-134">Die **Win32_OperatingSystem**-Klasse hat viel mehr Eigenschaften als hier aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-134">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="a1d3b-135">Sie können „Get-Member“ verwenden, um alle Eigenschaften anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-135">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="a1d3b-136">Die Eigenschaften einer WMI-Klasse sind automatisch wie andere Objekteigenschaften verfügbar:</span><span class="sxs-lookup"><span data-stu-id="a1d3b-136">The properties of a WMI class are automatically available like other object properties:</span></span>

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="a1d3b-137">Anzeigen von Nicht-Standardeigenschaften mit „Format“-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="a1d3b-137">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="a1d3b-138">Wenn Sie Informationen anzeigen möchten, die in der **Win32_OperatingSystem**-Klasse enthalten sind, aber nicht standardmäßig angezeigt werden, verwenden Sie die **Format**-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-138">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="a1d3b-139">Wenn Sie beispielsweise die verfügbaren Arbeitsspeicherdaten anzeigen möchten, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="a1d3b-139">For example, if you want to display available memory data, type:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> <span data-ttu-id="a1d3b-140">Platzhalter können für Eigenschaftsnamen in **Format-Table** verwendet werden. Das letzte Pipelineelement kann daher auf `Format-Table -Property Total,Free` reduziert werden.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-140">Wildcards work with property names in **Format-Table**, so the final pipeline element can be reduced to `Format-Table -Property Total,Free`</span></span>

<span data-ttu-id="a1d3b-141">Die Arbeitsspeicherdaten lassen sich möglicherweise besser lesen, wenn Sie sie durch die folgende Eingabe als Liste formatieren:</span><span class="sxs-lookup"><span data-stu-id="a1d3b-141">The memory data might be more readable if you format it as a list by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
