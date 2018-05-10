# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="0aab6-101">PowerShell-Remoting über SSH</span><span class="sxs-lookup"><span data-stu-id="0aab6-101">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="0aab6-102">Übersicht</span><span class="sxs-lookup"><span data-stu-id="0aab6-102">Overview</span></span>

<span data-ttu-id="0aab6-103">In der Regel wird beim PowerShell-Remoting für die Aushandlung der Verbindung und den Datentransport WinRM verwendet.</span><span class="sxs-lookup"><span data-stu-id="0aab6-103">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span>
<span data-ttu-id="0aab6-104">Für diese Remoting-Implementierung wurde Secure Shell (SSH) ausgewählt, da dieses Netzwerkprotokoll jetzt sowohl für Linux- als auch für Windows-Plattformen verfügbar ist und das PowerShell-Remoting für mehrere Plattformen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="0aab6-104">SSH was chosen for this remoting implementation since it is now available for both Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>
<span data-ttu-id="0aab6-105">Allerdings stellt WinRM auch einen stabiles Hostingmodell für PowerShell-Remotesitzungen zur Verfügung. Dies ist bei dieser Implementierung noch nicht der Fall.</span><span class="sxs-lookup"><span data-stu-id="0aab6-105">However, WinRM also provides a robust hosting model for PowerShell remote sessions which this implementation does not yet do.</span></span>
<span data-ttu-id="0aab6-106">Das bedeutet, dass die Remotekonfiguration von Endpunkten und „Just Enough Administration“ (JEA, Minimale Administration) für PowerShell in dieser Implementierung noch nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="0aab6-106">And this means that PowerShell remote endpoint configuration and JEA (Just Enough Administration) is not yet supported in this implementation.</span></span>

<span data-ttu-id="0aab6-107">Mithilfe des SSH-Remotings für PowerShell können Sie grundlegendes PowerShell-Remoting von Sitzungen zwischen Windows- und Linux-Computern ausführen.</span><span class="sxs-lookup"><span data-stu-id="0aab6-107">PowerShell SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span>
<span data-ttu-id="0aab6-108">Dies geschieht durch Erstellen eines Hostingprozesses für PowerShell als SSH-Subsystem auf dem Zielcomputer.</span><span class="sxs-lookup"><span data-stu-id="0aab6-108">This is done by creating a PowerShell hosting process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="0aab6-109">Dies soll zukünftig in ein allgemeineres Hostingmodell geändert werden, das ähnlich wie WinRM funktioniert, um so Endpunktkonfigurationen und JEA zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="0aab6-109">Eventually this will be changed to a more general hosting model similar to how WinRM works in order to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="0aab6-110">Die neuen Cmdlets „New-PSSession“, „Enter-PSSession“ und „Invoke-Command“ verfügen nun über Parameter, die diese neue Remotingverbindung vereinfachen sollen.</span><span class="sxs-lookup"><span data-stu-id="0aab6-110">The New-PSSession, Enter-PSSession and Invoke-Command cmdlets now have a new parameter set to facilitate this new remoting connection</span></span>

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="0aab6-111">Es werden voraussichtlich noch Änderungen an diesen neuen Parametern vorgenommen. Derzeit dienen sie jedoch dazu, Ihnen das Erstellen von SSH PSSessions zu ermöglichen, die Sie an die Befehlszeile koppeln oder über die Sie Befehle und Skripts aufrufen können.</span><span class="sxs-lookup"><span data-stu-id="0aab6-111">This new parameter set will likely change but for now allows you to create SSH PSSessions that you can interact with from the command line or invoke commands and scripts on.</span></span>
<span data-ttu-id="0aab6-112">Geben Sie den Zielcomputer über den HostName-Parameter an, und fügen Sie über „UserName“ einen Benutzernamen hinzu.</span><span class="sxs-lookup"><span data-stu-id="0aab6-112">You specify the target machine with the HostName parameter and provide the user name with UserName.</span></span>
<span data-ttu-id="0aab6-113">Wenn Sie die Cmdlets über die PowerShell-Befehlszeile ausführen, werden Sie dazu aufgefordert, ein Kennwort einzugeben.</span><span class="sxs-lookup"><span data-stu-id="0aab6-113">When running the cmdlets interactively at the PowerShell command line you will be prompted for a password.</span></span>
<span data-ttu-id="0aab6-114">Außerdem haben Sie die Möglichkeit, die SSH-Schlüsselauthentifizierung zu verwenden und einen Dateipfad mit einem privaten Schlüssel über den KeyFilePath-Parameter bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="0aab6-114">But you also have the option to use SSH key authentication and provide a private key file path with the KeyFilePath parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="0aab6-115">Allgemeine Setupinformationen</span><span class="sxs-lookup"><span data-stu-id="0aab6-115">General setup information</span></span>

