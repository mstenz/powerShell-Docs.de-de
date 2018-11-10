---
title: Installieren von PowerShell Core unter macOS
description: Informationen zur Installation von PowerShell Core unter macOS
ms.date: 11/02/2018
ms.openlocfilehash: 162e841bf71d708e9db84ea1bb2dbef13924783b
ms.sourcegitcommit: f4247d3f91d06ec392c4cd66921ce7d0456a2bd9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "50998502"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="cd3c1-103">Installieren von PowerShell Core unter macOS</span><span class="sxs-lookup"><span data-stu-id="cd3c1-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="cd3c1-104">PowerShell Core unterstützt macOs 10.12 und höher.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="cd3c1-105">Sämtliche Pakete sind auf der Seite [Releases][] über GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="cd3c1-106">Führen Sie `pwsh` über das Terminal aus, nachdem Sie das Paket installiert haben.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="cd3c1-107">Informationen zu Brew</span><span class="sxs-lookup"><span data-stu-id="cd3c1-107">About Brew</span></span>

<span data-ttu-id="cd3c1-108">Bei [Homebrew][brew] handelt es sich um den bevorzugten Paket-Manager für macOS.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="cd3c1-109">Wenn der Befehl `brew` nicht gefunden wird, müssen Sie Homebrew installieren, indem Sie [die entsprechenden Anweisungen][brew] ausführen.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="cd3c1-110">Installation des neuesten stabilen Release über Homebrew unter macOS 10.12 oder höher</span><span class="sxs-lookup"><span data-stu-id="cd3c1-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="cd3c1-111">Weitere Informationen zu Ansichten finden Sie unter [Info zu Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="cd3c1-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="cd3c1-112">Jetzt können Sie PowerShell installieren:</span><span class="sxs-lookup"><span data-stu-id="cd3c1-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="cd3c1-113">Vergewissern Sie sich abschließend, dass Ihre Installation voll funktionsfähig ist:</span><span class="sxs-lookup"><span data-stu-id="cd3c1-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="cd3c1-114">Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie einfach die Formel für Homebrew, und führen Sie ein Upgrade für PowerShell aus:</span><span class="sxs-lookup"><span data-stu-id="cd3c1-114">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="cd3c1-115">Die oben genannten Befehle können innerhalb eines PowerShell-Hosts (pwsh) aufgerufen werden, die Shell von PowerShell muss dann jedoch beendet und neu gestartet werden, um das Upgrade abzuschließen und die in $PSVersionTable dargestellten Werte zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="cd3c1-116">Installation der neuesten stabilen Vorschauversion über Homebrew unter macOS 10.12 oder höher</span><span class="sxs-lookup"><span data-stu-id="cd3c1-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="cd3c1-117">Weitere Informationen zu Ansichten finden Sie unter [Info zu Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="cd3c1-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="cd3c1-118">Wenn Sie Homebrew installiert haben, können Sie auch problemlos PowerShell installieren.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-118">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="cd3c1-119">Installieren Sie zunächst [Cask-Versions][cask-versions]. Dies ermöglicht Ihnen das Installieren alternativer Versionen von Cask-Paketen:</span><span class="sxs-lookup"><span data-stu-id="cd3c1-119">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="cd3c1-120">Jetzt können Sie PowerShell installieren:</span><span class="sxs-lookup"><span data-stu-id="cd3c1-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="cd3c1-121">Vergewissern Sie sich abschließend, dass Ihre Installation voll funktionsfähig ist:</span><span class="sxs-lookup"><span data-stu-id="cd3c1-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="cd3c1-122">Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie einfach die Formel für Homebrew, und führen Sie ein Upgrade für PowerShell aus:</span><span class="sxs-lookup"><span data-stu-id="cd3c1-122">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="cd3c1-123">Die oben genannten Befehle können innerhalb eines PowerShell-Hosts (pwsh) aufgerufen werden, die Shell von PowerShell muss dann jedoch beendet und neu angegeben werden, um das Upgrade abzuschließen</span><span class="sxs-lookup"><span data-stu-id="cd3c1-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="cd3c1-124">und die in $PSVersionTable dargestellten Werte zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-124">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="cd3c1-125">Installation über einen direkten Download</span><span class="sxs-lookup"><span data-stu-id="cd3c1-125">Installation via Direct Download</span></span>

