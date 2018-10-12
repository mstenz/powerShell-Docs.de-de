---
title: PowerShell-Remoting über SSH
description: Remoting in PowerShell Core mithilfe von SSH
ms.date: 08/14/2018
ms.openlocfilehash: 84c3896fe28847beb03e930f933bb4a9dfad397f
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851236"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="9a50f-103">PowerShell-Remoting über SSH</span><span class="sxs-lookup"><span data-stu-id="9a50f-103">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="9a50f-104">Übersicht</span><span class="sxs-lookup"><span data-stu-id="9a50f-104">Overview</span></span>

<span data-ttu-id="9a50f-105">In der Regel wird beim PowerShell-Remoting für die Aushandlung der Verbindung und den Datentransport WinRM verwendet.</span><span class="sxs-lookup"><span data-stu-id="9a50f-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="9a50f-106">SSH ist jetzt für Linux- und Windows-Plattformen verfügbar und ermöglicht echtes PowerShell-Remoting für mehrere Plattformen.</span><span class="sxs-lookup"><span data-stu-id="9a50f-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="9a50f-107">WinRM bietet ein stabiles Hostingmodell für PowerShell-Remotesitzungen.</span><span class="sxs-lookup"><span data-stu-id="9a50f-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="9a50f-108">Diese Implementierung von SSH-basiertem Remoting unterstützt derzeit die Remotekonfiguration von Endpunkten und „Just Enough Administration“ (JEA, minimale Administration) nicht.</span><span class="sxs-lookup"><span data-stu-id="9a50f-108">which this implementation SSH-based remoting doesn't currently support remote endpoint configuration and JEA (Just Enough Administration).</span></span>

<span data-ttu-id="9a50f-109">Mithilfe von SSH-Remoting können Sie grundlegendes PowerShell-Remoting von Sitzungen zwischen Windows- und Linux-Computern ausführen.</span><span class="sxs-lookup"><span data-stu-id="9a50f-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="9a50f-110">SSH-Remoting erstellt einen PowerShell-Hostprozess als SSH-Subsystem auf dem Zielcomputer.</span><span class="sxs-lookup"><span data-stu-id="9a50f-110">SSH Remoting creates a PowerShell host process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="9a50f-111">Schließlich implementieren wir ein allgemeines mit WinRM vergleichbares Hostingmodell, um die Endpunktkonfiguration und JEA zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="9a50f-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="9a50f-112">Die Cmdlets `New-PSSession`, `Enter-PSSession` und `Invoke-Command` verfügen nun über einen neuen Parameter, der diese neue Remotingverbindung unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9a50f-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="9a50f-113">Um eine Remotesitzung zu erstellen, geben Sie den Zielcomputer über den `HostName`-Parameter an, und fügen Sie über `UserName` den Benutzernamen hinzu.</span><span class="sxs-lookup"><span data-stu-id="9a50f-113">To create a remote session, you specify the target machine with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="9a50f-114">Wenn Sie die Cmdlets interaktiv ausführen, werden Sie zur Kennworteingabe aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="9a50f-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="9a50f-115">Sie können auch die SSH-Schlüsselauthentifizierung mithilfe einer privaten Schlüsseldatei mit dem `KeyFilePath`-Parameter verwenden.</span><span class="sxs-lookup"><span data-stu-id="9a50f-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="9a50f-116">Allgemeine Setupinformationen</span><span class="sxs-lookup"><span data-stu-id="9a50f-116">General setup information</span></span>

