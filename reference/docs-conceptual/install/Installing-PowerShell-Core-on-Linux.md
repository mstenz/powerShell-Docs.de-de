---
title: Installieren von PowerShell unter Linux
description: Informationen zur Installation von PowerShell auf verschiedenen Linux-Distributionen
ms.date: 03/09/2020
ms.openlocfilehash: 201bb693c3473f6b1f05d860562b1fc132912bb2
ms.sourcegitcommit: 7c7f8bb9afdc592d07bf7ff4179d000a48716f13
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82174132"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="d3a46-103">Installieren von PowerShell unter Linux</span><span class="sxs-lookup"><span data-stu-id="d3a46-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="d3a46-104">Sämtliche Pakete sind auf der Seite [Freigaben][] über GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d3a46-104">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="d3a46-105">Nachdem Sie das Paket installiert haben, führen Sie `pwsh` über das Terminal aus.</span><span class="sxs-lookup"><span data-stu-id="d3a46-105">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="d3a46-106">Führen Sie `pwsh-preview` aus, wenn Sie eine [Vorschauversion](#installing-preview-releases) installiert haben.</span><span class="sxs-lookup"><span data-stu-id="d3a46-106">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="d3a46-107">PowerShell 7 ist ein direktes Upgrade, mit dem PowerShell Core 6.x entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="d3a46-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="d3a46-108">Der Ordner `/usr/local/microsoft/powershell/6` wird durch `/usr/local/microsoft/powershell/7` ersetzt.</span><span class="sxs-lookup"><span data-stu-id="d3a46-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="d3a46-109">Wenn Sie PowerShell 6 und PowerShell 7 parallel ausführen müssen, installieren Sie PowerShell 6 mithilfe der [binary archive](#binary-archives)-Methode neu.</span><span class="sxs-lookup"><span data-stu-id="d3a46-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="d3a46-110">Für nicht offiziell unterstützte Linux-Distributionen können Sie versuchen, PowerShell über das [Snap-Paket für PowerShell][snap] zu installieren.</span><span class="sxs-lookup"><span data-stu-id="d3a46-110">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="d3a46-111">Stattdessen können Sie auch versuchen, PowerShell-Binärdateien über das [`tar.gz`-Archiv][tar] für Linux bereitzustellen. Dafür müssen Sie aber die für Ihr Betriebssystem erforderlichen Abhängigkeiten in zusätzlichen Schritten einrichten.</span><span class="sxs-lookup"><span data-stu-id="d3a46-111">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

[snap]: #snap-package
[tar]: #binary-archives

<span data-ttu-id="d3a46-112">Offiziell unterstützte Releases:</span><span class="sxs-lookup"><span data-stu-id="d3a46-112">Officially supported releases</span></span>

- <span data-ttu-id="d3a46-113">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d3a46-113">Ubuntu 16.04</span></span>
- <span data-ttu-id="d3a46-114">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d3a46-114">Ubuntu 18.04</span></span>
- <span data-ttu-id="d3a46-115">Debian 8</span><span class="sxs-lookup"><span data-stu-id="d3a46-115">Debian 8</span></span>
- <span data-ttu-id="d3a46-116">Debian 9</span><span class="sxs-lookup"><span data-stu-id="d3a46-116">Debian 9</span></span>
- <span data-ttu-id="d3a46-117">Debian 10</span><span class="sxs-lookup"><span data-stu-id="d3a46-117">Debian 10</span></span>
- <span data-ttu-id="d3a46-118">Alpine 3.9 und 3.10</span><span class="sxs-lookup"><span data-stu-id="d3a46-118">Alpine 3.9 and 3.10</span></span>
- <span data-ttu-id="d3a46-119">CentOS 7:</span><span class="sxs-lookup"><span data-stu-id="d3a46-119">CentOS 7</span></span>
- <span data-ttu-id="d3a46-120">Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="d3a46-120">Red Hat Enterprise Linux (RHEL) 7</span></span>
- <span data-ttu-id="d3a46-121">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="d3a46-121">Fedora 28</span></span>
- <span data-ttu-id="d3a46-122">Fedora 29</span><span class="sxs-lookup"><span data-stu-id="d3a46-122">Fedora 29</span></span>
- <span data-ttu-id="d3a46-123">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="d3a46-123">Fedora 30</span></span>
- <span data-ttu-id="d3a46-124">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="d3a46-124">openSUSE 42.3</span></span>
- <span data-ttu-id="d3a46-125">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="d3a46-125">openSUSE Leap 15</span></span>

