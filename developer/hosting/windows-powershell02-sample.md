---
title: Beispiel für Windows-PowerShell02 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082514"
---
# <a name="windows-powershell02-sample"></a>Windows PowerShell02-Beispiel

Dieses Beispiel zeigt, wie Befehle asynchron ausgeführt wird, wird der Runspaces, der einen runspacepool verwenden. Im Beispiel generiert eine Liste der Befehle, und klicken Sie dann diese Befehle ausgeführt werden, während des Windows PowerShell-Moduls aus dem Pool einen Runspace öffnet, wenn er benötigt wird.

## <a name="requirements"></a>Anforderungen

- Dieses Beispiel ist die Windows PowerShell 2.0 erforderlich.

## <a name="demonstrates"></a>Zeigt

Dieses Beispiel zeigt Folgendes:

- Erstellen einen RunspacePool-Objekt, mit einer minimalen und maximalen Anzahl von Runspaces, die zur gleichen Zeit geöffnet sein dürfen.

- Erstellen eine Liste der Befehle.

- Die Befehle ausführen asynchron.

- Aufrufen der [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) Methode, um festzustellen, wie viele Runspaces kostenlos sind.

- Erfassen die Ausgabe des Befehls mit der [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) Methode.

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie der Runspaces, der einen runspacepool geöffnet und asynchron ausführen von Befehlen in diese Runspaces.

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a>Weitere Informationen

[Schreiben Sie eine Windows PowerShell-Hostanwendung](./writing-a-windows-powershell-host-application.md)