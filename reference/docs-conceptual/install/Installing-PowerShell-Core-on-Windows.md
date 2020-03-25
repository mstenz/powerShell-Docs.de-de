---
title: Installieren von PowerShell unter Windows
description: Informationen zur Installation von PowerShell unter Windows
ms.date: 08/06/2018
ms.openlocfilehash: bb0971b6c4ac99bde70b226da2becf2f4ed82083
ms.sourcegitcommit: d36db3a1bc44aee6bc97422b557041c3aece4c67
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082779"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="cb0f3-103">Installieren von PowerShell unter Windows</span><span class="sxs-lookup"><span data-stu-id="cb0f3-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="cb0f3-104">Es gibt mehrere Möglichkeiten zum Installieren von PowerShell unter Windows.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cb0f3-105">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="cb0f3-105">Prerequisites</span></span>

<span data-ttu-id="cb0f3-106">Zum Aktivieren des PowerShell-Remoting über WSMan müssen die folgenden Voraussetzungen erfüllt sein:</span><span class="sxs-lookup"><span data-stu-id="cb0f3-106">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="cb0f3-107">[Universal C-Runtime](https://www.microsoft.com/download/details.aspx?id=50410) muss auf Windows-Versionen vor Windows 10 installiert werden.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-107">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="cb0f3-108">Sie ist über einen direkten Download oder durch ein Windows-Update verfügbar.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-108">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="cb0f3-109">Auf vollständig gepatchten (inklusive optionaler Pakete), unterstützten Systeme ist sie bereits installiert.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-109">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="cb0f3-110">Installieren Sie Windows Management Framework (WMF) 4.0 oder höher auf Windows 7 und Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-110">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="cb0f3-111">Weitere Informationen zu WMF erhalten Sie in der [WMF-Übersicht](/powershell/scripting/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="cb0f3-111">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="cb0f3-112"><a id="msi" />Installieren des MSI-Pakets</span><span class="sxs-lookup"><span data-stu-id="cb0f3-112"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="cb0f3-113">Installieren Sie PowerShell auf einem Windows-Client oder Windows Server (funktioniert auf Windows 7 SP1, Windows Server 2008 R2 und höher), indem Sie das MSI-Paket von unserer GitHub [Freigaben][releases]-Seite herunterladen.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-113">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="cb0f3-114">Scrollen Sie nach unten zum Abschnitt **Assets** des Release, das Sie installieren möchten.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-114">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="cb0f3-115">Der Abschnitt „Assets“ ist möglicherweise reduziert, sodass Sie klicken müssen, um ihn zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-115">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="cb0f3-116">Die MSI-Datei sieht wie folgt aus: `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="cb0f3-116">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>

<span data-ttu-id="cb0f3-117">Sobald sie heruntergeladen wurde, führen Sie den Installer mit einem Doppelklick aus und befolgen die Anweisungen.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-117">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="cb0f3-118">Das Installationsprogramm erstellt eine Verknüpfung im Windows-Startmenü.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-118">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="cb0f3-119">Das Paket wird standardmäßig unter `$env:ProgramFiles\PowerShell\<version>` installiert</span><span class="sxs-lookup"><span data-stu-id="cb0f3-119">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="cb0f3-120">Sie können PowerShell über das Startmenü oder über `$env:ProgramFiles\PowerShell\<version>\pwsh.exe` starten</span><span class="sxs-lookup"><span data-stu-id="cb0f3-120">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="cb0f3-121">PowerShell 7 wird in ein neues Verzeichnis installiert und parallel mit Windows PowerShell 5.1 ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-121">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="cb0f3-122">Für PowerShell Core 6.x ist PowerShell 7 ein direktes Upgrade, durch das PowerShell Core 6.x entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-122">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> - <span data-ttu-id="cb0f3-123">PowerShell 7 wird in `%programfiles%\PowerShell\7` installiert.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-123">PowerShell 7 is installed to `%programfiles%\PowerShell\7`</span></span>
> - <span data-ttu-id="cb0f3-124">Der Ordner `%programfiles%\PowerShell\7` wird `$env:PATH` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-124">The `%programfiles%\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="cb0f3-125">Der Ordner `%programfiles%\PowerShell\6` wird gelöscht.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-125">The `%programfiles%\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="cb0f3-126">Wenn Sie PowerShell 6 und PowerShell 7 parallel ausführen müssen, installieren Sie PowerShell 6 mithilfe der [ZIP-Installationsmethode](#zip) neu.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-126">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [ZIP install](#zip) method.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="cb0f3-127">Administrative Installation über die Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="cb0f3-127">Administrative install from the command line</span></span>

<span data-ttu-id="cb0f3-128">MSI-Pakete können über die Befehlszeile installiert werden.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-128">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="cb0f3-129">Dies ermöglicht es Administratoren, Pakete ohne Benutzerinteraktion bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-129">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="cb0f3-130">Das MSI-Paket für PowerShell enthält die folgenden Eigenschaften zum Steuern der Installationsoptionen:</span><span class="sxs-lookup"><span data-stu-id="cb0f3-130">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="cb0f3-131">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** – Diese Eigenschaft steuert die Option zum Hinzufügen des Elements **PowerShell öffnen** zum Kontextmenü im Windows-Explorer.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-131">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="cb0f3-132">**ENABLE_PSREMOTING** – Diese Eigenschaft steuert die Option zum Aktivieren von PowerShell-Remoting während der Installation.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-132">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="cb0f3-133">**REGISTER_MANIFEST** – Diese Eigenschaft steuert die Option zum Registrieren des Manifests für Windows-Ereignisprotokollierung.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-133">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="cb0f3-134">Die folgenden Beispiele zeigen, wie PowerShell im Hintergrund installiert wird, wobei alle Installationsoptionen aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-134">The following examples shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="cb0f3-135">Eine vollständige Liste der Befehlszeilenoptionen für „Msiexec.exe“ finden Sie unter [Befehlszeilenoptionen](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="cb0f3-135">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="installing-the-msix-package"></a><span data-ttu-id="cb0f3-136"><a id="msix" />Installieren des MSIX-Pakets</span><span class="sxs-lookup"><span data-stu-id="cb0f3-136"><a id="msix" />Installing the MSIX package</span></span>

<span data-ttu-id="cb0f3-137">Um das MSIX-Paket manuell auf einem Windows 10-Client zu installieren, laden Sie das MSIX-Paket von der GitHub-Seite mit [Releases][releases] herunter.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-137">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="cb0f3-138">Scrollen Sie nach unten zum Abschnitt **Assets** des Release, das Sie installieren möchten.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-138">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="cb0f3-139">Der Abschnitt „Assets“ ist möglicherweise reduziert, sodass Sie klicken müssen, um ihn zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-139">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="cb0f3-140">Die MSIX-Datei sieht so aus: `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="cb0f3-140">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="cb0f3-141">Nach dem Download können Sie nicht einfach auf das Installationsprogramm doppelklicken, weil dieses Paket die Verwendung nicht virtualisierter Ressourcen erfordert.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-141">Once downloaded, you cannot simply double-click on the installer as this package requires use of un-virtualized resources.</span></span>  <span data-ttu-id="cb0f3-142">Zum Installieren müssen Sie das Cmdlet `Add-AppxPackage` verwenden:</span><span class="sxs-lookup"><span data-stu-id="cb0f3-142">To install, you must use the `Add-AppxPackage` cmdlet:</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="installing-the-zip-package"></a><span data-ttu-id="cb0f3-143"><a id="zip" />Installieren des ZIP-Pakets</span><span class="sxs-lookup"><span data-stu-id="cb0f3-143"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="cb0f3-144">Binäre PowerShell ZIP-Archive werden zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-144">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="cb0f3-145">Beachten Sie, dass die Prüfung der Voraussetzungen bei der Benutzung des ZIP-Archivs nicht wie bei dem MSI-Paket durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-145">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="cb0f3-146">Damit Remoting über WSMan einwandfrei funktioniert, müssen Sie die [Voraussetzungen](#prerequisites) erfüllt haben.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-146">For remoting over WSMan to work properly, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="cb0f3-147">Bereitstellen auf Windows IoT</span><span class="sxs-lookup"><span data-stu-id="cb0f3-147">Deploying on Windows IoT</span></span>

<span data-ttu-id="cb0f3-148">Windows IoT wird bereits mit Windows PowerShell geliefert, welches Sie zum Bereitstellen von PowerShell 7 verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-148">Windows IoT already comes with Windows PowerShell which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="cb0f3-149">Erstellen Sie `PSSession` auf dem Zielgerät.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-149">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="cb0f3-150">Kopieren Sie das ZIP-Paket auf das Gerät.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-150">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="cb0f3-151">Stellen Sie eine Verbindung mit dem Gerät her, und erweitern Sie das Archiv.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-151">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="cb0f3-152">Richten Sie Remoting für PowerShell 7 ein.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-152">Setup remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="cb0f3-153">Stellen Sie eine Verbindung mit dem PowerShell 7-Endpunkt auf dem Gerät her.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-153">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="cb0f3-154">Bereitstellen auf Nano Server</span><span class="sxs-lookup"><span data-stu-id="cb0f3-154">Deploying on Nano Server</span></span>

<span data-ttu-id="cb0f3-155">Diese Anweisungen gehen von einer Version von PowerShell aus, die bereits auf dem Nano Server-Image ausgeführt wird und von dem [Nano Server-Image-Builder](/windows-server/get-started/deploy-nano-server) erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-155">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="cb0f3-156">Nano Server ist ein „monitorloses“ Betriebssystem.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-156">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="cb0f3-157">PowerShell-Binärdateien können auf zwei verschiedene Arten bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-157">PowerShell binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="cb0f3-158">Offline: Binden Sie die Nano Server-VHD ein, und entpacken Sie den Inhalt der ZIP-Datei an dem von Ihnen gewünschten Speicherort in dem eingebundenen Image.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-158">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="cb0f3-159">Online: Übertragen Sie die ZIP-Datei über eine PowerShell-Sitzung, und entpacken Sie sie an dem von Ihnen gewünschten Speicherort.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-159">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="cb0f3-160">In beiden Fällen benötigen Sie das Windows 10 x64 ZIP-Releasepaket, und Sie müssen die Befehle in einer „Administrator“-PowerShell-Instanz ausführen.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-160">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="cb0f3-161">Offlinebereitstellung von PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb0f3-161">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="cb0f3-162">Verwenden Sie Ihr bevorzugtes ZIP-Hilfsprogramm, um das Paket in ein Verzeichnis im eingebundenen Nano Server-Image zu entpacken.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-162">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="cb0f3-163">Heben Sie die Bereitstellung des Images auf, und starten Sie es.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-163">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="cb0f3-164">Stellen Sie eine Verbindung zur Posteingangsinstanz von Windows PowerShell her.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-164">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="cb0f3-165">Befolgen Sie die Anweisungen, um einen Remoting-Endpunkt mithilfe der [„Andere Instanz-Methode“](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-165">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="cb0f3-166">Onlinebereitstellung von PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb0f3-166">Online Deployment of PowerShell</span></span>

<span data-ttu-id="cb0f3-167">Die folgenden Schritte führen Sie durch die Bereitstellung von PowerShell für eine ausgeführte Instanz von Nano Server und die Konfiguration des zugehörigen Remoteendpunkts.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-167">The following steps guide you through the deployment of PowerShell to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="cb0f3-168">Stellen Sie eine Verbindung zur Posteingangsinstanz von Windows PowerShell her.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-168">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="cb0f3-169">Kopieren Sie die Datei in die Nano Server-Instanz.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-169">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="cb0f3-170">Geben Sie die Sitzung ein.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-170">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="cb0f3-171">Extrahieren Sie die ZIP-Datei.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-171">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="cb0f3-172">Befolgen Sie die Anweisungen, wenn Sie auf WSMan basierendes Remoting verwenden möchten, um einen Remoting-Endpunkt mithilfe der [„Andere Instanz-Methode“](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-172">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="cb0f3-173">Installieren als globales .NET-Tool</span><span class="sxs-lookup"><span data-stu-id="cb0f3-173">Install as a .NET Global tool</span></span>

<span data-ttu-id="cb0f3-174">Wenn Sie das [.NET Core SDK](/dotnet/core/sdk) bereits installiert haben, können Sie PowerShell einfach als [globales .NET-Tool](/dotnet/core/tools/global-tools) installieren.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-174">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="cb0f3-175">Der .NET-Toolinstaller fügt `$env:USERPROFILE\dotnet\tools` Ihrer `$env:PATH`-Umgebungsvariablen hinzu.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-175">The dotnet tool installer adds `$env:USERPROFILE\dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="cb0f3-176">Die aktuell ausgeführte Shell verfügt jedoch nicht über den aktualisierten `$env:PATH`.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-176">However, the currently running shell does not have the updated `$env:PATH`.</span></span> <span data-ttu-id="cb0f3-177">Sie sollten PowerShell über eine neue Shell starten können, indem Sie `pwsh` eingeben.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-177">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="cb0f3-178">Vorgehensweise zum Erstellen eines Remoting-Endpunkts</span><span class="sxs-lookup"><span data-stu-id="cb0f3-178">How to create a remoting endpoint</span></span>

<span data-ttu-id="cb0f3-179">PowerShell unterstützt das PowerShell-Remotingprotokoll (PSRP) über WSMan und SSH.</span><span class="sxs-lookup"><span data-stu-id="cb0f3-179">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="cb0f3-180">Weitere Informationen finden Sie unter</span><span class="sxs-lookup"><span data-stu-id="cb0f3-180">For more information, see:</span></span>

- <span data-ttu-id="cb0f3-181">[SSH-Remoting in PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="cb0f3-181">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="cb0f3-182">[WSMan-Remoting in PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="cb0f3-182">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
