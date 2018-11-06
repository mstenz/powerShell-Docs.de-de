---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Problembehandlung für Cmdlets
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002461"
---
# <a name="troubleshooting-cmdlets"></a>Problembehandlung für Cmdlets

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Gewusst wie: Beheben des Fehlers „WARNUNG: Fehler beim Herunterladen des Pakets "Name Ihres Pakets"“

Es wurde berichtet, dass bei Ausführung von `Install-Module` oder `Update-Module` auf einigen Computern ein Fehler auftritt.
Unseren Untersuchungen zufolge hängt dieses Problem mit der Netzwerkverbindung zusammen.
Der NuGet-Anbieter wurde vor Kurzem aktualisiert, sodass Pakete nun zuverlässig heruntergeladen werden können.
Befolgen Sie die unten stehenden Anweisungen, um den aktuellen Build des NuGet-Anbieters zu installieren und anschließend Ihr Modul zu installieren oder zu aktualisieren.
Im nachfolgenden Beispiel wird das Modul „Azure“ verwendet.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
