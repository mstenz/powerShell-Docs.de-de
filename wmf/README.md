---
title: Windows Management Framework (WMF)
ms.date: 2016-12-07
keywords: PowerShell, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: b652613561655c4cbd63342b0fcc495195f83a80
ms.sourcegitcommit: b88151841dd44c8ee9296d0855d8b322cbf16076
translationtype: HT
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

- [WMF 5.1 (Preview)](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)

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
