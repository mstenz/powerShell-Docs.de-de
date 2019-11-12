---
title: PowerShell-Remoting über SSH
description: Remoting in PowerShell Core mithilfe von SSH
ms.date: 09/30/2019
ms.openlocfilehash: 0f2fb13010d62dec5b19b373a24a199bff22665d
ms.sourcegitcommit: 36e4c79afda2ce11febd93951e143687245f0b50
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2019
ms.locfileid: "73444364"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="72b40-103">PowerShell-Remoting über SSH</span><span class="sxs-lookup"><span data-stu-id="72b40-103">PowerShell remoting over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="72b40-104">Übersicht</span><span class="sxs-lookup"><span data-stu-id="72b40-104">Overview</span></span>

<span data-ttu-id="72b40-105">In der Regel wird beim PowerShell-Remoting für die Aushandlung der Verbindung und den Datentransport WinRM verwendet.</span><span class="sxs-lookup"><span data-stu-id="72b40-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="72b40-106">SSH ist jetzt für Linux- und Windows-Plattformen verfügbar und ermöglicht echtes PowerShell-Remoting für mehrere Plattformen.</span><span class="sxs-lookup"><span data-stu-id="72b40-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="72b40-107">WinRM bietet ein stabiles Hostingmodell für PowerShell-Remotesitzungen.</span><span class="sxs-lookup"><span data-stu-id="72b40-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="72b40-108">SSH-basiertes Remoting unterstützt derzeit nicht die Remotekonfiguration von Endpunkten und JEA (Just Enough Administration, minimale Verwaltung).</span><span class="sxs-lookup"><span data-stu-id="72b40-108">SSH-based remoting doesn't currently support remote endpoint configuration and Just Enough Administration (JEA).</span></span>

<span data-ttu-id="72b40-109">Mithilfe von SSH-Remoting können Sie grundlegendes PowerShell-Remoting von Sitzungen zwischen Windows- und Linux-Computern ausführen.</span><span class="sxs-lookup"><span data-stu-id="72b40-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux computers.</span></span> <span data-ttu-id="72b40-110">SSH-Remoting erstellt einen PowerShell-Hostprozess als SSH-Subsystem auf dem Zielcomputer.</span><span class="sxs-lookup"><span data-stu-id="72b40-110">SSH remoting creates a PowerShell host process on the target computer as an SSH subsystem.</span></span> <span data-ttu-id="72b40-111">Schließlich implementieren wir ein allgemeines mit WinRM vergleichbares Hostingmodell, um die Endpunktkonfiguration und JEA zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="72b40-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="72b40-112">Die Cmdlets `New-PSSession`, `Enter-PSSession` und `Invoke-Command` verfügen nun über einen neuen Parameter, der diese neue Remotingverbindung unterstützt.</span><span class="sxs-lookup"><span data-stu-id="72b40-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="72b40-113">Um eine Remotesitzung zu erstellen, geben Sie den Zielcomputer über den `HostName`-Parameter an, und fügen Sie über `UserName` den Benutzernamen hinzu.</span><span class="sxs-lookup"><span data-stu-id="72b40-113">To create a remote session, you specify the target computer with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="72b40-114">Wenn Sie die Cmdlets interaktiv ausführen, werden Sie zur Kennworteingabe aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="72b40-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="72b40-115">Sie können auch die SSH-Schlüsselauthentifizierung mithilfe einer privaten Schlüsseldatei mit dem `KeyFilePath`-Parameter verwenden.</span><span class="sxs-lookup"><span data-stu-id="72b40-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="72b40-116">Allgemeine Setupinformationen</span><span class="sxs-lookup"><span data-stu-id="72b40-116">General setup information</span></span>

