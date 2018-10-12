---
title: Installieren von PowerShell Core unter macOS
description: Informationen zur Installation von PowerShell Core unter macOS
ms.date: 08/06/2018
ms.openlocfilehash: 042c933dfa83f3ab52e315036e4f817145116d00
ms.sourcegitcommit: aa41249f153bbc6e11667ade60c878980c15abc6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2018
ms.locfileid: "45611486"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="591df-103">Installieren von PowerShell Core unter macOS</span><span class="sxs-lookup"><span data-stu-id="591df-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="591df-104">PowerShell Core unterstützt macOs 10.12 und höher.</span><span class="sxs-lookup"><span data-stu-id="591df-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="591df-105">Sämtliche Pakete sind auf der Seite [Releases][] über GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="591df-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="591df-106">Führen Sie `pwsh` über das Terminal aus, nachdem Sie das Paket installiert haben.</span><span class="sxs-lookup"><span data-stu-id="591df-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="591df-107">Installation des neuesten stabilen Release über Homebrew unter macOS 10.12 oder höher</span><span class="sxs-lookup"><span data-stu-id="591df-107">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="591df-108">Bei [Homebrew][brew] handelt es sich um den bevorzugten Paket-Manager für macOS.</span><span class="sxs-lookup"><span data-stu-id="591df-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="591df-109">Wenn der Befehl `brew` nicht gefunden wird, müssen Sie Homebrew installieren, indem Sie [die entsprechenden Anweisungen][brew] ausführen.</span><span class="sxs-lookup"><span data-stu-id="591df-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="591df-110">Jetzt können Sie PowerShell installieren:</span><span class="sxs-lookup"><span data-stu-id="591df-110">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="591df-111">Vergewissern Sie sich abschließend, dass Ihre Installation voll funktionsfähig ist:</span><span class="sxs-lookup"><span data-stu-id="591df-111">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="591df-112">Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie einfach die Formel für Homebrew, und führen Sie ein Upgrade für PowerShell aus:</span><span class="sxs-lookup"><span data-stu-id="591df-112">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="591df-113">Die oben genannten Befehle können innerhalb eines PowerShell-Hosts (pwsh) aufgerufen werden, die Shell von PowerShell muss dann jedoch beendet und neu angegeben werden, um das Upgrade abzuschließen</span><span class="sxs-lookup"><span data-stu-id="591df-113">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="591df-114">und die in $PSVersionTable dargestellten Werte zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="591df-114">and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="591df-115">Installation der neuesten stabilen Vorschauversion über Homebrew unter macOS 10.12 oder höher</span><span class="sxs-lookup"><span data-stu-id="591df-115">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="591df-116">Bei [Homebrew][brew] handelt es sich um den bevorzugten Paket-Manager für macOS.</span><span class="sxs-lookup"><span data-stu-id="591df-116">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="591df-117">Wenn der Befehl `brew` nicht gefunden wird, müssen Sie Homebrew installieren, indem Sie [die entsprechenden Anweisungen][brew] ausführen.</span><span class="sxs-lookup"><span data-stu-id="591df-117">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="591df-118">Wenn Sie Homebrew installiert haben, können Sie auch problemlos PowerShell installieren.</span><span class="sxs-lookup"><span data-stu-id="591df-118">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="591df-119">Installieren Sie zunächst [Cask-Versions][cask-versions]. Dies ermöglicht Ihnen das Installieren alternativer Versionen von Cask-Paketen:</span><span class="sxs-lookup"><span data-stu-id="591df-119">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="591df-120">Jetzt können Sie PowerShell installieren:</span><span class="sxs-lookup"><span data-stu-id="591df-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="591df-121">Vergewissern Sie sich abschließend, dass Ihre Installation voll funktionsfähig ist:</span><span class="sxs-lookup"><span data-stu-id="591df-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="591df-122">Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie einfach die Formel für Homebrew, und führen Sie ein Upgrade für PowerShell aus:</span><span class="sxs-lookup"><span data-stu-id="591df-122">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="591df-123">Die oben genannten Befehle können innerhalb eines PowerShell-Hosts (pwsh) aufgerufen werden, die Shell von PowerShell muss dann jedoch beendet und neu angegeben werden, um das Upgrade abzuschließen</span><span class="sxs-lookup"><span data-stu-id="591df-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="591df-124">und die in $PSVersionTable dargestellten Werte zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="591df-124">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="591df-125">Installation über einen direkten Download</span><span class="sxs-lookup"><span data-stu-id="591df-125">Installation via Direct Download</span></span>

