---
title: Runspace-Beispiele | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c92a6d3d-8d34-4a76-bdc3-dea923d9858e
caps.latest.revision: 17
ms.openlocfilehash: e24d40746da91f60aaf2af655ddcadc88ab6a4db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857336"
---
# <a name="runspace-samples"></a>Runspace-Beispiele

Dieser Abschnitt enthält Beispielcode, der zeigt, wie Sie verschiedene Arten von Runspaces, um die Befehle synchron und asynchron ausgeführt. Sie können Microsoft Visual Studio verwenden, erstellen eine Konsolenanwendung, und kopieren Sie den Code in den Themen in diesem Abschnitt, in der hostanwendung.

## <a name="in-this-section"></a>In diesem Abschnitt

> [!NOTE]
> Beispiele für hostanwendungen, die Schnittstellen der benutzerdefinierten Host zu erstellen, finden Sie [benutzerdefinierte Hostbeispiele](./custom-host-samples.md).

 [Runspace01 Beispiel](./runspace01-sample.md) diesem Beispiel wird gezeigt, wie Sie mit der [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) -Klasse zum Ausführen der [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet synchron und zeigen ihre Ausgabe in einer Konsole Fenster.

 [Runspace02 Beispiel](./runspace02-sample.md) diesem Beispiel wird gezeigt, wie Sie mit der [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) -Klasse zum Ausführen der [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) und [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) Cmdlets synchron. Die Ergebnisse dieser Befehle anzeigen, indem eine [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) Steuerelement.

 [Runspace03 Beispiel](./runspace03-sample.md) diesem Beispiel wird gezeigt, wie Sie mit der [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) Klasse, um ein Skript synchron auszuführen, und wie Fehler ohne Abbruch behandelt. Das Skript empfängt eine Liste von Prozessnamen und ruft diese Prozesse anschließend ab. Die Ergebnisse des Skripts, einschließlich Fehler ohne Abbruch, die beim Ausführen des Skripts generiert wurden, werden in einem Konsolenfenster angezeigt.

 [Runspace04 Beispiel](./runspace04-sample.md) diesem Beispiel wird gezeigt, wie Sie mit der [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) Klasse zum Ausführen von Befehlen, und wie Sie Fehler mit Abbruch abgefangen, die beim Ausführen der Befehle ausgelöst werden. Zwei Befehle werden ausgeführt. An den letzten Befehl wird ein ungültiges Parameterargument übergeben. Daher werden keine Objekte zurückgegeben, und ein Fehler mit Abbruch wird ausgelöst.

 [Runspace05 Beispiel](./runspace05-sample.md) diesem Beispiel wird gezeigt, wie Sie ein Snap-in zum Hinzufügen einer [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) Objekts, sodass das Cmdlet aus, der das Snap-in verfügbar ist, wenn der Runspace geöffnet wird. Das Snap-In stellt ein Get-Proc-Cmdlet (definiert durch die [GetProcessSample01-Beispiel](../cmdlet/getprocesssample01-sample.md)), die ausgeführt wird, synchron mit eine [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) Objekt.

 [Runspace06 Beispiel](./runspace06-sample.md) diesem Beispiel wird gezeigt, wie Sie ein Modul zum Hinzufügen einer [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) Objekts, sodass das Modul geladen wird, wenn der Runspace geöffnet wird. Das Modul stellt ein Get-Proc-Cmdlet (definiert durch die [GetProcessSample02-Beispiel](../cmdlet/getprocesssample02-sample.md)), die ausgeführt wird, synchron mit eine [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) Objekt.

 [Runspace07 Beispiel](./runspace07-sample.md) diesem Beispiel wird gezeigt, wie Sie einen Runspace erstellen und verwenden Sie dann diesen Runspace zum synchronen Ausführen von zwei Cmdlets mit einem [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) Objekt.

 [Runspace08 Beispiel](./runspace08-sample.md) dieses Beispiel veranschaulicht das Hinzufügen von Befehle und Argumente an die Pipeline von einer [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) -Objekt und wie Sie die Befehle synchron ausführen.

 [Runspace09 Beispiel](./runspace09-sample.md) diesem Beispiel wird gezeigt, wie Sie ein Skript hinzufügen, der Pipeline eine [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) -Objekt und das Skript asynchron ausführen. Ereignisse werden verwendet, um die Ausgabe des Skripts zu verarbeiten.

 [Runspace10 Beispiel](./runspace10-sample.md) in diesem Beispiel wird gezeigt, wie Sie einen anfänglichen Standardsitzungsstatus erstellen ein Cmdlet zum Hinzufügen der [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), wie Sie einen Runspace erstellen, verwendet die anfänglichen Sitzungsstatus sowie die zum Ausführen des Befehls mithilfe einer [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) Objekt.

 [Runspace11 Beispiel](./runspace11-sample.md) Dies zeigt, wie die [System.Management.Automation.Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand) Klasse, um einen Proxybefehl zu erstellen, die ein vorhandenes Cmdlet aufruft, aber der Satz der verfügbaren Parameter einschränkt. Der Proxybefehl wird anschließend zu einem anfänglichen Sitzungsstatus hinzugefügt, der dazu verwendet wird, einen eingeschränkten Runspace zu erstellen. Dies bedeutet, dass der Benutzer nur über den Proxybefehl auf die Funktionalität des Cmdlets zugreifen kann.

## <a name="see-also"></a>Weitere Informationen
