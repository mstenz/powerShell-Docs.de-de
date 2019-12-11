---
ms.date: 06/03/2019
keywords: powershell,cmdlet
title: Arbeiten mit Softwareinstallationen
ms.openlocfilehash: 6d2111a332f0e8c1b545186d3d950e936aed1834
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "66830289"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="c3136-103">Arbeiten mit Softwareinstallationen</span><span class="sxs-lookup"><span data-stu-id="c3136-103">Working with Software Installations</span></span>

<span data-ttu-id="c3136-104">Auf Anwendungen, die für die Verwendung von Windows Installer entwickelt wurden, kann über die WMI-Klasse **Win32_Product** zugegriffen werden, aber nicht alle heute verfügbaren Anwendungen verwenden den Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="c3136-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span>
<span data-ttu-id="c3136-105">Anwendungen, die alternative Setuproutinen verwenden, werden normalerweise nicht von Windows Installer verwaltet.</span><span class="sxs-lookup"><span data-stu-id="c3136-105">Applications that use alternate setup routines are not usually managed by the Windows Installer.</span></span>
<span data-ttu-id="c3136-106">Spezifische Verfahren für die Arbeit mit diesen Anwendungen hängen von der Installationssoftware und von den Entscheidungen des Anwendungsentwicklers ab.</span><span class="sxs-lookup"><span data-stu-id="c3136-106">Specific techniques for working with those applications depends on the installer software and decisions made by the application developer.</span></span> <span data-ttu-id="c3136-107">Beispielsweise können Anwendungen, die durch Kopieren der Dateien in einen Ordner auf den Computer installiert werden, in der Regel nicht mit den hier beschriebenen Verfahren verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="c3136-107">For example, applications installed by copying the files to a folder on the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="c3136-108">Sie können diese Anwendungen als Dateien und Ordner mit den Verfahren verwalten, die unter [Arbeiten mit Dateien und Ordnern](Working-with-Files-and-Folders.md) erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="c3136-108">You can manage these applications as files and folders by using the techniques discussed in [Working With Files and Folders](Working-with-Files-and-Folders.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="c3136-109">Die Klasse **Win32_Product** ist nicht für Abfragen optimiert.</span><span class="sxs-lookup"><span data-stu-id="c3136-109">The **Win32_Product** class is not query optimized.</span></span> <span data-ttu-id="c3136-110">Abfragen mit Platzhalterfiltern führen dazu, dass WMI alle installierten Produkte über den MSI-Anbieter auflistet und anschließend die vollständige Liste sequenziell analysiert, um den Filter zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="c3136-110">Queries that use wildcard filters cause WMI to use the MSI provider to enumerate all installed products then parse the full list sequentially to handle the filter.</span></span> <span data-ttu-id="c3136-111">Außerdem wird eine Konsistenzprüfung der installierten Pakete gestartet, um die Installation zu überprüfen und zu reparieren.</span><span class="sxs-lookup"><span data-stu-id="c3136-111">This also initiates a consistency check of packages installed, verifying and repairing the install.</span></span> <span data-ttu-id="c3136-112">Die Validierung ist ein langwieriger Prozess und kann zu Fehlern in den Ereignisprotokollen führen.</span><span class="sxs-lookup"><span data-stu-id="c3136-112">The validation is a slow process and may result in errors in the event logs.</span></span> <span data-ttu-id="c3136-113">Weitere Informationen finden Sie im [KB-Artikel 974524](https://support.microsoft.com/help/974524).</span><span class="sxs-lookup"><span data-stu-id="c3136-113">For more information seek [KB article 974524](https://support.microsoft.com/help/974524).</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="c3136-114">Auflisten von Windows Installer-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="c3136-114">Listing Windows Installer Applications</span></span>

<span data-ttu-id="c3136-115">Verwenden Sie die folgende einfache WMI-Abfrage zum Auflisten von Anwendungen, die mithilfe von Windows Installer auf einem lokalen System oder Remotesystem installiert wurden:</span><span class="sxs-lookup"><span data-stu-id="c3136-115">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)"
```

```Output
Name               Caption                     Vendor                 Version      IdentifyingNumber
----               -------                     ------                 -------      -----------------
Microsoft .NET ... Microsoft .NET Core Runt... Microsoft Corporation  16.72.26629  {ACC73072-9AD5-416C-94B...
```

<span data-ttu-id="c3136-116">Um alle Eigenschaften des Objekts **Win32_Product** auf dem Bildschirm anzuzeigen, verwenden Sie den Parameter **Property** der Formatierungs-Cmdlets (z.B. Cmdlet `Format-List`) mit dem Wert `*` (alle).</span><span class="sxs-lookup"><span data-stu-id="c3136-116">To display all the properties of the **Win32_Product** object to the display, use the **Properties** parameter of the formatting cmdlets, such as the `Format-List` cmdlet, with a value of `*` (all).</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.2 (x64)
Version               : 16.72.26629
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.2 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.2 (x64)
IdentifyingNumber     : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20180816
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\414c96e.msi
PackageCache          : C:\WINDOWS\Installer\414c96e.msi
PackageCode           : {D20AC783-1EC5-4A58-9277-F452F5EB9AD9}
PackageName           : dotnet-runtime-2.1.2-win-x64.msi
ProductID             :
RegCompany            :
RegOwner              :
Transforms            :
URLInfoAbout          :
URLUpdateInfo         :
WordCount             : 0
PSComputerName        :
CimClass              : root/cimv2:Win32_Product
CimInstanceProperties : {Caption, Description, IdentifyingNumber, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

<span data-ttu-id="c3136-117">Verwenden Sie alternativ den **Filter**-Parameter `Get-CimInstance`, um nur Microsoft .NET Framework 2.0 auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="c3136-117">Or, you could use the `Get-CimInstance` **Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="c3136-118">Der Wert des **Filter**-Parameters verwendet die Syntax der WMI-Abfragesprache (WMI Query Language, WQL) und nicht die Windows PowerShell-Syntax.</span><span class="sxs-lookup"><span data-stu-id="c3136-118">The value of the **Filter** parameter uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="c3136-119">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="c3136-119">For example:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property *
```

<span data-ttu-id="c3136-120">Um nur die relevanten Eigenschaften aufzulisten, verwenden Sie den Parameter **Property** der Formatierungs-Cmdlets zum Auflisten der gewünschten Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="c3136-120">To list only the properties that interest you, use the **Property** parameter of the formatting cmdlets to list the desired properties.</span></span>

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.2 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\414c96e.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="c3136-121">Auflisten aller deinstallierbaren Anwendungen</span><span class="sxs-lookup"><span data-stu-id="c3136-121">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="c3136-122">Da die meisten Standardanwendungen ein Deinstallationsprogramm bei Windows registrieren, können Sie mit diesen lokal arbeiten, indem Sie sie in der Windows-Registrierung suchen.</span><span class="sxs-lookup"><span data-stu-id="c3136-122">Because most standard applications register an uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span> <span data-ttu-id="c3136-123">Es gibt keine garantierte Möglichkeit, jede Anwendung auf einem System zu finden.</span><span class="sxs-lookup"><span data-stu-id="c3136-123">There is no guaranteed way to find every application on a system.</span></span> <span data-ttu-id="c3136-124">Allerdings ist es möglich, alle Programme mit Auflistungen zu finden, die unter **Software** angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c3136-124">However, it is possible to find all programs with listings displayed in **Add or Remove Programs**.</span></span> <span data-ttu-id="c3136-125">**Software** sucht diese Anwendungen im folgenden Registrierungsschlüssel:</span><span class="sxs-lookup"><span data-stu-id="c3136-125">**Add or Remove Programs** finds these applications in the following registry key:</span></span>

<span data-ttu-id="c3136-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span><span class="sxs-lookup"><span data-stu-id="c3136-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span></span>

<span data-ttu-id="c3136-127">Dieser Schlüssel kann untersucht werden, um Anwendungen zu finden.</span><span class="sxs-lookup"><span data-stu-id="c3136-127">We can examine this key to find applications.</span></span> <span data-ttu-id="c3136-128">Um die Anzeige des Deinstallationsschlüssels zu vereinfachen, kann diesem Registrierungsspeicherort ein PowerShell-Laufwerk zugeordnet werden:</span><span class="sxs-lookup"><span data-stu-id="c3136-128">To make it easier to view the Uninstall key, we can map a PowerShell drive to this registry location:</span></span>

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```
<span data-ttu-id="c3136-129">Wir haben nun ein Laufwerk mit dem Namen „Uninstall:“, das für die schnelle und bequeme Suche nach Anwendungsinstallationen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="c3136-129">We now have a drive named "Uninstall:" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="c3136-130">Wir können die Anzahl der installierten Anwendungen durch Zählen der Anzahl der Registrierungsschlüssel im PowerShell-Laufwerk „Uninstall:“ finden:</span><span class="sxs-lookup"><span data-stu-id="c3136-130">We can find the number of installed applications by counting the number of registry keys in the Uninstall: PowerShell drive:</span></span>

```
(Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="c3136-131">Diese Liste mit Anwendungen kann nun anhand einer Vielzahl von Verfahren weiter durchsucht werden, beginnend mit **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="c3136-131">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="c3136-132">Um eine Liste der Anwendungen abzurufen und in der Variablen **$UninstallableApplications** zu speichern, verwenden Sie folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="c3136-132">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

<span data-ttu-id="c3136-133">Um die Werte der Registrierungseinträge in den Registrierungsschlüsseln unter „Deinstallieren“ anzuzeigen, verwenden Sie die Methode „GetValue“ der Registrierungsschlüssel.</span><span class="sxs-lookup"><span data-stu-id="c3136-133">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="c3136-134">Der Wert der Methode ist der Name des Registrierungseintrags.</span><span class="sxs-lookup"><span data-stu-id="c3136-134">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="c3136-135">Um die Anzeigenamen der Anwendungen beispielsweise im Deinstallationsschlüssel zu suchen, verwenden Sie den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="c3136-135">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="c3136-136">Es gibt keine Garantie dafür, dass diese Werte eindeutig sind.</span><span class="sxs-lookup"><span data-stu-id="c3136-136">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="c3136-137">Im folgenden Beispiel werden zwei installierte Elemente als „Windows Media Encoder 9-Reihe“ angezeigt:</span><span class="sxs-lookup"><span data-stu-id="c3136-137">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```powershell
$UninstallableApplications | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}
```

```Output
Name                           Property
----                           --------
{ACC73072-9AD5-416C-94BF-D82DD AuthorizedCDFPrefix :
CEA0F1B}                       Comments            :
                               Contact             :
                               DisplayVersion      : 16.72.26629
                               HelpLink            :
                               HelpTelephone       :
                               InstallDate         : 20180816
                               InstallLocation     :
                               InstallSource       : C:\ProgramData\Package
                               Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
                               ModifyPath          : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               NoModify            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 67156
                               SystemComponent     : 1
                               UninstallString     : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 16
                               VersionMinor        : 72
                               WindowsInstaller    : 1
                               Version             : 273180677
                               Language            : 1033
                               DisplayName         : Microsoft .NET Core Runtime - 2.1.2 (x64)
```

## <a name="installing-applications"></a><span data-ttu-id="c3136-138">Installieren von Anwendungen</span><span class="sxs-lookup"><span data-stu-id="c3136-138">Installing Applications</span></span>

<span data-ttu-id="c3136-139">Sie können die Klasse **Win32_Product** verwenden, um Windows Installer-Pakete remote oder lokal zu installieren.</span><span class="sxs-lookup"><span data-stu-id="c3136-139">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="c3136-140">Um eine Anwendung zu installieren, müssen Sie PowerShell mit der Option „Als Administrator ausführen“ starten.</span><span class="sxs-lookup"><span data-stu-id="c3136-140">To install an application, you must start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="c3136-141">Verwenden Sie bei der Remoteinstallation einen UNC-Netzwerkpfad (Universal Naming Convention), um den Pfad zum MSI-Paket anzugeben, weil das WMI-Subsystem PowerShell-Pfade nicht interpretieren kann.</span><span class="sxs-lookup"><span data-stu-id="c3136-141">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand PowerShell paths.</span></span> <span data-ttu-id="c3136-142">Geben Sie beispielsweise zum Installieren des Pakets „NewPackage.msi“ in der Netzwerkfreigabe `\\AppServ\dsp` auf dem Remotecomputer PC01 den folgenden Befehl in der PowerShell-Eingabeaufforderung ein:</span><span class="sxs-lookup"><span data-stu-id="c3136-142">For example, to install the NewPackage.msi package located in the network share `\\AppServ\dsp` on the remote computer PC01, type the following command at the PowerShell prompt:</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

<span data-ttu-id="c3136-143">Anwendungen, die keine Windows Installer-Technologie verwenden, verfügen möglicherweise über anwendungsspezifische Methoden für die automatisierte Bereitstellung.</span><span class="sxs-lookup"><span data-stu-id="c3136-143">Applications that do not use Windows Installer technology may have application-specific methods for automated deployment.</span></span> <span data-ttu-id="c3136-144">Lesen Sie die Dokumentation zur Anwendung, oder wenden Sie sich an den Support des Anwendungsherstellers.</span><span class="sxs-lookup"><span data-stu-id="c3136-144">Check the documentation for the application or consult the application vendor's support system.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="c3136-145">Entfernen von Anwendungen</span><span class="sxs-lookup"><span data-stu-id="c3136-145">Removing Applications</span></span>

<span data-ttu-id="c3136-146">Das Entfernen eines Windows Installer-Pakets über PowerShell funktioniert ungefähr so wie die Installation eines Pakets.</span><span class="sxs-lookup"><span data-stu-id="c3136-146">Removing a Windows Installer package using PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="c3136-147">Im Folgenden ist ein Beispiel aufgeführt, in dem das zu deinstallierende Paket basierend auf seinem Namen ausgewählt wird. In einigen Fällen ist es möglicherweise einfacher, mit **IdentifyingNumber** zu filtern:</span><span class="sxs-lookup"><span data-stu-id="c3136-147">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

<span data-ttu-id="c3136-148">Das Entfernen von anderen Anwendungen ist nicht ganz so einfach, auch wenn es lokal durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c3136-148">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="c3136-149">Nach den Befehlszeilen-Deinstallationszeichenfolgen für diese Anwendungen wird durch Extrahieren der Eigenschaft **UninstallString** gesucht.</span><span class="sxs-lookup"><span data-stu-id="c3136-149">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span>
<span data-ttu-id="c3136-150">Diese Methode funktioniert für Windows Installer-Anwendungen und ältere Programme, die unter dem Deinstallationsschlüssel angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="c3136-150">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="c3136-151">Sie können die Ausgabe bei Bedarf nach dem Anzeigenamen filtern:</span><span class="sxs-lookup"><span data-stu-id="c3136-151">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="c3136-152">Möglicherweise sind diese Zeichenfolgen jedoch nur mit einigen Änderungen direkt über die PowerShell-Eingabeaufforderung verwendbar.</span><span class="sxs-lookup"><span data-stu-id="c3136-152">However, these strings may not be directly usable from the PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="c3136-153">Aktualisieren von Windows Installer-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="c3136-153">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="c3136-154">Um eine Anwendung zu aktualisieren, müssen Sie den Namen der Anwendung und den Pfad zum Aktualisierungspaket der Anwendung kennen.</span><span class="sxs-lookup"><span data-stu-id="c3136-154">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="c3136-155">Mit diesen Informationen können Sie eine Anwendung mit einem einzigen PowerShell-Befehl aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="c3136-155">With that information, you can upgrade an application with a single PowerShell command:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
