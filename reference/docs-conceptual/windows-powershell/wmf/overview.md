---
ms.date: 04/19/2019
keywords: wmf,powershell,setup
title: Windows Management Framework (WMF)
ms.openlocfilehash: d581370fd602e03c86aa549eb8b273ff4d01b4e5
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808686"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) bietet eine einheitliche Verwaltungsschnittstelle für Windows. WMF bietet eine einheitliche Möglichkeit, verschiedene Versionen des Windows-Clients und von Windows Server zu verwalten. Die WMF-Installationspakete enthalten Updates der Verwaltungsfunktion und sind für ältere Windows-Versionen verfügbar.

Bei der WMF-Installation werden die folgenden Features hinzugefügt bzw. aktualisiert:

- Windows PowerShell
- Windows PowerShell Desired State Configuration (DSC)
- Windows PowerShell Integrated Scripting Environment (ISE)
- Windows-Remoteverwaltung (WinRM)
- Windows-Verwaltungsinstrumentation (WMI, Windows Management Instrumentation)
- Windows PowerShell-Webdienste (Verwaltung der OData-IIS-Erweiterung)
- Protokollierung des Softwarebestands (Software Inventory Logging, SIL)
- CIM-Anbieter für Server-Manager

## <a name="wmf-release-notes"></a>Anmerkungen zur WMF-Version

Um die verschiedenen Verbesserungen an PowerShell und anderen Komponenten einer bestimmten WMF-Version kennenzulernen, klicken Sie auf die nachstehenden Links, um die Anmerkungen zur jeweiligen Version zu prüfen:

- [WMF 5.1](whats-new/release-notes.md#wmf-51-changes)
- [WMF 5.0](whats-new/release-notes.md#wmf-50-changes)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>Verfügbarkeit von WMF unter Windows-Betriebssystemen

|        Betriebssystemversion         | [WMF 5.1][]  | WMF 5.0<br>*Nicht mehr unterstützt* | [WMF 4.0][]  | [WMF 3.0][]  | [WMF 2.0][]  |
| --------------------------------------- | ------------ | --------------------------- | ------------ | ------------ | ------------ |
| Windows Server 2019                     | Im Lieferumfang |                             |              |              |              |
| Windows Server 2016                     | Im Lieferumfang |                             |              |              |              |
| Windows 10                              | Im Lieferumfang | Im Lieferumfang                |              |              |              |
| Windows Server 2012 R2                  | Ja          | Ja                         | Im Lieferumfang |              |              |
| Windows 8.1                             | Ja          | Ja                         | Im Lieferumfang |              |              |
| Windows Server 2012                     | Ja          | Ja                         | Ja          | Im Lieferumfang |              |
| Windows 8<br>*Nicht mehr unterstützt*           |              |                             |              | Im Lieferumfang |              |
| Windows Server 2008 R2 SP1              | Ja          | Ja                         | Ja          | Ja          | Im Lieferumfang |
| Windows 7 SP1                           | Ja          | Ja                         | Ja          | Ja          | Im Lieferumfang |
| Windows Server 2008 SP2                 |              |                             |              | Ja          | Ja          |
| Windows Vista<br>*Nicht mehr unterstützt*       |              |                             |              |              | Ja          |
| Windows Server 2003<br>*Nicht mehr unterstützt* |              |                             |              |              | Ja          |
| Windows XP<br>*Nicht mehr unterstützt*          |              |                             |              | Ja          | Ja          |

- **Im Lieferumfang enthalten**: Die Features von der angegebenen WMF-Version waren in den angegebenen Versionen des Windows-Clients und von Windows Server im Lieferumfang enthalten.
- **Nicht mehr unterstützt** Diese Produkte werden von Microsoft nicht mehr unterstützt. Sie müssen ein Upgrade auf eine neue Version ausführen, die unterstützt wird. Weitere Informationen finden Sie auf der Seite [Microsoft Lifecycle-Richtlinie][].

> [!NOTE]
> Das Installationsprogramm für WMF 5.0 ist nicht mehr verfügbar und wird nicht mehr unterstützt. Es wurde durch WMF 5.1 ersetzt.

[Microsoft-Lebenszyklusrichtlinie]: https://support.microsoft.com/lifecycle
[WMF 5.1]: https://aka.ms/wmf51download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
