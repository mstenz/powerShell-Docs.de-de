# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="c89f9-101">Installieren von PowerShell Core unter Linux</span><span class="sxs-lookup"><span data-stu-id="c89f9-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="c89f9-102">Unterstützt [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] und [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="c89f9-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="c89f9-103">Für nicht offiziell unterstützte Linux-Distributionen können Sie versuchen, [PowerShell AppImage][lai] zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="c89f9-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="c89f9-104">Stattdessen können Sie auch versuchen, PowerShell-Binärdateien über das [`tar.gz`-Archiv][tar] für Linux bereitzustellen. Dafür müssen Sie aber basierend auf Ihrem Betriebssystem die benötigten Abhängigkeiten in zusätzlichen Schritten einrichten.</span><span class="sxs-lookup"><span data-stu-id="c89f9-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="c89f9-105">Sämtliche Pakete sind auf der Seite [Releases][] über GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c89f9-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="c89f9-106">Führen Sie `pwsh` über das Terminal aus, nachdem Sie das Paket installiert haben.</span><span class="sxs-lookup"><span data-stu-id="c89f9-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="c89f9-107">Installieren von Vorschauversionen</span><span class="sxs-lookup"><span data-stu-id="c89f9-107">Installing Preview Releases</span></span>

<span data-ttu-id="c89f9-108">Wenn eine Vorschauversion von PowerShell Core für Linux über ein Paketrepository installiert wird, ändert sich der Paketname von `powershell` in `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="c89f9-108">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="c89f9-109">Bei einer Installation über einen direkten Download wird nur der Dateiname geändert.</span><span class="sxs-lookup"><span data-stu-id="c89f9-109">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="c89f9-110">In der nachfolgenden Tabelle werden die Befehle aufgeführt, über die Sie Pakete stabiler Versionen und von Vorschauversionen unter Verwendung der verschiedenen Paket-Manager installieren können:</span><span class="sxs-lookup"><span data-stu-id="c89f9-110">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="c89f9-111">Verteilung(en)</span><span class="sxs-lookup"><span data-stu-id="c89f9-111">Distrobution(s)</span></span>|<span data-ttu-id="c89f9-112">Befehl für die stabile Version</span><span class="sxs-lookup"><span data-stu-id="c89f9-112">Stable Command</span></span> | <span data-ttu-id="c89f9-113">Befehl für die Vorschauversion</span><span class="sxs-lookup"><span data-stu-id="c89f9-113">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="c89f9-114">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="c89f9-114">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="c89f9-115">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="c89f9-115">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="c89f9-116">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="c89f9-116">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="c89f9-117">Fedora</span><span class="sxs-lookup"><span data-stu-id="c89f9-117">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="c89f9-118">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c89f9-118">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="c89f9-119">Installation über das Paketrepository: Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c89f9-119">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="c89f9-120">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c89f9-121">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="c89f9-121">This is the preferred method.</span></span>

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

<span data-ttu-id="c89f9-122">Registrieren Sie das Microsoft-Repository als Superuser.</span><span class="sxs-lookup"><span data-stu-id="c89f9-122">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="c89f9-123">Von nun an müssen Sie nur `sudo apt-get upgrade powershell` verwenden, um die Installation zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="c89f9-123">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="c89f9-124">Installation über einen direkten Download: Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c89f9-124">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="c89f9-125">Laden Sie das Debian-Paket `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` über die Seite [Releases][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="c89f9-125">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c89f9-126">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="c89f9-126">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c89f9-127">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="c89f9-127">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c89f9-128">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-128">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="c89f9-129">Deinstallation: Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c89f9-129">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="c89f9-130">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c89f9-130">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="c89f9-131">Installation über das Paketrepository: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c89f9-131">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="c89f9-132">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-132">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c89f9-133">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="c89f9-133">This is the preferred method.</span></span>

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

<span data-ttu-id="c89f9-134">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="c89f9-134">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="c89f9-135">Installation über einen direkten Download: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c89f9-135">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="c89f9-136">Laden Sie das Debian-Paket `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` über die Seite [Releases][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="c89f9-136">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c89f9-137">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="c89f9-137">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c89f9-138">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="c89f9-138">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c89f9-139">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-139">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="c89f9-140">Deinstallation: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c89f9-140">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a><span data-ttu-id="c89f9-141">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="c89f9-141">Ubuntu 17.10</span></span>

> [!NOTE]
> <span data-ttu-id="c89f9-142">Unterstützung für Ubuntu 17.04 wurde nach `6.1.0-preview.2` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="c89f9-142">Support for Ubuntu 17.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1710"></a><span data-ttu-id="c89f9-143">Installation über das Paketrepository: Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="c89f9-143">Installation via Package Repository - Ubuntu 17.10</span></span>

<span data-ttu-id="c89f9-144">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-144">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c89f9-145">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="c89f9-145">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.10/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c89f9-146">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="c89f9-146">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1710"></a><span data-ttu-id="c89f9-147">Installation über einen direkten Download: Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="c89f9-147">Installation via Direct Download - Ubuntu 17.10</span></span>

<span data-ttu-id="c89f9-148">Laden Sie das Debian-Paket `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` über die Seite [Releases][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="c89f9-148">Download the Debian package `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c89f9-149">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="c89f9-149">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c89f9-150">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="c89f9-150">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c89f9-151">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-151">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="c89f9-152">Deinstallation: Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="c89f9-152">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="c89f9-153">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c89f9-153">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="c89f9-154">Die Unterstützung für Ubuntu 18.04. wurde nach `6.1.0-preview.2` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="c89f9-154">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="c89f9-155">Installation über das Paketrepository: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c89f9-155">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="c89f9-156">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-156">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c89f9-157">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="c89f9-157">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c89f9-158">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="c89f9-158">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="c89f9-159">Installation über einen direkten Download: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c89f9-159">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="c89f9-160">Laden Sie das Debian-Paket `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` über die Seite [Releases][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="c89f9-160">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c89f9-161">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="c89f9-161">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c89f9-162">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="c89f9-162">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c89f9-163">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-163">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="c89f9-164">Deinstallation: Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="c89f9-164">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="c89f9-165">Debian 8</span><span class="sxs-lookup"><span data-stu-id="c89f9-165">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="c89f9-166">Installation über das Paketrepository: Debian 8</span><span class="sxs-lookup"><span data-stu-id="c89f9-166">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="c89f9-167">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c89f9-168">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="c89f9-168">This is the preferred method.</span></span>

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

<span data-ttu-id="c89f9-169">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="c89f9-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="c89f9-170">Installation über einen direkten Download: Debian 8</span><span class="sxs-lookup"><span data-stu-id="c89f9-170">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="c89f9-171">Laden Sie das Debian-Paket `powershell_6.0.2-1.debian.8_amd64.deb` über die Seite [Releases][] auf den Debian-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="c89f9-171">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="c89f9-172">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="c89f9-172">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c89f9-173">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="c89f9-173">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c89f9-174">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-174">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="c89f9-175">Deinstallation: Debian 8</span><span class="sxs-lookup"><span data-stu-id="c89f9-175">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="c89f9-176">Debian 9</span><span class="sxs-lookup"><span data-stu-id="c89f9-176">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="c89f9-177">Installation über das Paketrepository: Debian 9</span><span class="sxs-lookup"><span data-stu-id="c89f9-177">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="c89f9-178">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-178">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c89f9-179">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="c89f9-179">This is the preferred method.</span></span>

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

<span data-ttu-id="c89f9-180">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="c89f9-180">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="c89f9-181">Installation über einen direkten Download: Debian 9</span><span class="sxs-lookup"><span data-stu-id="c89f9-181">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="c89f9-182">Laden Sie das Debian-Paket `powershell_6.0.2-1.debian.9_amd64.deb` über die Seite [Releases][] auf den Debian-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="c89f9-182">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="c89f9-183">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="c89f9-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="c89f9-184">Deinstallation: Debian 9</span><span class="sxs-lookup"><span data-stu-id="c89f9-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="c89f9-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c89f9-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="c89f9-186">Dieses Paket funktioniert ebenfalls unter Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="c89f9-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="c89f9-187">Installation über das Paketrepository (bevorzugt): CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c89f9-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="c89f9-188">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c89f9-189">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo yum update powershell` verwenden, um Updates für PowerShell auszuführen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="c89f9-190">Installation über einen direkten Download: CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c89f9-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="c89f9-191">Für [CentOS 7][]: Laden Sie das RPM-Paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den CentOS-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="c89f9-191">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="c89f9-192">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="c89f9-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c89f9-193">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="c89f9-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="c89f9-194">Deinstallation: CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c89f9-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c89f9-196">Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="c89f9-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c89f9-197">Installation über ein Paketrepository (bevorzugt): Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="c89f9-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="c89f9-198">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c89f9-199">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo yum update powershell` verwenden, um Updates für PowerShell auszuführen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c89f9-200">Installation über einen direkten Download: Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="c89f9-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="c89f9-201">Laden Sie das RPM-Paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den Red Hat Enterprise Linux-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="c89f9-201">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="c89f9-202">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="c89f9-202">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c89f9-203">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="c89f9-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c89f9-204">Deinstallation: Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="c89f9-204">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="c89f9-205">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="c89f9-205">OpenSUSE 42.2</span></span>

<span data-ttu-id="c89f9-206">Bei der Installation von PowerShell Core verursacht `zypper` eventuell den folgenden Fehler:</span><span class="sxs-lookup"><span data-stu-id="c89f9-206">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="c89f9-207">Stellen Sie in diesem Fall sicher, dass eine kompatible `libcurl`-Bibliothek vorhanden ist, indem Sie überprüfen, ob der folgende Befehl das `libcurl4`-Paket als installiert anzeigt:</span><span class="sxs-lookup"><span data-stu-id="c89f9-207">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="c89f9-208">Wählen Sie bei der Installation des PowerShell-Pakets die Lösung `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` aus.</span><span class="sxs-lookup"><span data-stu-id="c89f9-208">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="c89f9-209">Installation über das Paketrepository (bevorzugt): OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="c89f9-209">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="c89f9-210">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-210">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="c89f9-211">Installation über einen direkten Download: OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="c89f9-211">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="c89f9-212">Laden Sie das RPM-Paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den OpenSUSE-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="c89f9-212">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c89f9-213">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="c89f9-213">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="c89f9-214">Deinstallation. OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="c89f9-214">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="c89f9-215">Fedora</span><span class="sxs-lookup"><span data-stu-id="c89f9-215">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="c89f9-216">Fedora 28 wird nur in PowerShell Core 6.1 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c89f9-216">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="c89f9-217">Installation über das Paketrepository (bevorzugt): Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c89f9-217">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="c89f9-218">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-218">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="c89f9-219">Installation über einen direkten Download: Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c89f9-219">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="c89f9-220">Laden Sie das RPM-Paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den Fedora-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="c89f9-220">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="c89f9-221">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="c89f9-221">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c89f9-222">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="c89f9-222">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="c89f9-223">Deinstallation: Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c89f9-223">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="c89f9-224">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="c89f9-224">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="c89f9-225">Die Unterstützung von Arch wird noch getestet.</span><span class="sxs-lookup"><span data-stu-id="c89f9-225">Arch support is experimental.</span></span>

<span data-ttu-id="c89f9-226">PowerShell ist über das Benutzerrepository [Arch Linux][] verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c89f9-226">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="c89f9-227">Es kann gemeinsam mit dem [zuletzt markierten Release][arch-release] installiert werden.</span><span class="sxs-lookup"><span data-stu-id="c89f9-227">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="c89f9-228">Es kann gemeinsam mit dem [letzten Commit für den Master][arch-git] kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="c89f9-228">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="c89f9-229">Es kann mithilfe der [zuletzt veröffentlichten Binärdatei][arch-bin] kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="c89f9-229">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="c89f9-230">Pakete im Benutzerrepository „Arch Linux“ werden von der Community verwaltet. Es gibt keinen offiziellen Support.</span><span class="sxs-lookup"><span data-stu-id="c89f9-230">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="c89f9-231">Weitere Informationen zum Installieren von Paketen aus dem Benutzerrepository „Arch Linux“ finden Sie im [Arch Linux-Wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) oder in [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) der Community.</span><span class="sxs-lookup"><span data-stu-id="c89f9-231">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="c89f9-233">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="c89f9-233">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="c89f9-234">Die Unterstützung von AppImage wird noch getestet.</span><span class="sxs-lookup"><span data-stu-id="c89f9-234">AppImage support is experimental</span></span>

<span data-ttu-id="c89f9-235">Wenn Sie eine aktuelle Linux-Distribution verwenden, laden Sie AppImage `powershell-6.0.1-x86_64.AppImage` auf der Seite [Releases][] auf den Linux-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="c89f9-235">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="c89f9-236">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="c89f9-236">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="c89f9-237">Mithilfe von [AppImage][] können Sie PowerShell ohne Installation ausführen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-237">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="c89f9-238">Dabei handelt es sich um eine portierbare Anwendung, die PowerShell und dessen Abhängigkeiten in ein Paket bündelt (einschließlich der Systemabhängigkeiten von .NET Core).</span><span class="sxs-lookup"><span data-stu-id="c89f9-238">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="c89f9-239">Dieses Paket funktioniert unabhängig von der Linux-Distribution des Benutzers. Außerdem handelt es sich dabei um eine einzelne Binärdatei.</span><span class="sxs-lookup"><span data-stu-id="c89f9-239">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="c89f9-241">Kali</span><span class="sxs-lookup"><span data-stu-id="c89f9-241">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="c89f9-242">Die Unterstützung von Kali wird noch getestet.</span><span class="sxs-lookup"><span data-stu-id="c89f9-242">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="c89f9-243">Installation</span><span class="sxs-lookup"><span data-stu-id="c89f9-243">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="c89f9-244">Führen Sie PowerShell unter der neusten Kali-Version (Kali GNU/Linux Rolling) aus, ohne es zuvor zu installieren.</span><span class="sxs-lookup"><span data-stu-id="c89f9-244">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="c89f9-245">Deinstallation: Kali</span><span class="sxs-lookup"><span data-stu-id="c89f9-245">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="c89f9-246">Raspbian</span><span class="sxs-lookup"><span data-stu-id="c89f9-246">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="c89f9-247">Die Unterstützung von Raspbian wird noch getestet.</span><span class="sxs-lookup"><span data-stu-id="c89f9-247">Raspbian support is experimental.</span></span>

<span data-ttu-id="c89f9-248">Derzeit wird PowerShell nur unter Raspbian Stretch unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c89f9-248">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="c89f9-249">Außerdem funktioniert CoreCLR (und daher auch PowerShell Core) nur auf Geräten mit Pi 2 und Pi 3, da andere Geräte, wie z.B. [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), einen nicht unterstützten Prozessor haben.</span><span class="sxs-lookup"><span data-stu-id="c89f9-249">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="c89f9-250">Laden Sie [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) herunter, und folgen Sie den [Installationsanweisungen](https://www.raspberrypi.org/documentation/installation/installing-images/README.md), um es zu installieren.</span><span class="sxs-lookup"><span data-stu-id="c89f9-250">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="c89f9-251">Installation</span><span class="sxs-lookup"><span data-stu-id="c89f9-251">Installation</span></span>

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

<span data-ttu-id="c89f9-252">Optional können Sie eine symbolische Verknüpfung erstellen, damit Sie PowerShell ohne Angabe eines Pfads auf die Binärdatei „pwsh“ starten können.</span><span class="sxs-lookup"><span data-stu-id="c89f9-252">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="c89f9-253">Deinstallation: Raspbian</span><span class="sxs-lookup"><span data-stu-id="c89f9-253">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="c89f9-254">Archive der Binärdateien</span><span class="sxs-lookup"><span data-stu-id="c89f9-254">Binary Archives</span></span>

<span data-ttu-id="c89f9-255">`tar.gz`-Archive der PowerShell-Binärdateien werden für Linux-Plattformen zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="c89f9-255">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="c89f9-256">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="c89f9-256">Dependencies</span></span>

<span data-ttu-id="c89f9-257">PowerShell erstellt portierbare Binärdateien für alle Linux-Distributionen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-257">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="c89f9-258">Allerdings erfordert die .NET Core-Laufzeit, und damit auch PowerShell, verschiedene Abhängigkeiten für die verschiedenen Distributionen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-258">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="c89f9-259">Im folgenden Diagramm werden die Abhängigkeiten von .NET Core 2.0 für die verschiedenen Linux-Distributionen dargestellt, die offiziell unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="c89f9-259">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="c89f9-260">Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="c89f9-260">OS</span></span>                 | <span data-ttu-id="c89f9-261">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="c89f9-261">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="c89f9-262">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c89f9-262">Ubuntu 14.04</span></span>       | <span data-ttu-id="c89f9-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="c89f9-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c89f9-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="c89f9-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="c89f9-265">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c89f9-265">Ubuntu 16.04</span></span>       | <span data-ttu-id="c89f9-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="c89f9-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c89f9-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="c89f9-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="c89f9-268">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="c89f9-268">Ubuntu 17.10</span></span>       | <span data-ttu-id="c89f9-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="c89f9-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c89f9-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="c89f9-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="c89f9-271">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c89f9-271">Ubuntu 18.04</span></span>       | <span data-ttu-id="c89f9-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="c89f9-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c89f9-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="c89f9-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="c89f9-274">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="c89f9-274">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="c89f9-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="c89f9-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c89f9-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="c89f9-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="c89f9-277">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="c89f9-277">Debian 9 (Stretch)</span></span> | <span data-ttu-id="c89f9-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="c89f9-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c89f9-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="c89f9-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="c89f9-280">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c89f9-280">CentOS 7</span></span> <br> <span data-ttu-id="c89f9-281">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="c89f9-281">Oracle Linux 7</span></span> <br> <span data-ttu-id="c89f9-282">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="c89f9-282">RHEL 7</span></span> <br> <span data-ttu-id="c89f9-283">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="c89f9-283">OpenSUSE 42.2</span></span> | <span data-ttu-id="c89f9-284">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="c89f9-284">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="c89f9-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="c89f9-285">Fedora 27</span></span> <br> <span data-ttu-id="c89f9-286">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c89f9-286">Fedora 28</span></span> | <span data-ttu-id="c89f9-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="c89f9-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="c89f9-288">Sie müssen zur Bereitstellung von PowerShell-Binärdateien für nicht offiziell unterstützte Linux-Distributionen die notwendigen Abhängigkeiten für das Zielbetriebssystem über zusätzliche Schritte installieren.</span><span class="sxs-lookup"><span data-stu-id="c89f9-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="c89f9-289">Beispielsweise installiert die [Amazon Linux-Dockerfile][amazon-dockerfile] zuerst die Abhängigkeiten und extrahiert anschließend erst das Linux-`tar.gz`-Archiv.</span><span class="sxs-lookup"><span data-stu-id="c89f9-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="c89f9-290">Installation: Archive von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="c89f9-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="c89f9-291">Linux</span><span class="sxs-lookup"><span data-stu-id="c89f9-291">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="c89f9-292">Deinstallation: Archive von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="c89f9-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="c89f9-293">Pfade</span><span class="sxs-lookup"><span data-stu-id="c89f9-293">Paths</span></span>

* <span data-ttu-id="c89f9-294">`$PSHOME` ist `/opt/microsoft/powershell/6.0.2/`.</span><span class="sxs-lookup"><span data-stu-id="c89f9-294">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="c89f9-295">Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="c89f9-296">Standardprofile werden über `$PSHOME/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="c89f9-297">Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="c89f9-298">Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="c89f9-299">Standardmodule werden über `$PSHOME/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="c89f9-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="c89f9-300">Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="c89f9-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="c89f9-301">Die Profile beachten die Konfigurationen von PowerShell pro Host. Das bedeutet, die hostspezifischen Standardprofile sind an denselben Orten unter `Microsoft.PowerShell_profile.ps1` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="c89f9-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="c89f9-302">PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter Linux ein.</span><span class="sxs-lookup"><span data-stu-id="c89f9-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Releases]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