<span data-ttu-id="cd3c1-126">Laden Sie das PKG-Paket `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="cd3c1-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="cd3c1-127">über die Seite [Releases][] auf Ihren macOS-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="cd3c1-128">Doppelklicken Sie entweder auf die Datei, und befolgen Sie die Anweisungen, oder installieren Sie das Paket über das Terminal:</span><span class="sxs-lookup"><span data-stu-id="cd3c1-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

<span data-ttu-id="cd3c1-129">Installieren Sie [OpenSSL](#install-openssl), da dies für PowerShell-Remotingfunktionen und CIM-Vorgänge erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-129">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="cd3c1-130">Archive der Binärdateien</span><span class="sxs-lookup"><span data-stu-id="cd3c1-130">Binary Archives</span></span>

<span data-ttu-id="cd3c1-131">`tar.gz`-Archive der PowerShell-Binärdateien werden für die macOS-Plattform zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-131">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="cd3c1-132">Installieren von Archiven der Binärdateien unter macOS</span><span class="sxs-lookup"><span data-stu-id="cd3c1-132">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.1.0/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="cd3c1-133">Installieren Sie [OpenSSL](#install-openssl), da dies für PowerShell-Remotingfunktionen und CIM-Vorgänge erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-133">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="cd3c1-134">Installieren von Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="cd3c1-134">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="cd3c1-135">Installieren von XCode-Befehslzeilentools</span><span class="sxs-lookup"><span data-stu-id="cd3c1-135">Install XCode command line tools</span></span>

```shell
xcode-select -install
```

### <a name="install-openssl"></a><span data-ttu-id="cd3c1-136">Installieren von OpenSSL</span><span class="sxs-lookup"><span data-stu-id="cd3c1-136">Install OpenSSL</span></span>

<span data-ttu-id="cd3c1-137">OpenSSL ist für PowerShell-Remotingfunktionen und CIM-Vorgänge erforderlich.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-137">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>  <span data-ttu-id="cd3c1-138">Die Installation kann über MacPorts oder Brew erfolgen.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-138">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="cd3c1-139">Installieren von OpenSSL über Brew</span><span class="sxs-lookup"><span data-stu-id="cd3c1-139">Install OpenSSL via Brew</span></span>

<span data-ttu-id="cd3c1-140">Weitere Informationen zu Ansichten finden Sie unter [Info zu Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="cd3c1-140">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="cd3c1-141">Führen Sie `brew install openssl` aus, um OpenSSL zu installieren.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-141">Run `brew install openssl` to install OpenSSL.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="cd3c1-142">Installieren von OpenSSL über MacPorts</span><span class="sxs-lookup"><span data-stu-id="cd3c1-142">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="cd3c1-143">Installieren der [XCode-Befehslzeilentools](#install-xcode-command-line-tools)</span><span class="sxs-lookup"><span data-stu-id="cd3c1-143">Instal the [XCode command line tools](#install-xcode-command-line-tools)</span></span>
1. <span data-ttu-id="cd3c1-144">Installieren Sie MacPorts.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-144">Install MacPorts.</span></span>
   <span data-ttu-id="cd3c1-145">Anweisungen finden Sie im [Installationsleitfaden](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="cd3c1-145">See the [installation guide](https://guide.macports.org/chunked/installing.macports.html) if you need instructions.</span></span>
1. <span data-ttu-id="cd3c1-146">Verwenden von MacPorts durch Ausführen von `sudo port selfupdate`</span><span class="sxs-lookup"><span data-stu-id="cd3c1-146">Update MacPorts by running `sudo port selfupdate`</span></span>
1. <span data-ttu-id="cd3c1-147">Aktualisieren von MacPorts-Paketen durch Ausführen von `sudo port upgrade outdated`</span><span class="sxs-lookup"><span data-stu-id="cd3c1-147">Upgrade MacPorts packages by running `sudo port upgrade outdated`</span></span>
1. <span data-ttu-id="cd3c1-148">Installieren von OpenSSL durch Ausführen von `sudo port instal openssl`</span><span class="sxs-lookup"><span data-stu-id="cd3c1-148">Install OpenSSL by running by running `sudo port instal openssl`</span></span>
1. <span data-ttu-id="cd3c1-149">Verknüpfen Sie die Bibliotheken, sodass PowerShell diese verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-149">Link the libraries so that PowerShell can use it.</span></span>

```shell
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="cd3c1-150">Deinstallieren von PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="cd3c1-150">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="cd3c1-151">Wenn Sie PowerShell mit Homebrew installiert haben, gestaltet sich die Deinstallation einfach:</span><span class="sxs-lookup"><span data-stu-id="cd3c1-151">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="cd3c1-152">Wenn Sie PowerShell über einen direkten Download installiert haben, muss PowerShell manuell entfernt werden:</span><span class="sxs-lookup"><span data-stu-id="cd3c1-152">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="cd3c1-153">Lesen Sie den Abschnitt [Pfade](#paths) in diesem Artikel, um zu erfahren, wie Sie zusätzliche PowerShell-Pfade deinstallieren können. Entfernen Sie die gewünschten Pfade mithilfe von `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-153">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="cd3c1-154">Dies ist nicht notwendig, wenn Sie eine Installation mit Homebrew durchgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-154">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="cd3c1-155">Pfade</span><span class="sxs-lookup"><span data-stu-id="cd3c1-155">Paths</span></span>

* <span data-ttu-id="cd3c1-156">`$PSHOME` ist `/usr/local/microsoft/powershell/6.1.0/`.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-156">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="cd3c1-157">Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-157">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="cd3c1-158">Standardprofile werden über `$PSHOME/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-158">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="cd3c1-159">Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-159">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="cd3c1-160">Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-160">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="cd3c1-161">Standardmodule werden über `$PSHOME/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-161">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="cd3c1-162">Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-162">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="cd3c1-163">Die Profile halten sich an die Konfiguration von PowerShell pro Host.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-163">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="cd3c1-164">Das bedeutet, dass hostspezifische Standardprofile in `Microsoft.PowerShell_profile.ps1` am gleichen Speicherort vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-164">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="cd3c1-165">PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter macOs ein.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-165">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="cd3c1-166">Da macOS eine Ableitung von BSD ist, wird das Präfix `/usr/local` anstelle von `/opt` verwendet.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-166">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="cd3c1-167">Daher ist `$PSHOME` gleich `/usr/local/microsoft/powershell/6.1.0/` und der symbolische Link wird unter `/usr/local/bin/pwsh` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="cd3c1-167">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="cd3c1-168">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="cd3c1-168">Additional Resources</span></span>

* <span data-ttu-id="cd3c1-169">[Homebrew-Website][brew]</span><span class="sxs-lookup"><span data-stu-id="cd3c1-169">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="cd3c1-170">[Homebrew-GitHub-Repository][GitHub]</span><span class="sxs-lookup"><span data-stu-id="cd3c1-170">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="cd3c1-171">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="cd3c1-171">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[Releases]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
