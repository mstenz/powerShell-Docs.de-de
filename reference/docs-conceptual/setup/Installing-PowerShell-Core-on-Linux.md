---
title: Installieren von PowerShell Core unter Linux
description: Informationen zur Installation von PowerShell Core auf verschiedenen Linux-Distributionen
ms.date: 08/06/2018
ms.openlocfilehash: d60e1d5a89b6907b67c19b8cfcde969be156bd60
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851288"
---
# <a name="installing-powershell-core-on-linux"></a>Installieren von PowerShell Core unter Linux

Unterstützt [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] und [Arch Linux][arch].

Für nicht offiziell unterstützte Linux-Distributionen können Sie versuchen, das [Snap-Paket für PowerShell][snap] zu verwenden.
Stattdessen können Sie auch versuchen, PowerShell-Binärdateien über das [`tar.gz`-Archiv][tar] für Linux bereitzustellen. Dafür müssen Sie aber basierend auf Ihrem Betriebssystem die benötigten Abhängigkeiten in zusätzlichen Schritten einrichten.

Sämtliche Pakete sind auf der Seite [Releases][] über GitHub verfügbar.
Führen Sie `pwsh` über das Terminal aus, nachdem Sie das Paket installiert haben.

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u18]: #ubuntu-1810
[u18]: #ubuntu-1804
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a>Installieren von Vorschauversionen

Wenn eine Vorschauversion von PowerShell Core für Linux über ein Paketrepository installiert wird, ändert sich der Paketname von `powershell` in `powershell-preview`.

Bei einer Installation über einen direkten Download wird nur der Dateiname geändert.

In der nachfolgenden Tabelle werden die Befehle aufgeführt, über die Sie Pakete stabiler Versionen und von Vorschauversionen unter Verwendung der verschiedenen Paket-Manager installieren können:

|Distribution(en)|Befehl für die stabile Version | Befehl für die Vorschauversion |
|---------------|---------------|-----------------|
| Ubuntu, Debian |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| CentOS, RedHat |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| OpenSUSE |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| Fedora   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Installation über das Paketrepository: Ubuntu 14.04

PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.
Dies ist die bevorzugte Methode.

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/14.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Registrieren Sie das Microsoft-Repository als Superuser.
Von nun an müssen Sie nur `sudo apt-get upgrade powershell` verwenden, um die Installation zu aktualisieren.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Installation über einen direkten Download: Ubuntu 14.04

Laden Sie das Debian-Paket `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`
über die Seite [Releases][] auf den Ubuntu-Computer herunter.

Führen Sie dann folgenden Befehl im Terminal aus:

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.
> Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.

### <a name="uninstallation---ubuntu-1404"></a>Deinstallation: Ubuntu 14.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Installation über das Paketrepository: Ubuntu 16.04

PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.
Dies ist die bevorzugte Methode.

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Installation über einen direkten Download: Ubuntu 16.04

Laden Sie das Debian-Paket `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`
über die Seite [Releases][] auf den Ubuntu-Computer herunter.

Führen Sie dann folgenden Befehl im Terminal aus:

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.
> Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.

### <a name="uninstallation---ubuntu-1604"></a>Deinstallation: Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

> [!NOTE]
> Die Unterstützung für Ubuntu 18.04. wurde nach `6.1.0-preview.2` hinzugefügt.

### <a name="installation-via-package-repository---ubuntu-1804"></a>Installation über das Paketrepository: Ubuntu 18.04

PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.
Dies ist die bevorzugte Methode.

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Installation über einen direkten Download: Ubuntu 18.04

Laden Sie das Debian-Paket `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`
über die Seite [Releases][] auf den Ubuntu-Computer herunter.

Führen Sie dann folgenden Befehl im Terminal aus:

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.
> Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.

### <a name="uninstallation---ubuntu-1804"></a>Deinstallation: Ubuntu 18.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a>Ubuntu 18.10

> [!NOTE]
> Die Unterstützung für Ubuntu 18.10. wurde nach `6.1.0-preview.3` hinzugefügt.
> Bei 18.10 handelt es sich um einen Daily Build, daher wird diese Version nur von der Community unterstützt.

Die Installation auf 18.10 wird über `snapd` unterstützt. Eine vollständige Anweisung finden Sie unter [Snap-Paket][snap].

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Installation über das Paketrepository: Debian 8

PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.
Dies ist die bevorzugte Methode.

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.

