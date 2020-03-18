---
title: Installieren von PowerShell unter Linux
description: Informationen zur Installation von PowerShell auf verschiedenen Linux-Distributionen
ms.date: 03/09/2020
ms.openlocfilehash: 0c7b2bd804d07b2fcb61a61240b139f84fabd6db
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402537"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="dee98-103">Installieren von PowerShell unter Linux</span><span class="sxs-lookup"><span data-stu-id="dee98-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="dee98-104">Unterstützt [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 8][deb8], [Debian 9][deb9], [Debian 10][deb10], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], und [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="dee98-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 8][deb8], [Debian 9][deb9], [Debian 10][deb10], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="dee98-105">Für nicht offiziell unterstützte Linux-Distributionen können Sie versuchen, PowerShell über das [Snap-Paket für PowerShell][snap] zu installieren.</span><span class="sxs-lookup"><span data-stu-id="dee98-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="dee98-106">Stattdessen können Sie auch versuchen, PowerShell-Binärdateien über das [`tar.gz`-Archiv][tar] für Linux bereitzustellen. Dafür müssen Sie aber die für Ihr Betriebssystem erforderlichen Abhängigkeiten in zusätzlichen Schritten einrichten.</span><span class="sxs-lookup"><span data-stu-id="dee98-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="dee98-107">Sämtliche Pakete sind auf der Seite [Freigaben][] über GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="dee98-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="dee98-108">Nachdem Sie das Paket installiert haben, führen Sie `pwsh` über das Terminal aus.</span><span class="sxs-lookup"><span data-stu-id="dee98-108">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="dee98-109">Führen Sie `pwsh-preview` aus, wenn Sie eine [Vorschauversion](#installing-preview-releases) installiert haben.</span><span class="sxs-lookup"><span data-stu-id="dee98-109">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="dee98-110">PowerShell 7 ist ein direktes Upgrade, mit dem PowerShell Core 6.x entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="dee98-110">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="dee98-111">Der Ordner `/usr/local/microsoft/powershell/6` wird durch `/usr/local/microsoft/powershell/7` ersetzt.</span><span class="sxs-lookup"><span data-stu-id="dee98-111">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="dee98-112">Wenn Sie PowerShell 6 und PowerShell 7 parallel ausführen müssen, installieren Sie PowerShell 6 mithilfe der [binary archive](#binary-archives)-Methode neu.</span><span class="sxs-lookup"><span data-stu-id="dee98-112">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[u1904]: #ubuntu-1904
[deb8]: #debian-8
[deb9]: #debian-9
[deb10]: #debian-10
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives


## <a name="installing-preview-releases"></a><span data-ttu-id="dee98-113">Installieren von Vorschauversionen</span><span class="sxs-lookup"><span data-stu-id="dee98-113">Installing Preview Releases</span></span>

<span data-ttu-id="dee98-114">Wenn eine Vorschauversion von PowerShell für Linux über ein Paketrepository installiert wird, ändert sich der Paketname von `powershell` in `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="dee98-114">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="dee98-115">Bei einer Installation über einen direkten Download wird nur der Dateiname geändert.</span><span class="sxs-lookup"><span data-stu-id="dee98-115">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="dee98-116">In der nachfolgenden Tabelle werden die Befehle aufgeführt, über die Sie Pakete stabiler Versionen und von Vorschauversionen mithilfe der verschiedenen Paket-Manager installieren können:</span><span class="sxs-lookup"><span data-stu-id="dee98-116">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="dee98-117">Distribution(en)</span><span class="sxs-lookup"><span data-stu-id="dee98-117">Distribution(s)</span></span> |            <span data-ttu-id="dee98-118">Befehl für die stabile Version</span><span class="sxs-lookup"><span data-stu-id="dee98-118">Stable Command</span></span>            |               <span data-ttu-id="dee98-119">Befehl für die Vorschauversion</span><span class="sxs-lookup"><span data-stu-id="dee98-119">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="dee98-120">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="dee98-120">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="dee98-121">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="dee98-121">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="dee98-122">Fedora</span><span class="sxs-lookup"><span data-stu-id="dee98-122">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="ubuntu-1604"></a><span data-ttu-id="dee98-123">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="dee98-123">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="dee98-124">Installation über das Paketrepository: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="dee98-124">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="dee98-125">PowerShell für Linux wird in Paketrepositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="dee98-125">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="dee98-126">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="dee98-126">The preferred method is as follows:</span></span>

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

<span data-ttu-id="dee98-127">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="dee98-127">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="dee98-128">Nach der Registrierung können Sie PowerShell mit `sudo apt-get upgrade powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="dee98-128">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="dee98-129">Installation über einen direkten Download: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="dee98-129">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="dee98-130">Laden Sie das Debian-Paket `powershell_7.0.0-1.ubuntu.16.04_amd64.deb` über die Seite [Freigaben][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="dee98-130">Download the Debian package `powershell_7.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="dee98-131">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="dee98-131">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="dee98-132">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="dee98-132">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="dee98-133">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="dee98-133">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="dee98-134">Deinstallation: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="dee98-134">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="dee98-135">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="dee98-135">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="dee98-136">Installation über das Paketrepository: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="dee98-136">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="dee98-137">PowerShell für Linux wird in Paketrepositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="dee98-137">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="dee98-138">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="dee98-138">The preferred method is as follows:</span></span>

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

<span data-ttu-id="dee98-139">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="dee98-139">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="dee98-140">Nach der Registrierung können Sie PowerShell mit `sudo apt-get upgrade powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="dee98-140">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="dee98-141">Installation über einen direkten Download: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="dee98-141">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="dee98-142">Laden Sie das Debian-Paket `powershell_7.0.0-1.ubuntu.18.04_amd64.deb` über die Seite [Freigaben][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="dee98-142">Download the Debian package `powershell_7.0.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="dee98-143">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="dee98-143">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="dee98-144">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="dee98-144">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="dee98-145">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="dee98-145">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="dee98-146">Deinstallation: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="dee98-146">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="dee98-147">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="dee98-147">Ubuntu 18.10</span></span>

<span data-ttu-id="dee98-148">Die Installation wird über `snapd` unterstützt.</span><span class="sxs-lookup"><span data-stu-id="dee98-148">Installation is supported via `snapd`.</span></span> <span data-ttu-id="dee98-149">Anweisungen finden Sie unter [Snap-Paket][snap].</span><span class="sxs-lookup"><span data-stu-id="dee98-149">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="dee98-150">Ubuntu 18.10 ist ein [Zwischenrelease](https://www.ubuntu.com/about/release-cycle), das von der [Community unterstützt](../powershell-support-lifecycle.md) wird.</span><span class="sxs-lookup"><span data-stu-id="dee98-150">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="dee98-151">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="dee98-151">Ubuntu 19.04</span></span>

<span data-ttu-id="dee98-152">Die Installation wird über `snapd` unterstützt.</span><span class="sxs-lookup"><span data-stu-id="dee98-152">Installation is supported via `snapd`.</span></span> <span data-ttu-id="dee98-153">Anweisungen finden Sie unter [Snap-Paket][snap].</span><span class="sxs-lookup"><span data-stu-id="dee98-153">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="dee98-154">Ubuntu 19.04 ist ein [Zwischenrelease](https://www.ubuntu.com/about/release-cycle), das von der [Community unterstützt](../powershell-support-lifecycle.md) wird.</span><span class="sxs-lookup"><span data-stu-id="dee98-154">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="dee98-155">Debian 8</span><span class="sxs-lookup"><span data-stu-id="dee98-155">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="dee98-156">Installation über das Paketrepository: Debian 8</span><span class="sxs-lookup"><span data-stu-id="dee98-156">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="dee98-157">PowerShell für Linux wird in Paketrepositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="dee98-157">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="dee98-158">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="dee98-158">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl apt-transport-https

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

<span data-ttu-id="dee98-159">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="dee98-159">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="dee98-160">Nach der Registrierung können Sie PowerShell mit `sudo apt-get upgrade powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="dee98-160">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="dee98-161">Debian 9</span><span class="sxs-lookup"><span data-stu-id="dee98-161">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="dee98-162">Installation über das Paketrepository: Debian 9</span><span class="sxs-lookup"><span data-stu-id="dee98-162">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="dee98-163">PowerShell für Linux wird in Paketrepositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="dee98-163">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="dee98-164">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="dee98-164">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl gnupg apt-transport-https

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

<span data-ttu-id="dee98-165">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="dee98-165">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="dee98-166">Nach der Registrierung können Sie PowerShell mit `sudo apt-get upgrade powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="dee98-166">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="dee98-167">Installation über einen direkten Download: Debian 9</span><span class="sxs-lookup"><span data-stu-id="dee98-167">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="dee98-168">Laden Sie das Debian-Paket `powershell_7.0.0-1.debian.9_amd64.deb` über die Seite [Freigaben][] auf den Debian-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="dee98-168">Download the Debian package `powershell_7.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="dee98-169">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="dee98-169">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="dee98-170">Deinstallation: Debian 9</span><span class="sxs-lookup"><span data-stu-id="dee98-170">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="dee98-171">Debian 10</span><span class="sxs-lookup"><span data-stu-id="dee98-171">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="dee98-172">Debian 10 wird nur in PowerShell 7.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="dee98-172">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="dee98-173">Installation über direkten Download: Debian 10</span><span class="sxs-lookup"><span data-stu-id="dee98-173">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="dee98-174">Laden Sie das tar.gz-Paket `powershell_7.0.0-linux-x64.tar.gz` über die Seite [Freigaben][] auf den Debian-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="dee98-174">Download the tar.gz package `powershell_7.0.0-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="dee98-175">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="dee98-175">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo apt-get update
# install the requirements
sudo apt-get install -y \
        less \
        locales \
        ca-certificates \
        libicu63 \
        libssl1.1 \
        libc6 \
        libgcc1 \
        libgssapi-krb5-2 \
        liblttng-ust0 \
        libstdc++6 \
        zlib1g \
        curl

# Download the powershell '.tar.gz' archive
curl -L  https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

## <a name="alpine-39-and-310"></a><span data-ttu-id="dee98-176">Alpine 3.9 und 3.10</span><span class="sxs-lookup"><span data-stu-id="dee98-176">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="dee98-177">Alpine 3.9 und 3.10 werden nur in PowerShell 7.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="dee98-177">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="dee98-178">Installation über direkten Download: Alpine 3.9 und 3.10</span><span class="sxs-lookup"><span data-stu-id="dee98-178">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="dee98-179">Laden Sie das tar.gz-Paket `powershell_7.0.0-linux-x64.tar.gz` über die Seite [Freigaben][] auf den Alpine-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="dee98-179">Download the tar.gz package `powershell_7.0.0-linux-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="dee98-180">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="dee98-180">Then, in the terminal, execute the following commands:</span></span>

```sh
# install the requirements
sudo apk add --no-cache \
    ca-certificates \
    less \
    ncurses-terminfo-base \
    krb5-libs \
    libgcc \
    libintl \
    libssl1.1 \
    libstdc++ \
    tzdata \
    userspace-rcu \
    zlib \
    icu-libs \
    curl

sudo apk -X https://dl-cdn.alpinelinux.org/alpine/edge/main add --no-cache \
    lttng-ust

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

## <a name="centos-7"></a><span data-ttu-id="dee98-181">CentOS 7:</span><span class="sxs-lookup"><span data-stu-id="dee98-181">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="dee98-182">Dieses Paket funktioniert unter Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="dee98-182">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="dee98-183">Installation über das Paketrepository (bevorzugt): CentOS 7</span><span class="sxs-lookup"><span data-stu-id="dee98-183">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="dee98-184">PowerShell für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="dee98-184">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="dee98-185">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="dee98-185">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="dee98-186">Nach der Registrierung können Sie PowerShell mit `sudo yum update powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="dee98-186">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="dee98-187">Installation über einen direkten Download: CentOS 7</span><span class="sxs-lookup"><span data-stu-id="dee98-187">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="dee98-188">Für [CentOS 7][]: Laden Sie das RPM-Paket `powershell-7.0.0-1.rhel.7.x86_64.rpm` über die Seite [Freigaben][] auf den CentOS-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="dee98-188">Using [CentOS 7][], download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="dee98-189">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="dee98-189">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="dee98-190">Sie können RPM ohne Download installieren:</span><span class="sxs-lookup"><span data-stu-id="dee98-190">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="dee98-191">Deinstallation: CentOS 7</span><span class="sxs-lookup"><span data-stu-id="dee98-191">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="dee98-193">Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="dee98-193">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="dee98-194">Installation über ein Paketrepository (bevorzugt): Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="dee98-194">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="dee98-195">PowerShell für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="dee98-195">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="dee98-196">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="dee98-196">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="dee98-197">Nach der Registrierung können Sie PowerShell mit `sudo yum update powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="dee98-197">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="dee98-198">Installation über einen direkten Download: Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="dee98-198">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="dee98-199">Laden Sie das RPM-Paket `powershell-7.0.0-1.rhel.7.x86_64.rpm` über die Seite [Freigaben][] auf den Red Hat Enterprise Linux-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="dee98-199">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="dee98-200">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="dee98-200">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="dee98-201">Sie können RPM ohne Download installieren:</span><span class="sxs-lookup"><span data-stu-id="dee98-201">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="dee98-202">Deinstallation: Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="dee98-202">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="dee98-203">openSUSE</span><span class="sxs-lookup"><span data-stu-id="dee98-203">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="dee98-204">Installation: openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="dee98-204">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="dee98-205">Installation: openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="dee98-205">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="dee98-206">Deinstallation: openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="dee98-206">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="dee98-207">Fedora</span><span class="sxs-lookup"><span data-stu-id="dee98-207">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="dee98-208">Fedora 28 wird nur in PowerShell 6.1 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="dee98-208">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="dee98-209">Fedora 29 und 30 werden nur in PowerShell 7.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="dee98-209">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="dee98-210">Installation über das Paketrepository (bevorzugt): Fedora 28, 29 und 30</span><span class="sxs-lookup"><span data-stu-id="dee98-210">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="dee98-211">PowerShell für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="dee98-211">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="dee98-212">Installation über direkten Download: Fedora 28, 29 und 30</span><span class="sxs-lookup"><span data-stu-id="dee98-212">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="dee98-213">Laden Sie das RPM-Paket `powershell-7.0.0-1.rhel.7.x86_64.rpm` über die Seite [Freigaben][] auf den Fedora-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="dee98-213">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="dee98-214">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="dee98-214">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="dee98-215">Sie können RPM ohne Download installieren:</span><span class="sxs-lookup"><span data-stu-id="dee98-215">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="dee98-216">Deinstallation: Fedora 28, 29 und 30</span><span class="sxs-lookup"><span data-stu-id="dee98-216">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="dee98-217">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="dee98-217">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="dee98-218">Arch Linux wird offiziell nicht von Microsoft unterstützt und daher von der Community verwaltet.</span><span class="sxs-lookup"><span data-stu-id="dee98-218">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="dee98-219">PowerShell ist über das Benutzerrepository [Arch Linux][] verfügbar.</span><span class="sxs-lookup"><span data-stu-id="dee98-219">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="dee98-220">Es kann gemeinsam mit dem [zuletzt markierten Release][arch-release] kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="dee98-220">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="dee98-221">Es kann gemeinsam vom [letzten Commit für den Master][arch-git] aus kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="dee98-221">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="dee98-222">Es kann mithilfe der [zuletzt zur Veröffentlichung bestimmten Binärdatei][arch-bin] installiert werden.</span><span class="sxs-lookup"><span data-stu-id="dee98-222">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="dee98-223">Pakete im Benutzerrepository „Arch Linux“ werden von der Community verwaltet. Es gibt keinen offiziellen Support.</span><span class="sxs-lookup"><span data-stu-id="dee98-223">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="dee98-224">Weitere Informationen zum Installieren von Paketen aus dem Benutzerrepository „Arch Linux“ finden Sie im [Arch Linux-Wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) oder in [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) der Community.</span><span class="sxs-lookup"><span data-stu-id="dee98-224">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="dee98-226">Snap-Paket</span><span class="sxs-lookup"><span data-stu-id="dee98-226">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="dee98-227">Abrufen von snapd</span><span class="sxs-lookup"><span data-stu-id="dee98-227">Getting snapd</span></span>

<span data-ttu-id="dee98-228">`snapd` ist für das Ausführen von Snap-Paketen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="dee98-228">`snapd` is required to run snaps.</span></span> <span data-ttu-id="dee98-229">Halten Sie sich an [diese Anweisungen](https://docs.snapcraft.io/core/install), um sicherzustellen, dass `snapd` installiert ist.</span><span class="sxs-lookup"><span data-stu-id="dee98-229">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="dee98-230">Installation über Snap</span><span class="sxs-lookup"><span data-stu-id="dee98-230">Installation via Snap</span></span>

<span data-ttu-id="dee98-231">PowerShell für Linux wird im [Snap-Store](https://snapcraft.io/store) veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="dee98-231">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="dee98-232">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="dee98-232">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="dee98-233">Gehen Sie folgendermaßen vor, wenn Sie eine Vorschauversion installieren möchten:</span><span class="sxs-lookup"><span data-stu-id="dee98-233">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="dee98-234">Nach der Installation wird für Snap automatisch ein Upgrade durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="dee98-234">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="dee98-235">Sie können ein Upgrade mit `sudo snap refresh powershell` oder `sudo snap refresh powershell-preview` auslösen.</span><span class="sxs-lookup"><span data-stu-id="dee98-235">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="dee98-236">Deinstallation</span><span class="sxs-lookup"><span data-stu-id="dee98-236">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="dee98-237">oder</span><span class="sxs-lookup"><span data-stu-id="dee98-237">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="dee98-238">Kali</span><span class="sxs-lookup"><span data-stu-id="dee98-238">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="dee98-239">Kali wird offiziell nicht von Microsoft unterstützt und daher von der Community verwaltet.</span><span class="sxs-lookup"><span data-stu-id="dee98-239">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="dee98-240">Installation: Kali</span><span class="sxs-lookup"><span data-stu-id="dee98-240">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="dee98-241">Deinstallation: Kali</span><span class="sxs-lookup"><span data-stu-id="dee98-241">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="dee98-242">Raspbian</span><span class="sxs-lookup"><span data-stu-id="dee98-242">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="dee98-243">Die Unterstützung von Raspbian wird noch getestet.</span><span class="sxs-lookup"><span data-stu-id="dee98-243">Raspbian support is experimental.</span></span>

<span data-ttu-id="dee98-244">Derzeit wird PowerShell nur unter Raspbian Stretch unterstützt.</span><span class="sxs-lookup"><span data-stu-id="dee98-244">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="dee98-245">Außerdem funktionieren CoreCLR und PowerShell nur auf Geräten mit Pi 2 und Pi 3, da andere Geräte, wie z. B. [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), einen nicht unterstützten Prozessor haben.</span><span class="sxs-lookup"><span data-stu-id="dee98-245">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="dee98-246">Laden Sie [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) herunter, und folgen Sie den [Installationsanweisungen](https://www.raspberrypi.org/documentation/installation/installing-images/README.md), um es zu installieren.</span><span class="sxs-lookup"><span data-stu-id="dee98-246">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="dee98-247">Installation: Raspbian</span><span class="sxs-lookup"><span data-stu-id="dee98-247">Installation - Raspbian</span></span>

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
wget https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-7.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="dee98-248">Optional können Sie eine symbolische Verknüpfung erstellen, damit Sie PowerShell ohne Angabe des Pfads zur Binärdatei `pwsh` starten können.</span><span class="sxs-lookup"><span data-stu-id="dee98-248">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="dee98-249">Deinstallation: Raspbian</span><span class="sxs-lookup"><span data-stu-id="dee98-249">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="dee98-250">Installieren als globales .NET-Tool</span><span class="sxs-lookup"><span data-stu-id="dee98-250">Install as a .NET Global tool</span></span>

<span data-ttu-id="dee98-251">Wenn Sie das [.NET Core SDK](/dotnet/core/sdk) bereits installiert haben, können Sie PowerShell einfach als [globales .NET-Tool](/dotnet/core/tools/global-tools) installieren.</span><span class="sxs-lookup"><span data-stu-id="dee98-251">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

## <a name="binary-archives"></a><span data-ttu-id="dee98-252">Archive der Binärdateien</span><span class="sxs-lookup"><span data-stu-id="dee98-252">Binary Archives</span></span>

<span data-ttu-id="dee98-253">`tar.gz`-Archive der PowerShell-Binärdateien werden für Linux-Plattformen zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="dee98-253">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="dee98-254">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="dee98-254">Dependencies</span></span>

<span data-ttu-id="dee98-255">PowerShell erstellt portierbare Binärdateien für alle Linux-Distributionen.</span><span class="sxs-lookup"><span data-stu-id="dee98-255">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="dee98-256">Allerdings erfordern die .NET Core-Runtime und PowerShell verschiedene Abhängigkeiten für die verschiedenen Distributionen.</span><span class="sxs-lookup"><span data-stu-id="dee98-256">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="dee98-257">Im folgenden Diagramm werden die Abhängigkeiten von .NET Core 2.0 für die verschiedenen Linux-Distributionen dargestellt, die offiziell unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="dee98-257">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="dee98-258">OS</span><span class="sxs-lookup"><span data-stu-id="dee98-258">OS</span></span>                 | <span data-ttu-id="dee98-259">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="dee98-259">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="dee98-260">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="dee98-260">Ubuntu 16.04</span></span>       | <span data-ttu-id="dee98-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="dee98-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dee98-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="dee98-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="dee98-263">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="dee98-263">Ubuntu 17.10</span></span>       | <span data-ttu-id="dee98-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="dee98-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dee98-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="dee98-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="dee98-266">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="dee98-266">Ubuntu 18.04</span></span>       | <span data-ttu-id="dee98-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="dee98-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dee98-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="dee98-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="dee98-269">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="dee98-269">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="dee98-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="dee98-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dee98-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="dee98-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="dee98-272">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="dee98-272">Debian 9 (Stretch)</span></span> | <span data-ttu-id="dee98-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="dee98-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dee98-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="dee98-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="dee98-275">CentOS 7:</span><span class="sxs-lookup"><span data-stu-id="dee98-275">CentOS 7</span></span> <br> <span data-ttu-id="dee98-276">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="dee98-276">Oracle Linux 7</span></span> <br> <span data-ttu-id="dee98-277">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="dee98-277">RHEL 7</span></span> | <span data-ttu-id="dee98-278">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="dee98-278">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="dee98-279">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="dee98-279">openSUSE 42.3</span></span> | <span data-ttu-id="dee98-280">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="dee98-280">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="dee98-281">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="dee98-281">openSUSE Leap 15</span></span> | <span data-ttu-id="dee98-282">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="dee98-282">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="dee98-283">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="dee98-283">Fedora 27</span></span> <br> <span data-ttu-id="dee98-284">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="dee98-284">Fedora 28</span></span> | <span data-ttu-id="dee98-285">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="dee98-285">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="dee98-286">Sie müssen zur Bereitstellung von PowerShell-Binärdateien für nicht offiziell unterstützte Linux-Distributionen die notwendigen Abhängigkeiten für das Zielbetriebssystem über zusätzliche Schritte installieren.</span><span class="sxs-lookup"><span data-stu-id="dee98-286">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="dee98-287">Beispielsweise installiert die [Amazon Linux-Dockerfile][amazon-dockerfile] zuerst die Abhängigkeiten und extrahiert anschließend das `tar.gz`-Archiv für Linux.</span><span class="sxs-lookup"><span data-stu-id="dee98-287">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="dee98-288">Installation: Archive von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="dee98-288">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="dee98-289">Linux</span><span class="sxs-lookup"><span data-stu-id="dee98-289">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="dee98-290">Deinstallation: Archive von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="dee98-290">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="dee98-291">Paths</span><span class="sxs-lookup"><span data-stu-id="dee98-291">Paths</span></span>

- <span data-ttu-id="dee98-292">`$PSHOME` ist `/opt/microsoft/powershell/7/`.</span><span class="sxs-lookup"><span data-stu-id="dee98-292">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="dee98-293">Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="dee98-293">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="dee98-294">Standardprofile werden über `$PSHOME/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="dee98-294">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="dee98-295">Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="dee98-295">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="dee98-296">Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="dee98-296">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="dee98-297">Standardmodule werden über `$PSHOME/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="dee98-297">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="dee98-298">Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="dee98-298">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="dee98-299">Die Profile beachten die Konfigurationen von PowerShell pro Host. Das bedeutet, die hostspezifischen Standardprofile sind an denselben Orten unter `Microsoft.PowerShell_profile.ps1` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="dee98-299">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="dee98-300">PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter Linux ein.</span><span class="sxs-lookup"><span data-stu-id="dee98-300">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Freigaben]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
