---
ms.date: 12/06/2019
keywords: powershell,cmdlet
title: Windows PowerShell-Systemanforderungen
ms.openlocfilehash: 713b062916fec0c5c70ea9a7f95fea3570afb64a
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953788"
---
# <a name="windows-powershell-system-requirements"></a>Windows PowerShell-Systemanforderungen

In diesem Artikel werden die Systemanforderungen für Windows PowerShell 3.0, Windows PowerShell 4.0, Windows PowerShell 5.0 und Windows PowerShell 5.1 und spezielle Features wie Windows PowerShell Integrated Scripting Environment (ISE), Common Information Model -Befehle (CIM) und Workflows aufgeführt.

Windows® 8.1 und Windows Server® 2012 R2 enthalten alle erforderlichen Programme. Dieser Artikel ist für Benutzer früherer Releases von Windows gedacht.

## <a name="operating-system-requirements"></a>Anforderungen an das Betriebssystem

### <a name="windows-powershell-51"></a>Windows PowerShell 5.1

Windows PowerShell 5.1 wird unter den folgenden Windows-Versionen ausgeführt. Installieren Sie Windows Management Framework 5.1, um Windows PowerShell 5.1 auszuführen. Weitere Informationen finden Sie unter [Installieren und Konfigurieren von WMF 5.1](../wmf/setup/install-configure.md).

