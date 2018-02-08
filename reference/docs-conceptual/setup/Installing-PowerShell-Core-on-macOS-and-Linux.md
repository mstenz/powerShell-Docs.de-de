# <a name="installing-powershell-core-on-macos-and-linux"></a><span data-ttu-id="7ecde-101">Installieren von PowerShell Core unter macOS und Linux</span><span class="sxs-lookup"><span data-stu-id="7ecde-101">Installing PowerShell Core on macOS and Linux</span></span>

<span data-ttu-id="7ecde-102">Unterstützt [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch] und [macOS 10.12][mac].</span><span class="sxs-lookup"><span data-stu-id="7ecde-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch], and [macOS 10.12][mac].</span></span>

<span data-ttu-id="7ecde-103">Für nicht offiziell unterstützte Linux-Distributionen können Sie versuchen, [PowerShell AppImage][lai] zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="7ecde-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span> <span data-ttu-id="7ecde-104">Stattdessen können Sie auch versuchen, PowerShell-Binärdateien über das [`tar.gz`-Archiv][tar] für Linux bereitzustellen. Dafür müssen Sie aber basierend auf Ihrem Betriebssystem die benötigten Abhängigkeiten in zusätzlichen Schritten einrichten.</span><span class="sxs-lookup"><span data-stu-id="7ecde-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="7ecde-105">Sämtliche Pakete sind auf der Seite [Releases][] über GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="7ecde-105">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="7ecde-106">Führen Sie `pwsh` über das Terminal aus, nachdem Sie das Paket installiert haben.</span><span class="sxs-lookup"><span data-stu-id="7ecde-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fed25]: #fedora-25
[fed26]: #fedora-26
[arch]: #arch-linux
[lai]: #linux-appimage
[mac]: #macos-1012
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="7ecde-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="7ecde-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="7ecde-108">Installation über das Paketrepository: Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="7ecde-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="7ecde-109">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span> <span data-ttu-id="7ecde-110">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="7ecde-110">This is the preferred method.</span></span>

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

