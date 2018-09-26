---
title: Installieren von PowerShell Core unter Windows
description: Informationen zur Installation von PowerShell Core unter Windows
ms.date: 08/06/2018
ms.openlocfilehash: 595f12efd060406264a1a4efb9d54035da06ffe3
ms.sourcegitcommit: b235c58b34d23317076540631f5cf83f1f309c0d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45557177"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="f7ae0-103">Installieren von PowerShell Core unter Windows</span><span class="sxs-lookup"><span data-stu-id="f7ae0-103">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="f7ae0-104">MSI</span><span class="sxs-lookup"><span data-stu-id="f7ae0-104">MSI</span></span>

<span data-ttu-id="f7ae0-105">Installieren Sie PowerShell auf einem Windows-Client oder Windows Server (funktioniert auf Windows 7 SP1, Windows Server 2008 R2 und höher), indem Sie das MSI-Paket von unserer GitHub [Releases][]-Seite herunterladen.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-105">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="f7ae0-106">Die MSI-Datei sieht wie folgt aus: `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span><span class="sxs-lookup"><span data-stu-id="f7ae0-106">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span></span>

<span data-ttu-id="f7ae0-107">Sobald sie heruntergeladen wurde, führen Sie den Installer mit einem Doppelklick aus und befolgen die Anweisungen.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-107">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="f7ae0-108">Bei der Installation wird im Startmenü eine Verknüpfung erstellt.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-108">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="f7ae0-109">Das Paket wird standardmäßig unter `$env:ProgramFiles\PowerShell\<version>` installiert</span><span class="sxs-lookup"><span data-stu-id="f7ae0-109">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="f7ae0-110">Sie können PowerShell über das Startmenü oder über `$env:ProgramFiles\PowerShell\<version>\pwsh.exe` starten</span><span class="sxs-lookup"><span data-stu-id="f7ae0-110">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="f7ae0-111">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="f7ae0-111">Prerequisites</span></span>

