---
title: Installieren von PowerShell Core unter macOS
description: Informationen zur Installation von PowerShell Core unter macOS
ms.date: 08/06/2018
ms.openlocfilehash: ff1814d95b3ca3fa8497069dff249fd2ad5576ef
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587464"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="3efb8-103">Installieren von PowerShell Core unter macOS</span><span class="sxs-lookup"><span data-stu-id="3efb8-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="3efb8-104">PowerShell Core unterstützt macOs 10.12 und höher.</span><span class="sxs-lookup"><span data-stu-id="3efb8-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="3efb8-105">Sämtliche Pakete sind auf der Seite [Releases][] über GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3efb8-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="3efb8-106">Führen Sie `pwsh` über das Terminal aus, nachdem Sie das Paket installiert haben.</span><span class="sxs-lookup"><span data-stu-id="3efb8-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="3efb8-107">Installation über Homebrew unter macOS 10.12 und höher</span><span class="sxs-lookup"><span data-stu-id="3efb8-107">Installation via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="3efb8-108">Bei [Homebrew][brew] handelt es sich um den bevorzugten Paket-Manager für macOS.</span><span class="sxs-lookup"><span data-stu-id="3efb8-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="3efb8-109">Geben Sie in einem Terminalfenster `brew` ein, um Homebrew auszuführen.</span><span class="sxs-lookup"><span data-stu-id="3efb8-109">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="3efb8-110">Wenn der Befehl `brew` nicht gefunden wird, müssen Sie Homebrew installieren, indem Sie [die entsprechenden Anweisungen][brew] ausführen.</span><span class="sxs-lookup"><span data-stu-id="3efb8-110">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="3efb8-111">Wenn Sie in der Vergangenheit Homebrew installiert haben, empfiehlt es sich, stets „brew update-reset“ und „brew update“ auszuführen.</span><span class="sxs-lookup"><span data-stu-id="3efb8-111">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

> <span data-ttu-id="3efb8-112">Bei älteren Homebrew-Versionen wurde „caskroom/cask“ verwendet, das als veraltet markiert ist und zu „homebrew/cask“ migriert wurde.</span><span class="sxs-lookup"><span data-stu-id="3efb8-112">Older versions of Homebrew used the tap 'caskroom/cask', which has been deprecated, and migrated into 'homebrew/cask'.</span></span>  <span data-ttu-id="3efb8-113">Weitere Informationen finden Sie unter [Homebrew-cask][cask].</span><span class="sxs-lookup"><span data-stu-id="3efb8-113">More information can be found at [Homebrew-cask][cask].</span></span> <span data-ttu-id="3efb8-114">Verwenden Sie den Befehl „brew tap“, um Ihre aktuellen Taps aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="3efb8-114">Use the 'brew tap' command to list your current taps.</span></span>  <span data-ttu-id="3efb8-115">Wenn Sie „caskroom/cask“ sehen, können Sie mit „brew update“ die Migration der Taps in Homebrew veranlassen.</span><span class="sxs-lookup"><span data-stu-id="3efb8-115">If you see 'caskroom/cask' you can use 'brew update' to have Homebrew migrate the taps.</span></span>

```sh
brew tap
brew update
```

<span data-ttu-id="3efb8-116">Wenn Sie Homebrew installiert bzw. aktualisiert haben, können Sie auch problemlos PowerShell installieren.</span><span class="sxs-lookup"><span data-stu-id="3efb8-116">Once you've installed/updated Homebrew, installing PowerShell is easy.</span></span>

<span data-ttu-id="3efb8-117">So installieren Sie PowerShell</span><span class="sxs-lookup"><span data-stu-id="3efb8-117">To install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="3efb8-118">Vergewissern Sie sich abschließend, dass Ihre Installation voll funktionsfähig ist:</span><span class="sxs-lookup"><span data-stu-id="3efb8-118">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="3efb8-119">Um PowerShell zu beenden und zu Bash zurückzukehren, verwenden Sie den Befehl „exit“.</span><span class="sxs-lookup"><span data-stu-id="3efb8-119">To exit PowerShell, and return to bash, use the 'exit' command.</span></span>
```sh
exit
```

<span data-ttu-id="3efb8-120">Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie einfach die Formel für Homebrew, und führen Sie ein Upgrade für PowerShell aus:</span><span class="sxs-lookup"><span data-stu-id="3efb8-120">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="3efb8-121">Die oben genannten Befehle können innerhalb eines PowerShell-Hosts (pwsh) aufgerufen werden, die Shell von PowerShell muss dann jedoch beendet und neu gestartet werden, um das Upgrade abzuschließen und die in $PSVersionTable dargestellten Werte zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="3efb8-121">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installing-preview-via-homebrew-on-macos-1012"></a><span data-ttu-id="3efb8-122">Installation der Vorschauversion über Homebrew unter macOS 10.12 und höher</span><span class="sxs-lookup"><span data-stu-id="3efb8-122">Installing Preview via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="3efb8-123">Bei [Homebrew][brew] handelt es sich um den bevorzugten Paket-Manager für macOS.</span><span class="sxs-lookup"><span data-stu-id="3efb8-123">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="3efb8-124">Geben Sie in einem Terminalfenster `brew` ein, um Homebrew auszuführen.</span><span class="sxs-lookup"><span data-stu-id="3efb8-124">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="3efb8-125">Wenn der Befehl `brew` nicht gefunden wird, müssen Sie Homebrew installieren, indem Sie [die entsprechenden Anweisungen][brew] ausführen.</span><span class="sxs-lookup"><span data-stu-id="3efb8-125">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="3efb8-126">Wenn Sie in der Vergangenheit Homebrew installiert haben, empfiehlt es sich, stets „brew update-reset“ und „brew update“ auszuführen.</span><span class="sxs-lookup"><span data-stu-id="3efb8-126">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

