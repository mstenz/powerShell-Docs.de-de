---
title: Installieren von PowerShell Core unter Windows
description: Informationen zur Installation von PowerShell Core unter Windows
ms.date: 08/06/2018
ms.openlocfilehash: c06eba06e376c3f795ab9c0fae9270cf6cf8f2ce
ms.sourcegitcommit: 36e4c79afda2ce11febd93951e143687245f0b50
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2019
ms.locfileid: "73444458"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="2b81e-103">Installieren von PowerShell Core unter Windows</span><span class="sxs-lookup"><span data-stu-id="2b81e-103">Installing PowerShell Core on Windows</span></span>

<span data-ttu-id="2b81e-104">Es gibt mehrere Möglichkeiten zum Installieren von PowerShell Core unter Windows.</span><span class="sxs-lookup"><span data-stu-id="2b81e-104">There are multiple ways to install PowerShell Core in Windows.</span></span>

> [!TIP]
> <span data-ttu-id="2b81e-105">Wenn Sie das [.NET Core SDK](/dotnet/core/sdk) bereits installiert haben, können Sie PowerShell einfach als [globales .NET-Tool](/dotnet/core/tools/global-tools) installieren.</span><span class="sxs-lookup"><span data-stu-id="2b81e-105">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it’s easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>
>
> ```
> dotnet tool install --global PowerShell
> ```

## <a name="prerequisites"></a><span data-ttu-id="2b81e-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="2b81e-106">Prerequisites</span></span>

<span data-ttu-id="2b81e-107">Zum Aktivieren des PowerShell-Remoting über WSMan müssen die folgenden Voraussetzungen erfüllt sein:</span><span class="sxs-lookup"><span data-stu-id="2b81e-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="2b81e-108">[Universal C-Runtime](https://www.microsoft.com/download/details.aspx?id=50410) muss auf Windows-Versionen vor Windows 10 installiert werden.</span><span class="sxs-lookup"><span data-stu-id="2b81e-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="2b81e-109">Sie ist über einen direkten Download oder durch ein Windows-Update verfügbar.</span><span class="sxs-lookup"><span data-stu-id="2b81e-109">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="2b81e-110">Auf vollständig gepatchten (inklusive optionaler Pakete), unterstützten Systeme ist sie bereits installiert.</span><span class="sxs-lookup"><span data-stu-id="2b81e-110">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="2b81e-111">Installieren Sie Windows Management Framework (WMF) 4.0 oder höher auf Windows 7 und Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="2b81e-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="2b81e-112">Weitere Informationen zu WMF erhalten Sie in der [WMF-Übersicht](/powershell/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="2b81e-112">For more information about WMF, see [WMF Overview](/powershell/wmf/overview).</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="2b81e-113"><a id="msi" />Installieren des MSI-Pakets</span><span class="sxs-lookup"><span data-stu-id="2b81e-113"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="2b81e-114">Installieren Sie PowerShell auf einem Windows-Client oder Windows Server (funktioniert auf Windows 7 SP1, Windows Server 2008 R2 und höher), indem Sie das MSI-Paket von unserer GitHub [Freigaben][releases]-Seite herunterladen.</span><span class="sxs-lookup"><span data-stu-id="2b81e-114">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="2b81e-115">Scrollen Sie nach unten zum Abschnitt **Assets** des Release, das Sie installieren möchten.</span><span class="sxs-lookup"><span data-stu-id="2b81e-115">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="2b81e-116">Der Abschnitt „Assets“ ist möglicherweise reduziert, sodass Sie klicken müssen, um ihn zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="2b81e-116">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="2b81e-117">Die MSI-Datei sieht wie folgt aus: `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="2b81e-117">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="2b81e-118">Sobald sie heruntergeladen wurde, führen Sie den Installer mit einem Doppelklick aus und befolgen die Anweisungen.</span><span class="sxs-lookup"><span data-stu-id="2b81e-118">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="2b81e-119">Das Installationsprogramm erstellt eine Verknüpfung im Windows-Startmenü.</span><span class="sxs-lookup"><span data-stu-id="2b81e-119">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="2b81e-120">Das Paket wird standardmäßig unter `$env:ProgramFiles\PowerShell\<version>` installiert</span><span class="sxs-lookup"><span data-stu-id="2b81e-120">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="2b81e-121">Sie können PowerShell über das Startmenü oder über `$env:ProgramFiles\PowerShell\<version>\pwsh.exe` starten</span><span class="sxs-lookup"><span data-stu-id="2b81e-121">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="2b81e-122">Administrative Installation über die Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="2b81e-122">Administrative install from the command line</span></span>