<span data-ttu-id="72b40-117">PowerShell 6 oder höher und SSH müssen auf allen Computern installiert sein.</span><span class="sxs-lookup"><span data-stu-id="72b40-117">PowerShell 6 or higher, and SSH must be installed on all computers.</span></span> <span data-ttu-id="72b40-118">Installieren Sie den SSH-Client (`ssh.exe`) und -Server (`sshd.exe`), damit Sie Remoting zwischen den Computern nutzen können.</span><span class="sxs-lookup"><span data-stu-id="72b40-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the computers.</span></span> <span data-ttu-id="72b40-119">OpenSSH für Windows ist jetzt im Windows 10-Build 1809 sowie in Windows Server 2019 verfügbar.</span><span class="sxs-lookup"><span data-stu-id="72b40-119">OpenSSH for Windows is now available in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="72b40-120">Weitere Informationen finden Sie unter [Installation von OpenSSH für Windows Server 2019 und Windows 10](/windows-server/administration/openssh/openssh_overview).</span><span class="sxs-lookup"><span data-stu-id="72b40-120">For more information, see [Manage Windows with OpenSSH](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="72b40-121">Installieren Sie für Linux SSH, einschließlich SSHD-Server, entsprechend Ihrer Plattform.</span><span class="sxs-lookup"><span data-stu-id="72b40-121">For Linux, install SSH, including sshd server, that's appropriate for your platform.</span></span> <span data-ttu-id="72b40-122">Sie müssen auch PowerShell über GitHub installieren, um das SSH-Remotingfeature zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="72b40-122">You also need to install PowerShell from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="72b40-123">Der SSH-Server muss konfiguriert werden, um ein SSH-Subsystem zum Hosten eines PowerShell-Prozesses auf dem Remotecomputer zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="72b40-123">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote computer.</span></span> <span data-ttu-id="72b40-124">Sie müssen auch eine **kennwort-** oder **schlüsselbasierte** Authentifizierung konfigurieren und aktivieren.</span><span class="sxs-lookup"><span data-stu-id="72b40-124">And, you must enable **password** or **key-based** authentication.</span></span>

## <a name="set-up-on-a-windows-computer"></a><span data-ttu-id="72b40-125">Einrichten auf einem Windows-Computer</span><span class="sxs-lookup"><span data-stu-id="72b40-125">Set up on a Windows computer</span></span>

