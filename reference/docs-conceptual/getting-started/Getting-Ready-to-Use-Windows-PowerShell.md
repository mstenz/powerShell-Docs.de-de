---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Vorbereiten des Verwendens von WindowsPowerShell
ms.assetid: 6dc7052d-cc5a-4220-950f-98f963a2b587
ms.openlocfilehash: de09c74e938f11a130864b1620d6c169006a27be
ms.sourcegitcommit: 4807ab554d55fdee499980835bcc279368b1df68
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="getting-ready-to-use-windows-powershell"></a>Vorbereiten des Verwendens von WindowsPowerShell
Wenn Sie die Windows PowerShell installieren und ausführen, sollten Sie die folgenden Setupoptionen berücksichtigen. Sie können diese Aufgaben zu einem beliebigen Zeitpunkt ausführen.

- **Installieren von Hilfedateien.** Die Cmdlets, die in Windows PowerShell 3.0 enthalten sind, werden zunächst ohne Hilfedateien bereitgestellt. Sie können aber das Cmdlet [Update-Help](/powershell/module/microsoft.powershell.core/update-help) verwenden, um die neuesten Hilfedateien auf Ihren Computer herunterzuladen und zu installieren. Wenn diese Dateien installiert sind, können Sie das Cmdlet [Get-Help](/powershell/module/microsoft.powershell.core/get-help) verwenden, um sie direkt über die Befehlszeile anzuzeigen. Weitere Informationen hierzu finden Sie unter [about_Updatable_Help](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

    Wenn Sie sich entscheiden, die Hilfedateien nicht zu installieren, können Sie die Hilfethemen weiterhin online lesen. Um die Onlineversion eines Cmdlet-Hilfethemas zu finden, geben Sie `Get-Help <CmdletName> -Online` ein. Informationen zum Durchsuchen der Windows PowerShell-Hilfethemen finden Sie in der [PowerShell-Dokumentation](/powershell/scripting).

- **Ausführen von Skripts.** Um die Sicherheit von Windows PowerShell zu gewährleisten, ist die Standardausführungsrichtlinie in Windows PowerShell **Eingeschränkt**. Diese Richtlinie lässt das Ausführen von Cmdlets, aber nicht das Ausführen von Skripts zu. Wenn Sie Skripts ausführen möchten, verwenden Sie das Cmdlet [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy), um die Ausführungsrichtlinie in **AllSigned** oder **RemoteSigned** zu ändern. Dieses Cmdlet kann nur von Mitgliedern der Gruppe „Administratoren“ auf dem Computer ausgeführt werden. Weitere Informationen finden Sie unter [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

- **Aktivieren von Remoting.** Das System ist bereits so konfiguriert, dass es Remotebefehle auf anderen Computern ausführen kann. Unter Windows Server 2012 R2 und Windows Server 2012 ist das System ebenfalls für das Empfangen von Remotebefehlen konfiguriert, d.h. es gestattet anderen Computern, Remotebefehle auf dem lokalen Computer auszuführen. Wenn Sie für einen Computer, auf dem eine andere Version von Windows ausgeführt wird, das Empfangen von Remotebefehlen ermöglichen möchten, führen Sie das Cmdlet [Enable-PSRemoting](/powershell/module/microsoft.powershell.core/enable-psremoting) auf diesem Computer aus. Dieses Cmdlet kann nur von Mitgliedern der Gruppe „Administratoren“ auf dem Computer ausgeführt werden. Weitere Informationen hierzu finden Sie unter [about_Remote](/powershell/module/microsoft.powershell.core/about/about_remote).

    HINWEIS: Ist Remoting auf einem Computer unter Windows PowerShell 2.0 aktiviert, ist es auch nach der Installation von Windows Management Framework 3.0 weiterhin aktiviert. Allerdings müssen Sie Remoting unter Windows Server 2008 (nicht Windows Server 2008 R2) nach der Installation von Windows Management Framework 3.0 erneut aktivieren.

## <a name="see-also"></a>Weitere Informationen
- [Installieren von Windows PowerShell](../setup/Installing-Windows-PowerShell.md)
- [Starten von Windows PowerShell](/powershell/scripting/setup/starting-windows-powershell)