### <a name="installation-via-direct-download---debian-8"></a>Installation über einen direkten Download: Debian 8

Laden Sie das Debian-Paket `powershell_6.1.0-1.debian.8_amd64.deb`
über die Seite [Releases][] auf den Debian-Computer herunter.

Führen Sie dann folgenden Befehl im Terminal aus:

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.
> Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.

### <a name="uninstallation---debian-8"></a>Deinstallation: Debian 8

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Installation über das Paketrepository: Debian 9

PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.
Dies ist die bevorzugte Methode.

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.

### <a name="installation-via-direct-download---debian-9"></a>Installation über einen direkten Download: Debian 9

Laden Sie das Debian-Paket `powershell_6.1.0-1.debian.9_amd64.deb`
über die Seite [Releases][] auf den Debian-Computer herunter.

Führen Sie dann folgenden Befehl im Terminal aus:

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>Deinstallation: Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> Dieses Paket funktioniert ebenfalls unter Oracle Linux 7.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Installation über das Paketrepository (bevorzugt): CentOS 7

PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo yum update powershell` verwenden, um Updates für PowerShell auszuführen.

### <a name="installation-via-direct-download---centos-7"></a>Installation über einen direkten Download: CentOS 7

Laden Sie mithilfe von [CentOS 7][] das RPM-Paket `powershell-6.1.0-1.rhel.7.x86_64.rpm`
über die Seite [Releases][] auf den CentOS-Computer herunter.

Führen Sie dann folgenden Befehl im Terminal aus:

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Deinstallation: CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux 7 (RHEL)

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Installation über ein Paketrepository (bevorzugt): Red Hat Enterprise Linux 7 (RHEL)

PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo yum update powershell` verwenden, um Updates für PowerShell auszuführen.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Installation über einen direkten Download: Red Hat Enterprise Linux 7 (RHEL)

Laden Sie das RPM-Paket `powershell-6.1.0-1.rhel.7.x86_64.rpm`
über die Seite [Releases][] auf den Red Hat Enterprise Linux-Computer herunter.

Führen Sie dann folgenden Befehl im Terminal aus:

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Deinstallation: Red Hat Enterprise Linux 7 (RHEL)

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a>openSUSE 42.3

Bei der Installation von PowerShell Core verursacht `zypper` eventuell den folgenden Fehler:

```Output
Problem: nothing provides libcurl needed by powershell-6.1.0-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.1.0-1.rhel.7.x86_64
 Solution 2: break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies
```

Stellen Sie in diesem Fall sicher, dass eine kompatible `libcurl`-Bibliothek vorhanden ist, indem Sie überprüfen, ob der folgende Befehl das `libcurl4`-Paket als installiert anzeigt:

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

Wählen Sie bei der Installation des PowerShell-Pakets die Lösung `break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies` aus.

### <a name="installation-via-package-repository-preferred---opensuse-423"></a>Installation über das Paketrepository (bevorzugt): openSUSE 42.3

PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Repository
zypper ar https://packages.microsoft.com/rhel/7/prod/

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-423"></a>Installation über einen direkten Download: openSUSE 42.3