<span data-ttu-id="0aab6-116">SSH muss auf allen Computern installiert sein.</span><span class="sxs-lookup"><span data-stu-id="0aab6-116">SSH is required to be installed on all machines.</span></span>
<span data-ttu-id="0aab6-117">Sie sollten sowohl den Client („ssh.exe“) als auch den Server („sshd.exe“) installieren, damit Sie das Remoting für Computer ausgiebig testen können.</span><span class="sxs-lookup"><span data-stu-id="0aab6-117">You should install both client (ssh.exe) and server (sshd.exe) so that you can experiment with remoting to and from the machines.</span></span>
<span data-ttu-id="0aab6-118">Für Windows müssen Sie [Win32 OpenSSH über GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases) installieren.</span><span class="sxs-lookup"><span data-stu-id="0aab6-118">For Windows you will need to install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="0aab6-119">Für Linux müssen Sie SSH (einschließlich SSHD-Server) entsprechend Ihrer jeweiligen Plattform installieren.</span><span class="sxs-lookup"><span data-stu-id="0aab6-119">For Linux you will need to install SSH (including sshd server) appropriate to your platform.</span></span>
<span data-ttu-id="0aab6-120">Außerdem benötigen Sie einen aktuellen PowerShell-Build oder ein PowerShell-Paket von GitHub, das die Remotefunktion für SSH anbietet.</span><span class="sxs-lookup"><span data-stu-id="0aab6-120">You will also need a recent PowerShell build or package from GitHub having the SSH remoting feature.</span></span>
<span data-ttu-id="0aab6-121">SSH-Subsysteme werden verwendet, um PowerShell-Prozesse auf dem Remotecomputer zu verwenden. Dafür muss der SSH-Server konfiguriert sein.</span><span class="sxs-lookup"><span data-stu-id="0aab6-121">SSH subsystems is used to establish a PowerShell process on the remote machine and the SSH server will need to be configured for that.</span></span>
<span data-ttu-id="0aab6-122">Zusätzlich müssen Sie die Kennwortauthentifizierung und ggf. die schlüsselbasierte Authentifizierung aktivieren.</span><span class="sxs-lookup"><span data-stu-id="0aab6-122">In addition you will need to enable password authentication and optionally key based authentication.</span></span>

## <a name="setup-on-windows-machine"></a><span data-ttu-id="0aab6-123">Setup auf dem Windows-Computer</span><span class="sxs-lookup"><span data-stu-id="0aab6-123">Setup on Windows Machine</span></span>

1. <span data-ttu-id="0aab6-124">Installieren Sie die neuste Version von [PowerShell Core für Windows]</span><span class="sxs-lookup"><span data-stu-id="0aab6-124">Install the latest version of [PowerShell Core for Windows]</span></span>
    - <span data-ttu-id="0aab6-125">Anhand der Parameter für „New-PSSession“ können Sie bestimmen, ob der Support für SSH-Remoting eingerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="0aab6-125">You can tell if it has the SSH remoting support by looking at the parameter sets for New-PSSession</span></span>

    ```powershell
    PS> Get-Command New-PSSession -syntax
    New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
    ```

1. <span data-ttu-id="0aab6-126">Installieren Sie den neusten [Win32 OpenSSH]-Build über GitHub, und verwenden Sie dabei die [Installationsanweisungen].</span><span class="sxs-lookup"><span data-stu-id="0aab6-126">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
1. <span data-ttu-id="0aab6-127">Bearbeiten Sie die Datei „sshd_config“ am selben Ort, an dem Sie Win32 OpenSSH installiert haben.</span><span class="sxs-lookup"><span data-stu-id="0aab6-127">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>
    - <span data-ttu-id="0aab6-128">Vergewissern Sie sich, dass die Kennwortauthentifizierung aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="0aab6-128">Make sure password authentication is enabled</span></span>

    ```
    PasswordAuthentication yes
    ```

    - <span data-ttu-id="0aab6-129">Fügen Sie einen Eintrag für das PowerShell-Subsystem hinzu, und ersetzen Sie `c:/program files/powershell/6.0.0/pwsh.exe` durch den Pfad zu der Version, die verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="0aab6-129">Add a PowerShell subsystem entry, replace `c:/program files/powershell/6.0.0/pwsh.exe` with the correct path to the version you want to use</span></span>

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    - <span data-ttu-id="0aab6-130">Aktivieren Sie ggf. die Schlüsselauthentifizierung.</span><span class="sxs-lookup"><span data-stu-id="0aab6-130">Optionally enable key authentication</span></span>

    ```
    PubkeyAuthentication yes
    ```

1. <span data-ttu-id="0aab6-131">Starten Sie den SSHD-Dienst neu.</span><span class="sxs-lookup"><span data-stu-id="0aab6-131">Restart the sshd service</span></span>

    ```powershell
    Restart-Service sshd
    ```

