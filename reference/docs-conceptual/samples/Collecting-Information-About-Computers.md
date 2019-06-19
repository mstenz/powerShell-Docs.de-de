---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Erfassen von Informationen über Computer
ms.openlocfilehash: 5dc8fcc5f12fdf9e3fc8151d3e50b8b660262c62
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030840"
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="c6bc5-103">Erfassen von Informationen über Computer</span><span class="sxs-lookup"><span data-stu-id="c6bc5-103">Collecting Information About Computers</span></span>

<span data-ttu-id="c6bc5-104">Cmdlets des Moduls **CimCmdlets** sind die wichtigsten Cmdlets für einfache Tasks zur Systemverwaltung.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-104">Cmdlets from **CimCmdlets** module are the most important cmdlets for general system management tasks.</span></span>
<span data-ttu-id="c6bc5-105">Alle kritischen Subsystemeinstellungen werden über WMI verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-105">All critical subsystem settings are exposed through WMI.</span></span>
<span data-ttu-id="c6bc5-106">Darüber hinaus behandelt WMI Daten als Objekte, die zu Sammlungen eines oder mehrerer Elemente gehören.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span>
<span data-ttu-id="c6bc5-107">Da Windows PowerShell ebenfalls mit Objekten arbeitet und über eine Pipeline verfügt, mit der Sie einzelne oder mehrere Objekte auf die gleiche Weise behandeln können, ermöglicht der generische WMI-Zugriff Ihnen, einige erweiterte Aufgaben mit sehr geringem Aufwand auszuführen.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

<span data-ttu-id="c6bc5-108">In den folgenden Beispielen wird gezeigt, wie Sie mit `Get-CimInstance` spezifische Informationen für einen beliebigen Computer sammeln.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-108">The following examples demonstrate how to collect specific information by using `Get-CimInstance` against an arbitrary computer.</span></span>
<span data-ttu-id="c6bc5-109">Sie geben den Parameter **ComputerName** mit dem Punkt ( **.** ) als Wert an, der den lokalen Computer darstellt.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-109">We specify the **ComputerName** parameter with the dot value (**.**), which represents the local computer.</span></span>
<span data-ttu-id="c6bc5-110">Sie können einen Namen oder eine IP-Adresse eines beliebigen Computers angeben, den Sie über WMI erreichen können.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-110">You can specify a name or IP address associated with any computer you can reach through WMI.</span></span>
<span data-ttu-id="c6bc5-111">Zum Abrufen von Informationen über den lokalen Computer können Sie den Parameter **ComputerName** weglassen.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-111">To retrieve information about the local computer, you could omit the **ComputerName** parameter.</span></span>

## <a name="listing-desktop-settings"></a><span data-ttu-id="c6bc5-112">Auflisten von Desktopeinstellungen</span><span class="sxs-lookup"><span data-stu-id="c6bc5-112">Listing Desktop Settings</span></span>

<span data-ttu-id="c6bc5-113">Wir beginnen mit einem Befehl, der Informationen über die Desktops auf dem lokalen Computer erfasst.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-113">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

<span data-ttu-id="c6bc5-114">Dadurch werden Informationen über alle Desktops zurückgegeben, ganz gleich, ob sie verwendet werden oder nicht.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-114">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="c6bc5-115">Einige WMI-Klassen geben sehr detaillierte Informationen zurück, die häufig Metadaten über die WMI-Klasse enthalten.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-115">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span>
<span data-ttu-id="c6bc5-116">Da die meisten dieser Metadateneigenschaften über Namen verfügen, die mit **Cim** beginnen, können Sie die Eigenschaften mit `Select-Object` filtern.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-116">Because most of these metadata properties have names that begin with **Cim**, you can filter the properties using `Select-Object`.</span></span>
<span data-ttu-id="c6bc5-117">Geben Sie dem Parameter **-ExcludeProperty** mit „Cim\*“ als Wert an.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-117">Specify the **-ExcludeProperty** parameter with "Cim\*" as the value.</span></span>
<span data-ttu-id="c6bc5-118">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="c6bc5-118">For example:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="c6bc5-119">Um die Metadaten zu filtern, verwenden Sie einen Pipelineoperator (|), um die Ergebnisse des Befehls `Get-CimInstance` an `Select-Object -ExcludeProperty "CIM*"` zu senden.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-119">To filter out the metadata, use a pipeline operator (|) to send the results of the `Get-CimInstance` command to `Select-Object -ExcludeProperty "CIM*"`.</span></span>

