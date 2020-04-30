---
title: Installieren von PowerShell unter Windows
description: Informationen zur Installation von PowerShell unter Windows
ms.date: 08/06/2018
ms.openlocfilehash: a8543a91ad503364c5346a11c9c9d9f910547278
ms.sourcegitcommit: b80ce0396550d0896189d0205d6c4b4372ac2015
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141381"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="9dc88-103">Installieren von PowerShell unter Windows</span><span class="sxs-lookup"><span data-stu-id="9dc88-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="9dc88-104">Es gibt mehrere Möglichkeiten zum Installieren von PowerShell unter Windows.</span><span class="sxs-lookup"><span data-stu-id="9dc88-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9dc88-105">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="9dc88-105">Prerequisites</span></span>

<span data-ttu-id="9dc88-106">Die neueste Version von PowerShell wird unter Windows 7 SP1, Windows Server 2008 R2 und höheren Versionen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9dc88-106">The latest release of PowerShell is supported on Windows 7 SP1, Server 2008 R2, and later versions.</span></span>

<span data-ttu-id="9dc88-107">Zum Aktivieren des PowerShell-Remoting über WSMan müssen die folgenden Voraussetzungen erfüllt sein:</span><span class="sxs-lookup"><span data-stu-id="9dc88-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="9dc88-108">[Universal C-Runtime](https://www.microsoft.com/download/details.aspx?id=50410) muss unter Windows-Versionen vor Windows 10 installiert sein.</span><span class="sxs-lookup"><span data-stu-id="9dc88-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions predating Windows 10.</span></span> <span data-ttu-id="9dc88-109">Die Runtime ist über einen direkten Download oder Windows-Update verfügbar.</span><span class="sxs-lookup"><span data-stu-id="9dc88-109">It's available via direct download or Windows Update.</span></span> <span data-ttu-id="9dc88-110">Auf vollständig gepatchten Systemen ist dieses Paket bereits installiert.</span><span class="sxs-lookup"><span data-stu-id="9dc88-110">Fully patched systems already have this package installed.</span></span>
- <span data-ttu-id="9dc88-111">Installieren Sie Windows Management Framework (WMF) 4.0 oder höher auf Windows 7 und Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="9dc88-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="9dc88-112">Weitere Informationen zu WMF erhalten Sie in der [WMF-Übersicht](/powershell/scripting/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="9dc88-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="download-the-installer-package"></a><span data-ttu-id="9dc88-113">Herunterladen des Installationspakets</span><span class="sxs-lookup"><span data-stu-id="9dc88-113">Download the installer package</span></span>

<span data-ttu-id="9dc88-114">Um PowerShell unter Windows zu installieren, laden Sie das Installationspaket von unserer GitHub-Seite [Releases][releases] herunter.</span><span class="sxs-lookup"><span data-stu-id="9dc88-114">To install PowerShell on Windows, download the install package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="9dc88-115">Scrollen Sie auf der Seite „Release“ nach unten zum Abschnitt **Assets**.</span><span class="sxs-lookup"><span data-stu-id="9dc88-115">Scroll down to the **Assets** section of the Release page.</span></span> <span data-ttu-id="9dc88-116">Der Abschnitt **Assets** ist möglicherweise zugeklappt, sodass Sie darauf klicken müssen, um ihn aufzuklappen.</span><span class="sxs-lookup"><span data-stu-id="9dc88-116">The **Assets** section may be collapsed, so you may need to click to expand it.</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="9dc88-117"><a id="msi" />Installieren des MSI-Pakets</span><span class="sxs-lookup"><span data-stu-id="9dc88-117"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="9dc88-118">Die MSI-Datei sieht so aus: `PowerShell-<version>-win-<os-arch>.msi`.</span><span class="sxs-lookup"><span data-stu-id="9dc88-118">The MSI file looks like `PowerShell-<version>-win-<os-arch>.msi`.</span></span> <span data-ttu-id="9dc88-119">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="9dc88-119">For example:</span></span>

- `PowerShell-7.0.0-win-x64.msi`
- `PowerShell-7.0.0-win-x86.msi`

