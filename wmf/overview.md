---
ms.date: 06/12/2018
keywords: wmf,powershell,setup
title: Windows Management Framework (WMF)
ms.openlocfilehash: f279f975527dc198dd9b47ca1dc4258f54fafef5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677849"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) bietet eine einheitliche Verwaltungsschnittstelle für Windows. WMF bietet eine einheitliche Möglichkeit, verschiedene Versionen des Windows-Clients und von Windows Server zu verwalten. Die WMF-Installationspakete enthalten Updates der Verwaltungsfunktion und sind für ältere Windows-Versionen verfügbar.

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

|Betriebssystemversion  |[WMF 5.1][] |[WMF 5.0][] |[WMF 4.0][] |[WMF 3.0][]  |[WMF 2.0][] |
|--------------------------|------------|------------|------------|-------------|------------|
|Windows Server 2019       |Im Lieferumfang|            |            |             |            |
|Windows Server 2016       |Im Lieferumfang|            |            |             |            |
|Windows 10                |Im Lieferumfang|Im Lieferumfang|            |             |            |
|Windows Server 2012 R2    |Ja         |Ja         |Im Lieferumfang|             |            |
|Windows 8.1               |Ja         |Ja         |Im Lieferumfang|             |            |
|Windows Server 2012       |Ja         |Ja         |Ja         |Im Lieferumfang |            |
|Windows 8                 |            |            |            |Im Lieferumfang |            |
|Windows Server 2008 R2 SP1|Ja         |Ja         |Ja         |Ja          |Im Lieferumfang|
|Windows 7 SP1             |Ja         |Ja         |Ja         |Ja          |Im Lieferumfang|
|Windows Server 2008 SP2   |            |            |            |Ja          |Ja         |
|Windows Vista             |            |            |            |             |Ja         |
|WindowsServer 2003       |            |            |            |             |Ja         |
|Windows XP                |            |            |            |Ja          |            |

**Im Lieferumfang enthalten**: Die Features von der angegebenen WMF-Version waren in den angegebenen Versionen des Windows-Clients und von Windows Server im Lieferumfang enthalten.

[WMF 5.1]: https://aka.ms/wmf51download
[WMF 5.0]: https://aka.ms/wmf5download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
