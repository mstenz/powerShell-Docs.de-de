---
title: PowerShell-Remoting über SSH
description: Remoting in PowerShell Core mithilfe von SSH
ms.date: 08/06/2018
ms.openlocfilehash: 27a8fc5623796a270a2ea67aa550c9a0998e766b
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587498"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="fce72-103">PowerShell-Remoting über SSH</span><span class="sxs-lookup"><span data-stu-id="fce72-103">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="fce72-104">Übersicht</span><span class="sxs-lookup"><span data-stu-id="fce72-104">Overview</span></span>

<span data-ttu-id="fce72-105">In der Regel wird beim PowerShell-Remoting für die Aushandlung der Verbindung und den Datentransport WinRM verwendet.</span><span class="sxs-lookup"><span data-stu-id="fce72-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="fce72-106">Für diese Remoting-Implementierung wurde Secure Shell (SSH) ausgewählt, da dieses Netzwerkprotokoll jetzt sowohl für Linux- als auch für Windows-Plattformen verfügbar ist und das PowerShell-Remoting für mehrere Plattformen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="fce72-106">SSH was chosen for this remoting implementation since it is now available for both Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span> <span data-ttu-id="fce72-107">Allerdings stellt WinRM auch einen stabiles Hostingmodell für PowerShell-Remotesitzungen zur Verfügung. Dies ist bei dieser Implementierung noch nicht der Fall.</span><span class="sxs-lookup"><span data-stu-id="fce72-107">However, WinRM also provides a robust hosting model for PowerShell remote sessions which this implementation does not yet do.</span></span> <span data-ttu-id="fce72-108">Das bedeutet, dass die Remotekonfiguration von Endpunkten und „Just Enough Administration“ (JEA, Minimale Administration) für PowerShell in dieser Implementierung noch nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="fce72-108">And this means that PowerShell remote endpoint configuration and JEA (Just Enough Administration) is not yet supported in this implementation.</span></span>

<span data-ttu-id="fce72-109">Mithilfe des SSH-Remotings für PowerShell können Sie grundlegendes PowerShell-Remoting von Sitzungen zwischen Windows- und Linux-Computern ausführen.</span><span class="sxs-lookup"><span data-stu-id="fce72-109">PowerShell SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="fce72-110">Dies geschieht durch Erstellen eines Hostingprozesses für PowerShell als SSH-Subsystem auf dem Zielcomputer.</span><span class="sxs-lookup"><span data-stu-id="fce72-110">This is done by creating a PowerShell hosting process on the target machine as an SSH subsystem.</span></span> <span data-ttu-id="fce72-111">Dies soll zukünftig in ein allgemeineres Hostingmodell geändert werden, das ähnlich wie WinRM funktioniert, um so Endpunktkonfigurationen und JEA zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="fce72-111">Eventually this will be changed to a more general hosting model similar to how WinRM works in order to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="fce72-112">Die Cmdlets `New-PSSession`, `Enter-PSSession` und `Invoke-Command` verfügen nun über einen neuen Parameter, der diese neue Remotingverbindung vereinfachen sollen.</span><span class="sxs-lookup"><span data-stu-id="fce72-112">The `New-PSSession`, `Enter-PSSession` and `Invoke-Command` cmdlets now have a new parameter set to facilitate this new remoting connection</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="fce72-113">Es werden voraussichtlich noch Änderungen an diesen neuen Parametern vorgenommen. Derzeit dienen sie jedoch dazu, Ihnen das Erstellen von SSH PSSessions zu ermöglichen, die Sie an die Befehlszeile koppeln oder über die Sie Befehle und Skripts aufrufen können.</span><span class="sxs-lookup"><span data-stu-id="fce72-113">This new parameter set will likely change but for now allows you to create SSH PSSessions that you can interact with from the command line or invoke commands and scripts on.</span></span> <span data-ttu-id="fce72-114">Geben Sie den Zielcomputer über den HostName-Parameter an, und fügen Sie über „UserName“ einen Benutzernamen hinzu.</span><span class="sxs-lookup"><span data-stu-id="fce72-114">You specify the target machine with the HostName parameter and provide the user name with UserName.</span></span> <span data-ttu-id="fce72-115">Wenn Sie die Cmdlets über die PowerShell-Befehlszeile ausführen, werden Sie dazu aufgefordert, ein Kennwort einzugeben.</span><span class="sxs-lookup"><span data-stu-id="fce72-115">When running the cmdlets interactively at the PowerShell command line you will be prompted for a password.</span></span> <span data-ttu-id="fce72-116">Außerdem haben Sie die Möglichkeit, die SSH-Schlüsselauthentifizierung zu verwenden und einen Dateipfad mit einem privaten Schlüssel über den KeyFilePath-Parameter bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="fce72-116">But you also have the option to use SSH key authentication and provide a private key file path with the KeyFilePath parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="fce72-117">Allgemeine Setupinformationen</span><span class="sxs-lookup"><span data-stu-id="fce72-117">General setup information</span></span>