<span data-ttu-id="9a50f-117">SSH muss auf allen Computern installiert sein.</span><span class="sxs-lookup"><span data-stu-id="9a50f-117">SSH must be installed on all machines.</span></span> <span data-ttu-id="9a50f-118">Installieren Sie den SSH-Client (`ssh.exe`) und -Server (`sshd.exe`), damit Sie Remoting zwischen den Computern nutzen können.</span><span class="sxs-lookup"><span data-stu-id="9a50f-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the machines.</span></span> <span data-ttu-id="9a50f-119">Installieren Sie für Windows [Win32 OpenSSH über GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="9a50f-119">For Windows, install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="9a50f-120">Installieren Sie für Linux SSH (einschließlich SSHD-Server) entsprechend Ihrer Plattform.</span><span class="sxs-lookup"><span data-stu-id="9a50f-120">For Linux, install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="9a50f-121">Sie müssen auch PowerShell Core über GitHub installieren, um das SSH-Remotingfeature zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="9a50f-121">You also need to install PowerShell Core from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="9a50f-122">Der SSH-Server muss konfiguriert werden, um ein SSH-Subsystem zum Hosten eines PowerShell-Prozesses auf dem Remotecomputer zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="9a50f-122">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote machine.</span></span> <span data-ttu-id="9a50f-123">Sie müssen auch eine kennwort- oder schlüsselbasierte Authentifizierung konfigurieren und aktivieren.</span><span class="sxs-lookup"><span data-stu-id="9a50f-123">You also must configure enable password or key-based authentication.</span></span>

## <a name="set-up-on-windows-machine"></a><span data-ttu-id="9a50f-124">Setup auf dem Windows-Computer</span><span class="sxs-lookup"><span data-stu-id="9a50f-124">Set up on Windows Machine</span></span>

