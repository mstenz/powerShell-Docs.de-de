---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Arbeiten mit Softwareinstallationen
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: 9369e3c5ac670895cd4fbd3ebc895c50efd02051
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086271"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="abb29-103">Arbeiten mit Softwareinstallationen</span><span class="sxs-lookup"><span data-stu-id="abb29-103">Working with Software Installations</span></span>

<span data-ttu-id="abb29-104">Auf Anwendungen, die für die Verwendung von Windows Installer entwickelt wurden, kann über die WMI-Klasse **Win32_Product** zugegriffen werden, aber nicht alle heute verfügbaren Anwendungen verwenden den Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="abb29-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span> <span data-ttu-id="abb29-105">Da Windows Installer eine breite Palette von Standardverfahren für die Arbeit mit installierbaren Anwendungen bereitstellt, konzentrieren wir uns in erster Linie auf diese Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="abb29-105">Because the Windows Installer provides the widest range of standard techniques for working with installable applications, we will focus primarily on those applications.</span></span> <span data-ttu-id="abb29-106">Anwendungen, die alternative Setuproutinen verwenden, werden im Allgemeinen nicht von Windows Installer verwaltet.</span><span class="sxs-lookup"><span data-stu-id="abb29-106">Applications that use alternate setup routines will generally not be managed by the Windows Installer.</span></span> <span data-ttu-id="abb29-107">Spezifische Verfahren für die Arbeit mit diesen Anwendungen hängen von der Installationssoftware und Entscheidungen des Anwendungsentwicklers ab.</span><span class="sxs-lookup"><span data-stu-id="abb29-107">Specific techniques for working with those applications will depend on the installer software and decisions made by the application developer.</span></span>

> [!NOTE]
> <span data-ttu-id="abb29-108">Anwendungen, die durch Kopieren der Anwendungsdateien auf den Computer installiert werden, können in der Regel nicht mit den hier beschriebenen Verfahren verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="abb29-108">Applications that are installed by copying the application files to the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="abb29-109">Sie können diese Anwendungen als Dateien und Ordner mit den Verfahren verwalten, die im Abschnitt „Arbeiten mit Dateien und Ordnern“ erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="abb29-109">You can manage these applications as files and folders by using the techniques discussed in the "Working With Files and Folders" section.</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="abb29-110">Auflisten von Windows Installer-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="abb29-110">Listing Windows Installer Applications</span></span>

<span data-ttu-id="abb29-111">Verwenden Sie die folgende einfache WMI-Abfrage zum Auflisten von Anwendungen, die mithilfe von Windows Installer auf einem lokalen System oder Remotesystem installiert wurden:</span><span class="sxs-lookup"><span data-stu-id="abb29-111">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

<span data-ttu-id="abb29-112">Um alle Eigenschaften des Objekts „Win32_Product“ auf dem Bildschirm anzuzeigen, verwenden Sie den Eigenschaftenparameter der Formatierungs-Cmdlets wie z.B. das Cmdlet „Format-List“ mit dem Wert „\*“ (alle).</span><span class="sxs-lookup"><span data-stu-id="abb29-112">To display all of the properties of the Win32_Product object to the display, use the Properties parameter of the formatting cmdlets, such as the Format-List cmdlet, with a value of \* (all).</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Microsoft .NET Framework 2.0"} | Format-List -Property *