## <a name="listing-bios-information"></a><span data-ttu-id="c6bc5-120">Auflisten von BIOS-Informationen</span><span class="sxs-lookup"><span data-stu-id="c6bc5-120">Listing BIOS Information</span></span>

<span data-ttu-id="c6bc5-121">Die WMI-Klasse **Win32_BIOS** gibt kompakte und vollständige Informationen zum System-BIOS auf dem lokalen Computer zurück:</span><span class="sxs-lookup"><span data-stu-id="c6bc5-121">The WMI **Win32_BIOS** class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

## <a name="listing-processor-information"></a><span data-ttu-id="c6bc5-122">Auflisten von Prozessorinformationen</span><span class="sxs-lookup"><span data-stu-id="c6bc5-122">Listing Processor Information</span></span>

<span data-ttu-id="c6bc5-123">Sie können allgemeine Prozessorinformationen mithilfe der WMI-Klasse **Win32_Processor** abrufen. Allerdings möchten Sie die Daten wahrscheinlich filtern:</span><span class="sxs-lookup"><span data-stu-id="c6bc5-123">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="c6bc5-124">Wenn Sie eine Zeichenfolge mit einer allgemeinen Beschreibung der Prozessorfamilie erhalten möchten, lassen Sie die **SystemType**-Eigenschaft zurückgeben:</span><span class="sxs-lookup"><span data-stu-id="c6bc5-124">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="c6bc5-125">Auflisten von Informationen zum Computerhersteller und -modell</span><span class="sxs-lookup"><span data-stu-id="c6bc5-125">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="c6bc5-126">Informationen zum Computermodell sind auch über **Win32_ComputerSystem** verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-126">Computer model information is also available from **Win32_ComputerSystem**.</span></span>
<span data-ttu-id="c6bc5-127">Zum Bereitstellen von OEM-Daten ist keine Filterung der angezeigten Standardausgabe erforderlich:</span><span class="sxs-lookup"><span data-stu-id="c6bc5-127">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

<span data-ttu-id="c6bc5-128">Die Ausgabe von Befehlen, die Informationen direkt von bestimmter Hardware zurückgeben, kann nur so gut sein, wie die vorhandenen Daten.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-128">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span>
<span data-ttu-id="c6bc5-129">Einige Informationen wurden von den Hardwareherstellern nicht ordnungsgemäß konfiguriert und sind daher möglicherweise nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-129">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

## <a name="listing-installed-hotfixes"></a><span data-ttu-id="c6bc5-130">Auflisten installierter Hotfixes</span><span class="sxs-lookup"><span data-stu-id="c6bc5-130">Listing Installed Hotfixes</span></span>

<span data-ttu-id="c6bc5-131">Mit **Win32_QuickFixEngineering** können Sie alle installierten Hotfixes auflisten:</span><span class="sxs-lookup"><span data-stu-id="c6bc5-131">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

<span data-ttu-id="c6bc5-132">Diese Klasse gibt eine Liste von Hotfixes zurück, die wie folgt aussieht:</span><span class="sxs-lookup"><span data-stu-id="c6bc5-132">This class returns a list of hotfixes that looks like this:</span></span>

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