<span data-ttu-id="d3a46-126">Von der Community unterstützte Releases:</span><span class="sxs-lookup"><span data-stu-id="d3a46-126">Community supported releases</span></span>

- <span data-ttu-id="d3a46-127">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="d3a46-127">Ubuntu 18.10</span></span>
- <span data-ttu-id="d3a46-128">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="d3a46-128">Ubuntu 19.04</span></span>
- <span data-ttu-id="d3a46-129">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="d3a46-129">Arch Linux</span></span>
- <span data-ttu-id="d3a46-130">Kali</span><span class="sxs-lookup"><span data-stu-id="d3a46-130">Kali</span></span>
- <span data-ttu-id="d3a46-131">Raspbian (experimentell)</span><span class="sxs-lookup"><span data-stu-id="d3a46-131">Raspbian (experimental)</span></span>

<span data-ttu-id="d3a46-132">Alternative Installationsmethoden</span><span class="sxs-lookup"><span data-stu-id="d3a46-132">Alternate install methods</span></span>

- <span data-ttu-id="d3a46-133">Snap-Paket</span><span class="sxs-lookup"><span data-stu-id="d3a46-133">Snap Package</span></span>
- <span data-ttu-id="d3a46-134">Archive der Binärdateien</span><span class="sxs-lookup"><span data-stu-id="d3a46-134">Binary Archives</span></span>
- <span data-ttu-id="d3a46-135">Globales .NET-Tool</span><span class="sxs-lookup"><span data-stu-id="d3a46-135">.NET Global tool</span></span>

## <a name="ubuntu-1604"></a><span data-ttu-id="d3a46-136">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d3a46-136">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="d3a46-137">Installation über das Paketrepository: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d3a46-137">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="d3a46-138">PowerShell für Linux wird in Paketrepositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="d3a46-138">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="d3a46-139">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="d3a46-139">The preferred method is as follows:</span></span>

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

