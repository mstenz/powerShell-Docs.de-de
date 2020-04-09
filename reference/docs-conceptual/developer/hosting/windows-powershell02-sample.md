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
ms.openlocfilehash: 4d697e73ff4ab4cc4b88593f814d589f89005663
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978643"
---
# <a name="windows-powershell02-sample"></a>Windows PowerShell02-Beispiel

Dieses Beispiel zeigt, wie Befehle asynchron mit den Runspaces eines Runspace-Pools ausgeführt werden. Das Beispiel generiert eine Liste mit Befehlen und führt diese Befehle aus, während die Windows PowerShell-Engine einen Runspace aus dem Pool öffnet, wenn Sie benötigt wird.

## <a name="requirements"></a>Voraussetzungen

- Dieses Beispiel erfordert Windows PowerShell 2,0.

## <a name="demonstrates"></a>Veranschaulicht

Dieses Beispiel zeigt die folgenden Vorgänge:

- Das Erstellen eines runspacepool-Objekts mit einer minimalen und maximalen Anzahl von Runspaces, die gleichzeitig geöffnet sein dürfen.
- Erstellen einer Liste von Befehlen.
- Asynchrones Ausführen der Befehle.
- Aufrufen der [System. Management. Automation. Runspaces. runspacepool. getavailablerunspaces *](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) -Methode, um zu sehen, wie viele Runspaces kostenlos sind.
- Erfassen der Befehlsausgabe mit der [System. Management. Automation. PowerShell. EndInvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) -Methode.

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie Sie die Runspaces eines Runspace-Pools öffnen und Befehle in diesen Runspaces asynchron ausführen.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs" range="11-96":::

## <a name="see-also"></a>Weitere Informationen

[Schreiben einer Windows PowerShell-Host Anwendung](./writing-a-windows-powershell-host-application.md)