Name              : Microsoft .NET Framework 2.0
Version           : 2.0.50727
InstallState      : 5
Caption           : Microsoft .NET Framework 2.0
Description       : Microsoft .NET Framework 2.0
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
InstallDate       : 20060506
InstallDate2      : 20060506000000.000000-000
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\619ab2.msi
SKUNumber         :
Vendor            : Microsoft Corporation
```

<span data-ttu-id="abb29-113">Oder verwenden Sie den Parameter **Get-WmiObject Filter**, um nur Microsoft .NET Framework 2.0 auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="abb29-113">Or, you could use the **Get-WmiObject Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="abb29-114">Da es sich bei dem in diesem Befehl verwendeten Filter um einen WMI-Filter handelt, verwendet er die Syntax der WMI Query Language (WQL) und nicht die Windows PowerShell-Syntax</span><span class="sxs-lookup"><span data-stu-id="abb29-114">Because the filter used in this command is a WMI filter, it uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="abb29-115">:</span><span class="sxs-lookup"><span data-stu-id="abb29-115">Instead,:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

<span data-ttu-id="abb29-116">Beachten Sie, dass WQL-Abfragen häufig Zeichen wie Leerzeichen oder Gleichheitszeichen verwenden, die in Windows PowerShell eine besondere Bedeutung haben.</span><span class="sxs-lookup"><span data-stu-id="abb29-116">Note that WQL queries frequently use characters, such as spaces or equal signs, that have a special meaning in Windows PowerShell.</span></span> <span data-ttu-id="abb29-117">Aus diesem Grund ist es ratsam, den Wert des Filterparameters immer in Anführungszeichen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="abb29-117">For this reason, it is prudent to always enclose the value of the Filter parameter in quotation marks.</span></span> <span data-ttu-id="abb29-118">Sie können auch das Windows PowerShell-Escapezeichen verwenden, ein Hochkomma (\`), obwohl die Lesbarkeit damit möglicherweise nicht verbessert wird.</span><span class="sxs-lookup"><span data-stu-id="abb29-118">You can also use the Windows PowerShell escape character, a backtick (\`), although it may not improve readability.</span></span> <span data-ttu-id="abb29-119">Der folgende Befehl entspricht dem vorherigen Befehl und es werden dieselben Ergebnisse zurückgegeben, aber es wird das Hochkomma als Escapezeichen für Sonderzeichen verwendet, statt die gesamte Filterzeichenfolge wiederzugeben</span><span class="sxs-lookup"><span data-stu-id="abb29-119">The following command is equivalent to the previous command and returns the same results, but uses the backtick to escape special characters, instead of quoting the entire filter string.</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

<span data-ttu-id="abb29-120">Um nur die Eigenschaften von Interesse aufzulisten, verwenden Sie den Eigenschaftenparameter der Formatierungs-Cmdlets zur Auflistung der gewünschten Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="abb29-120">To list only the properties that interest you, use the Property parameter of the formatting cmdlets to list the desired properties.</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName . | Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
...
Name              : HighMAT Extension to Microsoft Windows XP CD Writing Wizard
InstallDate       : 20051022
InstallLocation   : C:\Program Files\HighMAT CD Writing Wizard\
PackageCache      : C:\WINDOWS\Installer\113b54.msi
Vendor            : Microsoft Corporation
Version           : 1.1.1905.1
IdentifyingNumber : {FCE65C4E-B0E8-4FBD-AD16-EDCBE6CD591F}
...
```

<span data-ttu-id="abb29-121">Um schließlich nur die Namen der installierten Anwendungen anzuzeigen, vereinfacht die **Format-Wide**-Anweisung die Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="abb29-121">Finally, to find only the names of installed applications, a simple **Format-Wide** statement simplifies the output:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

<span data-ttu-id="abb29-122">Obwohl es nun mehrere Möglichkeiten zum Anzeigen der Anwendungen gibt, die mit Windows Installer installiert wurden, wurden keine anderen Anwendungen berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="abb29-122">Although we now have several ways to look at applications that used the Windows Installer for installation, we have not considered other applications.</span></span> <span data-ttu-id="abb29-123">Da die meisten Standardanwendungen ihr Deinstallationsprogramm bei Windows registrieren, können Sie mit diesen lokal arbeiten, indem Sie sie in der Windows-Registrierung suchen.</span><span class="sxs-lookup"><span data-stu-id="abb29-123">Because most standard applications register their uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span>

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="abb29-124">Auflisten aller deinstallierbaren Anwendungen</span><span class="sxs-lookup"><span data-stu-id="abb29-124">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="abb29-125">Es gibt zwar keine sichere Methode, alle Anwendungen auf einem System zu finden, aber es ist möglich, alle Programme mit Auflistungen zu finden, die im Dialogfeld „Software“ angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="abb29-125">Although there is no guaranteed way to find every application on a system, it is possible to find all programs with listings displayed in the Add or Remove Programs dialog box.</span></span> <span data-ttu-id="abb29-126">„Software“ sucht diese Anwendungen im folgenden Registrierungsschlüssel:</span><span class="sxs-lookup"><span data-stu-id="abb29-126">Add or Remove Programs finds these applications in the following registry key:</span></span>

<span data-ttu-id="abb29-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span><span class="sxs-lookup"><span data-stu-id="abb29-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span></span>

