---
title: Codebeispiel RunSpace05 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: abf19d848f6150d005c63bb0fc2ffbe1de405e2a
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734969"
---
# <a name="runspace05-code-sample"></a>RunSpace05-Codebeispiel

Hier ist der Quellcode für das Runspace05-Beispiel, das beschrieben ist [konfigurieren einen Runspace mithilfe RunspaceConfiguration](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2). Dieses Beispiel zeigt, wie Sie die Konfigurationsinformationen des Runspace erstellen, einen Runspace erstellen, erstellen Sie eine Pipeline mit einem einzigen Befehl und führen Sie dann auf die Pipeline. Der Befehl, der ausgeführt wird, wird die `Get-Process` Cmdlet.

> [!NOTE]
> Sie können die C# Quelldatei (runspace05.cs) mithilfe des Microsoft Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3.0-Laufzeitkomponenten. Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.

## <a name="code-sample"></a>Codebeispiel

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell Handbuch für Programmierer](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)