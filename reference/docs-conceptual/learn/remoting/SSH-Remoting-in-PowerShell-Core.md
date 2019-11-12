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
# <a name="powershell-remoting-over-ssh"></a>PowerShell-Remoting über SSH

## <a name="overview"></a>Übersicht

In der Regel wird beim PowerShell-Remoting für die Aushandlung der Verbindung und den Datentransport WinRM verwendet. SSH ist jetzt für Linux- und Windows-Plattformen verfügbar und ermöglicht echtes PowerShell-Remoting für mehrere Plattformen.

WinRM bietet ein stabiles Hostingmodell für PowerShell-Remotesitzungen. SSH-basiertes Remoting unterstützt derzeit nicht die Remotekonfiguration von Endpunkten und JEA (Just Enough Administration, minimale Verwaltung).

Mithilfe von SSH-Remoting können Sie grundlegendes PowerShell-Remoting von Sitzungen zwischen Windows- und Linux-Computern ausführen. SSH-Remoting erstellt einen PowerShell-Hostprozess als SSH-Subsystem auf dem Zielcomputer. Schließlich implementieren wir ein allgemeines mit WinRM vergleichbares Hostingmodell, um die Endpunktkonfiguration und JEA zu unterstützen.

Die Cmdlets `New-PSSession`, `Enter-PSSession` und `Invoke-Command` verfügen nun über einen neuen Parameter, der diese neue Remotingverbindung unterstützt.

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Um eine Remotesitzung zu erstellen, geben Sie den Zielcomputer über den `HostName`-Parameter an, und fügen Sie über `UserName` den Benutzernamen hinzu. Wenn Sie die Cmdlets interaktiv ausführen, werden Sie zur Kennworteingabe aufgefordert. Sie können auch die SSH-Schlüsselauthentifizierung mithilfe einer privaten Schlüsseldatei mit dem `KeyFilePath`-Parameter verwenden.

## <a name="general-setup-information"></a>Allgemeine Setupinformationen

PowerShell 6 oder höher und SSH müssen auf allen Computern installiert sein. Installieren Sie den SSH-Client (`ssh.exe`) und -Server (`sshd.exe`), damit Sie Remoting zwischen den Computern nutzen können. OpenSSH für Windows ist jetzt im Windows 10-Build 1809 sowie in Windows Server 2019 verfügbar. Weitere Informationen finden Sie unter [Installation von OpenSSH für Windows Server 2019 und Windows 10](/windows-server/administration/openssh/openssh_overview). Installieren Sie für Linux SSH, einschließlich SSHD-Server, entsprechend Ihrer Plattform. Sie müssen auch PowerShell über GitHub installieren, um das SSH-Remotingfeature zu erhalten. Der SSH-Server muss konfiguriert werden, um ein SSH-Subsystem zum Hosten eines PowerShell-Prozesses auf dem Remotecomputer zu erstellen. Sie müssen auch eine **kennwort-** oder **schlüsselbasierte** Authentifizierung konfigurieren und aktivieren.

## <a name="set-up-on-a-windows-computer"></a>Einrichten auf einem Windows-Computer

