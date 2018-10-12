---
title: Installieren von PowerShell Core unter Linux
description: Informationen zur Installation von PowerShell Core auf verschiedenen Linux-Distributionen
ms.date: 08/06/2018
ms.openlocfilehash: acd88f686ce6a657c9ccda9d2615d4ab355ddcbe
ms.sourcegitcommit: 601609575a3214ea7086a3bcb586ae0d1df3d418
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "46532951"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="0da41-103">Installieren von PowerShell Core unter Linux</span><span class="sxs-lookup"><span data-stu-id="0da41-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="0da41-104">Unterstützt [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] und [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="0da41-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="0da41-105">Für nicht offiziell unterstützte Linux-Distributionen können Sie versuchen, das [Snap-Paket für PowerShell][snap] zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="0da41-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="0da41-106">Stattdessen können Sie auch versuchen, PowerShell-Binärdateien über das [`tar.gz`-Archiv][tar] für Linux bereitzustellen. Dafür müssen Sie aber basierend auf Ihrem Betriebssystem die benötigten Abhängigkeiten in zusätzlichen Schritten einrichten.</span><span class="sxs-lookup"><span data-stu-id="0da41-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="0da41-107">Sämtliche Pakete sind auf der Seite [Releases][] über GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="0da41-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="0da41-108">Führen Sie `pwsh` über das Terminal aus, nachdem Sie das Paket installiert haben.</span><span class="sxs-lookup"><span data-stu-id="0da41-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="installing-preview-releases"></a><span data-ttu-id="0da41-109">Installieren von Vorschauversionen</span><span class="sxs-lookup"><span data-stu-id="0da41-109">Installing Preview Releases</span></span>

