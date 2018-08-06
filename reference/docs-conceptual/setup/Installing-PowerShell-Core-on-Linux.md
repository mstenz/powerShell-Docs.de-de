# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="fdbf6-101">Installieren von PowerShell Core unter Linux</span><span class="sxs-lookup"><span data-stu-id="fdbf6-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="fdbf6-102">Unterstützt [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] und [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="fdbf6-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="fdbf6-103">Für nicht offiziell unterstützte Linux-Distributionen können Sie versuchen, [PowerShell AppImage][lai] zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="fdbf6-104">Stattdessen können Sie auch versuchen, PowerShell-Binärdateien über das [`tar.gz`-Archiv][tar] für Linux bereitzustellen. Dafür müssen Sie aber basierend auf Ihrem Betriebssystem die benötigten Abhängigkeiten in zusätzlichen Schritten einrichten.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="fdbf6-105">Sämtliche Pakete sind auf der Seite [Releases][] über GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="fdbf6-106">Führen Sie `pwsh` über das Terminal aus, nachdem Sie das Paket installiert haben.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[u18]: #ubuntu-1804
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="fdbf6-107">Installieren von Vorschauversionen</span><span class="sxs-lookup"><span data-stu-id="fdbf6-107">Installing Preview Releases</span></span>

<span data-ttu-id="fdbf6-108">Wenn eine Vorschauversion von PowerShell Core für Linux über ein Paketrepository installiert wird, ändert sich der Paketname von `powershell` in `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-108">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="fdbf6-109">Bei einer Installation über einen direkten Download wird nur der Dateiname geändert.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-109">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="fdbf6-110">In der nachfolgenden Tabelle werden die Befehle aufgeführt, über die Sie Pakete stabiler Versionen und von Vorschauversionen unter Verwendung der verschiedenen Paket-Manager installieren können:</span><span class="sxs-lookup"><span data-stu-id="fdbf6-110">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="fdbf6-111">Distribution(en)</span><span class="sxs-lookup"><span data-stu-id="fdbf6-111">Distribution(s)</span></span>|<span data-ttu-id="fdbf6-112">Befehl für die stabile Version</span><span class="sxs-lookup"><span data-stu-id="fdbf6-112">Stable Command</span></span> | <span data-ttu-id="fdbf6-113">Befehl für die Vorschauversion</span><span class="sxs-lookup"><span data-stu-id="fdbf6-113">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="fdbf6-114">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="fdbf6-114">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="fdbf6-115">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="fdbf6-115">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="fdbf6-116">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="fdbf6-116">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="fdbf6-117">Fedora</span><span class="sxs-lookup"><span data-stu-id="fdbf6-117">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="fdbf6-118">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="fdbf6-118">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="fdbf6-119">Installation über das Paketrepository: Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="fdbf6-119">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="fdbf6-120">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="fdbf6-121">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-121">This is the preferred method.</span></span>

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

<span data-ttu-id="fdbf6-122">Registrieren Sie das Microsoft-Repository als Superuser.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-122">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="fdbf6-123">Von nun an müssen Sie nur `sudo apt-get upgrade powershell` verwenden, um die Installation zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-123">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="fdbf6-124">Installation über einen direkten Download: Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="fdbf6-124">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="fdbf6-125">Laden Sie das Debian-Paket `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` über die Seite [Releases][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-125">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="fdbf6-126">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="fdbf6-126">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="fdbf6-127">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-127">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="fdbf6-128">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-128">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="fdbf6-129">Deinstallation: Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="fdbf6-129">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="fdbf6-130">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="fdbf6-130">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="fdbf6-131">Installation über das Paketrepository: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="fdbf6-131">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="fdbf6-132">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-132">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="fdbf6-133">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-133">This is the preferred method.</span></span>

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

<span data-ttu-id="fdbf6-134">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-134">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="fdbf6-135">Installation über einen direkten Download: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="fdbf6-135">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="fdbf6-136">Laden Sie das Debian-Paket `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` über die Seite [Releases][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-136">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="fdbf6-137">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="fdbf6-137">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="fdbf6-138">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-138">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="fdbf6-139">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-139">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="fdbf6-140">Deinstallation: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="fdbf6-140">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a><span data-ttu-id="fdbf6-141">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="fdbf6-141">Ubuntu 17.10</span></span>

> [!NOTE]
> <span data-ttu-id="fdbf6-142">Unterstützung für Ubuntu 17.04 wurde nach `6.1.0-preview.2` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-142">Support for Ubuntu 17.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1710"></a><span data-ttu-id="fdbf6-143">Installation über das Paketrepository: Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="fdbf6-143">Installation via Package Repository - Ubuntu 17.10</span></span>

<span data-ttu-id="fdbf6-144">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-144">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="fdbf6-145">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-145">This is the preferred method.</span></span>

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

<span data-ttu-id="fdbf6-146">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-146">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1710"></a><span data-ttu-id="fdbf6-147">Installation über einen direkten Download: Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="fdbf6-147">Installation via Direct Download - Ubuntu 17.10</span></span>

<span data-ttu-id="fdbf6-148">Laden Sie das Debian-Paket `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` über die Seite [Releases][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-148">Download the Debian package `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="fdbf6-149">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="fdbf6-149">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="fdbf6-150">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-150">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="fdbf6-151">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-151">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="fdbf6-152">Deinstallation: Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="fdbf6-152">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="fdbf6-153">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="fdbf6-153">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="fdbf6-154">Die Unterstützung für Ubuntu 18.04. wurde nach `6.1.0-preview.2` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-154">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="fdbf6-155">Installation über das Paketrepository: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="fdbf6-155">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="fdbf6-156">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-156">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="fdbf6-157">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-157">This is the preferred method.</span></span>

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

