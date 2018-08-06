# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="4a9b2-101">Installieren von PowerShell Core unter macOS</span><span class="sxs-lookup"><span data-stu-id="4a9b2-101">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="4a9b2-102">PowerShell Core unterstützt macOs 10.12 und höher.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-102">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="4a9b2-103">Sämtliche Pakete sind auf der Seite [Releases][] über GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-103">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="4a9b2-104">Führen Sie `pwsh` über das Terminal aus, nachdem Sie das Paket installiert haben.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-104">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="4a9b2-105">Installation über Homebrew unter macOS 10.12 und höher</span><span class="sxs-lookup"><span data-stu-id="4a9b2-105">Installation via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="4a9b2-106">Bei [Homebrew][brew] handelt es sich um den bevorzugten Paket-Manager für macOS.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-106">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="4a9b2-107">Geben Sie in einem Terminalfenster `brew` ein, um Homebrew auszuführen.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-107">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="4a9b2-108">Wenn der Befehl `brew` nicht gefunden wird, müssen Sie Homebrew installieren, indem Sie [die entsprechenden Anweisungen][brew] ausführen.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-108">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="4a9b2-109">Wenn Sie in der Vergangenheit Homebrew installiert haben, empfiehlt es sich, stets „brew update-reset“ und „brew update“ auszuführen.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-109">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

> <span data-ttu-id="4a9b2-110">Bei älteren Homebrew-Versionen wurde „caskroom/cask“ verwendet, das als veraltet markiert ist und zu „homebrew/cask“ migriert wurde.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-110">Older versions of Homebrew used the tap 'caskroom/cask', which has been deprecated, and migrated into 'homebrew/cask'.</span></span>  <span data-ttu-id="4a9b2-111">Weitere Informationen finden Sie unter [Homebrew-cask][cask].</span><span class="sxs-lookup"><span data-stu-id="4a9b2-111">More information can be found at [Homebrew-cask][cask].</span></span> <span data-ttu-id="4a9b2-112">Verwenden Sie den Befehl „brew tap“, um Ihre aktuellen Taps aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-112">Use the 'brew tap' command to list your current taps.</span></span>  <span data-ttu-id="4a9b2-113">Wenn Sie „caskroom/cask“ sehen, können Sie mit „brew update“ die Migration der Taps in Homebrew veranlassen.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-113">If you see 'caskroom/cask' you can use 'brew update' to have Homebrew migrate the taps.</span></span>

```sh
brew tap
brew update
```

<span data-ttu-id="4a9b2-114">Wenn Sie Homebrew installiert bzw. aktualisiert haben, können Sie auch problemlos PowerShell installieren.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-114">Once you've installed/updated Homebrew, installing PowerShell is easy.</span></span>

<span data-ttu-id="4a9b2-115">So installieren Sie PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a9b2-115">To install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="4a9b2-116">Vergewissern Sie sich abschließend, dass Ihre Installation voll funktionsfähig ist:</span><span class="sxs-lookup"><span data-stu-id="4a9b2-116">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="4a9b2-117">Um PowerShell zu beenden und zu Bash zurückzukehren, verwenden Sie den Befehl „exit“.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-117">To exit PowerShell, and return to bash, use the 'exit' command.</span></span> 
```sh
exit
```

<span data-ttu-id="4a9b2-118">Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie einfach die Formel für Homebrew, und führen Sie ein Upgrade für PowerShell aus:</span><span class="sxs-lookup"><span data-stu-id="4a9b2-118">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="4a9b2-119">Die oben genannten Befehle können innerhalb eines PowerShell-Hosts (pwsh) aufgerufen werden, die Shell von PowerShell muss dann jedoch beendet und neu gestartet werden, um das Upgrade abzuschließen und die in $PSVersionTable dargestellten Werte zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-119">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installing-preview-via-homebrew-on-macos-1012"></a><span data-ttu-id="4a9b2-120">Installation der Vorschauversion über Homebrew unter macOS 10.12 und höher</span><span class="sxs-lookup"><span data-stu-id="4a9b2-120">Installing Preview via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="4a9b2-121">Bei [Homebrew][brew] handelt es sich um den bevorzugten Paket-Manager für macOS.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-121">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="4a9b2-122">Geben Sie in einem Terminalfenster `brew` ein, um Homebrew auszuführen.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-122">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="4a9b2-123">Wenn der Befehl `brew` nicht gefunden wird, müssen Sie Homebrew installieren, indem Sie [die entsprechenden Anweisungen][brew] ausführen.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-123">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="4a9b2-124">Wenn Sie in der Vergangenheit Homebrew installiert haben, empfiehlt es sich, stets „brew update-reset“ und „brew update“ auszuführen.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-124">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

