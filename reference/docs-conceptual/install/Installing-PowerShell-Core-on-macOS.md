---
title: Installieren von PowerShell unter macOS
description: Informationen zur Installation von PowerShell unter macOS
ms.date: 05/21/2020
ms.openlocfilehash: 32b3ebf3eb4017af41fc1a062f2f0a2e08629a58
ms.sourcegitcommit: fd6a33b9fac973b3554fecfea7f51475e650a606
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2020
ms.locfileid: "83791474"
---
# <a name="installing-powershell-on-macos"></a><span data-ttu-id="bb993-103">Installieren von PowerShell unter macOS</span><span class="sxs-lookup"><span data-stu-id="bb993-103">Installing PowerShell on macOS</span></span>

<span data-ttu-id="bb993-104">PowerShell unterstützt macOS 10.12 und höher.</span><span class="sxs-lookup"><span data-stu-id="bb993-104">PowerShell supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="bb993-105">Sämtliche Pakete sind auf der Seite [Freigaben][] über GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bb993-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="bb993-106">Nachdem Sie das Paket installiert haben, führen Sie `pwsh` über das Terminal aus.</span><span class="sxs-lookup"><span data-stu-id="bb993-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!NOTE]
> <span data-ttu-id="bb993-107">PowerShell 7 ist ein direktes Upgrade, mit dem PowerShell Core 6.x entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="bb993-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="bb993-108">Der Ordner `/usr/local/microsoft/powershell/6` wird durch `/usr/local/microsoft/powershell/7` ersetzt.</span><span class="sxs-lookup"><span data-stu-id="bb993-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="bb993-109">Wenn Sie PowerShell 6 und PowerShell 7 parallel ausführen müssen, installieren Sie PowerShell 6 mithilfe der [binary archive](#binary-archives)-Methode neu.</span><span class="sxs-lookup"><span data-stu-id="bb993-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

## <a name="about-brew"></a><span data-ttu-id="bb993-110">Informationen zu Brew</span><span class="sxs-lookup"><span data-stu-id="bb993-110">About Brew</span></span>

<span data-ttu-id="bb993-111">Bei [Homebrew][brew] handelt es sich um den bevorzugten Paket-Manager für macOS.</span><span class="sxs-lookup"><span data-stu-id="bb993-111">[Homebrew][brew] is the preferred package manager for macOS.</span></span> <span data-ttu-id="bb993-112">Wenn der Befehl `brew` nicht gefunden wird, müssen Sie Homebrew installieren, indem Sie [die entsprechenden Anweisungen][brew] ausführen.</span><span class="sxs-lookup"><span data-stu-id="bb993-112">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span> <span data-ttu-id="bb993-113">Andernfalls können Sie PowerShell über [Direkter Download](#installation-via-direct-download) oder aus [Archive der Binärdateien](#binary-archives) installieren.</span><span class="sxs-lookup"><span data-stu-id="bb993-113">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="bb993-114">Installation des neuesten stabilen Release über Homebrew unter macOS 10.12 oder höher</span><span class="sxs-lookup"><span data-stu-id="bb993-114">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="bb993-115">Weitere Informationen zu Brew finden Sie unter [Info zu Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="bb993-115">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="bb993-116">Jetzt können Sie PowerShell installieren:</span><span class="sxs-lookup"><span data-stu-id="bb993-116">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="bb993-117">Vergewissern Sie sich abschließend, dass Ihre Installation voll funktionsfähig ist:</span><span class="sxs-lookup"><span data-stu-id="bb993-117">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="bb993-118">Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie die Formeln für Homebrew, und führen Sie ein Upgrade für PowerShell aus:</span><span class="sxs-lookup"><span data-stu-id="bb993-118">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="bb993-119">Die oben genannten Befehle können innerhalb eines PowerShell-Hosts (pwsh) aufgerufen werden. Allerdings muss dann die Shell von PowerShell beendet und neu gestartet werden, um das Upgrade abzuschließen und die in `$PSVersionTable` dargestellten Werte zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="bb993-119">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="bb993-120">Installation der neuesten Vorschauversion über Homebrew unter macOS 10.12 oder höher</span><span class="sxs-lookup"><span data-stu-id="bb993-120">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="bb993-121">Weitere Informationen zu Brew finden Sie unter [Info zu Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="bb993-121">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="bb993-122">Nachdem Sie Homebrew installiert haben, können Sie PowerShell installieren.</span><span class="sxs-lookup"><span data-stu-id="bb993-122">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="bb993-123">Installieren Sie zunächst das Paket [Cask-Versions][cask-versions]. Dies ermöglicht Ihnen das Installieren alternativer Versionen von Cask-Paketen:</span><span class="sxs-lookup"><span data-stu-id="bb993-123">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="bb993-124">Jetzt können Sie PowerShell installieren:</span><span class="sxs-lookup"><span data-stu-id="bb993-124">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="bb993-125">Vergewissern Sie sich abschließend, dass Ihre Installation voll funktionsfähig ist:</span><span class="sxs-lookup"><span data-stu-id="bb993-125">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="bb993-126">Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie die Formeln für Homebrew, und führen Sie ein Upgrade für PowerShell aus:</span><span class="sxs-lookup"><span data-stu-id="bb993-126">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="bb993-127">Die oben genannten Befehle können innerhalb eines PowerShell-Hosts (pwsh) aufgerufen werden, die Shell von PowerShell muss dann jedoch beendet und neu angegeben werden, um das Upgrade abzuschließen</span><span class="sxs-lookup"><span data-stu-id="bb993-127">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="bb993-128">und die in `$PSVersionTable` dargestellten Werte zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="bb993-128">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="bb993-129">Installation über einen direkten Download</span><span class="sxs-lookup"><span data-stu-id="bb993-129">Installation via Direct Download</span></span>

<span data-ttu-id="bb993-130">Laden Sie das PKG-Paket `powershell-lts-7.0.1-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="bb993-130">Download the PKG package `powershell-lts-7.0.1-osx-x64.pkg`</span></span>
<span data-ttu-id="bb993-131">über die Seite [Freigaben][] auf Ihren macOS-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="bb993-131">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="bb993-132">Doppelklicken Sie entweder auf die Datei, und befolgen Sie die Anweisungen, oder installieren Sie das Paket über das Terminal:</span><span class="sxs-lookup"><span data-stu-id="bb993-132">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-lts-7.0.1-osx-x64.pkg -target /
```

<span data-ttu-id="bb993-133">Installieren Sie [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="bb993-133">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="bb993-134">OpenSSL ist für PowerShell-Remotingfunktionen und CIM-Vorgänge erforderlich.</span><span class="sxs-lookup"><span data-stu-id="bb993-134">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="bb993-135">Installieren als globales .NET-Tool</span><span class="sxs-lookup"><span data-stu-id="bb993-135">Install as a .NET Global tool</span></span>

<span data-ttu-id="bb993-136">Wenn Sie das [.NET Core SDK](/dotnet/core/sdk) bereits installiert haben, können Sie PowerShell einfach als [globales .NET-Tool](/dotnet/core/tools/global-tools) installieren.</span><span class="sxs-lookup"><span data-stu-id="bb993-136">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="bb993-137">Der .NET-Toolinstaller fügt `~/.dotnet/tools` Ihrer `PATH`-Umgebungsvariablen hinzu.</span><span class="sxs-lookup"><span data-stu-id="bb993-137">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="bb993-138">Die aktuell ausgeführte Shell verfügt jedoch nicht über den aktualisierten `PATH`.</span><span class="sxs-lookup"><span data-stu-id="bb993-138">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="bb993-139">Sie sollten PowerShell über eine neue Shell starten können, indem Sie `pwsh` eingeben.</span><span class="sxs-lookup"><span data-stu-id="bb993-139">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="bb993-140">Archive der Binärdateien</span><span class="sxs-lookup"><span data-stu-id="bb993-140">Binary Archives</span></span>

<span data-ttu-id="bb993-141">`tar.gz`-Archive der PowerShell-Binärdateien werden für die macOS-Plattform zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="bb993-141">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="bb993-142">Installieren von Archiven der Binärdateien unter macOS</span><span class="sxs-lookup"><span data-stu-id="bb993-142">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-7.0.1-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.0.1

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.0.1

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.0.1/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.0.1/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="bb993-143">Installieren Sie [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="bb993-143">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="bb993-144">OpenSSL ist für PowerShell-Remotingfunktionen und CIM-Vorgänge erforderlich.</span><span class="sxs-lookup"><span data-stu-id="bb993-144">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="bb993-145">Installieren von Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="bb993-145">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="bb993-146">Installieren von XCode-Befehslzeilentools</span><span class="sxs-lookup"><span data-stu-id="bb993-146">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="bb993-147">Installieren von OpenSSL</span><span class="sxs-lookup"><span data-stu-id="bb993-147">Install OpenSSL</span></span>

<span data-ttu-id="bb993-148">OpenSSL ist für PowerShell-Remotingfunktionen und CIM-Vorgänge erforderlich.</span><span class="sxs-lookup"><span data-stu-id="bb993-148">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="bb993-149">Die Installation kann über MacPorts erfolgen.</span><span class="sxs-lookup"><span data-stu-id="bb993-149">You can install via MacPorts.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="bb993-150">Installieren von OpenSSL über MacPorts</span><span class="sxs-lookup"><span data-stu-id="bb993-150">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="bb993-151">Installieren Sie die [XCode-Befehlszeilentools](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="bb993-151">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="bb993-152">Installieren Sie MacPorts.</span><span class="sxs-lookup"><span data-stu-id="bb993-152">Install MacPorts.</span></span>
   <span data-ttu-id="bb993-153">Wenn Sie Anleitungen dazu benötigen, lesen Sie das [Installationshandbuch](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="bb993-153">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="bb993-154">Aktualisieren Sie MacPorts durch Ausführen von `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="bb993-154">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="bb993-155">Führen Sie eine Upgrade von MacPorts-Paketen durch Ausführen von `sudo port upgrade outdated` durch.</span><span class="sxs-lookup"><span data-stu-id="bb993-155">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="bb993-156">Installieren Sie OpenSSL durch Ausführen von `sudo port install openssl10`.</span><span class="sxs-lookup"><span data-stu-id="bb993-156">Install OpenSSL by running `sudo port install openssl10`.</span></span>
1. <span data-ttu-id="bb993-157">Verknüpfen Sie die Bibliotheken, um sie PowerShell zur Verfügung zu stellen:</span><span class="sxs-lookup"><span data-stu-id="bb993-157">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib/openssl-1.0 /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell"></a><span data-ttu-id="bb993-158">Deinstallieren von PowerShell</span><span class="sxs-lookup"><span data-stu-id="bb993-158">Uninstalling PowerShell</span></span>

<span data-ttu-id="bb993-159">Wenn Sie PowerShell mit Homebrew installiert haben, verwenden Sie den folgenden Befehl zum Deinstallieren:</span><span class="sxs-lookup"><span data-stu-id="bb993-159">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="bb993-160">Wenn Sie PowerShell über einen direkten Download installiert haben, muss PowerShell manuell entfernt werden:</span><span class="sxs-lookup"><span data-stu-id="bb993-160">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="bb993-161">Lesen Sie den Abschnitt [Pfade](#paths) in diesem Artikel, um zu erfahren, wie Sie zusätzliche PowerShell-Pfade deinstallieren können. Entfernen Sie die Pfade mithilfe von `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="bb993-161">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="bb993-162">Dies ist nicht notwendig, wenn Sie eine Installation mit Homebrew durchgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="bb993-162">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="bb993-163">Paths</span><span class="sxs-lookup"><span data-stu-id="bb993-163">Paths</span></span>

* <span data-ttu-id="bb993-164">`$PSHOME` ist `/usr/local/microsoft/powershell/7.0.1/`.</span><span class="sxs-lookup"><span data-stu-id="bb993-164">`$PSHOME` is `/usr/local/microsoft/powershell/7.0.1/`</span></span>
* <span data-ttu-id="bb993-165">Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="bb993-165">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="bb993-166">Standardprofile werden über `$PSHOME/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="bb993-166">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="bb993-167">Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="bb993-167">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="bb993-168">Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="bb993-168">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="bb993-169">Standardmodule werden über `$PSHOME/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="bb993-169">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="bb993-170">Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="bb993-170">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="bb993-171">Die Profile halten sich an die Konfiguration von PowerShell pro Host.</span><span class="sxs-lookup"><span data-stu-id="bb993-171">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="bb993-172">Dies bedeutet, dass hostspezifische Standardprofile in `Microsoft.PowerShell_profile.ps1` am gleichen Speicherort vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="bb993-172">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="bb993-173">PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter macOs ein.</span><span class="sxs-lookup"><span data-stu-id="bb993-173">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="bb993-174">Da macOS eine Ableitung von BSD ist, wird das Präfix `/usr/local` anstelle von `/opt` verwendet.</span><span class="sxs-lookup"><span data-stu-id="bb993-174">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="bb993-175">Daher ist `$PSHOME` gleich `/usr/local/microsoft/powershell/7.0.1/`, und der symbolische Link wird unter `/usr/local/bin/pwsh` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="bb993-175">So, `$PSHOME` is `/usr/local/microsoft/powershell/7.0.1/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="bb993-176">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="bb993-176">Additional Resources</span></span>

* <span data-ttu-id="bb993-177">[Homebrew-Website][brew]</span><span class="sxs-lookup"><span data-stu-id="bb993-177">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="bb993-178">[Homebrew-GitHub-Repository][GitHub]</span><span class="sxs-lookup"><span data-stu-id="bb993-178">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="bb993-179">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="bb993-179">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[Freigaben]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