<span data-ttu-id="d3a46-140">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="d3a46-140">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d3a46-141">Nach der Registrierung können Sie PowerShell mit `sudo apt-get upgrade powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="d3a46-141">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="d3a46-142">Installation über einen direkten Download: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d3a46-142">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="d3a46-143">Laden Sie das Debian-Paket `powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb` über die Seite [Freigaben][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="d3a46-143">Download the Debian package `powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="d3a46-144">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="d3a46-144">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="d3a46-145">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="d3a46-145">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="d3a46-146">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="d3a46-146">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="d3a46-147">Deinstallation: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d3a46-147">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="d3a46-148">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d3a46-148">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="d3a46-149">Installation über das Paketrepository: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d3a46-149">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="d3a46-150">PowerShell für Linux wird in Paketrepositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="d3a46-150">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="d3a46-151">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="d3a46-151">The preferred method is as follows:</span></span>

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

<span data-ttu-id="d3a46-152">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="d3a46-152">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d3a46-153">Nach der Registrierung können Sie PowerShell mit `sudo apt-get upgrade powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="d3a46-153">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="d3a46-154">Installation über einen direkten Download: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d3a46-154">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="d3a46-155">Laden Sie das Debian-Paket `powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb` über die Seite [Freigaben][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="d3a46-155">Download the Debian package `powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="d3a46-156">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="d3a46-156">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="d3a46-157">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="d3a46-157">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="d3a46-158">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="d3a46-158">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="d3a46-159">Deinstallation: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d3a46-159">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="d3a46-160">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="d3a46-160">Ubuntu 18.10</span></span>

<span data-ttu-id="d3a46-161">Die Installation wird über `snapd` unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d3a46-161">Installation is supported via `snapd`.</span></span> <span data-ttu-id="d3a46-162">Anweisungen finden Sie unter [Snap-Paket][snap].</span><span class="sxs-lookup"><span data-stu-id="d3a46-162">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="d3a46-163">Ubuntu 18.10 ist ein [Zwischenrelease](https://www.ubuntu.com/about/release-cycle), das von der [Community unterstützt](../powershell-support-lifecycle.md) wird.</span><span class="sxs-lookup"><span data-stu-id="d3a46-163">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="d3a46-164">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="d3a46-164">Ubuntu 19.04</span></span>

<span data-ttu-id="d3a46-165">Die Installation wird über `snapd` unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d3a46-165">Installation is supported via `snapd`.</span></span> <span data-ttu-id="d3a46-166">Anweisungen finden Sie unter [Snap-Paket][snap].</span><span class="sxs-lookup"><span data-stu-id="d3a46-166">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="d3a46-167">Ubuntu 19.04 ist ein [Zwischenrelease](https://www.ubuntu.com/about/release-cycle), das von der [Community unterstützt](../powershell-support-lifecycle.md) wird.</span><span class="sxs-lookup"><span data-stu-id="d3a46-167">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="d3a46-168">Debian 8</span><span class="sxs-lookup"><span data-stu-id="d3a46-168">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="d3a46-169">Installation über das Paketrepository: Debian 8</span><span class="sxs-lookup"><span data-stu-id="d3a46-169">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="d3a46-170">PowerShell für Linux wird in Paketrepositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="d3a46-170">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="d3a46-171">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="d3a46-171">The preferred method is as follows:</span></span>

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

<span data-ttu-id="d3a46-172">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="d3a46-172">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d3a46-173">Nach der Registrierung können Sie PowerShell mit `sudo apt-get upgrade powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="d3a46-173">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="d3a46-174">Debian 9</span><span class="sxs-lookup"><span data-stu-id="d3a46-174">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="d3a46-175">Installation über das Paketrepository: Debian 9</span><span class="sxs-lookup"><span data-stu-id="d3a46-175">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="d3a46-176">PowerShell für Linux wird in Paketrepositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="d3a46-176">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="d3a46-177">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="d3a46-177">The preferred method is as follows:</span></span>

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

<span data-ttu-id="d3a46-178">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="d3a46-178">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d3a46-179">Nach der Registrierung können Sie PowerShell mit `sudo apt-get upgrade powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="d3a46-179">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="d3a46-180">Installation über einen direkten Download: Debian 9</span><span class="sxs-lookup"><span data-stu-id="d3a46-180">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="d3a46-181">Laden Sie das Debian-Paket `powershell-lts_7.0.0-1.debian.9_amd64.deb` über die Seite [Freigaben][] auf den Debian-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="d3a46-181">Download the Debian package `powershell-lts_7.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="d3a46-182">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="d3a46-182">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="d3a46-183">Deinstallation: Debian 9</span><span class="sxs-lookup"><span data-stu-id="d3a46-183">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="d3a46-184">Debian 10</span><span class="sxs-lookup"><span data-stu-id="d3a46-184">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="d3a46-185">Debian 10 wird nur in PowerShell 7.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d3a46-185">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository---debian-10"></a><span data-ttu-id="d3a46-186">Installation über das Paketrepository: Debian 10</span><span class="sxs-lookup"><span data-stu-id="d3a46-186">Installation via Package Repository - Debian 10</span></span>

<span data-ttu-id="d3a46-187">PowerShell für Linux wird in Paketrepositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="d3a46-187">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="d3a46-188">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="d3a46-188">The preferred method is as follows:</span></span>

```sh
# Download the Microsoft repository GPG keys
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="d3a46-189">Installation über direkten Download: Debian 10</span><span class="sxs-lookup"><span data-stu-id="d3a46-189">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="d3a46-190">Laden Sie das tar.gz-Paket `powershell_7.0.0-linux-x64.tar.gz` über die Seite [Freigaben][] auf den Debian-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="d3a46-190">Download the tar.gz package `powershell_7.0.0-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="d3a46-191">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="d3a46-191">Then, in the terminal, execute the following commands:</span></span>

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

## <a name="alpine-39-and-310"></a><span data-ttu-id="d3a46-192">Alpine 3.9 und 3.10</span><span class="sxs-lookup"><span data-stu-id="d3a46-192">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="d3a46-193">Alpine 3.9 und 3.10 werden nur in PowerShell 7.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d3a46-193">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="d3a46-194">Installation über direkten Download: Alpine 3.9 und 3.10</span><span class="sxs-lookup"><span data-stu-id="d3a46-194">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="d3a46-195">Laden Sie das tar.gz-Paket `powershell-7.0.0-linux-alpine-x64.tar.gz` über die Seite [Freigaben][] auf den Alpine-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="d3a46-195">Download the tar.gz package `powershell-7.0.0-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="d3a46-196">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="d3a46-196">Then, in the terminal, execute the following commands:</span></span>

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

## <a name="centos-7"></a><span data-ttu-id="d3a46-197">CentOS 7:</span><span class="sxs-lookup"><span data-stu-id="d3a46-197">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="d3a46-198">Dieses Paket funktioniert unter Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="d3a46-198">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="d3a46-199">Installation über das Paketrepository (bevorzugt): CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d3a46-199">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="d3a46-200">PowerShell für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="d3a46-200">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="d3a46-201">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="d3a46-201">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d3a46-202">Nach der Registrierung können Sie PowerShell mit `sudo yum update powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="d3a46-202">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="d3a46-203">Installation über einen direkten Download: CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d3a46-203">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="d3a46-204">Für [CentOS 7][]: Laden Sie das RPM-Paket `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` über die Seite [Freigaben][] auf den CentOS-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="d3a46-204">Using [CentOS 7][], download the RPM package `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="d3a46-205">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="d3a46-205">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="d3a46-206">Sie können RPM ohne Download installieren:</span><span class="sxs-lookup"><span data-stu-id="d3a46-206">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="d3a46-207">Deinstallation: CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d3a46-207">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d3a46-209">Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="d3a46-209">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d3a46-210">Installation über ein Paketrepository (bevorzugt): Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="d3a46-210">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="d3a46-211">PowerShell für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="d3a46-211">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="d3a46-212">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="d3a46-212">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d3a46-213">Nach der Registrierung können Sie PowerShell mit `sudo yum update powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="d3a46-213">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d3a46-214">Installation über einen direkten Download: Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="d3a46-214">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="d3a46-215">Laden Sie das RPM-Paket `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` über die Seite [Freigaben][] auf den Red Hat Enterprise Linux-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="d3a46-215">Download the RPM package `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="d3a46-216">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="d3a46-216">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="d3a46-217">Sie können RPM ohne Download installieren:</span><span class="sxs-lookup"><span data-stu-id="d3a46-217">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d3a46-218">Deinstallation: Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="d3a46-218">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="d3a46-219">openSUSE</span><span class="sxs-lookup"><span data-stu-id="d3a46-219">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="d3a46-220">Installation: openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="d3a46-220">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="d3a46-221">Installation: openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="d3a46-221">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="d3a46-222">Deinstallation: openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="d3a46-222">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="d3a46-223">Fedora</span><span class="sxs-lookup"><span data-stu-id="d3a46-223">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="d3a46-224">Fedora 28 wird nur in PowerShell 6.1 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d3a46-224">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="d3a46-225">Fedora 29 und 30 werden nur in PowerShell 7.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d3a46-225">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="d3a46-226">Installation über das Paketrepository (bevorzugt): Fedora 28, 29 und 30</span><span class="sxs-lookup"><span data-stu-id="d3a46-226">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="d3a46-227">PowerShell für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="d3a46-227">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="d3a46-228">Installation über direkten Download: Fedora 28, 29 und 30</span><span class="sxs-lookup"><span data-stu-id="d3a46-228">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="d3a46-229">Laden Sie das RPM-Paket `powershell-7.0.0-1.rhel.7.x86_64.rpm` über die Seite [Freigaben][] auf den Fedora-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="d3a46-229">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="d3a46-230">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="d3a46-230">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="d3a46-231">Sie können RPM ohne Download installieren:</span><span class="sxs-lookup"><span data-stu-id="d3a46-231">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="d3a46-232">Deinstallation: Fedora 28, 29 und 30</span><span class="sxs-lookup"><span data-stu-id="d3a46-232">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="d3a46-233">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="d3a46-233">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="d3a46-234">Arch Linux wird offiziell nicht von Microsoft unterstützt und daher von der Community verwaltet.</span><span class="sxs-lookup"><span data-stu-id="d3a46-234">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="d3a46-235">PowerShell ist über das Benutzerrepository [Arch Linux][] verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d3a46-235">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

- <span data-ttu-id="d3a46-236">Es kann gemeinsam mit dem [zuletzt markierten Release][arch-release] kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="d3a46-236">It can be compiled with the [latest tagged release][arch-release]</span></span>
- <span data-ttu-id="d3a46-237">Es kann gemeinsam vom [letzten Commit für den Master][arch-git] aus kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="d3a46-237">It can be compiled from the [latest commit to master][arch-git]</span></span>
- <span data-ttu-id="d3a46-238">Es kann mithilfe der [zuletzt zur Veröffentlichung bestimmten Binärdatei][arch-bin] installiert werden.</span><span class="sxs-lookup"><span data-stu-id="d3a46-238">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="d3a46-239">Pakete im Benutzerrepository „Arch Linux“ werden von der Community verwaltet. Es gibt keinen offiziellen Support.</span><span class="sxs-lookup"><span data-stu-id="d3a46-239">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="d3a46-240">Weitere Informationen zum Installieren von Paketen aus dem Benutzerrepository „Arch Linux“ finden Sie im [Arch Linux-Wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) oder unter [Verwenden von PowerShell in Docker](powershell-in-docker.md).</span><span class="sxs-lookup"><span data-stu-id="d3a46-240">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or [Using PowerShell in Docker](powershell-in-docker.md).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="d3a46-242">Snap-Paket</span><span class="sxs-lookup"><span data-stu-id="d3a46-242">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="d3a46-243">Abrufen von snapd</span><span class="sxs-lookup"><span data-stu-id="d3a46-243">Getting snapd</span></span>

<span data-ttu-id="d3a46-244">`snapd` ist für das Ausführen von Snap-Paketen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d3a46-244">`snapd` is required to run snaps.</span></span> <span data-ttu-id="d3a46-245">Halten Sie sich an [diese Anweisungen](https://docs.snapcraft.io/core/install), um sicherzustellen, dass `snapd` installiert ist.</span><span class="sxs-lookup"><span data-stu-id="d3a46-245">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="d3a46-246">Installation über Snap</span><span class="sxs-lookup"><span data-stu-id="d3a46-246">Installation via Snap</span></span>

<span data-ttu-id="d3a46-247">PowerShell für Linux wird im [Snap-Store](https://snapcraft.io/store) veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="d3a46-247">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="d3a46-248">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="d3a46-248">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="d3a46-249">Gehen Sie folgendermaßen vor, wenn Sie eine Vorschauversion installieren möchten:</span><span class="sxs-lookup"><span data-stu-id="d3a46-249">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="d3a46-250">Nach der Installation wird für Snap automatisch ein Upgrade durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="d3a46-250">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="d3a46-251">Sie können ein Upgrade mit `sudo snap refresh powershell` oder `sudo snap refresh powershell-preview` auslösen.</span><span class="sxs-lookup"><span data-stu-id="d3a46-251">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="d3a46-252">Deinstallation</span><span class="sxs-lookup"><span data-stu-id="d3a46-252">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="d3a46-253">oder</span><span class="sxs-lookup"><span data-stu-id="d3a46-253">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="d3a46-254">Kali</span><span class="sxs-lookup"><span data-stu-id="d3a46-254">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="d3a46-255">Kali wird offiziell nicht von Microsoft unterstützt und daher von der Community verwaltet.</span><span class="sxs-lookup"><span data-stu-id="d3a46-255">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="d3a46-256">Installation: Kali</span><span class="sxs-lookup"><span data-stu-id="d3a46-256">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="d3a46-257">Deinstallation: Kali</span><span class="sxs-lookup"><span data-stu-id="d3a46-257">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="d3a46-258">Raspbian</span><span class="sxs-lookup"><span data-stu-id="d3a46-258">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="d3a46-259">Die Unterstützung von Raspbian wird noch getestet.</span><span class="sxs-lookup"><span data-stu-id="d3a46-259">Raspbian support is experimental.</span></span>

<span data-ttu-id="d3a46-260">Derzeit wird PowerShell nur unter Raspbian Stretch unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d3a46-260">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="d3a46-261">Außerdem funktionieren CoreCLR und PowerShell nur auf Geräten mit Pi 2 und Pi 3, da andere Geräte, wie z. B. [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), einen nicht unterstützten Prozessor haben.</span><span class="sxs-lookup"><span data-stu-id="d3a46-261">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="d3a46-262">Laden Sie [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) herunter, und folgen Sie den [Installationsanweisungen](https://www.raspberrypi.org/documentation/installation/installing-images/README.md), um es zu installieren.</span><span class="sxs-lookup"><span data-stu-id="d3a46-262">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="d3a46-263">Installation: Raspbian</span><span class="sxs-lookup"><span data-stu-id="d3a46-263">Installation - Raspbian</span></span>

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

<span data-ttu-id="d3a46-264">Optional können Sie eine symbolische Verknüpfung erstellen, damit Sie PowerShell ohne Angabe des Pfads zur Binärdatei `pwsh` starten können.</span><span class="sxs-lookup"><span data-stu-id="d3a46-264">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="d3a46-265">Deinstallation: Raspbian</span><span class="sxs-lookup"><span data-stu-id="d3a46-265">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a><span data-ttu-id="d3a46-266">Installieren von Vorschauversionen</span><span class="sxs-lookup"><span data-stu-id="d3a46-266">Installing Preview Releases</span></span>

<span data-ttu-id="d3a46-267">Wenn eine Vorschauversion von PowerShell für Linux über ein Paketrepository installiert wird, ändert sich der Paketname von `powershell` in `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="d3a46-267">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="d3a46-268">Bei einer Installation über einen direkten Download wird nur der Dateiname geändert.</span><span class="sxs-lookup"><span data-stu-id="d3a46-268">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="d3a46-269">In der nachfolgenden Tabelle werden die Befehle aufgeführt, über die Sie Pakete stabiler Versionen und von Vorschauversionen mithilfe der verschiedenen Paket-Manager installieren können:</span><span class="sxs-lookup"><span data-stu-id="d3a46-269">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="d3a46-270">Distribution(en)</span><span class="sxs-lookup"><span data-stu-id="d3a46-270">Distribution(s)</span></span> |            <span data-ttu-id="d3a46-271">Befehl für die stabile Version</span><span class="sxs-lookup"><span data-stu-id="d3a46-271">Stable Command</span></span>            |               <span data-ttu-id="d3a46-272">Befehl für die Vorschauversion</span><span class="sxs-lookup"><span data-stu-id="d3a46-272">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="d3a46-273">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="d3a46-273">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="d3a46-274">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="d3a46-274">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="d3a46-275">Fedora</span><span class="sxs-lookup"><span data-stu-id="d3a46-275">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="d3a46-276">Installieren als globales .NET-Tool</span><span class="sxs-lookup"><span data-stu-id="d3a46-276">Install as a .NET Global tool</span></span>

<span data-ttu-id="d3a46-277">Wenn Sie das [.NET Core SDK](/dotnet/core/sdk) bereits installiert haben, können Sie PowerShell einfach als [globales .NET-Tool](/dotnet/core/tools/global-tools) installieren.</span><span class="sxs-lookup"><span data-stu-id="d3a46-277">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="d3a46-278">Der .NET-Toolinstaller fügt `~/.dotnet/tools` Ihrer `PATH`-Umgebungsvariablen hinzu.</span><span class="sxs-lookup"><span data-stu-id="d3a46-278">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="d3a46-279">Die aktuell ausgeführte Shell verfügt jedoch nicht über den aktualisierten `PATH`.</span><span class="sxs-lookup"><span data-stu-id="d3a46-279">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="d3a46-280">Sie sollten PowerShell über eine neue Shell starten können, indem Sie `pwsh` eingeben.</span><span class="sxs-lookup"><span data-stu-id="d3a46-280">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="d3a46-281">Archive der Binärdateien</span><span class="sxs-lookup"><span data-stu-id="d3a46-281">Binary Archives</span></span>

<span data-ttu-id="d3a46-282">`tar.gz`-Archive der PowerShell-Binärdateien werden für Linux-Plattformen zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="d3a46-282">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="d3a46-283">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="d3a46-283">Dependencies</span></span>

<span data-ttu-id="d3a46-284">PowerShell erstellt portierbare Binärdateien für alle Linux-Distributionen.</span><span class="sxs-lookup"><span data-stu-id="d3a46-284">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="d3a46-285">Allerdings erfordern die .NET Core-Runtime und PowerShell verschiedene Abhängigkeiten für die verschiedenen Distributionen.</span><span class="sxs-lookup"><span data-stu-id="d3a46-285">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="d3a46-286">Im folgenden Diagramm werden die Abhängigkeiten von .NET Core 2.0 für die verschiedenen Linux-Distributionen dargestellt, die offiziell unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="d3a46-286">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="d3a46-287">OS</span><span class="sxs-lookup"><span data-stu-id="d3a46-287">OS</span></span>                 | <span data-ttu-id="d3a46-288">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="d3a46-288">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="d3a46-289">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d3a46-289">Ubuntu 16.04</span></span>       | <span data-ttu-id="d3a46-290">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="d3a46-290">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d3a46-291">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="d3a46-291">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="d3a46-292">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="d3a46-292">Ubuntu 17.10</span></span>       | <span data-ttu-id="d3a46-293">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="d3a46-293">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d3a46-294">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="d3a46-294">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="d3a46-295">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d3a46-295">Ubuntu 18.04</span></span>       | <span data-ttu-id="d3a46-296">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="d3a46-296">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d3a46-297">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="d3a46-297">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="d3a46-298">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="d3a46-298">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="d3a46-299">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="d3a46-299">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d3a46-300">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="d3a46-300">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="d3a46-301">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="d3a46-301">Debian 9 (Stretch)</span></span> | <span data-ttu-id="d3a46-302">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="d3a46-302">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d3a46-303">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="d3a46-303">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="d3a46-304">CentOS 7:</span><span class="sxs-lookup"><span data-stu-id="d3a46-304">CentOS 7</span></span> <br> <span data-ttu-id="d3a46-305">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="d3a46-305">Oracle Linux 7</span></span> <br> <span data-ttu-id="d3a46-306">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="d3a46-306">RHEL 7</span></span> | <span data-ttu-id="d3a46-307">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="d3a46-307">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="d3a46-308">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="d3a46-308">openSUSE 42.3</span></span> | <span data-ttu-id="d3a46-309">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="d3a46-309">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="d3a46-310">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="d3a46-310">openSUSE Leap 15</span></span> | <span data-ttu-id="d3a46-311">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="d3a46-311">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="d3a46-312">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="d3a46-312">Fedora 27</span></span> <br> <span data-ttu-id="d3a46-313">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="d3a46-313">Fedora 28</span></span> | <span data-ttu-id="d3a46-314">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="d3a46-314">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="d3a46-315">Sie müssen zur Bereitstellung von PowerShell-Binärdateien für nicht offiziell unterstützte Linux-Distributionen die notwendigen Abhängigkeiten für das Zielbetriebssystem über zusätzliche Schritte installieren.</span><span class="sxs-lookup"><span data-stu-id="d3a46-315">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="d3a46-316">Beispielsweise installiert die [Amazon Linux-Dockerfile][amazon-dockerfile] zuerst die Abhängigkeiten und extrahiert anschließend das `tar.gz`-Archiv für Linux.</span><span class="sxs-lookup"><span data-stu-id="d3a46-316">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="d3a46-317">Installation: Archive von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="d3a46-317">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="d3a46-318">Linux</span><span class="sxs-lookup"><span data-stu-id="d3a46-318">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="d3a46-319">Deinstallation: Archive von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="d3a46-319">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="d3a46-320">Paths</span><span class="sxs-lookup"><span data-stu-id="d3a46-320">Paths</span></span>

- <span data-ttu-id="d3a46-321">`$PSHOME` ist `/opt/microsoft/powershell/7/`.</span><span class="sxs-lookup"><span data-stu-id="d3a46-321">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="d3a46-322">Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="d3a46-322">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="d3a46-323">Standardprofile werden über `$PSHOME/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="d3a46-323">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="d3a46-324">Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="d3a46-324">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="d3a46-325">Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="d3a46-325">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="d3a46-326">Standardmodule werden über `$PSHOME/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="d3a46-326">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="d3a46-327">Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="d3a46-327">PSReadLine history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="d3a46-328">Die Profile beachten die Konfigurationen von PowerShell pro Host. Das bedeutet, die hostspezifischen Standardprofile sind an denselben Orten unter `Microsoft.PowerShell_profile.ps1` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="d3a46-328">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="d3a46-329">PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter Linux ein.</span><span class="sxs-lookup"><span data-stu-id="d3a46-329">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Freigaben]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
