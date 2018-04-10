---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Windows Management Framework (WMF)
ms.openlocfilehash: 715ac6fe5df47066415a65d91a0982fd7070a426
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) ist der Mechanismus, der eine einheitliche Verwaltungsschnittstelle zwischen den verschiedenen Versionen von Windows und Windows Server bereitstellt.
Bei Installation von WMF erhalten Kunden ein nahtloses Verfahren zum gemeinsamen Betrieb verschiedener Kombinationen von Betriebssystemen in ihrer Umgebung.
WMF stellt die Updates für die Verwaltungsfunktionalität in einer bestimmten Version von Windows und Windows Server zur Verfügung, damit diese in niedrigeren Versionen (in der Regel 2 niedrigeren Versionen) von Windows und Windows Server installiert werden.

Bei der WMF-Installation werden die folgenden Features hinzugefügt bzw. aktualisiert:

- Windows PowerShell
- Windows PowerShell Desired State Configuration (DSC)
- Windows PowerShell Integrated Scripting Environment (ISE)
- Windows-Remoteverwaltung (WinRM)
- Windows-Verwaltungsinstrumentation (Windows Management Instrumentation, WMI)
- Windows PowerShell-Webdienste (Verwaltung der OData-IIS-Erweiterung)
- Protokollierung des Softwarebestands (Software Inventory Logging, SIL)
- CIM-Anbieter für Server-Manager

## <a name="wmf-release-notes"></a>Anmerkungen zur WMF-Version

Um die verschiedenen Verbesserungen an PowerShell und anderen Komponenten einer bestimmten WMF-Version kennenzulernen, klicken Sie auf die nachstehenden Links, um die Anmerkungen zur jeweiligen Version zu prüfen:

- [WMF 5.1](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>Verfügbarkeit von WMF unter Windows-Betriebssystemen

| Betriebssystemversion | [WMF 5.1](https://aka.ms/wmf51download) | [WMF 5.0](https://aka.ms/wmf5download) | [WMF 4.0](https://aka.ms/wmf4download) |  [WMF 3.0](https://aka.ms/wmf3download) | [WMF 2.0](https://aka.ms/wmf2download) |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| Windows Server 2016 | Im Lieferumfang |  |  |  |  |
| Windows 10 | Im Lieferumfang | Im Lieferumfang  | | | |
| Windows Server 2012 R2| Ja | Ja | Im Lieferumfang |  |  |
| Windows 8.1 | Ja | Ja |  Im Lieferumfang |  |  |
| Windows Server 2012 | Ja | Ja | Ja |  Im Lieferumfang | |
| Windows 8 |  |  |  | Im Lieferumfang | |
| Windows Server 2008 R2 SP1 | Ja | Ja | Ja |  Ja| Im Lieferumfang |
| Windows 7 SP1  | Ja | Ja | Ja | Ja | Im Lieferumfang |
| Windows Server 2008 SP2 | | | | Ja | Ja |
| Windows Vista | | | | | Ja |
| WindowsServer 2003| | | |  | Ja |
| Windows XP | | | |  | Ja |

**„Im Lieferumfang“**: Die Features von `specified WMF` wurden in der angegebenen Version von Windows und Windows Server ausgeliefert.
Daher muss `specified WMF` nicht unter den angegebenen Betriebssystemversionen installiert werden.