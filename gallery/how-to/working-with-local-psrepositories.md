---
ms.date: 11/06/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery,psget
title: Arbeiten mit lokalen PSRepositories
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619209"
---
# <a name="working-with-local-powershellget-repositories"></a>Arbeiten mit lokalen PowerShellGet-Repositorys

Die PowerShellGet-Modul unterstützt Repositorys als PowerShell-Katalog.
Diese Cmdlets ermöglichen die folgenden Szenarien:

- Einen vertrauenswürdige, bereits überprüften Satz von PowerShell-Module für die Verwendung in Ihrer Umgebung zu unterstützen.
- Testen einer CI/CD-Pipeline, in dem PowerShell-Module oder Skripts erstellt.
- Übermitteln Sie PowerShell-Skripts und Module auf Systeme, die auf das Internet zugreifen können nicht

Dieser Artikel beschreibt, wie Sie ein lokales Repository mit PowerShell einrichten. Der Artikel befasst sich auch die [OfflinePowerShellGetDeploy][] aus dem PowerShell-Katalog verfügbaren Modul. Dieses Modul enthält Cmdlets, um die neueste Version von PowerShellGet in das lokale Repository zu installieren.

## <a name="local-repository-types"></a>Lokales Repository-Typen

Es gibt zwei Möglichkeiten zum Erstellen einer lokalen PSRepository: NuGet-Server oder eine Dateifreigabe. Jeder Typ verfügt über vor- und Nachteile:

NuGet-Server

| Vorteile| Nachteile |
| --- | --- |
| Eng imitiert im PowerShell-Katalog-Funktion | App mit mehreren Ebenen ist erforderlich, Vorgänge, die Planung und support |
| NuGet ist in Visual Studio, andere Tools integriert. | Authentifizierungsmodell und NuGet-Kontenverwaltung, die erforderlich sind |
| NuGet unterstützt Metadaten in `.Nupkg` Pakete | Veröffentlichen muss der API-Schlüssel Verwaltung & Wartung |
| Bietet Suche, Paket-Verwaltung, usw. an. | |

Dateifreigabe

| Vorteile| Nachteile |
| --- | --- |
| Einfach zu richten, Sichern und verwalten | Metadaten von PowerShellGet verwendet nicht verfügbar sind |
| Einfache Sicherheitsmodell - Benutzerberechtigungen für die Freigabe | Keine Benutzeroberfläche, über die einfache Dateifreigabe |
| Keine Einschränkungen, wie z. B. das Ersetzen von vorhandener Elementen | Eingeschränkte Sicherheit und updates, die keine Aufzeichnung |

PowerShellGet kann mit entweder "Typ" und "unterstützt das Suchen von Versionen und Installation der Abhängigkeit.
Einige Funktionen, die für den PowerShell-Katalog funktioniert sind jedoch nicht verfügbar für die Basis-NuGet-Server oder Dateifreigaben.

- Alles, was ist ein Paket - keine Differenzierung von Skripts, Module, DSC-Ressourcen oder Funktionen der Rolle.
- Dateiserver für die Freigabe nicht auf Metadaten von Paketen, einschließlich Tags angezeigt.

## <a name="creating-a-local-repository"></a>Erstellen eines lokalen Repositorys

Im folgende Artikel sind die Schritte zum Einrichten eines eigenen NuGet-Servers aufgeführt.

- ["NuGet.Server"][]

