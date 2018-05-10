# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="24de9-101">Installieren von PowerShell Core unter macOS</span><span class="sxs-lookup"><span data-stu-id="24de9-101">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="24de9-102">PowerShell Core unterstützt macOs 10.12 und höher.</span><span class="sxs-lookup"><span data-stu-id="24de9-102">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="24de9-103">Sämtliche Pakete sind auf der Seite [Releases][] über GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="24de9-103">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="24de9-104">Führen Sie `pwsh` über das Terminal aus, nachdem Sie das Paket installiert haben.</span><span class="sxs-lookup"><span data-stu-id="24de9-104">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="24de9-105">Installation über Homebrew unter macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="24de9-105">Installation via Homebrew on macOS 10.12</span></span>

<span data-ttu-id="24de9-106">Bei [Homebrew][brew] handelt es sich um den bevorzugten Paket-Manager für macOS.</span><span class="sxs-lookup"><span data-stu-id="24de9-106">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="24de9-107">Wenn der Befehl `brew` nicht gefunden wird, müssen Sie Homebrew installieren, indem Sie [die entsprechenden Anweisungen][brew] ausführen.</span><span class="sxs-lookup"><span data-stu-id="24de9-107">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="24de9-108">Wenn Sie Homebrew installiert haben, können Sie auch problemlos PowerShell installieren.</span><span class="sxs-lookup"><span data-stu-id="24de9-108">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="24de9-109">Installieren Sie zuerst [Homebrew-Cask][cask], damit Sie danach weitere Pakete installieren können:</span><span class="sxs-lookup"><span data-stu-id="24de9-109">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="24de9-110">Jetzt können Sie PowerShell installieren:</span><span class="sxs-lookup"><span data-stu-id="24de9-110">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="24de9-111">Vergewissern Sie sich abschließend, dass Ihre Installation voll funktionsfähig ist:</span><span class="sxs-lookup"><span data-stu-id="24de9-111">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="24de9-112">Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie einfach die Formel für Homebrew, und führen Sie ein Upgrade für PowerShell aus:</span><span class="sxs-lookup"><span data-stu-id="24de9-112">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="24de9-113">Die oben genannten Befehle können innerhalb eines PowerShell-Hosts (pwsh) aufgerufen werden, die Shell von PowerShell muss dann jedoch beendet und neu angegeben werden, um das Upgrade abzuschließen</span><span class="sxs-lookup"><span data-stu-id="24de9-113">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="24de9-114">und die in $PSVersionTable dargestellten Werte zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="24de9-114">and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download"></a><span data-ttu-id="24de9-115">Installation über einen direkten Download</span><span class="sxs-lookup"><span data-stu-id="24de9-115">Installation via Direct Download</span></span>

<span data-ttu-id="24de9-116">Laden Sie das PKG-Paket `powershell-6.0.2-osx.10.12-x64.pkg` über die Seite [Releases][] auf den macOS-Computer herunter.</span><span class="sxs-lookup"><span data-stu-id="24de9-116">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="24de9-117">Doppelklicken Sie entweder auf die Datei, und befolgen Sie die Anweisungen, oder installieren Sie das Paket über das Terminal:</span><span class="sxs-lookup"><span data-stu-id="24de9-117">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="24de9-118">Archive der Binärdateien</span><span class="sxs-lookup"><span data-stu-id="24de9-118">Binary Archives</span></span>

<span data-ttu-id="24de9-119">`tar.gz`-Archive der PowerShell-Binärdateien werden für die Plattformen macOs und Linux zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="24de9-119">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="24de9-120">Installieren von Archiven der Binärdateien unter macOS</span><span class="sxs-lookup"><span data-stu-id="24de9-120">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="24de9-121">Deinstallieren von PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="24de9-121">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="24de9-122">Wenn Sie PowerShell mit Homebrew installiert haben, gestaltet sich die Deinstallation einfach:</span><span class="sxs-lookup"><span data-stu-id="24de9-122">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="24de9-123">Wenn Sie PowerShell über einen direkten Download installiert haben, muss PowerShell manuell entfernt werden:</span><span class="sxs-lookup"><span data-stu-id="24de9-123">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="24de9-124">Lesen Sie den Abschnitt [Pfade][] in diesem Artikel, um zu erfahren, wie Sie zusätzliche PowerShell-Pfade deinstallieren können. Entfernen Sie die gewünschten Pfade mithilfe von `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="24de9-124">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="24de9-125">Dies ist nicht notwendig, wenn Sie eine Installation mit Homebrew durchgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="24de9-125">This is not necessary if you installed with Homebrew.</span></span>

[Pfade]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="24de9-127">Pfade</span><span class="sxs-lookup"><span data-stu-id="24de9-127">Paths</span></span>

* <span data-ttu-id="24de9-128">`$PSHOME` ist `/opt/microsoft/powershell/6.0.0/`.</span><span class="sxs-lookup"><span data-stu-id="24de9-128">`$PSHOME` is `/opt/microsoft/powershell/6.0.0/`</span></span>
* <span data-ttu-id="24de9-129">Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="24de9-129">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="24de9-130">Standardprofile werden über `$PSHOME/profile.ps1` gelesen.</span><span class="sxs-lookup"><span data-stu-id="24de9-130">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="24de9-131">Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="24de9-131">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="24de9-132">Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="24de9-132">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="24de9-133">Standardmodule werden über `$PSHOME/Modules` gelesen.</span><span class="sxs-lookup"><span data-stu-id="24de9-133">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="24de9-134">Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="24de9-134">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="24de9-135">Die Profile halten sich an die Konfiguration von PowerShell pro Host.</span><span class="sxs-lookup"><span data-stu-id="24de9-135">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="24de9-136">Das bedeutet, dass hostspezifische Standardprofile in `Microsoft.PowerShell_profile.ps1` am gleichen Speicherort vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="24de9-136">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="24de9-137">PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter macOs ein.</span><span class="sxs-lookup"><span data-stu-id="24de9-137">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="24de9-138">Da macOS eine Ableitung von BSD ist, wird das Präfix `/usr/local` anstelle von `/opt` verwendet.</span><span class="sxs-lookup"><span data-stu-id="24de9-138">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="24de9-139">Daher ist `$PSHOME` `/usr/local/microsoft/powershell/6.0.0/` und der Symlink wird unter `/usr/local/bin/pwsh` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="24de9-139">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[Releases]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
