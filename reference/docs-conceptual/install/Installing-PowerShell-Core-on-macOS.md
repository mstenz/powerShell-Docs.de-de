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
# <a name="installing-powershell-core-on-macos"></a>Installieren von PowerShell Core unter macOS

PowerShell Core unterstützt macOs 10.12 und höher.
Sämtliche Pakete sind auf der Seite [Freigaben][] über GitHub verfügbar.
Nachdem das Paket installiert ist, führen Sie `pwsh` über das Terminal.

## <a name="about-brew"></a>Informationen zu Brew

Bei [Homebrew][brew] handelt es sich um den bevorzugten Paket-Manager für macOS.
Wenn der Befehl `brew` nicht gefunden wird, müssen Sie Homebrew installieren, indem Sie [die entsprechenden Anweisungen][brew] ausführen.

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a>Installation des neuesten stabilen Release über Homebrew unter macOS 10.12 oder höher

Weitere Informationen zu Ansichten finden Sie unter [Info zu Brew](#about-brew).

Jetzt können Sie PowerShell installieren:

```sh
brew cask install powershell
```

Vergewissern Sie sich abschließend, dass Ihre Installation voll funktionsfähig ist:

```sh
pwsh
```

Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie Homebrews-Formeln, und aktualisieren Sie PowerShell:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Die oben genannten Befehle können von innerhalb eines Hosts-PowerShell (Pwsh) aufgerufen werden, aber dann muss die PowerShell-Shell wurde beendet und neu gestartet, um das Upgrade abzuschließen, und aktualisieren die Werte im `$PSVersionTable`.

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>Installation der neuesten stabilen Vorschauversion über Homebrew unter macOS 10.12 oder höher

Weitere Informationen zu Ansichten finden Sie unter [Info zu Brew](#about-brew).

Nachdem Sie Homebrew installiert haben, können Sie PowerShell installieren.
Installieren Sie zunächst die [Cask-Versionen] [ cask-versions] Paket, das Sie alternative Versionen Cask-Pakete installieren kann:

```sh
brew tap homebrew/cask-versions
```

Jetzt können Sie PowerShell installieren:

```sh
brew cask install powershell-preview
```

Vergewissern Sie sich abschließend, dass Ihre Installation voll funktionsfähig ist:

```sh
pwsh-preview
```

Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie Homebrews-Formeln, und aktualisieren Sie PowerShell:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Die oben genannten Befehle können innerhalb eines PowerShell-Hosts (pwsh) aufgerufen werden, die Shell von PowerShell muss dann jedoch beendet und neu angegeben werden, um das Upgrade abzuschließen
> und aktualisieren Sie die Werte im `$PSVersionTable`.

## <a name="installation-via-direct-download"></a>Installation über einen direkten Download

Laden Sie das PKG-Paket `powershell-6.1.0-osx-x64.pkg`
über die Seite [Freigaben][] auf Ihren macOS-Computer herunter.

Doppelklicken Sie entweder auf die Datei, und befolgen Sie die Anweisungen, oder installieren Sie das Paket über das Terminal:

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

Installieren Sie [OpenSSL](#install-openssl). OpenSSL ist für PowerShell-Remotingfunktionen und CIM-Vorgänge erforderlich.

## <a name="binary-archives"></a>Archive der Binärdateien

`tar.gz`-Archive der PowerShell-Binärdateien werden für die macOS-Plattform zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu ermöglichen.

### <a name="installing-binary-archives-on-macos"></a>Installieren von Archiven der Binärdateien unter macOS

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

Installieren Sie [OpenSSL](#install-openssl). OpenSSL ist für PowerShell-Remotingfunktionen und CIM-Vorgänge erforderlich.

## <a name="installing-dependencies"></a>Installieren von Abhängigkeiten

### <a name="install-xcode-command-line-tools"></a>Installieren von XCode-Befehslzeilentools

```sh
xcode-select --install
```

### <a name="install-openssl"></a>Installieren von OpenSSL

OpenSSL ist für PowerShell-Remotingfunktionen und CIM-Vorgänge erforderlich. Die Installation kann über MacPorts oder Brew erfolgen.

#### <a name="install-openssl-via-brew"></a>Installieren von OpenSSL über Brew

Weitere Informationen zu Ansichten finden Sie unter [Info zu Brew](#about-brew).

Führen Sie zum Installieren von OpenSSL `brew install openssl`.

#### <a name="install-openssl-via-macports"></a>Installieren von OpenSSL über MacPorts

1. Installieren Sie die [XCode-Befehlszeilentools](#install-xcode-command-line-tools).
1. Installieren Sie MacPorts.
   Wenn Sie Anweisungen benötigen, lesen Sie die [Installationshandbuch](https://guide.macports.org/chunked/installing.macports.html).
1. Aktualisieren Sie MacPorts durch Ausführen von `sudo port selfupdate`.
1. Führen Sie eine Upgrade von MacPorts-Paketen durch Ausführen von `sudo port upgrade outdated` durch.
1. Installieren Sie OpenSSL durch Ausführen von `sudo port install openssl`.
1. Verknüpfen Sie die Bibliotheken aus, um sie zu PowerShell zur Verfügung zu stellen:

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a>Deinstallieren von PowerShell Core

Wenn Sie PowerShell mit Homebrew installiert haben, verwenden Sie den folgenden Befehl zum Deinstallieren:

```sh
brew cask uninstall powershell
```

Wenn Sie PowerShell über einen direkten Download installiert haben, muss PowerShell manuell entfernt werden:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Um zusätzliche PowerShell-Pfade zu entfernen, finden Sie in der [Pfade](#paths) in diesem Dokument im Abschnitt, und entfernen Sie die Pfade mit `sudo rm`.

> [!NOTE]
> Dies ist nicht notwendig, wenn Sie eine Installation mit Homebrew durchgeführt haben.

## <a name="paths"></a>Pfade

* `$PSHOME` ist `/usr/local/microsoft/powershell/6.1.0/`.
* Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.
* Standardprofile werden über `$PSHOME/profile.ps1` gelesen.
* Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.
* Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.
* Standardmodule werden über `$PSHOME/Modules` gelesen.
* Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.

Die Profile halten sich an die Konfiguration von PowerShell pro Host.
Damit das Standardprofil für die hostspezifische am vorhanden ist `Microsoft.PowerShell_profile.ps1` am gleichen Speicherort.

PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter macOs ein.

Da macOS eine Ableitung von BSD ist, wird das Präfix `/usr/local` anstelle von `/opt` verwendet.
Also `$PSHOME` ist `/usr/local/microsoft/powershell/6.1.0/`, und die symbolische Verknüpfung befindet sich am `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Weitere Ressourcen

* [Homebrew-Website][brew]
* [Homebrew-GitHub-Repository][GitHub]
* [Homebrew-Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[Freigaben]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
