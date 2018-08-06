# <a name="installing-powershell-core-on-macos"></a>Installieren von PowerShell Core unter macOS

PowerShell Core unterstützt macOs 10.12 und höher.
Sämtliche Pakete sind auf der Seite [Releases][] über GitHub verfügbar.
Führen Sie `pwsh` über das Terminal aus, nachdem Sie das Paket installiert haben.

### <a name="installation-via-homebrew-on-macos-1012"></a>Installation über Homebrew unter macOS 10.12 und höher

Bei [Homebrew][brew] handelt es sich um den bevorzugten Paket-Manager für macOS.
Geben Sie in einem Terminalfenster `brew` ein, um Homebrew auszuführen.  Wenn der Befehl `brew` nicht gefunden wird, müssen Sie Homebrew installieren, indem Sie [die entsprechenden Anweisungen][brew] ausführen.

> [!NOTE]
> Wenn Sie in der Vergangenheit Homebrew installiert haben, empfiehlt es sich, stets „brew update-reset“ und „brew update“ auszuführen.
```sh
brew update-reset
brew update
```

> Bei älteren Homebrew-Versionen wurde „caskroom/cask“ verwendet, das als veraltet markiert ist und zu „homebrew/cask“ migriert wurde.  Weitere Informationen finden Sie unter [Homebrew-cask][cask]. Verwenden Sie den Befehl „brew tap“, um Ihre aktuellen Taps aufzulisten.  Wenn Sie „caskroom/cask“ sehen, können Sie mit „brew update“ die Migration der Taps in Homebrew veranlassen.

```sh
brew tap
brew update
```

Wenn Sie Homebrew installiert bzw. aktualisiert haben, können Sie auch problemlos PowerShell installieren.

So installieren Sie PowerShell

```sh
brew cask install powershell
```

Vergewissern Sie sich abschließend, dass Ihre Installation voll funktionsfähig ist:

```sh
pwsh
```

Um PowerShell zu beenden und zu Bash zurückzukehren, verwenden Sie den Befehl „exit“. 
```sh
exit
```

Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie einfach die Formel für Homebrew, und führen Sie ein Upgrade für PowerShell aus:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Die oben genannten Befehle können innerhalb eines PowerShell-Hosts (pwsh) aufgerufen werden, die Shell von PowerShell muss dann jedoch beendet und neu gestartet werden, um das Upgrade abzuschließen und die in $PSVersionTable dargestellten Werte zu aktualisieren.

### <a name="installing-preview-via-homebrew-on-macos-1012"></a>Installation der Vorschauversion über Homebrew unter macOS 10.12 und höher

Bei [Homebrew][brew] handelt es sich um den bevorzugten Paket-Manager für macOS.
Geben Sie in einem Terminalfenster `brew` ein, um Homebrew auszuführen.  Wenn der Befehl `brew` nicht gefunden wird, müssen Sie Homebrew installieren, indem Sie [die entsprechenden Anweisungen][brew] ausführen.

> [!NOTE]
> Wenn Sie in der Vergangenheit Homebrew installiert haben, empfiehlt es sich, stets „brew update-reset“ und „brew update“ auszuführen.
```sh
brew update-reset
brew update
```

Anschließend müssen Sie das Cask-Repository `versions` verwenden, um das Vorschaupaket abzurufen:

```sh
brew tap homebrew/cask-versions
```

So installieren Sie die Vorschauversion von PowerShell

```sh
brew cask install powershell-preview
```

Vergewissern Sie sich abschließend, dass Ihre Installation voll funktionsfähig ist:

```sh
pwsh-preview
```

Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie einfach die Formel für Homebrew, und führen Sie ein Upgrade für die Vorschauversion von PowerShell durch:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Die oben genannten Befehle können innerhalb eines PowerShell-Hosts (pwsh) aufgerufen werden, die Shell von PowerShell muss dann jedoch beendet und neu gestartet werden, um das Upgrade abzuschließen und die in $PSVersionTable dargestellten Werte zu aktualisieren.

### <a name="installation-via-direct-download"></a>Installation über einen direkten Download

Laden Sie das PKG-Paket `powershell-6.0.2-osx.10.12-x64.pkg` über die Seite [Releases][] auf den macOS-Computer herunter.

Doppelklicken Sie entweder auf die Datei, und befolgen Sie die Anweisungen, oder installieren Sie das Paket über das Terminal:

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a>Archive der Binärdateien

`tar.gz`-Archive der PowerShell-Binärdateien werden für die Plattformen macOs und Linux zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu aktivieren.

### <a name="installing-binary-archives-on-macos"></a>Installieren von Archiven der Binärdateien unter macOS

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

## <a name="uninstalling-powershell-core"></a>Deinstallieren von PowerShell Core

Wenn Sie PowerShell mit Homebrew installiert haben, gestaltet sich die Deinstallation einfach:

```sh
brew cask uninstall powershell
```

Wenn Sie PowerShell über einen direkten Download installiert haben, muss PowerShell manuell entfernt werden:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Lesen Sie den Abschnitt [Pfade][] in diesem Artikel, um zu erfahren, wie Sie zusätzliche PowerShell-Pfade deinstallieren können. Entfernen Sie die gewünschten Pfade mithilfe von `sudo rm`.

> [!NOTE]
> Dies ist nicht notwendig, wenn Sie eine Installation mit Homebrew durchgeführt haben.

[Pfade]:#paths

## <a name="paths"></a>Pfade

* `$PSHOME` ist `/usr/local/microsoft/powershell/6.0.2/`.
* Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.
* Standardprofile werden über `$PSHOME/profile.ps1` gelesen.
* Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.
* Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.
* Standardmodule werden über `$PSHOME/Modules` gelesen.
* Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.

Die Profile halten sich an die Konfiguration von PowerShell pro Host.
Das bedeutet, dass hostspezifische Standardprofile in `Microsoft.PowerShell_profile.ps1` am gleichen Speicherort vorhanden sind.

PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter macOs ein.

Da macOS eine Ableitung von BSD ist, wird das Präfix `/usr/local` anstelle von `/opt` verwendet.
Daher ist `$PSHOME` `/usr/local/microsoft/powershell/6.0.2/` und der Symlink wird unter `/usr/local/bin/pwsh` gespeichert.

## <a name="additional-resources"></a>Weitere Ressourcen

* [Homebrew-Website][brew]
* [Homebrew-GitHub-Repository][GitHub]
* [Homebrew-Cask][cask]


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[Releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