<span data-ttu-id="9dc88-120">Sobald sie heruntergeladen wurde, führen Sie den Installer mit einem Doppelklick aus und befolgen die Anweisungen.</span><span class="sxs-lookup"><span data-stu-id="9dc88-120">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="9dc88-121">Das Installationsprogramm erstellt eine Verknüpfung im Windows-Startmenü.</span><span class="sxs-lookup"><span data-stu-id="9dc88-121">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="9dc88-122">Das Paket wird standardmäßig unter `$env:ProgramFiles\PowerShell\<version>` installiert</span><span class="sxs-lookup"><span data-stu-id="9dc88-122">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="9dc88-123">Sie können PowerShell über das Startmenü oder über `$env:ProgramFiles\PowerShell\<version>\pwsh.exe` starten</span><span class="sxs-lookup"><span data-stu-id="9dc88-123">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="9dc88-124">PowerShell 7 wird in ein neues Verzeichnis installiert und parallel mit Windows PowerShell 5.1 ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="9dc88-124">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="9dc88-125">Für PowerShell Core 6.x ist PowerShell 7 ein direktes Upgrade, durch das PowerShell Core 6.x entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="9dc88-125">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> - <span data-ttu-id="9dc88-126">PowerShell 7 wird in `$env:ProgramFiles\PowerShell\7` installiert.</span><span class="sxs-lookup"><span data-stu-id="9dc88-126">PowerShell 7 is installed to `$env:ProgramFiles\PowerShell\7`</span></span>
> - <span data-ttu-id="9dc88-127">Der Ordner `$env:ProgramFiles\PowerShell\7` wird `$env:PATH` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="9dc88-127">The `$env:ProgramFiles\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="9dc88-128">Der Ordner `$env:ProgramFiles\PowerShell\6` wird gelöscht.</span><span class="sxs-lookup"><span data-stu-id="9dc88-128">The `$env:ProgramFiles\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="9dc88-129">Wenn Sie PowerShell 6 und PowerShell 7 parallel ausführen müssen, installieren Sie PowerShell 6 mithilfe der [ZIP-Installationsmethode](#zip) neu.</span><span class="sxs-lookup"><span data-stu-id="9dc88-129">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [ZIP install](#zip) method.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="9dc88-130">Administrative Installation über die Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="9dc88-130">Administrative install from the command line</span></span>

<span data-ttu-id="9dc88-131">MSI-Pakete können über die Befehlszeile installiert werden, sodass Administratoren Pakete ohne Benutzerinteraktion bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="9dc88-131">MSI packages can be installed from the command line allowing administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="9dc88-132">Das MSI-Paket enthält die folgenden Eigenschaften zum Steuern der Installationsoptionen:</span><span class="sxs-lookup"><span data-stu-id="9dc88-132">The MSI package includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="9dc88-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** – Diese Eigenschaft steuert die Option zum Hinzufügen des Elements **PowerShell öffnen** zum Kontextmenü im Windows-Explorer.</span><span class="sxs-lookup"><span data-stu-id="9dc88-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="9dc88-134">**ENABLE_PSREMOTING** – Diese Eigenschaft steuert die Option zum Aktivieren von PowerShell-Remoting während der Installation.</span><span class="sxs-lookup"><span data-stu-id="9dc88-134">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="9dc88-135">**REGISTER_MANIFEST** – Diese Eigenschaft steuert die Option zum Registrieren des Manifests für Windows-Ereignisprotokollierung.</span><span class="sxs-lookup"><span data-stu-id="9dc88-135">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="9dc88-136">Das folgenden Beispiel zeigt, wie PowerShell mit allen aktivierten Installationsoptionen im Hintergrund installiert wird.</span><span class="sxs-lookup"><span data-stu-id="9dc88-136">The following example shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-7.0.0-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="9dc88-137">Eine vollständige Liste der Befehlszeilenoptionen für `Msiexec.exe` finden Sie unter [Befehlszeilenoptionen](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="9dc88-137">For a full list of command-line options for `Msiexec.exe`, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="installing-the-msix-package"></a><span data-ttu-id="9dc88-138"><a id="msix" />Installieren des MSIX-Pakets</span><span class="sxs-lookup"><span data-stu-id="9dc88-138"><a id="msix" />Installing the MSIX package</span></span>

<span data-ttu-id="9dc88-139">Um das MSIX-Paket manuell auf einem Windows 10-Client zu installieren, laden Sie das MSIX-Paket von der GitHub-Seite mit [Releases][releases] herunter.</span><span class="sxs-lookup"><span data-stu-id="9dc88-139">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="9dc88-140">Scrollen Sie nach unten zum Abschnitt **Assets** des Release, das Sie installieren möchten.</span><span class="sxs-lookup"><span data-stu-id="9dc88-140">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="9dc88-141">Der Abschnitt „Assets“ ist möglicherweise reduziert, sodass Sie klicken müssen, um ihn zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="9dc88-141">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="9dc88-142">Die MSIX-Datei sieht so aus: `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="9dc88-142">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="9dc88-143">Zum Installieren des Pakets müssen Sie das Cmdlet `Add-AppxPackage` verwenden:</span><span class="sxs-lookup"><span data-stu-id="9dc88-143">To install the package, you must use the `Add-AppxPackage` cmdlet.</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

> [!NOTE]
> <span data-ttu-id="9dc88-144">Das MSIX-Paket wurde noch nicht veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="9dc88-144">The MSIX package has not been released yet.</span></span> <span data-ttu-id="9dc88-145">Nach seiner Veröffentlichung ist es im Microsoft Store und auf der GitHub-Seite [Releases][releases] verfügbar.</span><span class="sxs-lookup"><span data-stu-id="9dc88-145">When released, the package will be available in the Microsoft Store and from the GitHub [releases][releases] page.</span></span>

## <a name="installing-the-zip-package"></a><span data-ttu-id="9dc88-146"><a id="zip" />Installieren des ZIP-Pakets</span><span class="sxs-lookup"><span data-stu-id="9dc88-146"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="9dc88-147">Binäre PowerShell ZIP-Archive werden zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="9dc88-147">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="9dc88-148">Bei der Installation des ZIP-Archivs werden die Voraussetzungen nicht wie bei den MSI-Paketen überprüft.</span><span class="sxs-lookup"><span data-stu-id="9dc88-148">Installing the ZIP archive doesn't check the prerequisites like the MSI packages do.</span></span> <span data-ttu-id="9dc88-149">Laden Sie das ZIP-Archiv von der Seite [Releases][releases] herunter.</span><span class="sxs-lookup"><span data-stu-id="9dc88-149">Download the ZIP archive from the [releases][releases] page.</span></span> <span data-ttu-id="9dc88-150">Je nachdem, wie Sie die Datei herunterladen, müssen Sie die Blockierung der Datei mit dem Cmdlet `Unblock-File` aufheben.</span><span class="sxs-lookup"><span data-stu-id="9dc88-150">Depending on how you download the file you may need to unblock the file using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="9dc88-151">Entpacken Sie den Inhalt an den Speicherort Ihrer Wahl, und führen Sie `pwsh.exe` von dort aus.</span><span class="sxs-lookup"><span data-stu-id="9dc88-151">Unzip the contents to the location of your choice and run `pwsh.exe` from there.</span></span> <span data-ttu-id="9dc88-152">Damit Remoting über WSMan einwandfrei funktioniert, müssen die [Voraussetzungen](#prerequisites) unbedingt erfüllt sein.</span><span class="sxs-lookup"><span data-stu-id="9dc88-152">For remoting over WSMan to work properly, ensure that you've met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-10-iot-enterprise"></a><span data-ttu-id="9dc88-153">Bereitstellung unter Windows 10 IoT Enterprise</span><span class="sxs-lookup"><span data-stu-id="9dc88-153">Deploying on Windows 10 IoT Enterprise</span></span>

<span data-ttu-id="9dc88-154">Bei Windows 10 IoT Enterprise ist Windows PowerShell bereits im Funktionsumfang enthalten, sodass PowerShell 7 bereitgestellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="9dc88-154">Windows 10 IoT Enterprise comes with Windows PowerShell, which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="9dc88-155">Erstellen Sie `PSSession` auf dem Zielgerät.</span><span class="sxs-lookup"><span data-stu-id="9dc88-155">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="9dc88-156">Kopieren Sie das ZIP-Paket auf das Gerät.</span><span class="sxs-lookup"><span data-stu-id="9dc88-156">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="9dc88-157">Stellen Sie eine Verbindung mit dem Gerät her, und erweitern Sie das Archiv.</span><span class="sxs-lookup"><span data-stu-id="9dc88-157">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="9dc88-158">Richten Sie Remoting für PowerShell 7 ein.</span><span class="sxs-lookup"><span data-stu-id="9dc88-158">Set up remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="9dc88-159">Stellen Sie eine Verbindung mit dem PowerShell 7-Endpunkt auf dem Gerät her.</span><span class="sxs-lookup"><span data-stu-id="9dc88-159">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```
## <a name="deploying-on-windows-10-iot-core"></a><span data-ttu-id="9dc88-160">Bereitstellung unter Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="9dc88-160">Deploying on Windows 10 IoT Core</span></span>

<span data-ttu-id="9dc88-161">Bei Windows 10 IoT Core wird Windows PowerShell hinzugefügt, wenn Sie das Feature *IOT_POWERSHELL* aufnehmen. Über dieses Feature kann PowerShell 7 bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="9dc88-161">Windows 10 IoT Core adds Windows PowerShell when you include *IOT_POWERSHELL* feature, which we can use to deploy PowerShell 7.</span></span>
<span data-ttu-id="9dc88-162">Die oben beschriebenen Schritte für Windows 10 IoT Enterprise können auch für IoT Core ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="9dc88-162">The steps defined above for Windows 10 IoT Enterprise can be followed for IoT Core as well.</span></span>

<span data-ttu-id="9dc88-163">Verwenden Sie zum Hinzufügen der aktuellen PowerShell-Version im Image den Befehl [Import-PSCoreRelease](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease). Mit diesem Befehl wird das Paket im Arbeitsbereich eingefügt und das Feature *OPENSRC_POWERSHELL* zu Ihrem Image hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="9dc88-163">For adding the latest powershell in the shipping image, use [Import-PSCoreRelease](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease) command to include the package in the workarea and add *OPENSRC_POWERSHELL* feature to your image.</span></span>

> [!NOTE]
> <span data-ttu-id="9dc88-164">Bei der ARM64-Architektur wird Windows PowerShell nicht hinzugefügt, wenn Sie *IOT_POWERSHELL* einfügen.</span><span class="sxs-lookup"><span data-stu-id="9dc88-164">For ARM64 architecture, Windows Powershell is not added when you include *IOT_POWERSHELL*.</span></span> <span data-ttu-id="9dc88-165">Daher funktioniert die ZIP-basierte Installation nicht.</span><span class="sxs-lookup"><span data-stu-id="9dc88-165">So the zip based install will not work.</span></span>
> <span data-ttu-id="9dc88-166">Sie müssen den Befehl „Import-PSCoreRelease“ verwenden, um PowerShell im Image hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="9dc88-166">You will need to use Import-PSCoreRelease command to add it in the image.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="9dc88-167">Bereitstellen auf Nano Server</span><span class="sxs-lookup"><span data-stu-id="9dc88-167">Deploying on Nano Server</span></span>

<span data-ttu-id="9dc88-168">Diese Anweisungen gehen davon aus, dass der Nano Server ein „monitorloses“ Betriebssystem ist, unter dem bereits eine Version von PowerShell ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="9dc88-168">These instructions assume that the Nano Server is a "headless" OS that has a version of PowerShell is already running on it.</span></span> <span data-ttu-id="9dc88-169">Weitere Informationen finden Sie in der [Dokumentation zu Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="9dc88-169">For more information, see the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) documentation.</span></span>

<span data-ttu-id="9dc88-170">PowerShell-Binärdateien können auf zwei verschiedene Arten bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="9dc88-170">PowerShell binaries can be deployed using two different methods.</span></span>

1. <span data-ttu-id="9dc88-171">Offline: Binden Sie die Nano Server-VHD ein, und entpacken Sie den Inhalt der ZIP-Datei an dem von Ihnen gewünschten Speicherort in dem eingebundenen Image.</span><span class="sxs-lookup"><span data-stu-id="9dc88-171">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="9dc88-172">Online: Übertragen Sie die ZIP-Datei über eine PowerShell-Sitzung, und entpacken Sie sie an dem von Ihnen gewünschten Speicherort.</span><span class="sxs-lookup"><span data-stu-id="9dc88-172">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="9dc88-173">In beiden Fällen benötigen Sie das ZIP-Releasepaket für Windows 10 x64.</span><span class="sxs-lookup"><span data-stu-id="9dc88-173">In both cases, you need the Windows 10 x64 ZIP release package.</span></span> <span data-ttu-id="9dc88-174">Führen Sie die Befehle in einer „Administrator“-Instanz von PowerShell aus.</span><span class="sxs-lookup"><span data-stu-id="9dc88-174">Run the commands within an "Administrator" instance of PowerShell.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="9dc88-175">Offlinebereitstellung von PowerShell</span><span class="sxs-lookup"><span data-stu-id="9dc88-175">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="9dc88-176">Verwenden Sie Ihr bevorzugtes ZIP-Hilfsprogramm, um das Paket in ein Verzeichnis im eingebundenen Nano Server-Image zu entpacken.</span><span class="sxs-lookup"><span data-stu-id="9dc88-176">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="9dc88-177">Heben Sie die Bereitstellung des Images auf, und starten Sie es.</span><span class="sxs-lookup"><span data-stu-id="9dc88-177">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="9dc88-178">Stellen Sie eine Verbindung zur Posteingangsinstanz von Windows PowerShell her.</span><span class="sxs-lookup"><span data-stu-id="9dc88-178">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="9dc88-179">Befolgen Sie die Anweisungen, um einen Remoting-Endpunkt mithilfe der [„Andere Instanz-Methode“](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="9dc88-179">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="9dc88-180">Onlinebereitstellung von PowerShell</span><span class="sxs-lookup"><span data-stu-id="9dc88-180">Online Deployment of PowerShell</span></span>

<span data-ttu-id="9dc88-181">Stellen Sie PowerShell mithilfe der folgenden Schritte für Nano Server bereit.</span><span class="sxs-lookup"><span data-stu-id="9dc88-181">Deploy PowerShell to Nano Server using the following steps.</span></span>

- <span data-ttu-id="9dc88-182">Stellen Sie eine Verbindung zur Posteingangsinstanz von Windows PowerShell her.</span><span class="sxs-lookup"><span data-stu-id="9dc88-182">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="9dc88-183">Kopieren Sie die Datei in die Nano Server-Instanz.</span><span class="sxs-lookup"><span data-stu-id="9dc88-183">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="9dc88-184">Geben Sie die Sitzung ein.</span><span class="sxs-lookup"><span data-stu-id="9dc88-184">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="9dc88-185">Extrahieren Sie die ZIP-Datei.</span><span class="sxs-lookup"><span data-stu-id="9dc88-185">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="9dc88-186">Befolgen Sie die Anweisungen, wenn Sie auf WSMan basierendes Remoting verwenden möchten, um einen Remoting-Endpunkt mithilfe der [„Andere Instanz-Methode“](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="9dc88-186">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="9dc88-187">Installieren als globales .NET-Tool</span><span class="sxs-lookup"><span data-stu-id="9dc88-187">Install as a .NET Global tool</span></span>

<span data-ttu-id="9dc88-188">Wenn Sie das [.NET Core SDK](/dotnet/core/sdk) bereits installiert haben, können Sie PowerShell einfach als [globales .NET-Tool](/dotnet/core/tools/global-tools) installieren.</span><span class="sxs-lookup"><span data-stu-id="9dc88-188">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="9dc88-189">Der .NET-Toolinstaller fügt `$env:USERPROFILE\dotnet\tools` Ihrer `$env:PATH`-Umgebungsvariablen hinzu.</span><span class="sxs-lookup"><span data-stu-id="9dc88-189">The dotnet tool installer adds `$env:USERPROFILE\dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="9dc88-190">Die aktuell ausgeführte Shell verfügt jedoch nicht über die aktualisierte Umgebungsvariable `$env:PATH`.</span><span class="sxs-lookup"><span data-stu-id="9dc88-190">However, the currently running shell doesn't have the updated `$env:PATH`.</span></span> <span data-ttu-id="9dc88-191">Sie können PowerShell über eine neue Shell starten, indem Sie `pwsh` eingeben.</span><span class="sxs-lookup"><span data-stu-id="9dc88-191">You can start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="9dc88-192">Vorgehensweise zum Erstellen eines Remoting-Endpunkts</span><span class="sxs-lookup"><span data-stu-id="9dc88-192">How to create a remoting endpoint</span></span>

<span data-ttu-id="9dc88-193">PowerShell unterstützt das PowerShell-Remotingprotokoll (PSRP) über WSMan und SSH.</span><span class="sxs-lookup"><span data-stu-id="9dc88-193">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="9dc88-194">Weitere Informationen finden Sie unter</span><span class="sxs-lookup"><span data-stu-id="9dc88-194">For more information, see:</span></span>

- <span data-ttu-id="9dc88-195">[SSH-Remoting in PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="9dc88-195">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="9dc88-196">[WSMan-Remoting in PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="9dc88-196">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