<span data-ttu-id="0da41-110">Wenn eine Vorschauversion von PowerShell Core für Linux über ein Paketrepository installiert wird, ändert sich der Paketname von `powershell` in `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="0da41-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="0da41-111">Bei einer Installation über einen direkten Download wird nur der Dateiname geändert.</span><span class="sxs-lookup"><span data-stu-id="0da41-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="0da41-112">In der nachfolgenden Tabelle werden die Befehle aufgeführt, über die Sie Pakete stabiler Versionen und von Vorschauversionen unter Verwendung der verschiedenen Paket-Manager installieren können:</span><span class="sxs-lookup"><span data-stu-id="0da41-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="0da41-113">Distribution(en)</span><span class="sxs-lookup"><span data-stu-id="0da41-113">Distribution(s)</span></span>|<span data-ttu-id="0da41-114">Befehl für die stabile Version</span><span class="sxs-lookup"><span data-stu-id="0da41-114">Stable Command</span></span> | <span data-ttu-id="0da41-115">Befehl für die Vorschauversion</span><span class="sxs-lookup"><span data-stu-id="0da41-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="0da41-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="0da41-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="0da41-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="0da41-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="0da41-118">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="0da41-118">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="0da41-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="0da41-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="0da41-120">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="0da41-120">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="0da41-121">Installation über das Paketrepository: Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="0da41-121">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="0da41-122">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="0da41-122">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="0da41-123">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="0da41-123">This is the preferred method.</span></span>

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

<span data-ttu-id="0da41-124">Registrieren Sie das Microsoft-Repository als Superuser.</span><span class="sxs-lookup"><span data-stu-id="0da41-124">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="0da41-125">Von nun an müssen Sie nur `sudo apt-get upgrade powershell` verwenden, um die Installation zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="0da41-125">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="0da41-126">Installation über einen direkten Download: Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="0da41-126">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="0da41-127">Laden Sie das Debian-Paket `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="0da41-127">Download the Debian package `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="0da41-128">über die Seite [Releases][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="0da41-128">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="0da41-129">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="0da41-129">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="0da41-130">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="0da41-130">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="0da41-131">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="0da41-131">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="0da41-132">Deinstallation: Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="0da41-132">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="0da41-133">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="0da41-133">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="0da41-134">Installation über das Paketrepository: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="0da41-134">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="0da41-135">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="0da41-135">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="0da41-136">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="0da41-136">This is the preferred method.</span></span>

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

<span data-ttu-id="0da41-137">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="0da41-137">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="0da41-138">Installation über einen direkten Download: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="0da41-138">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="0da41-139">Laden Sie das Debian-Paket `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="0da41-139">Download the Debian package `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="0da41-140">über die Seite [Releases][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="0da41-140">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="0da41-141">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="0da41-141">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="0da41-142">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="0da41-142">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="0da41-143">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="0da41-143">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="0da41-144">Deinstallation: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="0da41-144">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="0da41-145">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="0da41-145">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="0da41-146">Die Unterstützung für Ubuntu 18.04. wurde nach `6.1.0-preview.2` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="0da41-146">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="0da41-147">Installation über das Paketrepository: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="0da41-147">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="0da41-148">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="0da41-148">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="0da41-149">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="0da41-149">This is the preferred method.</span></span>

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

<span data-ttu-id="0da41-150">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="0da41-150">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="0da41-151">Installation über einen direkten Download: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="0da41-151">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="0da41-152">Laden Sie das Debian-Paket `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="0da41-152">Download the Debian package `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="0da41-153">über die Seite [Releases][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="0da41-153">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="0da41-154">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="0da41-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="0da41-155">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="0da41-155">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="0da41-156">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="0da41-156">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="0da41-157">Deinstallation: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="0da41-157">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="0da41-158">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="0da41-158">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="0da41-159">Die Unterstützung für Ubuntu 18.10. wurde nach `6.1.0-preview.3` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="0da41-159">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="0da41-160">Bei 18.10 handelt es sich um einen Daily Build, daher wird diese Version nur von der Community unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0da41-160">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="0da41-161">Die Installation auf 18.10 wird über `snapd` unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0da41-161">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="0da41-162">Eine vollständige Anweisung finden Sie unter [Snap-Paket][snap].</span><span class="sxs-lookup"><span data-stu-id="0da41-162">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="0da41-163">Debian 8</span><span class="sxs-lookup"><span data-stu-id="0da41-163">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="0da41-164">Installation über das Paketrepository: Debian 8</span><span class="sxs-lookup"><span data-stu-id="0da41-164">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="0da41-165">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="0da41-165">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="0da41-166">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="0da41-166">This is the preferred method.</span></span>

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

<span data-ttu-id="0da41-167">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="0da41-167">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="0da41-168">Installation über einen direkten Download: Debian 8</span><span class="sxs-lookup"><span data-stu-id="0da41-168">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="0da41-169">Laden Sie das Debian-Paket `powershell_6.1.0-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="0da41-169">Download the Debian package `powershell_6.1.0-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="0da41-170">über die Seite [Releases][] auf den Debian-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="0da41-170">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="0da41-171">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="0da41-171">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="0da41-172">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="0da41-172">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="0da41-173">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="0da41-173">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="0da41-174">Deinstallation: Debian 8</span><span class="sxs-lookup"><span data-stu-id="0da41-174">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="0da41-175">Debian 9</span><span class="sxs-lookup"><span data-stu-id="0da41-175">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="0da41-176">Installation über das Paketrepository: Debian 9</span><span class="sxs-lookup"><span data-stu-id="0da41-176">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="0da41-177">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="0da41-177">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="0da41-178">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="0da41-178">This is the preferred method.</span></span>

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

<span data-ttu-id="0da41-179">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="0da41-179">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="0da41-180">Installation über einen direkten Download: Debian 9</span><span class="sxs-lookup"><span data-stu-id="0da41-180">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="0da41-181">Laden Sie das Debian-Paket `powershell_6.1.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="0da41-181">Download the Debian package `powershell_6.1.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="0da41-182">über die Seite [Releases][] auf den Debian-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="0da41-182">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="0da41-183">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="0da41-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="0da41-184">Deinstallation: Debian 9</span><span class="sxs-lookup"><span data-stu-id="0da41-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="0da41-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0da41-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="0da41-186">Dieses Paket funktioniert ebenfalls unter Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="0da41-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="0da41-187">Installation über das Paketrepository (bevorzugt): CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0da41-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="0da41-188">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="0da41-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="0da41-189">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo yum update powershell` verwenden, um Updates für PowerShell auszuführen.</span><span class="sxs-lookup"><span data-stu-id="0da41-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="0da41-190">Installation über einen direkten Download: CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0da41-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="0da41-191">Laden Sie mithilfe von [CentOS 7][] das RPM-Paket `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="0da41-191">Using [CentOS 7][], download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="0da41-192">über die Seite [Releases][] auf den CentOS-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="0da41-192">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="0da41-193">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="0da41-193">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0da41-194">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="0da41-194">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="0da41-195">Deinstallation: CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0da41-195">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="0da41-197">Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="0da41-197">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="0da41-198">Installation über ein Paketrepository (bevorzugt): Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="0da41-198">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="0da41-199">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="0da41-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="0da41-200">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo yum update powershell` verwenden, um Updates für PowerShell auszuführen.</span><span class="sxs-lookup"><span data-stu-id="0da41-200">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="0da41-201">Installation über einen direkten Download: Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="0da41-201">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="0da41-202">Laden Sie das RPM-Paket `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="0da41-202">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="0da41-203">über die Seite [Releases][] auf den Red Hat Enterprise Linux-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="0da41-203">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="0da41-204">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="0da41-204">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0da41-205">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="0da41-205">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="0da41-206">Deinstallation: Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="0da41-206">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="0da41-207">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="0da41-207">OpenSUSE 42.3</span></span>

