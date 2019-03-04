---
title: Windows PowerShell-Formatierungsdateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4c8f84-ebd2-4405-bb10-cfc5400d4ad6
caps.latest.revision: 6
ms.openlocfilehash: 35efd36fd70c209e3cbeb9eff0ddf978615fffd6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854266"
---
# <a name="windows-powershell-formatting-files"></a>Windows PowerShell-Formatierungsdateien

Windows PowerShell stellt mehrere Formatierungsdateien (. ps1xml), die sich im Installationsverzeichnis (`$pshome`). Jede dieser Dateien definiert die Standardanzeige für einen bestimmten Satz von .NET-Objekten. Diese Dateien sollten nie geändert werden. Allerdings werden als Referenz können Sie zum Erstellen Ihrer eigenen benutzerdefinierten Formatierungsdateien.

Certificate.Format.ps1xml definiert die Anzeige von Objekten in den Zertifikatspeicher, z. B. x. 509-Zertifikate und Zertifikatspeicher.

DotNetTypes.Format.ps1xml definiert verschiedene .NET Objekte wie z. B. die CultureInfo, FileVersionInfo und EventLogEntry-Objekten.

FileSystem.Format.ps1xml definiert die Anzeige von Objekten wie z. B. Dateien und Verzeichnisse-Objekte.

Help.Format.ps1xml definiert die verschiedenen Ansichten verwendet werden, indem die [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) wie z. B. die ausführlichen Ansichten für vollständige, Parameter und Beispiel-Cmdlet.
Definiert die verschiedenen Ansichten ein, die die [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) wie z. B. die ausführlichen Ansichten für vollständige, Parameter und Beispiel-Cmdlet.

PowerShellCore.Format.ps1xml definiert die Anzeige der Objekte, die vom Windows PowerShell-Kern-Cmdlets, z. B. die zurückgegebenen Objekte die [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) und [Get-History](/powershell/module/Microsoft.PowerShell.Core/Get-History) Cmdlets.
Definiert die Anzeige der Objekte, die vom Windows PowerShell-Kern-Cmdlets, z. B. die zurückgegebenen Objekte die [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) und [Get-History](/powershell/module/Microsoft.PowerShell.Core/Get-History) Cmdlets.

PowerShellTrace.Format.ps1xml definiert die Anzeige von Trace-Objekten, z. B. die generierten werden, indem die [Trace-Command](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) Cmdlet.
Definiert die Anzeige von Trace-Objekten, z. B. die generierten werden, indem die [Trace-Command](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) Cmdlet.

Registry.Format.ps1xml definiert die Anzeige des Registrierungs-Objekten, z. B. und Eintragsnamen-Objekten.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](../cmdlet/writing-a-windows-powershell-cmdlet.md)
