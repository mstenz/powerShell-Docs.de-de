---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Problembehandlung für Cmdlets
ms.openlocfilehash: d87c680472c2588efbfe8b3c4d6f2dbee6883a0c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352109"
---
# <a name="troubleshooting-cmdlets"></a>Problembehandlung für Cmdlets

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Gewusst wie: Beheben des Fehlers „WARNUNG: Fehler beim Herunterladen des Pakets "Name Ihres Pakets"“

Es wurde berichtet, dass bei Ausführung von `Install-Module` oder `Update-Module` auf einigen Computern ein Fehler auftritt. Unseren Untersuchungen zufolge hängt dieses Problem mit der Netzwerkverbindung zusammen. Der NuGet-Anbieter wurde vor Kurzem aktualisiert, sodass Pakete nun zuverlässig heruntergeladen werden können. Befolgen Sie die unten stehenden Anweisungen, um den aktuellen Build des NuGet-Anbieters zu installieren und anschließend Ihr Modul zu installieren oder zu aktualisieren. Im nachfolgenden Beispiel wird das Modul „Azure“ verwendet.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a>Erforderliche Netzwerkendpunkte

Die Install- und Update-Cmdlets erfordern einen Internetzugang, um eine Verbindung mit den vom PowerShell-Katalog verwendeten Netzwerkendpunkten herzustellen. Stellen Sie sicher, dass Ihre Netzwerkzugriffsrichtlinien das Herstellen einer Verbindung mit den folgenden Endpunkten zulassen.

- oneget.org
- go.microsoft.com
- az818661.vo.msecnd.net
- [www.powershellgallery.com](www.powershellgallery.com)
- devopsgallerystorage.blob.core.windows.net