<span data-ttu-id="fce72-118">SSH muss auf allen Computern installiert sein.</span><span class="sxs-lookup"><span data-stu-id="fce72-118">SSH is required to be installed on all machines.</span></span> <span data-ttu-id="fce72-119">Sie sollten sowohl den Client (`ssh.exe`) als auch den Server (`sshd.exe`) installieren, damit Sie das Remoting für Computer ausgiebig testen können.</span><span class="sxs-lookup"><span data-stu-id="fce72-119">You should install both client (`ssh.exe`) and server (`sshd.exe`) so that you can experiment with remoting to and from the machines.</span></span> <span data-ttu-id="fce72-120">Für Windows müssen Sie [Win32 OpenSSH über GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases) installieren.</span><span class="sxs-lookup"><span data-stu-id="fce72-120">For Windows you will need to install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="fce72-121">Für Linux müssen Sie SSH (einschließlich SSHD-Server) entsprechend Ihrer jeweiligen Plattform installieren.</span><span class="sxs-lookup"><span data-stu-id="fce72-121">For Linux you will need to install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="fce72-122">Außerdem benötigen Sie einen aktuellen PowerShell-Build oder ein PowerShell-Paket von GitHub, das die Remotefunktion für SSH anbietet.</span><span class="sxs-lookup"><span data-stu-id="fce72-122">You will also need a recent PowerShell build or package from GitHub having the SSH remoting feature.</span></span>
<span data-ttu-id="fce72-123">SSH-Subsysteme werden verwendet, um PowerShell-Prozesse auf dem Remotecomputer zu verwenden. Dafür muss der SSH-Server konfiguriert sein.</span><span class="sxs-lookup"><span data-stu-id="fce72-123">SSH subsystems is used to establish a PowerShell process on the remote machine and the SSH server will need to be configured for that.</span></span> <span data-ttu-id="fce72-124">Zusätzlich müssen Sie die Kennwortauthentifizierung und ggf. die schlüsselbasierte Authentifizierung aktivieren.</span><span class="sxs-lookup"><span data-stu-id="fce72-124">In addition you will need to enable password authentication and optionally key based authentication.</span></span>

## <a name="setup-on-windows-machine"></a><span data-ttu-id="fce72-125">Setup auf dem Windows-Computer</span><span class="sxs-lookup"><span data-stu-id="fce72-125">Setup on Windows Machine</span></span>

1. <span data-ttu-id="fce72-126">Installieren Sie die neuste Version von [PowerShell Core für Windows].</span><span class="sxs-lookup"><span data-stu-id="fce72-126">Install the latest version of [PowerShell Core for Windows]</span></span>

   - <span data-ttu-id="fce72-127">Anhand der Parameter für `New-PSSession` können Sie bestimmen, ob der Support für SSH-Remoting eingerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="fce72-127">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="fce72-128">Installieren Sie den neusten [Win32 OpenSSH]-Build über GitHub, und verwenden Sie dabei die Anweisungen zur [Installation].</span><span class="sxs-lookup"><span data-stu-id="fce72-128">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