<span data-ttu-id="f7ae0-112">Zum Aktivieren des PowerShell-Remoting über WSMan müssen die folgenden Voraussetzungen erfüllt sein:</span><span class="sxs-lookup"><span data-stu-id="f7ae0-112">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="f7ae0-113">[Universal C-Runtime](https://www.microsoft.com/download/details.aspx?id=50410) muss auf Windows-Versionen vor Windows 10 installiert werden.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-113">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="f7ae0-114">Sie ist über einen direkten Download oder durch ein Windows-Update verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-114">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="f7ae0-115">Auf vollständig gepatchten (inklusive optionaler Pakete), unterstützten Systeme ist sie bereits installiert.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-115">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="f7ae0-116">Installieren Sie Windows Management Framework (WMF) 4.0 oder höher auf Windows 7 und Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-116">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="f7ae0-117">ZIP</span><span class="sxs-lookup"><span data-stu-id="f7ae0-117">ZIP</span></span>

<span data-ttu-id="f7ae0-118">Binäre PowerShell ZIP-Archive werden zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-118">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="f7ae0-119">Beachten Sie, dass die Prüfung der Voraussetzungen bei der Benutzung des ZIP-Archivs nicht wie bei dem MSI-Paket durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-119">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="f7ae0-120">Damit das Remoting über WSMan auf Windows-Versionen vor Windows 10 richtig funktioniert, müssen Sie sicherstellen, dass die [Voraussetzungen](#prerequisites) erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-120">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="f7ae0-121">Bereitstellen auf Windows IoT</span><span class="sxs-lookup"><span data-stu-id="f7ae0-121">Deploying on Windows IoT</span></span>

<span data-ttu-id="f7ae0-122">Windows IoT ist bereits in Windows PowerShell enthalten, das Sie zum Bereitstellen von PowerShell Core 6 verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-122">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="f7ae0-123">Erstellen Sie `PSSession` auf dem Zielgerät.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-123">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="f7ae0-124">Kopieren Sie das ZIP-Paket auf das Gerät.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-124">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.1.0-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="f7ae0-125">Stellen Sie eine Verbindung mit dem Gerät her, und erweitern Sie das Archiv.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-125">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   cd u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.1.0-win-arm32.zip
   ```

4. <span data-ttu-id="f7ae0-126">Richten Sie Remoting für PowerShell Core 6 ein.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-126">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   cd .\PowerShell-6.1.0-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="f7ae0-127">Stellen Sie eine Verbindung mit dem PowerShell Core 6-Endpunkt auf dem Gerät her.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-127">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.1.0
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="f7ae0-128">Bereitstellen auf Nano Server</span><span class="sxs-lookup"><span data-stu-id="f7ae0-128">Deploying on Nano Server</span></span>

<span data-ttu-id="f7ae0-129">Diese Anweisungen gehen von einer Version von PowerShell aus, die bereits auf dem Nano Server-Image ausgeführt wird und von dem [Nano Server-Image-Builder](/windows-server/get-started/deploy-nano-server) erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-129">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="f7ae0-130">Nano Server ist ein „monitorloses“ Betriebssystem.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-130">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="f7ae0-131">Core-Binärdateien können auf zwei verschiedene Arten bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-131">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="f7ae0-132">Offline: Binden Sie die Nano Server-VHD ein, und entpacken Sie den Inhalt der ZIP-Datei an dem von Ihnen gewünschten Speicherort in dem eingebundenen Image.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-132">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="f7ae0-133">Online: Übertragen Sie die ZIP-Datei über eine PowerShell-Sitzung, und entpacken Sie sie an dem von Ihnen gewünschten Speicherort.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-133">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="f7ae0-134">In beiden Fällen benötigen Sie das Windows 10 x64 ZIP-Releasepaket, und Sie müssen die Befehle in einer „Administrator“-PowerShell-Instanz ausführen.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-134">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="f7ae0-135">Offline-Bereitstellung von PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="f7ae0-135">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="f7ae0-136">Verwenden Sie Ihr bevorzugtes ZIP-Hilfsprogramm, um das Paket in ein Verzeichnis im eingebundenen Nano Server-Image zu entpacken.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-136">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="f7ae0-137">Heben Sie die Bereitstellung des Images auf, und starten Sie es.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-137">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="f7ae0-138">Stellen Sie eine Verbindung zur Posteingangsinstanz von Windows PowerShell her.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-138">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="f7ae0-139">Befolgen Sie die Anweisungen, um einen Remoting-Endpunkt mithilfe der [„Andere Instanz-Methode“](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-139">Follow the instructions to create a remoting endpoint using the ["another instance technique"](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="f7ae0-140">Onlinebereitstellung von PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="f7ae0-140">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="f7ae0-141">Die folgenden Schritte führen Sie durch die Bereitstellung von PowerShell Core für eine ausgeführte Instanz von Nano Server und die Konfiguration des dazugehörigen Remoteendpunkts.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-141">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="f7ae0-142">Stellen Sie eine Verbindung zur Posteingangsinstanz von Windows PowerShell her.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-142">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="f7ae0-143">Kopieren Sie die Datei in die Nano Server-Instanz.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-143">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="f7ae0-144">Geben Sie die Sitzung ein.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-144">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="f7ae0-145">Extrahieren Sie die ZIP-Datei.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-145">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="f7ae0-146">Befolgen Sie die Anweisungen, wenn Sie auf WSMan basierendes Remoting verwenden möchten, um einen Remoting-Endpunkt mithilfe der [„Andere Instanz-Methode“](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-146">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="f7ae0-147">Anweisungen zum Erstellen eines Remoting-Endpunkts</span><span class="sxs-lookup"><span data-stu-id="f7ae0-147">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="f7ae0-148">PowerShell Core unterstützt das PowerShell-Remotingprotokoll (PSRP) über WSMan und SSH.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-148">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="f7ae0-149">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="f7ae0-149">For more information, see:</span></span>

- <span data-ttu-id="f7ae0-150">[SSH-Remoting in PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="f7ae0-150">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="f7ae0-151">[WSMan-Remoting in PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="f7ae0-151">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="f7ae0-152">Installationsanweisungen für Artefakte</span><span class="sxs-lookup"><span data-stu-id="f7ae0-152">Artifact Installation Instructions</span></span>

<span data-ttu-id="f7ae0-153">Ein Archiv mit CoreCLR-Bestandteilen wird auf jedem CI-Build über [AppVeyor][] veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-153">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="f7ae0-154">So Installieren Sie PowerShell Core über das CoreCLR-Artefakt:</span><span class="sxs-lookup"><span data-stu-id="f7ae0-154">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="f7ae0-155">Laden Sie das ZIP-Paket über die Registerkarte **Artefakte** eines bestimmten Builds herunter.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-155">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="f7ae0-156">Entsperren der ZIP-Datei: Rechtsklick auf Explorer > Eigenschaften. Setzen Sie dann ein Häkchen bei „Zulassen“ und klicken Sie auf „Anwenden“.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-156">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="f7ae0-157">Extrahieren Sie die ZIP-Datei in das Verzeichnis `bin`.</span><span class="sxs-lookup"><span data-stu-id="f7ae0-157">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[Releases]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
