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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360999"
---
# <a name="runspace-samples"></a>Runspace-Beispiele

Dieser Abschnitt enthält Beispielcode, der zeigt, wie verschiedene Typen von Runspaces verwendet werden, um Befehle synchron und asynchron auszuführen. Mit Microsoft Visual Studio können Sie eine Konsolenanwendung erstellen und dann den Code aus den Themen in diesem Abschnitt in die Host Anwendung kopieren.

## <a name="in-this-section"></a>In diesem Abschnitt

> [!NOTE]
> Beispiele für Host Anwendungen, die benutzerdefinierte Host Schnittstellen erstellen, finden Sie unter [Beispiele für benutzerdefinierte Hosts](./custom-host-samples.md).

 [Runspace01-Beispiel](./runspace01-sample.md) In diesem Beispiel wird gezeigt, wie die [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Klasse verwendet wird, um das [Get-Process-](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet synchron auszuführen und seine Ausgabe in einem Konsolenfenster anzuzeigen.

 [Runspace02-Beispiel](./runspace02-sample.md) In diesem Beispiel wird gezeigt, wie die [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Klasse zum synchronen Ausführen der Cmdlets " [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) " und " [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) " verwendet wird. Die Ergebnisse dieser Befehle werden mithilfe eines [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) -Steuer Elements angezeigt.

 [Runspace03-Beispiel](./runspace03-sample.md) In diesem Beispiel wird gezeigt, wie die [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Klasse verwendet wird, um ein Skript synchron auszuführen, und wie Fehler ohne Abbruch behandelt werden. Das Skript empfängt eine Liste von Prozessnamen und ruft diese Prozesse anschließend ab. Die Ergebnisse des Skripts, einschließlich Fehler ohne Abbruch, die beim Ausführen des Skripts generiert wurden, werden in einem Konsolenfenster angezeigt.

 [Runspace04-Beispiel](./runspace04-sample.md) Dieses Beispiel zeigt, wie Sie mit der [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Klasse Befehle ausführen und abschließende Fehler abfangen, die beim Ausführen der Befehle ausgelöst werden. Zwei Befehle werden ausgeführt. An den letzten Befehl wird ein ungültiges Parameterargument übergeben. Folglich werden keine Objekte zurückgegeben, und es wird ein Abbruch Fehler ausgelöst.

 [Runspace05-Beispiel](./runspace05-sample.md) In diesem Beispiel wird gezeigt, wie ein Snap-in zu einem [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt hinzugefügt wird, sodass das Cmdlet des Snap-Ins verfügbar ist, wenn der Runspace geöffnet wird. Das Snap-in stellt ein Get-proc-Cmdlet bereit (definiert durch das [GetProcessSample01-Beispiel](../cmdlet/getprocesssample01-sample.md)), das synchron mithilfe eines [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Objekts ausgeführt wird.

 [Runspace06-Beispiel](./runspace06-sample.md) In diesem Beispiel wird gezeigt, wie ein Modul einem [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt hinzugefügt wird, damit das Modul beim Öffnen des Runspace geladen wird. Das Modul stellt ein Get-proc-Cmdlet bereit (definiert durch das [GetProcessSample02-Beispiel](../cmdlet/getprocesssample02-sample.md)), das synchron mithilfe eines [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Objekts ausgeführt wird.

 [Runspace07-Beispiel](./runspace07-sample.md) Dieses Beispiel zeigt, wie ein Runspace erstellt und dann mit diesem Runspace zwei Cmdlets synchron mithilfe eines [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Objekts ausgeführt werden.

 [Runspace08-Beispiel](./runspace08-sample.md) In diesem Beispiel wird gezeigt, wie der Pipeline eines [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Objekts Befehle und Argumente hinzugefügt werden und wie die Befehle synchron ausgeführt werden.

 [Runspace09-Beispiel](./runspace09-sample.md) In diesem Beispiel wird gezeigt, wie ein Skript zur Pipeline eines [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Objekts hinzugefügt wird und wie das Skript asynchron ausgeführt wird. Ereignisse werden verwendet, um die Ausgabe des Skripts zu verarbeiten.

 [Runspace10-Beispiel](./runspace10-sample.md) In diesem Beispiel wird gezeigt, wie ein ursprünglicher Standard Sitzungszustand erstellt wird, wie ein Cmdlet zu [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)hinzugefügt wird, wie ein Runspace erstellt wird, der den anfänglichen Sitzungs Status verwendet, und wie der Befehl mit einem [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Objekt.

 [Runspace11-Beispiel](./runspace11-sample.md) Dies zeigt, wie Sie mit der [System. Management. Automation. ProxyCommand](/dotnet/api/System.Management.Automation.ProxyCommand) -Klasse einen Proxy Befehl erstellen, der ein vorhandenes Cmdlet aufruft, aber den Satz verfügbarer Parameter einschränkt. Der Proxybefehl wird anschließend zu einem anfänglichen Sitzungsstatus hinzugefügt, der dazu verwendet wird, einen eingeschränkten Runspace zu erstellen. Dies bedeutet, dass der Benutzer nur über den Proxybefehl auf die Funktionalität des Cmdlets zugreifen kann.

## <a name="see-also"></a>Weitere Informationen