<span data-ttu-id="591df-126">Laden Sie das PKG-Paket `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="591df-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="591df-127">über die Seite [Releases][] auf Ihren macOS-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="591df-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="591df-128">Doppelklicken Sie entweder auf die Datei, und befolgen Sie die Anweisungen, oder installieren Sie das Paket über das Terminal:</span><span class="sxs-lookup"><span data-stu-id="591df-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="591df-129">Archive der Binärdateien</span><span class="sxs-lookup"><span data-stu-id="591df-129">Binary Archives</span></span>

<span data-ttu-id="591df-130">`tar.gz`-Archive der PowerShell-Binärdateien werden für die macOS-Plattform zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="591df-130">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="591df-131">Installieren von Archiven der Binärdateien unter macOS</span><span class="sxs-lookup"><span data-stu-id="591df-131">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="591df-132">Deinstallieren von PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="591df-132">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="591df-133">Wenn Sie PowerShell mit Homebrew installiert haben, gestaltet sich die Deinstallation einfach:</span><span class="sxs-lookup"><span data-stu-id="591df-133">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="591df-134">Wenn Sie PowerShell über einen direkten Download installiert haben, muss PowerShell manuell entfernt werden:</span><span class="sxs-lookup"><span data-stu-id="591df-134">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="591df-135">Lesen Sie den Abschnitt [Pfade](#paths) in diesem Artikel, um zu erfahren, wie Sie zusätzliche PowerShell-Pfade deinstallieren können. Entfernen Sie die gewünschten Pfade mithilfe von `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="591df-135">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="591df-136">Dies ist nicht notwendig, wenn Sie eine Installation mit Homebrew durchgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="591df-136">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="591df-137">Pfade</span><span class="sxs-lookup"><span data-stu-id="591df-137">Paths</span></span>

* <span data-ttu-id="591df-138">`$PSHOME` ist `/usr/local/microsoft/powershell/6.1.0/`.</span><span class="sxs-lookup"><span data-stu-id="591df-138">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="591df-139">Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="591df-139">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="591df-140">Standardprofile werden über `$PSHOME/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="591df-140">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="591df-141">Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="591df-141">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="591df-142">Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="591df-142">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="591df-143">Standardmodule werden über `$PSHOME/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="591df-143">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="591df-144">Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="591df-144">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="591df-145">Die Profile halten sich an die Konfiguration von PowerShell pro Host.</span><span class="sxs-lookup"><span data-stu-id="591df-145">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="591df-146">Das bedeutet, dass hostspezifische Standardprofile in `Microsoft.PowerShell_profile.ps1` am gleichen Speicherort vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="591df-146">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="591df-147">PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter macOs ein.</span><span class="sxs-lookup"><span data-stu-id="591df-147">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="591df-148">Da macOS eine Ableitung von BSD ist, wird das Präfix `/usr/local` anstelle von `/opt` verwendet.</span><span class="sxs-lookup"><span data-stu-id="591df-148">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="591df-149">Daher ist `$PSHOME` `/usr/local/microsoft/powershell/6.1.0/` und der Symlink wird unter `/usr/local/bin/pwsh` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="591df-149">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="591df-150">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="591df-150">Additional Resources</span></span>

* <span data-ttu-id="591df-151">[Homebrew-Website][brew]</span><span class="sxs-lookup"><span data-stu-id="591df-151">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="591df-152">[Homebrew-GitHub-Repository][GitHub]</span><span class="sxs-lookup"><span data-stu-id="591df-152">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="591df-153">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="591df-153">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[Releases]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
