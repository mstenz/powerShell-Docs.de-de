---
title: Installieren von PowerShell Core unter macOS
description: Informationen zur Installation von PowerShell Core unter macOS
ms.date: 12/12/2018
ms.openlocfilehash: 91e64cace7d4ed988da56109dde9bf2a80528eb4
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401433"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="30d98-103">Installieren von PowerShell Core unter macOS</span><span class="sxs-lookup"><span data-stu-id="30d98-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="30d98-104">PowerShell Core unterstützt macOs 10.12 und höher.</span><span class="sxs-lookup"><span data-stu-id="30d98-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="30d98-105">Sämtliche Pakete sind auf der Seite [Freigaben][] über GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="30d98-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="30d98-106">Nachdem das Paket installiert ist, führen Sie `pwsh` über das Terminal.</span><span class="sxs-lookup"><span data-stu-id="30d98-106">After the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="30d98-107">Informationen zu Brew</span><span class="sxs-lookup"><span data-stu-id="30d98-107">About Brew</span></span>

<span data-ttu-id="30d98-108">Bei [Homebrew][brew] handelt es sich um den bevorzugten Paket-Manager für macOS.</span><span class="sxs-lookup"><span data-stu-id="30d98-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="30d98-109">Wenn der Befehl `brew` nicht gefunden wird, müssen Sie Homebrew installieren, indem Sie [die entsprechenden Anweisungen][brew] ausführen.</span><span class="sxs-lookup"><span data-stu-id="30d98-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="30d98-110">Installation des neuesten stabilen Release über Homebrew unter macOS 10.12 oder höher</span><span class="sxs-lookup"><span data-stu-id="30d98-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="30d98-111">Weitere Informationen zu Ansichten finden Sie unter [Info zu Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="30d98-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="30d98-112">Jetzt können Sie PowerShell installieren:</span><span class="sxs-lookup"><span data-stu-id="30d98-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="30d98-113">Vergewissern Sie sich abschließend, dass Ihre Installation voll funktionsfähig ist:</span><span class="sxs-lookup"><span data-stu-id="30d98-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="30d98-114">Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie Homebrews-Formeln, und aktualisieren Sie PowerShell:</span><span class="sxs-lookup"><span data-stu-id="30d98-114">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="30d98-115">Die oben genannten Befehle können von innerhalb eines Hosts-PowerShell (Pwsh) aufgerufen werden, aber dann muss die PowerShell-Shell wurde beendet und neu gestartet, um das Upgrade abzuschließen, und aktualisieren die Werte im `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="30d98-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="30d98-116">Installation der neuesten stabilen Vorschauversion über Homebrew unter macOS 10.12 oder höher</span><span class="sxs-lookup"><span data-stu-id="30d98-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="30d98-117">Weitere Informationen zu Ansichten finden Sie unter [Info zu Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="30d98-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="30d98-118">Nachdem Sie Homebrew installiert haben, können Sie PowerShell installieren.</span><span class="sxs-lookup"><span data-stu-id="30d98-118">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="30d98-119">Installieren Sie zunächst die [Cask-Versionen] [ cask-versions] Paket, das Sie alternative Versionen Cask-Pakete installieren kann:</span><span class="sxs-lookup"><span data-stu-id="30d98-119">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="30d98-120">Jetzt können Sie PowerShell installieren:</span><span class="sxs-lookup"><span data-stu-id="30d98-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="30d98-121">Vergewissern Sie sich abschließend, dass Ihre Installation voll funktionsfähig ist:</span><span class="sxs-lookup"><span data-stu-id="30d98-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="30d98-122">Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie Homebrews-Formeln, und aktualisieren Sie PowerShell:</span><span class="sxs-lookup"><span data-stu-id="30d98-122">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="30d98-123">Die oben genannten Befehle können innerhalb eines PowerShell-Hosts (pwsh) aufgerufen werden, die Shell von PowerShell muss dann jedoch beendet und neu angegeben werden, um das Upgrade abzuschließen</span><span class="sxs-lookup"><span data-stu-id="30d98-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="30d98-124">und aktualisieren Sie die Werte im `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="30d98-124">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="30d98-125">Installation über einen direkten Download</span><span class="sxs-lookup"><span data-stu-id="30d98-125">Installation via Direct Download</span></span>