1. Weitere Informationen zur Installation der neuesten Version von PowerShell finden Sie unter [Installieren von PowerShell Core unter Windows](../../install/installing-powershell-core-on-windows.md#msi).

   Sie können bestätigen, dass PowerShell SSH-Remoting unterstützt, indem Sie die `New-PSSession`-Parametersätze auflisten. Sie werden sehen, dass die Namen einiger Parametersätze mit **SSH** beginnen. Diese Parametersätze enthalten **SSH**-Parameter.

   ```powershell
   (Get-Command New-PSSession).ParameterSets.Name
   ```

   ```Output
   Name
   ----
   SSHHost
   SSHHostHashParam
   ```

1. Installieren Sie die neueste Win32-OpenSSH. Weitere Installationsanweisungen finden Sie unter [Getting started with OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse) (Erste Schritte mit OpenSSH).

   > [!NOTE]
   > Wenn Sie PowerShell als Standardshell für OpenSSH festlegen möchten, finden Sie weitere Informationen unter [Konfigurieren der Standardshell für OpenSSH in Windows](/windows-server/administration/openssh/openssh_server_configuration).

1. Bearbeiten Sie die `sshd_config`-Datei, die sich hier befindet: `$env:ProgramData\ssh`.

   Vergewissern Sie sich, dass die Kennwortauthentifizierung aktiviert ist:

   ```
   PasswordAuthentication yes
   ```

   Erstellen Sie das SSH-Subsystem, das einen PowerShell-Prozess auf dem Remotecomputer hostet:

   ```
   Subsystem powershell c:/progra~1/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   > [!NOTE]
   > Sie müssen den kurzen Namen von Version 8.3 für alle Dateipfade verwenden, die Leerzeichen enthalten. Es besteht ein Fehler in OpenSSH für Windows, der verhindert, dass Leerzeichen in ausführbaren Pfaden zu Subsystemen funktionieren. Weitere Informationen finden Sie in diesem [GitHub-Problem](https://github.com/PowerShell/Win32-OpenSSH/issues/784).
   >
   > Der kurze Name von Version 8.3 für den Ordner `Program Files` unter Windows lautet üblicherweise `Progra~1`. Sie können jedoch den folgenden Befehl verwenden, um dies sicherzustellen:
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

   Aktivieren Sie ggf. die Schlüsselauthentifizierung:

   ```
   PubkeyAuthentication yes
   ```

   Weitere Informationen finden Sie unter [OpenSSH-Schlüsselverwaltung](/windows-server/administration/openssh/openssh_keymanagement).

1. Starten Sie den **sshd**-Dienst neu.

   ```powershell
   Restart-Service sshd
   ```

1. Fügen Sie den Pfad der OpenSSH-Installation der Umgebungsvariablen „Path“ hinzu. Beispiel: `C:\Program Files\OpenSSH\`. Durch diesen Eintrag kann die Datei `ssh.exe` gefunden werden.

## <a name="set-up-on-an-ubuntu-1604-linux-computer"></a>Einrichten auf einem Linux-Computer unter Ubuntu 16.04

1. Weitere Informationen zur Installation der neuesten Version von PowerShell finden Sie unter [Installieren von PowerShell Core unter Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604).
1. Installieren Sie [Ubuntu OpenSSH Server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. Bearbeiten Sie die Datei `sshd_config` unter `/etc/ssh`.

   Vergewissern Sie sich, dass die Kennwortauthentifizierung aktiviert ist:

   ```
   PasswordAuthentication yes
   ```

   Fügen Sie einen Eintrag für das PowerShell-Subsystem hinzu:

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   Aktivieren Sie ggf. die Schlüsselauthentifizierung:

   ```
   PubkeyAuthentication yes
   ```

1. Starten Sie den **sshd**-Dienst neu.

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-a-macos-computer"></a>Einrichten auf einem macOS-Computer

1. Weitere Informationen zur Installation der neuesten Version von PowerShell finden Sie unter [Installieren von PowerShell Core unter macOS](../../install/installing-powershell-core-on-macos.md).

   Vergewissern Sie sich, dass SSH-Remoting aktiviert ist, indem Sie die folgenden Schritte ausführen:

   1. Öffnen Sie `System Preferences`.
   1. Klicken Sie auf `Sharing`.
   1. Aktivieren Sie `Remote Login`, um `Remote Login: On` festzulegen.
   1. Erteilen Sie den entsprechenden Benutzern Zugriff.

1. Bearbeiten Sie die Datei `sshd_config` unter `/private/etc/ssh/sshd_config`.

   Verwenden Sie einen Text-Editor, z.B. **nano**:

   ```bash
   sudo nano /private/etc/ssh/sshd_config
   ```

   Vergewissern Sie sich, dass die Kennwortauthentifizierung aktiviert ist:

   ```
   PasswordAuthentication yes
   ```

   Fügen Sie einen Eintrag für das PowerShell-Subsystem hinzu:

   ```
   Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   Aktivieren Sie ggf. die Schlüsselauthentifizierung:

   ```
   PubkeyAuthentication yes
   ```

1. Starten Sie den **sshd**-Dienst neu.

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a>Authentifizierung

PowerShell-Remoting über SSH basiert auf dem Authentifizierungsaustausch zwischen dem SSH-Client und dem SSH-Dienst und implementiert selbst keine Authentifizierungsschemas. Infolgedessen werden alle konfigurierten Authentifizierungsschemas, einschließlich der mehrstufigen Authentifizierung, von SSH und unabhängig von PowerShell verarbeitet. Sie können den SSH-Dienst beispielsweise für die Authentifizierung mit öffentlichen Schlüsseln oder die Verwendung eines Einmalkennworts zur Erhöhung der Sicherheit konfigurieren. Die Konfiguration einer mehrstufigen Authentifizierung wird in dieser Dokumentation nicht beschrieben. Bevor Sie versuchen, eine mehrstufige Authentifizierung mit PowerShell-Remoting zu verwenden, informieren Sie sich in der Dokumentation für SSH, wie Sie eine mehrstufige Authentifizierung richtig konfigurieren, und testen Sie, ob diese außerhalb von PowerShell funktioniert.

## <a name="powershell-remoting-example"></a>Beispiel für das PowerShell-Remoting

Sie können das Remoting am einfachsten auf einem einzelnen Computer testen. In diesem Beispiel haben wir eine Remotesitzung mit demselben Linux-Computer erstellt. Wir verwenden PowerShell-Cmdlets interaktiv, damit wir Eingabeaufforderungen von SSH sehen, die zum Überprüfen des Hostcomputers und zur Kennworteingabe auffordern. Sie können dies auch auf einem Windows-Computer durchführen, um sicherzustellen, dass das Remoting funktioniert. Verwenden Sie dann Remoting zwischen Computern, indem Sie den Hostnamen ändern.

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

### <a name="known-issues"></a>Bekannte Probleme

Der Befehl **sudo** funktioniert bei Remotesitzungen auf Linux-Computern nicht.

## <a name="see-also"></a>Siehe auch

[Installieren von PowerShell Core unter Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[Installieren von PowerShell Core unter macOS](../../install/installing-powershell-core-on-macos.md)

[Installing PowerShell Core on Windows (Installieren von PowerShell Core unter Windows)](../../install/installing-powershell-core-on-windows.md#msi)

[Installation von OpenSSH für Windows Server 2019 und Windows 10](/windows-server/administration/openssh/openssh_overview)

[OpenSSH-Schlüsselverwaltung](/windows-server/administration/openssh/openssh_keymanagement)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