Führen Sie die Schritte bis zum Zeitpunkt des Hinzufügens von Paketen aus. Die Schritte zum [Veröffentlichen eines Pakets](#publishing-to-a-local-repository) werden weiter unten in diesem Artikel behandelt.

Ein Repository mit Datei-Freigabe stellen Sie sicher, dass Ihre Benutzer über Berechtigungen zum Zugriff auf die Dateifreigabe verfügen.

## <a name="registering-a-local-repository"></a>Ein lokales Repository registrieren

Bevor Sie ein Repository verwendet werden kann, er muss registriert werden mithilfe der `Register-PSRepository` Befehl.
In den folgenden Beispielen die **InstallationPolicy** nastaven NA hodnotu *vertrauenswürdige*, unter der Annahme, dass Sie Ihr eigenes Repository vertrauen.

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

Notieren Sie sich den Unterschied zwischen die beiden Befehle wie behandeln **ScriptSourceLocation**. Für eine Datei-Freigabe-basierten Repositorys die die **SourceLocation** und **ScriptSourceLocation** müssen übereinstimmen. Ein Repository webbasierte, sie müssen unterschiedlich sein, also in diesem Beispiel wird eine nachfolgende "/" wird hinzugefügt, um die **SourceLocation**.

Wenn Sie die neu erstellte PSRepository das standardrepository sein möchten, müssen Sie alle anderen PSRepositories Registrierung aufheben. Beispiel:

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> Der Name des Repositorys "PSGallery" ist für die Verwendung von PowerShell-Katalog reserviert. Sie können die PSGallery Registrierung aufheben, aber Sie können den Namen "PSGallery" für alle anderen Repository nicht wiederverwenden.

Wenn Sie die PSGallery wiederherstellen müssen, führen Sie den folgenden Befehl aus:

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>Veröffentlichen in ein lokales repository

Nachdem Sie "lokale psrepository" registriert haben, können Sie in Ihrer lokalen PSRepository | MSDN veröffentlichen. Es gibt zwei Hauptszenarien veröffentlichen: Veröffentlichen Ihr eigenes Modul und veröffentlichen ein Modul aus der PSGallery.

### <a name="publishing-a-module-you-authored"></a>Die Veröffentlichung eines Moduls, die Sie erstellt

Verwendung `Publish-Module` und `Publish-Script` zu Ihrem Modul in Ihrer lokalen PSRepository genauso wie Sie für den PowerShell-Katalog veröffentlichen.

- Geben Sie den Speicherort für Ihren code
- Geben Sie einen API-Schlüssel
- Geben Sie den Namen des Repositorys. Beispiel: `-PSRepository LocalPSRepo`.

> [!NOTE]
> Sie müssen ein Konto in der NuGet-Server erstellen und dann melden Sie sich beim Generieren und speichern Sie den API-Schlüssel.
> Verwenden Sie eine beliebige nicht leere Zeichenfolge für eine Dateifreigabe für den NuGet API-Schlüssel-Wert.

Beispiele:

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Um die Sicherheit zu gewährleisten, sollte API-Schlüssel nicht in Skripts hartcodiert sein. Verwenden Sie eine sichere schlüsselverwaltung-System.

### <a name="publishing-a-module-from-the-psgallery"></a>Die Veröffentlichung eines Moduls aus dem PSGallery

Um ein Modul aus der PSGallery auf Ihrem lokalen PSRepository zu veröffentlichen, können Sie das Cmdlet "Save-Package".

- Geben Sie den Namen des Pakets
- Geben Sie "NuGet" als Dienstanbieter
- Geben Sie den PSGallery-Speicherort als die Quelle)https://www.powershellgallery.com/api/v2)
- Geben Sie den Pfad zu Ihrem lokalen Repository

Beispiel:

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

Wenn Ihre lokale PSRepository webbasierte ist, erfordert es einen zusätzlichen Schritt, der nuget.exe zum Veröffentlichen verwendet.

Finden Sie in der Dokumentation für die Verwendung von [nuget.exe][].

## <a name="installing-powershellget-on-a-disconnected-system"></a>Installieren von PowerShellGet auf einem nicht verbundenen system

Bereitstellen von PowerShellGet ist nur schwer in Umgebungen, die Systeme verfügt, die dem Internet verbunden sein müssen. PowerShellGet kann einen bootstrap-Prozess, der die neueste Version beim ersten installiert, die sie verwendet wird. Das OfflinePowerShellGetDeploy-Modul im PowerShell-Katalog bietet Cmdlets, die diese bootstrap-Prozess zu unterstützen.

Um eine offline-Bereitstellung zu starten, müssen Sie:

- Herunterladen Sie und installieren Sie das System Ihre Internetverbindung OfflinePowerShellGetDeploy und Ihren getrennten Systemen
- Herunterladen von PowerShellGet und seine Abhängigkeiten auf dem Internet verbundenen System mithilfe der `Save-PowerShellGetForOffline` Cmdlet
- Kopieren von PowerShellGet und seine Abhängigkeiten aus dem Internet verbundenen System in der nicht verbundenen system
- Verwenden der `Install-PowerShellGetOffline` auf dem getrennten System PowerShellGet und ihre Abhängigkeiten in den entsprechenden Ordnern platzieren

Die folgenden Befehle verwenden `Save-PowerShellGetForOffline` alle Komponenten in einen Ordner zu versetzen. `f:\OfflinePowerShellGet`

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Sie müssen an diesem Punkt, den Inhalt der `F:\OfflinePowerShellGet` Ihrer nicht verbundenen Systeme zur Verfügung. Führen Sie die `Install-PowerShellGetOffline` Cmdlet, um die powershellget-Modul auf dem getrennten System zu installieren.

> [!NOTE]
> Es ist wichtig, dass der PowerShellGet nicht in der PowerShell-Sitzung vor dem Ausführen dieser Befehle auszuführen. PowerShellGet in die Sitzung geladen wurden, werden nicht die Komponenten aktualisiert. Wenn Sie versehentlich PowerShellGet starten, beenden und starten Sie PowerShell neu.

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Nach dem Ausführen dieser Befehle können Sie sich, PowerShellGet auf Ihrem lokalen Repository zu veröffentlichen.

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Um die Sicherheit zu gewährleisten, sollte API-Schlüssel nicht in Skripts hartcodiert sein. Verwenden Sie eine sichere schlüsselverwaltung-System.

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
["NuGet.Server"]: /nuget/hosting-packages/nuget-server
[NuGet.exe]: /nuget/tools/nuget-exe-cli-reference