<span data-ttu-id="abb29-128">Dieser Schlüssel kann auch untersucht werden, um Anwendungen zu finden.</span><span class="sxs-lookup"><span data-stu-id="abb29-128">We can also examine this key to find applications.</span></span> <span data-ttu-id="abb29-129">Um die Anzeige des Deinstallationsschlüssel zu vereinfachen, kann diesem Registrierungsspeicherort ein Windows PowerShell-Laufwerk zugeordnet werden:</span><span class="sxs-lookup"><span data-stu-id="abb29-129">To make it easier to view the Uninstall key, we can map a Windows PowerShell drive to this registry location:</span></span>

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> <span data-ttu-id="abb29-130">Das Laufwerk **HKLM:** ist dem Stammverzeichnis von **HKEY_LOCAL_MACHINE** zugeordnet, daher haben wir dieses Laufwerk im Pfad zum Deinstallationsschlüssel verwendet.</span><span class="sxs-lookup"><span data-stu-id="abb29-130">The **HKLM:** drive is mapped to the root of **HKEY_LOCAL_MACHINE**, so we used that drive in the path to the Uninstall key.</span></span> <span data-ttu-id="abb29-131">Statt **HKLM:** hätten wir den Registrierungspfad entweder mit **HKLM** oder **HKEY_LOCAL_MACHINE** festlegen können.</span><span class="sxs-lookup"><span data-stu-id="abb29-131">Instead of **HKLM:** we could have specified the registry path by using either **HKLM** or **HKEY_LOCAL_MACHINE**.</span></span> <span data-ttu-id="abb29-132">Der Vorteil der Verwendung eines vorhandenen Registrierungslaufwerks ist, dass wir die Befehlszeilenergänzung verwenden können, um die Namen der Schlüssel zu vervollständigen, ohne sie ganz eingeben zu müssen.</span><span class="sxs-lookup"><span data-stu-id="abb29-132">The advantage of using an existing registry drive is that we can use tab-completion to fill in the keys names, so we do not need to type them.</span></span>

<span data-ttu-id="abb29-133">Wir haben nun ein Laufwerk mit dem Namen „Deinstallieren“, das für die schnelle und bequeme Suche nach Anwendungsinstallationen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="abb29-133">We now have a drive named "Uninstall" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="abb29-134">Wir können die Anzahl der installierten Anwendungen durch Zählen der Anzahl der Registrierungsschlüssel im Laufwerk „Deinstallieren: Windows PowerShell“ finden:</span><span class="sxs-lookup"><span data-stu-id="abb29-134">We can find the number of installed applications by counting the number of registry keys in the Uninstall: Windows PowerShell drive:</span></span>

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="abb29-135">Diese Liste mit Anwendungen kann nun anhand einer Vielzahl von Verfahren weiter durchsucht werden, beginnend mit **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="abb29-135">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="abb29-136">Um eine Liste der Anwendungen abzurufen und in der Variablen **$UninstallableApplications** zu speichern, verwenden Sie folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="abb29-136">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> <span data-ttu-id="abb29-137">Wir verwenden an dieser Stelle einen langen Variablennamen aus Gründen der Übersichtlichkeit.</span><span class="sxs-lookup"><span data-stu-id="abb29-137">We are using a lengthy variable name here for clarity.</span></span> <span data-ttu-id="abb29-138">Tatsächlich ist es nicht notwendig, lange Namen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="abb29-138">In actual use, there is no reason to use long names.</span></span> <span data-ttu-id="abb29-139">Zwar können Sie die Befehlszeilenergänzung für Variablennamen verwenden, Sie können aber zur schnelleren Bearbeitung auch Namen mit 1-2 Zeichen verwenden.</span><span class="sxs-lookup"><span data-stu-id="abb29-139">Although you can use tab-completion for variable names, you can also use 1-2 character names for speed.</span></span> <span data-ttu-id="abb29-140">Längere und aussagekräftige Namen sind besonders hilfreich, wenn Sie Code zur Wiederverwendung entwickeln.</span><span class="sxs-lookup"><span data-stu-id="abb29-140">Longer, descriptive names are most useful when you are developing code for reuse.</span></span>

<span data-ttu-id="abb29-141">Um die Werte der Registrierungseinträge in den Registrierungsschlüsseln unter „Deinstallieren“ anzuzeigen, verwenden Sie die Methode „GetValue“ der Registrierungsschlüssel.</span><span class="sxs-lookup"><span data-stu-id="abb29-141">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="abb29-142">Der Wert der Methode ist der Name des Registrierungseintrags.</span><span class="sxs-lookup"><span data-stu-id="abb29-142">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="abb29-143">Um die Anzeigenamen der Anwendungen beispielsweise im Deinstallationsschlüssel zu suchen, verwenden Sie den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="abb29-143">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="abb29-144">Es gibt keine Garantie dafür, dass diese Werte eindeutig sind.</span><span class="sxs-lookup"><span data-stu-id="abb29-144">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="abb29-145">Im folgenden Beispiel werden zwei installierte Elemente als „Windows Media Encoder 9-Reihe“ angezeigt:</span><span class="sxs-lookup"><span data-stu-id="abb29-145">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

## <a name="installing-applications"></a><span data-ttu-id="abb29-146">Installieren von Anwendungen</span><span class="sxs-lookup"><span data-stu-id="abb29-146">Installing Applications</span></span>

