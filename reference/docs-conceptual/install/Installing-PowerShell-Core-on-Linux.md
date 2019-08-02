---
title: Installieren von PowerShell Core unter Linux
description: Informationen zur Installation von PowerShell Core auf verschiedenen Linux-Distributionen
ms.date: 07/19/2019
ms.openlocfilehash: 929b153ef784f3203cd31a0e2fc52e744a07532f
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/26/2019
ms.locfileid: "68372200"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="ca6c3-103">Installieren von PowerShell Core unter Linux</span><span class="sxs-lookup"><span data-stu-id="ca6c3-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="ca6c3-104">Unterstützt [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] und [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="ca6c3-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="ca6c3-105">Für nicht offiziell unterstützte Linux-Distributionen können Sie versuchen, PowerShell über das [Snap-Paket für PowerShell][snap] zu installieren.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="ca6c3-106">Stattdessen können Sie auch versuchen, PowerShell-Binärdateien über das [`tar.gz`-Archiv][tar] für Linux bereitzustellen. Dafür müssen Sie aber die für Ihr Betriebssystem erforderlichen Abhängigkeiten in zusätzlichen Schritten einrichten.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="ca6c3-107">Sämtliche Pakete sind auf der Seite [Freigaben][] über GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="ca6c3-108">Nachdem Sie das Paket installiert haben, führen Sie `pwsh` über das Terminal aus.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-108">After the package is installed, run `pwsh` from a terminal.</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="ca6c3-109">Installieren von Vorschauversionen</span><span class="sxs-lookup"><span data-stu-id="ca6c3-109">Installing Preview Releases</span></span>

