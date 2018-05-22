---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Problembehandlung für Cmdlets
ms.openlocfilehash: e8890cb6bbe661b8524d83cabf91483acbde8095
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="troubleshooting-cmdlets"></a>Problembehandlung für Cmdlets

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Wie lässt sich das Problem „WARNUNG: Fehler beim Herunterladen des Pakets ‚Name Ihres Pakets‘“ lösen?

Uns wurde mitgeteilt, dass bei „Install-Module“ oder „Update-Module“ auf einigen Computern Fehler ausgelöst werden.
Unseren Untersuchungen zufolge hängt dieses Problem mit der Netzwerkverbindung zusammen.
Der NuGet-Anbieter wurde vor Kurzem aktualisiert, sodass Pakete nun zuverlässig heruntergeladen werden können.
Befolgen Sie die unten stehenden Anweisungen, um den aktuellen Build des NuGet-Anbieters zu installieren und anschließend Ihr Modul zu installieren oder zu aktualisieren.
Im nachfolgenden Beispiel wird das Modul „Azure“ verwendet.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```