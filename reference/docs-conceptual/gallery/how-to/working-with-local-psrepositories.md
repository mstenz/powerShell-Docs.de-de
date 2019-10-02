---
ms.date: 11/06/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery,psget
title: Arbeiten mit lokalen PSRepositorys
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71327991"
---
# <a name="working-with-local-powershellget-repositories"></a>Arbeiten mit lokalen PowerShellGet-Repositorys

Das PowerShellGet-Modul unterstützt andere Repositorys als den PowerShell-Katalog.
Diese Cmdlets ermöglichen die folgenden Szenarien:

- Unterstützung eines vertrauenswürdigen, bereits überprüften Satzes von PowerShell-Modulen für die Verwendung in Ihrer Umgebung
- Testen einer CI/CD-Pipeline, die PowerShell-Module oder -Skripts erstellt
- Bereitstellen von PowerShell-Skripts und -Modulen auf Systemen, die nicht auf das Internet zugreifen können

Dieser Artikel beschreibt, wie Sie ein lokales PowerShell-Repository einrichten. Der Artikel behandelt auch das im PowerShell-Katalog verfügbare [OfflinePowerShellGetDeploy][]-Modul. Dieses Modul enthält Cmdlets zum Installieren der neuesten Version von PowerShellGet in Ihrem lokalen Repository.

## <a name="local-repository-types"></a>Lokale Repositorytypen

Lokale PSRepositorys können auf zwei Arten erstellt werden: NuGet-Server oder Dateifreigabe. Jeder Typ hat Vor- und Nachteile:

NuGet-Server

| Vorteile| Nachteile |
| --- | --- |
| Eng imitierte PowerShell-Katalog-Funktionalität | App mit mehreren Ebenen erfordert Planung des Betriebs und Support |
| NuGet integriert in Visual Studio, andere Tools | Authentifizierungsmodell und NuGet-Kontenverwaltung erforderlich |
| NuGet unterstützt Metadaten in `.Nupkg`-Paketen | Veröffentlichung erfordert Verwaltung und Wartung des API-Schlüssels |
| Ermöglicht Suche, Paketverwaltung usw. | |

Dateifreigabe

| Vorteile| Nachteile |
| --- | --- |
| Kann einfach eingerichtet, gesichert und verwaltet werden | Von PowerShellGet verwendete Metadaten sind nicht verfügbar |
| Einfaches Sicherheitsmodell – Benutzerberechtigungen für Freigabe | Keine Benutzeroberfläche außer einfacher Dateifreigabe |
| Keine Einschränkungen, wie z.B. das Ersetzen vorhandener Elemente | Eingeschränkte Sicherheit und keine Aufzeichnung darüber, wer Updates ausführt |

PowerShellGet funktioniert mit jedem Typ und unterstützt das Suchen von Versionen und die Installation von Abhängigkeiten.
Einige Funktionen, die mit dem PowerShell-Katalog funktionieren, sind jedoch nicht für Basis-NuGet-Server oder Dateifreigaben verfügbar.

- Alles ist ein Paket – keine Differenzierung von Skripts, Modulen, DSC-Ressourcen oder Rollenfunktionen.
- Dateifreigabeserver können Paketmetadaten einschließlich Tags nicht sehen.

## <a name="creating-a-local-repository"></a>Erstellen eines lokalen Repositorys

Im folgenden Artikel sind die Schritte zum Einrichten Ihres eigenen NuGet-Servers aufgeführt.

- [NuGet.Server][]