<span data-ttu-id="30d98-126">Laden Sie das PKG-Paket `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="30d98-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="30d98-127">über die Seite [Freigaben][] auf Ihren macOS-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="30d98-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="30d98-128">Doppelklicken Sie entweder auf die Datei, und befolgen Sie die Anweisungen, oder installieren Sie das Paket über das Terminal:</span><span class="sxs-lookup"><span data-stu-id="30d98-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

<span data-ttu-id="30d98-129">Installieren Sie [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="30d98-129">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="30d98-130">OpenSSL ist für PowerShell-Remotingfunktionen und CIM-Vorgänge erforderlich.</span><span class="sxs-lookup"><span data-stu-id="30d98-130">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="30d98-131">Archive der Binärdateien</span><span class="sxs-lookup"><span data-stu-id="30d98-131">Binary Archives</span></span>

<span data-ttu-id="30d98-132">`tar.gz`-Archive der PowerShell-Binärdateien werden für die macOS-Plattform zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="30d98-132">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="30d98-133">Installieren von Archiven der Binärdateien unter macOS</span><span class="sxs-lookup"><span data-stu-id="30d98-133">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="30d98-134">Installieren Sie [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="30d98-134">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="30d98-135">OpenSSL ist für PowerShell-Remotingfunktionen und CIM-Vorgänge erforderlich.</span><span class="sxs-lookup"><span data-stu-id="30d98-135">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="30d98-136">Installieren von Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="30d98-136">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="30d98-137">Installieren von XCode-Befehslzeilentools</span><span class="sxs-lookup"><span data-stu-id="30d98-137">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="30d98-138">Installieren von OpenSSL</span><span class="sxs-lookup"><span data-stu-id="30d98-138">Install OpenSSL</span></span>

<span data-ttu-id="30d98-139">OpenSSL ist für PowerShell-Remotingfunktionen und CIM-Vorgänge erforderlich.</span><span class="sxs-lookup"><span data-stu-id="30d98-139">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="30d98-140">Die Installation kann über MacPorts oder Brew erfolgen.</span><span class="sxs-lookup"><span data-stu-id="30d98-140">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="30d98-141">Installieren von OpenSSL über Brew</span><span class="sxs-lookup"><span data-stu-id="30d98-141">Install OpenSSL via Brew</span></span>

<span data-ttu-id="30d98-142">Weitere Informationen zu Ansichten finden Sie unter [Info zu Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="30d98-142">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="30d98-143">Führen Sie zum Installieren von OpenSSL `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="30d98-143">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="30d98-144">Installieren von OpenSSL über MacPorts</span><span class="sxs-lookup"><span data-stu-id="30d98-144">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="30d98-145">Installieren Sie die [XCode-Befehlszeilentools](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="30d98-145">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="30d98-146">Installieren Sie MacPorts.</span><span class="sxs-lookup"><span data-stu-id="30d98-146">Install MacPorts.</span></span>
   <span data-ttu-id="30d98-147">Wenn Sie Anweisungen benötigen, lesen Sie die [Installationshandbuch](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="30d98-147">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="30d98-148">Aktualisieren Sie MacPorts durch Ausführen von `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="30d98-148">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="30d98-149">Führen Sie eine Upgrade von MacPorts-Paketen durch Ausführen von `sudo port upgrade outdated` durch.</span><span class="sxs-lookup"><span data-stu-id="30d98-149">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="30d98-150">Installieren Sie OpenSSL durch Ausführen von `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="30d98-150">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="30d98-151">Verknüpfen Sie die Bibliotheken aus, um sie zu PowerShell zur Verfügung zu stellen:</span><span class="sxs-lookup"><span data-stu-id="30d98-151">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="30d98-152">Deinstallieren von PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="30d98-152">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="30d98-153">Wenn Sie PowerShell mit Homebrew installiert haben, verwenden Sie den folgenden Befehl zum Deinstallieren:</span><span class="sxs-lookup"><span data-stu-id="30d98-153">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="30d98-154">Wenn Sie PowerShell über einen direkten Download installiert haben, muss PowerShell manuell entfernt werden:</span><span class="sxs-lookup"><span data-stu-id="30d98-154">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="30d98-155">Um zusätzliche PowerShell-Pfade zu entfernen, finden Sie in der [Pfade](#paths) in diesem Dokument im Abschnitt, und entfernen Sie die Pfade mit `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="30d98-155">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="30d98-156">Dies ist nicht notwendig, wenn Sie eine Installation mit Homebrew durchgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="30d98-156">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="30d98-157">Pfade</span><span class="sxs-lookup"><span data-stu-id="30d98-157">Paths</span></span>

* <span data-ttu-id="30d98-158">`$PSHOME` ist `/usr/local/microsoft/powershell/6.1.0/`.</span><span class="sxs-lookup"><span data-stu-id="30d98-158">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="30d98-159">Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="30d98-159">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="30d98-160">Standardprofile werden über `$PSHOME/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="30d98-160">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="30d98-161">Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="30d98-161">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="30d98-162">Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="30d98-162">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="30d98-163">Standardmodule werden über `$PSHOME/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="30d98-163">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="30d98-164">Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="30d98-164">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="30d98-165">Die Profile halten sich an die Konfiguration von PowerShell pro Host.</span><span class="sxs-lookup"><span data-stu-id="30d98-165">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="30d98-166">Damit das Standardprofil für die hostspezifische am vorhanden ist `Microsoft.PowerShell_profile.ps1` am gleichen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="30d98-166">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="30d98-167">PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter macOs ein.</span><span class="sxs-lookup"><span data-stu-id="30d98-167">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="30d98-168">Da macOS eine Ableitung von BSD ist, wird das Präfix `/usr/local` anstelle von `/opt` verwendet.</span><span class="sxs-lookup"><span data-stu-id="30d98-168">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="30d98-169">Also `$PSHOME` ist `/usr/local/microsoft/powershell/6.1.0/`, und die symbolische Verknüpfung befindet sich am `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="30d98-169">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="30d98-170">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="30d98-170">Additional Resources</span></span>

* <span data-ttu-id="30d98-171">[Homebrew-Website][brew]</span><span class="sxs-lookup"><span data-stu-id="30d98-171">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="30d98-172">[Homebrew-GitHub-Repository][GitHub]</span><span class="sxs-lookup"><span data-stu-id="30d98-172">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="30d98-173">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="30d98-173">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[Freigaben]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