| Windows-Version | Systemanforderungen |
| ----- | ----- |
| Windows Server 2019 | standardmäßig installiert |
| Windows Server 2016 | standardmäßig installiert |
| Windows Server 2012 R2 | Installieren von [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows Server 2012 | Installieren von [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows Server 2008 R2 mit Service Pack 1 | Installieren von [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 10 Version 1607 und höher | standardmäßig installiert |
| Windows 10 Version 1507, 1511 | Installieren von [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 8.1 | Installieren von [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 7 mit Service Pack 1 | Installieren von [Windows Management Framework 5.1](https://aka.ms/wmf5download) |

### <a name="windows-powershell-50"></a>Windows PowerShell 5.0

Windows PowerShell 5.0 wird unter den folgenden Versionen von Windows ausgeführt. Installieren Sie Windows Management Framework 5.0, um Windows PowerShell 5.1 auszuführen. Weitere Informationen finden Sie unter [Installieren und Konfigurieren von WMF 5.1](../wmf/setup/install-configure.md). Windows Management Framework 5.1 ersetzt Windows Management Framework 5.0.

| Windows-Version | Systemanforderungen |
| ----- | ----- |
| Windows Server 2019 | höhere Version standardmäßig installiert |
| Windows Server 2016 | höhere Version standardmäßig installiert |
| Windows Server 2012 R2 | Installieren von [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows Server 2012 | Installieren von [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows Server 2008 R2 mit Service Pack 1 | Installieren von [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 10 Version 1607 und höher | höhere Version standardmäßig installiert |
| Windows 10 Version 1507, 1511 | standardmäßig installiert |
| Windows 8.1 | Installieren von [Windows Management Framework 5.1](https://aka.ms/wmf5download) |
| Windows 7 mit Service Pack 1 | Installieren von [Windows Management Framework 5.1](https://aka.ms/wmf5download) |

### <a name="windows-powershell-40"></a>Windows PowerShell 4.0

Windows PowerShell 4.0 wird unter den folgenden Versionen von Windows ausgeführt. Installieren Sie die angegebene Version von Windows Management Framework für Ihr Betriebssystem, um Windows PowerShell 4.0 auszuführen.

| Windows-Version | Systemanforderungen |
| ----- | ----- |
| Windows 8.1 | standardmäßig installiert |
| Windows Server 2012 R2 | standardmäßig installiert |
| Windows® 7 mit Service Pack 1 | [Installieren von Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) |
| Windows Server® 2008 R2 mit Service Pack 1 | [Installieren von Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) |

### <a name="windows-powershell-30"></a>Windows PowerShell 3.0

Windows PowerShell 3.0 wird unter den folgenden Versionen von Windows ausgeführt. Installieren Sie die angegebene Version von Windows Management Framework für Ihr Betriebssystem, um Windows PowerShell 3.0 auszuführen.

| Windows-Version | Systemanforderungen |
| ----- | ----- |
| Windows 8 | standardmäßig installiert |
| Windows Server 2012 | standardmäßig installiert |
| Windows® 7 mit Service Pack 1 | [Installieren von Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) |
| Windows Server® 2008 R2 mit Service Pack 1 | [Installieren von Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) |
| Windows Server 2008 mit Service Pack 2 | [Installieren von Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) |

## <a name="microsoft-net-framework-requirements"></a>Microsoft .NET Framework-Anforderungen

In der folgenden Tabelle finden Sie die .NET Framework-Anforderungen für Windows PowerShell.

| Version | .NET-Anforderung |
| ----- | ----- |
| Windows PowerShell 5.1 | Erfordert die vollständige Installation von Microsoft .NET Framework 4.5. Windows 8.1 und Windows Server 2012 R2 enthalten standardmäßig Microsoft .NET Framework 4.5. |
| Windows PowerShell 5.0 | Erfordert die vollständige Installation von Microsoft .NET Framework 4.5. Windows 8.1 und Windows Server 2012 R2 enthalten standardmäßig Microsoft .NET Framework 4.5. |
| Windows PowerShell 4.0 | Erfordert die vollständige Installation von Microsoft .NET Framework 4.5. Windows 8.1 und Windows Server 2012 R2 enthalten standardmäßig Microsoft .NET Framework 4.5. |
| Windows PowerShell 3.0 | Erfordert die vollständige Installation von Microsoft .NET Framework 4. In Windows 8 und Windows Server 2012 ist Microsoft .NET Framework 4.5 standardmäßig enthalten, wodurch diese Anforderung erfüllt ist. |

Verwenden Sie die folgenden Links, um Microsoft .NET Framework aus dem Microsoft Download Center herunterzuladen.

| Version | Link |
| ----- | ----- |
| .NET Framework 4.5 (`dotNetFx45_Full_setup.exe`) | [Microsoft .NET Framework 4.5](https://go.microsoft.com/fwlink/?LinkID=242919) |
| .NET Framework 4 (`dotNetFx40_Full_setup.exe`) | [Microsoft .NET Framework 4 (Webinstaller)](https://www.microsoft.com/en-us/download/details.aspx?id=17851) |

## <a name="windows-management-framework-40"></a>Windows Management Framework 4.0

Windows PowerShell 5.0 erfordert Windows Management Framework 4.0 vorinstalliert unter Windows Server 2008 R2 SP1 und Windows 7 SP1.

## <a name="ws-management-30"></a>WS-Management 3.0

Windows PowerShell 3.0 und Windows PowerShell 4.0 erfordern WS-Management 3.0, das den WinRM-Dienst und das WSMan-Protokoll unterstützt. Dieses Programm ist in Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 und Windows Management Framework 3.0 enthalten.

## <a name="windows-management-instrumentation-30"></a>Windows-Verwaltungsinstrumentation 3.0 (Windows Management Instrumentation, WMI)

Windows PowerShell 3.0 und Windows PowerShell 4.0 erfordern Windows Management Instrumentation 3.0 (Windows-Verwaltungsinstrumentation, WMI). Dieses Programm ist in Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 und Windows Management Framework 3.0 enthalten. Wenn dieses Programm nicht auf dem Computer installiert ist, werden Features, die WMI erfordern, wie z. B. CIM-Befehle, nicht ausgeführt.

## <a name="common-language-runtime-40"></a>Common Language Runtime 4.0

Windows PowerShell 3.0, Windows PowerShell 4.0 und Windows PowerShell 5.0 werden für Common Language Runtime (CLR) 4.0 kompiliert.

## <a name="graphical-user-interface-requirements"></a>Anforderungen an die grafische Benutzeroberfläche

Windows PowerShell ist eine konsolenbasierte Anwendung, die keine grafische Benutzeroberfläche erfordert.
Die Anwendung eignet sich gut für Computer ohne Bildschirm oder Monitor bzw. ohne Benutzeroberfläche wie z. B. die Server Core-Installationsoptionen von Windows Server 2012 R2 oder Windows Server 2012.

Einige Elemente erfordern eine grafische Benutzeroberfläche. Weitere Informationen finden Sie im Hilfsartikel des jeweiligen Elements:

- Windows PowerShell Integrated Scripting Environment (ISE): Weitere Informationen finden Sie unter [Windows PowerShell ISE](/powershell/scripting/components/ise/introducing-the-windows-powershell-ise).
- Cmdlets
  - [Out-GridView](/powershell/module/microsoft.powershell.utility/out-gridview)
  - [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command)
  - [Show-ControlPanelItem](/powershell/module/Microsoft.PowerShell.Management/Show-ControlPanelItem)
  - [Show-EventLog](/powershell/module/Microsoft.PowerShell.Management/Show-EventLog)
- Parameter
  - **ShowWindow**-Parameter des Cmdlets [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help).
  - **ShowSecurityDescriptorUI**-Parameter der Cmdlets [Register-PSSessionConfiguration](/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) und [Set-PSSessionConfiguration](/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration).

## <a name="windows-powershell-engine-requirements"></a>Anforderungen an die Windows PowerShell-Engine

Windows PowerShell 4.0 ist mit Windows PowerShell 3.0 und Windows PowerShell 2.0 abwärtskompatibel. Cmdlets, Anbieter, Snap-Ins, Module und Skripts, die für Windows PowerShell 2.0 und Windows PowerShell 3.0 geschrieben wurden, können unverändert in Windows PowerShell 4.0 ausgeführt werden.

Doch aufgrund einer Änderung der Richtlinie für die Laufzeitaktivierung in Microsoft .NET Framework 4 können Windows PowerShell-Hostprogramme, die für Windows PowerShell 2.0 geschrieben und mit Common Language Runtime (CLR) 2.0 kompiliert wurden, nicht unverändert in Windows PowerShell 3.0 ausgeführt werden, das mit CLR 4.0 kompiliert wurde.

Die Windows PowerShell 2.0-Engine erfordert mindestens Microsoft .NET Framework 2.0.50727. Diese Anforderung wird durch Microsoft .NET Framework 3.5 Service Pack 1 erfüllt. Diese Anforderung wird nicht durch Microsoft .NET Framework 4 und höhere Versionen von Microsoft .NET Framework erfüllt.

Informationen zum Hinzufügen oder Installieren von Windows PowerShell 2.0 Engine sowie zum Hinzufügen oder Installieren der erforderlichen Versionen von Microsoft .NET Framework finden Sie unter [Installieren des Windows PowerShell 2.0-Moduls](Installing-the-Windows-PowerShell-2.0-Engine.md). Informationen zum Starten von Windows PowerShell 2.0 Engine finden Sie unter [Starten des Windows PowerShell 2.0-Moduls](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="windows-preinstallation-environment"></a>Windows Preinstallation Environment

Windows PowerShell 2.0, Windows PowerShell 3.0 und Windows PowerShell 4.0 werden in Windows Preinstallation Environment (Windows PE) ausgeführt. Die folgenden Cmdlets werden jedoch nicht unterstützt.

- BITS-Cmdlets (Background Intelligent Transfer Service, Intelligenter Hintergrundübertragungsdienst) Weitere Informationen hierzu finden Sie unter [BitsTransfer](/powershell/module/bitstransfer/?view=win10-ps).
- [Get-EventLog](/powershell/module/Microsoft.PowerShell.Management/Get-EventLog)
- [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)
- [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help)
- [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)

Der **WinRM**-Dienst ist nicht in Windows PE vorhanden.

## <a name="see-also"></a>Siehe auch

[Erste Schritte mit Windows PowerShell](../getting-started/Getting-Started-with-Windows-PowerShell.md)

[Installieren von Windows PowerShell](Installing-Windows-PowerShell.md)

[Starten von Windows PowerShell](../getting-started/Starting-Windows-PowerShell.md)

[Windows Management Framework](../wmf/overview.md)