<span data-ttu-id="c6bc5-133">Wenn Sie eine kompaktere Ausgabe erhalten möchten, können Sie bestimmte Eigenschaften ausschließen.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-133">For more succinct output, you may want to exclude some properties.</span></span>
<span data-ttu-id="c6bc5-134">Sie können zwar den `Get-CimInstance`Property **-Parameter von**  verwenden, um nur die **HotFixID** auszuwählen. Dennoch werden weitere Informationen zurückgegeben, da standardmäßig alle Metadaten angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="c6bc5-134">Although you can use the `Get-CimInstance`'s **Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

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

<span data-ttu-id="c6bc5-135">Die zusätzlichen Daten werden zurückgegeben, weil der „Property“-Parameter in `Get-CimInstance` die von WMI-Klasseninstanzen zurückgegebenen Eigenschaften, nicht aber das an die Windows PowerShell zurückgegebene Objekt einschränkt.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-135">The additional data is returned, because the Property parameter in `Get-CimInstance` restricts the properties returned from WMI class instances, not the object returned to Windows PowerShell.</span></span>
<span data-ttu-id="c6bc5-136">Um die Ausgabe zu verringern, verwenden Sie `Select-Object`:</span><span class="sxs-lookup"><span data-stu-id="c6bc5-136">To reduce the output, use `Select-Object`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a><span data-ttu-id="c6bc5-137">Auflisten von Informationen zur Betriebssystemversion</span><span class="sxs-lookup"><span data-stu-id="c6bc5-137">Listing Operating System Version Information</span></span>

<span data-ttu-id="c6bc5-138">Die Klasseneigenschaften **Win32_OperatingSystem** umfassen Informationen zur Version und zum Service Pack.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-138">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span>
<span data-ttu-id="c6bc5-139">Sie können mit **Win32_OperatingSystem** explizit nur diese Eigenschaften auswählen, um eine Zusammenfassung von Versionsinformationen abzurufen:</span><span class="sxs-lookup"><span data-stu-id="c6bc5-139">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="c6bc5-140">Sie können mit dem **Property**-Parameter von `Select-Object` auch Platzhalterzeichen verwenden.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-140">You can also use wildcards with the `Select-Object`'s **Property** parameter.</span></span>
<span data-ttu-id="c6bc5-141">Da alle Eigenschaften, die entweder mit **Build** oder **Service Pack** beginnen, hier wichtig sind, können wir das Beispiel auf das folgende Format kürzen:</span><span class="sxs-lookup"><span data-stu-id="c6bc5-141">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

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

## <a name="listing-local-users-and-owner"></a><span data-ttu-id="c6bc5-142">Auflisten der lokalen Benutzer und des Besitzers</span><span class="sxs-lookup"><span data-stu-id="c6bc5-142">Listing Local Users and Owner</span></span>

<span data-ttu-id="c6bc5-143">Allgemeine lokale Benutzerinformationen (z.B. Anzahl lizenzierter Benutzer, aktuelle Anzahl von Benutzern und Besitzername) können Sie mit einer Auswahl von **Win32_OperatingSystem**-Klasseneigenschaften suchen.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-143">Local general user information — number of licensed users, current number of users, and owner name — can be found with a selection of **Win32_OperatingSystem** class' properties.</span></span>
<span data-ttu-id="c6bc5-144">Sie können die anzuzeigenden Eigenschaften wie folgt explizit auswählen:</span><span class="sxs-lookup"><span data-stu-id="c6bc5-144">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="c6bc5-145">Eine kompaktere Version mit Platzhaltern ist:</span><span class="sxs-lookup"><span data-stu-id="c6bc5-145">A more succinct version using wildcards is:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a><span data-ttu-id="c6bc5-146">Abrufen des verfügbaren Speicherplatzes</span><span class="sxs-lookup"><span data-stu-id="c6bc5-146">Getting Available Disk Space</span></span>