<span data-ttu-id="7ecde-111">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="7ecde-111">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="7ecde-112">Installation über einen direkten Download: Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="7ecde-112">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="7ecde-113">Laden Sie das Debian-Paket `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` über die Seite [Releases][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="7ecde-113">Download the Debian package `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.14.04_amd64.deb
```

<span data-ttu-id="7ecde-114">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="7ecde-114">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="7ecde-115">Bitte beachten Sie, dass für `dpkg -i` ein Fehler aufgrund von nicht erfüllten Abhängigkeiten ausgelöst wird. Über den Befehl `apt-get install -f` wird dieses Problem behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-115">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="7ecde-116">Deinstallation: Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="7ecde-116">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="7ecde-117">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7ecde-117">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="7ecde-118">Installation über das Paketrepository: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7ecde-118">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="7ecde-119">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-119">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="7ecde-120">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="7ecde-120">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7ecde-121">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="7ecde-121">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="7ecde-122">Installation über einen direkten Download: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7ecde-122">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="7ecde-123">Laden Sie das Debian-Paket `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` über die Seite [Releases][] auf den Ubuntu-Computer herunter:</span><span class="sxs-lookup"><span data-stu-id="7ecde-123">Download the Debian package `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
```

<span data-ttu-id="7ecde-124">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="7ecde-124">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="7ecde-125">Bitte beachten Sie, dass für `dpkg -i` ein Fehler aufgrund von nicht erfüllten Abhängigkeiten ausgelöst wird. Über den Befehl `apt-get install -f` wird dieses Problem behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-125">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="7ecde-126">Deinstallation: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7ecde-126">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="7ecde-127">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="7ecde-127">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="7ecde-128">Installation über das Paketrepository: Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="7ecde-128">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="7ecde-129">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-129">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="7ecde-130">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="7ecde-130">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/17.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7ecde-131">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="7ecde-131">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="7ecde-132">Installation über einen direkten Download: Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="7ecde-132">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="7ecde-133">Laden Sie das Debian-Paket `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` über die Seite [Releases][] auf den Ubuntu-Computer herunter:</span><span class="sxs-lookup"><span data-stu-id="7ecde-133">Download the Debian package `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.17.04_amd64.deb
```

<span data-ttu-id="7ecde-134">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="7ecde-134">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="7ecde-135">Bitte beachten Sie, dass für `dpkg -i` ein Fehler aufgrund von nicht erfüllten Abhängigkeiten ausgelöst wird. Über den Befehl `apt-get install -f` wird dieses Problem behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-135">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="7ecde-136">Deinstallation: Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="7ecde-136">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="7ecde-137">Debian 8</span><span class="sxs-lookup"><span data-stu-id="7ecde-137">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="7ecde-138">Installation über das Paketrepository: Debian 8</span><span class="sxs-lookup"><span data-stu-id="7ecde-138">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="7ecde-139">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-139">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="7ecde-140">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="7ecde-140">This is the preferred method.</span></span>

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

<span data-ttu-id="7ecde-141">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="7ecde-141">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="7ecde-142">Installation über einen direkten Download: Debian 8</span><span class="sxs-lookup"><span data-stu-id="7ecde-142">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="7ecde-143">Laden Sie das Debian-Paket `powershell_6.0.0-1.debian.8_amd64.deb` über die Seite [Releases][] auf den Debian-Computer herunter:</span><span class="sxs-lookup"><span data-stu-id="7ecde-143">Download the Debian package `powershell_6.0.0-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.8_amd64.deb
```

<span data-ttu-id="7ecde-144">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="7ecde-144">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="7ecde-145">Bitte beachten Sie, dass für `dpkg -i` ein Fehler aufgrund von nicht erfüllten Abhängigkeiten ausgelöst wird. Über den Befehl `apt-get install -f` wird dieses Problem behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-145">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="7ecde-146">Deinstallation: Debian 8</span><span class="sxs-lookup"><span data-stu-id="7ecde-146">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="7ecde-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="7ecde-147">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="7ecde-148">Installation über das Paketrepository: Debian 9</span><span class="sxs-lookup"><span data-stu-id="7ecde-148">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="7ecde-149">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-149">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="7ecde-150">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="7ecde-150">This is the preferred method.</span></span>

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

<span data-ttu-id="7ecde-151">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="7ecde-151">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="7ecde-152">Installation über einen direkten Download: Debian 9</span><span class="sxs-lookup"><span data-stu-id="7ecde-152">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="7ecde-153">Laden Sie das Debian-Paket `powershell_6.0.0-1.debian.9_amd64.deb` über die Seite [Releases][] auf den Debian-Computer herunter:</span><span class="sxs-lookup"><span data-stu-id="7ecde-153">Download the Debian package `powershell_6.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

<span data-ttu-id="7ecde-154">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="7ecde-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="7ecde-155">Bitte beachten Sie, dass für `dpkg -i` ein Fehler aufgrund von nicht erfüllten Abhängigkeiten ausgelöst wird. Über den Befehl `apt-get install -f` wird dieses Problem behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-155">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="7ecde-156">Deinstallation: Debian 9</span><span class="sxs-lookup"><span data-stu-id="7ecde-156">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="7ecde-157">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7ecde-157">CentOS 7</span></span>

> <span data-ttu-id="7ecde-158">Dieses Paket funktioniert ebenfalls unter Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="7ecde-158">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="7ecde-159">Installation über das Paketrepository (bevorzugt): CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7ecde-159">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="7ecde-160">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-160">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7ecde-161">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo yum update powershell` verwenden, um Updates für PowerShell auszuführen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-161">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="7ecde-162">Installation über einen direkten Download: CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7ecde-162">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="7ecde-163">Für [CentOS 7][]: Laden Sie das RPM-Paket `powershell-6.0.0-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den CentOS-Computer herunter:</span><span class="sxs-lookup"><span data-stu-id="7ecde-163">Using [CentOS 7][], download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7ecde-164">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="7ecde-164">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7ecde-165">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="7ecde-165">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="7ecde-166">Deinstallation: CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7ecde-166">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7ecde-168">Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="7ecde-168">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7ecde-169">Installation über ein Paketrepository (bevorzugt): Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="7ecde-169">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="7ecde-170">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7ecde-171">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo yum update powershell` verwenden, um Updates für PowerShell auszuführen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-171">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7ecde-172">Installation über einen direkten Download: Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="7ecde-172">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="7ecde-173">Laden Sie das RPM-Paket `powershell-6.0.0-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den Red Hat Enterprise Linux-Computer herunter:</span><span class="sxs-lookup"><span data-stu-id="7ecde-173">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

<span data-ttu-id="7ecde-174">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="7ecde-174">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7ecde-175">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="7ecde-175">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7ecde-176">Deinstallation: Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="7ecde-176">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="7ecde-177">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="7ecde-177">OpenSUSE 42.2</span></span>

> <span data-ttu-id="7ecde-178">**Hinweis:** Bei der Installation von PowerShell Core gibt OpenSUSE möglicherweise die Meldung zurück, dass `libcurl` nicht bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="7ecde-178">**Note:** When installing PowerShell Core, OpenSUSE may report that nothing provides `libcurl`.</span></span>
<span data-ttu-id="7ecde-179">`libcurl` sollte für unterstützte OpenSUSE-Versionen bereits installiert sein.</span><span class="sxs-lookup"><span data-stu-id="7ecde-179">`libcurl` should already be installed on supported versions of OpenSUSE.</span></span>
<span data-ttu-id="7ecde-180">Führen Sie `zypper search libcurl` zur Bestätigung aus.</span><span class="sxs-lookup"><span data-stu-id="7ecde-180">Run `zypper search libcurl` to confirm.</span></span>
<span data-ttu-id="7ecde-181">In der Fehlermeldung werden zwei mögliche Lösungen genannt.</span><span class="sxs-lookup"><span data-stu-id="7ecde-181">The error will present 2 'solutions'.</span></span> <span data-ttu-id="7ecde-182">Wählen Sie Lösung 2 aus, um mit der Installation von PowerShell Core fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="7ecde-182">Choose 'Solution 2' to continue installing PowerShell Core.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="7ecde-183">Installation über das Paketrepository (bevorzugt): OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="7ecde-183">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="7ecde-184">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-184">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="7ecde-185">Installation über einen direkten Download: OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="7ecde-185">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="7ecde-186">Laden Sie das RPM-Paket `powershell-6.0.0-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den openSUSE-Computer herunter:</span><span class="sxs-lookup"><span data-stu-id="7ecde-186">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7ecde-187">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="7ecde-187">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="7ecde-188">Deinstallation. OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="7ecde-188">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="7ecde-189">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="7ecde-189">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="7ecde-190">Installation über das Paketrepository (bevorzugt): Fedora 25</span><span class="sxs-lookup"><span data-stu-id="7ecde-190">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="7ecde-191">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-191">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="7ecde-192">Installation über einen direkten Download: Fedora 25</span><span class="sxs-lookup"><span data-stu-id="7ecde-192">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="7ecde-193">Laden Sie das RPM-Paket `powershell-6.0.0-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den Fedora-Computer herunter:</span><span class="sxs-lookup"><span data-stu-id="7ecde-193">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7ecde-194">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="7ecde-194">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7ecde-195">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="7ecde-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="7ecde-196">Deinstallation: Fedora 25</span><span class="sxs-lookup"><span data-stu-id="7ecde-196">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="7ecde-197">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="7ecde-197">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="7ecde-198">Installation über das Paketrepository (bevorzugt): Fedora 26</span><span class="sxs-lookup"><span data-stu-id="7ecde-198">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="7ecde-199">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="7ecde-200">Installation über einen direkten Download: Fedora 26</span><span class="sxs-lookup"><span data-stu-id="7ecde-200">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="7ecde-201">Laden Sie das RPM-Paket `powershell-6.0.0-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den Fedora-Computer herunter:</span><span class="sxs-lookup"><span data-stu-id="7ecde-201">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7ecde-202">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="7ecde-202">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7ecde-203">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="7ecde-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="7ecde-204">Deinstallation: Fedora 26</span><span class="sxs-lookup"><span data-stu-id="7ecde-204">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="7ecde-205">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="7ecde-205">Arch Linux</span></span>

<span data-ttu-id="7ecde-206">PowerShell ist über das Benutzerrepository [Arch Linux][] verfügbar.</span><span class="sxs-lookup"><span data-stu-id="7ecde-206">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="7ecde-207">Es kann gemeinsam mit dem [zuletzt markierten Release][arch-release] installiert werden.</span><span class="sxs-lookup"><span data-stu-id="7ecde-207">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="7ecde-208">Es kann gemeinsam mit dem [letzten Commit für den Master][arch-git] kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="7ecde-208">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="7ecde-209">Es kann mithilfe der [zuletzt veröffentlichten Binärdatei][arch-bin] kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="7ecde-209">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="7ecde-210">Pakete im Benutzerrepository „Arch Linux“ werden von der Community verwaltet. Es gibt keinen offiziellen Support.</span><span class="sxs-lookup"><span data-stu-id="7ecde-210">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="7ecde-211">Weitere Informationen zum Installieren von Paketen aus dem Benutzerrepository „Arch Linux“ finden Sie im [Arch Linux-Wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) oder in [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) der Community.</span><span class="sxs-lookup"><span data-stu-id="7ecde-211">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="7ecde-213">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="7ecde-213">Linux AppImage</span></span>

<span data-ttu-id="7ecde-214">Wenn Sie eine aktuelle Linux-Distribution verwenden, laden Sie AppImage `powershell-6.0.0-x86_64.AppImage` auf der Seite [Releases][] auf den Linux-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="7ecde-214">Using a recent Linux distribution, download the AppImage `powershell-6.0.0-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="7ecde-215">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="7ecde-215">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.0-x86_64.AppImage
./powershell-6.0.0-x86_64.AppImage
```

<span data-ttu-id="7ecde-216">Mithilfe von [AppImage][] können Sie PowerShell ohne Installation ausführen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-216">The [AppImage][] lets you run PowerShell without installing it.</span></span> <span data-ttu-id="7ecde-217">Dabei handelt es sich um eine portierbare Anwendung, die PowerShell und dessen Abhängigkeiten in ein Paket bündelt (einschließlich der Systemabhängigkeiten von .NET Core).</span><span class="sxs-lookup"><span data-stu-id="7ecde-217">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span> <span data-ttu-id="7ecde-218">Dieses Paket funktioniert unabhängig von der Linux-Distribution des Benutzers. Außerdem handelt es sich dabei um eine einzelne Binärdatei.</span><span class="sxs-lookup"><span data-stu-id="7ecde-218">This package works independently of the user's Linux distribution, and is a single binary.</span></span>

[appimage]: http://appimage.org/

## <a name="macos-1012"></a><span data-ttu-id="7ecde-220">macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="7ecde-220">macOS 10.12</span></span>

### <a name="installation-via-homebrew-preferred---macos-1012"></a><span data-ttu-id="7ecde-221">Installation über Homebrew (bevorzugt): macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="7ecde-221">Installation via Homebrew (preferred) - macOS 10.12</span></span>

<span data-ttu-id="7ecde-222">Bei [Homebrew][brew] handelt es sich um den fehlenden Paket-Manager für macOS.</span><span class="sxs-lookup"><span data-stu-id="7ecde-222">[Homebrew][brew] is the missing package manager for macOS.</span></span> <span data-ttu-id="7ecde-223">Wenn der Befehl `brew` nicht gefunden wird, müssen Sie Homebrew installieren, indem Sie [die entsprechenden Anweisungen][brew] ausführen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-223">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="7ecde-224">Wenn Sie Homebrew installiert haben, können Sie auch problemlos PowerShell installieren.</span><span class="sxs-lookup"><span data-stu-id="7ecde-224">Once you've installed Homebrew, installing PowerShell is easy.</span></span> <span data-ttu-id="7ecde-225">Installieren Sie zuerst [Homebrew-Cask][cask], damit Sie danach weitere Pakete installieren können:</span><span class="sxs-lookup"><span data-stu-id="7ecde-225">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="7ecde-226">Jetzt können Sie PowerShell installieren:</span><span class="sxs-lookup"><span data-stu-id="7ecde-226">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="7ecde-227">Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie einfach die Formel für Homebrew, und führen Sie ein Upgrade für PowerShell aus:</span><span class="sxs-lookup"><span data-stu-id="7ecde-227">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask reinstall powershell
```

> <span data-ttu-id="7ecde-228">Hinweis: Aufgrund [dieses Problems in Cask](https://github.com/caskroom/homebrew-cask/issues/29301) müssen Sie das Upgrade derzeit erneut installieren.</span><span class="sxs-lookup"><span data-stu-id="7ecde-228">Note: because of [this issue in Cask](https://github.com/caskroom/homebrew-cask/issues/29301), you currently have to do a reinstall to upgrade.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a><span data-ttu-id="7ecde-229">Installation über einen direkten Download: macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="7ecde-229">Installation via Direct Download - macOS 10.12</span></span>

<span data-ttu-id="7ecde-230">Für macOS 10.12: Laden Sie das PKG-Paket `powershell-6.0.0-osx.10.12-x64.pkg` über die Seite [Releases][] auf den macOS-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="7ecde-230">Using macOS 10.12, download the PKG package `powershell-6.0.0-osx.10.12-x64.pkg` from the [releases][] page onto the macOS machine.</span></span>

<span data-ttu-id="7ecde-231">Doppelklicken Sie entweder auf die Datei, und befolgen Sie die Anweisungen, oder installieren Sie das Paket über das Terminal:</span><span class="sxs-lookup"><span data-stu-id="7ecde-231">Either double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.0-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a><span data-ttu-id="7ecde-232">Deinstallation: macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="7ecde-232">Uninstallation - macOS 10.12</span></span>

<span data-ttu-id="7ecde-233">Wenn Sie PowerShell mit Homebrew installiert haben, gestaltet sich die Deinstallation einfach:</span><span class="sxs-lookup"><span data-stu-id="7ecde-233">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="7ecde-234">Wenn Sie PowerShell über einen direkten Download installiert haben, muss PowerShell manuell entfernt werden:</span><span class="sxs-lookup"><span data-stu-id="7ecde-234">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="7ecde-235">Lesen Sie den Abschnitt [Pfade][paths] in diesem Artikel, um zu erfahren, wie Sie zusätzliche PowerShell-Pfade wie den Benutzerprofilpfad deinstallieren können, und entfernen Sie die gewünschten Pfade mit `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="7ecde-235">To uninstall the additional PowerShell paths (such as the user profile path) please see the [paths][paths] section below in this document and remove the desired the paths with `sudo rm`.</span></span> <span data-ttu-id="7ecde-236">(Hinweis: Dies ist nicht notwendig, wenn Sie eine Installation mit Homebrew durchgeführt haben.)</span><span class="sxs-lookup"><span data-stu-id="7ecde-236">(Note: this is not necessary if you installed with Homebrew.)</span></span>

[paths]:#paths

## <a name="kali"></a><span data-ttu-id="7ecde-237">Kali</span><span class="sxs-lookup"><span data-stu-id="7ecde-237">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="7ecde-238">Installation</span><span class="sxs-lookup"><span data-stu-id="7ecde-238">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Download & Install PowerShell
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="7ecde-239">Führen Sie PowerShell unter der neusten Kali-Version (Kali GNU/Linux Rolling) aus, ohne es zuvor zu installieren.</span><span class="sxs-lookup"><span data-stu-id="7ecde-239">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="7ecde-240">Deinstallation: Kali</span><span class="sxs-lookup"><span data-stu-id="7ecde-240">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell-6.0.0-x86_64.AppImage
```

## <a name="raspbian"></a><span data-ttu-id="7ecde-241">Raspbian</span><span class="sxs-lookup"><span data-stu-id="7ecde-241">Raspbian</span></span>

<span data-ttu-id="7ecde-242">Derzeit wird PowerShell nur unter Raspbian Stretch unterstützt.</span><span class="sxs-lookup"><span data-stu-id="7ecde-242">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

### <a name="installation"></a><span data-ttu-id="7ecde-243">Installation</span><span class="sxs-lookup"><span data-stu-id="7ecde-243">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="7ecde-244">Deinstallation: Raspbian</span><span class="sxs-lookup"><span data-stu-id="7ecde-244">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="7ecde-245">Archive der Binärdateien</span><span class="sxs-lookup"><span data-stu-id="7ecde-245">Binary Archives</span></span>

<span data-ttu-id="7ecde-246">`tar.gz`-Archive der PowerShell-Binärdateien werden für die Plattformen macOs und Linux zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="7ecde-246">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="7ecde-247">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="7ecde-247">Dependencies</span></span>

<span data-ttu-id="7ecde-248">Unter Linux erstellt PowerShell portierbare Binärdateien für alle Linux-Distributionen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-248">For Linux, PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="7ecde-249">Allerdings erfordert die .NET Core-Laufzeit, und damit auch PowerShell, verschiedene Abhängigkeiten für die verschiedenen Distributionen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-249">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="7ecde-250">Im folgenden Diagramm werden die Abhängigkeiten von .NET Core 2.0 für die verschiedenen Linux-Distributionen dargestellt, die offiziell unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="7ecde-250">The following chart shows the .NET Core 2.0 dependencies on different Linux distributions that are officially supported.</span></span>

| <span data-ttu-id="7ecde-251">Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="7ecde-251">OS</span></span>                 | <span data-ttu-id="7ecde-252">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="7ecde-252">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="7ecde-253">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="7ecde-253">Ubuntu 14.04</span></span>       | <span data-ttu-id="7ecde-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="7ecde-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7ecde-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="7ecde-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="7ecde-256">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7ecde-256">Ubuntu 16.04</span></span>       | <span data-ttu-id="7ecde-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="7ecde-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7ecde-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="7ecde-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="7ecde-259">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="7ecde-259">Ubuntu 17.04</span></span>       | <span data-ttu-id="7ecde-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="7ecde-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7ecde-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="7ecde-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="7ecde-262">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="7ecde-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="7ecde-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="7ecde-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7ecde-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="7ecde-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="7ecde-265">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="7ecde-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="7ecde-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="7ecde-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7ecde-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="7ecde-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="7ecde-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7ecde-268">CentOS 7</span></span> <br> <span data-ttu-id="7ecde-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="7ecde-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="7ecde-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="7ecde-270">RHEL 7</span></span> <br> <span data-ttu-id="7ecde-271">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="7ecde-271">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="7ecde-272">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="7ecde-272">Fedora 25</span></span> | <span data-ttu-id="7ecde-273">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="7ecde-273">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="7ecde-274">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="7ecde-274">Fedora 26</span></span>          | <span data-ttu-id="7ecde-275">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="7ecde-275">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="7ecde-276">Sie müssen zur Bereitstellung von PowerShell-Binärdateien für nicht offiziell unterstützte Linux-Verteilungen die notwendigen Abhängigkeiten für das Zielbetriebssystem über zusätzliche Schritte installieren.</span><span class="sxs-lookup"><span data-stu-id="7ecde-276">In order to deploy PowerShell binaries on Linux distributions that are not officially supported, you would need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="7ecde-277">Beispielsweise installiert die [Amazon Linux-Dockerfile][amazon-dockerfile] zuerst die Abhängigkeiten und extrahiert anschließend erst das Linux-`tar.gz`-Archiv.</span><span class="sxs-lookup"><span data-stu-id="7ecde-277">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="7ecde-278">Installation: Archive von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="7ecde-278">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="7ecde-279">Linux</span><span class="sxs-lookup"><span data-stu-id="7ecde-279">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.0/pwsh /usr/bin/pwsh
```

#### <a name="macos"></a><span data-ttu-id="7ecde-280">macOS</span><span class="sxs-lookup"><span data-stu-id="7ecde-280">macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.0/pwsh /usr/local/bin/pwsh
```

### <a name="uninstallation---binary-archives"></a><span data-ttu-id="7ecde-281">Deinstallation: Archive von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="7ecde-281">Uninstallation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="7ecde-282">Linux</span><span class="sxs-lookup"><span data-stu-id="7ecde-282">Linux</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a><span data-ttu-id="7ecde-283">macOS</span><span class="sxs-lookup"><span data-stu-id="7ecde-283">macOS</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="7ecde-284">Pfade</span><span class="sxs-lookup"><span data-stu-id="7ecde-284">Paths</span></span>

* <span data-ttu-id="7ecde-285">`$PSHOME` ist `/opt/microsoft/powershell/6.0.0/`.</span><span class="sxs-lookup"><span data-stu-id="7ecde-285">`$PSHOME` is `/opt/microsoft/powershell/6.0.0/`</span></span>
* <span data-ttu-id="7ecde-286">Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-286">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="7ecde-287">Standardprofile werden über `$PSHOME/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-287">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="7ecde-288">Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-288">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="7ecde-289">Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-289">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="7ecde-290">Standardmodule werden über `$PSHOME/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="7ecde-290">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="7ecde-291">Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="7ecde-291">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="7ecde-292">Die Profile beachten die Konfigurationen von PowerShell pro Host. Das bedeutet, die hostspezifischen Standardprofile sind an denselben Orten unter `Microsoft.PowerShell_profile.ps1` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="7ecde-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="7ecde-293">Unter Linux und macOS wird die [XDG Base Directory Specification][xdg-bds] beachtet.</span><span class="sxs-lookup"><span data-stu-id="7ecde-293">On Linux and macOS, the [XDG Base Directory Specification][xdg-bds] is respected.</span></span>

<span data-ttu-id="7ecde-294">Bitte beachten Sie, dass anstelle von `/opt` das Präfix `/usr/local` verwendet wird, da macOS eine Ableitung von BSD ist.</span><span class="sxs-lookup"><span data-stu-id="7ecde-294">Note that because macOS is a derivation of BSD, instead of `/opt`, the prefix used is `/usr/local`.</span></span> <span data-ttu-id="7ecde-295">Daher ist `$PSHOME` `/usr/local/microsoft/powershell/6.0.0/` und der Symlink wird unter `/usr/local/bin/pwsh` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="7ecde-295">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[Releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