<span data-ttu-id="fdbf6-158">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-158">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="fdbf6-159">Installation über einen direkten Download: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="fdbf6-159">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="fdbf6-160">Laden Sie das Debian-Paket `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` über die Seite [Releases][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-160">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="fdbf6-161">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="fdbf6-161">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="fdbf6-162">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-162">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="fdbf6-163">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-163">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="fdbf6-164">Deinstallation: Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="fdbf6-164">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="fdbf6-165">Debian 8</span><span class="sxs-lookup"><span data-stu-id="fdbf6-165">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="fdbf6-166">Installation über das Paketrepository: Debian 8</span><span class="sxs-lookup"><span data-stu-id="fdbf6-166">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="fdbf6-167">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="fdbf6-168">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-168">This is the preferred method.</span></span>

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

<span data-ttu-id="fdbf6-169">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="fdbf6-170">Installation über einen direkten Download: Debian 8</span><span class="sxs-lookup"><span data-stu-id="fdbf6-170">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="fdbf6-171">Laden Sie das Debian-Paket `powershell_6.0.2-1.debian.8_amd64.deb` über die Seite [Releases][] auf den Debian-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-171">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="fdbf6-172">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="fdbf6-172">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="fdbf6-173">Der `dpkg -i`-Befehl schlägt mit nicht erfüllten Abhängigkeiten fehl.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-173">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="fdbf6-174">Über den Befehl `apt-get install -f` werden diese Probleme behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-174">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="fdbf6-175">Deinstallation: Debian 8</span><span class="sxs-lookup"><span data-stu-id="fdbf6-175">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="fdbf6-176">Debian 9</span><span class="sxs-lookup"><span data-stu-id="fdbf6-176">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="fdbf6-177">Installation über das Paketrepository: Debian 9</span><span class="sxs-lookup"><span data-stu-id="fdbf6-177">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="fdbf6-178">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-178">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="fdbf6-179">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-179">This is the preferred method.</span></span>

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

