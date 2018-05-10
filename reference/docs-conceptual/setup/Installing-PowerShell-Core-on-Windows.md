# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="404b1-101">Installieren von PowerShell Core unter Windows</span><span class="sxs-lookup"><span data-stu-id="404b1-101">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="404b1-102">MSI</span><span class="sxs-lookup"><span data-stu-id="404b1-102">MSI</span></span>

<span data-ttu-id="404b1-103">Installieren Sie PowerShell auf einem Windows-Client oder Windows Server (funktioniert auf Windows 7 SP1, Windows Server 2008 R2 und höher), indem Sie das MSI-Paket von unserer GitHub [Freigaben][]-Seite herunterladen.</span><span class="sxs-lookup"><span data-stu-id="404b1-103">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="404b1-104">Die MSI-Datei sieht wie folgt aus: `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="404b1-104">The MSI file looks like this - `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="404b1-105">Sobald sie heruntergeladen wurde, führen Sie den Installer mit einem Doppelklick aus und befolgen die Anweisungen.</span><span class="sxs-lookup"><span data-stu-id="404b1-105">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="404b1-106">Bei der Installation wird im Startmenü eine Verknüpfung erstellt.</span><span class="sxs-lookup"><span data-stu-id="404b1-106">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="404b1-107">Das Paket wird standardmäßig unter `$env:ProgramFiles\PowerShell\` installiert</span><span class="sxs-lookup"><span data-stu-id="404b1-107">By default the package is installed to `$env:ProgramFiles\PowerShell\`</span></span>
- <span data-ttu-id="404b1-108">Sie können PowerShell über das Startmenü oder über `$env:ProgramFiles\PowerShell\pwsh.exe` starten</span><span class="sxs-lookup"><span data-stu-id="404b1-108">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="404b1-109">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="404b1-109">Prerequisites</span></span>

<span data-ttu-id="404b1-110">Zum Aktivieren des PowerShell-Remoting über WSMan müssen die folgenden Voraussetzungen erfüllt sein:</span><span class="sxs-lookup"><span data-stu-id="404b1-110">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="404b1-111">[Universal C-Runtime](https://www.microsoft.com/download/details.aspx?id=50410) muss auf Windows-Versionen vor Windows 10 installiert werden.</span><span class="sxs-lookup"><span data-stu-id="404b1-111">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="404b1-112">Sie ist über einen direkten Download oder durch ein Windows-Update verfügbar.</span><span class="sxs-lookup"><span data-stu-id="404b1-112">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="404b1-113">Auf vollständig gepatchten (inklusive optionaler Pakete), unterstützten Systeme ist sie bereits installiert.</span><span class="sxs-lookup"><span data-stu-id="404b1-113">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="404b1-114">Installieren Sie Windows Management Framework (WMF) 4.0 oder höher auf Windows 7 und Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="404b1-114">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="404b1-115">ZIP</span><span class="sxs-lookup"><span data-stu-id="404b1-115">ZIP</span></span>

<span data-ttu-id="404b1-116">Binäre PowerShell ZIP-Archive werden zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="404b1-116">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="404b1-117">Beachten Sie, dass die Prüfung der Voraussetzungen bei der Benutzung des ZIP-Archivs nicht wie bei dem MSI-Paket durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="404b1-117">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="404b1-118">Damit das Remoting über WSMan auf Windows-Versionen vor Windows 10 richtig funktioniert, müssen Sie sicherstellen, dass die [Voraussetzungen](#prerequisites) erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="404b1-118">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="404b1-119">Bereitstellen auf Windows IoT</span><span class="sxs-lookup"><span data-stu-id="404b1-119">Deploying on Windows IoT</span></span>

<span data-ttu-id="404b1-120">Windows IoT ist bereits in Windows PowerShell enthalten, das Sie zum Bereitstellen von PowerShell Core 6 verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="404b1-120">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="404b1-121">Erstellen Sie `PSSession` auf dem Zielgerät.</span><span class="sxs-lookup"><span data-stu-id="404b1-121">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="404b1-122">Kopieren Sie das ZIP-Paket auf das Gerät.</span><span class="sxs-lookup"><span data-stu-id="404b1-122">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.0.2-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="404b1-123">Stellen Sie eine Verbindung mit dem Gerät her, und erweitern Sie das Archiv.</span><span class="sxs-lookup"><span data-stu-id="404b1-123">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   cd u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.0.2-win-arm32.zip
   ```

4. <span data-ttu-id="404b1-124">Richten Sie Remoting für PowerShell Core 6 ein.</span><span class="sxs-lookup"><span data-stu-id="404b1-124">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   cd .\PowerShell-6.0.2-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="404b1-125">Stellen Sie eine Verbindung mit dem PowerShell Core 6-Endpunkt auf dem Gerät her.</span><span class="sxs-lookup"><span data-stu-id="404b1-125">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.0.2
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="404b1-126">Bereitstellen auf Nano Server</span><span class="sxs-lookup"><span data-stu-id="404b1-126">Deploying on Nano Server</span></span>

