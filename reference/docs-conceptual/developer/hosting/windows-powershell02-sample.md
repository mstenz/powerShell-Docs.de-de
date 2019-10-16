---
title: Windows PowerShell02 Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: db7ff3a2dbd92f562379d206db494ab92ef08736
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367299"
---
# <a name="windows-powershell02-sample"></a>Windows PowerShell02-Beispiel

In diesem Beispiel wird gezeigt, wie Befehle asynchron mit den Runspaces eines Runspace-Pools ausgeführt werden. Das Beispiel generiert eine Liste mit Befehlen und führt diese Befehle aus, während die Windows PowerShell-Engine einen Runspace aus dem Pool öffnet, wenn Sie benötigt wird.

## <a name="requirements"></a>Anforderungen

- Dieses Beispiel erfordert Windows PowerShell 2,0.

## <a name="demonstrates"></a>Deutlich

In diesem Beispiel wird Folgendes veranschaulicht:

- Das Erstellen eines runspacepool-Objekts mit einer minimalen und maximalen Anzahl von Runspaces, die gleichzeitig geöffnet sein dürfen.

- Erstellen einer Liste von Befehlen.

- Asynchrones Ausführen der Befehle.

- Aufrufen der [System. Management. Automation. Runspaces. runspacepool. getavailablerunspaces *](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) -Methode, um zu sehen, wie viele Runspaces kostenlos sind.

- Erfassen der Befehlsausgabe mit der [System. Management. Automation. PowerShell. EndInvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) -Methode.

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie Sie die Runspaces eines Runspace-Pools öffnen und Befehle in diesen Runspaces asynchron ausführen.

[!code-csharp[PowerShell02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a>Weitere Informationen

[Schreiben einer Windows PowerShell-Host Anwendung](./writing-a-windows-powershell-host-application.md)