1. <span data-ttu-id="9a50f-125">Installieren Sie die neuste Version von [PowerShell Core für Windows](../setup/installing-powershell-core-on-windows.md#msi)</span><span class="sxs-lookup"><span data-stu-id="9a50f-125">Install the latest version of [PowerShell Core for Windows](../setup/installing-powershell-core-on-windows.md#msi)</span></span>

   - <span data-ttu-id="9a50f-126">Anhand der Parameter für `New-PSSession` können Sie bestimmen, ob der Support für SSH-Remoting eingerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="9a50f-126">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="9a50f-127">Installieren Sie den neusten [Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)-Build über GitHub, und verwenden Sie dabei die [Installation](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH).</span><span class="sxs-lookup"><span data-stu-id="9a50f-127">Install the latest [Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases) build from GitHub using the [installation](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH) instructions</span></span>
3. <span data-ttu-id="9a50f-128">Bearbeiten Sie die Datei „sshd_config“ am selben Ort, an dem Sie Win32 OpenSSH installiert haben.</span><span class="sxs-lookup"><span data-stu-id="9a50f-128">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>

   - <span data-ttu-id="9a50f-129">Vergewissern Sie sich, dass die Kennwortauthentifizierung aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="9a50f-129">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6.0.4/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="9a50f-130">Es besteht ein Fehler in OpenSSH für Windows, der verhindert, dass Leerzeichen in ausführbaren Pfaden zu Subsystemen funktionieren.</span><span class="sxs-lookup"><span data-stu-id="9a50f-130">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="9a50f-131">Weitere Informationen finden Sie in [diesem GitHub-Problem](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="9a50f-131">For more information, see [this GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="9a50f-132">Um dieses Problem zu beheben, können Sie eine symbolische Verknüpfung mit dem PowerShell-Installationsverzeichnis herstellen, die keine Leerzeichen enthält:</span><span class="sxs-lookup"><span data-stu-id="9a50f-132">One solution is to create a symlink to the Powershell installation directory that doesn't have spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.4"
     ```

     <span data-ttu-id="9a50f-133">Geben Sie diese anschließend in das Subsystem ein:</span><span class="sxs-lookup"><span data-stu-id="9a50f-133">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="9a50f-134">Aktivieren Sie ggf. die Schlüsselauthentifizierung.</span><span class="sxs-lookup"><span data-stu-id="9a50f-134">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="9a50f-135">Starten Sie den SSHD-Dienst neu.</span><span class="sxs-lookup"><span data-stu-id="9a50f-135">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="9a50f-136">Fügen Sie den Pfad der OpenSSH-Installation der Umgebungsvariablen „Path“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="9a50f-136">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="9a50f-137">Beispiel: `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="9a50f-137">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="9a50f-138">Durch diesen Eintrag kann die Datei „ssh.exe“ gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="9a50f-138">This entry allows for the ssh.exe to be found.</span></span>

## <a name="set-up-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="9a50f-139">Setup auf einem Linux-Computer (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="9a50f-139">Set up on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="9a50f-140">Installieren Sie den neusten Build von [PowerShell Core für Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404) über GitHub.</span><span class="sxs-lookup"><span data-stu-id="9a50f-140">Install the latest [PowerShell Core for Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404) build from GitHub</span></span>
2. <span data-ttu-id="9a50f-141">Installieren Sie ggf. [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html).</span><span class="sxs-lookup"><span data-stu-id="9a50f-141">Install [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="9a50f-142">Bearbeiten Sie die Datei „sshd_config“ unter „/etc/ssh“.</span><span class="sxs-lookup"><span data-stu-id="9a50f-142">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="9a50f-143">Vergewissern Sie sich, dass die Kennwortauthentifizierung aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="9a50f-143">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="9a50f-144">Fügen Sie einen Eintrag für das PowerShell-Subsystem hinzu.</span><span class="sxs-lookup"><span data-stu-id="9a50f-144">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="9a50f-145">Aktivieren Sie ggf. die Schlüsselauthentifizierung.</span><span class="sxs-lookup"><span data-stu-id="9a50f-145">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="9a50f-146">Starten Sie den SSHD-Dienst neu.</span><span class="sxs-lookup"><span data-stu-id="9a50f-146">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a><span data-ttu-id="9a50f-147">Setup auf einem macOS-Computer</span><span class="sxs-lookup"><span data-stu-id="9a50f-147">Set up on MacOS Machine</span></span>

1. <span data-ttu-id="9a50f-148">Installieren Sie den neusten Build von [PowerShell Core für macOS](../setup/installing-powershell-core-on-macos.md).</span><span class="sxs-lookup"><span data-stu-id="9a50f-148">Install the latest [PowerShell Core for MacOS](../setup/installing-powershell-core-on-macos.md) build</span></span>

   - <span data-ttu-id="9a50f-149">Vergewissern Sie sich, dass SSH-Remoting aktiviert ist, indem Sie die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="9a50f-149">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="9a50f-150">Öffnen Sie `System Preferences`.</span><span class="sxs-lookup"><span data-stu-id="9a50f-150">Open `System Preferences`</span></span>
     - <span data-ttu-id="9a50f-151">Klicken Sie auf `Sharing`.</span><span class="sxs-lookup"><span data-stu-id="9a50f-151">Click on `Sharing`</span></span>
     - <span data-ttu-id="9a50f-152">Überprüfen Sie, ob für `Remote Login` `Remote Login: On` angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="9a50f-152">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="9a50f-153">Erteilen Sie den entsprechenden Benutzern Zugriff.</span><span class="sxs-lookup"><span data-stu-id="9a50f-153">Allow access to appropriate users</span></span>

2. <span data-ttu-id="9a50f-154">Bearbeiten Sie die Datei `sshd_config` unter `/private/etc/ssh/sshd_config`.</span><span class="sxs-lookup"><span data-stu-id="9a50f-154">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="9a50f-155">Verwenden Sie den von Ihnen bevorzugten Editor, oder</span><span class="sxs-lookup"><span data-stu-id="9a50f-155">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="9a50f-156">Vergewissern Sie sich, dass die Kennwortauthentifizierung aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="9a50f-156">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="9a50f-157">Fügen Sie einen Eintrag für das PowerShell-Subsystem hinzu.</span><span class="sxs-lookup"><span data-stu-id="9a50f-157">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="9a50f-158">Aktivieren Sie ggf. die Schlüsselauthentifizierung.</span><span class="sxs-lookup"><span data-stu-id="9a50f-158">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="9a50f-159">Starten Sie den SSHD-Dienst neu.</span><span class="sxs-lookup"><span data-stu-id="9a50f-159">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="9a50f-160">Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="9a50f-160">Authentication</span></span>

<span data-ttu-id="9a50f-161">PowerShell-Remoting über SSH basiert auf dem Authentifizierungsaustausch zwischen dem SSH-Client und dem SSH-Dienst und implementiert selbst keine Authentifizierungsschemas.</span><span class="sxs-lookup"><span data-stu-id="9a50f-161">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and does not implement any authentication schemes itself.</span></span>
<span data-ttu-id="9a50f-162">Dies bedeutet, dass alle konfigurierten Authentifizierungsschemas, einschließlich der mehrstufigen Authentifizierung, von SSH und unabhängig von PowerShell verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="9a50f-162">This means that any configured authentication schemes including multi-factor authentication is handled by SSH and independent of PowerShell.</span></span>
<span data-ttu-id="9a50f-163">Sie können den SSH-Dienst beispielsweise für die Authentifizierung mit öffentlichen Schlüsseln oder die Verwendung eines Einmalkennworts zur Erhöhung der Sicherheit konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="9a50f-163">For example, you can configure the SSH service to require public key authentication as well as a one-time password for added security.</span></span>
<span data-ttu-id="9a50f-164">Die Konfiguration einer mehrstufigen Authentifizierung wird in dieser Dokumentation nicht beschrieben.</span><span class="sxs-lookup"><span data-stu-id="9a50f-164">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span>
<span data-ttu-id="9a50f-165">Bevor Sie versuchen, eine mehrstufige Authentifizierung mit PowerShell-Remoting zu verwenden, informieren Sie sich in der Dokumentation für SSH, wie Sie eine mehrstufige Authentifizierung richtig konfigurieren, und testen Sie, ob diese außerhalb von PowerShell funktioniert.</span><span class="sxs-lookup"><span data-stu-id="9a50f-165">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="9a50f-166">Beispiel für das PowerShell-Remoting</span><span class="sxs-lookup"><span data-stu-id="9a50f-166">PowerShell Remoting Example</span></span>

<span data-ttu-id="9a50f-167">Sie können das Remoting am einfachsten auf einem einzelnen Computer testen.</span><span class="sxs-lookup"><span data-stu-id="9a50f-167">The easiest way to test remoting is to try it on a single machine.</span></span> <span data-ttu-id="9a50f-168">In diesem Beispiel haben wir eine Remotesitzung mit demselben Linux-Computer erstellt.</span><span class="sxs-lookup"><span data-stu-id="9a50f-168">In this example, we create a remote session back to the same Linux machine.</span></span> <span data-ttu-id="9a50f-169">Wir verwenden PowerShell-Cmdlets interaktiv, damit wir Eingabeaufforderungen von SSH sehen, die zum Überprüfen des Hostcomputers und zur Kennworteingabe auffordern.</span><span class="sxs-lookup"><span data-stu-id="9a50f-169">We are using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="9a50f-170">Sie können dies auch auf einem Windows-Computer durchführen, um sicherzustellen, dass das Remoting funktioniert.</span><span class="sxs-lookup"><span data-stu-id="9a50f-170">You can do the same thing on a Windows machine to ensure remoting is working.</span></span> <span data-ttu-id="9a50f-171">Verwenden Sie dann Remoting zwischen Computern, indem Sie den Hostnamen ändern.</span><span class="sxs-lookup"><span data-stu-id="9a50f-171">Then remote between machines by changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```output
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```output
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

```output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```output
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

### <a name="known-issues"></a><span data-ttu-id="9a50f-172">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="9a50f-172">Known Issues</span></span>

<span data-ttu-id="9a50f-173">Der Befehl „sudo“ funktioniert bei Remotesitzungen auf Linux-Computern nicht.</span><span class="sxs-lookup"><span data-stu-id="9a50f-173">The sudo command doesn't work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a50f-174">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9a50f-174">See Also</span></span>

[<span data-ttu-id="9a50f-175">PowerShell Core für Windows</span><span class="sxs-lookup"><span data-stu-id="9a50f-175">PowerShell Core for Windows</span></span>](../setup/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="9a50f-176">PowerShell Core für Linux</span><span class="sxs-lookup"><span data-stu-id="9a50f-176">PowerShell Core for Linux</span></span>](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="9a50f-177">PowerShell Core für macOS</span><span class="sxs-lookup"><span data-stu-id="9a50f-177">PowerShell Core for MacOS</span></span>](../setup/installing-powershell-core-on-macos.md)

[<span data-ttu-id="9a50f-178">Win32 OpenSSH</span><span class="sxs-lookup"><span data-stu-id="9a50f-178">Win32 OpenSSH</span></span>](https://github.com/PowerShell/Win32-OpenSSH/releases)

[<span data-ttu-id="9a50f-179">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="9a50f-179">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)