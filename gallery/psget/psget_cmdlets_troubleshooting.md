---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Problembehandlung von Cmdlets | MSDN
ms.openlocfilehash: ccb39f44e8d11f1e2a912da0c4f18b700e836c91
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="how-to-resolve-warning-package-your-package-name-failed-to-download-issue" class="xliff"></a>
## Wie lässt sich das Problem „WARNUNG: Fehler beim Herunterladen des Pakets ‚Name Ihres Pakets‘“ lösen?




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