<span data-ttu-id="404b1-127">Diese Anweisungen gehen von einer Version von PowerShell aus, die bereits auf dem Nano Server-Image ausgeführt wird und von dem [Nano Server-Image-Builder](/windows-server/get-started/deploy-nano-server) erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="404b1-127">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="404b1-128">Nano Server ist ein „monitorloses“ Betriebssystem.</span><span class="sxs-lookup"><span data-stu-id="404b1-128">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="404b1-129">Core-Binärdateien können auf zwei verschiedene Arten bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="404b1-129">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="404b1-130">Offline: Binden Sie die Nano Server-VHD ein, und entpacken Sie den Inhalt der ZIP-Datei an dem von Ihnen gewünschten Speicherort in dem eingebundenen Image.</span><span class="sxs-lookup"><span data-stu-id="404b1-130">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="404b1-131">Online: Übertragen Sie die ZIP-Datei über eine PowerShell-Sitzung, und entpacken Sie sie an dem von Ihnen gewünschten Speicherort.</span><span class="sxs-lookup"><span data-stu-id="404b1-131">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="404b1-132">In beiden Fällen benötigen Sie das Windows 10 x64 ZIP-Releasepaket, und Sie müssen die Befehle in einer „Administrator“-PowerShell-Instanz ausführen.</span><span class="sxs-lookup"><span data-stu-id="404b1-132">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="404b1-133">Offline-Bereitstellung von PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="404b1-133">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="404b1-134">Verwenden Sie Ihr bevorzugtes ZIP-Hilfsprogramm, um das Paket in ein Verzeichnis im eingebundenen Nano Server-Image zu entpacken.</span><span class="sxs-lookup"><span data-stu-id="404b1-134">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="404b1-135">Heben Sie die Bereitstellung des Images auf, und starten Sie es.</span><span class="sxs-lookup"><span data-stu-id="404b1-135">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="404b1-136">Stellen Sie eine Verbindung zur Posteingangsinstanz von Windows PowerShell her.</span><span class="sxs-lookup"><span data-stu-id="404b1-136">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="404b1-137">Befolgen Sie die Anweisungen, um einen Remoting-Endpunkt mithilfe der [„Andere Instanz-Methode“](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="404b1-137">Follow the instructions to create a remoting endpoint using the ["another instance technique"](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="404b1-138">Onlinebereitstellung von PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="404b1-138">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="404b1-139">Die folgenden Schritte führen Sie durch die Bereitstellung von PowerShell Core für eine ausgeführte Instanz von Nano Server und die Konfiguration des dazugehörigen Remoteendpunkts.</span><span class="sxs-lookup"><span data-stu-id="404b1-139">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="404b1-140">Stellen Sie eine Verbindung zur Posteingangsinstanz von Windows PowerShell her.</span><span class="sxs-lookup"><span data-stu-id="404b1-140">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="404b1-141">Kopieren Sie die Datei in die Nano Server-Instanz.</span><span class="sxs-lookup"><span data-stu-id="404b1-141">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="404b1-142">Geben Sie die Sitzung ein.</span><span class="sxs-lookup"><span data-stu-id="404b1-142">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="404b1-143">Extrahieren Sie die ZIP-Datei.</span><span class="sxs-lookup"><span data-stu-id="404b1-143">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="404b1-144">Befolgen Sie die Anweisungen, wenn Sie auf WSMan basierendes Remoting verwenden möchten, um einen Remoting-Endpunkt mithilfe der [„Andere Instanz-Methode“](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="404b1-144">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="404b1-145">Anweisungen zum Erstellen eines Remoting-Endpunkts</span><span class="sxs-lookup"><span data-stu-id="404b1-145">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="404b1-146">PowerShell Core unterstützt das PowerShell-Remotingprotokoll (PSRP) über WSMan und SSH.</span><span class="sxs-lookup"><span data-stu-id="404b1-146">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="404b1-147">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="404b1-147">For more information, see:</span></span>

- <span data-ttu-id="404b1-148">[SSH-Remoting in PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="404b1-148">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="404b1-149">[WSMan-Remoting in PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="404b1-149">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="404b1-150">Installationsanweisungen für Artefakte</span><span class="sxs-lookup"><span data-stu-id="404b1-150">Artifact Installation Instructions</span></span>

<span data-ttu-id="404b1-151">Ein Archiv mit CoreCLR-Bestandteilen wird auf jedem CI-Build über [AppVeyor][] veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="404b1-151">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="404b1-152">So Installieren Sie PowerShell Core über das CoreCLR-Artefakt:</span><span class="sxs-lookup"><span data-stu-id="404b1-152">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="404b1-153">Laden Sie das ZIP-Paket über die Registerkarte **Artefakte** eines bestimmten Builds herunter.</span><span class="sxs-lookup"><span data-stu-id="404b1-153">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="404b1-154">Entsperren der ZIP-Datei: Rechtsklick auf Explorer > Eigenschaften. Setzen Sie dann ein Häkchen bei „Zulassen“ und klicken Sie auf „Anwenden“.</span><span class="sxs-lookup"><span data-stu-id="404b1-154">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="404b1-155">Extrahieren Sie die ZIP-Datei in das Verzeichnis `bin`.</span><span class="sxs-lookup"><span data-stu-id="404b1-155">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[Freigaben]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell