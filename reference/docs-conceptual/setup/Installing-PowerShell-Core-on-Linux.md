# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="dd609-101">Installieren von PowerShell Core unter Linux</span><span class="sxs-lookup"><span data-stu-id="dd609-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="dd609-102">Unterstützt [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26][ und ]Arch Linux[arch].</span><span class="sxs-lookup"><span data-stu-id="dd609-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], and [Arch Linux][arch].</span></span>

<span data-ttu-id="dd609-103">Für nicht offiziell unterstützte Linux-Distributionen können Sie versuchen, [PowerShell AppImage][lai] zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="dd609-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="dd609-104">Stattdessen können Sie auch versuchen, PowerShell-Binärdateien über das [`tar.gz`-Archiv][tar] für Linux bereitzustellen. Dafür müssen Sie aber basierend auf Ihrem Betriebssystem die benötigten Abhängigkeiten in zusätzlichen Schritten einrichten.</span><span class="sxs-lookup"><span data-stu-id="dd609-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="dd609-105">Sämtliche Pakete sind auf der Seite [Releases][] über GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="dd609-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="dd609-106">Führen Sie `pwsh` über das Terminal aus, nachdem Sie das Paket installiert haben.</span><span class="sxs-lookup"><span data-stu-id="dd609-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

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
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="dd609-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="dd609-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="dd609-108">Installation über das Paketrepository: Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="dd609-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="dd609-109">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="dd609-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="dd609-110">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="dd609-110">This is the preferred method.</span></span>

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

<span data-ttu-id="dd609-111">Registrieren Sie das Microsoft-Repository als Superuser.</span><span class="sxs-lookup"><span data-stu-id="dd609-111">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="dd609-112">Von nun an müssen Sie nur `sudo apt-get upgrade powershell` verwenden, um die Installation zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="dd609-112">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="dd609-113">Installation über einen direkten Download: Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="dd609-113">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="dd609-114">Laden Sie das Debian-Paket `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` über die Seite [Releases][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="dd609-114">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="dd609-115">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="dd609-115">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="dd609-116">Bitte beachten Sie, dass für `dpkg -i` ein Fehler aufgrund von nicht erfüllten Abhängigkeiten ausgelöst wird. Über den Befehl `apt-get install -f` wird dieses Problem behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="dd609-116">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="dd609-117">Deinstallation: Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="dd609-117">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="dd609-118">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="dd609-118">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="dd609-119">Installation über das Paketrepository: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="dd609-119">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="dd609-120">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="dd609-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="dd609-121">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="dd609-121">This is the preferred method.</span></span>

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

<span data-ttu-id="dd609-122">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="dd609-122">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="dd609-123">Installation über einen direkten Download: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="dd609-123">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="dd609-124">Laden Sie das Debian-Paket `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` über die Seite [Releases][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="dd609-124">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="dd609-125">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="dd609-125">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="dd609-126">Bitte beachten Sie, dass für `dpkg -i` ein Fehler aufgrund von nicht erfüllten Abhängigkeiten ausgelöst wird. Über den Befehl `apt-get install -f` wird dieses Problem behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="dd609-126">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="dd609-127">Deinstallation: Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="dd609-127">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="dd609-128">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="dd609-128">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="dd609-129">Installation über das Paketrepository: Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="dd609-129">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="dd609-130">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="dd609-130">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="dd609-131">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="dd609-131">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="dd609-132">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="dd609-132">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="dd609-133">Installation über einen direkten Download: Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="dd609-133">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="dd609-134">Laden Sie das Debian-Paket `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` über die Seite [Releases][] auf den Ubuntu-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="dd609-134">Download the Debian package `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="dd609-135">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="dd609-135">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="dd609-136">Bitte beachten Sie, dass für `dpkg -i` ein Fehler aufgrund von nicht erfüllten Abhängigkeiten ausgelöst wird. Über den Befehl `apt-get install -f` wird dieses Problem behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="dd609-136">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="dd609-137">Deinstallation: Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="dd609-137">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="dd609-138">Debian 8</span><span class="sxs-lookup"><span data-stu-id="dd609-138">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="dd609-139">Installation über das Paketrepository: Debian 8</span><span class="sxs-lookup"><span data-stu-id="dd609-139">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="dd609-140">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="dd609-140">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="dd609-141">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="dd609-141">This is the preferred method.</span></span>

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

<span data-ttu-id="dd609-142">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="dd609-142">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="dd609-143">Installation über einen direkten Download: Debian 8</span><span class="sxs-lookup"><span data-stu-id="dd609-143">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="dd609-144">Laden Sie das Debian-Paket `powershell_6.0.2-1.debian.8_amd64.deb` über die Seite [Releases][] auf den Debian-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="dd609-144">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="dd609-145">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="dd609-145">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="dd609-146">Bitte beachten Sie, dass bei nicht erfüllten Abhängigkeiten ein Fehler für `dpkg -i` ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="dd609-146">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="dd609-147">Über den Befehl `apt-get install -f` wird dieses Problem behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="dd609-147">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="dd609-148">Deinstallation: Debian 8</span><span class="sxs-lookup"><span data-stu-id="dd609-148">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="dd609-149">Debian 9</span><span class="sxs-lookup"><span data-stu-id="dd609-149">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="dd609-150">Installation über das Paketrepository: Debian 9</span><span class="sxs-lookup"><span data-stu-id="dd609-150">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="dd609-151">PowerShell Core für Linux wird in Paketrepositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="dd609-151">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="dd609-152">Dies ist die bevorzugte Methode.</span><span class="sxs-lookup"><span data-stu-id="dd609-152">This is the preferred method.</span></span>

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

<span data-ttu-id="dd609-153">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo apt-get upgrade powershell` verwenden, um Updates ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="dd609-153">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="dd609-154">Installation über einen direkten Download: Debian 9</span><span class="sxs-lookup"><span data-stu-id="dd609-154">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="dd609-155">Laden Sie das Debian-Paket `powershell_6.0.2-1.debian.9_amd64.deb` über die Seite [Releases][] auf den Debian-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="dd609-155">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="dd609-156">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="dd609-156">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="dd609-157">Bitte beachten Sie, dass bei nicht erfüllten Abhängigkeiten ein Fehler für `dpkg -i` ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="dd609-157">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="dd609-158">Über den Befehl `apt-get install -f` wird dieses Problem behoben und die Konfiguration des PowerShell-Pakets abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="dd609-158">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="dd609-159">Deinstallation: Debian 9</span><span class="sxs-lookup"><span data-stu-id="dd609-159">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="dd609-160">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="dd609-160">CentOS 7</span></span>

> <span data-ttu-id="dd609-161">Dieses Paket funktioniert ebenfalls unter Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="dd609-161">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="dd609-162">Installation über das Paketrepository (bevorzugt): CentOS 7</span><span class="sxs-lookup"><span data-stu-id="dd609-162">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="dd609-163">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="dd609-163">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="dd609-164">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo yum update powershell` verwenden, um Updates für PowerShell auszuführen.</span><span class="sxs-lookup"><span data-stu-id="dd609-164">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="dd609-165">Installation über einen direkten Download: CentOS 7</span><span class="sxs-lookup"><span data-stu-id="dd609-165">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="dd609-166">Für [CentOS 7][]: Laden Sie das RPM-Paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den CentOS-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="dd609-166">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="dd609-167">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="dd609-167">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="dd609-168">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="dd609-168">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="dd609-169">Deinstallation: CentOS 7</span><span class="sxs-lookup"><span data-stu-id="dd609-169">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="dd609-171">Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="dd609-171">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="dd609-172">Installation über ein Paketrepository (bevorzugt): Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="dd609-172">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="dd609-173">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="dd609-173">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="dd609-174">Wenn Sie das Microsoft-Repository einmal als Benutzer mit Administratorrechten registriert haben, müssen Sie danach immer `sudo yum update powershell` verwenden, um Updates für PowerShell auszuführen.</span><span class="sxs-lookup"><span data-stu-id="dd609-174">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="dd609-175">Installation über einen direkten Download: Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="dd609-175">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="dd609-176">Laden Sie das RPM-Paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den Red Hat Enterprise Linux-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="dd609-176">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="dd609-177">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="dd609-177">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="dd609-178">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="dd609-178">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="dd609-179">Deinstallation: Red Hat Enterprise Linux 7 (RHEL)</span><span class="sxs-lookup"><span data-stu-id="dd609-179">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="dd609-180">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="dd609-180">OpenSUSE 42.2</span></span>

> [!NOTE]
> <span data-ttu-id="dd609-181">Bei der Installation von PowerShell Core verursacht `zypper` eventuell den folgenden Fehler:</span><span class="sxs-lookup"><span data-stu-id="dd609-181">When installing PowerShell Core, `zypper` may report the following error:</span></span>
>
> ```Output
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> <span data-ttu-id="dd609-182">Stellen Sie in diesem Fall sicher, dass eine kompatible `libcurl`-Bibliothek vorhanden ist, indem Sie überprüfen, ob der folgende Befehl das `libcurl4`-Paket als installiert anzeigt:</span><span class="sxs-lookup"><span data-stu-id="dd609-182">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> <span data-ttu-id="dd609-183">Wählen Sie bei der Installation des PowerShell-Pakets die Lösung `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` aus.</span><span class="sxs-lookup"><span data-stu-id="dd609-183">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="dd609-184">Installation über das Paketrepository (bevorzugt): OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="dd609-184">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="dd609-185">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="dd609-185">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="dd609-186">Installation über einen direkten Download: OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="dd609-186">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="dd609-187">Laden Sie das RPM-Paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den OpenSUSE-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="dd609-187">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="dd609-188">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="dd609-188">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="dd609-189">Deinstallation. OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="dd609-189">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="dd609-190">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="dd609-190">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="dd609-191">Installation über das Paketrepository (bevorzugt): Fedora 25</span><span class="sxs-lookup"><span data-stu-id="dd609-191">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="dd609-192">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="dd609-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="dd609-193">Installation über einen direkten Download: Fedora 25</span><span class="sxs-lookup"><span data-stu-id="dd609-193">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="dd609-194">Laden Sie das RPM-Paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den Fedora-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="dd609-194">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="dd609-195">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="dd609-195">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="dd609-196">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="dd609-196">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="dd609-197">Deinstallation: Fedora 25</span><span class="sxs-lookup"><span data-stu-id="dd609-197">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="dd609-198">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="dd609-198">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="dd609-199">Installation über das Paketrepository (bevorzugt): Fedora 26</span><span class="sxs-lookup"><span data-stu-id="dd609-199">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="dd609-200">PowerShell Core für Linux wird in offiziellen Microsoft-Repositorys veröffentlicht, um die Installation (und die Updates) zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="dd609-200">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="dd609-201">Installation über einen direkten Download: Fedora 26</span><span class="sxs-lookup"><span data-stu-id="dd609-201">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="dd609-202">Laden Sie das RPM-Paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` über die Seite [Releases][] auf den Fedora-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="dd609-202">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="dd609-203">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="dd609-203">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="dd609-204">Außerdem können Sie RPM installieren, ohne es herunterladen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="dd609-204">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="dd609-205">Deinstallation: Fedora 26</span><span class="sxs-lookup"><span data-stu-id="dd609-205">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="dd609-206">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="dd609-206">Arch Linux</span></span>

<span data-ttu-id="dd609-207">PowerShell ist über das Benutzerrepository [Arch Linux][] verfügbar.</span><span class="sxs-lookup"><span data-stu-id="dd609-207">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="dd609-208">Es kann gemeinsam mit dem [zuletzt markierten Release][arch-release] installiert werden.</span><span class="sxs-lookup"><span data-stu-id="dd609-208">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="dd609-209">Es kann gemeinsam mit dem [letzten Commit für den Master][arch-git] kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="dd609-209">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="dd609-210">Es kann mithilfe der [zuletzt veröffentlichten Binärdatei][arch-bin] kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="dd609-210">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="dd609-211">Pakete im Benutzerrepository „Arch Linux“ werden von der Community verwaltet. Es gibt keinen offiziellen Support.</span><span class="sxs-lookup"><span data-stu-id="dd609-211">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="dd609-212">Weitere Informationen zum Installieren von Paketen aus dem Benutzerrepository „Arch Linux“ finden Sie im [Arch Linux-Wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) oder in [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) der Community.</span><span class="sxs-lookup"><span data-stu-id="dd609-212">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="dd609-214">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="dd609-214">Linux AppImage</span></span>

<span data-ttu-id="dd609-215">Wenn Sie eine aktuelle Linux-Distribution verwenden, laden Sie AppImage `powershell-6.0.1-x86_64.AppImage` auf der Seite [Releases][] auf den Linux-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="dd609-215">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="dd609-216">Führen Sie dann folgenden Befehl im Terminal aus:</span><span class="sxs-lookup"><span data-stu-id="dd609-216">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="dd609-217">Mithilfe von [AppImage][] können Sie PowerShell ohne Installation ausführen.</span><span class="sxs-lookup"><span data-stu-id="dd609-217">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="dd609-218">Dabei handelt es sich um eine portierbare Anwendung, die PowerShell und dessen Abhängigkeiten in ein Paket bündelt (einschließlich der Systemabhängigkeiten von .NET Core).</span><span class="sxs-lookup"><span data-stu-id="dd609-218">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="dd609-219">Dieses Paket funktioniert unabhängig von der Linux-Distribution des Benutzers. Außerdem handelt es sich dabei um eine einzelne Binärdatei.</span><span class="sxs-lookup"><span data-stu-id="dd609-219">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="dd609-221">Kali</span><span class="sxs-lookup"><span data-stu-id="dd609-221">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="dd609-222">Installation</span><span class="sxs-lookup"><span data-stu-id="dd609-222">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="dd609-223">Führen Sie PowerShell unter der neusten Kali-Version (Kali GNU/Linux Rolling) aus, ohne es zuvor zu installieren.</span><span class="sxs-lookup"><span data-stu-id="dd609-223">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="dd609-224">Deinstallation: Kali</span><span class="sxs-lookup"><span data-stu-id="dd609-224">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="dd609-225">Raspbian</span><span class="sxs-lookup"><span data-stu-id="dd609-225">Raspbian</span></span>

<span data-ttu-id="dd609-226">Derzeit wird PowerShell nur unter Raspbian Stretch unterstützt.</span><span class="sxs-lookup"><span data-stu-id="dd609-226">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="dd609-227">Außerdem funktioniert CoreCLR (und daher auch PowerShell Core) nur auf Geräten mit Pi 2 und Pi 3, da andere Geräte, wie z.B. [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), einen nicht unterstützten Prozessor haben.</span><span class="sxs-lookup"><span data-stu-id="dd609-227">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="dd609-228">Laden Sie [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) herunter, und folgen Sie den [Installationsanweisungen](https://www.raspberrypi.org/documentation/installation/installing-images/README.md), um es zu installieren.</span><span class="sxs-lookup"><span data-stu-id="dd609-228">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="dd609-229">Installation</span><span class="sxs-lookup"><span data-stu-id="dd609-229">Installation</span></span>

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

<span data-ttu-id="dd609-230">Optional können Sie eine symbolische Verknüpfung erstellen, damit Sie PowerShell ohne Angabe eines Pfads auf die Binärdatei „pwsh“ starten können.</span><span class="sxs-lookup"><span data-stu-id="dd609-230">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="dd609-231">Deinstallation: Raspbian</span><span class="sxs-lookup"><span data-stu-id="dd609-231">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="dd609-232">Archive der Binärdateien</span><span class="sxs-lookup"><span data-stu-id="dd609-232">Binary Archives</span></span>

<span data-ttu-id="dd609-233">`tar.gz`-Archive der PowerShell-Binärdateien werden für Linux-Plattformen zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="dd609-233">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="dd609-234">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="dd609-234">Dependencies</span></span>

<span data-ttu-id="dd609-235">PowerShell erstellt portierbare Binärdateien für alle Linux-Distributionen.</span><span class="sxs-lookup"><span data-stu-id="dd609-235">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="dd609-236">Allerdings erfordert die .NET Core-Laufzeit, und damit auch PowerShell, verschiedene Abhängigkeiten für die verschiedenen Distributionen.</span><span class="sxs-lookup"><span data-stu-id="dd609-236">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="dd609-237">Im folgenden Diagramm werden die Abhängigkeiten von .NET Core 2.0 für die verschiedenen Linux-Distributionen dargestellt, die offiziell unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="dd609-237">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="dd609-238">Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="dd609-238">OS</span></span>                 | <span data-ttu-id="dd609-239">Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="dd609-239">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="dd609-240">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="dd609-240">Ubuntu 14.04</span></span>       | <span data-ttu-id="dd609-241">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="dd609-241">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dd609-242">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="dd609-242">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="dd609-243">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="dd609-243">Ubuntu 16.04</span></span>       | <span data-ttu-id="dd609-244">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="dd609-244">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dd609-245">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="dd609-245">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="dd609-246">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="dd609-246">Ubuntu 17.04</span></span>       | <span data-ttu-id="dd609-247">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="dd609-247">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dd609-248">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="dd609-248">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="dd609-249">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="dd609-249">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="dd609-250">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="dd609-250">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dd609-251">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="dd609-251">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="dd609-252">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="dd609-252">Debian 9 (Stretch)</span></span> | <span data-ttu-id="dd609-253">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="dd609-253">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dd609-254">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="dd609-254">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="dd609-255">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="dd609-255">CentOS 7</span></span> <br> <span data-ttu-id="dd609-256">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="dd609-256">Oracle Linux 7</span></span> <br> <span data-ttu-id="dd609-257">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="dd609-257">RHEL 7</span></span> <br> <span data-ttu-id="dd609-258">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="dd609-258">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="dd609-259">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="dd609-259">Fedora 25</span></span> | <span data-ttu-id="dd609-260">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="dd609-260">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="dd609-261">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="dd609-261">Fedora 26</span></span>          | <span data-ttu-id="dd609-262">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="dd609-262">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="dd609-263">Sie müssen zur Bereitstellung von PowerShell-Binärdateien für nicht offiziell unterstützte Linux-Distributionen die notwendigen Abhängigkeiten für das Zielbetriebssystem über zusätzliche Schritte installieren.</span><span class="sxs-lookup"><span data-stu-id="dd609-263">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="dd609-264">Beispielsweise installiert die [Amazon Linux-Dockerfile][amazon-dockerfile] zuerst die Abhängigkeiten und extrahiert anschließend erst das Linux-`tar.gz`-Archiv.</span><span class="sxs-lookup"><span data-stu-id="dd609-264">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="dd609-265">Installation: Archive von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="dd609-265">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="dd609-266">Linux</span><span class="sxs-lookup"><span data-stu-id="dd609-266">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="dd609-267">Deinstallation: Archive von Binärdateien</span><span class="sxs-lookup"><span data-stu-id="dd609-267">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="dd609-268">Pfade</span><span class="sxs-lookup"><span data-stu-id="dd609-268">Paths</span></span>

* <span data-ttu-id="dd609-269">`$PSHOME` ist `/opt/microsoft/powershell/6.0.2/`.</span><span class="sxs-lookup"><span data-stu-id="dd609-269">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="dd609-270">Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="dd609-270">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="dd609-271">Standardprofile werden über `$PSHOME/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="dd609-271">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="dd609-272">Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="dd609-272">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="dd609-273">Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="dd609-273">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="dd609-274">Standardmodule werden über `$PSHOME/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="dd609-274">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="dd609-275">Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="dd609-275">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="dd609-276">Die Profile beachten die Konfigurationen von PowerShell pro Host. Das bedeutet, die hostspezifischen Standardprofile sind an denselben Orten unter `Microsoft.PowerShell_profile.ps1` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="dd609-276">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="dd609-277">PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter Linux ein.</span><span class="sxs-lookup"><span data-stu-id="dd609-277">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Releases]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
