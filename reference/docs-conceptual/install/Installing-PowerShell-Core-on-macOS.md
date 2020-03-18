---
title: Installieren von PowerShell unter macOS
description: Informationen zur Installation von PowerShell unter macOS
ms.date: 12/12/2018
ms.openlocfilehash: 7f0d6a1aa275deb39a7d670546ee7e833b8ef315
ms.sourcegitcommit: 4a26c05f162c4fa347a9d67e339f8a33e230b9ba
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78404824"
---
# <a name="installing-powershell-on-macos"></a>Installieren von PowerShell unter macOS

PowerShell unterstützt macOS 10.12 und höher.
Sämtliche Pakete sind auf der Seite [Freigaben][] über GitHub verfügbar.
Nachdem Sie das Paket installiert haben, führen Sie `pwsh` über das Terminal aus.

> [!NOTE]
> PowerShell 7 ist ein direktes Upgrade, mit dem PowerShell Core 6.x entfernt wird.
>
> Der Ordner `/usr/local/microsoft/powershell/6` wird durch `/usr/local/microsoft/powershell/7` ersetzt.
>
> Wenn Sie PowerShell 6 und PowerShell 7 parallel ausführen müssen, installieren Sie PowerShell 6 mithilfe der [binary archive](#binary-archives)-Methode neu.

## <a name="about-brew"></a>Informationen zu Brew

Bei [Homebrew][brew] handelt es sich um den bevorzugten Paket-Manager für macOS. Wenn der Befehl `brew` nicht gefunden wird, müssen Sie Homebrew installieren, indem Sie [die entsprechenden Anweisungen][brew] ausführen. Andernfalls können Sie PowerShell über [Direkter Download](#installation-via-direct-download) oder aus [Archive der Binärdateien](#binary-archives) installieren.

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a>Installation des neuesten stabilen Release über Homebrew unter macOS 10.12 oder höher

Weitere Informationen zu Brew finden Sie unter [Info zu Brew](#about-brew).

Jetzt können Sie PowerShell installieren:

```sh
brew cask install powershell
```

Vergewissern Sie sich abschließend, dass Ihre Installation voll funktionsfähig ist:

```sh
pwsh
```

Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie die Formeln für Homebrew, und führen Sie ein Upgrade für PowerShell aus:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Die oben genannten Befehle können innerhalb eines PowerShell-Hosts (pwsh) aufgerufen werden. Allerdings muss dann die Shell von PowerShell beendet und neu gestartet werden, um das Upgrade abzuschließen und die in `$PSVersionTable` dargestellten Werte zu aktualisieren.

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>Installation der neuesten Vorschauversion über Homebrew unter macOS 10.12 oder höher

Weitere Informationen zu Brew finden Sie unter [Info zu Brew](#about-brew).

Nachdem Sie Homebrew installiert haben, können Sie PowerShell installieren.
Installieren Sie zunächst das Paket [Cask-Versions][cask-versions]. Dies ermöglicht Ihnen das Installieren alternativer Versionen von Cask-Paketen:

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

Wenn neue Versionen von PowerShell veröffentlicht werden, aktualisieren Sie die Formeln für Homebrew, und führen Sie ein Upgrade für PowerShell aus:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Die oben genannten Befehle können innerhalb eines PowerShell-Hosts (pwsh) aufgerufen werden, die Shell von PowerShell muss dann jedoch beendet und neu angegeben werden, um das Upgrade abzuschließen
> und die in `$PSVersionTable` dargestellten Werte zu aktualisieren.

## <a name="installation-via-direct-download"></a>Installation über einen direkten Download

Laden Sie das PKG-Paket `powershell-6.2.0-osx-x64.pkg`
über die Seite [Freigaben][] auf Ihren macOS-Computer herunter.

Doppelklicken Sie entweder auf die Datei, und befolgen Sie die Anweisungen, oder installieren Sie das Paket über das Terminal:

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

Installieren Sie [OpenSSL](#install-openssl). OpenSSL ist für PowerShell-Remotingfunktionen und CIM-Vorgänge erforderlich.

## <a name="install-as-a-net-global-tool"></a>Installieren als globales .NET-Tool

Wenn Sie das [.NET Core SDK](/dotnet/core/sdk) bereits installiert haben, können Sie PowerShell einfach als [globales .NET-Tool](/dotnet/core/tools/global-tools) installieren.

```
dotnet tool install --global PowerShell
```

## <a name="binary-archives"></a>Archive der Binärdateien

`tar.gz`-Archive der PowerShell-Binärdateien werden für die macOS-Plattform zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu ermöglichen.

### <a name="installing-binary-archives-on-macos"></a>Installieren von Archiven der Binärdateien unter macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.2.0/pwsh /usr/local/bin/pwsh
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

Weitere Informationen zu Brew finden Sie unter [Info zu Brew](#about-brew).

Führen Sie `brew install openssl` aus, um OpenSSL zu installieren.

#### <a name="install-openssl-via-macports"></a>Installieren von OpenSSL über MacPorts

1. Installieren Sie die [XCode-Befehlszeilentools](#install-xcode-command-line-tools).
1. Installieren Sie MacPorts.
   Wenn Sie Anleitungen dazu benötigen, lesen Sie das [Installationshandbuch](https://guide.macports.org/chunked/installing.macports.html).
1. Aktualisieren Sie MacPorts durch Ausführen von `sudo port selfupdate`.
1. Führen Sie eine Upgrade von MacPorts-Paketen durch Ausführen von `sudo port upgrade outdated` durch.
1. Installieren Sie OpenSSL durch Ausführen von `sudo port install openssl`.
1. Verknüpfen Sie die Bibliotheken, um sie PowerShell zur Verfügung zu stellen:

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell"></a>Deinstallieren von PowerShell

Wenn Sie PowerShell mit Homebrew installiert haben, verwenden Sie den folgenden Befehl zum Deinstallieren:

```sh
brew cask uninstall powershell
```

Wenn Sie PowerShell über einen direkten Download installiert haben, muss PowerShell manuell entfernt werden:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Lesen Sie den Abschnitt [Pfade](#paths) in diesem Artikel, um zu erfahren, wie Sie zusätzliche PowerShell-Pfade deinstallieren können. Entfernen Sie die Pfade mithilfe von `sudo rm`.

> [!NOTE]
> Dies ist nicht notwendig, wenn Sie eine Installation mit Homebrew durchgeführt haben.

## <a name="paths"></a>Paths

* `$PSHOME` ist `/usr/local/microsoft/powershell/6.2.0/`.
* Benutzerprofile werden über `~/.config/powershell/profile.ps1` gelesen.
* Standardprofile werden über `$PSHOME/profile.ps1` gelesen.
* Benutzermodule werden über `~/.local/share/powershell/Modules` gelesen.
* Freigegebene Module werden über `/usr/local/share/powershell/Modules` gelesen.
* Standardmodule werden über `$PSHOME/Modules` gelesen.
* Der Verlauf von „PSReadline“ wird in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt` aufgezeichnet.

Die Profile halten sich an die Konfiguration von PowerShell pro Host.
Dies bedeutet, dass hostspezifische Standardprofile in `Microsoft.PowerShell_profile.ps1` am gleichen Speicherort vorhanden sind.

PowerShell hält die [XDG Base Directory Specification (XDG Base Directory-Spezifikation)][xdg-bds] unter macOs ein.

Da macOS eine Ableitung von BSD ist, wird das Präfix `/usr/local` anstelle von `/opt` verwendet.
Daher ist `$PSHOME` gleich `/usr/local/microsoft/powershell/6.2.0/`, und der symbolische Link wird unter `/usr/local/bin/pwsh` gespeichert.

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