<span data-ttu-id="3efb8-127">Anschließend müssen Sie das Cask-Repository `versions` verwenden, um das Vorschaupaket abzurufen:</span><span class="sxs-lookup"><span data-stu-id="3efb8-127">Then, you must tap the `versions` casks repository to get the preview package:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="3efb8-128">So installieren Sie die Vorschauversion von PowerShell</span><span class="sxs-lookup"><span data-stu-id="3efb8-128">To install PowerShell Preview:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="3efb8-129">Vergewissern Sie sich abschließend, dass Ihre Installation voll funktionsfähig ist:</span><span class="sxs-lookup"><span data-stu-id="3efb8-129">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="3efb8-130">Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie einfach die Formel für Homebrew, und führen Sie ein Upgrade für die Vorschauversion von PowerShell durch:</span><span class="sxs-lookup"><span data-stu-id="3efb8-130">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell Preview:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="3efb8-131">Die oben genannten Befehle können innerhalb eines PowerShell-Hosts (pwsh) aufgerufen werden, die Shell von PowerShell muss dann jedoch beendet und neu gestartet werden, um das Upgrade abzuschließen und die in $PSVersionTable dargestellten Werte zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="3efb8-131">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installation-via-direct-download"></a><span data-ttu-id="3efb8-132">Installation über einen direkten Download</span><span class="sxs-lookup"><span data-stu-id="3efb8-132">Installation via Direct Download</span></span>

<span data-ttu-id="3efb8-133">Laden Sie das PKG-Paket `powershell-6.0.2-osx.10.12-x64.pkg` über die Seite [Releases][] auf den macOS-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="3efb8-133">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="3efb8-134">Doppelklicken Sie entweder auf die Datei, und befolgen Sie die Anweisungen, oder installieren Sie das Paket über das Terminal:</span><span class="sxs-lookup"><span data-stu-id="3efb8-134">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="3efb8-135">Archive der Binärdateien</span><span class="sxs-lookup"><span data-stu-id="3efb8-135">Binary Archives</span></span>

<span data-ttu-id="3efb8-136">`tar.gz`-Archive der PowerShell-Binärdateien werden für die Plattformen macOs und Linux zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="3efb8-136">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="3efb8-137">Installieren von Archiven der Binärdateien unter macOS</span><span class="sxs-lookup"><span data-stu-id="3efb8-137">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.2/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="3efb8-138">Deinstallieren von PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="3efb8-138">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="3efb8-139">Wenn Sie PowerShell mit Homebrew installiert haben, gestaltet sich die Deinstallation einfach:</span><span class="sxs-lookup"><span data-stu-id="3efb8-139">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="3efb8-140">Wenn Sie PowerShell über einen direkten Download installiert haben, muss PowerShell manuell entfernt werden:</span><span class="sxs-lookup"><span data-stu-id="3efb8-140">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="3efb8-141">Lesen Sie den Abschnitt [Pfade][] in diesem Artikel, um zu erfahren, wie Sie zusätzliche PowerShell-Pfade deinstallieren können. Entfernen Sie die gewünschten Pfade mithilfe von `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="3efb8-141">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="3efb8-142">Dies ist nicht notwendig, wenn Sie eine Installation mit Homebrew durchgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="3efb8-142">This is not necessary if you installed with Homebrew.</span></span>

[Pfade]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="3efb8-144">Pfade</span><span class="sxs-lookup"><span data-stu-id="3efb8-144">Paths</span></span>

* <span data-ttu-id="3efb8-145">`$PSHOME` ist `/usr/local/microsoft/powershell/6.0.2/`.</span><span class="sxs-lookup"><span data-stu-id="3efb8-145">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="3efb8-146">Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="3efb8-146">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="3efb8-147">Standardprofile werden über `$PSHOME/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="3efb8-147">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="3efb8-148">Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="3efb8-148">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="3efb8-149">Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="3efb8-149">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="3efb8-150">Standardmodule werden über `$PSHOME/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="3efb8-150">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="3efb8-151">Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="3efb8-151">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="3efb8-152">Die Profile halten sich an die Konfiguration von PowerShell pro Host.</span><span class="sxs-lookup"><span data-stu-id="3efb8-152">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="3efb8-153">Das bedeutet, dass hostspezifische Standardprofile in `Microsoft.PowerShell_profile.ps1` am gleichen Speicherort vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="3efb8-153">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="3efb8-154">PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter macOs ein.</span><span class="sxs-lookup"><span data-stu-id="3efb8-154">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="3efb8-155">Da macOS eine Ableitung von BSD ist, wird das Präfix `/usr/local` anstelle von `/opt` verwendet.</span><span class="sxs-lookup"><span data-stu-id="3efb8-155">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="3efb8-156">Daher ist `$PSHOME` `/usr/local/microsoft/powershell/6.0.2/` und der Symlink wird unter `/usr/local/bin/pwsh` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="3efb8-156">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="3efb8-157">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="3efb8-157">Additional Resources</span></span>

* <span data-ttu-id="3efb8-158">[Homebrew-Website][brew]</span><span class="sxs-lookup"><span data-stu-id="3efb8-158">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="3efb8-159">[Homebrew-GitHub-Repository][GitHub]</span><span class="sxs-lookup"><span data-stu-id="3efb8-159">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="3efb8-160">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="3efb8-160">[Homebrew-Cask][cask]</span></span>


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[Releases]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
