---
title: Verwenden von PowerShell in Docker
description: Informationen zur Verwendung von in einem Docker-Image vorinstallierter PowerShell.
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/03/2020
ms.openlocfilehash: 771214c719ef01fe2c8bc56a4b26c629fcad3856
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279657"
---
# <a name="using-powershell-in-docker"></a>Verwenden von PowerShell in Docker

Wir veröffentlichen Docker-Images mit vorinstallierter PowerShell. Dieser Artikel veranschaulicht die ersten Schritte mit PowerShell im Docker-Container.

## <a name="finding-available-images"></a>Ermitteln verfügbarer Images

Für die veröffentlichten Images ist mindestens Docker 17.05 erforderlich. Es wird auch erwartet, dass Sie Docker ohne `sudo` oder lokale Administratorrechte ausführen können. Befolgen Sie die offiziellen [Anweisungen][install] von Docker zur ordnungsgemäßen Installation von `docker`.

Die Releasecontainer leiten sich vom offiziellen Distributionsimage ab, wie z. B. `centos:7`, installieren dann die Abhängigkeiten und zuletzt das PowerShell-Paket.

Diese Container befinden sich unter [hub.docker.com/r/microsoft/powershell][docker-release].

Weitere Informationen zu diesen Docker-Images finden Sie im Repository [PowerShell-Docker][PowerShell-Docker] auf GitHub.

## <a name="using-powershell-in-a-container"></a>Verwenden von PowerShell in einem Container

Die folgenden Schritte zeigen die Docker-Befehle, die zum Herunterladen des Images und zum Starten einer interaktiven PowerShell-Sitzung erforderlich sind.

```console
docker run -it mcr.microsoft.com/powershell
```

### <a name="remove-the-image-when-no-longer-needed"></a>Entfernen des Images, sobald es nicht mehr benötigt wird

Der folgende Befehl dient zum Löschen des Docker-Containers, wenn Sie ihn nicht mehr benötigen.

```console
docker rmi mcr.microsoft.com/powershell
```

## <a name="legal-and-licensing"></a>Rechtliche Hinweise und Lizenzierung

PowerShell wird unter der [MIT-Lizenz][] lizenziert.

### <a name="windows-docker-file-and-image-licenses"></a>Windows Docker-Datei- und Imagelizenzen

Indem Sie das Container-Betriebssystemimage für Windows-Container anfordern und verwenden, erklären Sie sich mit den ergänzenden Lizenzbedingungen einverstanden, die auf dem Docker-Hub verfügbar sind:

- [Window Server Core][Window Server Core]
- [Nano Server][Nano Server]

### <a name="telemetry"></a>Telemetrie

Standardmäßig sammelt PowerShell begrenzte Telemetriedaten ohne personenbezogene Informationen, um die Entwicklung künftiger Versionen von PowerShell zu unterstützen. Um das Senden von Telemetriedaten zu deaktivieren, erstellen Sie eine Umgebungsvariable namens `POWERSHELL_TELEMETRY_OPTOUT`, die auf den Wert `1` festgelegt wird, bevor Sie PowerShell am Installationsspeicherort starten. Die von uns erfassten Telemetriedaten unterliegen den [Datenschutzbestimmungen von Microsoft][privacy].

<!-- link references -->
[install]: https://docs.docker.com/engine/installation/
[docker-release]: https://hub.docker.com/r/microsoft/powershell/
[appinsights]: https://azure.microsoft.com/services/application-insights/
[MIT-Lizenz]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[PowerShell-Docker]: https://github.com/PowerShell/PowerShell-Docker
[Window Server Core]: https://hub.docker.com/r/microsoft/windowsservercore/
[Nano Server]: https://hub.docker.com/r/microsoft/nanoserver/
[privacy]: https://privacy.microsoft.com/privacystatement/