<span data-ttu-id="ca6c3-110">Wenn eine Vorschauversion von PowerShell Core für Linux über ein Paketrepository installiert wird, ändert sich der Paketname von `powershell` in `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="ca6c3-111">Bei einer Installation über einen direkten Download wird nur der Dateiname geändert.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-111">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="ca6c3-112">In der nachfolgenden Tabelle werden die Befehle aufgeführt, über die Sie Pakete stabiler Versionen und von Vorschauversionen mithilfe der verschiedenen Paket-Manager installieren können:</span><span class="sxs-lookup"><span data-stu-id="ca6c3-112">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="ca6c3-113">Distribution(en)</span><span class="sxs-lookup"><span data-stu-id="ca6c3-113">Distribution(s)</span></span>|<span data-ttu-id="ca6c3-114">Befehl für die stabile Version</span><span class="sxs-lookup"><span data-stu-id="ca6c3-114">Stable Command</span></span> | <span data-ttu-id="ca6c3-115">Befehl für die Vorschauversion</span><span class="sxs-lookup"><span data-stu-id="ca6c3-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="ca6c3-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="ca6c3-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="ca6c3-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="ca6c3-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="ca6c3-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="ca6c3-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="ca6c3-119">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ca6c3-119">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="ca6c3-120">Installation über das Paketrepository: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ca6c3-120">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="ca6c3-121">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-121">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="ca6c3-122">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="ca6c3-122">The preferred method is as follows:</span></span>

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

<span data-ttu-id="ca6c3-123">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-123">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="ca6c3-124">Nach der Registrierung können Sie PowerShell mit `sudo apt-get upgrade powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-124">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="ca6c3-125">Installation über einen direkten Download: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ca6c3-125">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="ca6c3-126">Laden Sie das Debian-Paket `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` über die Seite [Freigaben][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-126">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="ca6c3-127">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="ca6c3-127">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="ca6c3-128">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-128">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="ca6c3-129">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-129">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="ca6c3-130">Deinstallation: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ca6c3-130">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="ca6c3-131">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ca6c3-131">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="ca6c3-132">Installation über das Paketrepository: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ca6c3-132">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="ca6c3-133">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-133">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="ca6c3-134">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="ca6c3-134">The preferred method is as follows:</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Enable the "universe" repositories
sudo add-apt-repository universe

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="ca6c3-135">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-135">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="ca6c3-136">Nach der Registrierung können Sie PowerShell mit `sudo apt-get upgrade powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-136">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="ca6c3-137">Installation über einen direkten Download: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ca6c3-137">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="ca6c3-138">Laden Sie das Debian-Paket `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` über die Seite [Freigaben][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-138">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="ca6c3-139">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="ca6c3-139">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="ca6c3-140">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-140">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="ca6c3-141">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="ca6c3-142">Deinstallation: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ca6c3-142">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="ca6c3-143">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="ca6c3-143">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="ca6c3-144">Da Ubuntu 18.10 ein [Zwischenrelease](https://www.ubuntu.com/about/release-cycle) ist, wird es nur von der [Community unterstützt](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="ca6c3-144">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="ca6c3-145">Die Installation auf 18.10 wird über `snapd` unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-145">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="ca6c3-146">Eine vollständige Anleitung finden Sie unter [Snap-Paket][snap].</span><span class="sxs-lookup"><span data-stu-id="ca6c3-146">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="ca6c3-147">Debian 8</span><span class="sxs-lookup"><span data-stu-id="ca6c3-147">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="ca6c3-148">Installation über das Paketrepository: Debian 8</span><span class="sxs-lookup"><span data-stu-id="ca6c3-148">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="ca6c3-149">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-149">PowerShell Core, for Linux, is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="ca6c3-150">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="ca6c3-150">The preferred method is as follows:</span></span>

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

<span data-ttu-id="ca6c3-151">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-151">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="ca6c3-152">Nach der Registrierung können Sie PowerShell mit `sudo apt-get upgrade powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-152">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="ca6c3-153">Debian 9</span><span class="sxs-lookup"><span data-stu-id="ca6c3-153">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="ca6c3-154">Installation über das Paketrepository: Debian 9</span><span class="sxs-lookup"><span data-stu-id="ca6c3-154">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="ca6c3-155">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-155">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="ca6c3-156">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="ca6c3-156">The preferred method is as follows:</span></span>

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

<span data-ttu-id="ca6c3-157">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-157">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="ca6c3-158">Nach der Registrierung können Sie PowerShell mit `sudo apt-get upgrade powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-158">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="ca6c3-159">Installation über einen direkten Download: Debian 9</span><span class="sxs-lookup"><span data-stu-id="ca6c3-159">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="ca6c3-160">Laden Sie das Debian-Paket `powershell_6.2.0-1.debian.9_amd64.deb` über die Seite [Freigaben][] auf den Debian-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-160">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="ca6c3-161">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="ca6c3-161">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="ca6c3-162">Deinstallation: Debian 9</span><span class="sxs-lookup"><span data-stu-id="ca6c3-162">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="ca6c3-163">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ca6c3-163">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="ca6c3-164">Dieses Paket funktioniert unter Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-164">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="ca6c3-165">Installation über das Paketrepository (bevorzugt): CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ca6c3-165">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="ca6c3-166">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-166">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="ca6c3-167">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-167">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="ca6c3-168">Nach der Registrierung können Sie PowerShell mit `sudo yum update powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-168">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="ca6c3-169">Installation über einen direkten Download: CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ca6c3-169">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="ca6c3-170">Für [CentOS 7][]: Laden Sie das RPM-Paket `powershell-6.2.0-1.rhel.7.x86_64.rpm` über die Seite [Freigaben][] auf den CentOS-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-170">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="ca6c3-171">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="ca6c3-171">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ca6c3-172">Sie können RPM ohne Download installieren:</span><span class="sxs-lookup"><span data-stu-id="ca6c3-172">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="ca6c3-173">Deinstallation: CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ca6c3-173">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ca6c3-175">Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="ca6c3-175">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ca6c3-176">Installation über ein Paketrepository (bevorzugt): Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="ca6c3-176">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="ca6c3-177">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-177">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="ca6c3-178">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-178">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="ca6c3-179">Nach der Registrierung können Sie PowerShell mit `sudo yum update powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-179">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ca6c3-180">Installation über einen direkten Download: Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="ca6c3-180">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="ca6c3-181">Laden Sie das RPM-Paket `powershell-6.2.0-1.rhel.7.x86_64.rpm` über die Seite [Freigaben][] auf den Red Hat Enterprise Linux-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-181">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="ca6c3-182">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="ca6c3-182">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ca6c3-183">Sie können RPM ohne Download installieren:</span><span class="sxs-lookup"><span data-stu-id="ca6c3-183">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ca6c3-184">Deinstallation: Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="ca6c3-184">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="ca6c3-185">openSUSE</span><span class="sxs-lookup"><span data-stu-id="ca6c3-185">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="ca6c3-186">Installation: openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="ca6c3-186">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="ca6c3-187">Installation: openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="ca6c3-187">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="ca6c3-188">Deinstallation: openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="ca6c3-188">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="ca6c3-189">Fedora</span><span class="sxs-lookup"><span data-stu-id="ca6c3-189">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="ca6c3-190">Fedora 28 wird nur in PowerShell Core 6.1 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-190">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="ca6c3-191">Installation über das Paketrepository (bevorzugt): Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ca6c3-191">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="ca6c3-192">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="ca6c3-193">Installation über einen direkten Download: Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ca6c3-193">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="ca6c3-194">Laden Sie das RPM-Paket `powershell-6.2.0-1.rhel.7.x86_64.rpm` über die Seite [Freigaben][] auf den Fedora-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-194">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="ca6c3-195">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="ca6c3-195">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ca6c3-196">Sie können RPM ohne Download installieren:</span><span class="sxs-lookup"><span data-stu-id="ca6c3-196">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="ca6c3-197">Deinstallation: Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ca6c3-197">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="ca6c3-198">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="ca6c3-198">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="ca6c3-199">Die Unterstützung von Arch wird noch getestet.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-199">Arch support is experimental.</span></span>

<span data-ttu-id="ca6c3-200">PowerShell ist über das Benutzerrepository [Arch Linux][] verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-200">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="ca6c3-201">Es kann gemeinsam mit dem [zuletzt markierten Release][arch-release] kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-201">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="ca6c3-202">Es kann gemeinsam vom [letzten Commit für den Master][arch-git] aus kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-202">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="ca6c3-203">Es kann mithilfe der [zuletzt zur Veröffentlichung bestimmten Binärdatei][arch-bin] installiert werden.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-203">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="ca6c3-204">Pakete im Benutzerrepository „Arch Linux“ werden von der Community verwaltet. Es gibt keinen offiziellen Support.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-204">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="ca6c3-205">Weitere Informationen zum Installieren von Paketen aus dem Benutzerrepository „Arch Linux“ finden Sie im [Arch Linux-Wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) oder in [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) der Community.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-205">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="ca6c3-207">Snap-Paket</span><span class="sxs-lookup"><span data-stu-id="ca6c3-207">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="ca6c3-208">Abrufen von snapd</span><span class="sxs-lookup"><span data-stu-id="ca6c3-208">Getting snapd</span></span>

<span data-ttu-id="ca6c3-209">`snapd` ist für das Ausführen von Snap-Paketen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-209">`snapd` is required to run snaps.</span></span> <span data-ttu-id="ca6c3-210">Halten Sie sich an [diese Anweisungen](https://docs.snapcraft.io/core/install), um sicherzustellen, dass `snapd` installiert ist.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-210">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="ca6c3-211">Installation über Snap</span><span class="sxs-lookup"><span data-stu-id="ca6c3-211">Installation via Snap</span></span>

<span data-ttu-id="ca6c3-212">PowerShell Core für Linux wird im [Snap-Store](https://snapcraft.io/store) veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-212">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="ca6c3-213">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="ca6c3-213">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="ca6c3-214">Gehen Sie folgendermaßen vor, wenn Sie eine Vorschauversion installieren möchten:</span><span class="sxs-lookup"><span data-stu-id="ca6c3-214">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="ca6c3-215">Nach der Installation wird für Snap automatisch ein Upgrade durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-215">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="ca6c3-216">Sie können ein Upgrade mit `sudo snap refresh powershell` oder `sudo snap refresh powershell-preview` auslösen.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-216">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="ca6c3-217">Deinstallation</span><span class="sxs-lookup"><span data-stu-id="ca6c3-217">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="ca6c3-218">oder</span><span class="sxs-lookup"><span data-stu-id="ca6c3-218">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="ca6c3-219">Kali</span><span class="sxs-lookup"><span data-stu-id="ca6c3-219">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="ca6c3-220">Installation: Kali</span><span class="sxs-lookup"><span data-stu-id="ca6c3-220">Installation - Kali</span></span>

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-6+deb9u2_amd64.deb
dpkg -i libicu57_57.1-6+deb9u2_amd64.deb
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

### <a name="uninstallation---kali"></a><span data-ttu-id="ca6c3-221">Deinstallation: Kali</span><span class="sxs-lookup"><span data-stu-id="ca6c3-221">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="ca6c3-222">Raspbian</span><span class="sxs-lookup"><span data-stu-id="ca6c3-222">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="ca6c3-223">Die Unterstützung von Raspbian wird noch getestet.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-223">Raspbian support is experimental.</span></span>

<span data-ttu-id="ca6c3-224">Derzeit wird PowerShell nur unter Raspbian Stretch unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-224">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="ca6c3-225">Außerdem funktionieren CoreCLR und PowerShell Core nur auf Geräten mit Pi 2 und Pi 3, da andere Geräte, wie z.B. [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), einen nicht unterstützten Prozessor haben.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-225">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="ca6c3-226">Laden Sie [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) herunter, und folgen Sie den [Installationsanweisungen](https://www.raspberrypi.org/documentation/installation/installing-images/README.md), um es zu installieren.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-226">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="ca6c3-227">Installation: Raspbian</span><span class="sxs-lookup"><span data-stu-id="ca6c3-227">Installation - Raspbian</span></span>

```sh
###################################
# Prerequisites

# Update package lists
sudo apt-get update

# Install libunwind8 and libssl1.0
# Regex is used to ensure that we do not install libssl1.0-dev, as it is a variant that is not required
sudo apt-get install '^libssl1.0.[0-9]$' libunwind8 -y

###################################
# Download and extract PowerShell

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="ca6c3-228">Optional können Sie eine symbolische Verknüpfung erstellen, damit Sie PowerShell ohne Angabe des Pfads zur Binärdatei `pwsh` starten können.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-228">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="ca6c3-229">Deinstallation: Raspbian</span><span class="sxs-lookup"><span data-stu-id="ca6c3-229">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="ca6c3-230">Archive der Binärdateien</span><span class="sxs-lookup"><span data-stu-id="ca6c3-230">Binary Archives</span></span>

<span data-ttu-id="ca6c3-231">`tar.gz`-Archive der PowerShell-Binärdateien werden für Linux-Plattformen zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-231">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="ca6c3-232">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="ca6c3-232">Dependencies</span></span>

<span data-ttu-id="ca6c3-233">PowerShell erstellt portierbare Binärdateien für alle Linux-Distributionen.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-233">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="ca6c3-234">Allerdings erfordern die .NET Core-Runtime und PowerShell verschiedene Abhängigkeiten für die verschiedenen Distributionen.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-234">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="ca6c3-235">Im folgenden Diagramm werden die Abhängigkeiten von .NET Core 2.0 für die verschiedenen Linux-Distributionen dargestellt, die offiziell unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-235">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="ca6c3-236">Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="ca6c3-236">OS</span></span>                 | <span data-ttu-id="ca6c3-237">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="ca6c3-237">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="ca6c3-238">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ca6c3-238">Ubuntu 16.04</span></span>       | <span data-ttu-id="ca6c3-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ca6c3-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ca6c3-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="ca6c3-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="ca6c3-241">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="ca6c3-241">Ubuntu 17.10</span></span>       | <span data-ttu-id="ca6c3-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ca6c3-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ca6c3-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="ca6c3-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="ca6c3-244">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ca6c3-244">Ubuntu 18.04</span></span>       | <span data-ttu-id="ca6c3-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ca6c3-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ca6c3-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="ca6c3-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="ca6c3-247">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="ca6c3-247">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="ca6c3-248">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ca6c3-248">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ca6c3-249">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="ca6c3-249">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="ca6c3-250">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="ca6c3-250">Debian 9 (Stretch)</span></span> | <span data-ttu-id="ca6c3-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ca6c3-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ca6c3-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="ca6c3-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="ca6c3-253">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ca6c3-253">CentOS 7</span></span> <br> <span data-ttu-id="ca6c3-254">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="ca6c3-254">Oracle Linux 7</span></span> <br> <span data-ttu-id="ca6c3-255">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="ca6c3-255">RHEL 7</span></span> | <span data-ttu-id="ca6c3-256">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="ca6c3-256">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="ca6c3-257">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="ca6c3-257">openSUSE 42.3</span></span> | <span data-ttu-id="ca6c3-258">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="ca6c3-258">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="ca6c3-259">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="ca6c3-259">openSUSE Leap 15</span></span> | <span data-ttu-id="ca6c3-260">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="ca6c3-260">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="ca6c3-261">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="ca6c3-261">Fedora 27</span></span> <br> <span data-ttu-id="ca6c3-262">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ca6c3-262">Fedora 28</span></span> | <span data-ttu-id="ca6c3-263">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="ca6c3-263">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="ca6c3-264">Sie müssen zur Bereitstellung von PowerShell-Binärdateien für nicht offiziell unterstützte Linux-Distributionen die notwendigen Abhängigkeiten für das Zielbetriebssystem über zusätzliche Schritte installieren.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-264">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="ca6c3-265">Beispielsweise installiert die [Amazon Linux-Dockerfile][amazon-dockerfile] zuerst die Abhängigkeiten und extrahiert anschließend das `tar.gz`-Archiv für Linux.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-265">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="ca6c3-266">Installation: Archive von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="ca6c3-266">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="ca6c3-267">Linux</span><span class="sxs-lookup"><span data-stu-id="ca6c3-267">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="ca6c3-268">Deinstallation: Archive von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="ca6c3-268">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="ca6c3-269">Pfade</span><span class="sxs-lookup"><span data-stu-id="ca6c3-269">Paths</span></span>

* <span data-ttu-id="ca6c3-270">`$PSHOME` ist `/opt/microsoft/powershell/6.2.0/`.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-270">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="ca6c3-271">Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-271">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="ca6c3-272">Standardprofile werden über `$PSHOME/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-272">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="ca6c3-273">Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-273">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="ca6c3-274">Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-274">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="ca6c3-275">Standardmodule werden über `$PSHOME/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-275">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="ca6c3-276">Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-276">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="ca6c3-277">Die Profile beachten die Konfigurationen von PowerShell pro Host. Das bedeutet, die hostspezifischen Standardprofile sind an denselben Orten unter `Microsoft.PowerShell_profile.ps1` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-277">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="ca6c3-278">PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter Linux ein.</span><span class="sxs-lookup"><span data-stu-id="ca6c3-278">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Freigaben]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