<span data-ttu-id="0da41-208">Bei der Installation von PowerShell Core verursacht `zypper` eventuell den folgenden Fehler:</span><span class="sxs-lookup"><span data-stu-id="0da41-208">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.1.0-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.1.0-1.rhel.7.x86_64
 Solution 2: break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="0da41-209">Stellen Sie in diesem Fall sicher, dass eine kompatible `libcurl`-Bibliothek vorhanden ist, indem Sie überprüfen, ob der folgende Befehl das `libcurl4`-Paket als installiert anzeigt:</span><span class="sxs-lookup"><span data-stu-id="0da41-209">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="0da41-210">Wählen Sie bei der Installation des PowerShell-Pakets die Lösung `break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies` aus.</span><span class="sxs-lookup"><span data-stu-id="0da41-210">Then choose the `break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="0da41-211">Installation über das Paketrepository (bevorzugt): openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="0da41-211">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="0da41-212">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="0da41-212">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="0da41-213">Installation über einen direkten Download: openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="0da41-213">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="0da41-214">Laden Sie das RPM-Paket `powershell-6.1.0-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den OpenSUSE-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="0da41-214">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0da41-215">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="0da41-215">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="0da41-216">Deinstallation: openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="0da41-216">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="0da41-217">Fedora</span><span class="sxs-lookup"><span data-stu-id="0da41-217">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="0da41-218">Fedora 28 wird nur in PowerShell Core 6.1 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0da41-218">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="0da41-219">Installation über das Paketrepository (bevorzugt): Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="0da41-219">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="0da41-220">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="0da41-220">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="0da41-221">Installation über einen direkten Download: Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="0da41-221">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="0da41-222">Laden Sie das RPM-Paket `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="0da41-222">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="0da41-223">über die Seite [Releases][] auf den Fedora-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="0da41-223">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="0da41-224">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="0da41-224">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0da41-225">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="0da41-225">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="0da41-226">Deinstallation: Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="0da41-226">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="0da41-227">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="0da41-227">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="0da41-228">Die Unterstützung von Arch wird noch getestet.</span><span class="sxs-lookup"><span data-stu-id="0da41-228">Arch support is experimental.</span></span>

<span data-ttu-id="0da41-229">PowerShell ist über das Benutzerrepository [Arch Linux][] verfügbar.</span><span class="sxs-lookup"><span data-stu-id="0da41-229">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="0da41-230">Es kann gemeinsam mit dem [zuletzt markierten Release][arch-release] installiert werden.</span><span class="sxs-lookup"><span data-stu-id="0da41-230">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="0da41-231">Es kann gemeinsam mit dem [letzten Commit für den Master][arch-git] kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="0da41-231">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="0da41-232">Es kann mithilfe der [zuletzt veröffentlichten Binärdatei][arch-bin] kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="0da41-232">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="0da41-233">Pakete im Benutzerrepository „Arch Linux“ werden von der Community verwaltet. Es gibt keinen offiziellen Support.</span><span class="sxs-lookup"><span data-stu-id="0da41-233">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="0da41-234">Weitere Informationen zum Installieren von Paketen aus dem Benutzerrepository „Arch Linux“ finden Sie im [Arch Linux-Wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) oder in [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) der Community.</span><span class="sxs-lookup"><span data-stu-id="0da41-234">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="0da41-236">Snap-Paket</span><span class="sxs-lookup"><span data-stu-id="0da41-236">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="0da41-237">Abrufen von snapd</span><span class="sxs-lookup"><span data-stu-id="0da41-237">Getting snapd</span></span>

<span data-ttu-id="0da41-238">`snapd` ist für das Ausführen von Snap-Paketen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="0da41-238">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="0da41-239">Halten Sie sich an [diese Anweisungen](https://docs.snapcraft.io/core/install), um sicherzustellen, dass `snapd` installiert ist.</span><span class="sxs-lookup"><span data-stu-id="0da41-239">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="0da41-240">Installation über Snap</span><span class="sxs-lookup"><span data-stu-id="0da41-240">Installation via Snap</span></span>

<span data-ttu-id="0da41-241">PowerShell Core für Linux wird im [Snap-Store](https://snapcraft.io/store) veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="0da41-241">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="0da41-242">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="0da41-242">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="0da41-243">Nach der Installation führt Snap automatisch ein Upgrade durch, Sie können jedoch ein Upgrade mithilfe von `sudo snap refresh powershell-preview` auslösen.</span><span class="sxs-lookup"><span data-stu-id="0da41-243">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="0da41-244">Deinstallation</span><span class="sxs-lookup"><span data-stu-id="0da41-244">Uninstallation</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="0da41-245">Kali</span><span class="sxs-lookup"><span data-stu-id="0da41-245">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="0da41-246">Die Kali-Unterstützung funktioniert derzeit nicht.</span><span class="sxs-lookup"><span data-stu-id="0da41-246">Kali support is not currently working.</span></span> <span data-ttu-id="0da41-247">Verwenden Sie stattdessen das [Snap-Paket][snap].</span><span class="sxs-lookup"><span data-stu-id="0da41-247">Please use the [Snap package][snap] instead.</span></span>

### <a name="installation"></a><span data-ttu-id="0da41-248">Installation</span><span class="sxs-lookup"><span data-stu-id="0da41-248">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="0da41-249">Deinstallation: Kali</span><span class="sxs-lookup"><span data-stu-id="0da41-249">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="0da41-250">Raspbian</span><span class="sxs-lookup"><span data-stu-id="0da41-250">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="0da41-251">Die Unterstützung von Raspbian wird noch getestet.</span><span class="sxs-lookup"><span data-stu-id="0da41-251">Raspbian support is experimental.</span></span>

<span data-ttu-id="0da41-252">Derzeit wird PowerShell nur unter Raspbian Stretch unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0da41-252">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="0da41-253">Außerdem funktioniert CoreCLR (und daher auch PowerShell Core) nur auf Geräten mit Pi 2 und Pi 3, da andere Geräte, wie z.B. [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), einen nicht unterstützten Prozessor haben.</span><span class="sxs-lookup"><span data-stu-id="0da41-253">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="0da41-254">Laden Sie [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) herunter, und folgen Sie den [Installationsanweisungen](https://www.raspberrypi.org/documentation/installation/installing-images/README.md), um es zu installieren.</span><span class="sxs-lookup"><span data-stu-id="0da41-254">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="0da41-255">Installation</span><span class="sxs-lookup"><span data-stu-id="0da41-255">Installation</span></span>

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

<span data-ttu-id="0da41-256">Optional können Sie eine symbolische Verknüpfung erstellen, damit Sie PowerShell ohne Angabe eines Pfads auf die Binärdatei „pwsh“ starten können.</span><span class="sxs-lookup"><span data-stu-id="0da41-256">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="0da41-257">Deinstallation: Raspbian</span><span class="sxs-lookup"><span data-stu-id="0da41-257">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="0da41-258">Archive der Binärdateien</span><span class="sxs-lookup"><span data-stu-id="0da41-258">Binary Archives</span></span>

<span data-ttu-id="0da41-259">`tar.gz`-Archive der PowerShell-Binärdateien werden für Linux-Plattformen zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="0da41-259">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="0da41-260">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="0da41-260">Dependencies</span></span>

<span data-ttu-id="0da41-261">PowerShell erstellt portierbare Binärdateien für alle Linux-Distributionen.</span><span class="sxs-lookup"><span data-stu-id="0da41-261">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="0da41-262">Allerdings erfordert die .NET Core-Laufzeit, und damit auch PowerShell, verschiedene Abhängigkeiten für die verschiedenen Distributionen.</span><span class="sxs-lookup"><span data-stu-id="0da41-262">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="0da41-263">Im folgenden Diagramm werden die Abhängigkeiten von .NET Core 2.0 für die verschiedenen Linux-Distributionen dargestellt, die offiziell unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="0da41-263">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="0da41-264">Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="0da41-264">OS</span></span>                 | <span data-ttu-id="0da41-265">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="0da41-265">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="0da41-266">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="0da41-266">Ubuntu 14.04</span></span>       | <span data-ttu-id="0da41-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="0da41-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0da41-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="0da41-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="0da41-269">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="0da41-269">Ubuntu 16.04</span></span>       | <span data-ttu-id="0da41-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="0da41-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0da41-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="0da41-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="0da41-272">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="0da41-272">Ubuntu 17.10</span></span>       | <span data-ttu-id="0da41-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="0da41-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0da41-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="0da41-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="0da41-275">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="0da41-275">Ubuntu 18.04</span></span>       | <span data-ttu-id="0da41-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="0da41-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0da41-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="0da41-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="0da41-278">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="0da41-278">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="0da41-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="0da41-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0da41-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="0da41-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="0da41-281">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="0da41-281">Debian 9 (Stretch)</span></span> | <span data-ttu-id="0da41-282">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="0da41-282">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0da41-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="0da41-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="0da41-284">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0da41-284">CentOS 7</span></span> <br> <span data-ttu-id="0da41-285">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="0da41-285">Oracle Linux 7</span></span> <br> <span data-ttu-id="0da41-286">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="0da41-286">RHEL 7</span></span> <br> <span data-ttu-id="0da41-287">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="0da41-287">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="0da41-288">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="0da41-288">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="0da41-289">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="0da41-289">Fedora 27</span></span> <br> <span data-ttu-id="0da41-290">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="0da41-290">Fedora 28</span></span> | <span data-ttu-id="0da41-291">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="0da41-291">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="0da41-292">Sie müssen zur Bereitstellung von PowerShell-Binärdateien für nicht offiziell unterstützte Linux-Distributionen die notwendigen Abhängigkeiten für das Zielbetriebssystem über zusätzliche Schritte installieren.</span><span class="sxs-lookup"><span data-stu-id="0da41-292">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="0da41-293">Beispielsweise installiert die [Amazon Linux-Dockerfile][amazon-dockerfile] zuerst die Abhängigkeiten und extrahiert anschließend erst das Linux-`tar.gz`-Archiv.</span><span class="sxs-lookup"><span data-stu-id="0da41-293">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="0da41-294">Installation: Archive von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="0da41-294">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="0da41-295">Linux</span><span class="sxs-lookup"><span data-stu-id="0da41-295">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="0da41-296">Deinstallation: Archive von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="0da41-296">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="0da41-297">Pfade</span><span class="sxs-lookup"><span data-stu-id="0da41-297">Paths</span></span>

* <span data-ttu-id="0da41-298">`$PSHOME` ist `/opt/microsoft/powershell/6.1.0/`.</span><span class="sxs-lookup"><span data-stu-id="0da41-298">`$PSHOME` is `/opt/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="0da41-299">Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="0da41-299">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="0da41-300">Standardprofile werden über `$PSHOME/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="0da41-300">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="0da41-301">Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="0da41-301">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="0da41-302">Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="0da41-302">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="0da41-303">Standardmodule werden über `$PSHOME/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="0da41-303">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="0da41-304">Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="0da41-304">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="0da41-305">Die Profile beachten die Konfigurationen von PowerShell pro Host. Das bedeutet, die hostspezifischen Standardprofile sind an denselben Orten unter `Microsoft.PowerShell_profile.ps1` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="0da41-305">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="0da41-306">PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter Linux ein.</span><span class="sxs-lookup"><span data-stu-id="0da41-306">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Releases]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