<span data-ttu-id="2b81e-123">MSI-Pakete können über die Befehlszeile installiert werden.</span><span class="sxs-lookup"><span data-stu-id="2b81e-123">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="2b81e-124">Dies ermöglicht es Administratoren, Pakete ohne Benutzerinteraktion bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="2b81e-124">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="2b81e-125">Das MSI-Paket für PowerShell enthält die folgenden Eigenschaften zum Steuern der Installationsoptionen:</span><span class="sxs-lookup"><span data-stu-id="2b81e-125">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="2b81e-126">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** – Diese Eigenschaft steuert die Option zum Hinzufügen des Elements **PowerShell öffnen** zum Kontextmenü im Windows-Explorer.</span><span class="sxs-lookup"><span data-stu-id="2b81e-126">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="2b81e-127">**ENABLE_PSREMOTING** – Diese Eigenschaft steuert die Option zum Aktivieren von PowerShell-Remoting während der Installation.</span><span class="sxs-lookup"><span data-stu-id="2b81e-127">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="2b81e-128">**REGISTER_MANIFEST** – Diese Eigenschaft steuert die Option zum Registrieren des Manifests für Windows-Ereignisprotokollierung.</span><span class="sxs-lookup"><span data-stu-id="2b81e-128">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="2b81e-129">Die folgenden Beispiele zeigen, wie PowerShell Core im Hintergrund installiert wird, wobei alle Installationsoptionen aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="2b81e-129">The following examples shows how to silently install PowerShell Core with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="2b81e-130">Eine vollständige Liste der Befehlszeilenoptionen für „Msiexec.exe“ finden Sie unter [Befehlszeilenoptionen](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="2b81e-130">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="2b81e-131"><a id="zip" />Installieren des ZIP-Pakets</span><span class="sxs-lookup"><span data-stu-id="2b81e-131"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="2b81e-132">Binäre PowerShell ZIP-Archive werden zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="2b81e-132">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="2b81e-133">Beachten Sie, dass die Prüfung der Voraussetzungen bei der Benutzung des ZIP-Archivs nicht wie bei dem MSI-Paket durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2b81e-133">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="2b81e-134">Damit Remoting über WSMan einwandfrei funktioniert, müssen Sie die [Voraussetzungen](#prerequisites) erfüllt haben.</span><span class="sxs-lookup"><span data-stu-id="2b81e-134">For remoting over WSMan to work properly, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="2b81e-135">Bereitstellen auf Windows IoT</span><span class="sxs-lookup"><span data-stu-id="2b81e-135">Deploying on Windows IoT</span></span>

<span data-ttu-id="2b81e-136">Windows IoT ist bereits in Windows PowerShell enthalten, das Sie zum Bereitstellen von PowerShell Core 6 verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="2b81e-136">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="2b81e-137">Erstellen Sie `PSSession` auf dem Zielgerät.</span><span class="sxs-lookup"><span data-stu-id="2b81e-137">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="2b81e-138">Kopieren Sie das ZIP-Paket auf das Gerät.</span><span class="sxs-lookup"><span data-stu-id="2b81e-138">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="2b81e-139">Stellen Sie eine Verbindung mit dem Gerät her, und erweitern Sie das Archiv.</span><span class="sxs-lookup"><span data-stu-id="2b81e-139">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="2b81e-140">Richten Sie Remoting für PowerShell Core 6 ein.</span><span class="sxs-lookup"><span data-stu-id="2b81e-140">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="2b81e-141">Stellen Sie eine Verbindung mit dem PowerShell Core 6-Endpunkt auf dem Gerät her.</span><span class="sxs-lookup"><span data-stu-id="2b81e-141">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="2b81e-142">Bereitstellen auf Nano Server</span><span class="sxs-lookup"><span data-stu-id="2b81e-142">Deploying on Nano Server</span></span>

<span data-ttu-id="2b81e-143">Diese Anweisungen gehen von einer Version von PowerShell aus, die bereits auf dem Nano Server-Image ausgeführt wird und von dem [Nano Server-Image-Builder](/windows-server/get-started/deploy-nano-server) erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="2b81e-143">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="2b81e-144">Nano Server ist ein „monitorloses“ Betriebssystem.</span><span class="sxs-lookup"><span data-stu-id="2b81e-144">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="2b81e-145">Core-Binärdateien können auf zwei verschiedene Arten bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="2b81e-145">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="2b81e-146">Offline: Binden Sie die Nano Server-VHD ein, und entpacken Sie den Inhalt der ZIP-Datei an dem von Ihnen gewünschten Speicherort in dem eingebundenen Image.</span><span class="sxs-lookup"><span data-stu-id="2b81e-146">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="2b81e-147">Online: Übertragen Sie die ZIP-Datei über eine PowerShell-Sitzung, und entpacken Sie sie an dem von Ihnen gewünschten Speicherort.</span><span class="sxs-lookup"><span data-stu-id="2b81e-147">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="2b81e-148">In beiden Fällen benötigen Sie das Windows 10 x64 ZIP-Releasepaket, und Sie müssen die Befehle in einer „Administrator“-PowerShell-Instanz ausführen.</span><span class="sxs-lookup"><span data-stu-id="2b81e-148">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="2b81e-149">Offline-Bereitstellung von PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="2b81e-149">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="2b81e-150">Verwenden Sie Ihr bevorzugtes ZIP-Hilfsprogramm, um das Paket in ein Verzeichnis im eingebundenen Nano Server-Image zu entpacken.</span><span class="sxs-lookup"><span data-stu-id="2b81e-150">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="2b81e-151">Heben Sie die Bereitstellung des Images auf, und starten Sie es.</span><span class="sxs-lookup"><span data-stu-id="2b81e-151">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="2b81e-152">Stellen Sie eine Verbindung zur Posteingangsinstanz von Windows PowerShell her.</span><span class="sxs-lookup"><span data-stu-id="2b81e-152">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="2b81e-153">Befolgen Sie die Anweisungen, um einen Remoting-Endpunkt mithilfe der [„Andere Instanz-Methode“](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2b81e-153">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="2b81e-154">Onlinebereitstellung von PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="2b81e-154">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="2b81e-155">Die folgenden Schritte führen Sie durch die Bereitstellung von PowerShell Core für eine ausgeführte Instanz von Nano Server und die Konfiguration des dazugehörigen Remoteendpunkts.</span><span class="sxs-lookup"><span data-stu-id="2b81e-155">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="2b81e-156">Stellen Sie eine Verbindung zur Posteingangsinstanz von Windows PowerShell her.</span><span class="sxs-lookup"><span data-stu-id="2b81e-156">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="2b81e-157">Kopieren Sie die Datei in die Nano Server-Instanz.</span><span class="sxs-lookup"><span data-stu-id="2b81e-157">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="2b81e-158">Geben Sie die Sitzung ein.</span><span class="sxs-lookup"><span data-stu-id="2b81e-158">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="2b81e-159">Extrahieren Sie die ZIP-Datei.</span><span class="sxs-lookup"><span data-stu-id="2b81e-159">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="2b81e-160">Befolgen Sie die Anweisungen, wenn Sie auf WSMan basierendes Remoting verwenden möchten, um einen Remoting-Endpunkt mithilfe der [„Andere Instanz-Methode“](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2b81e-160">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="2b81e-161">Vorgehensweise zum Erstellen eines Remoting-Endpunkts</span><span class="sxs-lookup"><span data-stu-id="2b81e-161">How to create a remoting endpoint</span></span>

<span data-ttu-id="2b81e-162">PowerShell Core unterstützt das PowerShell-Remotingprotokoll (PSRP) über WSMan und SSH.</span><span class="sxs-lookup"><span data-stu-id="2b81e-162">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="2b81e-163">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="2b81e-163">For more information, see:</span></span>

- <span data-ttu-id="2b81e-164">[SSH-Remoting in PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="2b81e-164">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="2b81e-165">[WSMan-Remoting in PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="2b81e-165">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
