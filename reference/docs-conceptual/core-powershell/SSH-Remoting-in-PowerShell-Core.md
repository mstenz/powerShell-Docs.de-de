---
title: PowerShell-Remoting über SSH
description: Remoting in PowerShell Core mithilfe von SSH
ms.date: 08/14/2018
ms.openlocfilehash: 842e67e96661bca8be54aab33cbc11aa23dbd1c0
ms.sourcegitcommit: 47becf2823ece251a7264db2387bb503cf3abaa9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "49451064"
---
# <a name="powershell-remoting-over-ssh"></a>PowerShell-Remoting über SSH

## <a name="overview"></a>Übersicht

In der Regel wird beim PowerShell-Remoting für die Aushandlung der Verbindung und den Datentransport WinRM verwendet. SSH ist jetzt für Linux- und Windows-Plattformen verfügbar und ermöglicht echtes PowerShell-Remoting für mehrere Plattformen.

WinRM bietet ein stabiles Hostingmodell für PowerShell-Remotesitzungen. SSH-basiertes Remoting unterstützt derzeit nicht die Remotekonfiguration von Endpunkten und JEA (Just Enough Administration, minimale Verwaltung).

Mithilfe von SSH-Remoting können Sie grundlegendes PowerShell-Remoting von Sitzungen zwischen Windows- und Linux-Computern ausführen. SSH-Remoting erstellt einen PowerShell-Hostprozess als SSH-Subsystem auf dem Zielcomputer.
Schließlich implementieren wir ein allgemeines mit WinRM vergleichbares Hostingmodell, um die Endpunktkonfiguration und JEA zu unterstützen.

Die Cmdlets `New-PSSession`, `Enter-PSSession` und `Invoke-Command` verfügen nun über einen neuen Parameter, der diese neue Remotingverbindung unterstützt.

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Um eine Remotesitzung zu erstellen, geben Sie den Zielcomputer über den `HostName`-Parameter an, und fügen Sie über `UserName` den Benutzernamen hinzu. Wenn Sie die Cmdlets interaktiv ausführen, werden Sie zur Kennworteingabe aufgefordert. Sie können auch die SSH-Schlüsselauthentifizierung mithilfe einer privaten Schlüsseldatei mit dem `KeyFilePath`-Parameter verwenden.

## <a name="general-setup-information"></a>Allgemeine Setupinformationen

SSH muss auf allen Computern installiert sein. Installieren Sie den SSH-Client (`ssh.exe`) und -Server (`sshd.exe`), damit Sie Remoting zwischen den Computern nutzen können. Installieren Sie für Windows [Win32 OpenSSH über GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).
Installieren Sie für Linux SSH (einschließlich SSHD-Server) entsprechend Ihrer Plattform. Sie müssen auch PowerShell Core über GitHub installieren, um das SSH-Remotingfeature zu erhalten. Der SSH-Server muss konfiguriert werden, um ein SSH-Subsystem zum Hosten eines PowerShell-Prozesses auf dem Remotecomputer zu erstellen. Sie müssen auch eine kennwort- oder schlüsselbasierte Authentifizierung konfigurieren und aktivieren.

## <a name="set-up-on-windows-machine"></a>Setup auf dem Windows-Computer