3. <span data-ttu-id="fce72-129">Bearbeiten Sie die Datei „sshd_config“ am selben Ort, an dem Sie Win32 OpenSSH installiert haben.</span><span class="sxs-lookup"><span data-stu-id="fce72-129">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>

   - <span data-ttu-id="fce72-130">Vergewissern Sie sich, dass die Kennwortauthentifizierung aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="fce72-130">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="fce72-131">Es besteht ein Fehler in OpenSSH für Windows, der verhindert, dass Leerzeichen in ausführbaren Pfaden zu Subsystemen funktionieren.</span><span class="sxs-lookup"><span data-stu-id="fce72-131">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span>
     > <span data-ttu-id="fce72-132">[Weitere Informationen zu diesem Problem finden Sie auf GitHub.](https://github.com/PowerShell/Win32-OpenSSH/issues/784)</span><span class="sxs-lookup"><span data-stu-id="fce72-132">See [this issue on GitHub for more information](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="fce72-133">Um dieses Problem zu beheben, können Sie eine symbolische Verknüpfung mit dem Installationsverzeichnis herstellen, das keine Leerzeichen enthält:</span><span class="sxs-lookup"><span data-stu-id="fce72-133">One solution is to create a symlink to the Powershell installation directory that does not contain spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.0"
     ```

     <span data-ttu-id="fce72-134">Geben Sie diese anschließend in das Subsystem ein:</span><span class="sxs-lookup"><span data-stu-id="fce72-134">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="fce72-135">Aktivieren Sie ggf. die Schlüsselauthentifizierung.</span><span class="sxs-lookup"><span data-stu-id="fce72-135">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="fce72-136">Starten Sie den SSHD-Dienst neu.</span><span class="sxs-lookup"><span data-stu-id="fce72-136">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="fce72-137">Fügen Sie den Pfad an der Stelle hinzu, an der OpenSSH für die Variable „Path Env“ installiert ist.</span><span class="sxs-lookup"><span data-stu-id="fce72-137">Add the path where OpenSSH is installed to your Path Env Variable</span></span>

   - <span data-ttu-id="fce72-138">Dieser Pfad sollte wie folgt lauten: `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="fce72-138">This should be along the lines of `C:\Program Files\OpenSSH\`</span></span>
   - <span data-ttu-id="fce72-139">So kann die Datei „ssh.exe“ gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="fce72-139">This allows for the ssh.exe to be found</span></span>

## <a name="setup-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="fce72-140">Setup auf einem Linux-Computer (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="fce72-140">Setup on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="fce72-141">Installieren Sie den neusten Build von [PowerShell Core für Linux] über GitHub.</span><span class="sxs-lookup"><span data-stu-id="fce72-141">Install the latest [PowerShell Core for Linux] build from GitHub</span></span>
2. <span data-ttu-id="fce72-142">Installieren Sie ggf. [Ubuntu SSH].</span><span class="sxs-lookup"><span data-stu-id="fce72-142">Install [Ubuntu SSH] as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="fce72-143">Bearbeiten Sie die Datei „sshd_config“ unter „/etc/ssh“.</span><span class="sxs-lookup"><span data-stu-id="fce72-143">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="fce72-144">Vergewissern Sie sich, dass die Kennwortauthentifizierung aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="fce72-144">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="fce72-145">Fügen Sie einen Eintrag für das PowerShell-Subsystem hinzu.</span><span class="sxs-lookup"><span data-stu-id="fce72-145">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="fce72-146">Aktivieren Sie ggf. die Schlüsselauthentifizierung.</span><span class="sxs-lookup"><span data-stu-id="fce72-146">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="fce72-147">Starten Sie den SSHD-Dienst neu.</span><span class="sxs-lookup"><span data-stu-id="fce72-147">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="setup-on-macos-machine"></a><span data-ttu-id="fce72-148">Setup auf einem macOS-Computer</span><span class="sxs-lookup"><span data-stu-id="fce72-148">Setup on MacOS Machine</span></span>

1. <span data-ttu-id="fce72-149">Installieren Sie den neusten Build von [PowerShell Core für macOS].</span><span class="sxs-lookup"><span data-stu-id="fce72-149">Install the latest [PowerShell Core for MacOS] build</span></span>

   - <span data-ttu-id="fce72-150">Vergewissern Sie sich, dass SSH-Remoting aktiviert ist, indem Sie die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="fce72-150">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="fce72-151">Öffnen Sie `System Preferences`.</span><span class="sxs-lookup"><span data-stu-id="fce72-151">Open `System Preferences`</span></span>
     - <span data-ttu-id="fce72-152">Klicken Sie auf `Sharing`.</span><span class="sxs-lookup"><span data-stu-id="fce72-152">Click on `Sharing`</span></span>
     - <span data-ttu-id="fce72-153">Überprüfen Sie, ob für `Remote Login` `Remote Login: On` angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="fce72-153">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="fce72-154">Erteilen Sie den entsprechenden Benutzern Zugriff.</span><span class="sxs-lookup"><span data-stu-id="fce72-154">Allow access to appropriate users</span></span>

2. <span data-ttu-id="fce72-155">Bearbeiten Sie die Datei `sshd_config` unter `/private/etc/ssh/sshd_config`.</span><span class="sxs-lookup"><span data-stu-id="fce72-155">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="fce72-156">Verwenden Sie den von Ihnen bevorzugten Editor, oder</span><span class="sxs-lookup"><span data-stu-id="fce72-156">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="fce72-157">Vergewissern Sie sich, dass die Kennwortauthentifizierung aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="fce72-157">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="fce72-158">Fügen Sie einen Eintrag für das PowerShell-Subsystem hinzu.</span><span class="sxs-lookup"><span data-stu-id="fce72-158">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="fce72-159">Aktivieren Sie ggf. die Schlüsselauthentifizierung.</span><span class="sxs-lookup"><span data-stu-id="fce72-159">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="fce72-160">Starten Sie den SSHD-Dienst neu.</span><span class="sxs-lookup"><span data-stu-id="fce72-160">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="fce72-161">Beispiel für das PowerShell-Remoting</span><span class="sxs-lookup"><span data-stu-id="fce72-161">PowerShell Remoting Example</span></span>

<span data-ttu-id="fce72-162">Sie können das Remoting am einfachsten auf einem einzelnen Computer testen.</span><span class="sxs-lookup"><span data-stu-id="fce72-162">The easiest way to test remoting is to just try it on a single machine.</span></span> <span data-ttu-id="fce72-163">In diesem Beispiel wird eine Remotesitzung zu demselben Computer auf einem Linux-Feld erstellt.</span><span class="sxs-lookup"><span data-stu-id="fce72-163">Here I will create a remote session back to the same machine on a Linux box.</span></span> <span data-ttu-id="fce72-164">An dieser Stelle werden PowerShell-Cmdlets über eine Eingabeaufforderung verwendet, sodass SSH-Fenster angezeigt werden, in denen Sie dazu aufgefordert werden, den Hostcomputer zu überprüfen und Kennwörter einzugeben.</span><span class="sxs-lookup"><span data-stu-id="fce72-164">Notice that I am using PowerShell cmdlets from a command prompt so we see prompts from SSH asking to verify the host computer as well as password prompts.</span></span> <span data-ttu-id="fce72-165">Sie können auf einem Windows-Computer genauso vorgehen, um zu gewährleisten, dass das Remoting funktioniert. Stellen Sie dann eine Remoteverbindung zwischen verschiedenen Computern her, indem Sie nur den Hostnamen ändern.</span><span class="sxs-lookup"><span data-stu-id="fce72-165">You can do the same thing on a Windows machine to ensure remoting is working there and then remote between machines by simply changing the host name.</span></span>

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
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available
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

### <a name="known-issues"></a><span data-ttu-id="fce72-166">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="fce72-166">Known Issues</span></span>

<span data-ttu-id="fce72-167">Der Befehl „sudo“ funktioniert bei Remotesitzungen auf Linux-Computern nicht.</span><span class="sxs-lookup"><span data-stu-id="fce72-167">The sudo command does not work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="fce72-168">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fce72-168">See Also</span></span>

[<span data-ttu-id="fce72-169">PowerShell Core für Windows</span><span class="sxs-lookup"><span data-stu-id="fce72-169">PowerShell Core for Windows</span></span>](../setup/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="fce72-170">PowerShell Core für Linux</span><span class="sxs-lookup"><span data-stu-id="fce72-170">PowerShell Core for Linux</span></span>](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="fce72-171">PowerShell Core für macOS</span><span class="sxs-lookup"><span data-stu-id="fce72-171">PowerShell Core for MacOS</span></span>](../setup/installing-powershell-core-on-macos.md)

[<span data-ttu-id="fce72-172">Win32 OpenSSH</span><span class="sxs-lookup"><span data-stu-id="fce72-172">Win32 OpenSSH</span></span>](https://github.com/PowerShell/Win32-OpenSSH/releases)

[<span data-ttu-id="fce72-173">Installation</span><span class="sxs-lookup"><span data-stu-id="fce72-173">installation</span></span>](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[<span data-ttu-id="fce72-174">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="fce72-174">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)