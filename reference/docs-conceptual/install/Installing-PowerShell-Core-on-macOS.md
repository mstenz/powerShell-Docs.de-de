---
title: Installieren von PowerShell unter macOS
description: Informationen zur Installation von PowerShell unter macOS
ms.date: 12/12/2018
ms.openlocfilehash: 3a5e71d0f69d0c39f9b7f3fa667863d7ec0a31dd
ms.sourcegitcommit: bf71c8c5e2a4fc7d5c3a67a537db1285089d03a7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395010"
---
# <a name="installing-powershell-on-macos"></a><span data-ttu-id="9eaf5-103">Installieren von PowerShell unter macOS</span><span class="sxs-lookup"><span data-stu-id="9eaf5-103">Installing PowerShell on macOS</span></span>

<span data-ttu-id="9eaf5-104">PowerShell unterstützt macOS 10.12 und höher.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-104">PowerShell supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="9eaf5-105">Sämtliche Pakete sind auf der Seite [Freigaben][] über GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="9eaf5-106">Nachdem Sie das Paket installiert haben, führen Sie `pwsh` über das Terminal aus.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!NOTE]
> <span data-ttu-id="9eaf5-107">PowerShell 7 ist ein direktes Upgrade, mit dem PowerShell Core 6.x entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="9eaf5-108">Der Ordner `/usr/local/microsoft/powershell/6` wird durch `/usr/local/microsoft/powershell/7` ersetzt.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="9eaf5-109">Wenn Sie PowerShell 6 und PowerShell 7 parallel ausführen müssen, installieren Sie PowerShell 6 mithilfe der [binary archive](#binary-archives)-Methode neu.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

## <a name="about-brew"></a><span data-ttu-id="9eaf5-110">Informationen zu Brew</span><span class="sxs-lookup"><span data-stu-id="9eaf5-110">About Brew</span></span>

<span data-ttu-id="9eaf5-111">Bei [Homebrew][brew] handelt es sich um den bevorzugten Paket-Manager für macOS.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-111">[Homebrew][brew] is the preferred package manager for macOS.</span></span> <span data-ttu-id="9eaf5-112">Wenn der Befehl `brew` nicht gefunden wird, müssen Sie Homebrew installieren, indem Sie [die entsprechenden Anweisungen][brew] ausführen.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-112">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span> <span data-ttu-id="9eaf5-113">Andernfalls können Sie PowerShell über [Direkter Download](#installation-via-direct-download) oder aus [Archive der Binärdateien](#binary-archives) installieren.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-113">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="9eaf5-114">Installation des neuesten stabilen Release über Homebrew unter macOS 10.12 oder höher</span><span class="sxs-lookup"><span data-stu-id="9eaf5-114">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="9eaf5-115">Weitere Informationen zu Brew finden Sie unter [Info zu Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="9eaf5-115">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="9eaf5-116">Jetzt können Sie PowerShell installieren:</span><span class="sxs-lookup"><span data-stu-id="9eaf5-116">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="9eaf5-117">Vergewissern Sie sich abschließend, dass Ihre Installation voll funktionsfähig ist:</span><span class="sxs-lookup"><span data-stu-id="9eaf5-117">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="9eaf5-118">Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie die Formeln für Homebrew, und führen Sie ein Upgrade für PowerShell aus:</span><span class="sxs-lookup"><span data-stu-id="9eaf5-118">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="9eaf5-119">Die oben genannten Befehle können innerhalb eines PowerShell-Hosts (pwsh) aufgerufen werden. Allerdings muss dann die Shell von PowerShell beendet und neu gestartet werden, um das Upgrade abzuschließen und die in `$PSVersionTable` dargestellten Werte zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-119">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="9eaf5-120">Installation der neuesten Vorschauversion über Homebrew unter macOS 10.12 oder höher</span><span class="sxs-lookup"><span data-stu-id="9eaf5-120">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="9eaf5-121">Weitere Informationen zu Brew finden Sie unter [Info zu Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="9eaf5-121">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="9eaf5-122">Nachdem Sie Homebrew installiert haben, können Sie PowerShell installieren.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-122">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="9eaf5-123">Installieren Sie zunächst das Paket [Cask-Versions][cask-versions]. Dies ermöglicht Ihnen das Installieren alternativer Versionen von Cask-Paketen:</span><span class="sxs-lookup"><span data-stu-id="9eaf5-123">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="9eaf5-124">Jetzt können Sie PowerShell installieren:</span><span class="sxs-lookup"><span data-stu-id="9eaf5-124">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="9eaf5-125">Vergewissern Sie sich abschließend, dass Ihre Installation voll funktionsfähig ist:</span><span class="sxs-lookup"><span data-stu-id="9eaf5-125">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="9eaf5-126">Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie die Formeln für Homebrew, und führen Sie ein Upgrade für PowerShell aus:</span><span class="sxs-lookup"><span data-stu-id="9eaf5-126">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="9eaf5-127">Die oben genannten Befehle können innerhalb eines PowerShell-Hosts (pwsh) aufgerufen werden, die Shell von PowerShell muss dann jedoch beendet und neu angegeben werden, um das Upgrade abzuschließen</span><span class="sxs-lookup"><span data-stu-id="9eaf5-127">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="9eaf5-128">und die in `$PSVersionTable` dargestellten Werte zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-128">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="9eaf5-129">Installation über einen direkten Download</span><span class="sxs-lookup"><span data-stu-id="9eaf5-129">Installation via Direct Download</span></span>

<span data-ttu-id="9eaf5-130">Laden Sie das PKG-Paket `powershell-lts-7.0.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="9eaf5-130">Download the PKG package `powershell-lts-7.0.0-osx-x64.pkg`</span></span>
<span data-ttu-id="9eaf5-131">über die Seite [Freigaben][] auf Ihren macOS-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-131">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="9eaf5-132">Doppelklicken Sie entweder auf die Datei, und befolgen Sie die Anweisungen, oder installieren Sie das Paket über das Terminal:</span><span class="sxs-lookup"><span data-stu-id="9eaf5-132">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-lts-7.0.0-osx-x64.pkg -target /
```

<span data-ttu-id="9eaf5-133">Installieren Sie [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="9eaf5-133">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="9eaf5-134">OpenSSL ist für PowerShell-Remotingfunktionen und CIM-Vorgänge erforderlich.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-134">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="9eaf5-135">Installieren als globales .NET-Tool</span><span class="sxs-lookup"><span data-stu-id="9eaf5-135">Install as a .NET Global tool</span></span>

<span data-ttu-id="9eaf5-136">Wenn Sie das [.NET Core SDK](/dotnet/core/sdk) bereits installiert haben, können Sie PowerShell einfach als [globales .NET-Tool](/dotnet/core/tools/global-tools) installieren.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-136">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="9eaf5-137">Der .NET-Toolinstaller fügt `~/.dotnet/tools` Ihrer `PATH`-Umgebungsvariablen hinzu.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-137">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="9eaf5-138">Die aktuell ausgeführte Shell verfügt jedoch nicht über den aktualisierten `PATH`.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-138">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="9eaf5-139">Sie sollten PowerShell über eine neue Shell starten können, indem Sie `pwsh` eingeben.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-139">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="9eaf5-140">Archive der Binärdateien</span><span class="sxs-lookup"><span data-stu-id="9eaf5-140">Binary Archives</span></span>

<span data-ttu-id="9eaf5-141">`tar.gz`-Archive der PowerShell-Binärdateien werden für die macOS-Plattform zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-141">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="9eaf5-142">Installieren von Archiven der Binärdateien unter macOS</span><span class="sxs-lookup"><span data-stu-id="9eaf5-142">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.0.0/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="9eaf5-143">Installieren Sie [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="9eaf5-143">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="9eaf5-144">OpenSSL ist für PowerShell-Remotingfunktionen und CIM-Vorgänge erforderlich.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-144">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="9eaf5-145">Installieren von Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="9eaf5-145">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="9eaf5-146">Installieren von XCode-Befehslzeilentools</span><span class="sxs-lookup"><span data-stu-id="9eaf5-146">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="9eaf5-147">Installieren von OpenSSL</span><span class="sxs-lookup"><span data-stu-id="9eaf5-147">Install OpenSSL</span></span>

<span data-ttu-id="9eaf5-148">OpenSSL ist für PowerShell-Remotingfunktionen und CIM-Vorgänge erforderlich.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-148">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="9eaf5-149">Die Installation kann über MacPorts oder Brew erfolgen.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-149">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="9eaf5-150">Installieren von OpenSSL über Brew</span><span class="sxs-lookup"><span data-stu-id="9eaf5-150">Install OpenSSL via Brew</span></span>

<span data-ttu-id="9eaf5-151">Weitere Informationen zu Brew finden Sie unter [Info zu Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="9eaf5-151">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="9eaf5-152">Führen Sie `brew install openssl` aus, um OpenSSL zu installieren.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-152">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="9eaf5-153">Installieren von OpenSSL über MacPorts</span><span class="sxs-lookup"><span data-stu-id="9eaf5-153">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="9eaf5-154">Installieren Sie die [XCode-Befehlszeilentools](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="9eaf5-154">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="9eaf5-155">Installieren Sie MacPorts.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-155">Install MacPorts.</span></span>
   <span data-ttu-id="9eaf5-156">Wenn Sie Anleitungen dazu benötigen, lesen Sie das [Installationshandbuch](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="9eaf5-156">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="9eaf5-157">Aktualisieren Sie MacPorts durch Ausführen von `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-157">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="9eaf5-158">Führen Sie eine Upgrade von MacPorts-Paketen durch Ausführen von `sudo port upgrade outdated` durch.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-158">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="9eaf5-159">Installieren Sie OpenSSL durch Ausführen von `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-159">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="9eaf5-160">Verknüpfen Sie die Bibliotheken, um sie PowerShell zur Verfügung zu stellen:</span><span class="sxs-lookup"><span data-stu-id="9eaf5-160">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell"></a><span data-ttu-id="9eaf5-161">Deinstallieren von PowerShell</span><span class="sxs-lookup"><span data-stu-id="9eaf5-161">Uninstalling PowerShell</span></span>

<span data-ttu-id="9eaf5-162">Wenn Sie PowerShell mit Homebrew installiert haben, verwenden Sie den folgenden Befehl zum Deinstallieren:</span><span class="sxs-lookup"><span data-stu-id="9eaf5-162">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="9eaf5-163">Wenn Sie PowerShell über einen direkten Download installiert haben, muss PowerShell manuell entfernt werden:</span><span class="sxs-lookup"><span data-stu-id="9eaf5-163">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="9eaf5-164">Lesen Sie den Abschnitt [Pfade](#paths) in diesem Artikel, um zu erfahren, wie Sie zusätzliche PowerShell-Pfade deinstallieren können. Entfernen Sie die Pfade mithilfe von `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-164">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="9eaf5-165">Dies ist nicht notwendig, wenn Sie eine Installation mit Homebrew durchgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-165">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="9eaf5-166">Paths</span><span class="sxs-lookup"><span data-stu-id="9eaf5-166">Paths</span></span>

* <span data-ttu-id="9eaf5-167">`$PSHOME` ist `/usr/local/microsoft/powershell/7.0.0/`.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-167">`$PSHOME` is `/usr/local/microsoft/powershell/7.0.0/`</span></span>
* <span data-ttu-id="9eaf5-168">Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-168">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="9eaf5-169">Standardprofile werden über `$PSHOME/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-169">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="9eaf5-170">Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-170">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="9eaf5-171">Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-171">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="9eaf5-172">Standardmodule werden über `$PSHOME/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-172">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="9eaf5-173">Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-173">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="9eaf5-174">Die Profile halten sich an die Konfiguration von PowerShell pro Host.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-174">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="9eaf5-175">Dies bedeutet, dass hostspezifische Standardprofile in `Microsoft.PowerShell_profile.ps1` am gleichen Speicherort vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-175">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="9eaf5-176">PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter macOs ein.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-176">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="9eaf5-177">Da macOS eine Ableitung von BSD ist, wird das Präfix `/usr/local` anstelle von `/opt` verwendet.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-177">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="9eaf5-178">Daher ist `$PSHOME` gleich `/usr/local/microsoft/powershell/7.0.0/`, und der symbolische Link wird unter `/usr/local/bin/pwsh` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="9eaf5-178">So, `$PSHOME` is `/usr/local/microsoft/powershell/7.0.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9eaf5-179">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="9eaf5-179">Additional Resources</span></span>

* <span data-ttu-id="9eaf5-180">[Homebrew-Website][brew]</span><span class="sxs-lookup"><span data-stu-id="9eaf5-180">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="9eaf5-181">[Homebrew-GitHub-Repository][GitHub]</span><span class="sxs-lookup"><span data-stu-id="9eaf5-181">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="9eaf5-182">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="9eaf5-182">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[Freigaben]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
