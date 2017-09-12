---
ms.date: 2017-08-09
keywords: powershell,cmdlet,download,installieren,setup,windows 10, windows 8.1, windows 8.0,windows 7
title: Installieren von Windows PowerShell
ms.openlocfilehash: 7ccbee66d01dd8e0e6e6ab09c6c8a399bee59ce8
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2017
---
# <a name="installing-windows-powershell"></a>Installieren von Windows PowerShell

PowerShell ist ab Windows 7 SP1 und Windows Server 2008 R2 SP1 standardmäßig auf jedem Windows-Computer installiert.

Benutzer von Linux, macOS und Windows, die **PowerShell 6** (Beta) auf ihren Computern installieren möchten, müssen Folgendes durchführen:

1. PowerShell für ihr Betriebssystem und die entsprechende Version von [GitHub](https://github.com/powershell/powershell#get-powershell) herunterladen
1. Den Installationsanweisungen folgen
  - [Linux](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md)
  - [macOS](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#macos-1012)
  - [Windows](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi)

PowerShell 6 ist auch für Docker verfügbar. Hier finden Sie Anweisungen zur [Installation von Docker](https://github.com/PowerShell/PowerShell/tree/master/docker).

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a>Finden von PowerShell unter Windows 10, 8.1, 8.0 und 7

Manchmal kann es schwierig sein, die PowerShell-Konsole oder die ISE (integrierte Skriptumgebung) unter Windows zu finden, da sich der Speicherort je nach Windowsversion unterscheidet.

In den folgenden Tabellen erfahren Sie, wo sich PowerShell in Ihrer Windows-Version befindet.
Alle aufgelisteten Versionen sind die ursprünglich veröffentlichten Versionen ohne Updates.

### <a name="for-console"></a>Für die Konsole

Version | Optionen
-- | --
Windows 10 | Klicken Sie auf das Windows-Symbol in der linken unteren Ecke, geben Sie dort „PowerShell“ ein.
Windows 8.1, 8.0 | Geben Sie auf dem Startbildschirm „PowerShell“ ein.<br/>Wenn Sie sich auf dem Desktop befinden, klicken Sie auf das Windows-Symbol in der linken unteren Ecke, geben Sie dort „PowerShell“ ein.
Windows 7 SP1 | Klicken Sie auf das Windows-Symbol in der linken unteren Ecke, geben Sie in der Suchleiste „PowerShell“ ein.

### <a name="for-ise"></a>Für die ISE

Version | Optionen
-- | --
Windows 10 | Klicken Sie auf das Windows-Symbol in der linken unteren Ecke, geben Sie dort „ISE“ ein.
Windows 8.1, 8.0 | Geben Sie auf dem Startbildschirm **PowerShell ISE** ein.<br/>Wenn Sie sich auf dem Desktop befinden, klicken Sie auf das Windows-Symbol in der linken unteren Ecke, geben Sie dort **PowerShell ISE** ein.
Windows 7 SP1 | Klicken Sie auf das Windows-Symbol in der linken unteren Ecke, geben Sie in der Suchleiste „PowerShell“ ein.

## <a name="finding-powershell-in-windows-server-versions"></a>Finden von PowerShell in Windows Server-Versionen

Ab Windows Server 2008 R2 kann ein Windows-Betriebssystem ohne die GUI (grafische Benutzeroberfläche) installiert werden.
Editionen von Windows Server ohne die GUI werden als **Core**-Editionen bezeichnet. Editionen mit der GUI werden als **Desktop**-Editionen bezeichnet.

### <a name="windows-server-core-editions"></a>Windows Server Core-Editionen

In allen Core-Editionen wird ein Windows-Eingabeaufforderungsfenster geöffnet, wenn Sie sich beim Server anmelden.

Geben Sie `powerhell` ein, und drücken Sie auf **EINGABE**, um PowerShell in der Eingabeaufforderungssitzung zu starten. Geben Sie `exit` ein, um die PowerShell-Sitzung zu beenden und zur Eingabeaufforderung zurückzukehren.

### <a name="windows-server-desktop-editions"></a>Windows Server Desktop-Editionen

Klicken Sie in allen Desktop-Editionen auf das Windows-Symbol in der linken unteren Ecke, geben Sie dort „PowerShell“ ein.
Dann erhalten Sie sowohl Konsolen- als auch ISE-Optionen.

Von der oben genannten Regel ist nur die ISE in Windows Server 2008 R2 SP1 ausgenommen. Wenn Sie diese Version nutzen, klicken Sie auf das Windows-Symbol in der rechten unteren Ecke, und geben Sie „PowerShell ISE“ ein.

## <a name="how-to-check-the-version-of-powershell"></a>Überprüfen der PowerShell-Version

Um herauszufinden, welche Version von PowerShell installiert ist, starten Sie eine PowerShell-Konsole (oder die ISE), und geben Sie `$PSVersionTable` ein und drücken auf **EINGABE**.

## <a name="upgrading-existing-windows-powershell"></a>Aktualisieren einer vorhandenen Windows PowerShell

Das Installationspaket für PowerShell befindet sich in einem WMF-Installer.
Die Version des WMF-Installers entspricht der PowerShell-Version. Es gibt keinen eigenständigen Installer für Windows PowerShell.

Wenn Sie Ihre vorhandene Version in Windows aktualisieren müssen, können Sie in der folgenden Tabelle den Installer für die PowerShell-Version finden, auf die Sie aktualisieren möchten.

Windows | PS 3.0 | PS 4.0 | PS 5.0 | PS 5.1 |
--|--|--|--|--|
Windows 10 (siehe Hinweis 1)<br/>Windows Server 2016 | - | - | - | installiert
Windows 8.1<br/>Windows Server 2012 R2 | - | installiert | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 8<br/>Windows Server 2012 | installiert | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 7 SP1<br/>Windows Server 2008 R2 SP1 | [WMF 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> **Hinweis 1**:
  >>
  >> In der ersten Version von Windows 10 wird PowerShell von Version 5.0 auf 5.1 aktualisiert, wenn automatische Updates aktiviert sind.
  >>
  >> Wenn die ursprüngliche Version von Windows 10 nicht über Windows Updates aktualisiert wurde, ist die PowerShell-Version 5.0.

## <a name="need-azure-powershell"></a>Benötigen Sie Azure PowerShell?

Wenn Sie auf der Suche nach **Azure PowerShell** sind, können Sie sich zunächst den [Overview of Azure PowerShell (Überblick über Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure) anschauen.

Ansonsten finden Sie hier weitere Informationen: [Install and configure Azure PowerShell (Installieren und Konfigurieren von Azure PowerShell)](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps).

## <a name="see-also"></a>Weitere Informationen

- [Windows PowerShell-Systemanforderungen](Windows-PowerShell-System-Requirements.md)
- [Starten von Windows PowerShell](Starting-Windows-PowerShell.md)