Führen Sie die Schritte bis zum Punkt des Hinzufügens von Paketen aus. Die Schritte zum [Veröffentlichen eines Pakets](#publishing-to-a-local-repository) werden weiter unten in diesem Artikel behandelt.

Stellen Sie bei einem Repository auf Dateifreigabebasis sicher, dass Ihre Benutzer über Berechtigungen zum Zugriff auf die Dateifreigabe verfügen.

## <a name="registering-a-local-repository"></a>Registrieren eines lokalen Repositorys

Bevor ein Repository verwendet werden kann, muss es mithilfe des `Register-PSRepository`-Befehls registriert werden.
In den folgenden Beispielen ist die **InstallationPolicy** unter der Annahme, dass Sie Ihrem eigenen Repository vertrauen, auf *Trusted* festgelegt.

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

Beachten Sie, wie unterschiedlich die beiden Befehle **ScriptSourceLocation** behandeln. Für Repositorys auf Dateifreigabebasis müssen **SourceLocation** und **ScriptSourceLocation** übereinstimmen. Für ein webbasiertes Repository müssen sie unterschiedlich sein, also wird **SourceLocation** in diesem Beispiel ein nachstehender „/“ angefügt.

Wenn das neu erstellte PSRepository das Standardrepository sein soll, müssen Sie die Registrierung aller anderen PSRepositorys aufheben. Beispiel:

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> Das Repository mit dem Namen PSGallery ist für die Verwendung durch den PowerShell-Katalog reserviert. Sie können die Registrierung von PSGallery aufheben, aber den Namen PSGallery nicht für ein anderes Repository wiederverwenden.

Wenn Sie PSGallery wiederherstellen müssen, führen Sie den folgenden Befehl aus:

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>Veröffentlichung in einem lokalen Repository

Nachdem Sie das lokale PSRepository registriert haben, können Sie in Ihrem lokalen PSRepository veröffentlichen. Es gibt zwei Hauptveröffentlichungsszenarien: Veröffentlichen Ihres eigenen Moduls und Veröffentlichen eines Moduls aus der PSGallery.

### <a name="publishing-a-module-you-authored"></a>Veröffentlichung eines von Ihnen erstellten Moduls

Veröffentlichen Sie Ihr Modul mit `Publish-Module` und `Publish-Script` genauso wie für den PowerShell-Katalog in Ihrem lokalen PSRepository.

- Geben Sie den Speicherort für Ihren Code an
- Geben Sie einen API-Schlüssel an
- Geben Sie den Namen des Repositorys an. Beispiel: `-PSRepository LocalPSRepo`.

> [!NOTE]
> Sie müssen ein Konto auf dem NuGet-Server erstellen und sich dann anmelden, um den API-Schlüssel zu generieren und zu speichern.
> Verwenden Sie für eine Dateifreigabe eine beliebige nicht leere Zeichenfolge für den NuGetApiKey-Wert.

Beispiele:

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Um die Sicherheit zu gewährleisten, sollten API-Schlüssel nicht in Skripts hartcodiert sein. Verwenden Sie ein sicheres Schlüsselverwaltungssystem.

### <a name="publishing-a-module-from-the-psgallery"></a>Veröffentlichung eines Moduls aus der PSGallery

Um ein Modul aus der PSGallery in Ihrem lokalen PSRepository zu veröffentlichen, können Sie das Cmdlet „Save-Package“ verwenden.

- Geben Sie den Namen des Pakets an
- Geben Sie „NuGet“ als Anbieter an
- Geben Sie den PSGallery-Speicherort als Quelle an (https://www.powershellgallery.com/api/v2) )
- Geben Sie den Pfad zu Ihrem lokalen Repository an

Beispiel:

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

Wenn Ihr lokales PSRepository webbasiert ist, erfordert es einen zusätzlichen Schritt, der „nuget.exe“ zum Veröffentlichen verwendet.

Weitere Informationen finden Sie in der Dokumentation zur Verwendung von [nuget.exe][].

## <a name="installing-powershellget-on-a-disconnected-system"></a>Installieren von PowerShellGet auf einem nicht verbundenen System

Das Bereitstellen von PowerShellGet ist schwierig in Umgebungen, die erfordern, dass Systeme nicht mit dem Internet verbunden sind. Der Bootstrapprozess von PowerShellGet installiert bei der ersten Verwendung die aktuelle Version. Das OfflinePowerShellGetDeploy-Modul im PowerShell-Katalog bietet Cmdlets, die diesen Bootstrapprozess unterstützen.

Um eine Offlinebereitstellung zu starten, müssen Sie Folgendes tun:

- OfflinePowerShellGetDeploy herunterladen und auf Ihrem mit dem Internet verbundenen System und Ihren nicht verbundenen Systemen installieren
- PowerShellGet und seine Abhängigkeiten mithilfe des `Save-PowerShellGetForOffline`-Cmdlets auf das mit dem Internet verbundene System herunterladen
- PowerShellGet und seine Abhängigkeiten von dem mit dem Internet verbundenen System auf das nicht verbundene System kopieren
- Durch Verwendung von `Install-PowerShellGetOffline` auf dem nicht verbundenen System PowerShellGet und seine Abhängigkeiten in den richtigen Ordnern ablegen

Die folgenden Befehle legen mit `Save-PowerShellGetForOffline` alle Komponenten im Ordner `f:\OfflinePowerShellGet` ab.

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

An diesem Punkt müssen Sie den Inhalt von `F:\OfflinePowerShellGet` Ihren nicht verbundenen Systemen verfügbar machen. Führen Sie das `Install-PowerShellGetOffline`-Cmdlet aus, um PowerShellGet auf dem nicht verbundenen System zu installieren.

> [!NOTE]
> Es ist wichtig, dass Sie PowerShellGet nicht in der PowerShell-Sitzung ausführen, bevor Sie diese Befehle ausführen. Sobald PowerShellGet in die Sitzung geladen ist, können die Komponenten nicht aktualisiert werden. Wenn Sie PowerShellGet versehentlich starten, beenden Sie PowerShell, und starten Sie es neu.

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Nach dem Ausführen dieser Befehle können Sie PowerShellGet in Ihrem lokalen Repository veröffentlichen.

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Um die Sicherheit zu gewährleisten, sollten API-Schlüssel nicht in Skripts hartcodiert sein. Verwenden Sie ein sicheres Schlüsselverwaltungssystem.

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