1. <span data-ttu-id="0aab6-132">Fügen Sie den Pfad an der Stelle hinzu, an der OpenSSH für die Variable „Path Env“ installiert ist.</span><span class="sxs-lookup"><span data-stu-id="0aab6-132">Add the path where OpenSSH is installed to your Path Env Variable</span></span>
    - <span data-ttu-id="0aab6-133">Dieser Pfad sollte wie folgt lauten: `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="0aab6-133">This should be along the lines of `C:\Program Files\OpenSSH\`</span></span>
    - <span data-ttu-id="0aab6-134">So kann die Datei „ssh.exe“ gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="0aab6-134">This allows for the ssh.exe to be found</span></span>

## <a name="setup-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="0aab6-135">Setup auf einem Linux-Computer (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="0aab6-135">Setup on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="0aab6-136">Installieren Sie den neusten [PowerShell für Linux]-Build über GitHub.</span><span class="sxs-lookup"><span data-stu-id="0aab6-136">Install the latest [PowerShell for Linux] build from GitHub</span></span>
1. <span data-ttu-id="0aab6-137">Installieren Sie ggf. [Ubuntu SSH].</span><span class="sxs-lookup"><span data-stu-id="0aab6-137">Install [Ubuntu SSH] as needed</span></span>

    ```bash
    sudo apt install openssh-client
    sudo apt install openssh-server
    ```

1. <span data-ttu-id="0aab6-138">Bearbeiten Sie die Datei „sshd_config“ unter „/etc/ssh“.</span><span class="sxs-lookup"><span data-stu-id="0aab6-138">Edit the sshd_config file at location /etc/ssh</span></span>
    - <span data-ttu-id="0aab6-139">Vergewissern Sie sich, dass die Kennwortauthentifizierung aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="0aab6-139">Make sure password authentication is enabled</span></span>

    ```
    PasswordAuthentication yes
    ```

    - <span data-ttu-id="0aab6-140">Fügen Sie einen Eintrag für das PowerShell-Subsystem hinzu.</span><span class="sxs-lookup"><span data-stu-id="0aab6-140">Add a PowerShell subsystem entry</span></span>

    ```
    Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
    ```

    - <span data-ttu-id="0aab6-141">Aktivieren Sie ggf. die Schlüsselauthentifizierung.</span><span class="sxs-lookup"><span data-stu-id="0aab6-141">Optionally enable key authentication</span></span>

    ```
    PubkeyAuthentication yes
    ```

1. <span data-ttu-id="0aab6-142">Starten Sie den SSHD-Dienst neu.</span><span class="sxs-lookup"><span data-stu-id="0aab6-142">Restart the sshd service</span></span>

    ```bash
    sudo service sshd restart
    ```

## <a name="setup-on-macos-machine"></a><span data-ttu-id="0aab6-143">Setup auf einem macOS-Computer</span><span class="sxs-lookup"><span data-stu-id="0aab6-143">Setup on MacOS Machine</span></span>

1. <span data-ttu-id="0aab6-144">Installieren Sie den neusten [PowerShell für macOS]-Build.</span><span class="sxs-lookup"><span data-stu-id="0aab6-144">Install the latest [PowerShell for MacOS] build</span></span>
    - <span data-ttu-id="0aab6-145">Vergewissern Sie sich, dass SSH-Remoting aktiviert ist, indem Sie die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="0aab6-145">Make sure SSH Remoting is enabled by following these steps:</span></span>
      - <span data-ttu-id="0aab6-146">Öffnen Sie `System Preferences`.</span><span class="sxs-lookup"><span data-stu-id="0aab6-146">Open `System Preferences`</span></span>
      - <span data-ttu-id="0aab6-147">Klicken Sie auf `Sharing`.</span><span class="sxs-lookup"><span data-stu-id="0aab6-147">Click on `Sharing`</span></span>
      - <span data-ttu-id="0aab6-148">Überprüfen Sie, ob für `Remote Login` `Remote Login: On` angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="0aab6-148">Check `Remote Login` - Should say `Remote Login: On`</span></span>
      - <span data-ttu-id="0aab6-149">Erteilen Sie den entsprechenden Benutzern Zugriff.</span><span class="sxs-lookup"><span data-stu-id="0aab6-149">Allow access to appropriate users</span></span>
1. <span data-ttu-id="0aab6-150">Bearbeiten Sie die Datei `sshd_config` unter `/private/etc/ssh/sshd_config`.</span><span class="sxs-lookup"><span data-stu-id="0aab6-150">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>
    - <span data-ttu-id="0aab6-151">Verwenden Sie den von Ihnen bevorzugten Editor, oder</span><span class="sxs-lookup"><span data-stu-id="0aab6-151">Use your favorite editor or</span></span>

    ```bash
    sudo nano /private/etc/ssh/sshd_config
    ```

    - <span data-ttu-id="0aab6-152">Vergewissern Sie sich, dass die Kennwortauthentifizierung aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="0aab6-152">Make sure password authentication is enabled</span></span>

    ```
    PasswordAuthentication yes
    ```

    - <span data-ttu-id="0aab6-153">Fügen Sie einen Eintrag für das PowerShell-Subsystem hinzu.</span><span class="sxs-lookup"><span data-stu-id="0aab6-153">Add a PowerShell subsystem entry</span></span>

    ```
    Subsystem powershell /usr/local/bin/powershell -sshs -NoLogo -NoProfile
    ```

    - <span data-ttu-id="0aab6-154">Aktivieren Sie ggf. die Schlüsselauthentifizierung.</span><span class="sxs-lookup"><span data-stu-id="0aab6-154">Optionally enable key authentication</span></span>

    ```
    PubkeyAuthentication yes
    ```

1. <span data-ttu-id="0aab6-155">Starten Sie den SSHD-Dienst neu.</span><span class="sxs-lookup"><span data-stu-id="0aab6-155">Restart the sshd service</span></span>

    ```bash
    sudo launchctl stop com.openssh.sshd
    sudo launchctl start com.openssh.sshd
    ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="0aab6-156">Beispiel für das PowerShell-Remoting</span><span class="sxs-lookup"><span data-stu-id="0aab6-156">PowerShell Remoting Example</span></span>