1. Installieren Sie die neuste Version von [PowerShell Core für Windows](../setup/installing-powershell-core-on-windows.md#msi)

   - Anhand der Parameter für `New-PSSession` können Sie bestimmen, ob der Support für SSH-Remoting eingerichtet ist.

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. Installieren Sie den neusten [Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)-Build über GitHub, und verwenden Sie dabei die [Installation](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH).
3. Bearbeiten Sie die Datei „sshd_config“ unter `%ProgramData%\ssh`.

   - Vergewissern Sie sich, dass die Kennwortauthentifizierung aktiviert ist.

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > Es besteht ein Fehler in OpenSSH für Windows, der verhindert, dass Leerzeichen in ausführbaren Pfaden zu Subsystemen funktionieren. Weitere Informationen finden Sie in [diesem GitHub-Problem](https://github.com/PowerShell/Win32-OpenSSH/issues/784).

     Um dieses Problem zu beheben, können Sie eine symbolische Verknüpfung mit dem PowerShell-Installationsverzeichnis herstellen, die keine Leerzeichen enthält:

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     Geben Sie diese anschließend in das Subsystem ein:

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - Aktivieren Sie ggf. die Schlüsselauthentifizierung.

     ```
     PubkeyAuthentication yes
     ```

4. Starten Sie den SSHD-Dienst neu.

   ```powershell
   Restart-Service sshd
   ```

5. Fügen Sie den Pfad der OpenSSH-Installation der Umgebungsvariablen „Path“ hinzu. Beispiel: `C:\Program Files\OpenSSH\`. Durch diesen Eintrag kann die Datei „ssh.exe“ gefunden werden.

## <a name="set-up-on-linux-ubuntu-1404-machine"></a>Setup auf einem Linux-Computer (Ubuntu 14.04)

1. Installieren Sie den neusten Build von [PowerShell Core für Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404) über GitHub.
2. Installieren Sie ggf. [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html).

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. Bearbeiten Sie die Datei „sshd_config“ unter „/etc/ssh“.

   - Vergewissern Sie sich, dass die Kennwortauthentifizierung aktiviert ist.

   ```
   PasswordAuthentication yes
   ```

   - Fügen Sie einen Eintrag für das PowerShell-Subsystem hinzu.

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - Aktivieren Sie ggf. die Schlüsselauthentifizierung.

   ```
   PubkeyAuthentication yes
   ```

4. Starten Sie den SSHD-Dienst neu.

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a>Setup auf einem macOS-Computer

1. Installieren Sie den neusten Build von [PowerShell Core für macOS](../setup/installing-powershell-core-on-macos.md).

   - Vergewissern Sie sich, dass SSH-Remoting aktiviert ist, indem Sie die folgenden Schritte ausführen:
     - Öffnen Sie `System Preferences`.
     - Klicken Sie auf `Sharing`.
     - Überprüfen Sie, ob für `Remote Login` `Remote Login: On` angezeigt wird.
     - Erteilen Sie den entsprechenden Benutzern Zugriff.

2. Bearbeiten Sie die Datei `sshd_config` unter `/private/etc/ssh/sshd_config`.

   - Verwenden Sie den von Ihnen bevorzugten Editor, oder

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - Vergewissern Sie sich, dass die Kennwortauthentifizierung aktiviert ist.

     ```
     PasswordAuthentication yes
     ```

   - Fügen Sie einen Eintrag für das PowerShell-Subsystem hinzu.

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - Aktivieren Sie ggf. die Schlüsselauthentifizierung.

     ```
     PubkeyAuthentication yes
     ```

3. Starten Sie den SSHD-Dienst neu.

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a>Authentifizierung

PowerShell-Remoting über SSH basiert auf dem Authentifizierungsaustausch zwischen dem SSH-Client und dem SSH-Dienst und implementiert selbst keine Authentifizierungsschemas.
Dies bedeutet, dass alle konfigurierten Authentifizierungsschemas, einschließlich der mehrstufigen Authentifizierung, von SSH und unabhängig von PowerShell verarbeitet werden.
Sie können den SSH-Dienst beispielsweise für die Authentifizierung mit öffentlichen Schlüsseln oder die Verwendung eines Einmalkennworts zur Erhöhung der Sicherheit konfigurieren.
Die Konfiguration einer mehrstufigen Authentifizierung wird in dieser Dokumentation nicht beschrieben.
Bevor Sie versuchen, eine mehrstufige Authentifizierung mit PowerShell-Remoting zu verwenden, informieren Sie sich in der Dokumentation für SSH, wie Sie eine mehrstufige Authentifizierung richtig konfigurieren, und testen Sie, ob diese außerhalb von PowerShell funktioniert.

## <a name="powershell-remoting-example"></a>Beispiel für das PowerShell-Remoting

Sie können das Remoting am einfachsten auf einem einzelnen Computer testen. In diesem Beispiel haben wir eine Remotesitzung mit demselben Linux-Computer erstellt. Wir verwenden PowerShell-Cmdlets interaktiv, damit wir Eingabeaufforderungen von SSH sehen, die zum Überprüfen des Hostcomputers und zur Kennworteingabe auffordern. Sie können dies auch auf einem Windows-Computer durchführen, um sicherzustellen, dass das Remoting funktioniert. Verwenden Sie dann Remoting zwischen Computern, indem Sie den Hostnamen ändern.

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

### <a name="known-issues"></a>Bekannte Probleme

Der Befehl „sudo“ funktioniert bei Remotesitzungen auf Linux-Computern nicht.

## <a name="see-also"></a>Weitere Informationen

[PowerShell Core für Windows](../setup/installing-powershell-core-on-windows.md#msi)

[PowerShell Core für Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[PowerShell Core für macOS](../setup/installing-powershell-core-on-macos.md)

[Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
