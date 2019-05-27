---
title: Installieren von PowerShell Core unter Windows
description: Informationen zur Installation von PowerShell Core unter Windows
ms.date: 08/06/2018
ms.openlocfilehash: 5a3c43e27f0027cfbeeefab33b045e618e0ff045
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854360"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="4f6f6-103">Installieren von PowerShell Core unter Windows</span><span class="sxs-lookup"><span data-stu-id="4f6f6-103">Installing PowerShell Core on Windows</span></span>

<span data-ttu-id="4f6f6-104">Es gibt mehrere Möglichkeiten zum Installieren von PowerShell Core unter Windows.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-104">There are multiple ways to install PowerShell Core in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4f6f6-105">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="4f6f6-105">Prerequisites</span></span>

<span data-ttu-id="4f6f6-106">Zum Aktivieren des PowerShell-Remoting über WSMan müssen die folgenden Voraussetzungen erfüllt sein:</span><span class="sxs-lookup"><span data-stu-id="4f6f6-106">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="4f6f6-107">[Universal C-Runtime](https://www.microsoft.com/download/details.aspx?id=50410) muss auf Windows-Versionen vor Windows 10 installiert werden.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-107">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="4f6f6-108">Sie ist über einen direkten Download oder durch ein Windows-Update verfügbar.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-108">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="4f6f6-109">Auf vollständig gepatchten (inklusive optionaler Pakete), unterstützten Systeme ist sie bereits installiert.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-109">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="4f6f6-110">Installieren Sie Windows Management Framework (WMF) 4.0 oder höher auf Windows 7 und Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-110">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="4f6f6-111">Weitere Informationen zu WMF erhalten Sie in der [WMF-Übersicht](/powershell/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="4f6f6-111">For more information about WMF, see [WMF Overview](/powershell/wmf/overview).</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="4f6f6-112"><a id="msi" />Installieren des MSI-Pakets</span><span class="sxs-lookup"><span data-stu-id="4f6f6-112"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="4f6f6-113">Installieren Sie PowerShell auf einem Windows-Client oder Windows Server-Computer (funktioniert unter Windows 7 SP1, Windows Server 2008 R2 und höher), indem Sie das MSI-Paket von unserer GitHub-[Releases][]-Seite herunterladen.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-113">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span> <span data-ttu-id="4f6f6-114">Scrollen Sie nach unten zum Abschnitt **Assets** des Release, das Sie installieren möchten.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-114">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="4f6f6-115">Der Abschnitt „Assets“ ist möglicherweise reduziert, sodass Sie klicken müssen, um ihn zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-115">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="4f6f6-116">Die MSI-Datei sieht wie folgt aus: `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="4f6f6-116">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="4f6f6-117">Sobald sie heruntergeladen wurde, führen Sie den Installer mit einem Doppelklick aus und befolgen die Anweisungen.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-117">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="4f6f6-118">Das Installationsprogramm erstellt eine Verknüpfung im Windows-Startmenü.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-118">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="4f6f6-119">Das Paket wird standardmäßig unter `$env:ProgramFiles\PowerShell\<version>` installiert</span><span class="sxs-lookup"><span data-stu-id="4f6f6-119">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="4f6f6-120">Sie können PowerShell über das Startmenü oder über `$env:ProgramFiles\PowerShell\<version>\pwsh.exe` starten</span><span class="sxs-lookup"><span data-stu-id="4f6f6-120">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="4f6f6-121">Administrative Installation über die Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="4f6f6-121">Administrative install from the command line</span></span>

<span data-ttu-id="4f6f6-122">MSI-Pakete können über die Befehlszeile installiert werden.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-122">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="4f6f6-123">Dies ermöglicht es Administratoren, Pakete ohne Benutzerinteraktion bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-123">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="4f6f6-124">Das MSI-Paket für PowerShell enthält die folgenden Eigenschaften zum Steuern der Installationsoptionen:</span><span class="sxs-lookup"><span data-stu-id="4f6f6-124">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="4f6f6-125">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** – Diese Eigenschaft steuert die Option zum Hinzufügen des Elements **PowerShell öffnen** zum Kontextmenü im Windows-Explorer.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-125">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="4f6f6-126">**ENABLE_PSREMOTING** – Diese Eigenschaft steuert die Option zum Aktivieren von PowerShell-Remoting während der Installation.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-126">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="4f6f6-127">**REGISTER_MANIFEST** – Diese Eigenschaft steuert die Option zum Registrieren des Manifests für Windows-Ereignisprotokollierung.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-127">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="4f6f6-128">Die folgenden Beispiele zeigen, wie PowerShell Core im Hintergrund installiert wird, wobei alle Installationsoptionen aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-128">The following examples shows how to silently install PowerShell Core with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="4f6f6-129">Eine vollständige Liste der Befehlszeilenoptionen für „Msiexec.exe“ finden Sie unter [Befehlszeilenoptionen](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="4f6f6-129">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="4f6f6-130"><a id="zip" />Installieren des ZIP-Pakets</span><span class="sxs-lookup"><span data-stu-id="4f6f6-130"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="4f6f6-131">Binäre PowerShell ZIP-Archive werden zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-131">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="4f6f6-132">Beachten Sie, dass die Prüfung der Voraussetzungen bei der Benutzung des ZIP-Archivs nicht wie bei dem MSI-Paket durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-132">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="4f6f6-133">Damit Remoting über WSMan einwandfrei funktioniert, müssen Sie die [Voraussetzungen](#prerequisites) erfüllt haben.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-133">For remoting over WSMan to work properly,, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="4f6f6-134">Bereitstellen auf Windows IoT</span><span class="sxs-lookup"><span data-stu-id="4f6f6-134">Deploying on Windows IoT</span></span>

<span data-ttu-id="4f6f6-135">Windows IoT ist bereits in Windows PowerShell enthalten, das Sie zum Bereitstellen von PowerShell Core 6 verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-135">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="4f6f6-136">Erstellen Sie `PSSession` auf dem Zielgerät.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-136">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="4f6f6-137">Kopieren Sie das ZIP-Paket auf das Gerät.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-137">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="4f6f6-138">Stellen Sie eine Verbindung mit dem Gerät her, und erweitern Sie das Archiv.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-138">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="4f6f6-139">Richten Sie Remoting für PowerShell Core 6 ein.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-139">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="4f6f6-140">Stellen Sie eine Verbindung mit dem PowerShell Core 6-Endpunkt auf dem Gerät her.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-140">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="4f6f6-141">Bereitstellen auf Nano Server</span><span class="sxs-lookup"><span data-stu-id="4f6f6-141">Deploying on Nano Server</span></span>

<span data-ttu-id="4f6f6-142">Diese Anweisungen gehen von einer Version von PowerShell aus, die bereits auf dem Nano Server-Image ausgeführt wird und von dem [Nano Server-Image-Builder](/windows-server/get-started/deploy-nano-server) erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-142">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="4f6f6-143">Nano Server ist ein „monitorloses“ Betriebssystem.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-143">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="4f6f6-144">Core-Binärdateien können auf zwei verschiedene Arten bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-144">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="4f6f6-145">Offline: Binden Sie die Nano Server-VHD ein, und entpacken Sie den Inhalt der ZIP-Datei an dem von Ihnen gewünschten Speicherort in dem eingebundenen Image.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-145">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="4f6f6-146">Online: Übertragen Sie die ZIP-Datei über eine PowerShell-Sitzung, und entpacken Sie sie an dem von Ihnen gewünschten Speicherort.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-146">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="4f6f6-147">In beiden Fällen benötigen Sie das Windows 10 x64 ZIP-Releasepaket, und Sie müssen die Befehle in einer „Administrator“-PowerShell-Instanz ausführen.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-147">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="4f6f6-148">Offline-Bereitstellung von PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="4f6f6-148">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="4f6f6-149">Verwenden Sie Ihr bevorzugtes ZIP-Hilfsprogramm, um das Paket in ein Verzeichnis im eingebundenen Nano Server-Image zu entpacken.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-149">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="4f6f6-150">Heben Sie die Bereitstellung des Images auf, und starten Sie es.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-150">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="4f6f6-151">Stellen Sie eine Verbindung zur Posteingangsinstanz von Windows PowerShell her.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-151">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="4f6f6-152">Befolgen Sie die Anweisungen, um einen Remoting-Endpunkt mithilfe der [„Andere Instanz-Methode“](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-152">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="4f6f6-153">Onlinebereitstellung von PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="4f6f6-153">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="4f6f6-154">Die folgenden Schritte führen Sie durch die Bereitstellung von PowerShell Core für eine ausgeführte Instanz von Nano Server und die Konfiguration des dazugehörigen Remoteendpunkts.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-154">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="4f6f6-155">Stellen Sie eine Verbindung zur Posteingangsinstanz von Windows PowerShell her.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-155">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="4f6f6-156">Kopieren Sie die Datei in die Nano Server-Instanz.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-156">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="4f6f6-157">Geben Sie die Sitzung ein.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-157">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="4f6f6-158">Extrahieren Sie die ZIP-Datei.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-158">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="4f6f6-159">Befolgen Sie die Anweisungen, wenn Sie auf WSMan basierendes Remoting verwenden möchten, um einen Remoting-Endpunkt mithilfe der [„Andere Instanz-Methode“](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-159">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="4f6f6-160">Vorgehensweise zum Erstellen eines Remoting-Endpunkts</span><span class="sxs-lookup"><span data-stu-id="4f6f6-160">How to create a remoting endpoint</span></span>

<span data-ttu-id="4f6f6-161">PowerShell Core unterstützt das PowerShell-Remotingprotokoll (PSRP) über WSMan und SSH.</span><span class="sxs-lookup"><span data-stu-id="4f6f6-161">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="4f6f6-162">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="4f6f6-162">For more information, see:</span></span>

- <span data-ttu-id="4f6f6-163">[SSH Remoting in PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="4f6f6-163">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="4f6f6-164">[WSMan-Remoting in PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="4f6f6-164">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->
[Releases]: https://github.com/PowerShell/PowerShell/releases [ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md [wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
[releases]: https://github.com/PowerShell/PowerShell/releases [ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md [wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