<span data-ttu-id="0aab6-157">Sie können das Remoting am einfachsten auf einem einzelnen Computer testen.</span><span class="sxs-lookup"><span data-stu-id="0aab6-157">The easiest way to test remoting is to just try it on a single machine.</span></span>
<span data-ttu-id="0aab6-158">In diesem Beispiel wird eine Remotesitzung zu demselben Computer auf einem Linux-Feld erstellt.</span><span class="sxs-lookup"><span data-stu-id="0aab6-158">Here I will create a remote session back to the same machine on a Linux box.</span></span>
<span data-ttu-id="0aab6-159">An dieser Stelle werden PowerShell-Cmdlets über eine Eingabeaufforderung verwendet, sodass SSH-Fenster angezeigt werden, in denen Sie dazu aufgefordert werden, den Hostcomputer zu überprüfen und Kennwörter einzugeben.</span><span class="sxs-lookup"><span data-stu-id="0aab6-159">Notice that I am using PowerShell cmdlets from a command prompt so we see prompts from SSH asking to verify the host computer as well as password prompts.</span></span>
<span data-ttu-id="0aab6-160">Sie können auf einem Windows-Computer genauso vorgehen, um zu gewährleisten, dass das Remoting funktioniert. Stellen Sie dann eine Remoteverbindung zwischen verschiedenen Computern her, indem Sie nur den Hostnamen ändern.</span><span class="sxs-lookup"><span data-stu-id="0aab6-160">You can do the same thing on a Windows machine to ensure remoting is working there and then remote between machines by simply changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
PS /home/TestUser> $session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:

PS /home/TestUser> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available

PS /home/TestUser> Enter-PSSession $session

[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession

PS /home/TestUser> Invoke-Command $session -ScriptBlock { Get-Process powershell }

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1


#
# Linux to Windows
#
PS /home/TestUser> Enter-PSSession -HostName WinVM1 -UserName PTestName
PTestName@WinVM1s password:

[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver

Microsoft Windows [Version 10.0.10586]

[WinVM1]: PS C:\Users\PTestName\Documents>

#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.

PS C:\Users\PSUser\Documents> $session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
PS C:\Users\PSUser\Documents> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available


PS C:\Users\PSUser\Documents> Enter-PSSession -Session $session
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

### <a name="known-issues"></a><span data-ttu-id="0aab6-161">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="0aab6-161">Known Issues</span></span>

1. <span data-ttu-id="0aab6-162">Der Befehl „sudo“ funktioniert bei Remotesitzungen auf Linux-Computern nicht.</span><span class="sxs-lookup"><span data-stu-id="0aab6-162">sudo command does not work in remote session to Linux machine.</span></span>

[PowerShell Core für Windows]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi
[PowerShell Core for Windows]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi
[Win32 OpenSSH]: https://github.com/PowerShell/Win32-OpenSSH/releases
[Installationsanweisungen]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[installation]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[PowerShell für Linux]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#ubuntu-1404
[PowerShell for Linux]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#ubuntu-1404
[Ubuntu SSH]: https://help.ubuntu.com/lts/serverguide/openssh-server.html
[PowerShell für macOS]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/macos.md#macos-1012
[PowerShell for MacOS]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/macos.md#macos-1012
