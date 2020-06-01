---
title: Installieren von PowerShell unter Linux
description: Informationen zur Installation von PowerShell auf verschiedenen Linux-Distributionen
ms.date: 05/21/2020
ms.openlocfilehash: 1f3526507f84c43fbe44235e9a44e43d7f3d3e37
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84148462"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="3d2b0-103">Installieren von PowerShell unter Linux</span><span class="sxs-lookup"><span data-stu-id="3d2b0-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="3d2b0-104">Sämtliche Pakete sind auf der Seite [Freigaben][] über GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-104">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="3d2b0-105">Nachdem Sie das Paket installiert haben, führen Sie `pwsh` über das Terminal aus.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-105">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="3d2b0-106">Führen Sie `pwsh-preview` aus, wenn Sie eine [Vorschauversion](#installing-preview-releases) installiert haben.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-106">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="3d2b0-107">PowerShell 7 ist ein direktes Upgrade, mit dem PowerShell Core 6.x entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="3d2b0-108">Der Ordner `/usr/local/microsoft/powershell/6` wird durch `/usr/local/microsoft/powershell/7` ersetzt.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="3d2b0-109">Wenn Sie PowerShell 6 und PowerShell 7 parallel ausführen müssen, installieren Sie PowerShell 6 mithilfe der [binary archive](#binary-archives)-Methode neu.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="3d2b0-110">Für nicht offiziell unterstützte Linux-Distributionen können Sie versuchen, PowerShell über das [Snap-Paket für PowerShell][snap] zu installieren.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-110">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="3d2b0-111">Stattdessen können Sie auch versuchen, PowerShell-Binärdateien über das [`tar.gz`-Archiv][tar] für Linux bereitzustellen. Dafür müssen Sie aber die für Ihr Betriebssystem erforderlichen Abhängigkeiten in zusätzlichen Schritten einrichten.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-111">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

[snap]: #snap-package
[tar]: #binary-archives

<span data-ttu-id="3d2b0-112">Offiziell unterstützte Releases:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-112">Officially supported releases</span></span>

- <span data-ttu-id="3d2b0-113">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3d2b0-113">Ubuntu 16.04</span></span>
- <span data-ttu-id="3d2b0-114">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3d2b0-114">Ubuntu 18.04</span></span>
- <span data-ttu-id="3d2b0-115">Debian 8</span><span class="sxs-lookup"><span data-stu-id="3d2b0-115">Debian 8</span></span>
- <span data-ttu-id="3d2b0-116">Debian 9</span><span class="sxs-lookup"><span data-stu-id="3d2b0-116">Debian 9</span></span>
- <span data-ttu-id="3d2b0-117">Debian 10</span><span class="sxs-lookup"><span data-stu-id="3d2b0-117">Debian 10</span></span>
- <span data-ttu-id="3d2b0-118">Alpine 3.9 und 3.10</span><span class="sxs-lookup"><span data-stu-id="3d2b0-118">Alpine 3.9 and 3.10</span></span>
- <span data-ttu-id="3d2b0-119">CentOS 7:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-119">CentOS 7</span></span>
- <span data-ttu-id="3d2b0-120">Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="3d2b0-120">Red Hat Enterprise Linux (RHEL) 7</span></span>
- <span data-ttu-id="3d2b0-121">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3d2b0-121">Fedora 28</span></span>
- <span data-ttu-id="3d2b0-122">Fedora 29</span><span class="sxs-lookup"><span data-stu-id="3d2b0-122">Fedora 29</span></span>
- <span data-ttu-id="3d2b0-123">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="3d2b0-123">Fedora 30</span></span>
- <span data-ttu-id="3d2b0-124">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="3d2b0-124">openSUSE 42.3</span></span>
- <span data-ttu-id="3d2b0-125">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="3d2b0-125">openSUSE Leap 15</span></span>

<span data-ttu-id="3d2b0-126">Von der Community unterstützte Releases:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-126">Community supported releases</span></span>

- <span data-ttu-id="3d2b0-127">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="3d2b0-127">Ubuntu 18.10</span></span>
- <span data-ttu-id="3d2b0-128">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="3d2b0-128">Ubuntu 19.04</span></span>
- <span data-ttu-id="3d2b0-129">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="3d2b0-129">Arch Linux</span></span>
- <span data-ttu-id="3d2b0-130">Kali</span><span class="sxs-lookup"><span data-stu-id="3d2b0-130">Kali</span></span>
- <span data-ttu-id="3d2b0-131">Raspbian (experimentell)</span><span class="sxs-lookup"><span data-stu-id="3d2b0-131">Raspbian (experimental)</span></span>

<span data-ttu-id="3d2b0-132">Alternative Installationsmethoden</span><span class="sxs-lookup"><span data-stu-id="3d2b0-132">Alternate install methods</span></span>

- <span data-ttu-id="3d2b0-133">Snap-Paket</span><span class="sxs-lookup"><span data-stu-id="3d2b0-133">Snap Package</span></span>
- <span data-ttu-id="3d2b0-134">Archive der Binärdateien</span><span class="sxs-lookup"><span data-stu-id="3d2b0-134">Binary Archives</span></span>
- <span data-ttu-id="3d2b0-135">Globales .NET-Tool</span><span class="sxs-lookup"><span data-stu-id="3d2b0-135">.NET Global tool</span></span>

<span data-ttu-id="3d2b0-136">Derzeit nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="3d2b0-136">Not currently supported</span></span>

- <span data-ttu-id="3d2b0-137">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="3d2b0-137">Ubuntu 20.04</span></span>

## <a name="ubuntu-1604"></a><span data-ttu-id="3d2b0-138">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3d2b0-138">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="3d2b0-139">Installation über das Paketrepository: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3d2b0-139">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="3d2b0-140">PowerShell für Linux wird in Paketrepositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-140">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="3d2b0-141">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-141">The preferred method is as follows:</span></span>

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

<span data-ttu-id="3d2b0-142">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-142">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="3d2b0-143">Nach der Registrierung können Sie PowerShell mit `sudo apt-get install powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-143">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="3d2b0-144">Installation über einen direkten Download: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3d2b0-144">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="3d2b0-145">Laden Sie das Debian-Paket `powershell-lts_7.0.1-1.ubuntu.16.04_amd64.deb` über die Seite [Freigaben][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-145">Download the Debian package `powershell-lts_7.0.1-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="3d2b0-146">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-146">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.1-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="3d2b0-147">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-147">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="3d2b0-148">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-148">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="3d2b0-149">Deinstallation: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3d2b0-149">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="3d2b0-150">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3d2b0-150">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="3d2b0-151">Installation über das Paketrepository: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3d2b0-151">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="3d2b0-152">PowerShell für Linux wird in Paketrepositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-152">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="3d2b0-153">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-153">The preferred method is as follows:</span></span>

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

<span data-ttu-id="3d2b0-154">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-154">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="3d2b0-155">Nach der Registrierung können Sie PowerShell mit `sudo apt-get install powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-155">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="3d2b0-156">Installation über einen direkten Download: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3d2b0-156">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="3d2b0-157">Laden Sie das Debian-Paket `powershell-lts_7.0.1-1.ubuntu.18.04_amd64.deb` über die Seite [Freigaben][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-157">Download the Debian package `powershell-lts_7.0.1-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="3d2b0-158">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-158">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.1-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="3d2b0-159">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-159">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="3d2b0-160">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-160">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="3d2b0-161">Deinstallation: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3d2b0-161">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="3d2b0-162">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="3d2b0-162">Ubuntu 18.10</span></span>

<span data-ttu-id="3d2b0-163">Die Installation wird über `snapd` unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-163">Installation is supported via `snapd`.</span></span> <span data-ttu-id="3d2b0-164">Anweisungen finden Sie unter [Snap-Paket][snap].</span><span class="sxs-lookup"><span data-stu-id="3d2b0-164">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="3d2b0-165">Ubuntu 18.10 ist ein [Zwischenrelease](https://www.ubuntu.com/about/release-cycle), das von der [Community unterstützt](../powershell-support-lifecycle.md) wird.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-165">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="3d2b0-166">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="3d2b0-166">Ubuntu 19.04</span></span>

<span data-ttu-id="3d2b0-167">Die Installation wird über `snapd` unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-167">Installation is supported via `snapd`.</span></span> <span data-ttu-id="3d2b0-168">Anweisungen finden Sie unter [Snap-Paket][snap].</span><span class="sxs-lookup"><span data-stu-id="3d2b0-168">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="3d2b0-169">Ubuntu 19.04 ist ein [Zwischenrelease](https://www.ubuntu.com/about/release-cycle), das von der [Community unterstützt](../powershell-support-lifecycle.md) wird.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-169">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-2004"></a><span data-ttu-id="3d2b0-170">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="3d2b0-170">Ubuntu 20.04</span></span>

<span data-ttu-id="3d2b0-171">PowerShell 20.04 ist ein LTS-Release.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-171">Ubuntu 20.04 is an LTS release.</span></span> <span data-ttu-id="3d2b0-172">Diese Version wird von PowerShell derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-172">PowerShell does not currently support this version.</span></span> <span data-ttu-id="3d2b0-173">Die Unterstützung für diese Version wird für die PowerShell-Version 7.1 in Erwägung gezogen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-173">Support for this version is being considered for the PowerShell 7.1 release.</span></span> <span data-ttu-id="3d2b0-174">Bitte stimmen Sie für diese [Anforderung](https://github.com/PowerShell/PowerShell/issues/12626) zu, wenn Sie Unterstützung für Ubuntu 20.04 wünschen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-174">Please upvote this [request](https://github.com/PowerShell/PowerShell/issues/12626) if you would like support for Ubuntu 20.04.</span></span>

## <a name="debian-8"></a><span data-ttu-id="3d2b0-175">Debian 8</span><span class="sxs-lookup"><span data-stu-id="3d2b0-175">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="3d2b0-176">Installation über das Paketrepository: Debian 8</span><span class="sxs-lookup"><span data-stu-id="3d2b0-176">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="3d2b0-177">PowerShell für Linux wird in Paketrepositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-177">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="3d2b0-178">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-178">The preferred method is as follows:</span></span>

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

<span data-ttu-id="3d2b0-179">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-179">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="3d2b0-180">Nach der Registrierung können Sie PowerShell mit `sudo apt-get install powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-180">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="3d2b0-181">Debian 9</span><span class="sxs-lookup"><span data-stu-id="3d2b0-181">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="3d2b0-182">Installation über das Paketrepository: Debian 9</span><span class="sxs-lookup"><span data-stu-id="3d2b0-182">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="3d2b0-183">PowerShell für Linux wird in Paketrepositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-183">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="3d2b0-184">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-184">The preferred method is as follows:</span></span>

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

<span data-ttu-id="3d2b0-185">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-185">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="3d2b0-186">Nach der Registrierung können Sie PowerShell mit `sudo apt-get install powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-186">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="3d2b0-187">Installation über einen direkten Download: Debian 9</span><span class="sxs-lookup"><span data-stu-id="3d2b0-187">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="3d2b0-188">Laden Sie das Debian-Paket `powershell-lts_7.0.1-1.debian.9_amd64.deb` über die Seite [Freigaben][] auf den Debian-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-188">Download the Debian package `powershell-lts_7.0.1-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="3d2b0-189">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-189">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.1-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="3d2b0-190">Deinstallation: Debian 9</span><span class="sxs-lookup"><span data-stu-id="3d2b0-190">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="3d2b0-191">Debian 10</span><span class="sxs-lookup"><span data-stu-id="3d2b0-191">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="3d2b0-192">Debian 10 wird nur in PowerShell 7.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-192">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository---debian-10"></a><span data-ttu-id="3d2b0-193">Installation über das Paketrepository: Debian 10</span><span class="sxs-lookup"><span data-stu-id="3d2b0-193">Installation via Package Repository - Debian 10</span></span>

<span data-ttu-id="3d2b0-194">PowerShell für Linux wird in Paketrepositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-194">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="3d2b0-195">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-195">The preferred method is as follows:</span></span>

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

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="3d2b0-196">Installation über direkten Download: Debian 10</span><span class="sxs-lookup"><span data-stu-id="3d2b0-196">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="3d2b0-197">Laden Sie das tar.gz-Paket `powershell-7.0.1-linux-x64.tar.gz` über die Seite [Freigaben][] auf den Debian-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-197">Download the tar.gz package `powershell-7.0.1-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="3d2b0-198">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-198">Then, in the terminal, execute the following commands:</span></span>

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
curl -L  https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-7.0.1-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

## <a name="alpine-39-and-310"></a><span data-ttu-id="3d2b0-199">Alpine 3.9 und 3.10</span><span class="sxs-lookup"><span data-stu-id="3d2b0-199">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="3d2b0-200">Alpine 3.9 und 3.10 werden nur in PowerShell 7.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-200">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="3d2b0-201">Installation über direkten Download: Alpine 3.9 und 3.10</span><span class="sxs-lookup"><span data-stu-id="3d2b0-201">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="3d2b0-202">Laden Sie das tar.gz-Paket `powershell-7.0.1-linux-alpine-x64.tar.gz` über die Seite [Freigaben][] auf den Alpine-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-202">Download the tar.gz package `powershell-7.0.1-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="3d2b0-203">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-203">Then, in the terminal, execute the following commands:</span></span>

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
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-7.0.1-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

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

## <a name="centos-7"></a><span data-ttu-id="3d2b0-204">CentOS 7:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-204">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="3d2b0-205">Dieses Paket funktioniert unter Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-205">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="3d2b0-206">Installation über das Paketrepository (bevorzugt): CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3d2b0-206">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="3d2b0-207">PowerShell für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-207">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3d2b0-208">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-208">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="3d2b0-209">Nach der Registrierung können Sie PowerShell mit `sudo yum update powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-209">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="3d2b0-210">Installation über einen direkten Download: CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3d2b0-210">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="3d2b0-211">Für [CentOS 7][]: Laden Sie das RPM-Paket `powershell-lts-7.0.1-1.rhel.7.x86_64.rpm` über die Seite [Freigaben][] auf den CentOS-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-211">Using [CentOS 7][], download the RPM package `powershell-lts-7.0.1-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="3d2b0-212">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-212">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.1-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3d2b0-213">Sie können RPM ohne Download installieren:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-213">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-lts-7.0.1-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="3d2b0-214">Deinstallation: CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3d2b0-214">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3d2b0-216">Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="3d2b0-216">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3d2b0-217">Installation über ein Paketrepository (bevorzugt): Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="3d2b0-217">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="3d2b0-218">PowerShell für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-218">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3d2b0-219">Registrieren Sie das Microsoft-Repository einmal als Superuser.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-219">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="3d2b0-220">Nach der Registrierung können Sie PowerShell mit `sudo yum update powershell` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-220">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3d2b0-221">Installation über einen direkten Download: Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="3d2b0-221">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="3d2b0-222">Laden Sie das RPM-Paket `powershell-lts-7.0.1-1.rhel.7.x86_64.rpm` über die Seite [Freigaben][] auf den Red Hat Enterprise Linux-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-222">Download the RPM package `powershell-lts-7.0.1-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="3d2b0-223">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-223">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.1-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3d2b0-224">Sie können RPM ohne Download installieren:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-224">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-lts-7.0.1-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3d2b0-225">Deinstallation: Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="3d2b0-225">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="3d2b0-226">openSUSE</span><span class="sxs-lookup"><span data-stu-id="3d2b0-226">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="3d2b0-227">Installation: openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="3d2b0-227">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-7.0.1-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="3d2b0-228">Installation: openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="3d2b0-228">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-7.0.1-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="3d2b0-229">Deinstallation: openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="3d2b0-229">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="3d2b0-230">Fedora</span><span class="sxs-lookup"><span data-stu-id="3d2b0-230">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="3d2b0-231">Fedora 28 wird nur in PowerShell 6.1 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-231">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="3d2b0-232">Fedora 29 und 30 werden nur in PowerShell 7.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-232">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="3d2b0-233">Installation über das Paketrepository (bevorzugt): Fedora 28, 29 und 30</span><span class="sxs-lookup"><span data-stu-id="3d2b0-233">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="3d2b0-234">PowerShell für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-234">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf check-update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="3d2b0-235">Installation über direkten Download: Fedora 28, 29 und 30</span><span class="sxs-lookup"><span data-stu-id="3d2b0-235">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="3d2b0-236">Laden Sie das RPM-Paket `powershell-7.0.1-1.rhel.7.x86_64.rpm` über die Seite [Freigaben][] auf den Fedora-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-236">Download the RPM package `powershell-7.0.1-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="3d2b0-237">Führen Sie dann im Terminal folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-237">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.1-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3d2b0-238">Sie können RPM ohne Download installieren:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-238">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-7.0.1-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="3d2b0-239">Deinstallation: Fedora 28, 29 und 30</span><span class="sxs-lookup"><span data-stu-id="3d2b0-239">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="3d2b0-240">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="3d2b0-240">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="3d2b0-241">Arch Linux wird offiziell nicht von Microsoft unterstützt und daher von der Community verwaltet.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-241">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="3d2b0-242">PowerShell ist über das Benutzerrepository [Arch Linux][] verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-242">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

- <span data-ttu-id="3d2b0-243">Es kann gemeinsam mit dem [zuletzt markierten Release][arch-release] kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-243">It can be compiled with the [latest tagged release][arch-release]</span></span>
- <span data-ttu-id="3d2b0-244">Es kann gemeinsam vom [letzten Commit für den Master][arch-git] aus kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-244">It can be compiled from the [latest commit to master][arch-git]</span></span>
- <span data-ttu-id="3d2b0-245">Es kann mithilfe der [zuletzt zur Veröffentlichung bestimmten Binärdatei][arch-bin] installiert werden.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-245">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="3d2b0-246">Pakete im Benutzerrepository „Arch Linux“ werden von der Community verwaltet. Es gibt keinen offiziellen Support.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-246">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="3d2b0-247">Weitere Informationen zum Installieren von Paketen aus dem Benutzerrepository „Arch Linux“ finden Sie im [Arch Linux-Wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) oder unter [Verwenden von PowerShell in Docker](powershell-in-docker.md).</span><span class="sxs-lookup"><span data-stu-id="3d2b0-247">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or [Using PowerShell in Docker](powershell-in-docker.md).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="3d2b0-249">Snap-Paket</span><span class="sxs-lookup"><span data-stu-id="3d2b0-249">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="3d2b0-250">Abrufen von snapd</span><span class="sxs-lookup"><span data-stu-id="3d2b0-250">Getting snapd</span></span>

<span data-ttu-id="3d2b0-251">`snapd` ist für das Ausführen von Snap-Paketen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-251">`snapd` is required to run snaps.</span></span> <span data-ttu-id="3d2b0-252">Halten Sie sich an [diese Anweisungen](https://docs.snapcraft.io/core/install), um sicherzustellen, dass `snapd` installiert ist.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-252">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="3d2b0-253">Installation über Snap</span><span class="sxs-lookup"><span data-stu-id="3d2b0-253">Installation via Snap</span></span>

<span data-ttu-id="3d2b0-254">PowerShell für Linux wird im [Snap-Store](https://snapcraft.io/store) veröffentlicht, um die Installation und die Updates zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-254">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="3d2b0-255">Folgende Methode wird bevorzugt:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-255">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="3d2b0-256">Gehen Sie folgendermaßen vor, wenn Sie eine Vorschauversion installieren möchten:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-256">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="3d2b0-257">Nach der Installation wird für Snap automatisch ein Upgrade durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-257">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="3d2b0-258">Sie können ein Upgrade mit `sudo snap refresh powershell` oder `sudo snap refresh powershell-preview` auslösen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-258">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="3d2b0-259">Deinstallation</span><span class="sxs-lookup"><span data-stu-id="3d2b0-259">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="3d2b0-260">oder</span><span class="sxs-lookup"><span data-stu-id="3d2b0-260">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="3d2b0-261">Kali</span><span class="sxs-lookup"><span data-stu-id="3d2b0-261">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="3d2b0-262">Kali wird offiziell nicht von Microsoft unterstützt und daher von der Community verwaltet.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-262">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="3d2b0-263">Installation: Kali</span><span class="sxs-lookup"><span data-stu-id="3d2b0-263">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="3d2b0-264">Deinstallation: Kali</span><span class="sxs-lookup"><span data-stu-id="3d2b0-264">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="3d2b0-265">Raspbian</span><span class="sxs-lookup"><span data-stu-id="3d2b0-265">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="3d2b0-266">Die Unterstützung von Raspbian wird noch getestet.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-266">Raspbian support is experimental.</span></span>

<span data-ttu-id="3d2b0-267">Derzeit wird PowerShell nur unter Raspbian Stretch unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-267">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="3d2b0-268">Außerdem funktionieren CoreCLR und PowerShell nur auf Geräten mit Pi 2 und Pi 3, da andere Geräte, wie z. B. [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), einen nicht unterstützten Prozessor haben.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-268">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="3d2b0-269">Laden Sie [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) herunter, und folgen Sie den [Installationsanweisungen](https://www.raspberrypi.org/documentation/installation/installing-images/README.md), um es zu installieren.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-269">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="3d2b0-270">Installation: Raspbian</span><span class="sxs-lookup"><span data-stu-id="3d2b0-270">Installation - Raspbian</span></span>

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
wget https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-7.0.1-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-7.0.1-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="3d2b0-271">Optional können Sie eine symbolische Verknüpfung erstellen, damit Sie PowerShell ohne Angabe des Pfads zur Binärdatei `pwsh` starten können.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-271">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="3d2b0-272">Deinstallation: Raspbian</span><span class="sxs-lookup"><span data-stu-id="3d2b0-272">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a><span data-ttu-id="3d2b0-273">Installieren von Vorschauversionen</span><span class="sxs-lookup"><span data-stu-id="3d2b0-273">Installing Preview Releases</span></span>

<span data-ttu-id="3d2b0-274">Wenn eine Vorschauversion von PowerShell für Linux über ein Paketrepository installiert wird, ändert sich der Paketname von `powershell` in `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-274">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="3d2b0-275">Bei einer Installation über einen direkten Download wird nur der Dateiname geändert.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-275">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="3d2b0-276">In der nachfolgenden Tabelle werden die Befehle aufgeführt, über die Sie Pakete stabiler Versionen und von Vorschauversionen mithilfe der verschiedenen Paket-Manager installieren können:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-276">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="3d2b0-277">Distribution(en)</span><span class="sxs-lookup"><span data-stu-id="3d2b0-277">Distribution(s)</span></span> |            <span data-ttu-id="3d2b0-278">Befehl für die stabile Version</span><span class="sxs-lookup"><span data-stu-id="3d2b0-278">Stable Command</span></span>            |               <span data-ttu-id="3d2b0-279">Befehl für die Vorschauversion</span><span class="sxs-lookup"><span data-stu-id="3d2b0-279">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="3d2b0-280">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="3d2b0-280">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="3d2b0-281">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="3d2b0-281">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="3d2b0-282">Fedora</span><span class="sxs-lookup"><span data-stu-id="3d2b0-282">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="3d2b0-283">Installieren als globales .NET-Tool</span><span class="sxs-lookup"><span data-stu-id="3d2b0-283">Install as a .NET Global tool</span></span>

<span data-ttu-id="3d2b0-284">Wenn Sie das [.NET Core SDK](/dotnet/core/sdk) bereits installiert haben, können Sie PowerShell einfach als [globales .NET-Tool](/dotnet/core/tools/global-tools) installieren.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-284">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="3d2b0-285">Der .NET-Toolinstaller fügt `~/.dotnet/tools` Ihrer `PATH`-Umgebungsvariablen hinzu.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-285">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="3d2b0-286">Die aktuell ausgeführte Shell verfügt jedoch nicht über den aktualisierten `PATH`.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-286">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="3d2b0-287">Sie sollten PowerShell über eine neue Shell starten können, indem Sie `pwsh` eingeben.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-287">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="3d2b0-288">Archive der Binärdateien</span><span class="sxs-lookup"><span data-stu-id="3d2b0-288">Binary Archives</span></span>

<span data-ttu-id="3d2b0-289">`tar.gz`-Archive der PowerShell-Binärdateien werden für Linux-Plattformen zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-289">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="3d2b0-290">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="3d2b0-290">Dependencies</span></span>

<span data-ttu-id="3d2b0-291">PowerShell erstellt portierbare Binärdateien für alle Linux-Distributionen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-291">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="3d2b0-292">Allerdings erfordern die .NET Core-Runtime und PowerShell verschiedene Abhängigkeiten für die verschiedenen Distributionen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-292">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="3d2b0-293">Im folgenden Diagramm werden die Abhängigkeiten von .NET Core 2.0 für die verschiedenen Linux-Distributionen dargestellt, die offiziell unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-293">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="3d2b0-294">OS</span><span class="sxs-lookup"><span data-stu-id="3d2b0-294">OS</span></span>                 | <span data-ttu-id="3d2b0-295">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="3d2b0-295">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="3d2b0-296">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3d2b0-296">Ubuntu 16.04</span></span>       | <span data-ttu-id="3d2b0-297">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="3d2b0-297">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3d2b0-298">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="3d2b0-298">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="3d2b0-299">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="3d2b0-299">Ubuntu 17.10</span></span>       | <span data-ttu-id="3d2b0-300">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="3d2b0-300">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3d2b0-301">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="3d2b0-301">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="3d2b0-302">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3d2b0-302">Ubuntu 18.04</span></span>       | <span data-ttu-id="3d2b0-303">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="3d2b0-303">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3d2b0-304">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="3d2b0-304">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="3d2b0-305">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="3d2b0-305">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="3d2b0-306">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="3d2b0-306">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3d2b0-307">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="3d2b0-307">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="3d2b0-308">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="3d2b0-308">Debian 9 (Stretch)</span></span> | <span data-ttu-id="3d2b0-309">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="3d2b0-309">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3d2b0-310">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="3d2b0-310">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="3d2b0-311">CentOS 7:</span><span class="sxs-lookup"><span data-stu-id="3d2b0-311">CentOS 7</span></span> <br> <span data-ttu-id="3d2b0-312">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="3d2b0-312">Oracle Linux 7</span></span> <br> <span data-ttu-id="3d2b0-313">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="3d2b0-313">RHEL 7</span></span> | <span data-ttu-id="3d2b0-314">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="3d2b0-314">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="3d2b0-315">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="3d2b0-315">openSUSE 42.3</span></span> | <span data-ttu-id="3d2b0-316">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="3d2b0-316">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="3d2b0-317">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="3d2b0-317">openSUSE Leap 15</span></span> | <span data-ttu-id="3d2b0-318">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="3d2b0-318">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="3d2b0-319">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="3d2b0-319">Fedora 27</span></span> <br> <span data-ttu-id="3d2b0-320">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3d2b0-320">Fedora 28</span></span> | <span data-ttu-id="3d2b0-321">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="3d2b0-321">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="3d2b0-322">Sie müssen zur Bereitstellung von PowerShell-Binärdateien für nicht offiziell unterstützte Linux-Distributionen die notwendigen Abhängigkeiten für das Zielbetriebssystem über zusätzliche Schritte installieren.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-322">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="3d2b0-323">Beispielsweise installiert die [Amazon Linux-Dockerfile][amazon-dockerfile] zuerst die Abhängigkeiten und extrahiert anschließend das `tar.gz`-Archiv für Linux.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-323">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="3d2b0-324">Installation: Archive von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="3d2b0-324">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="3d2b0-325">Linux</span><span class="sxs-lookup"><span data-stu-id="3d2b0-325">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-7.0.1-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="3d2b0-326">Deinstallation: Archive von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="3d2b0-326">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="3d2b0-327">Paths</span><span class="sxs-lookup"><span data-stu-id="3d2b0-327">Paths</span></span>

- <span data-ttu-id="3d2b0-328">`$PSHOME` ist `/opt/microsoft/powershell/7/`.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-328">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="3d2b0-329">Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-329">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="3d2b0-330">Standardprofile werden über `$PSHOME/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-330">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="3d2b0-331">Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-331">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="3d2b0-332">Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-332">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="3d2b0-333">Standardmodule werden über `$PSHOME/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-333">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="3d2b0-334">Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-334">PSReadLine history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="3d2b0-335">Die Profile beachten die Konfigurationen von PowerShell pro Host. Das bedeutet, die hostspezifischen Standardprofile sind an denselben Orten unter `Microsoft.PowerShell_profile.ps1` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-335">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="3d2b0-336">PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter Linux ein.</span><span class="sxs-lookup"><span data-stu-id="3d2b0-336">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Freigaben]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