Laden Sie das RPM-Paket `powershell-6.1.0-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den OpenSUSE-Computer herunter.

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a>Deinstallation: openSUSE 42.3

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> Fedora 28 wird nur in PowerShell Core 6.1 und höher unterstützt.

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a>Installation über das Paketrepository (bevorzugt): Fedora 27, Fedora 28

PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a>Installation über einen direkten Download: Fedora 27, Fedora 28

Laden Sie das RPM-Paket `powershell-6.1.0-1.rhel.7.x86_64.rpm`
über die Seite [Releases][] auf den Fedora-Computer herunter.

Führen Sie dann folgenden Befehl im Terminal aus:

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a>Deinstallation: Fedora 27, Fedora 28

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

> [!NOTE]
> Die Unterstützung von Arch wird noch getestet.

PowerShell ist über das Benutzerrepository [Arch Linux][] verfügbar.

* Es kann gemeinsam mit dem [zuletzt markierten Release][arch-release] installiert werden.
* Es kann gemeinsam mit dem [letzten Commit für den Master][arch-git] kompiliert werden.
* Es kann mithilfe der [zuletzt veröffentlichten Binärdatei][arch-bin] kompiliert werden.

Pakete im Benutzerrepository „Arch Linux“ werden von der Community verwaltet. Es gibt keinen offiziellen Support.

Weitere Informationen zum Installieren von Paketen aus dem Benutzerrepository „Arch Linux“ finden Sie im [Arch Linux-Wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) oder in [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) der Community.

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a>Snap-Paket

### <a name="getting-snapd"></a>Abrufen von snapd

`snapd` ist für das Ausführen von Snap-Paketen erforderlich.
Halten Sie sich an [diese Anweisungen](https://docs.snapcraft.io/core/install), um sicherzustellen, dass `snapd` installiert ist.

### <a name="installation-via-snap"></a>Installation über Snap

PowerShell Core für Linux wird im [Snap-Store](https://snapcraft.io/store) veröffentlicht, um die Installation (und die Updates) zu vereinfachen.
Dies ist die bevorzugte Methode.

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

Nach der Installation führt Snap automatisch ein Upgrade durch, Sie können jedoch ein Upgrade mithilfe von `sudo snap refresh powershell-preview` auslösen.

### <a name="uninstallation"></a>Deinstallation

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a>Kali

### <a name="installation"></a>Installation

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-9_amd64.deb
dpkg -i libicu57_57.1-9_amd64.deb
apt-get update && apt-get install -y curl gnupg apt-transport-https

# Add Microsoft public repository key to APT
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

# Add Microsoft package repository to the source list
echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" | tee /etc/apt/sources.list.d/powershell.list

# Install PowerShell package
apt-get update && apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a>Deinstallation: Kali

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> Die Unterstützung von Raspbian wird noch getestet.

Derzeit wird PowerShell nur unter Raspbian Stretch unterstützt.

Außerdem funktioniert CoreCLR (und daher auch PowerShell Core) nur auf Geräten mit Pi 2 und Pi 3, da andere Geräte, wie z.B. [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), einen nicht unterstützten Prozessor haben.

Laden Sie [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) herunter, und folgen Sie den [Installationsanweisungen](https://www.raspberrypi.org/documentation/installation/installing-images/README.md), um es zu installieren.

### <a name="installation"></a>Installation

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.1.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

Optional können Sie eine symbolische Verknüpfung erstellen, damit Sie PowerShell ohne Angabe eines Pfads auf die Binärdatei „pwsh“ starten können.

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>Deinstallation: Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>Archive der Binärdateien

`tar.gz`-Archive der PowerShell-Binärdateien werden für Linux-Plattformen zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu aktivieren.

### <a name="dependencies"></a>Abhängigkeiten

PowerShell erstellt portierbare Binärdateien für alle Linux-Distributionen.
Allerdings erfordert die .NET Core-Laufzeit, und damit auch PowerShell, verschiedene Abhängigkeiten für die verschiedenen Distributionen.

Im folgenden Diagramm werden die Abhängigkeiten von .NET Core 2.0 für die verschiedenen Linux-Distributionen dargestellt, die offiziell unterstützt werden.

| Betriebssystem                 | Abhängigkeiten |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.10       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Ubuntu 18.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60 |
| Debian 8 (Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> openSUSE 42.3 | libunwind, libcurl, openssl-libs, libicu |
| Fedora 27 <br> Fedora 28 | libunwind, libcurl, openssl-libs, libicu, compat-openssl10 |

Sie müssen zur Bereitstellung von PowerShell-Binärdateien für nicht offiziell unterstützte Linux-Distributionen die notwendigen Abhängigkeiten für das Zielbetriebssystem über zusätzliche Schritte installieren.
Beispielsweise installiert die [Amazon Linux-Dockerfile][amazon-dockerfile] zuerst die Abhängigkeiten und extrahiert anschließend erst das Linux-`tar.gz`-Archiv.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Installation: Archive von Binärdateien

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a>Deinstallation: Archive von Binärdateien

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Pfade

* `$PSHOME` ist `/opt/microsoft/powershell/6.1.0/`.
* Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.
* Standardprofile werden über `$PSHOME/profile.ps1` gelesen.
* Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.
* Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.
* Standardmodule werden über `$PSHOME/Modules` gelesen.
* Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.

Die Profile beachten die Konfigurationen von PowerShell pro Host. Das bedeutet, die hostspezifischen Standardprofile sind an denselben Orten unter `Microsoft.PowerShell_profile.ps1` gespeichert.

PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter Linux ein.

[Releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