<span data-ttu-id="abb29-147">Sie können die Klasse **Win32_Product** verwenden, um Windows Installer-Pakete remote oder lokal zu installieren.</span><span class="sxs-lookup"><span data-stu-id="abb29-147">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="abb29-148">Unter Windows Vista, Windows Server 2008 und höheren Versionen von Windows müssen Sie Windows PowerShell zum Installieren einer Anwendung mit der Option „Als Administrator ausführen“ starten.</span><span class="sxs-lookup"><span data-stu-id="abb29-148">On Windows Vista, Windows Server 2008, and later versions of Windows, to install an application, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="abb29-149">Verwenden Sie bei der Remoteinstallation einen UNC-Netzwerkpfad (Universal Naming Convention), um den Pfad zum MSI-Paket anzugeben, da das WMI-Subsystem Windows PowerShell-Pfade nicht interpretieren kann.</span><span class="sxs-lookup"><span data-stu-id="abb29-149">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand Windows PowerShell paths.</span></span> <span data-ttu-id="abb29-150">Geben Sie beispielsweise zum Installieren des Pakets „NewPackage.msi“ in der Netzwerkfreigabe „\\\\AppServ\\dsp“ auf dem Remotecomputer PC01 den folgenden Befehl in der Windows PowerShell-Eingabeaufforderung ein:</span><span class="sxs-lookup"><span data-stu-id="abb29-150">For example, to install the NewPackage.msi package located in the network share \\\\AppServ\\dsp on the remote computer PC01, type the following command at the Windows PowerShell prompt:</span></span>

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

<span data-ttu-id="abb29-151">Anwendungen, die keine Windows Installer-Technologie verwenden, verfügen möglicherweise über anwendungsspezifische Methoden für die automatisierte Bereitstellung.</span><span class="sxs-lookup"><span data-stu-id="abb29-151">Applications that do not use Windows Installer technology may have application-specific methods available for automated deployment.</span></span> <span data-ttu-id="abb29-152">Um zu bestimmen, ob es eine Methode für die automatische Bereitstellung gibt, überprüfen Sie die Dokumentation für die Anwendung, oder wenden Sie sich an den Support des Anwendungsherstellers.</span><span class="sxs-lookup"><span data-stu-id="abb29-152">To determine whether there is a method for deployment automation, check the documentation for the application or consult the application vendor's support system.</span></span> <span data-ttu-id="abb29-153">In einigen Fällen verfügt die Installationssoftware möglicherweise über Verfahren zur Automatisierung, auch wenn der Hersteller der Anwendung diese nicht speziell für die Automatisierung der Installation vorgesehen hat.</span><span class="sxs-lookup"><span data-stu-id="abb29-153">In some cases, even if the application vendor did not specifically design the application for installation automation, the installer software manufacturer may have some techniques for automation.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="abb29-154">Entfernen von Anwendungen</span><span class="sxs-lookup"><span data-stu-id="abb29-154">Removing Applications</span></span>

<span data-ttu-id="abb29-155">Das Entfernen eines Windows Installer-Pakets mithilfe von Windows PowerShell funktioniert ungefähr so wie die Installation eines Pakets.</span><span class="sxs-lookup"><span data-stu-id="abb29-155">Removing a Windows Installer package by using Windows PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="abb29-156">Im Folgenden ist ein Beispiel aufgeführt, in dem das zu deinstallierende Paket basierend auf seinem Namen ausgewählt wird. In einigen Fällen ist es möglicherweise einfacher, mit **IdentifyingNumber** zu filtern:</span><span class="sxs-lookup"><span data-stu-id="abb29-156">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

<span data-ttu-id="abb29-157">Das Entfernen von anderen Anwendungen ist nicht ganz so einfach, auch wenn es lokal durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="abb29-157">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="abb29-158">Nach den Befehlszeilen-Deinstallationszeichenfolgen für diese Anwendungen wird durch Extrahieren der Eigenschaft **UninstallString** gesucht.</span><span class="sxs-lookup"><span data-stu-id="abb29-158">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span> <span data-ttu-id="abb29-159">Diese Methode funktioniert für Windows Installer-Anwendungen und ältere Programme, die unter dem Deinstallationsschlüssel angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="abb29-159">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="abb29-160">Sie können die Ausgabe bei Bedarf nach dem Anzeigenamen filtern:</span><span class="sxs-lookup"><span data-stu-id="abb29-160">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="abb29-161">Diese Zeichenfolgen sind jedoch möglicherweise direkt über die Windows PowerShell-Eingabeaufforderung nur mit einigen Änderungen verwendbar.</span><span class="sxs-lookup"><span data-stu-id="abb29-161">However, these strings may not be directly usable from the Windows PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="abb29-162">Aktualisieren von Windows Installer-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="abb29-162">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="abb29-163">Um eine Anwendung zu aktualisieren, müssen Sie den Namen der Anwendung und den Pfad zum Aktualisierungspaket der Anwendung kennen.</span><span class="sxs-lookup"><span data-stu-id="abb29-163">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="abb29-164">Mit diesen Informationen können Sie eine Anwendung mit einem einzigen Windows PowerShell-Befehl aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="abb29-164">With that information, you can upgrade an application with a single Windows PowerShell command:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```