<span data-ttu-id="c6bc5-147">Um den Speicherplatz und den freien Speicherplatz auf lokalen Laufwerken anzuzeigen, können Sie die WMI-Klasse „Win32_LogicalDisk“ verwenden.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-147">To see the disk space and free space for local drives, you can use the Win32_LogicalDisk WMI class.</span></span>
<span data-ttu-id="c6bc5-148">Sie brauchen nur Instanzen mit einem „DriveType“-Wert von „3“ anzuzeigen. Dieser Wert wird von WMI für Festplatten mit fester Größe verwendet.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-148">You need to see only instances with a DriveType of 3 — the value WMI uses for fixed hard disks.</span></span>

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

## <a name="getting-logon-session-information"></a><span data-ttu-id="c6bc5-149">Abrufen von Informationen zur Anmeldesitzung</span><span class="sxs-lookup"><span data-stu-id="c6bc5-149">Getting Logon Session Information</span></span>

<span data-ttu-id="c6bc5-150">Allgemeine Informationen zu Benutzern zugeordneten Anmeldesitzungen können Sie über die WMI-Klasse **Win32_LogonSession** abrufen:</span><span class="sxs-lookup"><span data-stu-id="c6bc5-150">You can get general information about logon sessions associated with users through the **Win32_LogonSession** WMI class:</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

## <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="c6bc5-151">Abrufen des auf einem Computer angemeldeten Benutzers</span><span class="sxs-lookup"><span data-stu-id="c6bc5-151">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="c6bc5-152">Mit „Win32_ComputerSystem“ können Sie den auf einem bestimmten Computer angemeldeten Benutzers anzeigen.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-152">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span>
<span data-ttu-id="c6bc5-153">Dieser Befehl gibt nur den auf dem Systemdesktop angemeldeten Benutzer zurück:</span><span class="sxs-lookup"><span data-stu-id="c6bc5-153">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

## <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="c6bc5-154">Abrufen der lokalen Uhrzeit eines Computers</span><span class="sxs-lookup"><span data-stu-id="c6bc5-154">Getting Local Time from a Computer</span></span>

<span data-ttu-id="c6bc5-155">Sie können die aktuelle lokale Zeit auf einem bestimmten Computer mit der Klasse **WMI-Win32_LocalTime** abrufen.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-155">You can retrieve the current local time on a specific computer by using the **Win32_LocalTime** WMI class.</span></span>

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

## <a name="displaying-service-status"></a><span data-ttu-id="c6bc5-156">Anzeigen des Dienststatus</span><span class="sxs-lookup"><span data-stu-id="c6bc5-156">Displaying Service Status</span></span>

<span data-ttu-id="c6bc5-157">Zum Anzeigen des Status aller Dienste auf einem bestimmten Computer können Sie das Cmdlet `Get-Service` verwenden.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-157">To view the status of all services on a specific computer, you can locally use the `Get-Service` cmdlet.</span></span>
<span data-ttu-id="c6bc5-158">Für Remotesysteme können Sie die Klasse **WMI-Win32_Service** verwenden.</span><span class="sxs-lookup"><span data-stu-id="c6bc5-158">For remote systems, you can use the **Win32_Service** WMI class.</span></span>
<span data-ttu-id="c6bc5-159">Wenn Sie die Ergebnisse außerdem mit `Select-Object` nach **Status**, **Name** und **DisplayName** filtern, ist das Ausgabeformat fast identisch mit dem von `Get-Service`:</span><span class="sxs-lookup"><span data-stu-id="c6bc5-159">If you also use `Select-Object` to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from `Get-Service`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="c6bc5-160">Um für die wenigen Dienste mit extrem langen Namen die Anzeige der vollständigen Namen zu ermöglichen, können Sie `Format-Table` mit den Parametern **AutoSize** und **Wrap** verwenden. Dadurch wird die Spaltenbreite optimiert und ermöglicht, dass lange Namen umgebrochen und nicht abgeschnitten werden:</span><span class="sxs-lookup"><span data-stu-id="c6bc5-160">To allow the complete display of names for the occasional services with extremely long names, you may want to use `Format-Table` with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
