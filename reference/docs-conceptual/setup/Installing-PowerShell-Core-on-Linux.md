---
title: Installieren von PowerShell Core unter Linux
description: Informationen zur Installation von PowerShell Core auf verschiedenen Linux-Distributionen
ms.date: 08/06/2018
ms.openlocfilehash: a6b0e3003f84ea6dc99cffcc7edf1b5b6963aa21
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587447"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="e9e27-103">Installieren von PowerShell Core unter Linux</span><span class="sxs-lookup"><span data-stu-id="e9e27-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="e9e27-104">Unterstützt [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] und [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="e9e27-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="e9e27-105">Für nicht offiziell unterstützte Linux-Distributionen können Sie versuchen, das [Snap-Paket für PowerShell][snap] zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e9e27-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="e9e27-106">Stattdessen können Sie auch versuchen, PowerShell-Binärdateien über das [`tar.gz`-Archiv][tar] für Linux bereitzustellen. Dafür müssen Sie aber basierend auf Ihrem Betriebssystem die benötigten Abhängigkeiten in zusätzlichen Schritten einrichten.</span><span class="sxs-lookup"><span data-stu-id="e9e27-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="e9e27-107">Sämtliche Pakete sind auf der Seite [Releases][] über GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e9e27-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="e9e27-108">Führen Sie `pwsh` über das Terminal aus, nachdem Sie das Paket installiert haben.</span><span class="sxs-lookup"><span data-stu-id="e9e27-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="installing-preview-releases"></a><span data-ttu-id="e9e27-109">Installieren von Vorschauversionen</span><span class="sxs-lookup"><span data-stu-id="e9e27-109">Installing Preview Releases</span></span>

<span data-ttu-id="e9e27-110">Wenn eine Vorschauversion von PowerShell Core für Linux über ein Paketrepository installiert wird, ändert sich der Paketname von `powershell` in `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="e9e27-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="e9e27-111">Bei einer Installation über einen direkten Download wird nur der Dateiname geändert.</span><span class="sxs-lookup"><span data-stu-id="e9e27-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="e9e27-112">In der nachfolgenden Tabelle werden die Befehle aufgeführt, über die Sie Pakete stabiler Versionen und von Vorschauversionen unter Verwendung der verschiedenen Paket-Manager installieren können:</span><span class="sxs-lookup"><span data-stu-id="e9e27-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="e9e27-113">Distribution(en)</span><span class="sxs-lookup"><span data-stu-id="e9e27-113">Distribution(s)</span></span>|<span data-ttu-id="e9e27-114">Befehl für die stabile Version</span><span class="sxs-lookup"><span data-stu-id="e9e27-114">Stable Command</span></span> | <span data-ttu-id="e9e27-115">Befehl für die Vorschauversion</span><span class="sxs-lookup"><span data-stu-id="e9e27-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="e9e27-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="e9e27-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="e9e27-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="e9e27-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="e9e27-118">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="e9e27-118">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="e9e27-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="e9e27-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="e9e27-120">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e9e27-120">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="e9e27-121">Installation über das Paketrepository: Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e9e27-121">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="e9e27-122">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-122">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e9e27-123">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="e9e27-123">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e9e27-124">Registrieren Sie das Microsoft-Repository als Superuser.</span><span class="sxs-lookup"><span data-stu-id="e9e27-124">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="e9e27-125">Von nun an müssen Sie nur `sudo apt-get upgrade powershell` verwenden, um die Installation zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="e9e27-125">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="e9e27-126">Installation über einen direkten Download: Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e9e27-126">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="e9e27-127">Laden Sie das Debian-Paket `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` über die Seite [Releases][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="e9e27-127">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e9e27-128">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="e9e27-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e9e27-129">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="e9e27-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e9e27-130">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="e9e27-131">Deinstallation: Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e9e27-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="e9e27-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e9e27-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="e9e27-133">Installation über das Paketrepository: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e9e27-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="e9e27-134">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e9e27-135">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="e9e27-135">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/16.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e9e27-136">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="e9e27-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="e9e27-137">Installation über einen direkten Download: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e9e27-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="e9e27-138">Laden Sie das Debian-Paket `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` über die Seite [Releases][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="e9e27-138">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e9e27-139">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="e9e27-139">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e9e27-140">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="e9e27-140">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e9e27-141">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="e9e27-142">Deinstallation: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e9e27-142">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="e9e27-143">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e9e27-143">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="e9e27-144">Die Unterstützung für Ubuntu 18.04. wurde nach `6.1.0-preview.2` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e9e27-144">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="e9e27-145">Installation über das Paketrepository: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e9e27-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="e9e27-146">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e9e27-147">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="e9e27-147">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell-preview

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="e9e27-148">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="e9e27-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="e9e27-149">Installation über einen direkten Download: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e9e27-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="e9e27-150">Laden Sie das Debian-Paket `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` über die Seite [Releases][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="e9e27-150">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e9e27-151">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="e9e27-151">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e9e27-152">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="e9e27-152">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e9e27-153">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-153">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="e9e27-154">Deinstallation: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e9e27-154">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="e9e27-155">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="e9e27-155">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="e9e27-156">Die Unterstützung für Ubuntu 18.10. wurde nach `6.1.0-preview.3` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e9e27-156">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="e9e27-157">Bei 18.10 handelt es sich um einen Daily Build, daher wird diese Version nur von der Community unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e9e27-157">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="e9e27-158">Die Installation auf 18.10 wird über `snapd` unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e9e27-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="e9e27-159">Eine vollständige Anweisung finden Sie unter [Snap-Paket][snap].</span><span class="sxs-lookup"><span data-stu-id="e9e27-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="e9e27-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="e9e27-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="e9e27-161">Installation über das Paketrepository: Debian 8</span><span class="sxs-lookup"><span data-stu-id="e9e27-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="e9e27-162">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e9e27-163">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="e9e27-163">This is the preferred method.</span></span>

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

<span data-ttu-id="e9e27-164">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="e9e27-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="e9e27-165">Installation über einen direkten Download: Debian 8</span><span class="sxs-lookup"><span data-stu-id="e9e27-165">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="e9e27-166">Laden Sie das Debian-Paket `powershell_6.0.2-1.debian.8_amd64.deb` über die Seite [Releases][] auf den Debian-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="e9e27-166">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="e9e27-167">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="e9e27-167">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e9e27-168">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="e9e27-168">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e9e27-169">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-169">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="e9e27-170">Deinstallation: Debian 8</span><span class="sxs-lookup"><span data-stu-id="e9e27-170">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="e9e27-171">Debian 9</span><span class="sxs-lookup"><span data-stu-id="e9e27-171">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="e9e27-172">Installation über das Paketrepository: Debian 9</span><span class="sxs-lookup"><span data-stu-id="e9e27-172">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="e9e27-173">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-173">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e9e27-174">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="e9e27-174">This is the preferred method.</span></span>

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

<span data-ttu-id="e9e27-175">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="e9e27-175">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="e9e27-176">Installation über einen direkten Download: Debian 9</span><span class="sxs-lookup"><span data-stu-id="e9e27-176">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="e9e27-177">Laden Sie das Debian-Paket `powershell_6.0.2-1.debian.9_amd64.deb` über die Seite [Releases][] auf den Debian-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="e9e27-177">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="e9e27-178">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="e9e27-178">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="e9e27-179">Deinstallation: Debian 9</span><span class="sxs-lookup"><span data-stu-id="e9e27-179">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="e9e27-180">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e9e27-180">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="e9e27-181">Dieses Paket funktioniert ebenfalls unter Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="e9e27-181">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="e9e27-182">Installation über das Paketrepository (bevorzugt): CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e9e27-182">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="e9e27-183">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-183">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e9e27-184">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo yum update powershell` verwenden, um Updates für PowerShell auszuführen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-184">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="e9e27-185">Installation über einen direkten Download: CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e9e27-185">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="e9e27-186">Für [CentOS 7][]: Laden Sie das RPM-Paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den CentOS-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="e9e27-186">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="e9e27-187">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="e9e27-187">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e9e27-188">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="e9e27-188">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="e9e27-189">Deinstallation: CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e9e27-189">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e9e27-191">Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="e9e27-191">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e9e27-192">Installation über ein Paketrepository (bevorzugt): Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="e9e27-192">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e9e27-193">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-193">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e9e27-194">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo yum update powershell` verwenden, um Updates für PowerShell auszuführen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-194">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e9e27-195">Installation über einen direkten Download: Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="e9e27-195">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e9e27-196">Laden Sie das RPM-Paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den Red Hat Enterprise Linux-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="e9e27-196">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="e9e27-197">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="e9e27-197">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e9e27-198">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="e9e27-198">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e9e27-199">Deinstallation: Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="e9e27-199">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="e9e27-200">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="e9e27-200">OpenSUSE 42.3</span></span>

<span data-ttu-id="e9e27-201">Bei der Installation von PowerShell Core verursacht `zypper` eventuell den folgenden Fehler:</span><span class="sxs-lookup"><span data-stu-id="e9e27-201">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="e9e27-202">Stellen Sie in diesem Fall sicher, dass eine kompatible `libcurl`-Bibliothek vorhanden ist, indem Sie überprüfen, ob der folgende Befehl das `libcurl4`-Paket als installiert anzeigt:</span><span class="sxs-lookup"><span data-stu-id="e9e27-202">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="e9e27-203">Wählen Sie bei der Installation des PowerShell-Pakets die Lösung `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` aus.</span><span class="sxs-lookup"><span data-stu-id="e9e27-203">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="e9e27-204">Installation über das Paketrepository (bevorzugt): openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="e9e27-204">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="e9e27-205">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-205">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="e9e27-206">Installation über einen direkten Download: openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="e9e27-206">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="e9e27-207">Laden Sie das RPM-Paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den OpenSUSE-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="e9e27-207">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e9e27-208">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="e9e27-208">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="e9e27-209">Deinstallation: openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="e9e27-209">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="e9e27-210">Fedora</span><span class="sxs-lookup"><span data-stu-id="e9e27-210">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="e9e27-211">Fedora 28 wird nur in PowerShell Core 6.1 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e9e27-211">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="e9e27-212">Installation über das Paketrepository (bevorzugt): Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e9e27-212">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="e9e27-213">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-213">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="e9e27-214">Installation über einen direkten Download: Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e9e27-214">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="e9e27-215">Laden Sie das RPM-Paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den Fedora-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="e9e27-215">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="e9e27-216">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="e9e27-216">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e9e27-217">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="e9e27-217">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="e9e27-218">Deinstallation: Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e9e27-218">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="e9e27-219">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="e9e27-219">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="e9e27-220">Die Unterstützung von Arch wird noch getestet.</span><span class="sxs-lookup"><span data-stu-id="e9e27-220">Arch support is experimental.</span></span>

<span data-ttu-id="e9e27-221">PowerShell ist über das Benutzerrepository [Arch Linux][] verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e9e27-221">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="e9e27-222">Es kann gemeinsam mit dem [zuletzt markierten Release][arch-release] installiert werden.</span><span class="sxs-lookup"><span data-stu-id="e9e27-222">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="e9e27-223">Es kann gemeinsam mit dem [letzten Commit für den Master][arch-git] kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="e9e27-223">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="e9e27-224">Es kann mithilfe der [zuletzt veröffentlichten Binärdatei][arch-bin] kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="e9e27-224">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="e9e27-225">Pakete im Benutzerrepository „Arch Linux“ werden von der Community verwaltet. Es gibt keinen offiziellen Support.</span><span class="sxs-lookup"><span data-stu-id="e9e27-225">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="e9e27-226">Weitere Informationen zum Installieren von Paketen aus dem Benutzerrepository „Arch Linux“ finden Sie im [Arch Linux-Wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) oder in [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) der Community.</span><span class="sxs-lookup"><span data-stu-id="e9e27-226">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="e9e27-228">Snap-Paket</span><span class="sxs-lookup"><span data-stu-id="e9e27-228">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="e9e27-229">Abrufen von snapd</span><span class="sxs-lookup"><span data-stu-id="e9e27-229">Getting snapd</span></span>

<span data-ttu-id="e9e27-230">`snapd` ist für das Ausführen von Snap-Paketen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="e9e27-230">`snapd` is required to run snaps.</span></span>  <span data-ttu-id="e9e27-231">Halten Sie sich an [diese Anweisungen](https://docs.snapcraft.io/core/install), um sicherzustellen, dass `snapd` installiert ist.</span><span class="sxs-lookup"><span data-stu-id="e9e27-231">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="e9e27-232">Installation über Snap</span><span class="sxs-lookup"><span data-stu-id="e9e27-232">Installation via Snap</span></span>

<span data-ttu-id="e9e27-233">PowerShell Core für Linux wird im [Snap-Store](https://snapcraft.io/store) veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-233">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="e9e27-234">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="e9e27-234">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="e9e27-235">Nach der Installation führt Snap automatisch ein Upgrade durch, Sie können jedoch ein Upgrade mithilfe von `sudo snap refresh powershell-preview` auslösen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-235">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="e9e27-236">Deinstallation</span><span class="sxs-lookup"><span data-stu-id="e9e27-236">Uninstallation</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="linux-appimage"></a><span data-ttu-id="e9e27-237">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="e9e27-237">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="e9e27-238">Die Unterstützung von AppImage wird noch getestet.</span><span class="sxs-lookup"><span data-stu-id="e9e27-238">AppImage support is experimental</span></span>

<span data-ttu-id="e9e27-239">Wenn Sie eine aktuelle Linux-Distribution verwenden, laden Sie AppImage `powershell-6.0.1-x86_64.AppImage` auf der Seite [Releases][] auf den Linux-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="e9e27-239">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="e9e27-240">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="e9e27-240">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="e9e27-241">Mithilfe von [AppImage][] können Sie PowerShell ohne Installation ausführen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-241">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="e9e27-242">Dabei handelt es sich um eine portierbare Anwendung, die PowerShell und dessen Abhängigkeiten in ein Paket bündelt (einschließlich der Systemabhängigkeiten von .NET Core).</span><span class="sxs-lookup"><span data-stu-id="e9e27-242">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="e9e27-243">Bei diesem Paket handelt es sich um eine einzelne Binärdatei, die unabhängig von der Linux-Distribution des Benutzers funktioniert.</span><span class="sxs-lookup"><span data-stu-id="e9e27-243">This package is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="e9e27-245">Kali</span><span class="sxs-lookup"><span data-stu-id="e9e27-245">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="e9e27-246">Die Unterstützung von Kali wird noch getestet.</span><span class="sxs-lookup"><span data-stu-id="e9e27-246">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="e9e27-247">Installation</span><span class="sxs-lookup"><span data-stu-id="e9e27-247">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="e9e27-248">Führen Sie PowerShell unter der neusten Kali-Version (Kali GNU/Linux Rolling) aus, ohne es zuvor zu installieren.</span><span class="sxs-lookup"><span data-stu-id="e9e27-248">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="e9e27-249">Deinstallation: Kali</span><span class="sxs-lookup"><span data-stu-id="e9e27-249">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="e9e27-250">Raspbian</span><span class="sxs-lookup"><span data-stu-id="e9e27-250">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="e9e27-251">Die Unterstützung von Raspbian wird noch getestet.</span><span class="sxs-lookup"><span data-stu-id="e9e27-251">Raspbian support is experimental.</span></span>

<span data-ttu-id="e9e27-252">Derzeit wird PowerShell nur unter Raspbian Stretch unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e9e27-252">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="e9e27-253">Außerdem funktioniert CoreCLR (und daher auch PowerShell Core) nur auf Geräten mit Pi 2 und Pi 3, da andere Geräte, wie z.B. [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), einen nicht unterstützten Prozessor haben.</span><span class="sxs-lookup"><span data-stu-id="e9e27-253">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="e9e27-254">Laden Sie [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) herunter, und folgen Sie den [Installationsanweisungen](https://www.raspberrypi.org/documentation/installation/installing-images/README.md), um es zu installieren.</span><span class="sxs-lookup"><span data-stu-id="e9e27-254">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="e9e27-255">Installation</span><span class="sxs-lookup"><span data-stu-id="e9e27-255">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.2-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="e9e27-256">Optional können Sie eine symbolische Verknüpfung erstellen, damit Sie PowerShell ohne Angabe eines Pfads auf die Binärdatei „pwsh“ starten können.</span><span class="sxs-lookup"><span data-stu-id="e9e27-256">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="e9e27-257">Deinstallation: Raspbian</span><span class="sxs-lookup"><span data-stu-id="e9e27-257">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="e9e27-258">Archive der Binärdateien</span><span class="sxs-lookup"><span data-stu-id="e9e27-258">Binary Archives</span></span>

<span data-ttu-id="e9e27-259">`tar.gz`-Archive der PowerShell-Binärdateien werden für Linux-Plattformen zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="e9e27-259">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="e9e27-260">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="e9e27-260">Dependencies</span></span>

<span data-ttu-id="e9e27-261">PowerShell erstellt portierbare Binärdateien für alle Linux-Distributionen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-261">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="e9e27-262">Allerdings erfordert die .NET Core-Laufzeit, und damit auch PowerShell, verschiedene Abhängigkeiten für die verschiedenen Distributionen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-262">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="e9e27-263">Im folgenden Diagramm werden die Abhängigkeiten von .NET Core 2.0 für die verschiedenen Linux-Distributionen dargestellt, die offiziell unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="e9e27-263">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="e9e27-264">Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="e9e27-264">OS</span></span>                 | <span data-ttu-id="e9e27-265">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="e9e27-265">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="e9e27-266">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e9e27-266">Ubuntu 14.04</span></span>       | <span data-ttu-id="e9e27-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e9e27-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e9e27-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e9e27-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e9e27-269">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e9e27-269">Ubuntu 16.04</span></span>       | <span data-ttu-id="e9e27-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e9e27-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e9e27-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="e9e27-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="e9e27-272">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e9e27-272">Ubuntu 17.10</span></span>       | <span data-ttu-id="e9e27-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e9e27-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e9e27-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="e9e27-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="e9e27-275">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e9e27-275">Ubuntu 18.04</span></span>       | <span data-ttu-id="e9e27-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e9e27-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e9e27-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="e9e27-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="e9e27-278">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="e9e27-278">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="e9e27-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e9e27-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e9e27-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e9e27-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e9e27-281">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="e9e27-281">Debian 9 (Stretch)</span></span> | <span data-ttu-id="e9e27-282">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e9e27-282">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e9e27-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="e9e27-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="e9e27-284">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e9e27-284">CentOS 7</span></span> <br> <span data-ttu-id="e9e27-285">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="e9e27-285">Oracle Linux 7</span></span> <br> <span data-ttu-id="e9e27-286">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="e9e27-286">RHEL 7</span></span> <br> <span data-ttu-id="e9e27-287">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="e9e27-287">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="e9e27-288">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="e9e27-288">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="e9e27-289">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="e9e27-289">Fedora 27</span></span> <br> <span data-ttu-id="e9e27-290">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e9e27-290">Fedora 28</span></span> | <span data-ttu-id="e9e27-291">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="e9e27-291">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="e9e27-292">Sie müssen zur Bereitstellung von PowerShell-Binärdateien für nicht offiziell unterstützte Linux-Distributionen die notwendigen Abhängigkeiten für das Zielbetriebssystem über zusätzliche Schritte installieren.</span><span class="sxs-lookup"><span data-stu-id="e9e27-292">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="e9e27-293">Beispielsweise installiert die [Amazon Linux-Dockerfile][amazon-dockerfile] zuerst die Abhängigkeiten und extrahiert anschließend erst das Linux-`tar.gz`-Archiv.</span><span class="sxs-lookup"><span data-stu-id="e9e27-293">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="e9e27-294">Installation: Archive von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="e9e27-294">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="e9e27-295">Linux</span><span class="sxs-lookup"><span data-stu-id="e9e27-295">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.2/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="e9e27-296">Deinstallation: Archive von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="e9e27-296">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="e9e27-297">Pfade</span><span class="sxs-lookup"><span data-stu-id="e9e27-297">Paths</span></span>

* <span data-ttu-id="e9e27-298">`$PSHOME` ist `/opt/microsoft/powershell/6.0.2/`.</span><span class="sxs-lookup"><span data-stu-id="e9e27-298">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="e9e27-299">Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-299">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="e9e27-300">Standardprofile werden über `$PSHOME/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-300">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="e9e27-301">Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-301">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e9e27-302">Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-302">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e9e27-303">Standardmodule werden über `$PSHOME/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="e9e27-303">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="e9e27-304">Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="e9e27-304">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="e9e27-305">Die Profile beachten die Konfigurationen von PowerShell pro Host. Das bedeutet, die hostspezifischen Standardprofile sind an denselben Orten unter `Microsoft.PowerShell_profile.ps1` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="e9e27-305">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="e9e27-306">PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter Linux ein.</span><span class="sxs-lookup"><span data-stu-id="e9e27-306">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Releases]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