1. <span data-ttu-id="72b40-126">Weitere Informationen zur Installation der neuesten Version von PowerShell finden Sie unter [Installieren von PowerShell Core unter Windows](../../install/installing-powershell-core-on-windows.md#msi).</span><span class="sxs-lookup"><span data-stu-id="72b40-126">Install the latest version of PowerShell, see [Installing PowerShell Core on Windows](../../install/installing-powershell-core-on-windows.md#msi).</span></span>

   <span data-ttu-id="72b40-127">Sie können bestätigen, dass PowerShell SSH-Remoting unterstützt, indem Sie die `New-PSSession`-Parametersätze auflisten.</span><span class="sxs-lookup"><span data-stu-id="72b40-127">You can confirm that PowerShell has SSH remoting support by listing the `New-PSSession` parameter sets.</span></span> <span data-ttu-id="72b40-128">Sie werden sehen, dass die Namen einiger Parametersätze mit **SSH** beginnen.</span><span class="sxs-lookup"><span data-stu-id="72b40-128">You'll notice there are parameter set names that begin with **SSH**.</span></span> <span data-ttu-id="72b40-129">Diese Parametersätze enthalten **SSH**-Parameter.</span><span class="sxs-lookup"><span data-stu-id="72b40-129">Those parameter sets include **SSH** parameters.</span></span>

   ```powershell
   (Get-Command New-PSSession).ParameterSets.Name
   ```

   ```Output
   Name
   ----
   SSHHost
   SSHHostHashParam
   ```

1. <span data-ttu-id="72b40-130">Installieren Sie die neueste Win32-OpenSSH.</span><span class="sxs-lookup"><span data-stu-id="72b40-130">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="72b40-131">Weitere Installationsanweisungen finden Sie unter [Getting started with OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse) (Erste Schritte mit OpenSSH).</span><span class="sxs-lookup"><span data-stu-id="72b40-131">For installation instructions, see [Getting started with OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>

   > [!NOTE]
   > <span data-ttu-id="72b40-132">Wenn Sie PowerShell als Standardshell für OpenSSH festlegen möchten, finden Sie weitere Informationen unter [Konfigurieren der Standardshell für OpenSSH in Windows](/windows-server/administration/openssh/openssh_server_configuration).</span><span class="sxs-lookup"><span data-stu-id="72b40-132">If you want to set PowerShell as the default shell for OpenSSH, see [Configuring Windows for OpenSSH](/windows-server/administration/openssh/openssh_server_configuration).</span></span>

1. <span data-ttu-id="72b40-133">Bearbeiten Sie die `sshd_config`-Datei, die sich hier befindet: `$env:ProgramData\ssh`.</span><span class="sxs-lookup"><span data-stu-id="72b40-133">Edit the `sshd_config` file located at `$env:ProgramData\ssh`.</span></span>

   <span data-ttu-id="72b40-134">Vergewissern Sie sich, dass die Kennwortauthentifizierung aktiviert ist:</span><span class="sxs-lookup"><span data-stu-id="72b40-134">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="72b40-135">Erstellen Sie das SSH-Subsystem, das einen PowerShell-Prozess auf dem Remotecomputer hostet:</span><span class="sxs-lookup"><span data-stu-id="72b40-135">Create the SSH subsystem that hosts a PowerShell process on the remote computer:</span></span>

   ```
   Subsystem powershell c:/progra~1/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   > [!NOTE]
   > <span data-ttu-id="72b40-136">Sie müssen den kurzen Namen von Version 8.3 für alle Dateipfade verwenden, die Leerzeichen enthalten.</span><span class="sxs-lookup"><span data-stu-id="72b40-136">You must use the 8.3 short name for any file paths that contain spaces.</span></span> <span data-ttu-id="72b40-137">Es besteht ein Fehler in OpenSSH für Windows, der verhindert, dass Leerzeichen in ausführbaren Pfaden zu Subsystemen funktionieren.</span><span class="sxs-lookup"><span data-stu-id="72b40-137">There's a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="72b40-138">Weitere Informationen finden Sie in diesem [GitHub-Problem](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="72b40-138">For more information, see this [GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>
   >
   > <span data-ttu-id="72b40-139">Der kurze Name von Version 8.3 für den Ordner `Program Files` unter Windows lautet üblicherweise `Progra~1`.</span><span class="sxs-lookup"><span data-stu-id="72b40-139">The 8.3 short name for the `Program Files` folder in Windows is usually `Progra~1`.</span></span> <span data-ttu-id="72b40-140">Sie können jedoch den folgenden Befehl verwenden, um dies sicherzustellen:</span><span class="sxs-lookup"><span data-stu-id="72b40-140">However, you can use the following command to make sure:</span></span>
   >
   > ```powershell
   > Get-CimInstance Win32_Directory -Filter 'Name="C:\\Program Files"' |
   >   Select-Object EightDotThreeFileName
   > ```
   >
   > ```Output
   > EightDotThreeFileName
   > ---------------------
   > c:\progra~1
   > ```

   <span data-ttu-id="72b40-141">Aktivieren Sie ggf. die Schlüsselauthentifizierung:</span><span class="sxs-lookup"><span data-stu-id="72b40-141">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

   <span data-ttu-id="72b40-142">Weitere Informationen finden Sie unter [OpenSSH-Schlüsselverwaltung](/windows-server/administration/openssh/openssh_keymanagement).</span><span class="sxs-lookup"><span data-stu-id="72b40-142">For more information, see [Managing OpenSSH Keys](/windows-server/administration/openssh/openssh_keymanagement).</span></span>

1. <span data-ttu-id="72b40-143">Starten Sie den **sshd**-Dienst neu.</span><span class="sxs-lookup"><span data-stu-id="72b40-143">Restart the **sshd** service.</span></span>

   ```powershell
   Restart-Service sshd
   ```

1. <span data-ttu-id="72b40-144">Fügen Sie den Pfad der OpenSSH-Installation der Umgebungsvariablen „Path“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="72b40-144">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="72b40-145">Beispiel: `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="72b40-145">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="72b40-146">Durch diesen Eintrag kann die Datei `ssh.exe` gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="72b40-146">This entry allows for the `ssh.exe` to be found.</span></span>

## <a name="set-up-on-an-ubuntu-1604-linux-computer"></a><span data-ttu-id="72b40-147">Einrichten auf einem Linux-Computer unter Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="72b40-147">Set up on an Ubuntu 16.04 Linux computer</span></span>

1. <span data-ttu-id="72b40-148">Weitere Informationen zur Installation der neuesten Version von PowerShell finden Sie unter [Installieren von PowerShell Core unter Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604).</span><span class="sxs-lookup"><span data-stu-id="72b40-148">Install the latest version of PowerShell, see [Installing PowerShell Core on Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604).</span></span>
1. <span data-ttu-id="72b40-149">Installieren Sie [Ubuntu OpenSSH Server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).</span><span class="sxs-lookup"><span data-stu-id="72b40-149">Install [Ubuntu OpenSSH Server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. <span data-ttu-id="72b40-150">Bearbeiten Sie die Datei `sshd_config` unter `/etc/ssh`.</span><span class="sxs-lookup"><span data-stu-id="72b40-150">Edit the `sshd_config` file at location `/etc/ssh`.</span></span>

   <span data-ttu-id="72b40-151">Vergewissern Sie sich, dass die Kennwortauthentifizierung aktiviert ist:</span><span class="sxs-lookup"><span data-stu-id="72b40-151">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="72b40-152">Fügen Sie einen Eintrag für das PowerShell-Subsystem hinzu:</span><span class="sxs-lookup"><span data-stu-id="72b40-152">Add a PowerShell subsystem entry:</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   <span data-ttu-id="72b40-153">Aktivieren Sie ggf. die Schlüsselauthentifizierung:</span><span class="sxs-lookup"><span data-stu-id="72b40-153">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="72b40-154">Starten Sie den **sshd**-Dienst neu.</span><span class="sxs-lookup"><span data-stu-id="72b40-154">Restart the **sshd** service.</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-a-macos-computer"></a><span data-ttu-id="72b40-155">Einrichten auf einem macOS-Computer</span><span class="sxs-lookup"><span data-stu-id="72b40-155">Set up on a macOS computer</span></span>

1. <span data-ttu-id="72b40-156">Weitere Informationen zur Installation der neuesten Version von PowerShell finden Sie unter [Installieren von PowerShell Core unter macOS](../../install/installing-powershell-core-on-macos.md).</span><span class="sxs-lookup"><span data-stu-id="72b40-156">Install the latest version of PowerShell, see [Installing PowerShell Core on macOS](../../install/installing-powershell-core-on-macos.md).</span></span>

   <span data-ttu-id="72b40-157">Vergewissern Sie sich, dass SSH-Remoting aktiviert ist, indem Sie die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="72b40-157">Make sure SSH Remoting is enabled by following these steps:</span></span>

   1. <span data-ttu-id="72b40-158">Öffnen Sie `System Preferences`.</span><span class="sxs-lookup"><span data-stu-id="72b40-158">Open `System Preferences`.</span></span>
   1. <span data-ttu-id="72b40-159">Klicken Sie auf `Sharing`.</span><span class="sxs-lookup"><span data-stu-id="72b40-159">Click on `Sharing`.</span></span>
   1. <span data-ttu-id="72b40-160">Aktivieren Sie `Remote Login`, um `Remote Login: On` festzulegen.</span><span class="sxs-lookup"><span data-stu-id="72b40-160">Check `Remote Login` to set `Remote Login: On`.</span></span>
   1. <span data-ttu-id="72b40-161">Erteilen Sie den entsprechenden Benutzern Zugriff.</span><span class="sxs-lookup"><span data-stu-id="72b40-161">Allow access to the appropriate users.</span></span>

1. <span data-ttu-id="72b40-162">Bearbeiten Sie die Datei `sshd_config` unter `/private/etc/ssh/sshd_config`.</span><span class="sxs-lookup"><span data-stu-id="72b40-162">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`.</span></span>

   <span data-ttu-id="72b40-163">Verwenden Sie einen Text-Editor, z.B. **nano**:</span><span class="sxs-lookup"><span data-stu-id="72b40-163">Use a text editor such as **nano**:</span></span>

   ```bash
   sudo nano /private/etc/ssh/sshd_config
   ```

   <span data-ttu-id="72b40-164">Vergewissern Sie sich, dass die Kennwortauthentifizierung aktiviert ist:</span><span class="sxs-lookup"><span data-stu-id="72b40-164">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="72b40-165">Fügen Sie einen Eintrag für das PowerShell-Subsystem hinzu:</span><span class="sxs-lookup"><span data-stu-id="72b40-165">Add a PowerShell subsystem entry:</span></span>

   ```
   Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   <span data-ttu-id="72b40-166">Aktivieren Sie ggf. die Schlüsselauthentifizierung:</span><span class="sxs-lookup"><span data-stu-id="72b40-166">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="72b40-167">Starten Sie den **sshd**-Dienst neu.</span><span class="sxs-lookup"><span data-stu-id="72b40-167">Restart the **sshd** service.</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="72b40-168">Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="72b40-168">Authentication</span></span>

<span data-ttu-id="72b40-169">PowerShell-Remoting über SSH basiert auf dem Authentifizierungsaustausch zwischen dem SSH-Client und dem SSH-Dienst und implementiert selbst keine Authentifizierungsschemas.</span><span class="sxs-lookup"><span data-stu-id="72b40-169">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and doesn't implement any authentication schemes itself.</span></span> <span data-ttu-id="72b40-170">Infolgedessen werden alle konfigurierten Authentifizierungsschemas, einschließlich der mehrstufigen Authentifizierung, von SSH und unabhängig von PowerShell verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="72b40-170">The result is that any configured authentication schemes including multi-factor authentication are handled by SSH and independent of PowerShell.</span></span> <span data-ttu-id="72b40-171">Sie können den SSH-Dienst beispielsweise für die Authentifizierung mit öffentlichen Schlüsseln oder die Verwendung eines Einmalkennworts zur Erhöhung der Sicherheit konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="72b40-171">For example, you can configure the SSH service to require public key authentication and a one-time password for added security.</span></span> <span data-ttu-id="72b40-172">Die Konfiguration einer mehrstufigen Authentifizierung wird in dieser Dokumentation nicht beschrieben.</span><span class="sxs-lookup"><span data-stu-id="72b40-172">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span> <span data-ttu-id="72b40-173">Bevor Sie versuchen, eine mehrstufige Authentifizierung mit PowerShell-Remoting zu verwenden, informieren Sie sich in der Dokumentation für SSH, wie Sie eine mehrstufige Authentifizierung richtig konfigurieren, und testen Sie, ob diese außerhalb von PowerShell funktioniert.</span><span class="sxs-lookup"><span data-stu-id="72b40-173">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="72b40-174">Beispiel für das PowerShell-Remoting</span><span class="sxs-lookup"><span data-stu-id="72b40-174">PowerShell remoting example</span></span>

<span data-ttu-id="72b40-175">Sie können das Remoting am einfachsten auf einem einzelnen Computer testen.</span><span class="sxs-lookup"><span data-stu-id="72b40-175">The easiest way to test remoting is to try it on a single computer.</span></span> <span data-ttu-id="72b40-176">In diesem Beispiel haben wir eine Remotesitzung mit demselben Linux-Computer erstellt.</span><span class="sxs-lookup"><span data-stu-id="72b40-176">In this example, we create a remote session back to the same Linux computer.</span></span> <span data-ttu-id="72b40-177">Wir verwenden PowerShell-Cmdlets interaktiv, damit wir Eingabeaufforderungen von SSH sehen, die zum Überprüfen des Hostcomputers und zur Kennworteingabe auffordern.</span><span class="sxs-lookup"><span data-stu-id="72b40-177">We're using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="72b40-178">Sie können dies auch auf einem Windows-Computer durchführen, um sicherzustellen, dass das Remoting funktioniert.</span><span class="sxs-lookup"><span data-stu-id="72b40-178">You can do the same thing on a Windows computer to ensure remoting is working.</span></span> <span data-ttu-id="72b40-179">Verwenden Sie dann Remoting zwischen Computern, indem Sie den Hostnamen ändern.</span><span class="sxs-lookup"><span data-stu-id="72b40-179">Then, remote between computers by changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```Output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```Output
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```Output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~16.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```Output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1
```

```powershell
#
# Linux to Windows
#
Enter-PSSession -HostName WinVM1 -UserName PTestName
```

```Output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```Output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```Output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```Output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```Output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```Output
[WinVM2]: PS C:\Users\PSRemoteUser\Documents> $PSVersionTable

Name                           Value
----                           -----
PSEdition                      Core
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
SerializationVersion           1.1.0.1
BuildVersion                   3.0.0.0
CLRVersion
PSVersion                      6.0.0-alpha
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
GitCommitId                    v6.0.0-alpha.17


[WinVM2]: PS C:\Users\PSRemoteUser\Documents>
```

### <a name="known-issues"></a><span data-ttu-id="72b40-180">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="72b40-180">Known issues</span></span>

<span data-ttu-id="72b40-181">Der Befehl **sudo** funktioniert bei Remotesitzungen auf Linux-Computern nicht.</span><span class="sxs-lookup"><span data-stu-id="72b40-181">The **sudo** command doesn't work in a remote session to a Linux computer.</span></span>

## <a name="see-also"></a><span data-ttu-id="72b40-182">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="72b40-182">See also</span></span>

[<span data-ttu-id="72b40-183">Installieren von PowerShell Core unter Linux</span><span class="sxs-lookup"><span data-stu-id="72b40-183">Installing PowerShell Core on Linux</span></span>](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[<span data-ttu-id="72b40-184">Installieren von PowerShell Core unter macOS</span><span class="sxs-lookup"><span data-stu-id="72b40-184">Installing PowerShell Core on macOS</span></span>](../../install/installing-powershell-core-on-macos.md)

[<span data-ttu-id="72b40-185">Installing PowerShell Core on Windows (Installieren von PowerShell Core unter Windows)</span><span class="sxs-lookup"><span data-stu-id="72b40-185">Installing PowerShell Core on Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="72b40-186">Installation von OpenSSH für Windows Server 2019 und Windows 10</span><span class="sxs-lookup"><span data-stu-id="72b40-186">Manage Windows with OpenSSH</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="72b40-187">OpenSSH-Schlüsselverwaltung</span><span class="sxs-lookup"><span data-stu-id="72b40-187">Managing OpenSSH Keys</span></span>](/windows-server/administration/openssh/openssh_keymanagement)

[<span data-ttu-id="72b40-188">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="72b40-188">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