<span data-ttu-id="4a9b2-125">Anschließend müssen Sie das Cask-Repository `versions` verwenden, um das Vorschaupaket abzurufen:</span><span class="sxs-lookup"><span data-stu-id="4a9b2-125">Then, you must tap the `versions` casks repository to get the preview package:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="4a9b2-126">So installieren Sie die Vorschauversion von PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a9b2-126">To install PowerShell Preview:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="4a9b2-127">Vergewissern Sie sich abschließend, dass Ihre Installation voll funktionsfähig ist:</span><span class="sxs-lookup"><span data-stu-id="4a9b2-127">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="4a9b2-128">Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie einfach die Formel für Homebrew, und führen Sie ein Upgrade für die Vorschauversion von PowerShell durch:</span><span class="sxs-lookup"><span data-stu-id="4a9b2-128">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell Preview:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="4a9b2-129">Die oben genannten Befehle können innerhalb eines PowerShell-Hosts (pwsh) aufgerufen werden, die Shell von PowerShell muss dann jedoch beendet und neu gestartet werden, um das Upgrade abzuschließen und die in $PSVersionTable dargestellten Werte zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-129">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installation-via-direct-download"></a><span data-ttu-id="4a9b2-130">Installation über einen direkten Download</span><span class="sxs-lookup"><span data-stu-id="4a9b2-130">Installation via Direct Download</span></span>

<span data-ttu-id="4a9b2-131">Laden Sie das PKG-Paket `powershell-6.0.2-osx.10.12-x64.pkg` über die Seite [Releases][] auf den macOS-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-131">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="4a9b2-132">Doppelklicken Sie entweder auf die Datei, und befolgen Sie die Anweisungen, oder installieren Sie das Paket über das Terminal:</span><span class="sxs-lookup"><span data-stu-id="4a9b2-132">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="4a9b2-133">Archive der Binärdateien</span><span class="sxs-lookup"><span data-stu-id="4a9b2-133">Binary Archives</span></span>

<span data-ttu-id="4a9b2-134">`tar.gz`-Archive der PowerShell-Binärdateien werden für die Plattformen macOs und Linux zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-134">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="4a9b2-135">Installieren von Archiven der Binärdateien unter macOS</span><span class="sxs-lookup"><span data-stu-id="4a9b2-135">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="4a9b2-136">Deinstallieren von PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="4a9b2-136">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="4a9b2-137">Wenn Sie PowerShell mit Homebrew installiert haben, gestaltet sich die Deinstallation einfach:</span><span class="sxs-lookup"><span data-stu-id="4a9b2-137">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="4a9b2-138">Wenn Sie PowerShell über einen direkten Download installiert haben, muss PowerShell manuell entfernt werden:</span><span class="sxs-lookup"><span data-stu-id="4a9b2-138">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="4a9b2-139">Lesen Sie den Abschnitt [Pfade][] in diesem Artikel, um zu erfahren, wie Sie zusätzliche PowerShell-Pfade deinstallieren können. Entfernen Sie die gewünschten Pfade mithilfe von `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-139">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="4a9b2-140">Dies ist nicht notwendig, wenn Sie eine Installation mit Homebrew durchgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-140">This is not necessary if you installed with Homebrew.</span></span>

[Pfade]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="4a9b2-142">Pfade</span><span class="sxs-lookup"><span data-stu-id="4a9b2-142">Paths</span></span>

* <span data-ttu-id="4a9b2-143">`$PSHOME` ist `/usr/local/microsoft/powershell/6.0.2/`.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-143">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="4a9b2-144">Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-144">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="4a9b2-145">Standardprofile werden über `$PSHOME/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-145">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="4a9b2-146">Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-146">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="4a9b2-147">Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-147">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="4a9b2-148">Standardmodule werden über `$PSHOME/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-148">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="4a9b2-149">Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-149">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="4a9b2-150">Die Profile halten sich an die Konfiguration von PowerShell pro Host.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-150">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="4a9b2-151">Das bedeutet, dass hostspezifische Standardprofile in `Microsoft.PowerShell_profile.ps1` am gleichen Speicherort vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-151">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="4a9b2-152">PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter macOs ein.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-152">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="4a9b2-153">Da macOS eine Ableitung von BSD ist, wird das Präfix `/usr/local` anstelle von `/opt` verwendet.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-153">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="4a9b2-154">Daher ist `$PSHOME` `/usr/local/microsoft/powershell/6.0.2/` und der Symlink wird unter `/usr/local/bin/pwsh` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="4a9b2-154">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="4a9b2-155">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4a9b2-155">Additional Resources</span></span>

* <span data-ttu-id="4a9b2-156">[Homebrew-Website][brew]</span><span class="sxs-lookup"><span data-stu-id="4a9b2-156">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="4a9b2-157">[Homebrew-GitHub-Repository][GitHub]</span><span class="sxs-lookup"><span data-stu-id="4a9b2-157">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="4a9b2-158">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="4a9b2-158">[Homebrew-Cask][cask]</span></span>


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[Releases]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