<span data-ttu-id="fdbf6-180">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-180">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="fdbf6-181">Installation über einen direkten Download: Debian 9</span><span class="sxs-lookup"><span data-stu-id="fdbf6-181">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="fdbf6-182">Laden Sie das Debian-Paket `powershell_6.0.2-1.debian.9_amd64.deb` über die Seite [Releases][] auf den Debian-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-182">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="fdbf6-183">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="fdbf6-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="fdbf6-184">Deinstallation: Debian 9</span><span class="sxs-lookup"><span data-stu-id="fdbf6-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="fdbf6-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="fdbf6-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="fdbf6-186">Dieses Paket funktioniert ebenfalls unter Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="fdbf6-187">Installation über das Paketrepository (bevorzugt): CentOS 7</span><span class="sxs-lookup"><span data-stu-id="fdbf6-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="fdbf6-188">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="fdbf6-189">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo yum update powershell` verwenden, um Updates für PowerShell auszuführen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="fdbf6-190">Installation über einen direkten Download: CentOS 7</span><span class="sxs-lookup"><span data-stu-id="fdbf6-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="fdbf6-191">Für [CentOS 7][]: Laden Sie das RPM-Paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den CentOS-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-191">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="fdbf6-192">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="fdbf6-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="fdbf6-193">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="fdbf6-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="fdbf6-194">Deinstallation: CentOS 7</span><span class="sxs-lookup"><span data-stu-id="fdbf6-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="fdbf6-196">Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="fdbf6-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="fdbf6-197">Installation über ein Paketrepository (bevorzugt): Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="fdbf6-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="fdbf6-198">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="fdbf6-199">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo yum update powershell` verwenden, um Updates für PowerShell auszuführen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="fdbf6-200">Installation über einen direkten Download: Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="fdbf6-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="fdbf6-201">Laden Sie das RPM-Paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den Red Hat Enterprise Linux-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-201">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="fdbf6-202">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="fdbf6-202">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="fdbf6-203">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="fdbf6-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="fdbf6-204">Deinstallation: Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="fdbf6-204">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="fdbf6-205">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="fdbf6-205">OpenSUSE 42.3</span></span>

<span data-ttu-id="fdbf6-206">Bei der Installation von PowerShell Core verursacht `zypper` eventuell den folgenden Fehler:</span><span class="sxs-lookup"><span data-stu-id="fdbf6-206">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="fdbf6-207">Stellen Sie in diesem Fall sicher, dass eine kompatible `libcurl`-Bibliothek vorhanden ist, indem Sie überprüfen, ob der folgende Befehl das `libcurl4`-Paket als installiert anzeigt:</span><span class="sxs-lookup"><span data-stu-id="fdbf6-207">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="fdbf6-208">Wählen Sie bei der Installation des PowerShell-Pakets die Lösung `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` aus.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-208">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="fdbf6-209">Installation über das Paketrepository (bevorzugt): openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="fdbf6-209">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="fdbf6-210">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-210">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="fdbf6-211">Installation über einen direkten Download: openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="fdbf6-211">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="fdbf6-212">Laden Sie das RPM-Paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den OpenSUSE-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-212">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="fdbf6-213">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="fdbf6-213">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="fdbf6-214">Deinstallation: openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="fdbf6-214">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="fdbf6-215">Fedora</span><span class="sxs-lookup"><span data-stu-id="fdbf6-215">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="fdbf6-216">Fedora 28 wird nur in PowerShell Core 6.1 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-216">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="fdbf6-217">Installation über das Paketrepository (bevorzugt): Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="fdbf6-217">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="fdbf6-218">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-218">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="fdbf6-219">Installation über einen direkten Download: Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="fdbf6-219">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="fdbf6-220">Laden Sie das RPM-Paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den Fedora-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-220">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="fdbf6-221">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="fdbf6-221">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="fdbf6-222">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="fdbf6-222">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="fdbf6-223">Deinstallation: Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="fdbf6-223">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="fdbf6-224">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="fdbf6-224">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="fdbf6-225">Die Unterstützung von Arch wird noch getestet.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-225">Arch support is experimental.</span></span>

<span data-ttu-id="fdbf6-226">PowerShell ist über das Benutzerrepository [Arch Linux][] verfügbar.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-226">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="fdbf6-227">Es kann gemeinsam mit dem [zuletzt markierten Release][arch-release] installiert werden.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-227">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="fdbf6-228">Es kann gemeinsam mit dem [letzten Commit für den Master][arch-git] kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-228">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="fdbf6-229">Es kann mithilfe der [zuletzt veröffentlichten Binärdatei][arch-bin] kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-229">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="fdbf6-230">Pakete im Benutzerrepository „Arch Linux“ werden von der Community verwaltet. Es gibt keinen offiziellen Support.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-230">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="fdbf6-231">Weitere Informationen zum Installieren von Paketen aus dem Benutzerrepository „Arch Linux“ finden Sie im [Arch Linux-Wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) oder in [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) der Community.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-231">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="fdbf6-233">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="fdbf6-233">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="fdbf6-234">Die Unterstützung von AppImage wird noch getestet.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-234">AppImage support is experimental</span></span>

<span data-ttu-id="fdbf6-235">Wenn Sie eine aktuelle Linux-Distribution verwenden, laden Sie AppImage `powershell-6.0.1-x86_64.AppImage` auf der Seite [Releases][] auf den Linux-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-235">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="fdbf6-236">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="fdbf6-236">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="fdbf6-237">Mithilfe von [AppImage][] können Sie PowerShell ohne Installation ausführen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-237">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="fdbf6-238">Dabei handelt es sich um eine portierbare Anwendung, die PowerShell und dessen Abhängigkeiten in ein Paket bündelt (einschließlich der Systemabhängigkeiten von .NET Core).</span><span class="sxs-lookup"><span data-stu-id="fdbf6-238">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="fdbf6-239">Bei diesem Paket handelt es sich um eine einzelne Binärdatei, die unabhängig von der Linux-Distribution des Benutzers funktioniert.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-239">This package is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="fdbf6-241">Kali</span><span class="sxs-lookup"><span data-stu-id="fdbf6-241">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="fdbf6-242">Die Unterstützung von Kali wird noch getestet.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-242">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="fdbf6-243">Installation</span><span class="sxs-lookup"><span data-stu-id="fdbf6-243">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="fdbf6-244">Führen Sie PowerShell unter der neusten Kali-Version (Kali GNU/Linux Rolling) aus, ohne es zuvor zu installieren.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-244">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="fdbf6-245">Deinstallation: Kali</span><span class="sxs-lookup"><span data-stu-id="fdbf6-245">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="fdbf6-246">Raspbian</span><span class="sxs-lookup"><span data-stu-id="fdbf6-246">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="fdbf6-247">Die Unterstützung von Raspbian wird noch getestet.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-247">Raspbian support is experimental.</span></span>

<span data-ttu-id="fdbf6-248">Derzeit wird PowerShell nur unter Raspbian Stretch unterstützt.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-248">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="fdbf6-249">Außerdem funktioniert CoreCLR (und daher auch PowerShell Core) nur auf Geräten mit Pi 2 und Pi 3, da andere Geräte, wie z.B. [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), einen nicht unterstützten Prozessor haben.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-249">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="fdbf6-250">Laden Sie [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) herunter, und folgen Sie den [Installationsanweisungen](https://www.raspberrypi.org/documentation/installation/installing-images/README.md), um es zu installieren.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-250">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="fdbf6-251">Installation</span><span class="sxs-lookup"><span data-stu-id="fdbf6-251">Installation</span></span>

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

<span data-ttu-id="fdbf6-252">Optional können Sie eine symbolische Verknüpfung erstellen, damit Sie PowerShell ohne Angabe eines Pfads auf die Binärdatei „pwsh“ starten können.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-252">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="fdbf6-253">Deinstallation: Raspbian</span><span class="sxs-lookup"><span data-stu-id="fdbf6-253">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="fdbf6-254">Archive der Binärdateien</span><span class="sxs-lookup"><span data-stu-id="fdbf6-254">Binary Archives</span></span>

<span data-ttu-id="fdbf6-255">`tar.gz`-Archive der PowerShell-Binärdateien werden für Linux-Plattformen zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-255">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="fdbf6-256">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="fdbf6-256">Dependencies</span></span>

<span data-ttu-id="fdbf6-257">PowerShell erstellt portierbare Binärdateien für alle Linux-Distributionen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-257">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="fdbf6-258">Allerdings erfordert die .NET Core-Laufzeit, und damit auch PowerShell, verschiedene Abhängigkeiten für die verschiedenen Distributionen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-258">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="fdbf6-259">Im folgenden Diagramm werden die Abhängigkeiten von .NET Core 2.0 für die verschiedenen Linux-Distributionen dargestellt, die offiziell unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-259">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="fdbf6-260">Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="fdbf6-260">OS</span></span>                 | <span data-ttu-id="fdbf6-261">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="fdbf6-261">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="fdbf6-262">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="fdbf6-262">Ubuntu 14.04</span></span>       | <span data-ttu-id="fdbf6-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="fdbf6-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="fdbf6-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="fdbf6-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="fdbf6-265">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="fdbf6-265">Ubuntu 16.04</span></span>       | <span data-ttu-id="fdbf6-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="fdbf6-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="fdbf6-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="fdbf6-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="fdbf6-268">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="fdbf6-268">Ubuntu 17.10</span></span>       | <span data-ttu-id="fdbf6-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="fdbf6-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="fdbf6-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="fdbf6-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="fdbf6-271">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="fdbf6-271">Ubuntu 18.04</span></span>       | <span data-ttu-id="fdbf6-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="fdbf6-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="fdbf6-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="fdbf6-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="fdbf6-274">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="fdbf6-274">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="fdbf6-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="fdbf6-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="fdbf6-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="fdbf6-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="fdbf6-277">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="fdbf6-277">Debian 9 (Stretch)</span></span> | <span data-ttu-id="fdbf6-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="fdbf6-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="fdbf6-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="fdbf6-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="fdbf6-280">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="fdbf6-280">CentOS 7</span></span> <br> <span data-ttu-id="fdbf6-281">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="fdbf6-281">Oracle Linux 7</span></span> <br> <span data-ttu-id="fdbf6-282">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="fdbf6-282">RHEL 7</span></span> <br> <span data-ttu-id="fdbf6-283">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="fdbf6-283">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="fdbf6-284">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="fdbf6-284">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="fdbf6-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="fdbf6-285">Fedora 27</span></span> <br> <span data-ttu-id="fdbf6-286">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="fdbf6-286">Fedora 28</span></span> | <span data-ttu-id="fdbf6-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="fdbf6-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="fdbf6-288">Sie müssen zur Bereitstellung von PowerShell-Binärdateien für nicht offiziell unterstützte Linux-Distributionen die notwendigen Abhängigkeiten für das Zielbetriebssystem über zusätzliche Schritte installieren.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="fdbf6-289">Beispielsweise installiert die [Amazon Linux-Dockerfile][amazon-dockerfile] zuerst die Abhängigkeiten und extrahiert anschließend erst das Linux-`tar.gz`-Archiv.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="fdbf6-290">Installation: Archive von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="fdbf6-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="fdbf6-291">Linux</span><span class="sxs-lookup"><span data-stu-id="fdbf6-291">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="fdbf6-292">Deinstallation: Archive von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="fdbf6-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="fdbf6-293">Pfade</span><span class="sxs-lookup"><span data-stu-id="fdbf6-293">Paths</span></span>

* <span data-ttu-id="fdbf6-294">`$PSHOME` ist `/opt/microsoft/powershell/6.0.2/`.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-294">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="fdbf6-295">Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="fdbf6-296">Standardprofile werden über `$PSHOME/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="fdbf6-297">Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="fdbf6-298">Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="fdbf6-299">Standardmodule werden über `$PSHOME/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="fdbf6-300">Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="fdbf6-301">Die Profile beachten die Konfigurationen von PowerShell pro Host. Das bedeutet, die hostspezifischen Standardprofile sind an denselben Orten unter `Microsoft.PowerShell_profile.ps1` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="fdbf6-302">PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter Linux ein.</span><span class="sxs-lookup"><span data-stu-id="fdbf6-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Releases]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
